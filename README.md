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
