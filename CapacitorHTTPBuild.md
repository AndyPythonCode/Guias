# Local Network URL can´t be acessed when building App

### Problema: No se puede acceder a URLs de red local al ejecutar la App (en Android)

Cuando desarrollas con Capacitor, puede que tengas problemas para acceder a recursos o servicios en tu red local (usando `http://`) desde la aplicación Android generada, debido a restricciones de seguridad. Aquí te presento dos pasos comunes para intentar solucionarlo:

**1. Permitir tráfico Cleartext en AndroidManifest.xml**

Agrega el atributo `android:usesCleartextTraffic="true"` dentro de la etiqueta `<application>` en tu archivo `android/app/src/main/AndroidManifest.xml`.

```xml
<application
    android:allowBackup="true"
    android:icon="@mipmap/ic_launcher"
    android:label="@string/app_name"
    android:roundIcon="@mipmap/ic_launcher_round"
    android:supportsRtl="true"
    android:theme="@style/AppTheme.NoActionBar"
    android:usesCleartextTraffic="true"> </application>
```
Nota: Permitir usesCleartextTraffic desactiva una medida de seguridad de Android para permitir conexiones HTTP (no cifradas) a destinos que no confían en certificados. 
Esto es útil para desarrollo o para acceder a recursos HTTP conocidos y de confianza en tu red local, 
pero debe usarse con precaución en producción si te conectas a servicios externos no seguros.


2 - En capacitor.config.ts configure la configuración como se muestra a continuación:

```ts
import { CapacitorConfig } from '@capacitor/cli';

const config: CapacitorConfig = {
  appId: 'io.ionic.starter',
  appName: 'My Capacitor App',
  webDir: 'www',
  android: {
    allowMixedContent: true // Añade o modifica esta línea
  }
};

export default config;
```

Nota: allowMixedContent permite que el WebView cargue contenido (como scripts, hojas de estilo o imágenes) a través de HTTP
en una página que se cargó originalmente a través de HTTPS. Esto puede ser necesario si tu app carga la interfaz principal 
vía HTTPS pero accede a recursos locales (como una API en tu máquina de desarrollo) vía HTTP. Al igual que el punto anterior, 
úsalo con conocimiento de sus implicaciones de seguridad.

Aplicando estos dos cambios y reconstruyendo tu proyecto Android (npx cap sync android seguido de la construcción en Android Studio),
deberías poder acceder a URLs HTTP de red local desde tu aplicación Capacitor.

3 - Opcional

android/app/src/main/res/xml/network_security_config.xml

```xml
 <network-security-config>
     <domain-config cleartextTrafficPermitted="true">
         <domain includeSubdomains="true">192.168.0.1</domain> // ONLY YOUR DOMAIN
         <domain includeSubdomains="true">10.0.0.1</domain> // ETC
     </domain-config>
 </network-security-config>
```
