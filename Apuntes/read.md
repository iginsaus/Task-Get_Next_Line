**Explicación general del comando **`read`\
El comando `read` es una función de C que se utiliza para leer datos de
un archivo o dispositivo. Se define en el encabezado `stdio.h` y toma
tres argumentos principales:

1.  **Descriptor de archivo:** El descriptor de archivo del archivo o
    dispositivo del que se desea leer. Este descriptor se obtiene al
    abrir el archivo con el comando `open`.

2.  **Buffer de destino:** Un puntero a una memoria donde se almacenarán
    los datos leídos.

3.  **Número de bytes a leer:** Un valor de tipo `size_t` que indica la
    cantidad máxima de bytes que se desea leer.\
    **Retorno de valor:**\
    La función `read` devuelve el número de bytes leídos. Si se produce
    un error, devuelve `-1` y establece la variable `errno` con el
    código de error correspondiente.\
    **Uso del comando **`read`** en get_next_line**\
    En get_next_line, el comando `read` se utiliza para leer datos del
    archivo abierto línea por línea. La función sigue estos pasos:


1.  **Lee del archivo:** Utiliza el comando `read` para leer datos del
    archivo abierto en el buffer de lectura. La función especifica el
    número de bytes a leer como el tamaño del buffer, lo que significa
    que intenta leer una línea completa del archivo.

2.  **Comprueba si hay errores:** Si la función `read` devuelve `-1`,
    get_next_line establece la variable `errno` con el código de error
    correspondiente y devuelve `NULL`.

3.  **Actualiza el puntero del buffer:** Si la lectura se realiza
    correctamente, get_next_line actualiza el puntero del buffer para
    apuntar al siguiente carácter leído.

4.  **Comprueba el final del archivo:** Si la
    función `read` devuelve `0`, significa que se ha llegado al final
    del archivo. En este caso, get_next_line establece la
    variable `eof` a `1` para indicar que no hay más líneas que leer y
    devuelve `NULL`.

5.  **Termina la línea:** Si la función `read` devuelve un número
    positivo, significa que se ha leído una línea completa del archivo.
    En este caso, get_next_line agrega un terminador de línea (`\``n`)
    al final del buffer, si aún no lo tiene, y actualiza el
    puntero `n` para indicar la longitud de la línea leída.\
    **Ejemplo de uso del comando **`read`** en get_next_line:**\
    C\
    `int get_next_line(int fd, char *line, int *n) ``{`\
    `  // ...`\
    \
    `  // Lee del archivo`\
    `  ssize_t bytes_read = read(fd, buffer, BUFFER_SIZE);`\
    `  if (bytes_read == -1) ``{`\
    `    errno = EIO;`\
    `    return -1;`\
    `  ``}`\
    \
    `  // ...`\
    \
    `  return 0;`\
    `}`\
    \
    \
    **Importancia del uso correcto del comando **`read`\
    El uso correcto del comando `read` es crucial para el correcto
    funcionamiento de get_next_line. Si la función no se utiliza
    correctamente, puede leer datos incorrectos o incompletos, lo que
    podría afectar a la lectura del archivo línea por línea.\
    **Conclusión:**\
    El comando `read` es una herramienta esencial en get_next_line, ya
    que permite leer datos del archivo abierto línea por línea. Su uso
    correcto garantiza que la función pueda acceder al archivo de forma
    segura y eficiente, obteniendo las líneas del archivo de manera
    precisa.
