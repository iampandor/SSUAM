#	Arquitectura

## Principios SOLID y Patrones de Diseño Arquitectónico

Los Principios SOLID son un conjunto de cinco directrices que ayudan a los desarrolladores a crear software que sea fácil de mantener y extender. Estos principios fueron introducidos por el ingeniero de software Robert C. Martin (Uncle Bob) y se han convertido en una base sólida para la programación orientada a objetos (POO) y el diseño de software en general. Los cinco principios SOLID son:

### 1. Principio de Responsabilidad Única (SRP - Single Responsibility Principle)

El SRP establece que una clase debe tener una única razón para cambiar. En otras palabras, una clase debe tener una sola responsabilidad o función. Esto significa que una clase no debe estar sobrecargada con múltiples responsabilidades que podrían cambiar por diferentes motivos.

**Ejemplo:** Supongamos que estamos desarrollando una aplicación de gestión de pedidos en línea. En lugar de tener una clase que maneje tanto el procesamiento de pedidos como la generación de facturas, deberíamos tener dos clases separadas: una para el procesamiento de pedidos y otra para la generación de facturas. Cada clase tiene una única responsabilidad y puede cambiar independientemente de la otra.


```
class  OrderProcessor  {
	public  void  processOrder(Order order)  {
	// Lógica para procesar el pedido  
	}
}
class  InvoiceGenerator  {
	public  void  generateInvoice(Order order)  {
	// Lógica para generar la factura
	}
}
```

### 2. Principio de Abierto/Cerrado (OCP - Open/Closed Principle)

El OCP establece que las entidades de software (clases, módulos, funciones, etc.) deben estar abiertas para extenderse pero cerradas para su modificación. Esto significa que debemos poder agregar nuevas funcionalidades a un sistema sin cambiar el código existente.

**Ejemplo:** Supongamos que estamos desarrollando un sistema de dibujo en el que se pueden crear diferentes tipos de formas. En lugar de modificar la clase Shape cada vez que agregamos una nueva forma, podemos seguir el OCP creando clases de formas nuevas que extiendan la clase Shape sin modificar su código original.

```
class  Shape  {
	// Métodos y propiedades comunes a todas las formas
}
class  Circle  extendsShape  {
	// Métodos y propiedades específicos de un círculo
}
class  Rectangle  extendsShape  {
	// Métodos y propiedades específicos de un rectángulo
}
```

### 3. Principio de Sustitución de Liskov (LSP - Liskov Substitution Principle)

El LSP establece que los objetos de una subclase deben poder sustituirse por objetos de la clase base sin afectar la integridad del programa. Esto significa que las subclases deben cumplir con la misma interfaz y comportamiento que la clase base.

**Ejemplo:** Supongamos que tenemos una clase base Bird (Ave) con un método fly (volar). Si creamos una subclase Penguin (Pingüino), que no puede volar, violaría el LSP. Para cumplir con este principio, podríamos tener una interfaz Flyable (Volador) que sea implementada solo por las clases de aves que pueden volar.


```
interface Flyable {
    public void fly();
}
class  Bird  {
    // A bird has wings and peak
}
class  Penguin extends  Bird  {
    // A penguin cannot fly
}
class  Pidgeon extends Bird implements Flyable{
    public void fly(){
        System.out.println("I can fly");
    }
}
```

### 4. Principio de Segregación de Interfaces (ISP - Interface Segregation Principle)

El ISP establece que una clase no debe verse obligada a implementar interfaces que no utiliza. En otras palabras, las interfaces deben ser específicas y contener solo los métodos que son relevantes para las clases que las implementan.

**Ejemplo:** Supongamos que estamos creando una interfaz de usuario (UI) para una aplicación y tenemos una interfaz llamada UIElement con métodos como render (renderizar) y onClick (al hacer clic). Si una clase Button solo necesita implementar onClick, no debería estar obligada a implementar el método render. En su lugar, podemos dividir la interfaz en dos: Renderable (Renderizable) y Clickable (Clicable).

```
interface  Renderable  {
	void  render();
}
interface  Clickable  {
	void  onClick();
}
classButton  implements  Clickable  {
	public  void  onClick()  {
		// Lógica para manejar el evento de clic en el botón
	}
}
```

### 5. Principio de Inversión de Dependencias (DIP - Dependency Inversion Principle)

El DIP establece que las dependencias deben ser hacia abajo y no hacia arriba. Esto significa que los módulos de alto nivel no deben depender de módulos de bajo nivel, ambos deben depender de abstracciones. Además, las abstracciones no deben depender de detalles, los detalles deben depender de abstracciones.

**Ejemplo:** Supongamos que estamos desarrollando un sistema de notificación en el que las clases de alto nivel envían notificaciones, pero no saben qué tipo de notificación se envía. Para seguir el DIP, podemos crear una abstracción Notification (Notificación) que las clases de alto nivel dependan en lugar de depender directamente de las implementaciones concretas.
```
interface  Notification  {
	void  send();
}
class  EmailNotification  implements  Notification  {
	public  void  send()  {
		// Lógica para enviar un correo electrónico
	}
}
classSMSNotification  implements  Notification  {
	public  void  send()  {
		// Lógica para enviar un mensaje de texto
	}
}
```
## Patrones de Diseño Arquitectónico

Además de los Principios SOLID, los Patrones de Diseño Arquitectónico son herramientas para diseñar sistemas de software robustos y escalables. Los patrones de diseño son soluciones probadas para problemas comunes de diseño de software.

### 1. Patrón Modelo-Vista-Controlador (MVC)

El patrón MVC es ampliamente utilizado en el desarrollo de aplicaciones web y de escritorio. Divide una aplicación en tres componentes principales:

-   **Modelo (Model)**: Representa la lógica de negocio y los datos de la aplicación.
-   **Vista (View)**: Es responsable de la presentación y la interfaz de usuario.
-   **Controlador (Controller)**: Maneja las solicitudes del usuario y coordina las acciones entre el Modelo y la Vista.

**Ejemplo:** Supongamos que estamos creando una aplicación web. El Modelo puede ser una clase que maneja la lógica de negocio y accede a la base de datos, la Vista puede ser una página HTML que muestra los datos y el Controlador puede ser una clase que gestiona las solicitudes HTTP y coordina la interacción entre el Modelo y la Vista.

```
// Modelo
class  ProductService  {
	public  Product  getProductById(int  id)  {
		// Lógica para obtener un producto de la base de datos
	}
}
// Vista  
class  ProductView  {
	public  voidrenderProduct(Product product)  {
		// Generar HTML para mostrar el producto
	}
}
// Controlador
class  ProductController  {
	private  ProductService productService;
	privateProductView productView;
	public  void  getProductDetails(int  productId)  {
		Product  product  =  productService.getProductById(productId);
		productView.renderProduct(product);
	}
}
```
### 2. Patrón Modelo-Vista-ViewModel (MVVM)

El patrón MVVM es una variante del patrón MVC que se utiliza comúnmente en el desarrollo de aplicaciones de una sola página (SPA) y aplicaciones móviles. Divide la aplicación en tres componentes:

-   **Modelo (Model)**: Representa la lógica de negocio y los datos.
-   **Vista (View)**: Representa la interfaz de usuario y se actualiza cuando cambia el Modelo.
-   **ViewModel (ViewModel)**: Actúa como un intermediario entre el Modelo y la Vista, proporcionando datos y lógica de presentación.

**Ejemplo:** Supongamos que estamos desarrollando una aplicación de seguimiento de tareas. El Modelo representa las tareas y su estado, la Vista muestra la lista de tareas y el ViewModel proporciona la lógica para filtrar y ordenar las tareas antes de mostrarlas en la Vista.
```
// Modelo 
class  Task  {
	private  String title;
	private  boolean  completed;
	// Getters y setters
}
// Vista
class  TaskView  {
	public  void  renderTasks(List<Task> tasks)  {
		// Generar la lista de tareas en la interfaz de usuario
	}
}
// ViewModel
class  TaskViewModel{
	private  List<Task> tasks;
	public  List<Task>  getFilteredTasks(boolean  showCompleted)  {
		// Aplicar filtros y ordenamientos a la lista de tareas
	}
}
```

### 3. Patrón Repositorio

El patrón Repositorio se utiliza para separar la lógica de acceso a datos de la lógica de negocio. Proporciona una capa de abstracción entre la aplicación y la base de datos, lo que facilita las operaciones CRUD (Crear, Leer, Actualizar, Eliminar) en la base de datos.

**Ejemplo:** Supongamos que estamos desarrollando una aplicación de gestión de empleados. El Repositorio se encargaría de realizar consultas a la base de datos para obtener y almacenar información de los empleados, mientras que la lógica de negocio se centraría en las operaciones relacionadas con los empleados.
```
interface  EmployeeRepository  {
	Employee  getById(int  id);
	List<Employee>  getAll();
	void save(Employee employee);  void  delete(int  id);
}
class  EmployeeService  {
	private EmployeeRepository employeeRepository;
	public  List<Employee>  getAllEmployees()  { 
		return employeeRepository.getAll();
	}
	public  void  addEmployee(Employee employee)  {
		employeeRepository.save(employee);
	}
}
```

### 4. Patrón Inyección de Dependencias (DI - Dependency Injection)

El patrón DI se utiliza para gestionar las dependencias entre los componentes de una aplicación. En lugar de que un componente cree directamente sus dependencias, se le proporcionan desde el exterior (inyectadas), lo que facilita la prueba y la flexibilidad.

**Ejemplo:** Supongamos que estamos desarrollando una aplicación de comercio electrónico. En lugar de que la clase ShoppingCart cree directamente una instancia de ProductService, la instancia de ProductService se inyecta en ShoppingCart a través de un constructor o un método setter. Esto permite intercambiar fácilmente diferentes implementaciones de ProductService sin modificar ShoppingCart.

```
class  ShoppingCart  {
	private  ProductService productService;
	// Constructor de inyección de dependencias
	public  ShoppingCart(ProductService productService)  {
		this.productService = productService;
	}
	public  void  addItemToCart(int  productId)  {
		Product  product  =  productService.getProductById(productId);
		// Lógica para agregar un producto al carrito
	}
}
```
### 5. Patrón Singleton

El patrón Singleton garantiza que una clase tenga una única instancia y proporciona un punto de acceso global a esa instancia. Se utiliza cuando se necesita una única instancia compartida en toda la aplicación.

**Ejemplo:** Supongamos que estamos desarrollando una aplicación de registro de eventos. La clase EventLogger podría implementarse como un Singleton para garantizar que todas las partes de la aplicación utilicen la misma instancia de registro de eventos.

```
class  EventLogger  {
	private  static  EventLogger  instance  =  new  EventLogger(); 
	privateEventLogger()  {
		// Constructor privado para evitar la creación de instancias externas
	}
	public  static  EventLogger  getInstance()  {
    if  (instance == null)  {
        instance  =  new Singleton(value);
    }
		return  instance;
	}
	public  void  logEvent(String event)  {
		// Lógica para registrar el evento
	}
}
```

## Arquitectura de Servicios y Comunicación

La Arquitectura de Servicios es un enfoque de diseño de software que se basa en la descomposición de una aplicación en múltiples servicios independientes, cada uno de los cuales se encarga de una parte específica de la funcionalidad. Cada servicio opera de manera autónoma y se comunica con otros servicios a través de interfaces bien definidas. Esto permite la creación de sistemas altamente escalables y modulares.

Principios Clave de la Arquitectura de Servicios
Antes de entrar en detalles sobre la comunicación en la Arquitectura de Servicios, es importante comprender algunos de los principios clave que guían este enfoque:

La Arquitectura de Servicios es un enfoque de diseño de software basado en la descomposición de una aplicación en múltiples servicios independientes, cada uno de los cuales es responsable de una parte específica de la funcionalidad. Cada servicio funciona de forma autónoma y se comunica con otros servicios a través de interfaces bien definidas. Esto permite crear sistemas altamente escalables y modulares.

Principios clave de la arquitectura de servicios
Antes de entrar en detalles sobre la comunicación en la Arquitectura de Servicios, es importante comprender algunos de los principios clave que guían este enfoque:

1. Descomposición de la Aplicación

La descomposición de la aplicación en servicios más pequeños y manejables es uno de los pilares de la Arquitectura de Servicios. En lugar de tener una aplicación monolítica grande y compleja, se divide en servicios independientes, cada uno de los cuales se centra en una funcionalidad específica.

Ejemplo:
En una aplicación de comercio electrónico, podemos tener servicios separados para la gestión de productos, el carrito de compras, el procesamiento de pagos y la gestión de pedidos.

2. Independencia de Implementación y Tecnología

Cada servicio en la Arquitectura de Servicios es independiente en cuanto a su implementación y la tecnología que utiliza. Esto significa que un servicio puede estar escrito en un lenguaje de programación diferente y utilizar una base de datos diferente sin afectar a otros servicios.

Ejemplo:
El servicio de gestión de productos puede estar escrito en Java y utilizar una base de datos MySQL, mientras que el servicio de procesamiento de pagos puede estar escrito en Python y utilizar una base de datos PostgreSQL.

3. Comunicación a Través de Interfaces

Los servicios se comunican entre sí a través de interfaces bien definidas. Esto se logra mediante la exposición de API (Application programming interface) que permiten a los servicios solicitar datos o realizar acciones en otros servicios.

Ejemplo:
Si un servicio de gestión de pedidos necesita obtener detalles de un producto, puede hacer una solicitud a través de la API proporcionada por el servicio de gestión de productos.

4. Escalabilidad Independiente

Un beneficio importante de la Arquitectura de Servicios es la capacidad de escalar cada servicio de manera independiente según sea necesario. Los servicios que experimentan una alta carga pueden escalarse horizontalmente agregando más instancias, mientras que los servicios menos utilizados pueden mantenerse con menos recursos.

Ejemplo:
Durante un evento de ventas masivas, el servicio de carrito de compras puede experimentar una carga significativamente mayor, por lo que se puede escalar de manera independiente para manejar la demanda adicional.


### Comunicación en la Arquitectura de Servicios

#### Protocolos de Comunicación
Los protocolos de comunicación son un aspecto clave en la Arquitectura de Servicios, ya que determinan cómo los servicios se comunican entre sí. A continuación, se describen dos de los protocolos más comunes utilizados en este contexto:

1. REST (Representational State Transfer)

REST es un estilo de arquitectura que utiliza el protocolo HTTP para la comunicación. Se basa en la idea de que los recursos (como datos o funcionalidades) se representan mediante URLs, y las operaciones se realizan utilizando los métodos HTTP estándar, como GET (obtener), POST (crear), PUT (actualizar) y DELETE (eliminar).

Ejemplo:
Si un servicio de gestión de productos necesita recuperar información sobre un producto específico, puede realizar una solicitud GET a través de HTTP a una URL específica, como https://api.miapp.com/productos/123.

2. gRPC (gRPC Remote Procedure Call)

gRPC es un protocolo de comunicación de alto rendimiento desarrollado por Google. Se basa en el intercambio de mensajes utilizando el formato Protocol Buffers (protobufs) y permite la definición de servicios y métodos de forma clara. gRPC es especialmente adecuado para aplicaciones que requieren una comunicación rápida y eficiente.

Ejemplo:
Un servicio de autenticación puede ofrecer un método VerificarUsuario definido en un archivo .proto. Otro servicio puede invocar este método de forma remota, lo que permite la verificación de usuarios de manera eficiente.

#### Gestión de Errores y Retries
La comunicación entre servicios en la Arquitectura de Servicios puede ser propensa a errores debido a la naturaleza distribuida del sistema. Por lo tanto, es fundamental implementar estrategias de gestión de errores y reintentos.

Ejemplo:
Si un servicio de procesamiento de pagos intenta cargar una tarjeta de crédito y falla debido a una conexión de red intermitente, puede implementar una estrategia de reintento automático para volver a intentar la operación varias veces antes de reportar un error al servicio de gestión de pedidos.

Descubrimiento y Registro de Servicios
Para que los servicios puedan comunicarse entre sí, es necesario que conozcan la ubicación y el estado de los otros servicios en tiempo real. Esto se logra mediante el descubrimiento y registro de servicios.

Ejemplo:
Cuando un nuevo servicio se despliega en la infraestructura, debe registrarse en un servidor de registro de servicios para que otros servicios puedan descubrirlo y comunicarse con él. Herramientas como Consul y Eureka son ejemplos de sistemas de registro de servicios.










#### Patrones de Comunicación en la Arquitectura de Servicios

La Arquitectura de Servicios, luego transformada en Arquitectura de Microservicios, es un enfoque de diseño de software que se ha convertido en la base de muchas aplicaciones modernas debido a su capacidad para crear sistemas altamente escalables, modulares y flexibles. Uno de los aspectos más críticos de esta arquitectura es cómo los diferentes servicios se comunican entre sí de manera eficiente y efectiva. 

1. API Gateway

El patrón de API Gateway actúa como una puerta de enlace central que se encuentra entre los clientes y los servicios individuales. Su función principal es agregar y enrutar las solicitudes de los clientes a los servicios apropiados. Este patrón simplifica la comunicación para los clientes, ya que solo necesitan interactuar con el API Gateway en lugar de conocer las ubicaciones y detalles de todos los servicios individuales en el sistema.

**Ejemplo de código (Node.js utilizando Express):**

javascript
```
const express = require('express');
const app = express();

// API Gateway enruta las solicitudes al servicio de gestión de productos
app.get('/productos/:id', (req, res) => {
  // Lógica para enrutar la solicitud al servicio de gestión de productos
  res.send('Detalles del producto');
});

// API Gateway enruta las solicitudes al servicio de carrito de compras
app.post('/carrito/agregar', (req, res) => {
  // Lógica para enrutar la solicitud al servicio de carrito de compras
  res.send('Producto agregado al carrito');
});

// API Gateway enruta las solicitudes al servicio de procesamiento de pedidos
app.post('/pedidos/crear', (req, res) => {
  // Lógica para enrutar la solicitud al servicio de procesamiento de pedidos
  res.send('Pedido creado con éxito');
});

app.listen(3000, () => {
  console.log('API Gateway en funcionamiento en el puerto 3000');
});
```

2. Cola de Mensajes

El patrón de Cola de Mensajes es fundamental cuando se trata de lograr una comunicación asincrónica y fiable entre servicios. En este patrón, los servicios envían mensajes a una cola de mensajes, y otros servicios los consumen de la cola según su disponibilidad. Esto permite una mayor flexibilidad y tolerancia a fallos en la comunicación entre servicios.

**Ejemplo de código (Java utilizando RabbitMQ):**


Java
```
import com.rabbitmq.client.*;

public class ColaDeMensajes {

  private final static String COLA_NOMBRE = "mi_cola";

  public static void main(String[] argv) throws Exception {
    ConnectionFactory factory = new ConnectionFactory();
    factory.setHost("localhost");
    try (Connection connection = factory.newConnection(); 
         Channel channel = connection.createChannel()) {
      channel.queueDeclare(COLA_NOMBRE, false, false, false, null);

      // Envío de un mensaje
      String mensaje = "Hola, mundo!";
      channel.basicPublish("", COLA_NOMBRE, null, mensaje.getBytes("UTF-8"));
      System.out.println(" [x] Enviado '" + mensaje + "'");

      // Consumo de un mensaje
      DeliverCallback deliverCallback = (consumerTag, delivery) -> {
        String mensajeRecibido = new String(delivery.getBody(), "UTF-8");
        System.out.println(" [x] Recibido '" + mensajeRecibido + "'");
      };
      channel.basicConsume(COLA_NOMBRE, true, deliverCallback, consumerTag -> { });
    }
  }
}
```


3. Balanceo de Carga


El patrón de Balanceo de Carga es fundamental en la Arquitectura de Servicios para garantizar la escalabilidad y la disponibilidad de los servicios. Su objetivo principal es distribuir las solicitudes de los clientes de manera equitativa entre múltiples instancias de un servicio, evitando la sobrecarga de un solo servidor. Esto mejora el rendimiento y la capacidad de respuesta del sistema, permitiendo que el tráfico se maneje de manera eficiente.

### ¿Por qué es necesario el Balanceo de Carga?

En sistemas de alta demanda, es común que múltiples usuarios o clientes realicen solicitudes simultáneas a un servicio o aplicación. Si todas estas solicitudes se dirigen a una única instancia del servicio, esa instancia puede sobrecargarse, lo que resultaría en una disminución del rendimiento o incluso en la caída del servicio. El Balanceo de Carga aborda este problema distribuyendo las solicitudes de manera uniforme entre varias instancias del servicio, evitando la congestión y mejorando la disponibilidad.


java

```
import java.io.IOException;
import java.io.OutputStream;
import com.sun.net.httpserver.HttpExchange;
import com.sun.net.httpserver.HttpHandler;
import com.sun.net.httpserver.HttpServer;

public class ServidorBalanceoCarga {

  public static void main(String[] args) throws Exception {
    // Crear un servidor HTTP en el puerto 8080
    HttpServer server = HttpServer.create(new InetSocketAddress(8080), 0);

    // Crear un contexto para manejar solicitudes en el endpoint /mi-servicio
    server.createContext("/mi-servicio", new MiServicioHandler());

    // Iniciar el servidor
    server.start();
  }

  // Manejador para el servicio
  static class MiServicioHandler implements HttpHandler {
    @Override
    public void handle(HttpExchange exchange) throws IOException {
      // Simular la lógica del servicio
      String respuesta = "Respuesta desde instancia de servicio";

      // Enviar la respuesta al cliente
      exchange.sendResponseHeaders(200, respuesta.length());
      OutputStream os = exchange.getResponseBody();
      os.write(respuesta.getBytes());
      os.close();
    }
  }
}
```
Este ejemplo crea un servidor HTTP que escucha en el puerto 8080 y maneja solicitudes en el contexto "/mi-servicio". Si tuviéramos múltiples instancias de este servidor en diferentes servidores físicos o máquinas virtuales, podríamos usar un balanceador de carga, como Nginx, para distribuir las solicitudes entre estas instancias.

### Ejemplo de Configuración de Nginx como Balanceador de Carga

Supongamos que tenemos tres instancias del servidor Java mencionado anteriormente ejecutándose en servidores separados con las direcciones IP y puertos correspondientes (servidor1:8080, servidor2:8080, servidor3:8080). A continuación, se muestra cómo se podría configurar Nginx como balanceador de carga para distribuir el tráfico entre estas instancias:

nginx
```
http {
  upstream mi_servicio {
    server servidor1:8080;
    server servidor2:8080;
    server servidor3:8080;
  }

  server {
    listen 80;
    server_name miapp.com;

    location / {
      proxy_pass http://mi_servicio;
    }
  }
}
```
En este ejemplo de configuración de Nginx, se define un grupo `upstream` llamado "mi_servicio" que incluye las direcciones de las tres instancias del servicio. Luego, se configura Nginx para escuchar en el puerto 80 y redirigir todas las solicitudes entrantes al grupo "mi_servicio". De esta manera, Nginx distribuirá las solicitudes entre las instancias de manera equitativa, lo que proporciona un equilibrio de carga efectivo.

https://nginx.org/en/docs/http/load_balancing.html

#### Proxy Inverso
El patrón de Proxy Inverso es una pieza esencial en la arquitectura de servicios que actúa como intermediario entre los clientes y los servicios internos. Su función principal es gestionar la seguridad, el enrutamiento y la autenticación de las solicitudes de los clientes antes de que lleguen a los servicios subyacentes. Este patrón proporciona una capa adicional de control y seguridad en la comunicación, lo que lo hace especialmente útil en entornos donde se requiere un acceso controlado y una gestión de las solicitudes.

**¿Por qué es necesario el Proxy Inverso?**

En una arquitectura de servicios, los clientes a menudo no interactúan directamente con los servicios internos. En su lugar, todas las solicitudes pasan a través de un proxy inverso que se encarga de dirigirlas al servicio correcto, realizar autenticación, autorización y otras funciones de seguridad, así como aplicar reglas de enrutamiento. Esto permite proteger los servicios internos de acceso no autorizado y simplificar la administración de la infraestructura.

 Servicio Interno:

java

```
import java.io.IOException;
import java.io.OutputStream;
import com.sun.net.httpserver.HttpExchange;
import com.sun.net.httpserver.HttpHandler;
import com.sun.net.httpserver.HttpServer;

public class ServicioInterno {

  public static void main(String[] args) throws Exception {
    HttpServer server = HttpServer.create(new InetSocketAddress(8080), 0);
    server.createContext("/", new MiServicioHandler());
    server.start();
  }

  static class MiServicioHandler implements HttpHandler {
    @Override
    public void handle(HttpExchange exchange) throws IOException {
      String respuesta = "Respuesta desde el servicio interno";
      exchange.sendResponseHeaders(200, respuesta.length());
      OutputStream os = exchange.getResponseBody();
      os.write(respuesta.getBytes());
      os.close();
    }
  }
}
```
En este ejemplo, hemos creado un servicio interno muy simple que escucha en el puerto 8080 y responde con un mensaje.

### Configuración de Nginx como Proxy Inverso:

A continuación, se muestra una configuración de ejemplo para Nginx como proxy inverso. En esta configuración, Nginx se encarga de enrutar las solicitudes hacia el servicio interno y un servicio administrativo protegido.

nginx

```
server {
  listen 80;
  server_name miapp.com;

  # Enrutamiento a servicio interno
  location / {
    proxy_pass http://localhost:8080; # Dirección del servicio interno
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
  }

  # Enrutamiento a servicio administrativo con autenticación
  location /admin {
    auth_basic "Acceso restringido";
    auth_basic_user_file /etc/nginx/.htpasswd; # Configuración de autenticación
    proxy_pass http://servicio_admin; # Dirección del servicio administrativo
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
  }
}
```
En esta configuración de Nginx, las solicitudes a la raíz ("/") se enrutan hacia el servicio interno en el puerto 8080, mientras que las solicitudes a "/admin" se enrutan hacia un servicio administrativo protegido. Nginx también se encarga de establecer las cabeceras necesarias para mantener la información de la solicitud original.
5. Circuit Breaker (Interruptor de Circuito)

El patrón de Circuit Breaker se utiliza para gestionar la tolerancia a fallos en la comunicación entre servicios. Funciona de manera similar a un interruptor eléctrico, donde se abre el circuito cuando se detectan fallos y se cierra cuando la comunicación se restablece. Esto evita la propagación de errores y mejora la resiliencia del sistema.

**Ejemplo de código (Java utilizando Hystrix):**

java

```
import com.netflix.hystrix.HystrixCommand;
import com.netflix.hystrix.HystrixCommandGroupKey;

public class ServicioResiliente extends HystrixCommand<String> {
  public ServicioResiliente() {
    super(HystrixCommandGroupKey.Factory.asKey("EjemploGrupo"));
  }

  @Override
  protected String run() throws Exception {
    // Lógica del servicio
    // ...
    return "Respuesta del servicio";
  }

  @Override
  protected String getFallback() {
    return "Respuesta de respaldo en caso de fallo";
  }
}
```
https://netflix.github.io/Hystrix/javadoc/overview-summary.html
### Patrón de Event Sourcing (Registro de Eventos) en la Arquitectura de Servicios

El patrón de Event Sourcing, también conocido como Registro de Eventos, es una técnica utilizada en la Arquitectura de Servicios para capturar y almacenar todos los cambios en el estado de una aplicación como una secuencia de eventos. A través de este registro de eventos, es posible reconstruir el estado actual de la aplicación en cualquier momento. Este patrón es especialmente útil en sistemas con múltiples servicios que deben mantener la coherencia de datos y permitir una trazabilidad completa de las acciones realizadas en la aplicación.

#### ¿Por qué es necesario el Event Sourcing?

En las aplicaciones tradicionales, se suele mantener el estado actual de una entidad o objeto, y cada cambio en ese estado sobrescribe el estado anterior. Sin embargo, esto puede limitar la capacidad de analizar y comprender el historial de cambios en el estado de la aplicación. El Event Sourcing aborda este problema registrando todos los eventos que afectan al estado de la aplicación, lo que permite mantener un historial completo y proporciona la capacidad de reconstruir el estado en cualquier punto en el tiempo.

#### Ejemplo de Código en Java

A continuación, se presenta un ejemplo de cómo implementar el patrón de Event Sourcing en java utilizando una clase `Producto` como ejemplo. En este ejemplo, la clase `Producto` registra eventos cada vez que se cambia el precio del producto y luego puede reconstruir su estado actual a partir de estos eventos.

java

```
import java.util.ArrayList;
import java.util.List;
import java.util.UUID;

public class Producto {
  private UUID Id;
  private String Nombre;
  private double Precio;

  // Registro de eventos
  private final List<Object> eventos = new ArrayList<>();

  public Producto(List<Object> eventos) {
    for (Object evento : eventos) {
      aplicarEvento(evento);
    }
  }

  public void cambiarPrecio(double nuevoPrecio) {
    PrecioCambiado evento = new PrecioCambiado(Id, nuevoPrecio);
    aplicarEvento(evento);
    eventos.add(evento);
  }

  private void aplicarEvento(Object evento) {
    // Lógica para aplicar el evento y actualizar el estado del producto
    if (evento instanceof PrecioCambiado) {
      PrecioCambiado precioCambiado = (PrecioCambiado) evento;
      Precio = precioCambiado.getNuevoPrecio();
    }
    // Otras lógicas para manejar diferentes tipos de eventos
  }

  // Clase interna para el evento PrecioCambiado
  public static class PrecioCambiado {
    private final UUID ProductoId;
    private final double NuevoPrecio;

    public PrecioCambiado(UUID productoId, double nuevoPrecio) {
      ProductoId = productoId;
      NuevoPrecio = nuevoPrecio;
    }

    public UUID getProductoId() {
      return ProductoId;
    }

    public double getNuevoPrecio() {
      return NuevoPrecio;
    }
  }
}
```
En este ejemplo, la clase `Producto` tiene un registro de eventos que almacena todos los eventos relacionados con cambios en el precio del producto. Cuando se produce un cambio en el precio, se registra un evento `PrecioCambiado` y se aplica a través del método `AplicarEvento`. Este método se encarga de actualizar el estado del producto en función del evento registrado.

### Ventajas del Event Sourcing

El Event Sourcing ofrece varias ventajas en la Arquitectura de Servicios:

1.  **Trazabilidad completa:** Se puede rastrear y auditar fácilmente todos los cambios en el estado de la aplicación.
    
2.  **Reconstrucción del estado:** Permite reconstruir el estado de la aplicación en cualquier momento, lo que facilita la solución de problemas y la recuperación de datos.
    
3.  **Mantenimiento de coherencia:** En sistemas distribuidos, el Event Sourcing ayuda a mantener la coherencia de datos entre diferentes servicios.
    
4.  **Historial de cambios:** Facilita el análisis histórico de datos y permite la generación de informes.
    
5.  **Detección de problemas:** Ayuda en la detección de problemas y la identificación de eventos que llevaron a estados no deseados.

https://microservices.io/patterns/data/event-sourcing.html

## Gestión de Bases de Datos en la Arquitectura y Seguridad
  La elección y el diseño de bases de datos son críticos para la seguridad de una aplicación.
  Cómo se diseñan bases de datos seguras y cómo se protegen contra amenazas.
## Arquitectura en la Nube y Arquitectura Serverless
  Cómo las arquitecturas modernas aprovechan la infraestructura en la nube.
  Cómo las arquitecturas en la nube pueden incluir elementos sin servidor y cómo se adaptan a la escalabilidad y la flexibilidad.
## Escalabilidad y Rendimiento y Arquitectura de Alta Disponibilidad
  La escalabilidad y la alta disponibilidad son objetivos comunes en la arquitectura de sistemas.
  Cómo se logra la escalabilidad sin comprometer la disponibilidad.
## Ambientes, Contenedores y Orquestación
  Gestión de ambientes e implementación de aplicaciones en contenedores.
  Cómo se gestionan ambientes de desarrollo, pruebas y producción mediante el uso de contenedores y tecnologías de orquestación como Kubernetes.
