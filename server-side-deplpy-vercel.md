
# 🚀 Server-Side Deployment on Firebase

See ph repo -> job portal resources -> server deploy

Follow these steps to deploy your server-side project to Firebase and integrate it with Vercel.

---

## 🔧 Server-Side Deployment

1. **Comment out the following commands** in your server-side code:
    ```js
    await client.connect();
    await client.db("admin").command({ ping: 1 });
    ```

2. **Set up CORS**:
    - Copy your Firebase Hosting URL and paste it in the `cors` configuration:
    ```js
    app.use(cors({
      origin: ['http://localhost:5173',
        'https://job-portal-a038b.web.app',
        'https://job-portal-a038b.firebaseapp.com'
      ],
      credentials: true
    }));
    ```
     - Make sure there are **no trailing slashes  'https://job-portal-a038b.web.app/'** after the URLs.

3. **Create a `vercel.json` file** in the root directory and add the following configuration:
    ```json
    {
      "version": 2,
      "builds": [
        {
          "src": "index.js",
          "use": "@vercel/node"
        }
      ],
      "routes": [
        {
          "src": "/(.*)",
          "dest": "index.js",
          "methods": ["GET", "POST", "PUT", "PATCH", "DELETE", "OPTIONS"]
        }
      ]
    }
    ```

4. **Make cookies secure** by updating the cookie configuration in your server-side code:
    ```js
    secure: process.env.NODE_ENV === "production",
    sameSite: process.env.NODE_ENV === "production" ? "none" : "strict",
    ```

5. **Deploy to Vercel**:
    Run the following command to deploy your project:
    ```bash
    vercel --prod
    ```

6. **Set up Vercel deployment**:
    - Press **Y** to proceed with the setup.
    - Choose **Y** for an existing project.
    - Press **N** to skip Git integration.
    - Enter your project name, or press **Enter** to use the default.
    - Choose the correct path `./` for the deployment.

7. **Go to Vercel**:
    - Open your Vercel dashboard and check your project domain.

8. **Check the public API**:
    - Verify your public API endpoints, like `/jobs`, are working correctly on the Vercel domain.

9. **Client-Side Configuration**:
    - In your client-side project (VS Code), copy `http://localhost:5000/`.
    - Paste the copied URL in the search and replace it with the Vercel server domain.
    - Ensure there are no extra `//` in the URL.

10. **Update the client-side project**:
    - Run the build command to generate the production version:
    ```bash
    npm run build
    ```

11. **Deploy the client-side to Firebase**:
    - Use the following command to deploy:
    ```bash
    firebase deploy
    ```

12. **Verify the client-side URL**:
    - Ensure the client-side application works correctly with the updated server-side URL.










<!-- Server Side Deploy in Firebase 

See ph repo -> job portal resources -> server deploy

1. //comment following commands
    await client.connect();
    await client.db("admin").command({ ping: 1 });

2. copy firebase hosting URL -> paste in cors -> 
    app.use(cors({
  origin: ['http://localhost:5173',
    'https://job-portal-a038b.web.app',
    'https://job-portal-a038b.firebaseapp.com'
  ],
  credentials: true
}))

3. create a vercel.json file in root
  add those line in vercel.json file

  {
    "version": 2,
    "builds": [
      {
        "src": "index.js",
        "use": "@vercel/node"
      }
    ],
    "routes": [
      {
        "src": "/(.*)",
        "dest": "index.js",
        "methods": ["GET", "POST", "PUT", "PATCH", "DELETE", "OPTIONS"]
      }
    ]
}


4. make .cookie secure : 

secure: process.env.NODE_ENV === "production",
sameSite: process.env.NODE_ENV === "production" ? "none" : "strict",

5. vercel --prod

6 . y -> y -> existing project -> n -> project name -> if want to change write project name otherwise press enter -> ./ 

7. Go to vercel 

8. open project domain -> check some public api like -> /jobs

9. go to client side in vs code

10. copy http://localhost:5000/ -> paste in search -> go to vercel.com -> copy server domain name -> then change every where -> must check there is no // in the url

11. then need to update the client side -> npm run build -> firebase deploy -> check client side url work correctly



 -->
