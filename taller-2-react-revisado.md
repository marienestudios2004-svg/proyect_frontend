# Taller 2 Corte: Investigación sobre React

**Modalidad:** Individual  
**Fecha de entrega:** viernes 16 de octubre de 2026

## Punto 1. ¿Qué es React?

Para mí, React es una biblioteca de JavaScript que sirve para crear la parte visual de una página web, es decir, aquello con lo que una persona interactúa, como botones, formularios, menús o tarjetas de productos. Una de sus ventajas es que permite dividir la interfaz en partes pequeñas llamadas componentes y organizarlas mejor.

React fue creado en Facebook, empresa que hoy se conoce como Meta, y se publicó como código abierto en 2013. Se considera una **biblioteca o librería**, no un framework completo, porque se enfoca principalmente en construir interfaces. Una biblioteca ofrece herramientas para una tarea concreta; en cambio, un framework suele ofrecer una estructura más amplia para organizar una aplicación. Con React se pueden elegir otras herramientas para completar el proyecto.

React es declarativo porque describimos cómo queremos que se vea la interfaz con los datos actuales, y React se encarga de actualizarla cuando esos datos cambian. Así no tenemos que escribir instrucciones manuales para modificar cada elemento de la página.

## Punto 2. ¿Qué problema resuelve React?

Cuando se construye una interfaz con JavaScript y se manipula directamente el DOM, hay que buscar los elementos y cambiar su contenido cada vez que ocurre algo. En una página pequeña esto puede ser sencillo, pero en una aplicación con muchos botones, formularios y datos cambiantes es fácil olvidar actualizar alguna parte. Como resultado, la pantalla puede mostrar información que ya no coincide con los datos.

El enfoque **imperativo** indica paso a paso qué debe hacer el programa, por ejemplo, buscar un párrafo y cambiar su texto. El enfoque **declarativo** describe cómo debe verse la interfaz según los datos actuales. React se encarga de aplicar los cambios necesarios.

Esto ayuda a mantener la interfaz sincronizada con el estado. Si un contador pasa de 2 a 3, React vuelve a renderizar el componente para mostrar el nuevo valor. Los componentes reutilizables también ayudan: una tienda puede crear una sola tarjeta de producto y utilizarla con nombres y precios diferentes. Así se evita repetir código y se mantiene un diseño uniforme.

## Punto 3. Principales elementos de React

### 3.1. Componentes

Un componente es una parte de la interfaz que podemos crear y reutilizar, como un encabezado, un botón o una tarjeta de producto. Normalmente se define como una función de JavaScript cuyo nombre empieza con mayúscula y que devuelve JSX.

**Características principales:**
- Organizan el código en partes más pequeñas.
- Se pueden combinar para construir una página completa.
- Pueden recibir datos por medio de props.
- Pueden manejar estado cuando necesitan recordar información que cambia.

**Ejemplo:**

```jsx
function Saludo() {
  return <h1>¡Hola! Bienvenida a mi página.</h1>;
}
```

`Saludo` es un componente funcional. Al usarlo como `<Saludo />`, se muestra el encabezado. Podemos reutilizarlo en distintas partes de la aplicación.

### 3.2. JSX

JSX es una sintaxis parecida a HTML que se escribe dentro de JavaScript para describir cómo se verá un componente. No es HTML puro, ya que las herramientas del proyecto lo transforman para que pueda ejecutarse.

**Reglas básicas:**
- Los componentes propios empiezan con mayúscula.
- Las etiquetas deben cerrarse correctamente.
- Si se devuelven varios elementos, se agrupan en un elemento padre o en un fragmento.
- Las expresiones de JavaScript van entre llaves `{}`.
- Para asignar una clase CSS se utiliza `className`.

**Ejemplo:**

```jsx
function Bienvenida() {
  const nombre = "Dani";

  return (
    <section>
      <h1>Hola, {nombre}</h1>
      <p>Estoy aprendiendo React.</p>
    </section>
  );
}
```

La variable `nombre` se inserta en el título mediante las llaves. `section` agrupa el título y el párrafo para que el componente devuelva un elemento principal.

### 3.3. Props

Las props son datos que un componente recibe desde el lugar donde se utiliza. Las entiendo como una forma de darle información diferente al mismo componente sin tener que escribirlo de nuevo.

**Características principales:**
- Pasan datos de un componente padre a uno hijo.
- Pueden ser textos, números y otros valores.
- Permiten reutilizar componentes con información diferente.
- Normalmente, el componente que las recibe no debe modificarlas.

**Ejemplo:**

```jsx
function TarjetaProducto({ nombre, precio }) {
  return (
    <article>
      <h2>{nombre}</h2>
      <p>Precio: ${precio}</p>
    </article>
  );
}

function Tienda() {
  return <TarjetaProducto nombre="Alimento para gatos" precio={45000} />;
}
```

`Tienda` entrega el nombre y el precio. La tarjeta muestra esos valores. Si enviamos otros datos, se conserva el diseño y cambia el contenido.

### 3.4. Estado: `useState`

El estado es la información que un componente necesita recordar mientras se usa la aplicación, como el número de clics o el texto escrito en un formulario. El Hook `useState` permite crear ese valor y una función para actualizarlo.

**Características principales:**
- Se importa desde React.
- Devuelve el valor actual y una función actualizadora.
- Cuando cambia el estado, React vuelve a renderizar el componente.
- No se debe modificar directamente la variable; se usa la función actualizadora.

**Ejemplo:**

```jsx
import { useState } from "react";

function Contador() {
  const [cantidad, setCantidad] = useState(0);

  return (
    <div>
      <p>Has hecho clic {cantidad} veces.</p>
      <button onClick={() => setCantidad(cantidad + 1)}>
        Aumentar
      </button>
    </div>
  );
}
```

`cantidad` empieza en cero. Al pulsar el botón, `setCantidad` aumenta el valor y React actualiza el texto en pantalla.

### 3.5. Eventos: `onClick` y `onChange`

Los eventos permiten que la página responda a las acciones del usuario. `onClick` se utiliza cuando se pulsa un botón y `onChange` cuando cambia el valor de un campo, como un cuadro de texto.

**Características principales:**
- Conectan las acciones del usuario con el comportamiento de la aplicación.
- Reciben una función que se ejecuta cuando ocurre el evento.
- Pueden actualizar el estado para que la interfaz refleje la interacción.

**Ejemplo:**

```jsx
import { useState } from "react";

function FormularioNombre() {
  const [nombre, setNombre] = useState("");

  return (
    <label>
      Escribe tu nombre:
      <input
        value={nombre}
        onChange={(evento) => setNombre(evento.target.value)}
      />
      <p>Hola, {nombre || "visitante"}.</p>
      <button onClick={() => setNombre("")}>Borrar</button>
    </label>
  );
}
```

`onChange` guarda lo que la persona escribe y el saludo cambia. `onClick` limpia el campo al pulsar el botón. Así se ve cómo los eventos y el estado trabajan juntos.

## Punto 4. Importancia de React en la industria

Considero que muchas empresas usan React porque ayuda a organizar interfaces grandes sin repetir tanto código. Los componentes permiten que un equipo trabaje de forma ordenada y mantenga una apariencia consistente. React también actualiza la interfaz cuando cambian los datos, algo importante en aplicaciones interactivas.

Su ecosistema incluye herramientas que complementan su función. **React Developer Tools** permite inspeccionar componentes; **Vite** facilita iniciar y construir proyectos; y **Next.js** es un framework basado en React que agrega herramientas y convenciones para crear aplicaciones web más completas.

React es de código abierto y cuenta con documentación pública y colaboradores de distintas empresas y países. Meta lo creó y lideró históricamente su desarrollo. En febrero de 2026, la documentación oficial anunció que la React Foundation se lanzó oficialmente y que React, React Native y proyectos relacionados pasaron a esa fundación independiente, alojada por la Linux Foundation. Esto muestra que el mantenimiento ya no depende exclusivamente de una sola empresa.

Para una persona que estudia desarrollo front-end, aprender React es útil porque permite practicar componentes, props, estado y eventos, conceptos presentes en muchas interfaces actuales. Sin embargo, no reemplaza las bases de HTML, CSS y JavaScript; entenderlas es necesario para saber qué hace el código y resolver problemas sin depender de ejemplos copiados.

## Punto 5. Grandes empresas que utilizan React

### 5.1. Discord

Discord explicó en su blog de ingeniería que su cliente de escritorio utiliza React y sus clientes móviles utilizan React Native. Es un caso relevante porque la plataforma muestra servidores, canales y mensajes que cambian continuamente. Usar React en escritorio y React Native en móviles ayuda a sus equipos a desarrollar funciones en distintas plataformas, aunque la empresa también debe trabajar cuidadosamente en el rendimiento.

**Fuente:** [Discord Engineering, “Supercharging Discord Mobile: Our Journey to a Faster App” (2025)](https://discord.com/blog/supercharging-discord-mobile-our-journey-to-a-faster-app)

### 5.2. Meta: Facebook e Instagram

Meta creó React para responder a necesidades de interfaces de sus productos y luego lo publicó como código abierto. La empresa continúa utilizándolo en sus productos y contribuyendo a su desarrollo junto con otras organizaciones y personas de la comunidad. Facebook e Instagram son ejemplos relevantes porque tienen interfaces grandes e interactivas y contenido que se actualiza constantemente.

**Fuentes:**
- [Meta Engineering: Introducing the React Foundation (2025)](https://engineering.fb.com/2025/10/07/open-source/introducing-the-react-foundation-the-new-home-for-react-react-native/)
- [React: Conoce al equipo](https://es.react.dev/community/team)

## Conclusión

Después de revisar estos conceptos, entiendo que React permite construir interfaces más organizadas al dividirlas en componentes y conectarlas con los datos. Las props pasan información, `useState` permite guardar datos que cambian y los eventos hacen que la aplicación responda a las acciones del usuario. Su ecosistema y su uso en productos reales hacen que sea una herramienta útil para aprender desarrollo front-end. Lo importante es comprender cómo se relacionan los elementos y poder explicar el código.

## Referencias

1. React. *Aprende React*. https://es.react.dev/learn
2. React. *Describir la interfaz de usuario*. https://react.dev/learn/describing-the-ui
3. React. *Añadir interactividad*. https://react.dev/learn/adding-interactivity
4. React. *La Fundación React*. https://react.dev/blog/2026/02/24/the-react-foundation
5. Discord Engineering. *Supercharging Discord Mobile: Our Journey to a Faster App* (2025). https://discord.com/blog/supercharging-discord-mobile-our-journey-to-a-faster-app
6. Meta Engineering. *Introducing the React Foundation* (2025). https://engineering.fb.com/2025/10/07/open-source/introducing-the-react-foundation-the-new-home-for-react-react-native/
