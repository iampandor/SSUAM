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
## Arquitectura de Servicios y Comunicación
  La Arquitectura de Servicios, como los microservicios, implica la comunicación entre componentes distribuidos.
  Cómo se establecen y gestionan estas comunicaciones utilizando protocolos como REST o gRPC.
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
