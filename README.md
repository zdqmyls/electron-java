# Maven + Springboot + Electron (+ OpenJDK)

This project can be used as a starting point to create your Java web application (f.e. Springboot) which is being wrapped in an  electron application. For the build process maven is being used only.
This project contains all the necessary configuration and some placeholder files to get you started.

This project was inspired a lot by [electron-java-app](https://github.com/jreznot/electron-java-app), but has some key differences: 
* Relies for building purposes purely on maven (ofcourse also Node but indirectly)
* Includes OpenJDK
* The electron app uses the shipped OpenJDK

# How to build
`mvn clean install -Pproduction`

The artifacts from the electron build will be put into:
* `target\electron\springboot-on-electron-darwin-x64`
* `target\electron\springboot-on-electron-win32-x64`

When using Mac OS or linux, `wine` is required to build `windows` (check the maven build for further informations).

When using Windows, admin privileges are required to build `darwin` (check the maven build for further informations).

# Shipping OpenJDK
Since not all your users have a JVM available via the classpath a OpenJDK 8 will be packed into the electron builds

# Documentation
* [Configure electron Application](https://github.com/appreciated/maven-springboot-electron/tree/master/src/main/javascript)
* [Configure the electron archs Part1](https://github.com/appreciated/maven-springboot-electron/blob/master/src/main/javascript/package.json)
* [Configure the electron archs Part2](https://github.com/appreciated/maven-springboot-electron/blob/master/pom.xml#L236-L257)

* [Electron build Part1](https://github.com/appreciated/maven-springboot-electron/blob/master/pom.xml#L198-L259)
* [Electron build Part2](https://github.com/appreciated/maven-springboot-electron/blob/master/pom.xml#L333-L358)
* [Configure OpenJDK download](https://github.com/appreciated/maven-springboot-electron/blob/master/pom.xml#L260-L332)
* [Configure OpenJDK injection](https://github.com/appreciated/maven-springboot-electron/blob/master/pom.xml#L359-L397)


# Build
When executing `mvn clean install -Pproduction` by default the `windows` (x64) and `darwin` (x64) will be build. Building the other archs will probably nto cause any build 
The rest is currently not supported but adding those shouldn't be to hard but some changed will nee to be mad at these places:
* [Create 'scripts' for the other electron archs](https://github.com/appreciated/maven-springboot-electron/blob/master/src/main/javascript/package.json#L14-L17)
* [Add the new 'scripts' to the maven build](https://github.com/appreciated/maven-springboot-electron/blob/master/pom.xml#L236-L257)
* [Download the correct JDK](https://github.com/appreciated/maven-springboot-electron/blob/master/pom.xml#L265-L294)
* [Unpack the Downloaded JDK](https://github.com/appreciated/maven-springboot-electron/blob/master/pom.xml#L296-L332)
* [Inject downloaded JDK to the electron build](https://github.com/appreciated/maven-springboot-electron/blob/master/pom.xml#L359-L395)
* [Use correct JDK at runtime](https://github.com/appreciated/maven-springboot-electron/blob/master/src/main/javascript/main.js#L108-L139)


# Pull requests are welcome
