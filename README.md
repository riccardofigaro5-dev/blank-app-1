

st.set_page_config(page_title="Chi è il tuo candidato ideale?", layout="centered")

st.title("🗳️ Scopri il candidato più vicino alle tue idee")
st.write("Rispondi alle domande scegliendo la posizione che condividi di più.")

# Domande e risposte
questions = [
    {
        "question": "Sicurezza",
        "answers": {
            "Via tutti gli immigrati": "A",
            "Pace e amore": "B",
            "Serve più polizia": "C",
            "Non è un tema prioritario": "D"
        }
    },
    {
        "question": "Ambiente",
        "answers": {
            "Bloccare tutte le grandi opere": "A",
            "Investire solo sulle rinnovabili": "B",
            "Sviluppo tecnologico e nucleare": "C",
            "Tema secondario": "D"
        }
    },
    {
        "question": "Tassazione",
        "answers": {
            "Tassare i più ricchi": "A",
            "Abbassare le tasse a tutti": "B",
            "Tasse ridotte per le imprese": "C",
            "Nessuna proposta chiara": "D"
        }
    }
]

# Inizializza punteggi
scores = {"A": 0, "B": 0, "C": 0, "D": 0}

# Mostra domande
for i, q in enumerate(questions):
    choice = st.radio(
        f"**{q['question']}**",
        list(q["answers"].keys()),
        key=i
    )
    scores[q["answers"][choice]] += 1

# Bottone finale
if st.button("🔍 Scopri il risultato"):
    winner = max(scores, key=scores.get)

    st.success("✅ Risultato calcolato!")
    st.subheader("Il candidato più vicino alle tue idee è:")

    # QUI puoi decidere quando rivelare i nomi
    candidate_names = {
        "A": "Candidato A",
        "B": "Candidato B",
        "C": "Candidato C",
        "D": "Candidato D"
    }

    st.markdown(f"## 🏆 {candidate_names[winner]}")

    st.write("### Punteggi finali:")
    st.write(scores)
