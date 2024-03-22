
# README - Aplicación de Juego de Rol con Spring

## Descripción

Esta aplicación simula un combate entre un personaje, específicamente un guerrero, y un monstruo en un juego de rol. Utiliza Spring Framework para gestionar los componentes del juego, la inyección de dependencias, y la configuración del entorno del juego.

## Componentes

- **Personaje (Interface)**: Define la estructura básica de los personajes en el juego, permitiendo obtener su nombre y ejecutar una acción de ataque.
- **Habilidad (Interface)**: Define las habilidades que pueden tener los personajes del juego.
- **AtaqueCuerpoACuerpo**: Implementa la interface Habilidad, representando una habilidad de ataque físico.
- **Guerrero**: Representa un personaje del juego, implementa la interface Personaje y es capaz de atacar utilizando una habilidad.
- **Combate**: Gestiona el encuentro entre el guerrero y el monstruo, iniciando el combate.
- **Configuración del Juego (ConfiguracionJuego)**: Configura los beans necesarios para el juego, incluyendo la habilidad de ataque cuerpo a cuerpo.
- **MainJuego**: Clase principal que ejecuta la aplicación, creando el contexto de Spring y iniciando el combate.

## Anotaciones de Spring Utilizadas

- **@Component**: Utilizada para definir que una clase será un bean gestionado por Spring, como se ve en `AtaqueCuerpoACuerpo`, `Combate` y `Guerrero`.
- **@Autowired**: Permite la inyección automática de dependencias en los componentes, como se observa en la clase `Combate` para inyectar un `Personaje` y en `Guerrero` para inyectar una `Habilidad` y un valor para el nombre.
- **@Qualifier**: Especifica cuál de las implementaciones de una interface se debe inyectar, utilizado en `Guerrero` para seleccionar la habilidad de ataque cuerpo a cuerpo.
- **@Value**: Inyecta valores de propiedades en los componentes, usado en `Guerrero` para asignar el nombre del personaje desde `application.properties`.
- **@Configuration**: Indica que una clase declara uno o más métodos `@Bean` y puede ser procesada por el contenedor de Spring para generar definiciones de bean y solicitudes de servicio para esos beans en tiempo de ejecución.
- **@ComponentScan**: Habilita el escaneo de componentes en un paquete especificado, permitiendo que Spring descubra y registre beans automáticamente.
- **@PropertySource**: Se utiliza para declarar un conjunto de propiedades definidas en un archivo que estará disponible en el entorno de Spring.
- **@Bean**: Define un bean en el contexto de Spring, usado en `ConfiguracionJuego` para crear el bean de la habilidad de ataque cuerpo a cuerpo.
- **@PostConstruct y @PreDestroy**: Anotaciones utilizadas para definir métodos de callback que se ejecutan después de la creación del bean y justo antes de la destrucción del bean, respectivamente. Utilizadas en `Guerrero` para gestionar el ciclo de vida del personaje en la mazmorra.

## Ejecución de la Aplicación

Para ejecutar esta aplicación, asegúrate de tener instalado un entorno de ejecución compatible con Java y Spring Framework. Luego, ejecuta la clase `MainJuego`, que iniciará el contexto de Spring, creará los beans necesarios, e iniciará el combate entre el guerrero y el monstruo. Al finalizar, el contexto de Spring se cerrará correctamente.
