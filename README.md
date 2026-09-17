# Decisiones tecnicas - prueba-diagnostica-java-trainee

Al momento de crear las clases, decidi hacer uso de la libreria lombok, ya que asi podia ahorrarme tiempo en escribir metodos Getter, Setter y ToString().

Para evitar hacer uso de muchas variables, decidi crear una lista para los productos que puede tener una orden:

`List<Producto> productos = new ArrayList<>();`

De esta forma, en el metodo `agregarProducto()` puedo hacer la validacion de una vez. Si la condicion se cumple, el metodo retona false, dando a entender que no se agrego el producto a la lista, caso contrario, agrega otro producto a la lista.

### Creacion de datos de prueba
Use un archivo para dejar datos quemados, de esta forma el programa no empieza con 0 datos y puede probarse de forma mas rapida.

### Funciones en el main
En el main, hay algunas funciones que use como apoyo, por ejemplo:

`leerEntero(Scanner sc, String mensaje)`: la cree para no repetir el mismo try/catch cada vez que necesito leer un numero. Imprime el mensaje, lee la linea y si el usuario escribe algo que no sea un numero (letras, texto vacio, etc.), avisa y vuelve a pedirlo en un bucle, en lugar de que el programa se caiga con una excepcion. La uso en todos los lugares donde se lee un entero (menu principal, tipo de pago, seleccion de cliente/orden/producto).

`crearCliente(Scanner sc)`: originalmente era un metodo `void`, pero lo cambie para que retorne el `Cliente` que crea. Asi puedo reutilizarlo tanto desde el menu principal como desde `crearOrden`, cuando el usuario elige crear un cliente nuevo al mismo tiempo que crea la orden, sin duplicar la logica de captura de datos.

`asignarClienteExistente(Scanner sc, Orden orden)`: separe esta logica de `crearOrden` para no sobrecargar esa funcion con demasiadas responsabilidades. Se encarga unicamente de mostrar la lista de clientes ya creados y asignar el seleccionado a la orden, validando que la posicion elegida exista.
