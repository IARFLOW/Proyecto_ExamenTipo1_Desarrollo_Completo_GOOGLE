# Guía Experta para la Preparación del Examen de Programación Multimedia de Dispositivos Móviles

## Índice

1. [Introducción](#introducción)
2. [Parte 1: Resolución Detallada del "ExamenTipo1.pdf"](#parte-1-resolución-detallada-del-examentipo1pdf)
   * [1.1. Análisis del Enunciado y Estructura del Proyecto](#11-análisis-del-enunciado-y-estructura-del-proyecto)
   * [1.2. Diseño de Interfaces (Pregunta 1)](#12-diseño-de-interfaces-pregunta-1)
   * [1.3. Implementación de Selección de Imágenes (Pregunta 2)](#13-implementación-de-selección-de-imágenes-pregunta-2)
   * [1.4. Gestión del Usuario Autenticado con Preferencias (Pregunta 3)](#14-gestión-del-usuario-autenticado-con-preferencias-pregunta-3)
   * [1.5. Integración con Base de Datos SQLite (Pregunta 4)](#15-integración-con-base-de-datos-sqlite-pregunta-4)
   * [1.6. Manejo de Errores y Feedback al Usuario](#16-manejo-de-errores-y-feedback-al-usuario)
   * [1.7. Fragmentos de Código Clave](#17-fragmentos-de-código-clave)
3. [Parte 2: Guía Metodológica Detallada para Afrontar y Realizar el Examen](#parte-2-guía-metodológica-detallada-para-afrontar-y-realizar-el-examen)
   * [2.1. Estrategia General y Preparación Previa al Examen](#21-estrategia-general-y-preparación-previa-al-examen)
   * [2.2. Durante el Examen: Enfoque Paso a Paso](#22-durante-el-examen-enfoque-paso-a-paso)
   * [2.3. Proceso de Desarrollo Práctico (usando "ExamenTipo1" como caso de estudio)](#23-proceso-de-desarrollo-práctico-usando-examentipo1-como-caso-de-estudio)
   * [2.4. Errores Comunes y Consejos Finales](#24-errores-comunes-y-consejos-finales)
4. [Conclusión](#conclusión)

## Introducción

Este informe ha sido concebido como una herramienta integral y detallada, diseñada para asistir en la preparación exhaustiva del examen de recuperación de la asignatura "Programación Multimedia de Dispositivos Móviles" (PMDM). El objetivo es proporcionar no solo soluciones técnicas a un examen tipo, sino también una metodología de estudio y afrontamiento del examen real, fomentando la confianza necesaria para superarlo con éxito.

Es fundamental realizar una aclaración importante respecto a los recursos inicialmente contemplados. Los repositorios de GitHub especificados en la consulta original (`IARFLOW/ExamenTipo1.git`, las guías de estudio bajo `IARFLOW/GUI-A-DE-ESTUDIO...`, `IARFLOW/EJFragments.git` y `IARFLOW/ExamenNoviembre.git`) resultaron inaccesibles durante la fase de investigación ([1, 2, 3, 4, 5]). En consecuencia, el contenido de este informe se fundamenta en:

  * La descripción pormenorizada de las preguntas y requisitos del "ExamenTipo1.pdf" proporcionada.
  * Los principios fundamentales y las mejores prácticas consolidadas en el desarrollo de aplicaciones Android, especialmente aquellas relevantes para el currículo de PMDM.
  * La estructura y los requisitos típicos que se suelen encontrar en los exámenes de PMDM, inferidos a partir de la descripción del "ExamenNoviembre\_Moviles.pdf".
  * La información útil extraída de los fragmentos de investigación que sí fueron accesibles, como el referente a los layouts en Android ([6]).

Esta situación, lejos de ser un impedimento, subraya la importancia crítica de dominar los conceptos fundamentales del desarrollo en Android. Cuando no es posible depender de un esqueleto de proyecto predefinido o de guías específicas del profesor, la comprensión profunda de los principios básicos de los componentes de Android (`Activity`, `Intent`, `SQLite`, `SharedPreferences`, gestión de archivos, etc.) se convierte en el pilar del éxito. Este informe, por lo tanto, se enfocará en construir y reforzar esa comprensión fundamental, ofreciendo explicaciones conceptuales detalladas junto con ejemplos de código aplicables.

El informe se divide en dos partes principales:

1.  **Resolución Detallada del "ExamenTipo1.pdf"**: Un desarrollo paso a paso de la aplicación propuesta en el examen tipo, simulando el proceso de creación desde la estructura del proyecto hasta la implementación de cada funcionalidad.
2.  **Guía Metodológica Exhaustiva para Afrontar el Examen**: Una estrategia detallada sobre cómo prepararse y cómo actuar el día del examen, desde la recepción del enunciado hasta la entrega final.

Con la dedicación adecuada y el uso de esta guía, se espera que el estudiante pueda afrontar el examen con una preparación sólida y una mayor seguridad en sus capacidades.

-----

## Parte 1: Resolución Detallada del "ExamenTipo1.pdf"

Esta sección abordará la implementación de la aplicación descrita en el "ExamenTipo1.pdf", siguiendo las especificaciones proporcionadas. Se detallará cada fase del desarrollo, desde la concepción inicial hasta la implementación de funcionalidades específicas.

### 1.1. Análisis del Enunciado y Estructura del Proyecto

Antes de escribir una sola línea de código, es crucial entender completamente los requisitos del examen y definir una estructura de proyecto sólida.

  * **Interpretación de las Preguntas del Examen:**
    Cada pregunta del "ExamenTipo1.pdf" debe ser desglosada para identificar los requisitos funcionales (qué debe hacer la aplicación) y técnicos (cómo debe implementarse). Es vital prestar atención a palabras clave como "guardar en preferencias", "usar streams para imágenes", "base de datos SQLite para usuarios", "comunicación entre activities", etc. Por ejemplo:

      * **Pregunta 1 (Interfaces):** Requiere la creación de layouts XML para tres pantallas (Principal, Login, Registro), con fidelidad a las imágenes proporcionadas y especificaciones de `inputType` para los `EditText`.
      * **Pregunta 2 (Selección de Imágenes):** Implica la creación de una nueva `Activity` para seleccionar un avatar, el uso de un `Adapter` para un `ListView`, la gestión de imágenes mediante `Streams` desde el almacenamiento interno, y la comunicación entre `Activities` para devolver la imagen seleccionada.
      * **Pregunta 3 (Gestión de Usuario con Preferencias):** Se centra en el uso de `SharedPreferences` para mantener el estado de la sesión del usuario (login e ID) y controlar el flujo de navegación.
      * **Pregunta 4 (Integración con Base de Datos SQLite):** Exige la definición de una tabla SQLite, la implementación de un `SQLiteOpenHelper`, y la creación de operaciones CRUD para el login, la visualización y modificación de datos del usuario, y el alta de nuevos usuarios, incluyendo el manejo de la imagen del avatar.
      * **Nota General (Errores y Feedback):** Indica la necesidad de manejar excepciones y proveer mensajes al usuario.

  * **Definición de Estructura de Proyecto Android:**
    Una estructura de proyecto bien organizada es fundamental, no solo para cumplir con las buenas prácticas, sino también para facilitar el desarrollo y la posterior revisión por parte del examinador. Aunque no se tenga acceso al repositorio base `ExamenTipo1.git` ([1]) ni al ejemplo del `ExamenNoviembre_Moviles.pdf` ([5]), se puede proponer una estructura estándar y robusta.

    Se sugiere la siguiente estructura de paquetes dentro de un proyecto Android Studio (usando, por ejemplo, `com.nombrealumno.examenpmdm` como paquete raíz):

      * `activities`: Contendrá las clases de las `Activity` (ej. `PrincipalActivity.kt`, `LoginActivity.kt`, `RegistroActivity.kt`, `AvatarSelectionActivity.kt`).
      * `adapters`: Para los adaptadores, como el que se usará para el `ListView` de selección de avatares (ej. `AvatarAdapter.kt`).
      * `database` (o `db`): Albergará la clase que herede de `SQLiteOpenHelper` (ej. `UserDbHelper.kt`) y, opcionalmente, clases DAO (Data Access Object) si se opta por un patrón de diseño más avanzado, aunque para un examen puede ser suficiente integrar las operaciones CRUD en el Helper o en las propias activities si la complejidad es baja.
      * `model` (o `entities`): Para las clases de datos o entidades que representan la información manejada por la aplicación (ej. `Usuario.kt`).
      * `utils` (o `helpers`): Para clases de utilidad general, como podría ser un gestor de `SharedPreferences` (ej. `SessionManager.kt`) o funciones auxiliares para el manejo de imágenes si la lógica se vuelve compleja.

    Además, los recursos de la aplicación se organizarán en las carpetas estándar proporcionadas por Android Studio:

      * `res/layout/`: Para los archivos XML que definen las interfaces de usuario.
      * `res/drawable/`: Para imágenes y otros elementos gráficos.
      * `res/values/`: Para `strings.xml`, `colors.xml`, `styles.xml`, etc.

  * **Justificación de la Estructura:**
    Esta organización promueve la **modularidad**, facilitando la localización de componentes específicos del código; la **mantenibilidad**, ya que los cambios en una parte del sistema tienen menos probabilidad de afectar a otras no relacionadas; y sigue las **convenciones comunes** en el desarrollo Android. Un proyecto bien estructurado no es solo una cuestión de estética, sino una demostración de profesionalismo y comprensión de las buenas prácticas de ingeniería de software. Bajo la presión de un examen, una estructura clara reduce la carga cognitiva, permite encontrar y modificar código más rápidamente y minimiza el riesgo de errores por confusión. Para el examinador, un proyecto ordenado es más fácil de evaluar y evidencia una planificación adecuada. Se recomienda crear esta estructura de paquetes al inicio del desarrollo en Android Studio.

### 1.2. Diseño de Interfaces (Pregunta 1)

La primera pregunta se centra en la creación de las interfaces de usuario (UI) de la aplicación. La fidelidad a las imágenes proporcionadas en "ExamenTipo1.pdf" es un requisito clave.

  * **Código XML para Layouts:**
    Se proporcionarán los lineamientos y fragmentos XML para las pantallas Principal, Login y Registro.

      * **Pantalla Principal (`activity_principal.xml`):**

          * Contendrá `TextViews` para mostrar el login del usuario (no editable, en la parte superior), nombre, email y teléfono (estos últimos en `EditTexts` para permitir su modificación).

          * Un `ImageView` para mostrar el avatar del usuario (en la parte superior, junto al login).

          * Un `Button` "Guardar Cambios" para persistir las modificaciones realizadas en los `EditTexts`.

          * Un `Button` "Cerrar Sesión".

          * Un `ConstraintLayout` sería adecuado aquí para posicionar los elementos de forma flexible, especialmente la cabecera con el avatar y el login, y luego los campos de datos.xml
            \<androidx.constraintlayout.widget.ConstraintLayout
            xmlns:android="[http://schemas.android.com/apk/res/android](https://www.google.com/url?sa=E&source=gmail&q=http://schemas.android.com/apk/res/android)"
            xmlns:app="[http://schemas.android.com/apk/res-auto](https://www.google.com/url?sa=E&source=gmail&q=http://schemas.android.com/apk/res-auto)"
            xmlns:tools="[http://schemas.android.com/tools](https://www.google.com/search?q=http://schemas.android.com/tools)"
            android:layout\_width="match\_parent"
            android:layout\_height="match\_parent"
            tools:context=".activities.PrincipalActivity"\>

            \<ImageView
            android:id="@+id/imgAvatarPrincipal"
            android:layout\_width="60dp"
            android:layout\_height="60dp"
            android:layout\_marginTop="16dp"
            android:layout\_marginStart="16dp"
            app:layout\_constraintTop\_toTopOf="parent"
            app:layout\_constraintStart\_toStartOf="parent"
            android:src="@drawable/ic\_avatar\_placeholder" /\>
            \<TextView
            android:id="@+id/tvLoginPrincipal"
            android:layout\_width="0dp"
            android:layout\_height="wrap\_content"
            android:layout\_marginStart="8dp"
            android:text="Login Usuario"
            android:textSize="18sp"
            app:layout\_constraintTop\_toTopOf="@id/imgAvatarPrincipal"
            app:layout\_constraintStart\_toEndOf="@id/imgAvatarPrincipal"
            app:layout\_constraintEnd\_toEndOf="parent"
            app:layout\_constraintBottom\_toBottomOf="@id/imgAvatarPrincipal"/\>

            \<EditText
            android:id="@+id/etNombrePrincipal"
            android:layout\_width="0dp"
            android:layout\_height="wrap\_content"
            android:layout\_marginTop="24dp"
            android:hint="Nombre"
            app:layout\_constraintTop\_toBottomOf="@id/imgAvatarPrincipal"
            app:layout\_constraintStart\_toStartOf="parent"
            app:layout\_constraintEnd\_toEndOf="parent"
            android:layout\_marginStart="16dp"
            android:layout\_marginEnd="16dp"
            android:inputType="textPersonName"/\>

            \<EditText
            android:id="@+id/etEmailPrincipal"
            android:layout\_width="0dp"
            android:layout\_height="wrap\_content"
            android:hint="Email"
            app:layout\_constraintTop\_toBottomOf="@id/etNombrePrincipal"
            app:layout\_constraintStart\_toStartOf="parent"
            app:layout\_constraintEnd\_toEndOf="parent"
            android:layout\_marginStart="16dp"
            android:layout\_marginEnd="16dp"
            android:layout\_marginTop="8dp"
            android:inputType="textEmailAddress"/\>

            \<EditText
            android:id="@+id/etTelefonoPrincipal"
            android:layout\_width="0dp"
            android:layout\_height="wrap\_content"
            android:hint="Teléfono"
            app:layout\_constraintTop\_toBottomOf="@id/etEmailPrincipal"
            app:layout\_constraintStart\_toStartOf="parent"
            app:layout\_constraintEnd\_toEndOf="parent"
            android:layout\_marginStart="16dp"
            android:layout\_marginEnd="16dp"
            android:layout\_marginTop="8dp"
            android:inputType="phone"/\>

            \<Button
            android:id="@+id/btnGuardarCambiosPrincipal"
            android:layout\_width="wrap\_content"
            android:layout\_height="wrap\_content"
            android:text="Guardar Cambios"
            app:layout\_constraintBottom\_toTopOf="@id/btnCerrarSesionPrincipal"
            app:layout\_constraintStart\_toStartOf="parent"
            app:layout\_constraintEnd\_toEndOf="parent"
            android:layout\_marginBottom="16dp"/\>

            \<Button
            android:id="@+id/btnCerrarSesionPrincipal"
            android:layout\_width="wrap\_content"
            android:layout\_height="wrap\_content"
            android:text="Cerrar Sesión"
            app:layout\_constraintBottom\_toBottomOf="parent"
            app:layout\_constraintStart\_toStartOf="parent"
            app:layout\_constraintEnd\_toEndOf="parent"
            android:layout\_marginBottom="32dp"/\>

        \</androidx.constraintlayout.widget.ConstraintLayout\>

        ```
        
        ```

      * **Pantalla de Login (`activity_login.xml`):**

          * Dos `EditText` para el login y la contraseña.
          * Un `Button` "Login".
          * Un `TextView` o `Button` "Registrarse aquí" para navegar a la pantalla de registro.
          * Un `LinearLayout` con orientación vertical puede ser suficiente para esta pantalla.

        <!-- end list -->

        ```xml
        <LinearLayout
            xmlns:android="[https://www.google.com/url?sa=E&source=gmail&q=http://schemas.android.com/apk/res/android](https://www.google.com/url?sa=E&source=gmail&q=http://schemas.android.com/apk/res/android)"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:orientation="vertical"
            android:padding="16dp"
            android:gravity="center">

            <EditText
                android:id="@+id/etLoginUsuario"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:hint="Login"
                android:inputType="text"
                android:layout_marginBottom="8dp"/>

            <EditText
                android:id="@+id/etLoginPassword"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:hint="Contraseña"
                android:inputType="textPassword"
                android:layout_marginBottom="16dp"/>

            <Button
                android:id="@+id/btnLogin"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Login"
                android:layout_marginBottom="24dp"/>

            <TextView
                android:id="@+id/tvIrARegistro"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="¿No tienes cuenta? Regístrate aquí"
                android:textColor="@android:color/holo_blue_dark" />
        </LinearLayout>
        ```

      * **Pantalla de Registro de Usuarios (`activity_registro.xml`):**

          * `EditTexts` para login, contraseña, nombre, email y teléfono.
          * Un `ImageView` para mostrar el avatar seleccionado (inicialmente un placeholder).
          * Un `Button` "Seleccionar Avatar" para lanzar la `Activity` de selección de imágenes.
          * Un `Button` "Registrar" para guardar el nuevo usuario.
          * Aquí también, `ConstraintLayout` puede ser útil para organizar el `ImageView` junto al botón de selección y los campos de texto.

        <!-- end list -->

        ```xml
        <androidx.constraintlayout.widget.ConstraintLayout
            xmlns:android="[https://www.google.com/url?sa=E&source=gmail&q=http://schemas.android.com/apk/res/android](https://www.google.com/url?sa=E&source=gmail&q=http://schemas.android.com/apk/res/android)"
            xmlns:app="[https://www.google.com/url?sa=E&source=gmail&q=http://schemas.android.com/apk/res-auto](https://www.google.com/url?sa=E&source=gmail&q=http://schemas.android.com/apk/res-auto)"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:padding="16dp">

            <ImageView
                android:id="@+id/imgAvatarRegistro"
                android:layout_width="100dp"
                android:layout_height="100dp"
                android:src="@drawable/ic_avatar_placeholder"
                app:layout_constraintTop_toTopOf="parent"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintEnd_toEndOf="parent"
                android:layout_marginTop="16dp"/>

            <Button
                android:id="@+id/btnSeleccionarAvatarRegistro"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Seleccionar Avatar"
                app:layout_constraintTop_toBottomOf="@id/imgAvatarRegistro"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintEnd_toEndOf="parent"
                android:layout_marginTop="8dp"/>

            <EditText
                android:id="@+id/etLoginRegistro"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:hint="Login"
                android:inputType="text"
                app:layout_constraintTop_toBottomOf="@id/btnSeleccionarAvatarRegistro"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintEnd_toEndOf="parent"
                android:layout_marginTop="16dp"/>

            <EditText
                android:id="@+id/etPasswordRegistro"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:hint="Contraseña"
                android:inputType="textPassword"
                app:layout_constraintTop_toBottomOf="@id/etLoginRegistro"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintEnd_toEndOf="parent"
                android:layout_marginTop="8dp"/>
            
            <EditText
                android:id="@+id/etNombreRegistro"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:hint="Nombre"
                android:inputType="textPersonName"
                app:layout_constraintTop_toBottomOf="@id/etPasswordRegistro"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintEnd_toEndOf="parent"
                android:layout_marginTop="8dp"/>

            <EditText
                android:id="@+id/etEmailRegistro"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:hint="Email"
                android:inputType="textEmailAddress"
                app:layout_constraintTop_toBottomOf="@id/etNombreRegistro"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintEnd_toEndOf="parent"
                android:layout_marginTop="8dp"/>
            
            <EditText
                android:id="@+id/etTelefonoRegistro"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:hint="Teléfono"
                android:inputType="phone"
                app:layout_constraintTop_toBottomOf="@id/etEmailRegistro"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintEnd_toEndOf="parent"
                android:layout_marginTop="8dp"/>

            <Button
                android:id="@+id/btnRegistrarUsuario"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Registrar"
                app:layout_constraintBottom_toBottomOf="parent"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintEnd_toEndOf="parent"
                android:layout_marginBottom="32dp"/>

        </androidx.constraintlayout.widget.ConstraintLayout>
        ```

  * **Elección de Layouts Contenedores:**
    Como se observa en los ejemplos, la elección entre `LinearLayout` y `ConstraintLayout` depende de la complejidad de la interfaz. `LinearLayout` es sencillo para apilar vistas en una dirección. `ConstraintLayout`, el layout por defecto al crear nuevas Activities en Android Studio ([6]), ofrece una gran flexibilidad para crear interfaces planas y responsivas, permitiendo posicionar elementos en relación con otros o con el contenedor padre mediante restricciones. Para lograr una alta fidelidad con las imágenes de muestra del examen, especialmente si tienen elementos posicionados de forma no lineal, `ConstraintLayout` suele ser la mejor opción.

  * **Atributos XML Clave:**
    Es importante utilizar correctamente atributos XML comunes como:

      * `android:id`: Para identificar unívocamente cada vista y poder referenciarla desde el código Kotlin/Java.
      * `android:layout_width`, `android:layout_height`: Para definir las dimensiones (`match_parent`, `wrap_content`, o un valor fijo en `dp`).
      * `android:text`: Para el texto visible en `TextViews` y `Buttons`.
      * `android:hint`: Para el texto de ayuda en `EditTexts`.
      * `android:src`: Para especificar la imagen en un `ImageView`.
      * `android:padding`: Espacio interno dentro de una vista.
      * `android:layout_margin`: Espacio externo alrededor de una vista.
      * `app:layout_constraintTop_toTopOf`, `app:layout_constraintStart_toEndOf`, etc. (para `ConstraintLayout`).

  * **Especificaciones para `inputType` en `EditTexts`:**
    Asegurar el `inputType` correcto para cada `EditText` es crucial para la usabilidad, ya que influye en el tipo de teclado que se muestra al usuario y puede habilitar ciertas validaciones o formatos de entrada.

      * Login (`etLoginUsuario`, `etLoginRegistro`): `android:inputType="text"`
      * Contraseña (`etLoginPassword`, `etPasswordRegistro`): `android:inputType="textPassword"` (oculta los caracteres)
      * Email (`etEmailPrincipal`, `etEmailRegistro`): `android:inputType="textEmailAddress"` (teclado con '@' y '.')
      * Teléfono (`etTelefonoPrincipal`, `etTelefonoRegistro`): `android:inputType="phone"` (teclado numérico)
      * Nombre (`etNombrePrincipal`, `etNombreRegistro`): `android:inputType="textPersonName"` (puede capitalizar nombres)

    La fidelidad visual con las imágenes del examen no es solo una cuestión estética; demuestra atención al detalle y la capacidad de traducir un diseño en una implementación funcional. El uso correcto de `inputType` es una expectativa básica de una buena experiencia de usuario (UX). Por ello, se debe dedicar tiempo a ajustar los layouts y verificar estos atributos antes de avanzar a la lógica más compleja.

### 1.3. Implementación de Selección de Imágenes (Pregunta 2)

Esta pregunta aborda la selección de un avatar para el usuario, involucrando la gestión de archivos, la creación de una `Activity` específica, el uso de un `Adapter` y la comunicación entre `Activities`.

  * **Creación de Carpeta `files` Interna y Copia de Imágenes de Muestra:**
    El almacenamiento interno de la aplicación es un espacio privado donde se pueden guardar archivos. La carpeta `files` se accede mediante `context.getFilesDir()`.
    Para las imágenes de muestra (1.png, 2.png, 3.png) que se usarán en la `Activity` de selección de avatar:

    1.  **Durante el desarrollo/prueba:** La forma más sencilla es copiarlas manualmente a la carpeta `files` de la aplicación en el emulador o dispositivo. Esto se puede hacer usando el "Device File Explorer" en Android Studio (View \> Tool Windows \> Device File Explorer), navegando a `/data/data/com.nombrealumno.examenpmdm/files/` y subiendo los archivos allí.
    2.  **Para una aplicación distribuible (o si se prefiere una solución programática):** Las imágenes se podrían incluir en la carpeta `res/raw` o `assets/` del proyecto. Luego, la primera vez que se necesiten (o al iniciar la app), se copiarían mediante código a `context.getFilesDir()`. Esto asegura que las imágenes estén disponibles.
        ```kotlin
        // Ejemplo de copia de un archivo desde res/raw a filesDir
        private fun copyImageToInternalStorage(resourceId: Int, fileName: String) {
            val internalFile = File(filesDir, fileName)
            if (!internalFile.exists()) {
                try {
                    val inputStream: InputStream = resources.openRawResource(resourceId)
                    val outputStream: FileOutputStream = openFileOutput(fileName, Context.MODE_PRIVATE)
                    inputStream.use { input ->
                        outputStream.use { output ->
                            input.copyTo(output)
                        }
                    }
                } catch (e: IOException) {
                    Log.e("ImageCopy", "Error copying image $fileName", e)
                    // Mostrar Toast de error
                }
            }
        }
        // Llamar a esta función para cada imagen:
        // copyImageToInternalStorage(R.raw.image1, "1.png")
        // copyImageToInternalStorage(R.raw.image2, "2.png")
        // copyImageToInternalStorage(R.raw.image3, "3.png")
        ```

    Para el contexto de un examen, si el tiempo es limitado, la copia manual o una simulación de que los archivos ya existen en `filesDir` podría ser aceptable, pero es bueno conocer la forma programática.

  * **`Activity` de Selección de Avatar (`AvatarSelectionActivity`) y `Adapter` para `ListView`:**

      * Se creará una nueva `Activity` llamada `AvatarSelectionActivity.kt` (o `.java`).
      * Su layout (`activity_avatar_selection.xml`) contendrá principalmente un `ListView` para mostrar las imágenes disponibles y dos `Button` ("Aceptar" y "Cancelar").
      * Se creará un `AvatarAdapter` (que puede extender `ArrayAdapter<AvatarItem>` o `BaseAdapter`). Este adapter será responsable de inflar un layout de ítem personalizado (ej. `list_item_avatar.xml`) para cada imagen en el `ListView`. Dicho layout de ítem contendrá un `ImageView` para el avatar y un `TextView` para mostrar el nombre del archivo de imagen (ej. "1.png").
      * El adapter necesitará una lista de objetos que representen cada avatar. Se puede crear una clase de datos simple:
        ```kotlin
        data class AvatarItem(val name: String, val filePath: String) // O val imageBitmap: Bitmap
        ```
      * El adapter cargará las imágenes desde `filesDir` (usando el `filePath`) y las mostrará.

    <!-- end list -->

    ```xml
    <LinearLayout xmlns:android="[https://www.google.com/url?sa=E&source=gmail&q=http://schemas.android.com/apk/res/android](https://www.google.com/url?sa=E&source=gmail&q=http://schemas.android.com/apk/res/android)"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:padding="8dp">

        <ImageView
            android:id="@+id/imgAvatarItem"
            android:layout_width="50dp"
            android:layout_height="50dp"
            android:scaleType="centerCrop"/>

        <TextView
            android:id="@+id/tvAvatarNameItem"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_gravity="center_vertical"
            android:layout_marginStart="16dp"
            android:textSize="16sp"/>
    </LinearLayout>
    ```

  * **Lógica de Selección y Cancelación:**

      * El `ListView` en `AvatarSelectionActivity` tendrá un `OnItemClickListener` (o se manejará la selección dentro del adapter) para que el usuario pueda seleccionar un avatar. Se puede resaltar visualmente el ítem seleccionado.
      * **Botón "Aceptar":** Cuando se pulse, se obtendrá la información del avatar seleccionado (principalmente su ruta de archivo o nombre de archivo). Esta información se empaquetará en un `Intent` y se devolverá a la `Activity` de registro.
      * **Botón "Cancelar":** Simplemente finalizará `AvatarSelectionActivity` sin devolver ningún dato, indicando que la operación fue cancelada.
      * **Reflejo en Pantalla de Alta (`RegistroActivity`):** Al regresar a `RegistroActivity` después de una selección exitosa, se recibirá la ruta de la imagen seleccionada. Con esta ruta, se cargará la imagen desde el almacenamiento interno y se mostrará en el `ImageView` destinado al avatar en la pantalla de registro.

  * **Gestión de Imágenes mediante `Streams`:**
    El enunciado especifica el uso de `Streams` para la gestión de imágenes.

      * **Lectura desde `filesDir`:** Para poblar el `ListView` en `AvatarSelectionActivity`, se listarán los archivos de imagen (ej. "1.png", "2.png", "3.png") de la carpeta `context.getFilesDir()`. Para cada archivo:
        1.  Se creará un `File` object: `val imageFile = File(context.getFilesDir(), imageName)`
        2.  Se abrirá un `FileInputStream` para ese archivo: `val fis = FileInputStream(imageFile)`
        3.  Se decodificará el stream en un `Bitmap`: `val bitmap = BitmapFactory.decodeStream(fis)`
        4.  Se cerrará el stream: `fis.close()` (o usar `fis.use {... }` en Kotlin para cierre automático).
            Estos `Bitmap` (o sus rutas si se prefiere cargar bajo demanda en el adapter) se usarán para poblar el `AvatarAdapter`.
      * **Paso de Datos de la Imagen Seleccionada:**
        Cuando el usuario selecciona un avatar y pulsa "Aceptar" en `AvatarSelectionActivity`, se debe devolver esta selección a `RegistroActivity`. La forma más eficiente y recomendada es **pasar la ruta del archivo (`String`) de la imagen seleccionada**. `RegistroActivity` luego usará esta ruta para leer el archivo de imagen desde `filesDir` (usando `FileInputStream` y `BitmapFactory.decodeStream()`) y mostrarlo.
        Evitar pasar el `Bitmap` directamente como `ByteArray` en el `Intent` si las imágenes son grandes, ya que los `Intent` tienen un límite de tamaño para los extras. Si se requiere pasar como `ByteArray` (por ejemplo, para guardarlo como `BLOB` en la BD directamente), se leería el archivo a un `ByteArrayOutputStream` y luego a un `ByteArray`.

  * **Comunicación entre `Activities` (Intents y `ActivityResultLauncher`):**
    Para lanzar `AvatarSelectionActivity` desde `RegistroActivity` y recibir un resultado (la ruta de la imagen seleccionada), se utilizará el mecanismo moderno `ActivityResultLauncher`. Este reemplaza al antiguo `startActivityForResult`/`onActivityResult`.

      * **En `RegistroActivity.kt`:**

        ```kotlin
        // Declarar el launcher como una variable miembro de la Activity
        private lateinit var selectedAvatarPath: String // Para guardar la ruta devuelta

        val selectAvatarLauncher = registerForActivityResult(ActivityResultContracts.StartActivityForResult()) { result ->
            if (result.resultCode == Activity.RESULT_OK) {
                val data: Intent? = result.data
                data?.getStringExtra("selectedAvatarPathKey")?.let { path ->
                    selectedAvatarPath = path // Guardar la ruta
                    // Cargar la imagen desde 'path' y mostrarla en el ImageView de RegistroActivity
                    try {
                        val file = File(path)
                        if (file.exists()) {
                            val bitmap = BitmapFactory.decodeStream(FileInputStream(file))
                            findViewById<ImageView>(R.id.imgAvatarRegistro).setImageBitmap(bitmap)
                            Toast.makeText(this, "Avatar seleccionado: ${file.name}", Toast.LENGTH_SHORT).show()
                        }
                    } catch (e: Exception) {
                        Log.e("AvatarLoad", "Error loading avatar", e)
                        Toast.makeText(this, "Error al cargar avatar", Toast.LENGTH_SHORT).show()
                    }
                }
            } else if (result.resultCode == Activity.RESULT_CANCELED) {
                Toast.makeText(this, "Selección de avatar cancelada", Toast.LENGTH_SHORT).show()
            }
        }

        // En el OnClickListener del botón "Seleccionar Avatar"
        // findViewById<Button>(R.id.btnSeleccionarAvatarRegistro).setOnClickListener {
        //    val intent = Intent(this, AvatarSelectionActivity::class.java)
        //    selectAvatarLauncher.launch(intent)
        // }
        ```

      * **En `AvatarSelectionActivity.kt`:**
        Al pulsar el botón "Aceptar" (suponiendo que `pathDelAvatarSeleccionado` contiene la ruta completa al archivo de imagen elegido):

        ```kotlin
        // private var pathDelAvatarSeleccionado: String? = null
        //...lógica para que el usuario seleccione un avatar y se guarde su path en pathDelAvatarSeleccionado...

        // En el OnClickListener del botón "Aceptar"
        // findViewById<Button>(R.id.btnAceptarAvatar).setOnClickListener {
        //    pathDelAvatarSeleccionado?.let { path ->
        //        val returnIntent = Intent()
        //        returnIntent.putExtra("selectedAvatarPathKey", path)
        //        setResult(Activity.RESULT_OK, returnIntent)
        //        finish() // Cierra AvatarSelectionActivity y vuelve a RegistroActivity
        //    }?: run {
        //        Toast.makeText(this, "Por favor, selecciona un avatar", Toast.LENGTH_SHORT).show()
        //    }
        // }
        ```

        Al pulsar el botón "Cancelar":

        ```kotlin
        // En el OnClickListener del botón "Cancelar"
        // findViewById<Button>(R.id.btnCancelarAvatar).setOnClickListener {
        //    setResult(Activity.RESULT_CANCELED)
        //    finish()
        // }
        ```

    El manejo de archivos y la comunicación efectiva entre actividades son habilidades fundamentales. `ActivityResultLauncher` no solo es la forma moderna, sino que también mejora la legibilidad y reduce el acoplamiento en comparación con el antiguo `onActivityResult`. El uso de `Streams` es esencial para el manejo de datos binarios como imágenes, y comprender la diferencia entre pasar una referencia (ruta de archivo) y el dato completo (Bitmap/ByteArray) es importante para la eficiencia de la aplicación.

### 1.4. Gestión del Usuario Autenticado con Preferencias (Pregunta 3)

Esta pregunta se enfoca en mantener el estado de la sesión del usuario (si está o no logueado) utilizando `SharedPreferences`.

  * **Uso de `SharedPreferences`:**
    `SharedPreferences` es un mecanismo de Android para almacenar pequeñas cantidades de datos primitivos en pares clave-valor de forma persistente. Es ideal para guardar preferencias de usuario, configuraciones o, como en este caso, información de sesión.

      * Se puede crear una clase de utilidad (ej. `SessionManager.kt`) para encapsular la lógica de acceso a `SharedPreferences`, o bien acceder directamente desde las `Activities` si la lógica es simple. Para un examen, el acceso directo puede ser más rápido de implementar.
      * **Nombre del archivo de preferencias:** Se usará un nombre único, por ejemplo, `"PREFS_SESION_USUARIO"`.
      * **Claves para los datos:** Se definirán constantes para las claves, ej. `"KEY_USER_LOGIN"` (para el login del usuario) y `"KEY_USER_ID"` (para el ID del usuario en la base de datos).

  * **Flujo Lógico Detallado:**

    1.  **Inicio de la Aplicación (en una `SplashActivity` o en la `MainActivity` si actúa como punto de entrada principal):**

          * En el método `onCreate()` de la `Activity` inicial:
              * Acceder a `SharedPreferences`: `val prefs = getSharedPreferences("PREFS_SESION_USUARIO", Context.MODE_PRIVATE)`
              * Verificar si existe un `KEY_USER_ID` válido (ej. que no sea el valor por defecto como -1 si es un `Int` o `Long`).
              * **Si hay un `ID` de usuario guardado:**
                  * Navegar directamente a `PrincipalActivity`.
                  * Es buena práctica pasar el `ID` del usuario a `PrincipalActivity` a través del `Intent`, aunque `PrincipalActivity` también podría leerlo de `SharedPreferences` directamente.
                  * Finalizar la `Activity` actual (si es una `SplashActivity`) para que no quede en la pila de actividades: `finish()`.
              * **Si no hay `ID` de usuario guardado:**
                  * Navegar a `LoginActivity`.
                  * Finalizar la `Activity` actual (si es una `SplashActivity`): `finish()`.

    2.  **`LoginActivity`:**

          * Cuando el usuario introduce sus credenciales y pulsa el botón "Login":
              * Se realiza la autenticación (inicialmente simulada, luego contra la base de datos SQLite como se verá en la Pregunta 4).
              * **Si la autenticación es exitosa:**
                  * Se obtiene el `login` y el `ID` del usuario autenticado.
                  * Se guardan estos datos en `SharedPreferences`:
                    ```kotlin
                    // Dentro de LoginActivity, tras autenticación exitosa
                    // val userId: Int =... // ID obtenido de la BD o simulación
                    // val userLogin: String =... // Login del usuario

                    val prefs = getSharedPreferences("PREFS_SESION_USUARIO", Context.MODE_PRIVATE)
                    val editor = prefs.edit()
                    editor.putString("KEY_USER_LOGIN", userLogin)
                    editor.putInt("KEY_USER_ID", userId) // Usar putLong si el ID es Long
                    editor.apply() // apply() es asíncrono y preferido sobre commit()
                    ```
                  * Navegar a `PrincipalActivity`.
                  * Finalizar `LoginActivity` para que el usuario no pueda volver a ella usando el botón "Atrás": `finish()`.
              * **Si la autenticación falla:**
                  * Mostrar un mensaje de error al usuario (ej. un `Toast` "Login o contraseña incorrectos").

    3.  **`PrincipalActivity`:**

          * En `onCreate()`:
              * Leer el `ID` y el `login` del usuario desde `SharedPreferences`:
                ```kotlin
                val prefs = getSharedPreferences("PREFS_SESION_USUARIO", Context.MODE_PRIVATE)
                val userId = prefs.getInt("KEY_USER_ID", -1) // -1 como valor por defecto si no se encuentra
                val userLogin = prefs.getString("KEY_USER_LOGIN", null)

                if (userId == -1 |
                ```

| userLogin == null) {
// No debería ocurrir si el flujo de inicio es correcto, pero por seguridad:
// Redirigir a LoginActivity y finalizar PrincipalActivity
startActivity(Intent(this, LoginActivity::class.java))
finish()
return // Importante para no continuar ejecutando el onCreate
}
// Usar userId para cargar datos completos del usuario desde la BD (Pregunta 4)
// Usar userLogin para mostrarlo en la UI (ej. en un TextView de bienvenida)
// findViewById\<TextView\>(R.id.tvLoginPrincipal).text = userLogin
\`\`\`
\*   Los datos leídos (especialmente el `ID`) se usarán para cargar la información completa del usuario desde la base de datos SQLite y mostrarla en los campos correspondientes. El \`login\` y el avatar se mostrarán en la parte superior de la pantalla.

````
4.  **Cerrar Sesión (Botón en `PrincipalActivity`):**
    *   Cuando el usuario pulsa el botón "Cerrar Sesión":
        *   Limpiar los datos de sesión de `SharedPreferences`:
            ```kotlin
            val prefs = getSharedPreferences("PREFS_SESION_USUARIO", Context.MODE_PRIVATE)
            val editor = prefs.edit()
            editor.clear() // Elimina todas las claves y valores de este archivo de preferencias
            editor.apply()
            ```
        *   Navegar de vuelta a `LoginActivity`.
        *   Finalizar `PrincipalActivity` para que no quede en la pila: `finish()`.

`SharedPreferences` ofrece una forma sencilla y eficiente de gestionar el estado de sesión. Es crucial que el flujo de navegación entre `Activities` sea robusto para asegurar que el usuario solo pueda acceder a las pantallas permitidas según su estado de autenticación. El uso adecuado de `finish()` después de las navegaciones (ej. de `Login` a `Principal`, o de `Principal` a `Login` tras cerrar sesión) es vital para gestionar correctamente la pila de actividades y el comportamiento del botón "Atrás" del dispositivo. Este patrón de gestión de sesión es muy común y fundamental en el desarrollo de aplicaciones móviles.
````

### 1.5. Integración con Base de Datos SQLite (Pregunta 4)

Esta pregunta requiere el uso de una base de datos SQLite para almacenar y gestionar los datos de los usuarios de forma persistente.

  * **Definición de la(s) Tabla(s) SQLite:**
    Se propondrá una única tabla llamada `Usuarios` para almacenar la información de los usuarios. Es crucial definir claramente las columnas, sus tipos de datos y cualquier restricción.

    **Tabla: `Usuarios`**

| Columna | Tipo de Dato SQL | Restricciones | Descripción |
|---------------|-------------------------|-----------------------------|-------------------------------------------------|
| `id` | `INTEGER` | `PRIMARY KEY AUTOINCREMENT` | Identificador único del usuario (autonumérico) |
| `login` | `TEXT` | `UNIQUE NOT NULL` | Login del usuario (único y obligatorio) |
| `password` | `TEXT` | `NOT NULL` | Contraseña del usuario (obligatoria) |
| `nombre` | `TEXT` | | Nombre completo del usuario |
| `email` | `TEXT` | `UNIQUE` | Email del usuario (único) |
| `telefono` | `TEXT` | | Número de teléfono del usuario |
| `path_avatar` | `TEXT` | | Ruta al archivo de imagen del avatar en el almacenamiento interno de la app |

```
*   **Nota sobre el Almacenamiento de la Imagen del Avatar:**
    Existen dos enfoques principales para manejar la imagen del avatar en relación con la base de datos:
    1.  **Almacenar la Ruta (`path_avatar TEXT` - Recomendado):** En esta aproximación, la imagen del avatar se guarda como un archivo físico en el almacenamiento interno de la aplicación (por ejemplo, en `context.getFilesDir()`, como se gestionó en la Pregunta 2). En la base de datos, en la columna `path_avatar`, se almacena únicamente la ruta (`String`) a este archivo. Este método mantiene la base de datos más ligera y ágil, ya que no almacena datos binarios grandes directamente. La carga y guardado de la imagen se maneja a nivel de sistema de archivos.
    2.  **Almacenar como BLOB (`avatar_blob BLOB`):** Alternativamente, la imagen podría convertirse en un array de bytes (`ByteArray`) y almacenarse directamente en una columna de tipo `BLOB` (Binary Large Object) en la tabla `Usuarios`. Esto puede simplificar la lógica de datos al tener toda la información del usuario en un solo lugar, pero puede hacer que la base de datos crezca considerablemente si las imágenes son grandes, lo que podría afectar al rendimiento.
    **Para este examen, se optará por el enfoque de `path_avatar TEXT`**, ya que suele ser la práctica más recomendada para imágenes. Si el enunciado del examen especificara explícitamente el uso de `BLOB`, se debería seguir esa indicación.
```

  * **Código de la Clase `SQLiteOpenHelper`:**
    Se creará una clase (ej. `UserDbHelper.kt`) que herede de `SQLiteOpenHelper`. Esta clase gestiona la creación de la base de datos y las tablas si no existen, y también maneja las actualizaciones de esquema (versiones de la BD).

    ```kotlin
    // En el paquete database (o db)
    // UserDbHelper.kt
    import android.content.ContentValues
    import android.content.Context
    import android.database.sqlite.SQLiteDatabase
    import android.database.sqlite.SQLiteOpenHelper
    import com.nombrealumno.examenpmdm.model.Usuario // Asumiendo una clase de datos Usuario

    class UserDbHelper(context: Context) : SQLiteOpenHelper(context, DATABASE_NAME, null, DATABASE_VERSION) {

        companion object {
            private const val DATABASE_VERSION = 1
            private const val DATABASE_NAME = "Usuarios.db"

            // Definición de la tabla Usuarios y sus columnas
            const val TABLE_USUARIOS = "Usuarios"
            const val COLUMN_ID = "id"
            const val COLUMN_LOGIN = "login"
            const val COLUMN_PASSWORD = "password" // En una app real, NUNCA guardar passwords en texto plano. Usar HASHES.
            const val COLUMN_NOMBRE = "nombre"
            const val COLUMN_EMAIL = "email"
            const val COLUMN_TELEFONO = "telefono"
            const val COLUMN_PATH_AVATAR = "path_avatar"
        }

        override fun onCreate(db: SQLiteDatabase?) {
            val CREATE_USUARIOS_TABLE = ("CREATE TABLE " + TABLE_USUARIOS + "("
                    + COLUMN_ID + " INTEGER PRIMARY KEY AUTOINCREMENT,"
                    + COLUMN_LOGIN + " TEXT UNIQUE NOT NULL,"
                    + COLUMN_PASSWORD + " TEXT NOT NULL,"
                    + COLUMN_NOMBRE + " TEXT,"
                    + COLUMN_EMAIL + " TEXT UNIQUE,"
                    + COLUMN_TELEFONO + " TEXT,"
                    + COLUMN_PATH_AVATAR + " TEXT" + ")")
            db?.execSQL(CREATE_USUARIOS_TABLE)
        }

        override fun onUpgrade(db: SQLiteDatabase?, oldVersion: Int, newVersion: Int) {
            // Política de actualización simple: borrar la tabla y crearla de nuevo.
            // En una app real, se necesitaría una migración de datos más sofisticada.
            db?.execSQL("DROP TABLE IF EXISTS $TABLE_USUARIOS")
            onCreate(db)
        }

        // Aquí se pueden añadir los métodos CRUD o ponerlos en una clase DAO separada.
        // Por simplicidad para el examen, se pueden incluir aquí.
    }
    ```

  * **Operaciones CRUD (Crear, Leer, Actualizar, Borrar) en Kotlin/Java:**
    Estas operaciones se implementarán como métodos dentro de `UserDbHelper` o en una clase DAO dedicada.

      * **Alta de Usuario (CREATE):** Guardar un nuevo usuario en la tabla `Usuarios`.

        ```kotlin
        // Dentro de UserDbHelper.kt
        fun addUser(usuario: Usuario): Long { // Suponiendo que Usuario tiene todos los campos
            val values = ContentValues().apply {
                put(COLUMN_LOGIN, usuario.login)
                put(COLUMN_PASSWORD, usuario.password) // Recordar: ¡hashear en producción!
                put(COLUMN_NOMBRE, usuario.nombre)
                put(COLUMN_EMAIL, usuario.email)
                put(COLUMN_TELEFONO, usuario.telefono)
                put(COLUMN_PATH_AVATAR, usuario.pathAvatar)
            }
            val db = this.writableDatabase
            val id = db.insert(TABLE_USUARIOS, null, values)
            // db.close() // No cerrar aquí si se va a usar el helper múltiples veces seguidas. Gestionar la apertura/cierre a nivel de Activity o Fragment.
            return id // Devuelve el ID del nuevo usuario o -1 si hay error
        }
        ```

        **Nota sobre `path_avatar` y `BLOB`:** Si se usara `BLOB`, la imagen (como `ByteArray`) se añadiría a `ContentValues` con `put(COLUMN_AVATAR_BLOB, byteArray)`. La imagen ya se habría guardado en el almacenamiento interno (Pregunta 2) y aquí solo se guarda su ruta.

      * **Login (READ):** Consultar un usuario por su `login` y `password`.

        ```kotlin
        // Dentro de UserDbHelper.kt
        fun getUserByLoginAndPassword(login: String, password: String): Usuario? {
            val db = this.readableDatabase
            // ¡PRECAUCIÓN! En una app real, la contraseña en la BD estaría hasheada.
            // La consulta compararía el hash del password introducido con el hash almacenado.
            // Para el examen, se asume texto plano si no se indica lo contrario.
            val query = "SELECT * FROM $TABLE_USUARIOS WHERE $COLUMN_LOGIN =? AND $COLUMN_PASSWORD =?"
            val cursor = db.rawQuery(query, arrayOf(login, password))
            var usuario: Usuario? = null

            if (cursor.moveToFirst()) {
                val id = cursor.getInt(cursor.getColumnIndexOrThrow(COLUMN_ID))
                val userLogin = cursor.getString(cursor.getColumnIndexOrThrow(COLUMN_LOGIN))
                // No es necesario leer el password aquí usualmente
                val nombre = cursor.getString(cursor.getColumnIndexOrThrow(COLUMN_NOMBRE))
                val email = cursor.getString(cursor.getColumnIndexOrThrow(COLUMN_EMAIL))
                val telefono = cursor.getString(cursor.getColumnIndexOrThrow(COLUMN_TELEFONO))
                val pathAvatar = cursor.getString(cursor.getColumnIndexOrThrow(COLUMN_PATH_AVATAR))
                
                usuario = Usuario(id, userLogin, "", nombre, email, telefono, pathAvatar) // Password vacío o no relevante aquí
            }
            cursor.close()
            // db.close()
            return usuario
        }
        ```

      * **Obtener Datos del Usuario por ID (READ - para `PrincipalActivity`):**

        ```kotlin
        // Dentro de UserDbHelper.kt
        fun getUserById(userId: Int): Usuario? {
            val db = this.readableDatabase
            val query = "SELECT * FROM $TABLE_USUARIOS WHERE $COLUMN_ID =?"
            val cursor = db.rawQuery(query, arrayOf(userId.toString()))
            var usuario: Usuario? = null

            if (cursor.moveToFirst()) {
                val login = cursor.getString(cursor.getColumnIndexOrThrow(COLUMN_LOGIN))
                // No es necesario leer el password aquí
                val nombre = cursor.getString(cursor.getColumnIndexOrThrow(COLUMN_NOMBRE))
                val email = cursor.getString(cursor.getColumnIndexOrThrow(COLUMN_EMAIL))
                val telefono = cursor.getString(cursor.getColumnIndexOrThrow(COLUMN_TELEFONO))
                val pathAvatar = cursor.getString(cursor.getColumnIndexOrThrow(COLUMN_PATH_AVATAR))
                
                usuario = Usuario(userId, login, "", nombre, email, telefono, pathAvatar)
            }
            cursor.close()
            // db.close()
            return usuario
        }
        ```

      * **Modificar Usuario (UPDATE - para `PrincipalActivity`):**
        Actualizar los campos editables (nombre, email, teléfono, path\_avatar). El login y password no se modifican desde esta pantalla según el enunciado.

        ```kotlin
        // Dentro de UserDbHelper.kt
        fun updateUser(userId: Int, nombre: String, email: String, telefono: String, pathAvatar: String?): Int {
            val db = this.writableDatabase
            val values = ContentValues().apply {
                put(COLUMN_NOMBRE, nombre)
                put(COLUMN_EMAIL, email)
                put(COLUMN_TELEFONO, telefono)
                pathAvatar?.let { put(COLUMN_PATH_AVATAR, it) } // Actualizar avatar solo si se proporciona uno nuevo
            }
            // La cláusula WHERE asegura que solo se actualice el usuario con el ID correcto
            val rowsAffected = db.update(TABLE_USUARIOS, values, "$COLUMN_ID =?", arrayOf(userId.toString()))
            // db.close()
            return rowsAffected // Devuelve el número de filas afectadas (debería ser 1 si el ID existe)
        }
        ```

  * **Mostrar Login e Imagen en la Parte Superior (`PrincipalActivity`):**
    Una vez que `PrincipalActivity` obtiene el `ID` del usuario desde `SharedPreferences`, llamará a `userDbHelper.getUserById(userId)` para obtener todos los datos del usuario.

      * El `login` del usuario (`usuario.login`) se mostrará en el `TextView` correspondiente (ej. `tvLoginPrincipal`).
      * La ruta del avatar (`usuario.pathAvatar`) se usará para cargar la imagen desde el almacenamiento interno (usando `FileInputStream` y `BitmapFactory.decodeStream()`, como en la Pregunta 2) y se mostrará en el `ImageView` del avatar (ej. `imgAvatarPrincipal`).

    SQLite es la solución de base de datos local estándar en Android. La clase `SQLiteOpenHelper` es fundamental para gestionar la creación y el versionado de la base de datos. Las operaciones CRUD (Crear, Leer, Actualizar, Borrar) son la base de toda interacción con los datos almacenados. La elección de cómo almacenar datos binarios como imágenes (ruta vs. BLOB) tiene implicaciones de diseño que deben considerarse. Es crucial entender el ciclo de vida de `SQLiteOpenHelper` (`onCreate` se llama solo cuando la BD se crea por primera vez, `onUpgrade` cuando cambia `DATABASE_VERSION`) y cómo construir y ejecutar consultas SQL de forma segura, utilizando placeholders (`?`) en las consultas parametrizadas para prevenir la inyección SQL.

### 1.6. Manejo de Errores y Feedback al Usuario

Una aplicación robusta no solo implementa la funcionalidad esperada, sino que también maneja posibles errores de forma elegante y proporciona feedback claro al usuario. La nota del examen que pide explícitamente mensajes al usuario refuerza esta necesidad.

  * **Implementación de Bloques `try-catch`:**
    Es esencial anticipar y manejar excepciones que puedan ocurrir durante operaciones críticas.

      * **Acceso a Ficheros (Streams para imágenes):**
        Las operaciones de lectura (`FileInputStream`, `BitmapFactory.decodeStream()`) o escritura (`FileOutputStream`) de archivos pueden lanzar `IOException` (ej. archivo no encontrado, permisos incorrectos aunque menos común en almacenamiento interno privado, error de E/S) o `OutOfMemoryError` si la imagen es muy grande y no se maneja adecuadamente (ej. escalado).

        ```kotlin
        // Ejemplo al cargar una imagen
        try {
            val file = File(filePath)
            if (file.exists()) {
                FileInputStream(file).use { fis -> //.use asegura que el stream se cierre
                    val bitmap = BitmapFactory.decodeStream(fis)
                    imageView.setImageBitmap(bitmap)
                }
            } else {
                // Mostrar Toast: "Archivo de imagen no encontrado"
            }
        } catch (e: IOException) {
            Log.e("ImageLoad", "Error de E/S al cargar imagen: $filePath", e)
            // Mostrar Toast: "Error al cargar imagen"
        } catch (e: OutOfMemoryError) {
            Log.e("ImageLoad", "Memoria insuficiente al cargar imagen: $filePath", e)
            // Mostrar Toast: "Imagen demasiado grande para cargar"
        }
        ```

      * **Operaciones de Base de Datos (SQLite):**
        Las llamadas a `db.insert()`, `db.update()`, `db.delete()`, `db.query()` o `db.rawQuery()` pueden lanzar `SQLiteException` por diversas razones:

          * `SQLiteConstraintException`: Si se viola una restricción `UNIQUE` (ej. intentar registrar un login o email que ya existe) o `NOT NULL`.
          * `SQLiteDiskIOException`: Si hay problemas de disco (ej. disco lleno).
          * Errores de sintaxis SQL si las consultas se construyen dinámicamente de forma incorrecta (menos probable si se usan los métodos de conveniencia de `SQLiteDatabase` o placeholders).

        <!-- end list -->

        ```kotlin
        // Ejemplo al añadir un usuario
        try {
            val id = userDbHelper.addUser(nuevoUsuario)
            if (id > -1) {
                // Mostrar Toast: "Usuario registrado correctamente"
            } else {
                // Mostrar Toast: "Error al registrar usuario (posiblemente login/email duplicado)"
            }
        } catch (e: SQLiteConstraintException) {
            Log.e("DBError", "Error de restricción al añadir usuario", e)
            // Mostrar Toast: "Error: El login o email ya está en uso."
        } catch (e: SQLiteException) {
            Log.e("DBError", "Error de SQLite al añadir usuario", e)
            // Mostrar Toast: "Error de base de datos al registrar."
        }
        ```

      * **Otras Operaciones:** Conversiones de tipo (ej. `String` a `Int` desde un `EditText`), acceso a red (si lo hubiera en otro tipo de examen), etc., también deberían estar protegidas.

  * **Mensajes al Usuario (`Toast`, `Snackbar`):**
    Proporcionar feedback al usuario es esencial para una buena experiencia.

      * **`Toast`:** Son mensajes cortos, no intrusivos, que desaparecen automáticamente. Son adecuados para notificaciones simples.

          * Éxito: "Datos guardados correctamente.", "Usuario registrado.", "Imagen seleccionada."
          * Cancelación/Info: "Operación cancelada.", "No se han realizado cambios."
          * Error: "Error al guardar: El login ya existe.", "Usuario no encontrado o contraseña incorrecta.", "Error de conexión con la base de datos.", "No se pudo cargar la imagen."

        <!-- end list -->

        ```kotlin
        Toast.makeText(applicationContext, "Datos guardados", Toast.LENGTH_SHORT).show()
        ```

      * **`Snackbar` (Opcional, más moderno y flexible):**
        Aparecen en la parte inferior de la pantalla y pueden incluir una acción opcional (ej. "Reintentar"). Requieren una `View` contenedora (a menudo una `CoordinatorLayout`) para un comportamiento óptimo. Para un examen, `Toast` suele ser suficiente y más rápido de implementar.

        ```kotlin
        // Necesita una vista raíz, por ejemplo, la vista principal del layout
        // val rootView = findViewById<View>(android.R.id.content) 
        // Snackbar.make(rootView, "Error de red", Snackbar.LENGTH_LONG)
        //  .setAction("Reintentar") { /* Lógica de reintento aquí */ }
        //  .show()
        ```

      * **Mensajes en `TextViews` o `setError()` en `EditTexts`:**
        Para errores de validación de formularios (ej. "Campo requerido", "Email no válido"), es más directo mostrar el error junto al campo problemático.

        ```kotlin
        // if (editTextEmail.text.toString().isEmpty()) {
        //    editTextEmail.error = "El email es requerido"
        // }
        ```

    Un buen manejo de errores y un feedback claro no solo mejoran drásticamente la experiencia del usuario, sino que también incrementan la robustez y la calidad percibida de la aplicación. En el contexto de un examen, demostrar competencia en estas áreas evidencia una comprensión más completa del ciclo de desarrollo de software y una atención al detalle que va más allá de la simple implementación de funcionalidades. No se deben dejar los bloques `catch` vacíos; como mínimo, se debe registrar el error (usando `Log.e("TAG", "Mensaje", excepcion)`) para facilitar la depuración y, cuando sea apropiado, informar al usuario de manera comprensible.

### 1.7. Fragmentos de Código Clave

A continuación, se presentan algunos fragmentos de código ilustrativos para los puntos más críticos, sin pretender ser un proyecto completo, sino ejemplos funcionales.

  * **XML: `EditText` con `inputType` y `ImageView` para avatar en `activity_registro.xml`**

    ```xml
    <EditText
        android:id="@+id/etEmailRegistro"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Email del usuario"
        android:inputType="textEmailAddress" />

    <ImageView
        android:id="@+id/imgAvatarRegistro"
        android:layout_width="100dp"
        android:layout_height="100dp"
        android:src="@drawable/ic_avatar_placeholder" /> 
    ```

  * **Kotlin: Inicialización de `ActivityResultLauncher` en `RegistroActivity.kt` (repaso)**

    ```kotlin
    // (Ya mostrado en la sección 1.3, se incluye aquí para consolidar)
    // private lateinit var selectedAvatarPath: String
    // val selectAvatarLauncher = registerForActivityResult(ActivityResultContracts.StartActivityForResult()) { result ->
    //     if (result.resultCode == Activity.RESULT_OK) {
    //         result.data?.getStringExtra("selectedAvatarPathKey")?.let { path ->
    //             selectedAvatarPath = path
    //             // Cargar y mostrar imagen...
    //             Toast.makeText(this, "Avatar seleccionado: $path", Toast.LENGTH_SHORT).show()
    //         }
    //     }
    // }
    //...
    // btnSeleccionarAvatar.setOnClickListener {
    //    val intent = Intent(this, AvatarSelectionActivity::class.java)
    //    selectAvatarLauncher.launch(intent)
    // }
    ```

  * **Kotlin: Lógica básica de un `AvatarAdapter` (para `ListView`)**

    ```kotlin
    // AvatarItem.kt (clase de datos)
    // data class AvatarItem(val name: String, val filePath: String)

    // AvatarAdapter.kt
    // class AvatarAdapter(context: Context, private val avatarList: List<AvatarItem>) :
    //    ArrayAdapter<AvatarItem>(context, 0, avatarList) {
    //
    //    override fun getView(position: Int, convertView: View?, parent: ViewGroup): View {
    //        val itemView = convertView?: LayoutInflater.from(context)
    //          .inflate(R.layout.list_item_avatar, parent, false) // list_item_avatar.xml definido antes
    //
    //        val currentItem = avatarList[position]
    //
    //        val imageView = itemView.findViewById<ImageView>(R.id.imgAvatarItem)
    //        val textView = itemView.findViewById<TextView>(R.id.tvAvatarNameItem)
    //
    //        textView.text = currentItem.name
    //        try {
    //            val file = File(currentItem.filePath)
    //            if (file.exists()) {
    //                FileInputStream(file).use { fis ->
    //                    val bitmap = BitmapFactory.decodeStream(fis)
    //                    imageView.setImageBitmap(bitmap)
    //                }
    //            } else {
    //                imageView.setImageResource(R.drawable.ic_avatar_placeholder) // Imagen por defecto si no se encuentra
    //            }
    //        } catch (e: Exception) {
    //            Log.e("AvatarAdapter", "Error loading image for ${currentItem.name}", e)
    //            imageView.setImageResource(R.drawable.ic_avatar_placeholder)
    //        }
    //        return itemView
    //    }
    // }
    ```

  * **Kotlin: Guardar/Leer de `SharedPreferences` (ejemplo en `LoginActivity`)**

    ```kotlin
    // Guardar tras login exitoso (userId y userLogin obtenidos previamente)
    // val prefs = getSharedPreferences("PREFS_SESION_USUARIO", Context.MODE_PRIVATE)
    // with(prefs.edit()) {
    //    putString("KEY_USER_LOGIN", userLogin)
    //    putInt("KEY_USER_ID", userId)
    //    apply()
    // }

    // Leer al inicio de la app (ej. en SplashActivity o MainActivity)
    // val prefs = getSharedPreferences("PREFS_SESION_USUARIO", Context.MODE_PRIVATE)
    // val userId = prefs.getInt("KEY_USER_ID", -1) // -1 si no se encuentra
    // if (userId!= -1) {
    //    // Usuario ya logueado, ir a PrincipalActivity
    // } else {
    //    // Ir a LoginActivity
    // }
    ```

  * **Kotlin: Función CRUD básica para SQLite (ej. `addUser` en `UserDbHelper.kt` - repaso)**

    ```kotlin
    // (Ya mostrado en la sección 1.5, se incluye aquí para consolidar)
    // fun addUser(usuario: Usuario): Long {
    //    val values = ContentValues().apply { /*... rellenar valores... */ }
    //    val db = this.writableDatabase
    //    val id = db.insert(TABLE_USUARIOS, null, values)
    //    return id
    // }
    ```

  * **Kotlin: Lectura de imagen desde `FileInputStream` (repaso)**

    ```kotlin
    // (Ya mostrado en secciones 1.3 y 1.6, se incluye aquí para consolidar)
    // try {
    //    val file = File(imagePathString)
    //    if (file.exists()) {
    //        FileInputStream(file).use { fis ->
    //            val bitmap = BitmapFactory.decodeStream(fis)
    //            // Hacer algo con el bitmap
    //        }
    //    }
    // } catch (e: IOException) {
    //    Log.e("ImageRead", "Error leyendo imagen", e)
    // }
    ```

    Estos fragmentos de código sirven para ilustrar los conceptos clave. Ver código real, aunque sea simplificado, ayuda a consolidar la comprensión teórica. Han sido elegidos para destacar las partes que suelen ser más desafiantes o cruciales en un examen de PMDM. Pueden servir como mini-plantillas o puntos de partida para adaptar y expandir según las necesidades específicas del examen.

-----

## Parte 2: Guía Metodológica Detallada para Afrontar y Realizar el Examen

Esta segunda parte se enfoca en proporcionar una estrategia completa para la preparación y realización del examen de PMDM, con el objetivo de maximizar las posibilidades de éxito.

### 2.1. Estrategia General y Preparación Previa al Examen

Una preparación sólida es la base para afrontar el examen con confianza.

  * **Conceptos Teóricos Cruciales a Dominar:**
    Dado que las guías de estudio específicas de GitHub ([2, 3]) no son accesibles, es vital asegurarse de dominar los siguientes temas fundamentales, que son pilares en cualquier currículo de PMDM:

      * **Componentes de la Aplicación Android:**
          * `Activity`: Entender profundamente su ciclo de vida (`onCreate`, `onStart`, `onResume`, `onPause`, `onStop`, `onRestart`, `onDestroy`), cómo manejar cambios de configuración y el guardado/restauración del estado. Saber cómo se inician y comunican.
          * `Intent`: Tipos (explícitos para iniciar componentes dentro de la misma app, implícitos para solicitar acciones a otras apps), cómo pasar datos (`putExtra`, `getExtra`), y el uso de `ActivityResultLauncher` para obtener resultados de `Activities`.
          * `Service`: Concepto básico, tipos (iniciados, enlazados), ciclo de vida. Menos común en exámenes básicos de implementación completa, pero el concepto es importante.
          * `BroadcastReceiver`: Para responder a eventos del sistema o de la aplicación. Registro estático (en `AndroidManifest.xml`) y dinámico.
          * `ContentProvider`: Para compartir datos entre aplicaciones (concepto, aunque su implementación completa es menos frecuente en exámenes introductorios).
      * **Interfaz de Usuario (UI):**
          * **Layouts XML:** Dominar la sintaxis y el uso de `ConstraintLayout` (muy flexible y potente), `LinearLayout` (para estructuras simples), `RelativeLayout` (alternativa a `ConstraintLayout` para relaciones entre vistas), y `FrameLayout` (para superponer vistas). La información de [6] destaca `ConstraintLayout` como el default y `LinearLayout` por su simplicidad.
          * **Vistas Comunes (`View`):** `TextView`, `EditText` (con sus `inputType`), `Button`, `ImageView`, `CheckBox`, `RadioButton`, `Spinner`.
          * **Listas y Rejillas:** `ListView` (más simple) y `RecyclerView` (más eficiente y flexible, preferido para listas complejas o grandes).
          * **`Adapters`:** El puente entre los datos y las vistas de lista/rejilla. `ArrayAdapter` (simple, para arrays o listas de objetos), `BaseAdapter` (más control), y `RecyclerView.Adapter` con `ViewHolder` (patrón obligatorio para `RecyclerView`).
          * **Manejo de Eventos:** `OnClickListener`, `OnItemClickListener` (para `ListView`), `OnItemSelectedListener` (para `Spinner`), etc.
      * **Persistencia de Datos:**
          * `SharedPreferences`: Para datos primitivos y pequeñas colecciones de strings (clave-valor). Ideal para configuraciones o estado de sesión.
          * **Almacenamiento Interno/Externo:**
              * Interno: `getFilesDir()`, `getCacheDir()`. Privado para la app.
              * Externo: Requiere permisos. Diferencias entre almacenamiento específico de la app y público.
              * Manejo de archivos con `Streams`: `FileInputStream`, `FileOutputStream`, `BufferedReader`, `BufferedWriter`.
          * **Bases de Datos SQLite:**
              * `SQLiteOpenHelper`: Para crear y versionar la BD. Métodos `onCreate` y `onUpgrade`.
              * Sentencias SQL: `CREATE TABLE`, `INSERT`, `SELECT`, `UPDATE`, `DELETE`.
              * `Cursor`: Para iterar sobre los resultados de una consulta.
              * `ContentValues`: Para empaquetar datos antes de un `insert` o `update`.
      * **Hilos y Tareas Asíncronas:**
          * **Hilo Principal (UI Thread):** Entender que todas las operaciones de UI deben ocurrir aquí y que operaciones largas lo bloquean (causando ANR - Application Not Responding).
          * **Tareas en Segundo Plano:** Necesidad de ejecutar operaciones de red, acceso a BD o procesamiento intensivo fuera del hilo principal.
          * **Mecanismos:** Coroutines de Kotlin (la forma moderna y recomendada si se usa Kotlin), `AsyncTask` (obsoleto pero puede aparecer en material antiguo o exámenes), `Thread` con `Handler` o `runOnUiThread` para actualizar la UI.
      * **Recursos de la Aplicación:**
          * Uso de `strings.xml` (para internacionalización y centralización de textos), `colors.xml`, `dimens.xml`, `styles.xml`.
          * Manejo de `drawables` (imágenes, shapes XML).
          * Layouts alternativos para diferentes tamaños de pantalla o configuraciones (aunque menos común en exámenes básicos).
      * **Permisos:**
          * Declaración en `AndroidManifest.xml` (ej. `android.permission.INTERNET`).
          * Solicitud de permisos en tiempo de ejecución para permisos peligrosos (a partir de Android 6.0 Marshmallow).
      * **Fragmentos (`Fragment`):**
          * Aunque el repositorio `EJFragments.git` ([4]) es inaccesible, los fragmentos son un tema muy común en PMDM.
          * Ciclo de vida del fragmento (diferente pero relacionado con el de la `Activity`).
          * Cómo añadir fragmentos a una `Activity` (estáticamente en XML o dinámicamente en código).
          * Comunicación entre fragmentos y entre un fragmento y su `Activity` contenedora.

    Para facilitar el estudio, la siguiente tabla resume los componentes Android clave:

    **Tabla: Resumen de Componentes Android Clave para el Estudio**

| Componente | Función Principal en PMDM | Puntos Clave a Estudiar |
|--------------------|-------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| `Activity` | Representa una pantalla individual con la que el usuario puede interactuar. | Ciclo de vida (`onCreate`, `onStart`, `onResume`, `onPause`, `onStop`, `onDestroy`), manejo de estado, `Intent`. |
| `Intent` | Objeto de mensajería para solicitar una acción de otro componente de la aplicación. | Explícitos (dentro de la app) vs. Implícitos (entre apps), pasar datos (`putExtra`), `ActivityResultLauncher`. |
| `Layouts` (XML) | Definen la estructura visual y los elementos de la interfaz de usuario. | `ConstraintLayout`, `LinearLayout`, `RelativeLayout`, `FrameLayout`. Atributos comunes. ([6]) |
| `Adapter` | Actúa como un puente entre una vista de colección (ej. `ListView`, `RecyclerView`) y los datos subyacentes. | `ArrayAdapter`, `BaseAdapter`, `RecyclerView.Adapter` con `ViewHolder`. Métodos clave (`getView`, `bindViewHolder`). |
| `SharedPreferences`| Almacena datos persistentes simples en formato clave-valor. | Obtener editor, `putTipo()`, `getTipo()`, `apply()` (asíncrono) vs `commit()` (síncrono). |
| `SQLiteOpenHelper` | Clase ayudante para la creación, apertura y gestión de versiones de bases de datos SQLite. | Métodos `onCreate()` y `onUpgrade()`. Sentencias SQL para CRUD. Uso de `ContentValues` y `Cursor`. |
| `FileInputStream` / `FileOutputStream` | Para leer o escribir flujos de bytes (streams) desde o hacia archivos en el almacenamiento. | Manejo de `IOException`. Uso de `try-with-resources` (Java) o la función `use` (Kotlin) para cierre automático. |
| `Fragment` | Componente modular de UI que puede ser reutilizado dentro de las `Activities`. | Ciclo de vida propio, comunicación con la `Activity` y otros `Fragments`. |

```
Esta tabla sirve como una lista de verificación rápida de los temas más importantes. Centrarse en los "Puntos Clave a Estudiar" para cada componente dirigirá el esfuerzo hacia los aspectos más relevantes para un examen.
```

  * **Cómo Enfocar el Estudio Práctico:**
    La teoría es necesaria, pero la habilidad se desarrolla con la práctica.

      * **Recrear Proyectos Pequeños y Específicos:** No limitarse a leer código de ejemplos. Es fundamental implementar pequeñas aplicaciones o funcionalidades aisladas que utilicen cada uno de los conceptos teóricos clave. Por ejemplo:
          * Una app que guarde una nota de texto en `SharedPreferences`.
          * Una app que muestre una lista de elementos leídos desde un array o una lista simple usando un `ArrayAdapter`.
          * Una app que permita añadir ítems a una base de datos SQLite y luego los muestre en un `ListView` o `RecyclerView`.
          * Una app que lance una segunda `Activity` para obtener un dato (ej. un nombre) y lo muestre en la primera.
          * Una app que cargue una imagen desde `drawable` o `filesDir` y la muestre en un `ImageView`.
      * **Analizar Ejemplos (Incluso Genéricos):** Dado que los ejemplos específicos del curso podrían no estar disponibles, buscar tutoriales de Android (de fuentes confiables como la documentación oficial de Android, blogs de desarrolladores, etc.) o ejemplos de proyectos en Android Studio que implementen funcionalidades similares a las del examen tipo. Prestar especial atención a:
          * La estructura del proyecto (paquetes, organización de recursos).
          * Cómo se conectan los diferentes componentes (Activities, Adapters, Helpers).
          * El flujo de datos a través de la aplicación.
      * **Utilizar el Depurador de Android Studio:** Aprender a usar el depurador es una habilidad crucial. Permite:
          * Establecer `breakpoints` (puntos de interrupción) para detener la ejecución del código en un punto específico.
          * Ejecutar el código paso a paso (`step over`, `step into`, `step out`).
          * Inspeccionar los valores de las variables en tiempo de ejecución.
          * Entender el flujo de ejecución y encontrar la causa raíz de los errores mucho más rápido que con `Log` statements (aunque estos también son útiles).

    La preparación efectiva combina una comprensión teórica sólida con una aplicación práctica intensiva. Un examen de PMDM evalúa tanto el conocimiento ("¿qué es un `Intent`?") como la habilidad ("¿cómo se usa un `Intent` para pasar datos y obtener un resultado?"). La teoría proporciona el "qué" y el "por qué", mientras que la práctica proporciona el "cómo". Al recrear proyectos pequeños, el estudiante se enfrenta a los mismos tipos de problemas y decisiones de diseño que encontrará en el examen, desarrollando así la fluidez y la capacidad de resolución de problemas necesarias. Se debe ser proactivo en el estudio, buscando y practicando con una variedad de problemas y ejemplos.

### 2.2. Durante el Examen: Enfoque Paso a Paso

El día del examen, una estrategia bien definida puede marcar una gran diferencia.

  * **Recepción y Análisis Inicial (Primeros 10-15 minutos):**
    No precipitarse a codificar. Estos primeros minutos son de inversión.

    1.  **Lectura Comprensiva Completa:** Leer TODO el enunciado del examen una vez, de principio a fin, para obtener una visión general de lo que se pide, la complejidad global y el alcance de la aplicación a desarrollar.
    2.  **Identificar Dependencias entre Preguntas:** ¿La pregunta 2 (ej. selección de avatar) depende de la 1 (ej. layout de registro)? ¿La pregunta 4 (BD) utiliza datos de la 3 (SharedPreferences)? Esto ayuda a planificar el orden de implementación. Generalmente, las interfaces se definen primero, luego la lógica de navegación, la gestión de datos simples, y finalmente la integración con bases de datos o componentes más complejos.
    3.  **Identificar Puntos Clave y Restricciones Técnicas:** Subrayar o anotar en una hoja aparte los verbos de acción ("implementar", "crear", "guardar", "mostrar", "validar", "comunicar") y, muy importante, las restricciones o requisitos técnicos específicos ("usar `Streams` para imágenes", "guardar el ID de usuario en `SharedPreferences`", "la base de datos debe ser SQLite", "no usar librerías externas" si se indica).
    4.  **Estimar Dificultad y Tiempo (Mentalmente o Anotado):** Asignar un tiempo estimado a cada pregunta o sección principal. Identificar las partes que parecen más sencillas (para abordarlas primero y ganar confianza y puntos "fáciles") y las que parecen más complejas o largas (para asegurar que se les asigna suficiente tiempo o para decidir si se abordan más tarde).
    5.  **Aclarar Dudas (si el formato del examen lo permite):** Si alguna parte del enunciado no está clara o parece ambigua, es el momento de preguntar al profesor o supervisor del examen. No asumir; una aclaración puede ahorrar mucho tiempo y esfuerzo mal dirigido.

  * **Desglose de Problemas en Subtareas:**
    Una vez comprendido el examen en su totalidad, tomar cada pregunta principal y dividirla mentalmente o por escrito en subtareas más pequeñas y manejables. Esto hace que el problema general parezca menos abrumador y proporciona una hoja de ruta más clara.
    Por ejemplo, para el "ExamenTipo1.pdf":

      * **Pregunta 1 (Interfaces):**
          * Subtarea 1.1: Crear `activity_login.xml`.
          * Subtarea 1.2: Crear `activity_registro.xml`.
          * Subtarea 1.3: Crear `activity_principal.xml`.
          * Subtarea 1.4: Verificar `inputType` en todos los `EditText`.
      * **Pregunta 2 (Selección de Imágenes):**
          * Subtarea 2.1: Crear `AvatarSelectionActivity.kt` y `activity_avatar_selection.xml`.
          * Subtarea 2.2: Implementar la lógica para tener las imágenes de muestra en `filesDir`.
          * Subtarea 2.3: Crear `AvatarAdapter.kt` y `list_item_avatar.xml`.
          * Subtarea 2.4: Implementar la lectura de imágenes con `Streams` en el adapter.
          * Subtarea 2.5: Implementar la lógica de `ActivityResultLauncher` para la comunicación.
      * **Pregunta 3 (Gestión de Usuario con Preferencias):**
          * Subtarea 3.1: Implementar el guardado del usuario en `SharedPreferences` tras el login.
          * Subtarea 3.2: Implementar la recuperación del usuario desde `SharedPreferences` en `PrincipalActivity`.
          * Subtarea 3.3: Implementar el cierre de sesión y la limpieza de `SharedPreferences`.
      * **Pregunta 4 (Integración con Base de Datos SQLite):**
          * Subtarea 4.1: Crear la clase `UserDbHelper` y definir la tabla `Usuarios`.
          * Subtarea 4.2: Implementar las funciones CRUD en `UserDbHelper`.
          * Subtarea 4.3: Integrar el registro y login de usuario con la base de datos.

  * **Interpretación Precisa de los Requisitos:**
    Prestar atención EXTREMA a los detalles del enunciado.

      * Si se pide "guardar el **nombre del fichero** de imagen en `SharedPreferences`", no se debe guardar el `Bitmap` entero o la ruta completa si no es lo especificado.
      * Si se pide "usar `Streams` para leer la imagen desde el almacenamiento interno", se debe implementar de esa manera, incluso si se conoce otra forma que podría parecer más rápida (a menos que el tiempo apremie críticamente y se justifique).
      * Si se especifican nombres de clases, paquetes, métodos, variables o IDs de vistas, es fundamental usarlos tal cual. Los correctores pueden tener scripts o buscar específicamente esos nombres.
      * Fijarse en las notas aclaratorias o requisitos adicionales (ej. "mostrar mensajes al usuario en caso de error o éxito").

    Una buena gestión del tiempo y una comprensión clara y detallada de los requisitos desde el principio son tan importantes como el conocimiento técnico en sí. Dividir problemas grandes en partes más pequeñas no solo facilita su resolución, sino que también reduce la sensación de agobio y permite un progreso más estructurado y medible. Es recomendable practicar esta fase de análisis y planificación con otros enunciados de examen o problemas de programación si es posible.

### 2.3. Proceso de Desarrollo Práctico (usando "ExamenTipo1" como caso de estudio)

Una vez planificado, se inicia el desarrollo en Android Studio.

  * **Configuración Inicial del Proyecto:**

    1.  **Crear Nuevo Proyecto:** En Android Studio, crear un nuevo proyecto (generalmente "Empty Activity" o "No Activity" si se prefiere configurar todo desde cero). Elegir Kotlin o Java según lo requerido o la preferencia personal (Kotlin es el lenguaje preferido actualmente para Android).
    2.  **Configurar `build.gradle` (Módulo: app):**
          * Verificar `compileSdk`, `minSdk`, `targetSdk`.
          * Añadir dependencias si son necesarias y permitidas (ej. para `RecyclerView` si no viene por defecto, aunque para un examen básico de PMDM las dependencias suelen ser mínimas).
          * Habilitar funcionalidades como `viewBinding` o `dataBinding` si se planea usarlas y se está familiarizado con ellas, ya que pueden simplificar el acceso a las vistas:
            ```gradle
            // En android {... } block de build.gradle (:app)
            // buildFeatures {
            //    viewBinding true
            // }
            ```
    3.  **Crear Estructura de Paquetes:** Inmediatamente después de crear el proyecto, crear la estructura de paquetes definida en la fase de análisis (ej. `com.nombrealumno.examenpmdm.activities`, `.adapters`, `.database`, `.model`, `.utils`). Esto establece un marco de trabajo ordenado desde el inicio.

  * **Abordaje por Funcionalidad (Iterativo e Incremental):**
    No intentar construir toda la aplicación de una vez. Es mejor abordar funcionalidad por funcionalidad, o pregunta por pregunta, de forma iterativa.

      * **Paso 1: Interfaces (XML primero):**

          * Muchos desarrolladores encuentran útil crear los layouts XML básicos para todas las pantallas requeridas al principio. Esto proporciona una estructura visual y permite enlazar las vistas en el código Kotlin/Java posteriormente (`findViewById` o mediante `viewBinding`).
          * **Consejos para la Fidelidad Visual:**
              * Tener las imágenes de muestra del examen visibles constantemente como referencia.
              * Empezar con `ConstraintLayout` si la UI tiene elementos posicionados de forma compleja o relativa. Usar `LinearLayout` para formularios o listas simples.
              * Utilizar el editor de diseño visual de Android Studio (Design/Split view) para arrastrar y soltar componentes y ajustar sus atributos. El modo "Blueprint" es útil para visualizar y gestionar las restricciones en `ConstraintLayout`.
              * Probar los layouts en un emulador o dispositivo físico con una densidad de pantalla y tamaño similar a la que se podría esperar o la que se usa como referencia en las imágenes del examen. Ajustar márgenes (`android:layout_margin`), paddings (`android:padding`), tamaños de texto (`android:textSize`), etc., hasta lograr la apariencia deseada.

      * **Paso 2: Lógica de Cada Pregunta (Orden Sugerido, puede variar según dependencias):**
        Se sugiere un orden que construya la aplicación de forma incremental, probando cada parte.

        1.  **Creación de `Activities` y Navegación Básica:**

              * Crear las clases Kotlin/Java para cada `Activity` (`LoginActivity`, `RegistroActivity`, `PrincipalActivity`, `AvatarSelectionActivity`).
              * Implementar la navegación básica entre ellas usando `Intents` explícitos. Por ejemplo, un botón en `LoginActivity` que lleve a `RegistroActivity`, y viceversa, o de `LoginActivity` a `PrincipalActivity` (inicialmente sin lógica de sesión).
              * Probar que la navegación funciona.

        2.  **Funcionalidad de Registro y Login (Simulada inicialmente):**

              * En `RegistroActivity`, enlazar los `EditTexts` y el botón "Registrar". Implementar la lógica de UI (ej. recoger los textos de los `EditTexts`).
              * En `LoginActivity`, enlazar los `EditTexts` y el botón "Login".
              * **Inicialmente, simular la lógica de autenticación y registro** para no depender aún de la base de datos. Por ejemplo, en `LoginActivity`, se puede tener un usuario y contraseña fijos:
                ```kotlin
                // if (login == "test" && password == "test1234") { /* Navegar a Principal */ } 
                // else { /* Mostrar error */ }
                ```
              * Esto permite probar el flujo de UI y navegación antes de introducir la complejidad de la BD.

        3.  **Integración de `SharedPreferences` (Pregunta 3):**

              * Implementar la lógica de `SharedPreferences` para guardar el ID y login del usuario tras una autenticación "exitosa" (aún simulada o ya con BD si se avanza rápido).
              * Modificar el inicio de la aplicación para que verifique `SharedPreferences` y navegue a `Login` o `Principal` según corresponda.
              * Implementar la funcionalidad de "Cerrar Sesión" en `PrincipalActivity` para limpiar `SharedPreferences` y volver a `Login`.
              * Probar todo el ciclo: inicio sin sesión -\> login -\> principal -\> cerrar sesión -\> inicio (debe ir a login).

        4.  **Implementación de la Base de Datos SQLite (Pregunta 4):**

              * Crear la clase `UserDbHelper` (heredando de `SQLiteOpenHelper`) con la definición de la tabla `Usuarios` y los métodos `onCreate` y `onUpgrade`.
              * Implementar las funciones CRUD en `UserDbHelper` o una clase DAO:
                  * `addUser()`: Probar primero el alta de un nuevo usuario. Se puede hacer desde `RegistroActivity`.
                  * `getUserByLoginAndPassword()`: Integrar esta función en `LoginActivity` para reemplazar la autenticación simulada.
                  * `getUserById()`: Usar en `PrincipalActivity` para cargar los datos del usuario logueado (cuyo ID se obtuvo de `SharedPreferences`).
                  * `updateUser()`: Implementar en `PrincipalActivity` para el botón "Guardar Cambios".
              * Probar cada operación CRUD cuidadosamente. Usar `Log` o el depurador para verificar que los datos se guardan y recuperan correctamente.

        5.  **Implementación de la Selección de Imágenes (Pregunta 2):**

              * Crear `AvatarSelectionActivity` y su layout con el `ListView` y botones.
              * Asegurar que las imágenes de muestra (1.png, 2.png, 3.png) estén en `context.getFilesDir()` (copiándolas manualmente para el examen o mediante código si se implementó).
              * Crear el `AvatarAdapter` personalizado para mostrar las imágenes y sus nombres en el `ListView`. El adapter leerá las imágenes de `filesDir` usando `FileInputStream`.
              * Implementar la lógica de selección en el `ListView` y los botones "Aceptar"/"Cancelar".
              * Implementar la comunicación entre `RegistroActivity` y `AvatarSelectionActivity` usando `ActivityResultLauncher` para devolver la ruta (`String`) de la imagen seleccionada.
              * En `RegistroActivity`, al recibir la ruta, cargar la imagen usando `FileInputStream` y mostrarla en el `ImageView` del avatar. Guardar esta ruta cuando se registre el usuario (se almacenará en la columna `path_avatar` de la BD).
              * En `PrincipalActivity`, al cargar los datos del usuario, usar la `path_avatar` de la BD para mostrar el avatar.

      * **Puntos Críticos a Recordar Durante la Implementación:**

          * **`Adapters`:** Entender bien cómo funciona `getView()` (para `ArrayAdapter`/`BaseAdapter`) o el par `onCreateViewHolder`/`onBindViewHolder` (para `RecyclerView.Adapter`). Asegurarse de que se infla el layout del ítem correctamente y se asignan los datos a las vistas del ítem. No olvidar llamar a `notifyDataSetChanged()` en el adapter si la lista de datos subyacente cambia y se quiere refrescar el `ListView`/`RecyclerView`.
          * **`SQLiteOpenHelper`:** `onCreate()` solo se llama una vez cuando la base de datos se crea por primera vez. `onUpgrade()` se llama si se incrementa `DATABASE_VERSION`. Gestionar la apertura (`getWritableDatabase()`, `getReadableDatabase()`) y cierre (`close()`) de la base de datos de forma adecuada para evitar fugas de recursos. A menudo, se obtiene una instancia de la BD al principio de una operación y se cierra al final, o se gestiona a nivel de ciclo de vida de la `Activity`/`Fragment`.
          * **Intents con Resultados (`ActivityResultLauncher`):** Seguir el flujo correcto:
            1.  Registrar el launcher en la `Activity` que llama (ej. `RegistroActivity`).
            2.  Lanzar la `Activity` que devuelve el resultado (ej. `AvatarSelectionActivity`) usando el método `launch()` del launcher.
            3.  En la `Activity` que devuelve el resultado, crear un `Intent` con los datos de vuelta, llamar a `setResult(Activity.RESULT_OK, intentDeVuelta)` y luego a `finish()`.
            4.  Procesar el resultado en el callback del launcher en la `Activity` que llamó.
          * **`Streams` (para archivos):** Siempre cerrar los streams (`FileInputStream`, `FileOutputStream`, etc.) para liberar recursos y evitar fugas. La forma más segura es usar un bloque `finally` o, preferiblemente en Kotlin, la función de extensión `use` que cierra el stream automáticamente, incluso si ocurren excepciones.
            ```kotlin
            // FileInputStream(file).use { fis ->
            //    val bitmap = BitmapFactory.decodeStream(fis)
            //    //...
            // } // fis se cierra automáticamente aquí
            ```

  * **Buenas Prácticas "En Vivo" (Durante el Desarrollo en el Examen):**

      * **Pruebas Incrementales y Frecuentes:** Probar cada pequeña pieza de funcionalidad tan pronto como se escribe o se completa una subtarea. No esperar a tener toda la aplicación "terminada" para empezar a probar. Esto ayuda a detectar y corregir errores temprano, cuando son más fáciles de aislar.
      * **Mensajes al Usuario (`Toast`):** Añadir `Toasts` para proporcionar feedback inmediato sobre las operaciones ("Usuario registrado con éxito", "Error al conectar con la base de datos", "Imagen seleccionada"). Esto no solo cumple con los requisitos del examen, sino que también ayuda durante el desarrollo a saber qué está sucediendo.
      * **Debugging Básico con `Log`:** Si el depurador completo de Android Studio parece consumir mucho tiempo en el examen, usar `Log.d("MI_TAG", "Valor de variable: $variable")` o `Log.e("MI_TAG", "Error ocurrido", excepcion)` para imprimir valores de variables o trazas de flujo en el Logcat. Esto puede ser más rápido para verificaciones puntuales.
      * **Control de Excepciones (`try-catch`):** Añadir bloques `try-catch` a medida que se implementan operaciones que son propensas a errores (E/S de archivos, operaciones de base de datos, conversiones de datos que podrían fallar). No esperar al final para "parchear" con manejo de errores.

    Un enfoque metódico, iterativo y con pruebas constantes es significativamente más eficiente y menos propenso a errores catastróficos que intentar construir toda la aplicación de una sola vez. Las "buenas prácticas" no son solo para proyectos grandes y a largo plazo; ayudan a mantener la cordura, la calidad y el control del tiempo en un entorno de examen. Aunque pueda parecer que escribir pruebas o añadir logs consume tiempo, a menudo ahorra mucho más tiempo a largo plazo al reducir drásticamente el tiempo dedicado a depurar errores complejos y difíciles de rastrear. Se debe adoptar este flujo de trabajo disciplinado.

### 2.4. Errores Comunes y Consejos Finales

Conocer los errores típicos y tener una estrategia de revisión final puede ser decisivo.

  * **Principales Tropiezos a Evitar (Errores Comunes en Exámenes PMDM):**

      * **Errores de Ciclo de Vida de `Activity` o `Fragment`:**
          * Realizar inicializaciones de vistas (`findViewById`, acceso a `viewBinding`) antes de que el layout haya sido inflado (`setContentView` en `Activity`, `onCreateView` en `Fragment`).
          * Acceder a recursos o realizar operaciones que dependen del estado de la `Activity`/`Fragment` en el método incorrecto del ciclo de vida (ej. iniciar una carga de datos pesada en `onResume` repetidamente sin control).
          * Olvidar guardar y restaurar el estado de la `Activity` o `Fragment` en caso de destrucción y recreación por cambios de configuración (ej. rotación de pantalla), si es relevante para la funcionalidad.
      * **Excepciones `NullPointerException` (NPE):**
          * Intentar usar un objeto que no ha sido inicializado (es `null`).
          * `findViewById` devuelve `null` porque el ID es incorrecto o el layout no es el esperado.
          * Intentar operar sobre un `Cursor` de base de datos que es `null` (porque la consulta falló o no devolvió resultados y no se verificó) o que ya ha sido cerrado.
          * Acceder a elementos de una lista o array con un índice fuera de límites.
      * **Errores Comunes con SQLite:**
          * Nombres de tabla o columna mal escritos en las sentencias SQL o al usar `ContentValues` (sensible a mayúsculas/minúsculas).
          * Tipos de datos incompatibles entre lo que se intenta insertar y lo definido en la tabla.
          * Olvidar llamar a `getWritableDatabase()` o `getReadableDatabase()` antes de operar con la BD.
          * **No cerrar el `Cursor`** después de usarlo (`cursor.close()`). Esto es una fuente común de fugas de memoria y problemas.
          * No cerrar la base de datos (`db.close()`) cuando ya no se necesita (aunque la gestión de esto puede variar; `SQLiteOpenHelper` gestiona parte de esto, pero los cursores siempre hay que cerrarlos).
          * Errores de `UNIQUE constraint` al insertar datos duplicados en columnas marcadas como únicas (ej. login, email).
      * **Problemas con `Adapter` y `ListView`/`RecyclerView`:**
          * Los datos no se muestran o la lista aparece vacía:
              * Olvidar llamar a `adapter.notifyDataSetChanged()` después de que los datos del adapter han cambiado.
              * El adapter no está correctamente configurado o asignado al `ListView`/`RecyclerView`.
              * El layout del ítem (`list_item_*.xml`) es incorrecto o las vistas dentro de él no tienen los IDs correctos.
              * La lista de datos pasada al adapter está vacía o es `null`.
          * Errores en `getView()` (ListView) o `onBindViewHolder()` (RecyclerView) al acceder a datos o vistas.
      * **Manejo de Hilos (Threading):**
          * Realizar operaciones de red o de base de datos largas y bloqueantes directamente en el hilo principal (UI thread). Esto causa la temida excepción ANR (Application Not Responding).
          * Intentar actualizar la UI (ej. cambiar el texto de un `TextView`) desde un hilo de fondo directamente. Esto lanzará una `CalledFromWrongThreadException`. Se debe usar `runOnUiThread {... }` (en Activities), `view.post {... }`, o mecanismos de coroutines/handlers para pasar la actualización al hilo principal.
      * **Permisos Olvidados o Mal Gestionados:**
          * Si la aplicación necesita acceder a internet, leer/escribir en almacenamiento externo (si fuera el caso, aunque para el examen tipo parece centrarse en interno), usar la cámara, etc., y no se declara el permiso correspondiente en `AndroidManifest.xml`.
          * Para permisos "peligrosos" (desde Android 6.0), no solo basta declararlos, sino que hay que solicitar la aprobación del usuario en tiempo de ejecución. (Menos común en exámenes básicos que se centren en almacenamiento interno y BD).
      * **Errores de Lógica en `SharedPreferences`:**
          * Usar claves incorrectas al guardar o leer datos (un error tipográfico en la `String` de la clave).
          * Olvidar llamar a `editor.apply()` o `editor.commit()` después de hacer cambios con el `Editor` de `SharedPreferences`. Sin esto, los cambios no se guardan.
          * Leer un tipo de dato incorrecto (ej. intentar leer un `Int` con `getString()`).

  * **Importancia de Seguir las Especificaciones del Examen:**

      * **Nombres:** Si el examen pide que una clase se llame `UserDatabaseHelper`, o que un layout se llame `main_activity.xml`, o que un ID de `EditText` sea `editTextUserName`, se deben usar esos nombres exactos. Los correctores pueden tener scripts o buscar específicamente esos nombres.
      * **Estructura de Paquetes:** Si se da una estructura de paquetes, seguirla.
      * **Tecnologías Específicas:** Si se pide explícitamente usar `Streams`, o `SharedPreferences`, o `SQLite`, se debe usar esa tecnología. Sustituirla por otra (aunque sea más familiar) sin una justificación muy clara (y si el tiempo lo permite) puede llevar a una penalización, ya que parte de la evaluación es la capacidad de usar las herramientas indicadas.
      * Estos detalles, que pueden parecer menores, a menudo tienen una puntuación asignada o contribuyen a la evaluación general de la atención al detalle y el seguimiento de instrucciones.

  * **Revisión Final (Últimos 15-20 minutos del Examen):**
    Reservar tiempo al final para una revisión es crucial.

    1.  **Releer Enunciado vs. Solución Implementada:** Repasar cada pregunta y sub-requisito del examen y verificar que se ha abordado en la solución. Hacer un checklist mental o en papel.
    2.  **Probar Flujos Principales de la Aplicación:** Ejecutar la aplicación en el emulador/dispositivo y probar las funcionalidades clave una última vez:
          * Flujo de Login (usuario correcto, usuario incorrecto).
          * Flujo de Registro (crear nuevo usuario, verificar si se guarda).
          * Selección de avatar (¿funciona la selección y se muestra?).
          * Visualización y Modificación de datos en la pantalla Principal (¿se cargan los datos?, ¿se guardan los cambios?).
          * Cierre de sesión.
    3.  **Limpiar Código (Si hay tiempo):**
          * Quitar `Log.d` o `println` excesivos que se usaron para depuración.
          * Eliminar comentarios de "TODO" que no se completaron o código comentado que ya no es relevante.
          * Un código limpio es más fácil de evaluar.
    4.  **Verificar Nombres y Convenciones:** Un último vistazo rápido para asegurar que se siguieron las especificaciones de nombrado de clases, archivos, IDs, etc.
    5.  **¡ASEGURAR QUE EL PROYECTO COMPILA Y CORRE\!** Este es el punto más fundamental de la revisión. Un proyecto que no compila o que crashea al inicio recibirá una puntuación muy baja o nula, independientemente de lo bien que estén algunas partes aisladas. Entregar un proyecto funcional, aunque alguna funcionalidad menor esté incompleta, es siempre mejor.

    Conocer los errores comunes permite estar más alerta durante la codificación para anticiparlos y evitarlos. La atención meticulosa al detalle en el seguimiento de las especificaciones del examen y una revisión final exhaustiva pueden marcar una diferencia significativa en la calificación. Esta "lista de verificación mental" de errores comunes y pasos de revisión debe ser parte de la estrategia para el día del examen.

-----

## Conclusión

Este informe ha buscado proporcionar una preparación integral para el examen de recuperación de PMDM, abordando tanto la resolución técnica de un examen tipo como una guía metodológica para el estudio y la ejecución el día de la prueba.

Los puntos más importantes a retener son:

  * **Dominio de los Fundamentos:** La inaccesibilidad de ciertos recursos específicos del curso subraya que una comprensión profunda de los componentes centrales de Android (`Activity`, `Intent`, `Layouts`, `Adapters`, `SharedPreferences`, `SQLite`, manejo de archivos con `Streams`, gestión de errores) es absolutamente esencial.
  * **Práctica Constante y Deliberada:** La teoría debe complementarse con la implementación práctica de pequeñas aplicaciones y funcionalidades. Recrear escenarios similares a los del examen y familiarizarse con el entorno de Android Studio, incluyendo su depurador, es crucial.
  * **Estrategia Metódica el Día del Examen:** Desde el análisis inicial del enunciado, el desglose de problemas, la implementación incremental con pruebas frecuentes, hasta la revisión final, seguir un plan estructurado ayuda a gestionar el tiempo y la complejidad eficazmente.
  * **Atención al Detalle:** Seguir las especificaciones del examen (nombres, tecnologías) y proporcionar un feedback claro al usuario y un manejo robusto de errores son aspectos que demuestran profesionalismo y competencia.

Se reitera la confianza en la capacidad del estudiante para prepararse adecuadamente y superar este desafío. El éxito en el examen del 5 de junio dependerá en gran medida de la dedicación al estudio y la aplicación activa de los conceptos y estrategias aquí presentados. Este informe es una guía extensa y una herramienta de apoyo; la clave final reside en el esfuerzo personal y la práctica diligente. ¡Mucho ánimo y éxito\!