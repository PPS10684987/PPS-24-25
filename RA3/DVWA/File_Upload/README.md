En esta parte trabajé con la funcionalidad de subir archivos, que es algo muy común en muchas páginas web (como cuando subes una foto de perfil, un documento, etc.). El problema viene cuando esa subida no se controla bien y te deja subir archivos peligrosos, como por ejemplo uno que ejecute código en el servidor.

Nivel Low

En el nivel Low, la página no revisa prácticamente nada del archivo que subes. Preparé un archivo .php que tenía una reverse shell, que es un pequeño script que me permite conectarme al servidor desde mi máquina.

Subí ese archivo sin problema, y luego simplemente entré a la URL donde se guardó el archivo, algo como lo que se muestra en las siguiente imagenes:

Archivo creado:

![captura](../images/Captura14)

Subida del archivo:

![captura](../images/Captura11)

Conexion al archivo:

![captura](../images/Captura12)

Y en cuanto abrí la URL de mi archivo, se conectó automáticamente al servidor, dándome acceso como si estuviera dentro. Fue curioso ver que solo con subir un archivo y visitarlo podía tomar el control.

![captura](../images/Captura13)

Nivel Medium

Aquí ya no me dejaba subir un archivo .php. Me decía que el tipo de archivo no era válido. Pero descubrí una forma de engañar al sistema: fui a la pestaña de "Red" en las herramientas del navegador, edité la petición y cambié el tipo de archivo (el Content-Type) a algo como image/png.

![captura](../images/Captura15)
![captura](../images/Captura16)

A pesar de que el archivo seguía siendo .php, al cambiar eso y reenviar la petición, la web pensó que era una imagen y lo aceptó.

Después, accedí al archivo de la misma forma que en el nivel Low, y otra vez se me abrió una reverse shell, consiguiendo acceso al sistema.

![captura](../images/Captura17)
