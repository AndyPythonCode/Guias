# Desde android estudio 4.2.1

En Android Studio, el versionamiento de tu aplicación se gestiona principalmente a través de los archivos de configuración de Gradle,
específicamente en el archivo build.gradle del módulo de tu aplicación (generalmente ubicado en app/build.gradle)

## Android Studio

FILE> PROJECT STRUCTURE> MODULE> DEFAULT CONFIG> [VERSION NAME]

### Cambiar APK DEBUG NAME

```gradle
    // APK name format
    // Configure the name of the output APK file
    applicationVariants.all { variant ->
    variant.outputs.all { output ->
    def date = new Date().format('yyyy-MM-dd_HH-mm')
    def versionName = defaultConfig.versionName
    outputFileName = "AndPlay_${versionName}_${date}.apk"
  }
}
```
