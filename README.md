 # 📝 Real-Time To-Do App (Glass UI)

A modern, real-time To-Do application with a sleek **Glass UI**, powered by **Firebase Firestore**. Add, mark as complete, soft delete, and undo tasks—all in real time across multiple devices. ✨

---

## 🚀 Features

- **🔄 Real-Time Sync**: Instantly updates across sessions and devices using Firebase Cloud Firestore.
- **➕ Add Tasks**: Quickly add new tasks to your list.
- **✅ Mark as Complete**: Toggle completion with visual strike-through and fading effect.
- **🗑 Soft Delete with Undo**: Tasks are faded (not permanently deleted) and can be restored with one click.
- **👤 Anonymous Authentication**: Users are automatically signed in anonymously—no login required!
- **🧊 Glass UI Design**: Clean glassmorphism with blur, shadows, and transparency.
- **📱 Responsive Design**: Optimized for mobile, tablet, and desktop screens.

---

## 🛠 Technologies Used

- **HTML5** – Structure
- **CSS3** – Styling and effects
- **JavaScript (ES6+)** – Application logic
- **Tailwind CSS** – Utility-first CSS styling
- **Font Awesome** – Icons
- **Firebase**:
  - **Authentication** – Anonymous sign-in
  - **Cloud Firestore** – Real-time task storage

---

## 🧩 Setup Instructions

### 1. 🔥 Create a Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com).
2. Click **Add project** and follow the steps.
3. Optional: Disable Google Analytics for the project.

### 2. 🌐 Register a Web App

1. Click the **Web (</>)** icon in the Firebase dashboard.
2. Enter a name (e.g., `My ToDo App`).
3. Uncheck Firebase Hosting if not needed.
4. Click **Register app** and copy the provided `firebaseConfig` object.

### 3. 📄 Insert `firebaseConfig`

1. Open `index.html` in a code editor.
2. Locate the `<script type="module">` section.
3. Replace the `firebaseConfig` placeholder with your config:
   ```js
   const firebaseConfig = {
     apiKey: "YOUR_API_KEY",
     authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
     projectId: "YOUR_PROJECT_ID",
     storageBucket: "YOUR_PROJECT_ID.appspot.com",
     messagingSenderId: "YOUR_SENDER_ID",
     appId: "YOUR_APP_ID",
     measurementId: "YOUR_MEASUREMENT_ID" // Optional
   };

### 4. 🔐 Enable Firebase Authentication

1. In Firebase Console → **Build > Authentication**.
2. Click **Get started**.
3. Under **Sign-in Method**, enable **Anonymous**.

### 5. 🗄 Set Up Firestore Database

1. Navigate to **Build > Firestore Database**.
2. Click **Create database** → choose **Start in test mode**.
3. Select a location (e.g., `asia-south1`).
4. Under the **Rules** tab, paste and publish:

   ```js
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       match /artifacts/{appId}/users/{userId}/tasks/{document=**} {
         allow read, write: if request.auth != null && request.auth.uid == userId;
       }
     }
   }
   ```

---

## ▶ Run the App

1. Save and open `index.html` in a web browser.
2. Start adding and managing your tasks in real-time!

---

## 💡 Usage Guide

* **Add Task**: Type a task and click **Add Task** or press `Enter`.
* **Mark Complete**: Click the checkbox next to the task.
* **Soft Delete**: Click the 🗑 icon. Click 🔁 to undo.

---

## 🎨 Customization

* **Styling**: Modify Tailwind classes or CSS styles.
* **Firebase Enhancements**: Upgrade to Email/Password auth, add Cloud Functions, or Firestore triggers as needed.

---

## 📄 License

This project is licensed under the **MIT License**.
Feel free to use, modify, and distribute it!

---


## 🙌 Acknowledgements

* [Firebase](https://firebase.google.com/)
* [Tailwind CSS](https://tailwindcss.com/)
* [Font Awesome](https://fontawesome.com/)

```

Let me know if you'd like a version with GitHub badges, deploy instructions (like Netlify or Vercel), or a ZIP-ready project template.
```
