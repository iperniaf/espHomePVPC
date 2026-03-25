# ESPHome PVPC Display

Proyecto ESPHome para mostrar en una pantalla ESP32 (ST7789 240x240) el precio de la luz (PVPC) y el consumo electrico de casa desde Home Assistant.

## Que hace este script

El archivo `esphome-pvpc.yaml` configura un dispositivo tipo GeekMagic/Mini Display TV con dos pantallas:

- **Vista 1 (tabla por horas):** muestra las 4 horas siguientes con precio por kWh y nivel visual por color (verde/amarillo/rojo).
- **Vista 2 (dashboard):** muestra consumo actual (W/kW) y precio actual (EUR/kWh) en dos arcos de progreso.
- **Cambio de vista tactil:** pulsacion en GPIO32 para alternar entre ambas paginas.
- **Ajustes dinamicos desde Home Assistant:** umbrales de color, umbrales de EUR, rango de precio y potencia maxima.

## Requisitos

- ESPHome instalado (addon de Home Assistant o CLI).
- Home Assistant con API habilitada para ESPHome.
- Hardware ESP32 con pantalla ST7789 240x240 por SPI.
- Sensor de precio PVPC en Home Assistant con atributos horarios `price_00h` a `price_23h`.
- Sensor de potencia instantanea del hogar.

## Entidades esperadas en Home Assistant

En la configuracion actual se usan estas entidades:

- Precio actual y atributos por hora: `sensor.esios_pvpc_2`
- Potencia instantanea: `sensor.sensor_consumo_electrico_power`

Si en tu instalacion tienen otro nombre, cambia los `entity_id` en `esphome-pvpc.yaml`.

## Configuracion inicial

1. Copia `secrets.example.yaml` a `secrets.yaml`.
2. Rellena tus credenciales Wi-Fi en `secrets.yaml`.
3. Revisa nombres de entidades (`entity_id`) y ajustalos si hace falta.
4. Opcional: ajusta umbrales iniciales en la seccion `number:`.

Ejemplo de `secrets.yaml`:

```yaml
wifi_ssid: "MiWiFi"
wifi_password: "MiPassword"
```

## Primer flasheo e instalacion

Tal como indica el propio YAML:

1. Importa `esphome-pvpc.yaml` en ESPHome Builder.
2. Compila y usa `Install -> Manual download` para obtener el `.bin`.
3. Flashea el `.bin` en el dispositivo desde el portal web del GeekMagic.
4. Una vez online en ESPHome, las siguientes actualizaciones ya pueden ser OTA.

## Estructura del repositorio

- `esphome-pvpc.yaml`: configuracion principal de ESPHome.
- `secrets.example.yaml`: plantilla para secretos locales.
- `secrets.yaml`: secretos locales (ignorado por git).

## Seguridad y publicacion en GitHub

- `secrets.yaml` esta ignorado por `.gitignore` para no subir credenciales.
- No subas tokens, claves API ni contrasenas reales al repositorio.
- Antes de publicar, revisa `entity_id`, SSID y cualquier dato sensible en el historial de commits.

## Licencia

Este proyecto se distribuye bajo licencia MIT. Consulta `LICENSE` para mas detalles.
