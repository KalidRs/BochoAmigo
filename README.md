bochoAmigoAPI:
  title: "🚗 BochoAmigo API"
  descripcion: >
    BochoAmigo API es un sistema sencillo y eficiente para el control de viajes de choferes.
    Permite registrar, consultar, modificar y cancelar viajes, facilitando la administración
    y el monitoreo de los traslados realizados, el pasajero transportado, el destino y la hora de cada viaje.

  caracteristicas:
    - Registro de viajes para cada chofer, incluyendo destino, hora y pasajero.
    - Consulta de todos los viajes activos o filtrados por ciudad.
    - Edición de los datos de un viaje (pasajero, destino, hora, etc.).
    - Cancelación de viajes, manteniendo el historial completo.
    - API RESTful: fácil de integrar con paneles web, apps o asistentes de voz (como Alexa).

  endpoints:
    - method: GET
      path: /viajes
      description: Consulta todos los viajes activos.

    - method: GET
      path: /viajes/ciudad/:destino
      description: Consulta viajes activos filtrados por ciudad.

    - method: POST
      path: /viajes
      description: Registra un nuevo viaje.
      body_example:
        nombre_conductor: "Pedro"
        destino: "Puebla"
        hora: "18:00"
        pasajero: "Luis"

    - method: PUT
      path: /viajes/:id
      description: Actualiza un viaje.
      body_example:
        pasajero: "Mario"
        destino: "CDMX"
        hora: "19:30"

    - method: DELETE
      path: /viajes/:id
      description: Cancela un viaje existente.

  alexa_integration:
    descripcion: >
      BochoAmigo cuenta con una skill personalizada para Alexa, desarrollada con el Alexa Skills Kit SDK (v2).
      Esta skill permite a los usuarios interactuar con el sistema usando comandos de voz en español.

    intents:
      - name: ListarViajesIntent
        examples:
          - "¿Qué viajes hay?"
          - "Dime los viajes activos"
        descripcion: Consulta los viajes actuales.

      - name: ListarViajesPorCiudadIntent
        examples:
          - "¿Qué viajes hay a Puebla?"
        descripcion: Filtra los viajes por destino.

      - name: RegistrarViajeIntent
        examples:
          - "Registra un viaje a Puebla a las 5 para Luis"
        descripcion: Registra un nuevo viaje.

      - name: ActualizarViajeIntent
        examples:
          - "Actualiza el viaje a Puebla para Mario con el conductor Pedro"
        descripcion: Edita un viaje existente.

      - name: EliminarViajeIntent
        examples:
          - "Cancela el viaje a Puebla de Luis"
        descripcion: Cancela un viaje.
