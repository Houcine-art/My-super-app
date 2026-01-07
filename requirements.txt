import streamlit as st
import google.generativeai as genai

# إعداد الربط بـ Gemini
genai.configure(api_key="YOUR_API_KEY_HERE")
model = genai.GenerativeModel('gemini-pro')

st.title("🚀 مركز القيادة للهاتف")

# القائمة الجانبية
menu = ["الذكاء الاصطناعي", "مشروع Autopilot", "مفكرة الأفكار"]
choice = st.sidebar.selectbox("ماذا تريد أن تفعل؟", menu)

if choice == "الذكاء الاصطناعي":
    st.subheader("🤖 استشارة المساعد الذكي")
    prompt = st.text_input("اسألني أي شيء:")
    if st.button("إرسال"):
        response = model.generate_content(prompt)
        st.write(response.text)

elif choice == "مشروع Autopilot":
    st.subheader("📊 حالة المواقع")
    st.write("موقع المنزل الذكي: ✅ يعمل")
    st.write("موقع الجيمنج: ✅ يعمل")
    st.write("موقع الصحة: ✅ يعمل")

elif choice == "مفكرة الأفكار":
    st.subheader("📝 سجل أفكارك")
    idea = st.text_area("فكرة جديدة:")
    if st.button("حفظ"):
        st.success("تم الحفظ!")
