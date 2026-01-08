import streamlit as st

st.set_page_config(page_title="Chi è il tuo candidato ideale?", layout="centered")

st.title("🗳️ Scopri il candidato più vicino alle tue idee")
st.write("Rispondi alle domande scegliendo la posizione che condividi di più.")

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

scores = {"A": 0, "B": 0, "C": 0, "D": 0}

for i, q in enumerate(questions):
    choice = st.radio(
        f"**{q['question']}**",
        list(q["answers"].keys()),
        key=i
    )
    scores[q["answers"][choice]] += 1

if st.button("🔍 Scopri il risultato"):
    winner = max(scores, key=scores.get)

    st.success("✅ Risultato calcolato!")
    st.subheader("Il candidato più vicino alle tue idee è:")

    candidate_names = {
        "A": "Candidato A",
        "B": "Candidato B",
        "C": "Candidato C",
        "D": "Candidato D"
    }

    st.markdown(f"## 🏆 {candidate_names[winner]}")
    st.write("### Punteggi finali:")
    st.write(scores)
