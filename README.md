## BochoAmigo API
### description: 
  BochoAmigo API es un sistema sencillo y eficiente para el control de viajes de choferes.
  Permite registrar, consultar, modificar y cancelar viajes, facilitando la administración
  y el monitoreo de los traslados realizados, el pasajero transportado, el destino y la hora de cada viaje.

### caracteristicas:
  - Registro de viajes para cada chofer, incluyendo destino, hora y pasajero.
  - Consulta de todos los viajes activos o filtrados por ciudad.
  - Edición de los datos de un viaje (pasajero, destino, hora, etc.).
  - Cancelación de viajes, manteniendo el historial completo.
  - API RESTful fácil de integrar con paneles web, apps o asistentes de voz como Alexa.

#### endpoints:
  #### - method: GET
    path: /viajes
    descripcion: Consulta todos los viajes activos.

  #### - method: GET
    path: /viajes/ciudad/:destino
    descripcion: Consulta viajes activos filtrados por ciudad.

  #### - method: POST
    path: /viajes
    descripcion: Registra un nuevo viaje.
    body_example:
      nombre_conductor: Pedro
      destino: Puebla
      hora: "18:00"
      pasajero: Luis

  #### - method: PUT
    path: /viajes/:id
    descripcion: Actualiza un viaje existente.
    body_example:
      pasajero: Mario
      destino: CDMX
      hora: "19:30"

  #### - method: DELETE
    path: /viajes/:id
    descripcion: Cancela un viaje existente.

### alexa_integration:
  #### descripcion: 
    BochoAmigo cuenta con una skill personalizada para Alexa, desarrollada con el Alexa Skills Kit SDK (v2).
    Esta skill permite a los usuarios interactuar con el sistema usando comandos de voz en español.

  #### intents:
    - name: ListarViajesIntent
      descripcion: Consulta los viajes actuales.
      examples:
        - ¿Qué viajes hay?
        - Dime los viajes activos

    - name: ListarViajesPorCiudadIntent
      descripcion: Filtra los viajes por ciudad.
      examples:
        - ¿Qué viajes hay a Puebla?

    - name: RegistrarViajeIntent
      descripcion: Registra un nuevo viaje.
      examples:
        - Registra un viaje a Puebla a las 5 para Luis

    - name: ActualizarViajeIntent
      descripcion: Edita un viaje existente.
      examples:
        - Actualiza el viaje a Puebla para Mario con el conductor Pedro

    - name: EliminarViajeIntent
      descripcion: Cancela un viaje.
      examples:
        - Cancela el viaje a Puebla de Luis

  #### slots:
    - name: destino
      type: text
      description: Ciudad destino del viaje

    - name: pasajero
      type: AMAZON.FirstName
      description: Nombre del pasajero

    - name: hora
      type: AMAZON.TIME
      description: Hora del viaje

    - name: nombre_conductor
      type: AMAZON.FirstName
      description: Nombre del conductor

