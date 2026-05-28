# README

## Eclipse Telemetry UI - Advanced

Eclipse Telemetry UI es una interfaz web de vanguardia diseñada para la monitorización en tiempo real de variables ambientales y críticas. Desarrollada bajo un enfoque estético minimalista e industrial, permite la conexión directa con hardware externo (como microcontroladores Arduino) a través del navegador, ofreciendo una visualización limpia y de alta fidelidad para el análisis de datos.

El sistema está licenciado y desarrollado por **Nicolás Graña Míguez** y **Nicotech**.

---

## Características Principales

* **Conexión Serial Nativa (Web Serial API):** Conexión directa a dispositivos físicos a través de puertos COM a 9600 baudios, eliminando la necesidad de servidores intermediarios o software puente local.
* **Analíticas en Tiempo Real:** Gráfica dinámica integrada mediante **Chart.js** con doble eje independiente optimizado para lecturas de Temperatura y Luminosidad.
* **Historial de Registros Continuo:** Tablas de datos que registran y muestran de forma estructura los últimos eventos capturados junto con su marca de tiempo exacta.
* **Exportación de Datos:** Capacidad de volcar todo el historial de datos acumulado durante la sesión activa en un archivo de hoja de cálculo estándar de Excel (`.xlsx`).
* **Modularidad y Flexibilidad:** * Alternancia entre disposiciones visuales del tablero principal (columnas en paralelo o lista vertical).
    * Capacidad de inyectar dinámicamente nuevas pestañas de visualización en el menú inferior (*Dock*).
    * Creación en caliente de tablas estáticas de referencia personalizadas.
* **Interfaz de Usuario Avanzada:** Diseño responsivo con tipografía refinada, transiciones fluidas y un menú de navegación persistente con efecto de desenfoque de fondo (*backdrop-filter*).

---

## Especificaciones Técnicas

* **Estructura y Estilos:** HTML5 y CSS3 nativo, utilizando Flexbox, Grid y animaciones optimizadas para el rendimiento del navegador.
* **Lógica del Lado del Cliente:** JavaScript (ES6+) asíncrono para la gestión del flujo continuo de datos de entrada.
* **Librerías Externas:** * **Chart.js:** Renderizado y actualización en tiempo real del lienzo de gráficos.
    * **SheetJS (XLSX):** Procesamiento y empaquetado de estructuras de datos a archivos binarios de Excel.

---

## Protocolo de Comunicación de Hardware

Para garantizar una correcta sincronización, el firmware del dispositivo emisor (Arduino, ESP32, etc.) debe transmitir las lecturas a través del puerto serie utilizando el formato estructurado **JSON**, finalizando cada trama estrictamente con un salto de línea (`\n`).

### Formato de Trama Requerido:
```json
{
  "temperatura": 24.5,
  "luz": 68
}
