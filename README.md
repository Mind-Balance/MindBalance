# Bootcamp Desarrollo de Apps Móviles - Proyecto final

<div align="center">
  <img src="assets/mindBalanceLogo.png" alt="Logo MindBalance" width="550" height="350">
</div>

---

<p align="center">
  <strong><span style="font-size:20px;">Backend</span></strong>
</p>

---

## Índice
 
* [💧 Servidor en Vapor](#server)
    * [Instalación](#instalacion)
    * [Endpoints](#endpoints)
        * [Sign In](#signIn)
        * [Refresh Token](#refresh)
        * [Change Password](#changePassword)
        * [Confirm Identity](#identity)
        * [Change Forgotten Password](#forgotten)
* [✍🏼 Autores/as](#autorxs)
* [©️ Licencia](#licencia)

<a name="server"></a>
## 💧 Servidor en Vapor

<a name="instalacion"></a>
### Instalación

Para comenzar a utilizar la API Rest, sigue estos sencillos pasos:

1. **Requisitos previos**

    * Swift 5.9
    * Vapor 4.92.4
    * Vapor Toolbox 18.7.4

2. **Clonar el Repositorio**

    ```bash
    git clone <url-del-repositorio>
    ```

    Asegurarse de tener instalado Git en el sistema antes de clonar el repositorio.     Esto descargará el código fuente de la API en tu máquina local.
    
3. **Crear BBDD local**

    Asegurarse de tener una base de datos PostgreSQL activa en tu máquina local.

4. **Configuración de Variables de Entorno**

    Crea un archivo `.env` en la raíz del proyecto y rellena la siguiente información:
    
    ```bash
    JWT_KEY=
    API_KEY=
    DATABASE_URL=postgresql://<usuario>@<host>/<nombre_de_la_base_de_datos>
    APP_BUNDLE_ID=

    ```
    Asegurarse de completar cada variable con los valores correspondientes necesarios para el funcionamiento de la aplicación. 
    
La URL de la base de datos debe seguir el formato `postgresql://<usuario>@<host>/<nombre_de_la_base_de_datos>`.

5. **Configuración de Xcode**

    * Abre el proyecto en Xcode.
    * Edita el esquema (Scheme) del proyecto.
    * Activa la opción de "Use custom working directory" y enlaza la carpeta donde     se encuentra el proyecto recién clonado.

6. **Ejecución del Proyecto**

    * Ejecuta el proyecto en Xcode.
    * Verifica en la terminal que el servidor se ha inicializado correctamente.

<a name="endpoints"></a>
### Endpoints

<a name="signIn"></a>
#### Sign In

* **Descripción:** permite a los usuarios iniciar sesión en la aplicación.
* **URL:** `<API_URL>/api/v1/auth/signin`
* **Método:** GET
* **Headers:**
    * `MindBalance-ApiKey`: API_KEY
    * `Authorization`: Basic Auth + email + password
* **Respuesta:**

    ```json
    {
          "accessToken": "<accessToken>",
          "refreshToken": "<refreshToken>"
    }
    ```
* **Notas:** al realizar la llamada, se comprueba si el usuario ha cambiado o no la contraseña a una personal en su primer inicio de sesión (lo cual es obligatorio). Si no la ha cambiado, la llamada devuelve el campo `accessToken` y `refreshToken` como `String` vacíos.

<a name="refresh"></a>
#### Refresh Token

* **Descripción:** permite refrescar el token de acceso.
* **URL:** `<API_URL>/api/v1/auth/refresh`
* **Método:** GET
* **Headers:**
    * `MindBalance-ApiKey`: API_KEY
    * `Authorization`: Bearer + Refresh Token
* **Respuesta:**

    ```json
    {
          "accessToken": "<accessToken>",
          "refreshToken": "<refreshToken>"
    }
    ```

<a name="changePassword"></a>
#### Change Password

* **Descripción:** permite a los usuarios cambiar de contraseña empleando su email y su contraseña actual. *Endpoint* usado para el cambio de contraseña obligatorio al iniciar sesión por primera vez en la aplicación MindBalance.
* **URL:** `<API_URL>/api/v1/password/change`
* **Método:** POST
* **Headers:**
    * `MindBalance-ApiKey`: API_KEY
    * `Authorization`: Basic Auth + email + password
* **Body:**
    * `newPassword`: nueva contraseña del usuario
* **Respuesta:**

    ```json
    {
          "accessToken": "<accessToken>",
          "refreshToken": "<refreshToken>"
    }
    ```
    
<a name="identity"></a>
#### Confirm Identity

* **Descripción:** permite al servidor identificar y autenticar al usuario mediante su email y DNI cuando este se ha olvidado de su contraseña.
* **URL:** `<API_URL>/api/v1/auth/identity`
* **Método:** POST
* **Headers:**
    * `MindBalance-ApiKey`: API_KEY
* **Body:**
    * `email`: correo electrónico del usuario
    * `dni`: DNI del usuario
* **Respuesta:**

    ```json
    {
          "accessToken": "<accessToken>",
          "refreshToken": "<refreshToken>"
    }
    ```
    
<a name="forgotten"></a>
#### Change Forgotten Password

* **Descripción:** permite a los usuarios cambiar de contraseña empleando en la llamada al servidor el email, DNI y nueva contraseña ya que se olvidó de la misma.
* **URL:** `<API_URL>/api/v1/password/forgotten`
* **Método:** POST
* **Headers:**
    * `MindBalance-ApiKey`: API_KEY
    * `Authorization`: Bearer + Access Token
* **Body:**
    * `email`: correo electrónico del usuario
    * `dni`: DNI del usuario
    * `newPassword`: nueva contraseña del usuario
* **Respuesta:**

    ```json
    true
    ```



<a name="autorxs"></a>
## ✍🏼 Autores/as

<table>
  <tbody>
    <tr>
      <td align="center" width="14.28%"><a href="https://github.com/manuelCAZALLA"><img src="https://github.com/manuelCAZALLA.png" width="100px;" alt="Manuel Cazalla"/><br /><sub><b>Manuel Cazalla</b></sub></a></td>
      <td align="center" width="14.28%"><a href="https://github.com/nataliacamero"><img src="https://github.com/nataliacamero.png" width="100px;" alt="Natalia Camero"/><br /><sub><b>Natalia Camero</b></sub></a></td>
      <td align="center" width="14.28%"><a href="https://github.com/NatCam22"><img src="https://github.com/NatCam22.png" width="100px;" alt="Natalia Hernández"/><br /><sub><b>Natalia Hernández</b></sub></a></td>
      <td align="center" width="14.28%"><a href="https://github.com/Castellano46"><img src="https://github.com/Castellano46.png" width="100px;" alt="Pedro Liébana"/><br /><sub><b>Pedro Liébana</b></sub></a></td>
      <td align="center" width="14.28%"><a href="https://github.com/salvaMsanchez"><img src="https://github.com/salvaMsanchez.png" width="100px;" alt="Salva Moreno"/><br /><sub><b>Salva Moreno</b></sub></a></td>
    </tr>
  </tbody>
</table>

<a name="licencia"></a>
## ©️ Licencia

Este proyecto está bajo la Licencia MIT - ver el archivo [LICENSE.md](https://github.com/Mind-Balance/Vapor-Backend/blob/main/LICENSE.md) para más detalles.
