
# 🚀 Client-Side Deployment to Firebase Hosting

Follow these steps to deploy your client-side project (e.g., React/Vite app) to Firebase Hosting.

---

## 🔧 Initial Deployment

1. Go to [Firebase Console](https://console.firebase.google.com).
2. Open your **project folder**.
3. Navigate to:
   **Build** → **Hosting**  
   *(Make sure you're logged in — use `firebase login` if needed)*.

4. In **VS Code**, initialize Firebase with the following command:
   ```bash
   firebase init
   ```

5. Press **Y** to proceed with the setup.

   - Select **Hosting** (use spacebar to select, then press Enter).
   - Choose **Use an existing project**.
   - Select your Firebase project from the list.
   - Set the public directory as: `dist`.
   - Configure as a **Single Page App**: Yes.
   - Set up **GitHub Hosting**: No.

6. Build your app:
   ```bash
   npm run build
   ```

7. Deploy your app to Firebase Hosting:
   ```bash
   firebase deploy
   ```

---

## 🔄 If You Change Something

1. Rebuild your project:
   ```bash
   npm run build
   ```

2. Redeploy to Firebase:
   ```bash
   firebase deploy
   ```















<!-- Client Side Deploy in Firebase 

1. Go to -> firebase.console.google.com

2. Go to -> project folder

3. Go to -> Build -> Hosting -> if need check firebase login/logout

4. In vs code -> firebase.init -> press y for init -> Select hosting -> Select hosting by press space bar -> 
   existing project -> select project -> public directory (dist) -> single page -> y -> github -> n

5. npm run build

6. firebase deploy



if change something 

1. npm run build

2. firebase deploy -->
