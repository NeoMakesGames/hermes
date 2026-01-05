# Hermes Loader

Hermes Loader is a specialized fork of [Fabric Loader](https://github.com/FabricMC/fabric-loader) designed to support **Java 26 (Project Babylon)** and other experimental JVM features. It provides mod loading facilities and useful abstractions for Minecraft mods, specifically tailored for cutting-edge Java environments.

## Key Features

- **Java 26 Support**: Fully compatible with Java 26 (class file version 70).
- **Project Babylon Integration**: Optimized for use with Babylon JDK builds.
- **Custom Branding**: Uses `hermesloader` as the mod ID and `.hermes` for its cache directory.
- **Experimental Mod Discovery**: Includes logic to handle and report non-Hermes mods.
- **Modern Gradle**: Configured with Gradle 9.4+ to support the latest Java features.

## Getting Started

Hermes Loader is intended for developers and enthusiasts who want to experiment with the latest Java features in a Minecraft environment.

### Prerequisites

- **Java 26 (Babylon)**: You must have a Java 26 build installed. You can find compatible builds in the `babylon-jdk` or `jdk-26` directories if provided in your environment.
- **Prism Launcher**: Recommended for testing, with the provided `net.hermes.hermes-loader.json` patch.

## Building

To build Hermes Loader, ensure your `JAVA_HOME` points to a Java 26 installation and run:

```powershell
.\gradlew clean build -x proguardJar
```

*Note: ProGuard is currently bypassed as it does not yet support Java 26 class files.*

For detailed build and deployment instructions, see [BUILDING.md](BUILDING.md).

## Project Structure

- `src/main/java`: Core loader implementation (forked from Fabric).
- `src/java26`: Java 26 specific enhancements and experiments.
- `minecraft/`: Minecraft-specific integration and testing environment.
- `babylon-jdk/`: Local copy of the Babylon JDK (if present).

## License

Hermes Loader is licensed under the **Apache License 2.0**, consistent with the original Fabric Loader project. See the [LICENSE](LICENSE) file for details.

---

*Hermes Loader is an independent project and is not officially affiliated with the Fabric Project or Mojang AB.*
