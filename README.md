import google.generativeai as genai
import streamlit as st

# Setup
genai.configure(api_key="YOUR_GEMINI_API_KEY")
model = genai.GenerativeModel('gemini-2.5-flash')

st.title("📚 AI Study Buddy")
user_input = st.text_area("Paste your notes here:")

if st.button("Generate Quiz"):
    prompt = f"Create 3 multiple choice questions based on these notes: {user_input}"
    response = model.generate_content(prompt)
    st.write(response.text)
