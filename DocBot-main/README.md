markdown
# 🩺 DocBot: AI-Powered Healthcare Assistant
DocBot is an intelligent, microservices-based healthcare application designed to provide preliminary symptom assessments and connect users with appropriate medical specialists in their area. 
By leveraging **Google's Gemini AI**, DocBot holds empathetic, conversational assessments to evaluate symptoms and recommend the correct medical specialty, while also functioning as a directory to find and book appointments with nearby healthcare providers.
---
## ✨ Features
- **🤖 AI Symptom Assessment**: Interactive chat interface powered by Gemini 2.5 Flash to evaluate symptoms, ask follow-up questions, and recommend a medical specialty.
- **🚨 Emergency Detection**: Automatically detects life-threatening symptoms in the chat and redirects users to emergency services.
- **🗺️ Location-Based Provider Search**: Find nearby healthcare providers, clinics, and hospitals based on the AI's recommended specialty using geospatial queries (Haversine formula).
- **📅 Appointment Booking**: View available time slots for registered doctors and book appointments seamlessly.
- **🔐 Secure Authentication**: JWT-based user authentication and secure session management.
- **🏗️ Microservices Architecture**: Separation of concerns with a React frontend, Spring Boot core backend, and a dedicated Python FastAPI service for AI interactions.
---
## 🛠️ Tech Stack
### Frontend
- **Framework**: React.js (Vite)
- **Styling**: Vanilla CSS with modern UI/UX principles (Glassmorphism, CSS Variables)
- **Icons**: Lucide React
- **Routing**: React Router DOM
### Backend (Core Application API)
- **Framework**: Spring Boot (Java)
- **Database**: PostgreSQL
- **Migrations**: Flyway
- **Security**: Spring Security + JWT
- **Build Tool**: Maven
### AI Service (Python)
- **Framework**: FastAPI
- **AI Model**: Google `genai` SDK (Gemini API)
- **Server**: Uvicorn
---
## 🚀 Getting Started
### Prerequisites
- Node.js (v18+)
- Java 17+
- Python 3.9+
- PostgreSQL
- A Google Gemini API Key
### 1. Database Setup
Ensure PostgreSQL is running. Create a database named `docbot` (or your configured DB name). The Spring Boot application will automatically run Flyway migrations on startup to create the necessary tables and seed mock data.
### 2. Python AI Service Setup
Navigate to the `ai-service` directory, install dependencies, and start the FastAPI server:
```bash
cd ai-service
python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`
pip install -r requirements.txt
Create an .env file in the ai-service directory:

env
GEMINI_API_KEY=your_gemini_api_key_here
GEMINI_MODEL=gemini-2.5-flash
Run the service:

bash
uvicorn main:app --reload --port 8000
3. Spring Boot Backend Setup
Navigate to the backend directory. Ensure your application-dev.properties is configured with your PostgreSQL credentials.

bash
cd backend
./mvnw spring-boot:run -Dspring-boot.run.profiles=dev
(The backend runs on port 8080 by default).

4. React Frontend Setup
Navigate to the frontend directory, install dependencies, and start the development server:

bash
cd "frontend - Copy" # Adjust folder name if necessary
npm install
npm run dev
🧩 Architecture Overview
User Interaction: Users interact with the React frontend to chat or search for providers.
Core Backend: The Spring Boot app handles authentication, manages the database (users, providers, appointments), and orchestrates the chat logs.
AI Delegation: When a user sends a chat message, the Spring Boot backend securely proxies the conversation history to the Python AI Service.
LLM Evaluation: The Python AI Service communicates with Google's Gemini API using a strict System Prompt, formats the response into JSON, and returns it to the backend.
⚠️ Disclaimer
DocBot is NOT a medical diagnosis tool. The information provided by the AI is a preliminary assessment only and should not replace professional medical advice, diagnosis, or treatment. Always consult a qualified healthcare provider for medical concerns.