# qro-transit-bot

Esta página identifica al bot que consulta el sitio público **qrobus.gob.mx**. Si viste este User-Agent en tus registros, aquí está quiénes somos y cómo contactarnos.

```
qro-transit-bot/<versión> (+<url de esta página>)
```

## ¿Qué es?

Es el recolector de datos de una **app no oficial** de transporte público para Querétaro. El objetivo es ofrecer una app rápida que funcione sin conexión a internet.

**No tenemos relación con la AMEQ ni con el Gobierno del Estado de Querétaro**, y no hablamos en su nombre.

## ¿Qué consulta y con qué frecuencia?

Solo consulta las páginas y los datos que el sitio público ya carga en cualquier navegador:

| Qué | Dónde | Frecuencia |
|---|---|---|
| Lista de rutas | `/Rutas`, `/RutasNocturnas` | 1 vez al día, de madrugada |
| Trazos y paradas de cada ruta | `/Rutas/rutaMostrar`, `/Rutas/paradasTimeline` | 1 vez al día, una ruta a la vez, con pausas entre rutas |
| Noticias y avisos | `/Nota/...` | cada 1 a 3 horas |
| Posición de los camiones | `/proxy/ultima_posicion` | 1 consulta cada 15 a 20 segundos, **compartida por todos los usuarios de la app** |

## Lo que nunca hacemos

- Consultar saldos de tarjetas de forma automática, masiva o desde nuestro servidor. La app permite que cada persona consulte el saldo de **sus propias** tarjetas: esa consulta sale de su teléfono solo cuando la pide (como si usara el sitio), con el User-Agent `qro-transit-app/<versión>` y máximo una vez por minuto.
- Iniciar sesión, enviar credenciales o hacer pagos.
- Descompilar la app oficial, interceptar su tráfico ni usar endpoints que el sitio web no use.
- Reintentar en bucle cuando el sitio falla: si algo responde con error, el bot se detiene y usamos los últimos datos guardados.

## Contacto

Para cualquier duda, queja o petición, **abre un Issue en este repositorio**.

Si nos piden reducir la frecuencia, dejar de consultar alguna página o dejar de consultar el sitio por completo, lo hacemos. También nos interesa colaborar: si existen datos oficiales (por ejemplo, GTFS), preferimos usarlos.
