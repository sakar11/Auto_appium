# Instalación de Appium para Windows

### Obtener Tipo de Procesador y CPU
* Ir a: Panel de control\Sistema y seguridad\Sistema
* Procesador: Intel o AMD
* Tipo de sistema: 64-bit x64-based o 32-bit x86-based

### Instalar JAVA JDK 8 (Java SE Development Kit)
* Abre el CMD y comprueba que versión de java tienes: `c:\> java -version`
	* Si la versión es menor que 1.8 o el comando no es reconocido tendrás que instalar java.
	* Si ya tienes la versión 1.8, asegurate de tener la última versión que se muestra mas abajo.
* Click [aquí](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
* Marca el check de "Accept License Agreement".
* Haz click en el enlace "jdk-8u231-windows-x64.exe" si tu ordenador es de 64-bit.
* Haz click en el enlace "jdk-8u231-windows-i586.exe" si tu ordenador es de 32-bit.
* Probablemente te pida hacer login para comenzar la descarga. En caso de no tener cuenta, creala.
* ¡Toma nota del directorio de instalación! Lo necesitarás mas tarde. Por ejemplo: `C:\Program Files\Java\jdk1.8.0_231`

### Instalar Node.js
* Descarga e instala [64-bit](https://nodejs.org/dist/v12.13.0/node-v12.13.0-x64.msi) o [32-bit](https://nodejs.org/dist/v12.13.0/node-v12.13.0-x86.msi)
* ¡Toma nota del directorio de instalación del **NPM**! Lo necesitarás mas tarde. Por ejemplo: `C:\Users\tuUsuario\AppData\Roaming\npm`

### Instalar Appium via NPM
* Abrir "Windows Powershell" como administrador. Para ello, busca "Windows Powershell" en el menu de inicio, haz click derecho en "Windows Powershell" y selecciona ejecutar como administrador.
	* Ejecuta: `npm install -g appium`
	* Verifica que appium se ha instalado correctamente poniendo esto en la consola `C:\> appium -v`
* En caso de tener ya appium instalado y queramos actualizar a la última versión:
	* Ejecuta: `npm update -g appium` y verifica que se ha actualizado la versión.

### Instalar Android Studio
* Click [aquí](https://developer.android.com/studio/index.html#win-bundle) para descargar Android Studio.
* Acepta los Terminos y Condiciones y después haz click en el botón DOWNLOAD ANDROID STUDIO FOR WINDOWS.
* Selecciona que SI permites a la aplicacion hacer cambios en tu dispositivo.
* Haz click en Next.
* En la ventana Choose Components asegurate de tener seleccionadas Android SDK and Android Virtual Device.
* Haz click en Next en la ventana Choose Components.
* Haz click en "I Agree" License Agreement.
* Establece la ruta de Android Studio en: `C:\Program Files\Android\Android Studio`. Esta será la ruta por defecto.
* Establece la ruta de Android SDK en: `C:\Users\tuUsuario\AppData\Local\Android\sdk`. Esta será la ruta por defecto.
* Establece Android Studio como nombre de la carpeta del Menu Inicio.
* Haz click en Install. Tomará un rato...
* Haz click en Next.
* Haz click en Finish para iniciar Android Studio.

### Instalar Android 6.0 SDK 23
* En la ventana de Bienvenida de Android Studio.
* Haz click en el botón Configure situado en la parte inferior derecha de la ventana de bienvenida de Android Studio.
* Haz click en SDK Manager en el desplegable de Configure.
* Selecciona Android 6.0 (Marshmallow) SDK. 
   * Es probable que ya tengas instalada la última versión de Android. Aun así, es bueno tener esta version de Android tambien ya que es la mas estable y usada.
* Haz click en el recuadro "Show Package Details" abajo a la derecha.
* Asegurate que están seleccionadas las siguientes dependencias del SDK para que las instale:
   * Android SDK Platform 23
   * Sources for Android 23
   * Intel x86 Atom System Image.
   * Intel x86 Atom_64 System Image.
   * Google API's Intel x86 Atom System Image
   * Google API's Intel X86 Atom_64 System Image
* Haz click en OK.
* Haz click en OK en la ventana de confirmación y acepta la "License Agreement".
* Haz click en Next para instalar los componentes del SDK 23. Esto tomará un rato...
* Haz click en Finish.
* Nota: Este proceso es el mismo para cualquier versión que se quiera tener.

### Add Environment Variables
* Ir a: Panel de control\Sistema y seguridad\Sistema > Configuración avanzada del sistema > Variables de entorno...
* En el recuadro "Variables de usuario para **tu_nombre_de_usuario**"
	* Añadir la variable ANDROID_HOME.
		* Click en Nueva...
		* Nombre de la variable: ANDROID_HOME
		* Valor de la variable: `C:\Users\tuUsuario\AppData\Local\Android\sdk` (Cambia esto a tu ruta del SDK)
		* Click en Aceptar.
	* Añadir la variable JAVA_HOME.
		* Click en Nueva...
		* Nombre de la variable: JAVA_HOME
		* Valor de la variable: `C:\Program Files\Java\jdk1.8.0_231` (Ruta de la instalacion del JDK)
		* Click en Aceptar.
	* Añadir la variable NODE_HOME.
		* Click en Nueva...
		* Nombre de la variable: NODE_HOME
		* Valor de la variable: `C:\Program Files\nodejs` (Cambia esto a tu ruta de instalacion del Nodejs)
		* Click en Aceptar.
	* Haz click en la variable "Path".
		* Click Editar > Nuevo por cada ruta que haya que añadir.
		* Añadir la ruta a "sdk\tools": `%ANDROID_HOME%\tools`
		* Añadir la ruta a "sdk\platform-tools": `%ANDROID_HOME%\platform-tools`
		* Añadir la ruta a "sdk\build-tools": `%ANDROID_HOME%\build-tools\29.0.2`
		* Click en Aceptar.
	* Haz click en la variable "Path".
		* Añadir (si no está ya añadida) la ruta a NPM: `C:\Users\tuUsuario\AppData\Roaming\npm`
		* Click en Aceptar.
* Cierra todo y **¡REINICIA EL ORDENADOR!**

### Test Variables de Entorno
* Abrir el CMD como administrador.
	* Ejecuta `C:\> java -version` en el CMD. Deberias ver algo así: `java version "1.8.0_231"`.
	* Ejecuta `C:\> npm`. Deberias ver el menu de opciones del npm.
	* Ejecuta `C:\> appium -v`. Deberias ver la versión de appium instalada anteriormente con Node (comando npm). Esta es la versión del Nodo de appium.
	* Si alguna de arriba no funciona deberás asegurarte de que las rutas de instalación están correctas y están anotadas correctamente en la variable de entorno "Path".

### Verificar que las Platform-tools están instaladas
* Ejecuta `C:\> adb` en el CMD. Deberias de ver que sale `Android Debug Bridge version 1.0.41` y opciones del menu adicionales.

### (OPCIONAL) Instalar Appium Desktop
* Descarga la última versión de la aplicación [aquí](https://github.com/appium/appium-desktop/releases)
