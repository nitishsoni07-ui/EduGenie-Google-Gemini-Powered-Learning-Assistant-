# EduGenie-Google-Gemini-Powered-Learning-Assistant-
app.py
import streamlit as st
import requests

st.title("EduGenie Learning Assistant")

# Input form
query = st.text_area("Ask EduGenie:", placeholder="Type your question here...")
if st.button("Submit"):
    if query.strip():
        # Replace with actual Google Gemini API call
        response = requests.post(
            "https://api.google-gemini.com/answer",
            json={"query": query},
            headers={"Authorization": "Bearer YOUR_API_KEY"}
        )
        if response.status_code == 200:
            st.subheader("Response:")
            st.write(response.json().get("answer", "No answer found."))
        else:
            st.error("Failed to fetch response. Please try again.")
    else:
        st.warning("Please enter a question.")
