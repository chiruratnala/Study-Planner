# 🎓 Study Planner Web App

A modern, cloud-synced academic task manager designed to help students organize assignments, track productivity, and visualize progress. Built with **Vanilla JavaScript**, **Tailwind CSS**, and **Firebase**.
<img width="1812" height="801" alt="Screenshot (391)" src="https://github.com/user-attachments/assets/6bd0e312-50b4-480c-ac9a-6438f2450c87" />

https://stdyplanner.netlify.app/


## ✨ Features

* **☁️ Cloud Sync:** Real-time data synchronization across all devices using **Firebase Realtime Database**.
* **🔐 Secure Authentication:** Google Sign-In integration via Firebase Auth.
* **📊 Analytics Dashboard:**
    * "Instagram-style" Daily Activity chart (Last 7 days) with navigation.
    * Subject performance progress bars.
    * Completion rates and overdue task tracking.
* **📅 Calendar View:** Interactive monthly calendar to visualize deadlines.
* **✅ Task Management:** Add, edit, delete, and filter tasks (Pending, In Progress, Completed).
* **🌙 Dark Mode:** Automatic theme detection based on system preferences.
* **📱 Fully Responsive:** Optimized for mobile, tablet, and desktop.
* **🔔 Notifications:** Browser notifications for tasks due soon.

## 🛠️ Tech Stack

* **Frontend:** HTML5, JavaScript (ES6 Modules)
* **Styling:** [Tailwind CSS](https://tailwindcss.com/) (via CDN)
* **Icons:** [Lucide Icons](https://lucide.dev/)
* **Charts:** [Chart.js](https://www.chartjs.org/)
* **Backend / Database:** [Firebase](https://firebase.google.com/) (Auth + Realtime Database)

## 🚀 Getting Started

### Prerequisites
You need a **Google Firebase** account to run this application.

### 1. Clone the Repository
```bash
git clone [https://github.com/yourusername/study-planner.git](https://github.com/yourusername/study-planner.git)
cd study-planner
```
### 2. Create a Firebase Project
Go to the Firebase Console.

Click Add project and follow the setup steps.

Once created, click the Web icon (</>) to register a web app.

Copy the firebaseConfig object provided (you will need this later).

### 3. Enable Authentication
In your Firebase Console, go to Build > Authentication.

Click Get Started.

Select Google as a Sign-in method and enable it.

Important: In the Authentication settings, look for Authorized Domains. Ensure localhost and 127.0.0.1 are listed.

### 4. Enable Realtime Database
Go to Build > Realtime Database.

Click Create Database.

Choose a location and start in Locked Mode (we will update rules next).

Go to the Rules tab and paste the following security rules to ensure users can only access their own data:
```bash
JSON

{
  "rules": {
    "users": {
      "$uid": {
        ".read": "$uid === auth.uid",
        ".write": "$uid === auth.uid"
      }
    }
  }
}
```
### 5. Configure the Application
Open index.html in your code editor. Scroll to the bottom script section and replace the placeholder config with your actual Firebase keys:
```bash
JavaScript

// --- REPLACE WITH YOUR CONFIG ---
const firebaseConfig = {
    apiKey: "YOUR_API_KEY_HERE",
    authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
    databaseURL: "https://YOUR_PROJECT_ID-default-rtdb.firebaseio.com",
    projectId: "YOUR_PROJECT_ID",
    storageBucket: "YOUR_PROJECT_ID.appspot.com",
    messagingSenderId: "YOUR_SENDER_ID",
    appId: "YOUR_APP_ID"
};
```
### 6. Run the Application
Since this project uses ES6 Modules, you cannot simply open the HTML file. You must run it on a local server.

Using VS Code:

Install the Live Server extension.

Right-click index.html and select Open with Live Server.

Using Python:

Bash

python3 -m http.server 5500
Then navigate to http://127.0.0.1:5500 in your browser.

⚠️ Troubleshooting
Error: auth/unauthorized-domain

This happens if the URL in your browser (e.g., 127.0.0.1) is not whitelisted in Firebase.

Fix: Go to Firebase Console > Authentication > Settings > Authorized Domains and add 127.0.0.1.

Charts look squashed or stretched

The analytics charts are optimized for a container height of 240px. Ensure the parent container in the HTML has relative positioning (already handled in index.html).

### Author 
## Chiru Ratnala
**GitHub:** https://github.com/chiruratnala
