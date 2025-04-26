# Desde android estudio 4.2.1

En Android Studio, el versionamiento de tu aplicación se gestiona principalmente a través de los archivos de configuración de Gradle,
específicamente en el archivo build.gradle del módulo de tu aplicación (generalmente ubicado en app/build.gradle)

## Android Studio

FILE> PROJECT STRUCTURE> MODULE> DEFAULT CONFIG> [VERSION NAME]

### Cambiar APK DEBUG NAME

```gradle
    // Itera sobre todas las variantes de la aplicación (debug, release, etc.)
    applicationVariants.all { variant ->
        // Nombre de la app, tipo de build y versión
        def appName = "AndPlay"
        def buildType = variant.buildType.name
        def versionName = variant.versionName

        // Personaliza el nombre del archivo APK generado
        variant.outputs.all { output ->
            outputFileName = "${appName}-${buildType}-v${versionName}.apk"
        }

        // Si es build de tipo debug, copia el APK personalizado al nombre por defecto (app-debug.apk)
        // Para que capacitor lo reconozca y lo instale en el dispositivo
        // Si no se hace esto, el APK personalizado no se instala en el dispositivo
        if (buildType == "debug") {
            variant.assemble.doLast {
                def apkDir = variant.outputs[0].outputFile.parent
                def customApk = new File(apkDir, "${appName}-debug-v${versionName}.apk")
                def defaultApk = new File(apkDir, "app-debug.apk")
                if (customApk.exists()) {
                    defaultApk.delete()
                    customApk.withInputStream { is ->
                        defaultApk.withOutputStream { os ->
                            os << is
                        }
                    }
                }
            }
        }
    }
```
