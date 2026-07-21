# Smart Hire

Smart Hire is a full-stack, on-demand local services platform that connects customers with trusted service providers (like Plumbers, Cleaners, Electricians, and Web Developers). 

The platform features role-based user authentication, dynamic service provider categorization, and an intelligent AI-powered chatbot that can assist users with finding services and managing bookings.

## 🚀 Features

### For Customers
- **Browse Categories**: Easily explore different service categories (Cleaning, Plumbing, Web Development, etc.).
- **View Providers**: See dedicated pages listing the exact professionals available under each category.
- **AI Chat Support**: An integrated AI Chatbot (powered by OpenAI + rule-based fallbacks) that can instantly recommend providers and answer support queries.
- **Direct Support**: A floating WhatsApp help button to directly contact the support team.

### For Service Providers
- **Specialized Registration**: Providers can select their specialized category (e.g., Electrician, Photographer) during registration.
- **Provider Dashboard**: A dedicated dashboard to manage service requests and bookings.

### Technical Features
- **Secure Authentication**: JWT-based secure login and registration system.
- **Role-based Access Control (RBAC)**: Distinct permissions for `customer`, `provider`, and `admin` roles.
- **Gravatar Integration**: Automatic profile picture generation based on user emails using the Gravatar API.

## 🛠️ Technology Stack

**Frontend:**
- HTML5, CSS3 (Modern, premium custom design, no external CSS frameworks)
- Vanilla JavaScript
- FontAwesome (for icons)

**Backend:**
- Python 3
- FastAPI (for high-performance API routing)
- SQLAlchemy (ORM for database management)
- MySQL (Primary Database, using `pymysql`)
- OpenAI API (For intelligent chatbot responses)

## 📂 Project Structure

```
project/
│
├── backend/
│   ├── .env               # Environment variables (DB URL, API Keys, Secret Keys)
│   ├── main.py            # FastAPI application entry point and main routes
│   ├── models.py          # SQLAlchemy database models
│   ├── schemas.py         # Pydantic models for data validation
│   ├── database.py        # Database connection setup
│   ├── auth.py            # JWT Authentication logic
│   ├── chatbot.py         # AI Chatbot logic and database integration
│   └── requirements.txt   # Python dependencies
│
└── frontend/
    ├── css/
    │   └── style.css      # Global styles and theme
    ├── js/
    │   ├── config.js      # Global configuration (BASE_URL)
    │   ├── auth.js        # Registration, login, and auth handling
    │   ├── providers.js   # Dynamic rendering of service providers
    │   └── chat-widget.js # Floating chatbot UI logic
    ├── index.html         # Landing page
    ├── register.html      # Registration page (Dynamic fields for providers)
    ├── login.html         # Login page
    ├── profile.html       # User profile page (with Gravatar)
    └── providers.html     # Categorized providers listing page
```

## ⚙️ Installation & Setup

### 1. Database Setup
1. Install and start **XAMPP** (or any MySQL server).
2. Start the **MySQL** service.
3. Open `phpMyAdmin` and create a new database named `smarthire`.

### 2. Backend Setup
1. Open a terminal and navigate to the `backend` directory.
2. Install the required Python packages:
   ```bash
   pip install -r requirements.txt
   ```
3. Create a `.env` file in the `backend` directory with the following variables:
   ```ini
   DATABASE_URL=mysql+pymysql://root:@localhost:3306/smarthire
   SECRET_KEY=your_super_secret_jwt_key
   OPENAI_API_KEY=your_openai_api_key_here
   ```
   *(Note: Adjust the port in `DATABASE_URL` if your MySQL runs on a different port like 3307).*
4. Start the FastAPI development server:
   ```bash
   uvicorn main:app --reload
   ```

### 3. Frontend Setup
1. The frontend consists of static files. You can open `index.html` directly in your browser.
2. Ensure that `frontend/js/config.js` has the correct `BASE_URL` pointing to your backend (default is `https://smarthire-backend-lx7p.vercel.app`).

## 🤖 Chatbot System

The platform features a highly resilient hybrid chatbot:
1. **AI Mode**: If an `OPENAI_API_KEY` is provided in the `.env` file, the bot uses GPT models to answer queries naturally.
2. **Database Fallback Mode**: If the API key is missing or the API fails, the bot falls back to a rule-based system. This fallback system queries the MySQL database in real-time to recommend actual registered service providers based on keywords (e.g., "I need a plumber").

## 📞 Support
If you need help setting up or running the project, use the floating **WhatsApp Help** button on the website to contact the support team.
