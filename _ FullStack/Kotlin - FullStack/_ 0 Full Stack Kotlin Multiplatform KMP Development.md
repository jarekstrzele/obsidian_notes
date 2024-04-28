#jovanovic_stefan

**K M P** - Kotlin Multiplatform


FRONTEND: *Kobweb* is an opinionated Kotlin framework for creating websites and web apps, built on top of Compose HTML and inspired by Next.js and Chakra UI

BACKEND: *Kobweb API* / *ktor* - it is a framework to easily build connected applications - web applications, HTTP services, mobile and browser applications

MOBILE - *JetPack* Compose with *Material 3*

DATABASE: *MongoDB*

WEB HOSTING: *Render* it is a unified cloud to build and run all your apps and websited with free TLS certificated, global CDN, private networks and auto deploys from Git


# Install `Kobweb`

## Go to `Kobweb` repo on GitHub
https://github.com/varabyte/kobweb

### install `Kobweb` binary
- Install `Kobweb` binary (https://github.com/varabyte/kobweb-cli/releases/tag/v0.9.15)
- for windows choose `.zip`
- extract it on `C:/` 
- go to `bin` folder and copy the path (`C:\kobweb-0.9.15\bin`)
- add that path to environment variables (*Edit the system environment*) and choose *Environment Variables*
- *user variables for ...* find `path` and add a new path
- make the same steps for *system variables*

check in `cmd`
```
C:\Users\jaros>kobweb --version
kobweb 0.9.15
```

### install JDK
you can find a link for `JDK` on that `GitHub` repo
- download `.zip` file and extract all on `C:/`
- add a path to *Environment Variables* in *system variable* find `JAVA_HOME`




# Create a first project template
- `kobweb create`
- choose `app/empty`
- write `BlogMultiplatform` (the name of the project)
- write the same

------
#### `settings.gradle.kts`  file !!!!!!!!!!!!!
`rootProject.name=` it can't have capital letters!!!!!

-----



OPEN that project in *Android Studio*
in terminal in `site` folder 
#### `kobweb run`

















