# Building Hermes Loader

This project is a fork of Fabric Loader modified to support Java 26 (Babylon) and other experimental features.

## Prerequisites

- **Java 26 (Babylon)**: You must use a Java 26 build (like the `babylon-jdk` or `jdk-26` folders in this workspace).
- **Gradle**: The project uses a Gradle wrapper configured for version 9.4.0-milestone-4 to support Java 26.

## Building

To build the project, run the following command in the root directory:

```powershell
$env:JAVA_HOME = "d:\Github\hermes\babylon-jdk"
$env:Path = "$env:JAVA_HOME\bin;$env:Path"
.\gradlew clean build -x proguardJar
```

### Notes:
- `-x proguardJar`: ProGuard currently does not support Java 26 class files (version 70). This task is bypassed to allow the build to complete.
- The output jar will be located at `build/libs/fabric-loader-0.18.4+local.jar`.

## Deploying to Prism Launcher

If you are using the provided Prism Launcher patch (`net.hermes.hermes-loader.json`), it expects the loader jar to be at:
`E:/minecraft/Prism Launcher/libraries/net/hermes/hermes-loader/0.18.4+local/hermes-loader-0.18.4+local.jar`

You can use the automated `deploy` task:

```powershell
.\gradlew deploy -x proguardJar
```

Or manually copy the jar:

```powershell
$dest = "E:/minecraft/Prism Launcher/libraries/net/hermes/hermes-loader/0.18.4+local/hermes-loader-0.18.4+local.jar"
New-Item -ItemType Directory -Force -Path (Split-Path $dest)
Copy-Item "build/libs/fabric-loader-0.18.4+local.jar" $dest -Force
```

## Troubleshooting

### "Unsupported class file major version 70"
This error occurs if you try to run Gradle or a plugin (like ProGuard) that doesn't yet support Java 26. Ensure you are using the updated Gradle wrapper and have bypassed ProGuard as shown above.

### "java.applet does not exist"
The `java.applet` package was removed in Java 26. The legacy applet loading code in the `minecraft` project has been excluded from the build.
