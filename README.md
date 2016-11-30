# Android-FirebaseAuthDemo-Signup
Firebase for Android basic singup


Basic useful feature list:

 * Allow user to sign up to the application
 * The user's information is dispalyed via Firebase Auth 


Dependencies

```gradle
 compile 'com.google.firebase:firebase-auth:10.0.1'
```

Apply this plugin to the **build.gradle(Module:app)** after *dependnecies*

```gradle
apply plugin: 'com.google.gms.google-services'
```

In your **build.gradle(Project:FirebaseAuthDemo)** or Poject folder add this classpath in the *dependencies*
```gradle
 classpath 'com.google.gms:google-services:3.0.0'
```



Permissions

Add this permission in you **AndroidManifest.xml** file
```xml
 <uses-permission android:name="android.permission.INTERNET"/>
```

In order to use Firebase you will need to initialize the firebase auth object. In your **MainActivity**

```java
FirebaseAuth firebaseAuth;
```
Next in your onCreate method you will create the object for firebase.

```java
 firebaseAuth = FirebaseAuth.getInstance();
```
You will need to create method for the *firebaseAuth* **creatUserWithEmailAndPassword()**

```java
     firebaseAuth.createUserWithEmailAndPassword(email, password)
                .addOnCompleteListener(this, new OnCompleteListener<AuthResult>() {
                    @Override
                    public void onComplete(@NonNull Task<AuthResult> task) {
                        //checking if success
                        if(task.isSuccessful()){
                            //display some message here
                            Toast.makeText(MainActivity.this,"Successfully registered",Toast.LENGTH_LONG).show();
                        }else{
                            //display some message here
                            Toast.makeText(MainActivity.this,"Registration Error",Toast.LENGTH_LONG).show();
                        }
                        progressDialog.dismiss();
                    }
                });
                
```
Additional information available via [Firebase](https://firebase.google.com/docs/auth/android/start/) website
