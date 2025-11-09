# BaTON - Candidate & Recruiter Matching Platform

*A full-stack application built for the [Name of Hackathon] hackathon. BaTON is a Telegram Web App designed to connect job candidates and recruiters in a fast, mobile-friendly, Tinder-like interface.*

---

## 💡 The Idea

In the modern job market, both candidates and recruiters are overwhelmed. BaTON aims to simplify the initial discovery phase by providing a simple, engaging platform right within Telegram. Candidates can showcase their key experience, and recruiters can quickly find talent that matches their vacancies.

## ✨ Key Features

-   **Dual Roles:** Separate user flows for Candidates and Recruiters.
-   **Candidate View:** Upload your profile and view it as a polished, interactive card.
-   **Recruiter View:** Upload a vacancy and get a swipeable stack of matched candidates.
-   **Interactive Profile Cards:** A rich UI featuring carousels for job experience, pop-ups for details (location, education), and action buttons.
-   **Telegram Integration:** Launches directly from the Telegram chat as a full-screen Web App.
-   **Mock Backend:** A complete Go backend that simulates creating profiles, vacancies, and fetching matches.

## 🛠️ Tech Stack

| Category      | Technology                                                                                                                                                                                                                           |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Frontend**  | ![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black)|
| **Backend**   | ![Go](https://img.shields.io/badge/Go-00ADD8?style=for-the-badge&logo=go&logoColor=white)                                                                                                                                               |
| **Database**  | ![SQLite](https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white)                                                                                                                                  |
| **DevOps**    | ![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white) ![Nginx](https://img.shields.io/badge/NGINX-009639?style=for-the-badge&logo=nginx&logoColor=white)                                |
| **Platform**  | ![Telegram](https://img.shields.io/badge/Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white)                                                                                                                            |

## 📂 Project Structure

The project is organized into a monorepo structure with distinct services for the frontend and backend.

```
/
├── backend/          # All Go backend source code
│   ├── internal/     # Core application logic (database, models, handlers)
│   ├── Dockerfile    # Production Dockerfile for Go
│   └── ...
├── frontend/         # All React frontend source code
│   ├── src/
│   │   ├── components/
│   │   ├── screens/
│   │   └── ...
│   └── Dockerfile
├── certs/            # Self-signed SSL certificates for local development
├── docker-compose.yml # Main file to orchestrate all services
├── nginx.conf        # Nginx reverse proxy configuration
├── .env              # Environment variables (BOT_TOKEN, WEBAPP_URL)
└── README.md
```

## 🚀 Getting Started

To run this project locally, you will need [Docker](https://www.docker.com/products/docker-desktop/) and [ngrok](https://ngrok.com/download) installed.

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd <repository-folder>
```

### 2. Set Up Environment Variables

Create a `.env` file in the root of the project by copying the example:

```bash
cp env.example .env
```

You will need to fill this file with your Telegram Bot Token.

### 3. Expose Your Local Server with ngrok

To allow Telegram to communicate with your local machine, you need a public URL.

In a **new terminal window**, run the following command to create a secure tunnel to the Nginx container's HTTPS port (443):

```bash
ngrok http 443
```

`ngrok` will provide you with a public URL (e.g., `https://<random-string>.ngrok-free.app`).

### 4. Update Your `.env` File

Open your `.env` file and update it with your new token and `ngrok` URL:

```env
BOT_TOKEN=<YOUR_NEW_TELEGRAM_BOT_TOKEN>
WEBAPP_URL=<YOUR_NGROK_HTTPS_URL>
```

### 5. Run the Application

With everything configured, start the services using Docker Compose:

```bash
docker-compose up --build
```

This command will build the Docker images for the frontend and backend, start all services, and show you the logs.

### 6. Interact with the Bot

1.  Open Telegram and find your bot.
2.  Send the `/start` command.
3.  Click the "Open Web App" button that appears.
4.  The web application should now open, running from your local machine!
