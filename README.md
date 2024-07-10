<h1 align="center">doGet</h1>
<p>El método doGet es una parte fundamental de la programación de servlets en Java. Es un método que debes sobrescribir cuando necesitas manejar solicitudes HTTP GET en tu aplicación web. Aquí tienes una explicación detallada de cómo funciona y cómo se utiliza:</p>

<h3>Concepto del método doGet</h3>

El método `doGet` se encuentra en la clase `HttpServlet` y es utilizado para manejar las solicitudes HTTP GET. Una solicitud GET es típicamente usada por los navegadores web para solicitar un recurso del servidor, como una página HTML, un archivo CSS, una imagen, etc.

<h3>Firma del método doGet</h3>

El método `doGet` tiene la siguiente firma:

```java
protected void doGet(HttpServletRequest request, HttpServletResponse response)
        throws ServletException, IOException {
    // implementación
}
```

<h3>Parámetros</h3>

-  <b>HttpServletRequest request</b>: Este objeto contiene la información de la solicitud HTTP enviada por el cliente. Puedes usarlo para obtener datos como parámetros de consulta, cabeceras, cookies, etc.
-  <b>HttpServletResponse response</b>: Este objeto es utilizado para construir y enviar la respuesta HTTP al cliente. Puedes usarlo para definir el tipo de contenido de la respuesta, establecer cabeceras, escribir datos en el cuerpo de la respuesta, etc.

<h3>Sobrescribiendo el método doGet</h3>

Para crear un servlet que maneje solicitudes GET, debes extender la clase HttpServlet y sobrescribir el método `doGet`.

```java
import java.io.IOException;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

public class MyServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        // Establece el tipo de contenido de la respuesta
        response.setContentType("text/html");

        // Obtiene el objeto PrintWriter para escribir la respuesta
        PrintWriter out = response.getWriter();

        // Escribe el contenido de la respuesta
        out.println("<html><body>");
        out.println("<h1>Hola, mundo!</h1>");
        out.println("</body></html>");
    }
}
```

<h3>Detalles importantes</h3>

-  <b>Establecer el Tipo de Contenido</b>: Es importante establecer el tipo de contenido de la respuesta utilizando response.setContentType(String type). Esto asegura que el cliente (por ejemplo, el navegador web) interprete correctamente los datos de la respuesta.

-  <b>Escribir la Respuesta</b>: Utiliza el objeto PrintWriter obtenido de response.getWriter() para escribir los datos que deseas enviar al cliente. Esto puede ser HTML, texto plano, JSON, etc.

-  <b>Manejo de Excepciones</b>: El método doGet puede lanzar ServletException y IOException, por lo que debes asegurarte de manejar o declarar estas excepciones adecuadamente.

<h1 align="center">Algunos Métodos de la clase HttpServletRequest</h1>
<h2>getMethod()</h2>
<p>Este método devuelve el método HTTP de la solicitud. Los métodos HTTP comunes incluyen GET, POST, PUT, DELETE, etc. Esto es útil para determinar qué tipo de operación se está solicitando.</p>

```java
String method = request.getMethod();
System.out.println("HTTP Method: " + method);
```
Salida posible: "HTTP Method: GET"


<h2>getRequestURI()</h2>
<p>Este método devuelve la URI de la solicitud desde el contexto del servidor web. La URI es la parte de la URL que viene después del nombre del servidor y el puerto, pero antes de cualquier parámetro de consulta.</p>

```java
String requestURI = request.getRequestURI();
System.out.println("Request URI: " + requestURI);
```
Salida posible: "Request URI: /myapp/myservlet"

<h2>getRequestURL()</h2>
<p>Este método devuelve la URL completa de la solicitud. La URL incluye el protocolo, el nombre del servidor, el puerto, y la URI del recurso solicitado.</p>

```java
StringBuffer requestURL = request.getRequestURL();
System.out.println("Request URL: " + requestURL.toString());
```
Salida posible: "Request URL: http://www.example.com:8080/myapp/myservlet"

<h2>getContextPath()</h2>
<p>Este método devuelve el contexto de la aplicación web. El contexto de la aplicación es la parte de la URL que se asigna a tu aplicación en el servidor. Si la aplicación está desplegada en el directorio raíz, el contexto será una cadena vacía.</p>

```java
String contextPath = request.getContextPath();
System.out.println("Context Path: " + contextPath);
```
Salida posible: "Context Path: /myapp"

<h2>getServletPath()</h2>
<p>Este método devuelve la parte de la URI de la solicitud que corresponde al servlet que está manejando la solicitud. Esto excluye el contexto de la aplicación y cualquier información adicional después del nombre del servlet.</p>

```java
String servletPath = request.getServletPath();
System.out.println("Servlet Path: " + servletPath);
```
Salida posible: "Servlet Path: /myservlet"

<h2>getLocalAddr()</h2>
<p>Este método devuelve la dirección IP del servidor en la que se recibió la solicitud. Es útil cuando el servidor tiene múltiples interfaces de red o está detrás de un balanceador de carga.</p>

```java
String localAddr = request.getLocalAddr();
System.out.println("Local Address: " + localAddr);
```
Salida posible: "Local Address: 192.168.1.100"

<h2>getLocalPort()</h2>
<p>Este método devuelve el puerto en el que el servidor está recibiendo la solicitud. Esto es útil cuando el servidor está escuchando en múltiples puertos o cuando necesitas conocer el puerto exacto utilizado para la conexión.</p>

```java
int localPort = request.getLocalPort();
System.out.println("Local Port: " + localPort);
```
Salida posible: "Local Port: 8080"

<h2>getScheme()</h2>
<p>Este método devuelve el esquema de la solicitud, que es el protocolo utilizado (por ejemplo, "http" o "https"). Esto es útil para determinar si la solicitud fue realizada a través de HTTP o HTTPS.</p>

```java
String scheme = request.getScheme();
System.out.println("Scheme: " + scheme);
```
Salida posible: "Scheme: https"

<h2>getHeader</h2>

Ejemplos comunes de cómo se puede usar `getHeader` en un servlet:


- Obtener el tipo de contenido aceptado</b>:
```java
String accept = request.getHeader("Accept");
System.out.println("Accept: " + accept);
```

- Obtener la codificación aceptada:
```java
String acceptEncoding = request.getHeader("Accept-Encoding");
System.out.println("Accept-Encoding: " + acceptEncoding);
```

- Obtener la lengua preferida:
```java
String acceptLanguage = request.getHeader("Accept-Language");
System.out.println("Accept-Language: " + acceptLanguage);
```

- Obtener la cabecera de referer:
```java
String referer = request.getHeader("Referer");
System.out.println("Referer: " + referer);
```

<h2>getRemoteAddr</h2>

El método `getRemoteAddr` de la clase `HttpServletRequest` se utiliza para obtener la dirección IP del cliente que realizó la solicitud. Esta información es útil para propósitos de registro, análisis y control de acceso basado en la dirección IP del cliente.

<h3>Firma del método</h3>

```java
public String getRemoteAddr()
```

- Este método no tiene parámetros.
- Devuelve una String que contiene la dirección IP del cliente que hizo la solicitud.

<h3>Usos comunes de getRemoteAddr</h3>

- <b>Registro de actividad del cliente</b>: Almacenar la dirección IP del cliente en los registros del servidor para análisis de uso y auditoría.
- <b>Control de acceso</b>: Implementar restricciones basadas en la dirección IP para permitir o denegar el acceso a ciertos recursos.
- <b>Detección de fraudes</b>: Utilizar la dirección IP para identificar patrones sospechosos y prevenir actividades fraudulentas.

<h1 align="center">Json</h1>
<p>JSON (JavaScript Object Notation) es un formato de texto ligero y fácil de leer/escribir para el intercambio de datos. Se utiliza comúnmente para transmitir datos entre un servidor y una aplicación web, así como para almacenar y organizar datos estructurados de manera sencilla.</p>
<h3>Características de JSON:</h3>

- <b>Simplicidad</b>: Es fácil de entender y usar, tanto por humanos como por máquinas.
- <b>Formato de texto</b>: Los datos se representan como texto legible, lo que facilita la lectura y el debug.
- <b>Lenguaje independiente</b>: Aunque se deriva de JavaScript, JSON es compatible con muchos lenguajes de programación.

<h3>Estructura de JSON:</h3>

- <b>Objetos</b>: Representados por llaves {} y contienen pares clave-valor. Ejemplo:

```json
{
  "nombre": "Juan",
  "edad": 30,
  "casado": true
}
```

- <b>Arreglos (Arrays)</b>: Representados por corchetes [] y contienen una lista de valores. Ejemplo:

```json
[
  "rojo",
  "verde",
  "azul"
]
```

<h3>Usos de JSON:</h3>

- <b>Intercambio de datos</b>: JSON se usa ampliamente para transmitir datos entre un cliente y un servidor en aplicaciones web a través de AJAX (Asynchronous JavaScript and XML).
- <b>Configuración</b>: Muchas aplicaciones y servicios utilizan archivos JSON para almacenar configuraciones.
- <b>Almacenamiento de datos</b>: Es común almacenar datos estructurados en bases de datos NoSQL como MongoDB, que utilizan JSON o formatos similares.

<h3>Ventajas de JSON:</h3>

- <b>Legibilidad</b>: El formato es fácil de leer y entender.
- <b>Compatibilidad</b>: Es compatible con casi todos los lenguajes de programación modernos.
- <b>Ligero</b>: Es menos verboso que XML, lo que reduce el tamaño de los datos transmitidos.

<h1 align="center">ObjectMapper</h1>

La clase `ObjectMapper` es una parte fundamental de la biblioteca Jackson en Java, que se utiliza para la conversión de objetos Java a JSON y viceversa. Jackson es una de las bibliotecas más populares para trabajar con JSON en Java debido a su facilidad de uso, flexibilidad y rendimiento.

<h3>Características y Usos de ObjectMapper:</h3>

- <b>Serialización (Convertir de Objeto Java a JSON)</b>:
La serialización es el proceso de convertir un objeto Java en una cadena JSON. Esto es útil cuando se necesita enviar datos desde una aplicación Java a un servicio web que espera recibir JSON.

```java
ObjectMapper mapper = new ObjectMapper();
User user = new User("Juan", 30);
String jsonString = mapper.writeValueAsString(user);
System.out.println(jsonString); // {"name":"Juan","age":30}
```

- <b>Deserialización (Convertir de JSON a Objeto Java)</b>:
La deserialización es el proceso de convertir una cadena JSON en un objeto Java. Esto es útil cuando recibes JSON de un servicio web y necesitas trabajar con él en tu aplicación Java.

```java
String jsonString = "{\"name\":\"Juan\",\"age\":30}";
ObjectMapper mapper = new ObjectMapper();
User user = mapper.readValue(jsonString, User.class);
System.out.println(user.getName()); // Juan
```

- <b>Lectura y Escritura desde/para Archivos</b>:
`ObjectMapper` puede leer y escribir JSON directamente desde y hacia archivos.

```java
// Escritura en archivo
mapper.writeValue(new File("user.json"), user);

// Lectura desde archivo
User userFromFile = mapper.readValue(new File("user.json"), User.class);
```

- <b>Configuración y Personalización</b>:
`ObjectMapper` permite configuraciones y personalizaciones avanzadas, como la inclusión o exclusión de propiedades, manejo de fechas, formatos personalizados, etc.

```java
mapper.configure(SerializationFeature.INDENT_OUTPUT, true); // Formatear JSON con indentación
```

<h3>Métodos Comunes:<h3></h3>
        
- <b>writeValueAsString(Object value)</b>: Convierte un objeto en una cadena JSON.
- <b>writeValue(File resultFile, Object value)</b>: Escribe JSON en un archivo.
- <b>readValue(String content, Class<T> valueType)</b>: Convierte una cadena JSON en un objeto Java.
- <b>readValue(File src, Class<T> valueType)</b>: Lee JSON desde un archivo y lo convierte en un objeto Java.
