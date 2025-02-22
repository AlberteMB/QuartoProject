
# Apuntes
## Hooks (10)
- **Rules:**
    * Only call hooks at the `top level`.
    * Only call hooks from React Functions.
    
### useState
- Permite añadir una variable de estado a tu componente. Lo usamos cuaando un componente necesita almacenar y actualizar valores (inputs, contadores, etc).
```j̀sx
const [state, setState] = useState(valorInicial);
```

### useEffect
- Ejecuta código después del render (fetch de datos, suscripciones, manipulación del DOM, etc). Lo usamos cuando necesitamos ejecutar código en eventos como el montaje, actualización o desmontaje del componente.
	- **Notas:**
		- Si [] está vacío, el efecto se ejecuta solo en el montaje.
		- Si tiene dependencias, se ejecuta cuando cambian.
		- Si retorna una función, esta se ejecuta en el desmontaje (cleanup)
```jsx
useEffect(() => {
  // Código a ejecutar
  return () => {
    // Cleanup (opcional)
  };
}, [dependencias]);
```

### useRef
- Permite crear referencias a elementos del DOM o almacenar valores que **NO** provocan render al cambiar. Lo usamos cuando necesitamos acceder a un elemento del DOM o almacenar un valor sin causar un re-render.
```jsx
const ref = useRef(valorInicial);
```

### useContext
- Permite acceder a un contexto global sin pasar props manualmente entre componentes. Lo usamos cuando varios componentes necesitan aceder a un mismo valor.
```jsx
const valor = useContext(MiContexto);
```

### useReducer
- Maneja estados complejos usando un reducer. Lo usamos cuando el estado tiene múltiples valores o una lógica de actualización compleja.
```jsx
const [state, dispatch] = useReducer(reducer, estadoInicial);
```

## React Router Dom y Render Virtual DOM (5)
### Qué es el DOM? `Document Object Model`
- Representación estructurada de una página web en forma de árbol. Forma en la que los navegadores interpretan y manipulan un documento `HTML`.

### Cómo funciona el DOM?
-  El navegador carga el HTML --> Crea el DOM --> Permite modificar la página dinámicamente.

### React Router DOM:
- Librería externa que permite manejar la navegación en Apps React.
- Controla cómo los componentes cambian según la URL sin recargar la página.
- Usa Client-Side Routing.

### Render Virtual DOM:
- **Virtual DOM:** Reprensentación en memoria del DOM real.Estructura de datos en forma de árbol que React usa para optimizar la manipulación del DOM real de la página.
- **Proceso de renderizado:** Cuando una App se monta por primera vez, se crea el Virtual DOM con la estructura inicial de la UI. React renderiza los componentes y genera la estructura en memoria antes de manipular el DOM real.  

## MUI y CSS (5)
### MUI 
- Es una librería de componentes de interface de usuario para react. Basada en las guías de diseño de `Material Design de Google`.
- Debemos instalarlo al iniciar un proyecto usando `npm`.
- Por qué usarlo?
    * **Componmentes:** Botones, formularios, tablas, modales, etc.
    * **Diseño moderno**
    * **Fácil de personalizar**
    * **Optimización para accesibilidad y rendimiento**
    * **Compatible con CSS-in-JS y Styled Components**
    
### CSS (Cascading Style Sheets)
- Lenguaje de hojas de estilo utilizado para dar formato y diseño a la web.
- Sirve para cambiar colores, fuentes, tamaños, posiciones, espacios, animaciones...

## Cycle Render (5)
Consiste en 3 fases: `Fase de trigger, Fase de Render, Fase de Commit`

- **Fase de Trigger:** Algo provoca un re-render (Cambio de estado, props, reloj, evento). No ejecuta código de usuario.
- **Fase de Render:** Ejecuta la función del componente y actualiza el `Virtual DOM`. Se ejecuta la función del componente.
- **Fase de Commit:** Se actualiza el DOM real y ejecuta efectos secundarios (`useEffect`). También se actualizan las referencias con `useRef`.

## Library, axios, leaflet, handler, form. (5)
### Handlers (Manejo de eventos)
- Funciones que se ejecutan cuando ocurre un evento (clicks, teclado, formularios, etc.)
    * **onClick**: Ejecuta cuando se hace click.
    * **onKeyPress**: Se ejecuta cuando se presiona una tecla.
    * **onChange**: Captura cambios en los elementos de entrada.
    
### Axios 
- Librería para hacer peticiones HTTP. Usada para comunicarse con APIs. 
    * Maneja respuestas JSON automáticamente.
    * Soporta cancelaciones de peticiones.
    * Permite configurar cabeceras globales.
    * Soporta interceptores para modificar peticiones y respuestas.
    
### Leaflet
- Librería para mapas interactivos. Usado para mostrar mapas personalizados.

### Formularios
- Los formularios manejan su estado internamente con `useState` o de forma controlada con `useRef`.

### ESLint Plugin
- Herramienta de análisis estático `para encontrar y corregir errores` en el código JS y React.

## Desarrollo: ejemplo Ciclo de Render (1)
