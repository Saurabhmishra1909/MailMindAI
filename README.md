# **MailMind AI - Smart Email Assistant**  

🚀 **Chrome extension** + **Spring Boot API** that adds an **AI-powered "Smart Reply"** button to Gmail, generating **context-aware email responses** using Google's Gemini API.  

## **✨ Features**  
✅ **One-click AI replies** directly in Gmail  
✅ **Context-aware suggestions** (analyzes tone, content, and sender)  
✅ **Customizable response styles** (Professional/Casual)  
✅ **Spring Boot backend** with rate-limited Gemini API calls  
✅ **Chrome extension** with React.js frontend  

---

## **🛠️ Tech Stack**  
| Component       | Technologies Used |  
|----------------|------------------|  
| **Backend**    | Spring Boot, WebClient, Gemini API |  
| **Frontend**   | React.js, Chrome Extension API |  
| **AI**         | Google Gemini (LLM), Prompt Engineering |  

---

## **⚙️ Setup**  

### **1. Backend (Spring Boot)**  
```bash
# Clone the repo
git clone https://github.com/yourusername/mailmind-ai.git
cd mailmind-ai/backend

# Set up environment variables
echo "GEMINI_API_KEY=your_api_key_here" > .env
echo "GEMINI_API_URL=https://generativelanguage.googleapis.com/v1beta/models/gemini-pro:generateContent?key=" >> .env

# Run the Spring Boot app
./mvnw spring-boot:run
```
- **API Endpoint:** `POST /api/email/generate`  
- **Request Body Example:**  
```json
{
  "emailContent": "Hi, can we reschedule tomorrow's meeting?",
  "tone": "professional"
}
```

---

### **2. Chrome Extension (React Frontend)**  
```bash
cd ../frontend/chrome-extension
npm install
npm run build
```
- Load the extension in Chrome:  
  1. Go to `chrome://extensions`  
  2. Enable **Developer mode**  
  3. Click **Load unpacked** and select the `dist/` folder  

---

### **3. Configure Extension**  
- Open `src/config.js` and set:  
```javascript
const API_ENDPOINT = "http://localhost:8080/api/email/generate";
```

---

## **📂 Project Structure**  
```
mailmind-ai/
├── backend/               # Spring Boot API
│   ├── src/main/java/com/email/writer/
│   │   ├── EmailGeneratorController.java  # REST endpoint
│   │   ├── EmailGeneratorService.java     # Gemini AI logic
│   │   └── EmailRequest.java              # DTO
│   └── application.properties
│
├── frontend/              # Chrome Extension
│   ├── public/            # Manifest & icons
│   ├── src/
│   │   ├── components/    # React UI
│   │   └── background.js  # Gmail integration
│   └── package.json
│
└── README.md
```

---

## **🚀 Future Improvements**  
- [ ] **Multi-language support**  
- [ ] **Email thread history analysis**  
- [ ] **User preference profiles**  
- [ ] **Deploy backend on Cloud Run/AWS**  

---

## **📜 License**  
MIT © [Saurabh Mishra](https://github.com/saurabhmishra1909)  

---

## **💡 How It Works**  
1. The **Chrome extension** injects a button into Gmail’s UI.  
2. When clicked, it sends the email content to the **Spring Boot API**.  
3. The backend processes the text using **Gemini AI** and returns a smart reply.  
4. The extension auto-fills the reply in Gmail’s compose box.  
