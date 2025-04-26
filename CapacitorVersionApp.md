# Desde android estudio 4.2.1

En Android Studio, el versionamiento de tu aplicación se gestiona principalmente a través de los archivos de configuración de Gradle,
específicamente en el archivo build.gradle del módulo de tu aplicación (generalmente ubicado en app/build.gradle)

## Android Studio

FILE> PROJECT STRUCTURE> MODULE> DEFAULT CONFIG> [VERSION NAME]

### Cambiar APK DEBUG NAME

```gradle
    // APK name format
    applicationVariants.all { variant ->
    variant.outputs.all {
        def versionName = variant.versionName
        def formattedDate = new Date().format('dd-MM-YYYY')
        outputFileName = "AndPlay_${formattedDate}_V_${versionName}.apk"
    }
}
```
