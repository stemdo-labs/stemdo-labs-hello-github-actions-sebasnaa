## Paso 2: Agrega un trabajo a tu archivo de flujo de trabajo

_¡Buen trabajo! :tada: ¡Has agregado un archivo de flujo de trabajo!_

Aquí está lo que significan las entradas en el archivo `welcome.yml`, en la rama `welcome-workflow`:

- `name: Post welcome comment` le da a tu flujo de trabajo un nombre. Este nombre aparecerá en la pestaña Actions de tu repositorio.
- `on: pull_request: types: [opened]` indica que tu flujo de trabajo se ejecutará cada vez que alguien abra una solicitud de extracción en tu repositorio.
- `permissions` asigna permisos al flujo de trabajo para operar en el repositorio.
- `pull-requests: write` le da al flujo de trabajo permiso para escribir en las solicitudes de extracción. Esto es necesario para crear el comentario de bienvenida.

A continuación, necesitamos especificar los trabajos a ejecutar.

**¿Qué es un _trabajo_?**: Un trabajo es un conjunto de pasos en un flujo de trabajo que se ejecutan en el mismo runner (un runner es un servidor que ejecuta tus flujos de trabajo cuando se activan). Los flujos de trabajo tienen trabajos, y los trabajos tienen pasos. Los pasos se ejecutan en orden y dependen entre sí. Más adelante en el curso, agregarás pasos a tu flujo de trabajo. Para obtener más información sobre los trabajos, consulta "[Trabajos](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions#jobs)".

En la siguiente actividad, agregarás un trabajo de "build" a tu flujo de trabajo. Especificarás `ubuntu-latest` como el runner de trabajo más rápido y económico disponible. Si deseas leer más sobre por qué usaremos ese runner, consulta la explicación de código para la línea `runs-on: ubuntu-latest` en el artículo "[Understanding the workflow file](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions#understanding-the-workflow-file)".


### :keyboard: Actividad: Agregar un trabajo a tu archivo de flujo de trabajo

1. En una pestaña de navegador separada, asegúrate de estar en la rama `welcome-workflow` y abre tu archivo `.github/workflows/welcome.yml`.
2. Edita el archivo y actualiza su contenido a:

   ```yaml copy
   name: Post welcome comment
   on:
     pull_request:
       types: [opened]
   permissions:
     pull-requests: write
   jobs:
     build:
       name: Post welcome comment
       runs-on: ubuntu-latest
   ```

1. Click **Commit changes** in the top right of the workflow editor.
1. Type a commit message and commit your changes directly to the `welcome-workflow` branch.
1. Wait about 20 seconds, then refresh this page (the one you're following instructions from). Another workflow will run and will replace the contents of this README file with instructions for the next step.

1. Haz clic en **Commit changes** en la parte superior derecha del editor de flujo de trabajo.
2. Escribe un mensaje de confirmación y confirma tus cambios directamente en la rama `welcome-workflow`.
3. Espera unos 20 segundos, luego actualiza esta página (la que estás siguiendo las instrucciones). Otro flujo de trabajo se ejecutará y reemplazará el contenido de este archivo README con instrucciones para el próximo paso.
