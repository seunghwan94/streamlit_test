# streamlit_test

        {
          "name": "xxx",
          "version": "0.1.0",
          "main": "./build/electron/main.js",
          "scripts": {
            "dump": "dump-stlite-desktop-artifacts",
            "serve": "cross-env NODE_ENV=production electron .",
            "pack": "electron-builder --dir",
            "dist": "electron-builder",
            "postinstall": "electron-builder install-app-deps"
          },
          "build": {
            "files": ["build/**/*"],
            "directories": {
              "buildResources": "assets"
            }
          },
          "devDependencies": {
            "@stlite/desktop": "0.36.0",
            "cross-env": "^7.0.3",
            "electron": "^25.2.0",
            "electron-builder": "^24.4.0"
          }
        }

1. Create the following package.json file to start a new NPM project. Edit the name field
2. Run
   
        npm install
5. Create directory and file
   
        streamlit_app/streamlit_app.py.
   * Any directory name can be used here.
   * Change the directory name if you used a different name in the previous step.
   * Write your Streamlit app code in streamlit_app/streamlit_app.py.
     * The file name streamlit_app.py is not configurable now.
8. Optionally, you can add more contents in the directory, including pages/*.py for multi-page apps, any data files, and so on.
9. Run The command argument streamlit_app is the directory name of the Streamlit app you have created in the previous steps. Change it if you used a different name.

        npm run dump streamlit_app
        npm run dump streamlit_app (PackageName1) ... (PackageNameN).
        npm run dump streamlit_app -- -r requirements.txt      
   * If installing some packages is needed, pass the package names following the directory name like
   * The -r option like the pip command is also available to specify the text files listing the package names to install like Note that if you are using NPM, you need to add -- before options such as -r in the run command (ref).
    * This dump command creates ./build directory. It includes
      * The stlite bare app files.
      * streamlit_app directory copied from the one you created in the previous steps.
      * site-packages-snapshot.tar.gz that includes the installed package files.
11. Run

        npm run serve 
    * This command is just a wrapper of electron command as you can see at the "scripts" field in the package.json. It launches Electron and starts the app with ./build/electron/main.js, which is specified at the "main" field in the package.json.
13. Run
    
        npm run dist 
    * This command bundles the ./build directory created in the step above into application files (.app, .exe, .dmg etc.) in the ./dist directory. To customize the built app, e.g. setting the icon, follow the electron-builder instructions.


https://github.com/whitphx/stlite/tree/main/packages/desktop
