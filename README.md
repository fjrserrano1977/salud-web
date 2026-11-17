# Salud y deporte · seguimiento

Web estática (un solo archivo, `index.html`) para registrar peso, composición corporal, medidas y calorías diarias.
Los datos se guardan en el dispositivo y se sincronizan con un archivo JSON de un repositorio de GitHub,
así que lo que anotes desde el móvil aparece en el ordenador y al revés. Git guarda además el historial completo.

## 1. Privacidad: lee esto antes de subir nada

Son datos de salud. Si el repositorio es **público**, cualquiera puede leerlos.

- **Recomendado, dos repositorios:** uno público solo con `index.html` (la web, sin datos) y otro **privado**
  para los datos (por ejemplo `salud-datos`). La web lee y escribe el repositorio privado con tu token.
- **Alternativa, un solo repositorio privado:** GitHub Pages desde repositorios privados exige un plan de pago.

## 2. Publicar la web

1. Sube `index.html` a la rama `main` del repositorio de la web (Add file → Upload files).
2. Settings → Pages → Build and deployment → Deploy from a branch → `main` / `(root)`.
3. En un minuto estará en `https://TU_USUARIO.github.io/NOMBRE_DEL_REPO/`.

## 3. Repositorio de datos

Crea el repositorio privado con un archivo inicial (por ejemplo, marca "Add a README").
No hace falta crear `data/seguimiento.json`: la primera sincronización lo crea.

## 4. Token de acceso

GitHub → Settings → Developer settings → Personal access tokens → **Fine-grained tokens** → Generate new token.

- Repository access: *Only select repositories* → el repositorio de datos.
- Permissions → Repository permissions → **Contents: Read and write**.
- Caducidad: la que prefieras (al caducar, genera otro y pégalo de nuevo).

## 5. Conectar cada dispositivo

Abre la web → pestaña **Sync** → usuario, repositorio de datos, rama (`main`) y token → *Guardar y sincronizar*.
El token queda solo en ese dispositivo; repite el paso en cada móvil u ordenador. Para tenerla como app en el móvil:
menú del navegador → *Añadir a pantalla de inicio*.

## Cómo sincroniza

- Al abrir la web, al volver a ella y 2 segundos después de cada cambio.
- Se fusionan los datos por fecha: gana el registro más reciente de cada día, y los borrados se propagan.
- Si dos dispositivos editan a la vez, se vuelve a leer y fusionar antes de guardar; no se pierde nada.
- Sin conexión sigue funcionando y sincroniza al recuperarla.

## Migrar los datos del artefacto antiguo

1. En el artefacto antiguo, baja hasta "Copia de seguridad", pulsa *Mostrar mis datos* y copia el texto.
2. En esta web: pestaña **Sync** → *Importar o exportar datos* → pega el texto → *Importar y fusionar*.
