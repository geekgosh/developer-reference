React Native debug without android studio
=========================================
Install Java SE Development Kit 8 
http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

Install Android SDK Manager
http://filehippo.com/download_android_sdk/

Install the options that are already selected when you open the SDK Manager
• Android SDK Tools 
• Android SDK Platform-tools 
• Android SDK Build-tools 
• Android 8.0.0 (API 26) 
• Extras > Google USB Driver

Navigate to Control Panel \ System and Security \ System \ Advanced System Settings \ Environment Variables

For User Variables select Path and click Edit....

Click New and add these: 
• C:\Users\PC-NAME\AppData\Local\Android\android-sdk\tools 
• C:\Users\PC-NAME\AppData\Local\Android\android-sdk\platform-tools 
• C:\Program Files\Java\jdk1.8.0_144

In react native, android > create file > local.properties
sdk.dir = C:\\Users\\shengchuang\\AppData\\Local\\Android\\sdk

Go to C:\Users\shengchuang\AppData\Local\Android\android-sdk\tools\bin
RUN command > sdkmanager --update OOOORRRR

Yeah that's quite funny. Use PowerShell for this. A way to do that is to copy the tools folder to another place (let's say C:\temp\). Then direct into the C:\temp\tools\bin\, open the cmd prompt there and run your update commands as such:

sdkmanager.bat --sdk_root=sdkRootPath --command
Where sdkRootPath is path to your original SDK folder (C:\testinstall\sdk\). Once that is done, delete the C:\temp\tools\ copied folder.

Now to confirm that it works, open cmd and type in android, the Android SDK Manager should open up.

NOTE: I suggest using the default command prompt over a third party one such as Git Bash. With cmd, when you run commands such as npm install, you actually get a loading bar where as in Git bash, you don't get one. Some commands that work properly in cmd such as android will not be recognized by Git bash.

Now in the command prompt, cd to the Desktop.

Run these commands: 
• npm install -g create-react-native-app 
• create-react-native-app my-app 
• cd my-app/ 
• npm start 

