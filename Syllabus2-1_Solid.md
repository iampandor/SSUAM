
# Principios SOLID y Patrones de Diseño Arquitectónico

Los Principios SOLID son un conjunto de cinco directrices que ayudan a los desarrolladores a crear software que sea fácil de mantener y extender. Estos principios fueron introducidos por el ingeniero de software Robert C. Martin (Uncle Bob) y se han convertido en una base sólida para la programación orientada a objetos (POO) y el diseño de software en general. Los cinco principios SOLID son:

## 1. Principio de Responsabilidad Única (SRP - Single Responsibility Principle)

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

## 2. Principio de Abierto/Cerrado (OCP - Open/Closed Principle)

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

## 3. Principio de Sustitución de Liskov (LSP - Liskov Substitution Principle)

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

## 4. Principio de Segregación de Interfaces (ISP - Interface Segregation Principle)

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

## 5. Principio de Inversión de Dependencias (DIP - Dependency Inversion Principle)

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
# Patrones de Diseño Arquitectónico

Además de los Principios SOLID, los Patrones de Diseño Arquitectónico son herramientas para diseñar sistemas de software robustos y escalables. Los patrones de diseño son soluciones probadas para problemas comunes de diseño de software.

## 1. Patrón Modelo-Vista-Controlador (MVC)

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
## 2. Patrón Modelo-Vista-ViewModel (MVVM)

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

## 3. Patrón Repositorio

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

## 4. Patrón Inyección de Dependencias (DI - Dependency Injection)

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
## 5. Patrón Singleton

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
