# Firebase-Auth
 Firebase Authentication with email and password
 Using firebase database, authentication and functions
 
 1. Create firebase database project and use your own config
 2. Create two collections - guides and users
 3. Change Rules

 service cloud.firestore {
  match /databases/{database}/documents {
    // match logged in user in user coll
    match /users/{userId} {
      allow create: if request.auth.uid != null;
      allow read: if request.auth.uid == userId;
    }
    
    // Allow the user to access documents in the "guides" collection
    // only if they are authenticated.
    match /guides/{guideId} {
      allow read: if request.auth.uid != null;
      allow write: if request.auth.token.admin == true;
    }
  }
}

4. In Authentication in Sign-in Method enabled email/password for this project
 
