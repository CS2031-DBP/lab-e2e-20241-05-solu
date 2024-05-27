# 📋 Proyecto E2E - Entrega 5: Frontend web con React

## Descripción 💡

Este laboratorio se centra en desarrollar la página web para el Backend del clon de Uber. Constará de una página de Login/Register para cada rol de usuario, así como un dashboard para visualizar el historial de viajes de cada usuario.

En esta entrega deberás:

- Desarrollar la página web con el paradigma basado en componentes con ayuda del framework de frontend [**React**](https://react.dev)
- Implementar el consumo de la API del E2E con ayuda de la librería [**Axios**](https://axios-http.com/es/)
- Clonar el diseño de la web del E2E con ayuda del framework de CSS [**Tailwind**](https://tailwindcss.com/)

## Requerimientos ✅

Tener instalado:
+ Runtime de Javascript [**Node.js**](https://nodejs.org/en) (v20 o superior)
+ Gestor de paquetes de Node [**npm**](https://www.npmjs.com/package/npm) (v9 o superior)

Investigar sobre:
+ La herramienta de desarrollo [**Vite**](https://vitejs.dev)
+ Framework de CSS [**Tailwind**](https://tailwindcss.com/)
+ Funcionamiento de [**React Hooks**](https://es.reactjs.org/docs/hooks-intro.html)

## Evaluación 📋

La evaluación se divide en dos partes:

<table>
  <tr>
    <th>Evaluación</th>
    <th>Detalles</th>
  </tr>
  <tr>
    <th>Diseño (5 pts)</th>
    <td>
      <ul>
        <li><strong>Estilos</strong>: Deberás clonar o asemejar el diseño de la web del E2E con ayuda de Tailwind. Tomar como referencia el <a href="#prototipo-en-figma">Prototipo del E2E</a>.</li>
        <li><strong>Usabilidad</strong>: Implementar un diseño intuitivo y fácil de usar para el usuario.</li>
        <li><strong>Responsividad</strong>: (OPCIONAL) Implementar un diseño responsivo para la página web.</li>
      </ul>
    </td>
  </tr>
  <tr>
    <th>Funcionalidad (15 pts)</th>
    <td>
      <ul>
        <li><strong>Consumo de API</strong>: Deberás consumir la API del E2E para obtener los datos necesarios con ayuda de <code>Axios</code>.</li>
        <li><strong>Formularios</strong>: Deberás implementar la funcionalidad de obtener los datos de los formularios con <code>React Hooks</code> y enviarlos al backend.</li>
        <li><strong>Redirecciones</strong>: Deberás implementar las redirecciones de las rutas según el rol del <code>Usuario</code> y su estado de autenticación.</li>
        <li><strong>Login/Register</strong>: Deberás implementar la funcionalidad de <code>Login</code> y <code>Register</code> para cada rol de usuario.</li>
        <li><strong>Dashboard</strong>: Deberás implementar la funcionalidad de visualizar el historial de <code>Rides</code> de cada usuario, visualizar el perfil de cada usuario, ya sea <code>Passenger</code> o <code>Driver</code> y en el caso sea conductor, visualizar la información de su <code>Vehicle</code>.</li>
        <li><strong>Actualizar datos</strong>: Deberás implementar la funcionalidad de actualizar el perfil del <code>Usuario</code> y el <code>Vehículo</code> del conductor.</li>
      </ul>
    </td>
  </tr>
</table>


## Importante ⚠️
> + No modificar ningún atributo `id` de los elementos HTML, ya que son necesarios para ejecutar los test del autograder.
> + No modificar las rutas del frontend, ya que también se usan para los test. Si deseas agregar una ruta nueva, asegúrate de que no entre en conflicto con las existentes.
> + No es necesario crear más componentes. Si deseas agregar más componentes, ten cuidado en no eliminar los existentes. 


## Getting Started 🚀

En la raíz verán dos carpetas: `backend` y `frontend`. 

- En la carpeta de `backend` se encuentra la API de Spring Boot realizada en los laboratorios e2e anteriores. 
- En la carpeta de `frontend` se encuentra el proyecto de React-Vite que consumirá el backend.

### Cambios en Spring Boot ❗
Para que el frontend pueda consumir la API de Spring Boot, se creó un nuevo archivo de configuración en la carpeta `config/CorsConfig.java`, el cual desactiva la política de CORS para que el frontend pueda consumir la API sin problemas.

Código de `CorsConfig.java`:
```java
@Configuration
public class CorsConfig {
    @Bean
    public WebMvcConfigurer corsConfigurer() {
        return new WebMvcConfigurer() {
            @Override
            public void addCorsMappings(CorsRegistry registry) {
                // Disable Cors Origin to React frontend
                registry.addMapping("/**").allowedOrigins("http://127.0.0.1:3000");
            }
        };
    }
}
```

### Ejecutar el proyecto de Spring Boot ▶️
Antes de ejecutar el proyecto de React-Vite, es necesario ejecutar el proyecto de Spring Boot para que la API esté disponible. Pueden abrirlo desde IntelliJ IDEA en la carpeta `backend` y ejecutarlo desde ahí. Asegurarse que su proyecto esté corriendo en el puerto `8080`.

### Organización de carpetas 📂
El proyecto de **fronend** está organizado de la siguiente manera:

``` markdown
frontend/
├── cypress/              # Carpeta de Cypress (Testing)
│ └── e2e/                # Archivos de testing 
├── node_modules/         # Dependencias del proyecto
├── public/               # Archivos estáticos de la aplicación
├── src/                  # Archivos de código fuente de la aplicación 
│ ├── assets/             # Archivos multimedia 
│ ├── components/         # Componentes de la aplicación
│ ├── layout/             # Componentes plantilla de la aplicación
│ ├── pages/              # Páginas principales
│ ├── service/            # Archivos de configuración de Axios
│ ├── styles/             # Estilos globales y de componentes
│ │ └── index.css
│ ├── App.jsx             # Archivo principal 
│ └── main.jsx            # Archivo de inicialización          
├── .gitignore
├── cypress.config.js     # Archivo de configuración de Cypress 
├── index.html            # Archivo HTML principal
├── package.json          # Archivo de configuración de dependencias
├── tailwind.config.js    # Archivo de configuración de Tailwind
└── vite.config.js        # Archivo de configuración de Vite
```

### Ejecutar el proyecto de React-Vite 🪽

Escribir los siguientes comandos en la terminal para cargar las dependencias del proyecto y ejecutar el servidor de React-Vite

```bash
cd frontend
npm install
npm run dev
```
  
Les aparecerá un mensaje similar a este:

```bash  
 VITE v5.2.11  ready in 429 ms

  ➜  Local:   http://localhost:3000/
  ➜  Network: http://192.168.0.11:3000/
  ➜  Network: http://172.31.96.1:3000/
  ➜  press h + enter to show help
```

Pueden acceder a su frontend desde el navegador en la dirección [http://localhost:3000/](http://localhost:3000/)

> **Nota:** el puerto puede variar dependiendo de la configuración de Vite.

### Ejecutar el test de Cypress 🧪

Para ejecutar los test de Cypress y probar tu avance, escribir el siguiente comando en una nueva terminal:

```bash
npx cypress open
```

> **Nota:** Asegurarse de tener el servidor de React y de SpringBoot corriendo antes de ejecutar los test de Cypress.

Luego, te aparecerá la interfaz de Cypress. Seguir los siguientes pasos para probar tu avance:

![Cypress test](./media/cypress_tests.gif)


## Diseño (5pts) 🖌️
El diseño es una parte fundamental en el desarrollo de software, ya que es lo primero que ve el usuario al interactuar con la aplicación. No obstante, en el curso de CS2031 no será indispensable tener un diseño perfecto, pero sí funcional.  

Se recomienda clonar el diseño del prototipo del E2E con ayuda de Tailwind. **Pero puedes crear tu propio diseño si lo deseas**.

### Prototipo en Figma
El prototipo en Figma es una guía visual para que puedan clonar el diseño de la web del E2E. Pueden acceder a él desde este enlace: [**Prototipo web del E2E**](https://www.figma.com/community/file/1374595433604097313/diseno-web-e2e)

![Prototipo web del E2E](./media/FigmaE2E.gif)

### Estructura de rutas y enrutamiento del Frontend 🌎
Se utilizó `React Router` para el enrutamiento de las páginas. A continuación, se muestra la estructura de rutas y redirecciones del frontend:

<table>
  <thead>
    <tr>
      <th>URL</th>
      <th>Funcionalidades</th>
      <th>Redirect</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>
        /auth/login
        <br>
        <br>
        Página de inicio de sesión para los usuarios    
      </th>
      <td>
        <ul>
          <li>Al hacer login, deberá redirigir a la página <code>/dashboard</code>.</li>
          <li>Tendrá que enrutarse a esta página siempre y cuando el usuario no esté autenticado.</li>
          <li>También deberá enrutarse a esta página cuando el usuario haga logout.</li>
          <li>La ruta principal <code>/</code> deberá redirigir a esta página.</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>/dashboard</li>
          <li>/auth/login</li>
        </ul>
      </td>
    </tr>
    <tr>
      <th>
        /auth/register
        <br>
        <br>
        Página de registro para los usuarios
      </th>
      <td>
        <ul>
          <li>Si el usuario selecciona que <strong>NO</strong> es conductor, deberá redirigir a la página <code>/dashboard</code>.</li>
          <li>Si el usuario selecciona que <strong>SI</strong> es conductor, deberá mostrar un componente nuevo con el formulario de registro de vehículo</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>/dashboard</li>
        </ul>
      </td>
    </tr>
    <tr>
      <th>
        /dashboard
        <br>
        <br>
        Página principal para visualizar el dashboard del usuario
      </th>
      <td>
        <ul>
          <li>Si el usuario es un <em>Passenger</em>, deberá mostrar el historial de viajes y su perfil.</li>
          <li>Si el usuario es un <em>Driver</em>, deberá mostrar su perfil y la información del vehículo.</li>
          <li>Al hacer logout, deberá redirigir a la página <code>/auth/login</code>.</li>
          <li>Tendrá que enrutarse a esta página siempre y cuando el usuario esté autenticado.</li>
          <li>Al editar el perfil del usuario, deberá redirigir a la página <code>/profile/edit</code>.</li>
          <li>Al editar el vehículo del conductor, deberá redirigir a la página <code>/vehicle/edit</code>.</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>/auth/login</li>
          <li>/profile/edit</li>
          <li>/vehicle/edit</li>
        </ul>
      </td>
    </tr>
    <tr>
      <th>
        /profile/edit
        <br>
        <br>
        Página para editar la información del usuario
      </th>
      <td>
        <ul>
          <li>Al hacer click en actualizar, deberá redirigir a <code>/dashboard</code>.</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>/dashboard</li>
        </ul>
      </td>
    </tr>
    <tr>
      <th>
        /vehicle/edit
        <br>
        <br>
        Página para editar la información del vehículo del conductor
      </th>
      <td>
        <ul>
          <li>Al hacer click en actualizar, deberá redirigir a <code>/dashboard</code>.</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>/dashboard</li>
        </ul>
      </td>
    </tr>
    <tr>
      <th>
        /*
        <br>
        (todos los demás)
      </th>
      <td>
        <ul>
          <li>Si la ruta no existe, deberá mostrar un componente de 404 - Not Found</li>
          <li>También mostrará un botón para retroceder a la página anterior en la que se estaba</li>
        </ul>
      </td>
      <td>
        <li>*return</li>
      </td>
    </tr>
  </tbody>
</table>


## Funcionalidad (15pts) 💻

### Tarea 1 - Creación de fetchs ✏️
Creación de los fetchs hacia la API de SpringBoot con JavaScript y Axios

Editar el archivo `/frontend/services/api.js` para implementar los fetchs necesarios para consumir la API del E2E. Aquí hay un ejemplo de una función async para el login:

```javascript
import axios from 'axios';
const API_URL = 'http://localhost:8080/';

// Implementar las funciones para hacer fetch
export const fetchLogin = async (body) => {
    // Implementar fetch para hacer login
};
```

> **HINT 1:** Utilizar el `localStorage` para almacenar el token con el siguiente código:
> ```javascript
> // Guardar token en localStorage
> localStorage.setItem('token', token);
> 
> // Obtener token de localStorage
> const token = localStorage.getItem('token');
> ```

> **HINT 2:** Utiliza la función `getRoleBasedOnToken` de `/services/api.js` para obtener el rol del usuario. 

Fetchs solicitados:

| **Función**      | **Método HTTP** | **Request Body**           | **Backend URI**  | **Response Body**          |
|------------------|-----------------|----------------------------|------------------|----------------------------|
| fetchLogin       | POST            | `LoginReq`                 | /auth/login      |                            |
| fetchRegister    | POST            | `RegisterReq`              | /auth/register   |                            |
| getPassenger     | GET             |                            | /passenger/me    | `PassengerSelfResponseDTO` |
| getDriver        | GET             |                            | /driver/me       | `DriverResponseDto`        |
| getRidesByUser   | GET             | page, size                 | /ride/user       | `Page<RidesByUserDto>`     |
| updatePassenger  | PATCH           | `passengerSelfResponseDTO` | /passenger/me    |                            |
| updateDriverInfo | PATCH           | id, `NewDriverInfoDto`     | /driver/{id}     | String                     |
| updateDriverCar  | PATCH           | id, `VehicleBasicDto`      | /driver/{id}/car | String                     |
| deletePassenger  | DELETE          | id                         | /passenger/{id}  |                            |
| deleteDriver     | DELETE          | id                         | /driver/{id}     |                            |


### Tarea 2 - Obtención de datos ✏️
Obtención de datos desde los formularios con React Hooks

+ Deberás utilizar React Hooks para obtener los datos de todos los formularios de la página web y enviarlos al backend. 
+ Además, se debe crear un apartado al final de cada formulario para mostrar los errores de validación.


### Tarea 3 - Register y delete de usuarios ✏️
Registrar un nuevo `User` y eliminar su cuenta.

+ El formulario de registro deberá aceptar el registro tanto de pasajeros como de conductores. 
  + Si el usuario selecciona que es conductor, deberá mostrarse un nuevo componente con el formulario de registro de vehículo.
  + Si el usuario selecciona que no es conductor, deberá redirigir a la página de dashboard.
+ En cualquiera de los dos casos, debe retornar el token JWT y almacenarlo en `localStorage` con el fin de enviarlo en los headers de los fetchs.
+ Al eliminar la cuenta, deberá redirigir a la página de login.

### Tarea 4 - Flujo de un Passenger ✏️
Loggear un `Passenger`, mostrar su perfil, mostrar su historial de viajes, actualizar su perfil y hacer logout.

+ Al hacer login, deberá redirigir a la página de dashboard.
+ El dashboard debe mostrar solamente el historial de viajes y el perfil del pasajero de acuerdo al token.
+ Se debe lograr editar el perfil de usuario y redirigir a la página de dashboard.
+ Al hacer logout, se debe eliminar el Token y deberá redirigir a la página de login.

### Tarea 5 - Flujo de un Driver ✏️
Loggear un `Driver` existente, mostrar su perfil, actualizar su vehículo y hacer logout.

+ Al hacer login, deberá redirigir a la página de dashboard.
+ El dashboard debe mostrar el perfil del conductor y la información del vehículo de acuerdo al token.
+ Se debe lograr editar el vehículo del conductor y redirigir a la página de dashboard.
+ Al hacer logout, se debe eliminar el Token y deberá redirigir a la página de login.

### Tarea 6 - Not Found Page ✏️
Mostrar una página de error 404 cuando la ruta no exista.

+ Mostrar un mensaje de error, la ruta actual y un botón para redirigir a la página de login.


