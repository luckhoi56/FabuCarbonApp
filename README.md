# routify


## Getting started

## Capacitor:
First run through if you clone repo from github carbon
1.In this repo, go to capacitor.config.json, change the "webDir":"www" to "webdir":"dist"
Basically webdir has to the same folder with npm run build


#### to build and run android
1. run "npm run build"
2. run "npx cap add android" (this should run first)
3.npx cap copy android
4.npx cap open android
5.when you get to android studio, follow their instruction



#### to build and run for web
1.run "npm run dev"