Real-Time To-Do App (Glass UI)
Overview
This is a modern, real-time To-Do application built with a sleek Glass UI. It allows users to add, mark as complete, and "soft delete" tasks, with all changes syncing instantly across devices thanks to Firebase Firestore. The app provides a smooth, interactive experience with visual feedback for all actions.
Features
Real-Time Synchronization: Tasks update instantly for the user, even across different browser sessions, powered by Firebase Cloud Firestore.
Add Tasks: Easily add new tasks to your list.
Mark as Complete: Toggle tasks as complete, which visually strikes them through and fades them out.
Soft Delete with Undo: Instead of permanent deletion, tasks are "soft deleted" (faded out) and their delete button changes to an "undo" button, allowing you to recover them.
Anonymous Authentication: Users are automatically signed in anonymously, ensuring their tasks are private and persistent without requiring explicit login.
Glass UI Design: Features a modern, aesthetically pleasing glassmorphism interface with transparent elements, blur effects, and subtle shadows.
Responsive Design: The UI is designed to look good and function well on various screen sizes (mobile, tablet, desktop).
Technologies Used
HTML5: Structure of the web application.
CSS3: Custom styles for the Glass UI elements.
JavaScript (ES6+): Core application logic and DOM manipulation.
Tailwind CSS: Utility-first CSS framework for rapid and responsive styling.
Font Awesome: Icon library for visual elements like "add," "trash," and "undo."
Firebase:
Firebase Authentication: For anonymous user management and session persistence.
Cloud Firestore: A NoSQL cloud database for real-time task storage and synchronization.
Setup Instructions
To get this To-Do app running locally and connected to your own Firebase project, follow these steps:
1. Create a Firebase Project
Go to the Firebase Console.
Sign in with your Google account.
Click "Add project" or select an existing project.
Follow the prompts to create your project. You can choose whether to enable Google Analytics (optional for this app).
2. Register Your Web App
Once your project is created and you're on its overview page, click the web icon (</>) to add a web app.
Enter an App nickname (e.g., "My ToDo Web App"). You can uncheck "Also set up Firebase Hosting" if you're only running locally.
Click "Register app."
Firebase will then provide you with your firebaseConfig object. Copy this entire JavaScript object.
3. Integrate firebaseConfig into the Code
Open the index.html file (the code I provided to you) in a text editor.
Locate the <script type="module"> block near the end of the <body>.
Find the const firebaseConfig = { ... }; placeholder.
Paste your copied firebaseConfig object from the Firebase Console, replacing the placeholder. It should look something like this:
const firebaseConfig = {
  apiKey: "AIzaSyCCRxE1rEcfBaDDfiMLGxJv3OzayfoKdlE",
  authDomain: "to-do-b88d9.firebaseapp.com",
  projectId: "to-do-b88d9",
  storageBucket: "to-do-b88d9.firebasestorage.app",
  messagingSenderId: "930590755387",
  appId: "1:930590755387:web:4fd3ffabd9cadce05cea1e",
  measurementId: "G-82WJ2HMWTY" // This line is optional if you don't use Analytics
};



4. Enable Firebase Authentication
In your Firebase Console, navigate to Build > Authentication from the left menu.
Click "Get started."
Go to the "Sign-in method" tab.
Find "Anonymous" in the list and enable it. Click "Save."
5. Set Up Cloud Firestore Database and Security Rules
In your Firebase Console, navigate to Build > Firestore Database from the left menu.
Click "Create database."
Select "Start in test mode" (for quick setup; remember to review rules for production).
Choose a Cloud Firestore location (e.g., asia-south1).
Once the database is provisioned, go to the Rules tab.
Replace the default rules with the following to ensure proper user-specific data access for this app:
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Allow read/write if the user is authenticated and is accessing their own data
    match /artifacts/{appId}/users/{userId}/tasks/{document=**} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}



Click "Publish" to apply the rules.
6. Run the Application
Save the index.html file (with your updated firebaseConfig).
Open the index.html file directly in your web browser. You can usually do this by double-clicking the file or dragging it into a browser window.
Your To-Do app should now load, connect to Firebase, and allow you to add and manage tasks in real-time!
Usage
Add Task: Type your task into the input field and press "Add Task" or Enter.
Mark Complete/Incomplete: Click the checkbox next to a task to toggle its completion status. Completed tasks will be struck through and faded.
Soft Delete/Undo: Click the trash can icon next to a task to "soft delete" it. The task will fade significantly, and the icon will change to an "undo" arrow. Click the undo arrow to restore the task.
Customization
Styling: Modify the CSS within the <style> tags or add/change Tailwind CSS classes in the HTML to alter the look and feel.
Firebase Integration: For advanced use cases, explore more Firebase features like Email/Password authentication, Cloud Functions, etc. You would need to update the JavaScript code accordingly.
License
This project is open-source and available under the MIT License.
