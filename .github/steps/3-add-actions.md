## Paso 3: Agregar un paso a tu archivo de flujo de trabajo

_¡Buen trabajo agregando un trabajo a tu flujo de trabajo! :dancer:_

Los flujos de trabajo tienen trabajos, y los trabajos tienen pasos. Entonces, ahora agregaremos un paso a tu flujo de trabajo.

**¿Qué son los _pasos_?**: Los pasos de acciones se ejecutan, en el orden especificado, de arriba hacia abajo, cuando se procesa un trabajo de flujo de trabajo. Cada paso debe pasar para que se ejecute el siguiente paso.

Cada paso consta de un script de shell que se ejecuta o una referencia a una acción que se ejecuta. Cuando hablamos de una acción (con una "a" minúscula) en este contexto, nos referimos a una unidad de código reutilizable. Puedes obtener más información sobre las acciones en "[Encontrar y personalizar acciones](https://docs.github.com/en/actions/learn-github-actions/finding-and-customizing-actions)", pero por ahora usaremos un script de shell en nuestro paso de flujo de trabajo.

Actualiza tu flujo de trabajo para que publique un comentario en nuevas pull requests. Esto se hará utilizando un script [bash](https://en.wikipedia.org/wiki/Bash_%28Unix_shell%29) y [GitHub CLI](https://cli.github.com/).



### :keyboard: Actividad: Agregar un paso a tu archivo de flujo de trabajo

1. Aún trabajando en la rama `welcome-workflow`, abre tu archivo `welcome.yml`.
2. Actualiza el contenido del archivo a:


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
       steps:
         - run: gh pr comment $PR_URL --body "Welcome to the repository!"
           env:
             GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
             PR_URL: ${{ github.event.pull_request.html_url }}
   ```
   
    **Nota:** El paso que has agregado utiliza GitHub CLI (`gh`) para agregar un comentario cuando se abre una solicitud de extracción. Para permitir que GitHub CLI publique un comentario, establecemos la variable de entorno `GITHUB_TOKEN` con el valor del secreto `GITHUB_TOKEN`, que es un token de acceso de instalación creado cuando se ejecuta el flujo de trabajo. Para obtener más información, consulta "[Autenticación automática de token](https://docs.github.com/en/actions/security-guides/automatic-token-authentication)". Establecemos la variable de entorno `PR_URL` con la URL de la nueva solicitud de extracción creada, y la usamos en el comando `gh`.


1. Haz clic en **Commit changes** en la parte superior derecha del editor de flujo de trabajo.
2. Escribe tu mensaje de confirmación y confirma tus cambios directamente en tu rama.
3. Espera unos 20 segundos, luego actualiza esta página (la que estás siguiendo las instrucciones). Otro flujo de trabajo se ejecutará y reemplazará el contenido de este archivo README con instrucciones para el próximo paso.
