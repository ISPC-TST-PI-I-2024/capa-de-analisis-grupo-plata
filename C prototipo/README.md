# Proyecto IoT: API RESTful

Este proyecto proporciona una API RESTful para gestionar datos de un proyecto IoT utilizando Flask y MySQL. La API soporta operaciones CRUD para varias entidades como usuarios, dispositivos, proyectos, configuraciones, datos de dispositivos y seguridad.

## Estructura del Proyecto

``` bash
c_capa_de_analisis/
├── app.py
├── db_config.py
├── models.py
├── routes/
│ ├── configuraciones.py
│ ├── datos_dispositivos.py
│ ├── dispositivos.py
│ ├── proyectos.py
│ ├── seguridad.py
│ └── usuarios.py
├── requirements.txt
└── Dockerfile
```

## Instalación

1. Clonar el repositorio.
2. Navegar al directorio del proyecto.
3. Ejecutar `pip install -r requirements.txt` para instalar las dependencias.
4. Configurar la base de datos en `db_config.py`.
5. Ejecutar `python app.py` para iniciar el servidor.

## Uso

### Endpoints

La API proporciona los siguientes endpoints:

#### Usuarios

1. **Obtener Usuarios**
   - **Método**: `GET`
   - **URL**: `/usuarios/`
   - **Descripción**: Devuelve una lista de todos los usuarios registrados en la base de datos.
   - **Respuesta**:
     ```json
     [
       {
         "id": 1,
         "nombre": "Juan Perez",
         "email": "juan.perez@example.com"
       },
       ...
     ]
     ```  

2. **Obtener Usuario**
   - **Método**: `GET`
   - **URL**: `/usuarios/<int:id>`
   - **Descripción**: Devuelve una lista con los datos del usuario registrado con un id específico.
   - **Respuesta**:
     ```json
     [
       {
         "id": 1,
         "nombre": "Juan Perez",
         "email": "juan.perez@example.com"
       },
     ]
     ```

3. **Crear Usuario**
    - **Método**: `POST`
    - **URL**: `/usuarios/`
    - **Descripción**: Crea un nuevo usuario en la base de datos.
    - **Cuerpo de la Solicitud**:
      ```json
      {
        "nombre": "Juan Perez",
        "email": "juan.perez@example.com",
        "rol": "admin", 
        "password": "password123"
      }
      ```
    - **Respuesta**: Código de estado `201 Created` si se crea con éxito.

4. **Actualizar usuario**
    - **Método**: `PUT`
    - **URL**: `/usuarios/<int:id>`
    - **Descripción**: Actualiza un usuario existente en la base de datos.
    - **Cuerpo de la Solicitud**:
    ```json
      {
        "nombre": "Juan Alberto Perez",
        "email": "juan.a.perez@example.com",
        "rol": "user", 
        "password": "password987"
      }
      ```
    - **Respuesta**: Código de estado `204 No Content` si se crea con éxito.

5. **Borrar usuario**
    - **Método**: `DELETE`
    - **URL**: `/usuarios/<int:id>`
    - **Descripción**: Elimina un usuario existente en la base de datos.
    - **Cuerpo de la Solicitud**:

    - **Respuesta**: Código de estado `204 No Content` si se elimina el usuario con éxito.

#### Dispositivos

1. **Obtener Dispositivos**
   - **Método**: `GET`
   - **URL**: `/dispositivos/`
   - **Descripción**: Devuelve una lista de todos los dispositivos registrados en la base de datos.
   - **Respuesta**:
     ```json
     [
       {
         "id": 1,
         "nombre": "Estation_1",
         "tipo": "Nodo medicion calidad aire",
         "ubicacion": "31°26'46.9\"S 64°10'28.8\"W",
         "id_usuario": "3"
       },
       ...
     ]
     ```  

2. **Obtener Dispositivo**
   - **Método**: `GET`
   - **URL**: `/dispositivos/<int:id>`
   - **Descripción**: Devuelve una lista con los datos del dispositivo registrado con un id específico.
   - **Respuesta**:
     ```json
     [
       {
          "id": 1,
         "nombre": "Estation_1",
         "tipo": "Nodo medicion calidad aire",
         "ubicacion": "31°26'46.9\"S 64°10'28.8\"W",
         "id_usuario": "3"
       },
     ]
     ```

3. **Crear Dispositivo**
    - **Método**: `POST`
    - **URL**: `/dispositivos/`
    - **Descripción**: Crea un nuevo dispositivo en la base de datos.
    - **Cuerpo de la Solicitud**:
      ```json
      [
        {
          "nombre": "Estation_2",
          "tipo": "Nodo medicion viento",
          "ubicacion": "31°26'46.9\"S 64°10'28.8\"W",
          "id_usuario": "2"
        },
      ]
      ```
    - **Respuesta**: Código de estado `201 Created` si se crea con éxito.

4. **Actualizar Dispositivo**
    - **Método**: `PUT`
    - **URL**: `/dispositivos/<int:id>`
    - **Descripción**: Actualiza un dispositivo existente en la base de datos.
    - **Cuerpo de la Solicitud**:
    ```json
      
      {
        "nombre": "Estation_2",
        "tipo": "Nodo medicion viento y calidad de aire",
        "ubicacion": "31°26'46.9\"S 64°10'28.8\"W",
        "id_usuario": "2"
      },
      
      ```
    - **Respuesta**: Código de estado `204 No Content` si se crea con éxito.

5. **Borrar Dispositivo**
    - **Método**: `DELETE`
    - **URL**: `/dispositivos/<int:id>`
    - **Descripción**: Elimina un dispositivo existente en la base de datos.
    - **Cuerpo de la Solicitud**:

    - **Respuesta**: Código de estado `204 No Content` si se elimina el usuario con éxito.

#### Datos de Dispositivos

1. **Obtener Datos de Dispositivos**
   - **Método**: `GET`
   - **URL**: `/datos_dispositivos/`
   - **Descripción**: Devuelve una lista de los datos registrados para los dispositivos.
   - **Respuesta**:
     ```json
     [
       {
         "id": 1,
         "dispositivo_id": 1,
         "timestamp": "2024-06-24T00:00:00Z",
         "valor": 23.5,
         "unidad": "C"
       },
       ...
     ]
     ```

2. **Obtener Dato de Dispositivo**
   - **Método**: `GET`
   - **URL**: `/datos_dispositivos/<int:id>`
   - **Descripción**: Devuelve una lista con los datos registrados para un dispositivo específico.
   - **Respuesta**:
     ```json
     [
       {
         "id": 1,
         "dispositivo_id": 1,
         "timestamp": "2024-06-24T00:00:00Z",
         "valor": 23.5,
         "unidad": "C"
       },
     ]
     ```

3. **Enviar Datos de Dispositivo**
   - **Método**: `POST`
   - **URL**: `/datos_dispositivos/`
   - **Descripción**: Envia nuevos datos para un dispositivo.
   - **Cuerpo de la Solicitud**:
     ```json
     {
       "dispositivo_id": 1,
       "valor": 23.5,
       "unidad": "C"
     }
     ```
   - **Respuesta**: Código de estado `201 Created` si se envía con éxito.  

4. **Actualizar Dato de Dispositivo**
    - **Método**: `PUT`
    - **URL**: `/datos_dispositivos/<int:id>`
    - **Descripción**: Actualiza el dato cargado por un dispositivo existente en la base de datos.
    - **Cuerpo de la Solicitud**:
    ```json
      
      {
        "dispositivo_id": 1,
       "valor": 27.5,
       "unidad": "C"
      },
      
      ```
    - **Respuesta**: Código de estado `204 No Content` si se crea con éxito.

5. **Borrar Dato de Dispositivo**
    - **Método**: `DELETE`
    - **URL**: `/datos_dispositivos/<int:id>`
    - **Descripción**: Elimina un dato cargado por un dispositivo existente en la base de datos.
    - **Cuerpo de la Solicitud**:

    - **Respuesta**: Código de estado `204 No Content` si se elimina el usuario con éxito.

#### Configuraciones

1. **Obtener Configuraciones**
   - **Método**: `GET`
   - **URL**: `/configuraciones/`
   - **Descripción**: Devuelve una lista de las configuraciones del sistema.
   - **Respuesta**:
     ```json
     [
       {
         "id": 1,
         "nombre": "intervalo_muestreo",
         "valor": "10s"
       },
       ...
     ]
     ```

2. **Actualizar Configuración**
   - **Método**: `PUT`
   - **URL**: `/configuraciones/{id}`
   - **Descripción**: Actualiza una configuración específica.
   - **Cuerpo de la Solicitud**:
     ```json
     {
       "nombre": "intervalo_muestreo",
       "valor": "10s"
     }
     ```
   - **Respuesta**: Código de estado `200 OK` si se actualiza con éxito.

#### Proyectos

1. **Obtener Proyectos**
   - **Método**: `GET`
   - **URL**: `/proyectos/`
   - **Descripción**: Devuelve una lista de todos los proyectos registrados.
   - **Respuesta**:
     ```json
     [
       {
         "id": 1,
         "nombre": "Proyecto IoT",
         "descripcion": "Proyecto para monitoreo de temperatura"
       },
       ...
     ]
     ```

2. **Crear Proyecto**
   - **Método**: `POST`
   - **URL**: `/proyectos/`
   - **Descripción**: Crea un nuevo proyecto en la base de datos.
   - **Cuerpo de la Solicitud**:
     ```json
     {
       "nombre": "Proyecto IoT",
       "descripcion": "Proyecto para monitoreo de temperatura"
     }
     ```
   - **Respuesta**: Código de estado `201 Created` si se crea con éxito.

#### Seguridad

1. **Obtener Información de Seguridad**
   - **Método**: `GET`
   - **URL**: `/seguridad/`
   - **Descripción**: Devuelve la información de seguridad del sistema.
   - **Respuesta**:
     ```json
     {
       "seguridad_activa": true,
       "ultimo_chequeo": "2024-06-24T00:00:00Z"
     }
     ```

### Autenticación

Se requiere una clave de API para todas las solicitudes. La clave debe ser incluida en el encabezado `X-API-KEY`. Claves válidas incluyen `jade`, `opalo`, `rubi`, `topaz`, y `plata`.

```bash
curl -H "X-API-KEY: jade" https://api.gonaiot.com/jade/usuarios/
```	

## Licencia

Este proyecto está licenciado bajo los términos de la licencia MIT. Ver el archivo LICENSE para más detalles.