# Política de privacidad — BabiBo

BabiBo está desarrollado por Le Phuong Trung.

_Última actualización: 18 de noviembre de 2026_

BabiBo es una app de finanzas personales para iPhone. No es una app para iPad.
Quienes la publican no operan un servicio que reciba tu libro mayor. No hay
cuenta de BabiBo, no hay analítica, no hay informes de fallos, no hay
identificador de publicidad y no hay un SDK de terceros que envíe datos por su
cuenta.

Algunas funciones sí envían datos fuera del dispositivo, a una empresa que tú
eliges o a un sitio al que la función tiene que llegar. Esta página dice qué
sale, cómo, por qué, quién lo recibe (incluido el proveedor de IA), cuánto
tiempo se conserva y cómo lo detienes o lo borras.

## Qué se queda en el dispositivo

Todo lo que el libro mayor conoce — cuentas, saldos, movimientos, categorías,
presupuestos, posiciones, fotos de tiques y nombres ya aprendidos de un tique —
se guarda en un archivo de base de datos dentro del contenedor de la app en tu
dispositivo.

Ese archivo entra en la copia de seguridad del dispositivo. Si tienes iCloud
Backup activado, una copia cifrada viaja con el resto del teléfono. Esa copia
es entre tú y Apple. Nosotros no podemos leerla.

Puedes exportar el archivo en cualquier momento desde **Ajustes → Datos** e
importarlo en BabiBo en otro dispositivo. Una copia restaurada no lleva la
sesión del banco: la clave de firma se queda en el teléfono que la creó, y
vuelves a conectar el banco en el teléfono nuevo.

Eliminar la app elimina este archivo. Eso incluye una clave de API de Gemini
guardada, los nombres de productos ya aprendidos, los precios guardados y los
logotipos en caché.

No usamos estos datos para publicidad ni seguimiento, y nunca recibimos una
copia.

## Tu banco, a través de Enable Banking

Opcional, en iPhone, Mac y un servidor que tú alojes. No se envía nada hasta
que registras tu propia aplicación en Enable Banking y conectas un banco.

**Qué.** Saldos, extractos (los movimientos) y los identificadores de cuenta
que devuelve el banco, incluido un IBAN cuando el banco envía uno.

**Cómo.** La app pregunta a Enable Banking, que pregunta a tu banco, y escribe
la respuesta en el archivo local. El identificador de la aplicación y la clave
privada se quedan en tu dispositivo. En el iPhone, una vez conectado un banco,
la app pide a iOS que la despierte por la mañana — apunta a las 07:15, y omite
la descarga si una sincronización ya tuvo éxito en las últimas seis horas — y
vuelve a descargar los extractos. iOS puede ignorar esa hora. La descarga solo
se ejecuta mientras la actualización en segundo plano está activada para
BabiBo.

**Por qué.** Para llenar el libro mayor. Si permitiste las notificaciones, el
teléfono también publica un resumen cuando llegan movimientos nuevos. Esa
notificación se crea en el dispositivo. No se nos envía.

**Quién.** Enable Banking y tu banco. No nosotros. Lo que hacen con los datos
sigue sus condiciones y el consentimiento que das al registrarte y al aprobar
el banco.

**Cuánto tiempo, y cómo detenerlo.** La copia en la app permanece hasta que
eliminas la cuenta. Eliminar una cuenta elimina sus movimientos y, cuando es la
última cuenta de esa conexión, elimina la conexión, de modo que la descarga de
la mañana ya no tiene nada que pedir. Enable Banking y el banco conservan lo
que exigen sus propias condiciones. Nosotros no podemos borrar su copia.
Revoca el consentimiento en tu banco, o en la aplicación de Enable Banking que
registraste.

## Google Gemini

Opcional, y solo en iPhone. No se hace ninguna petición hasta que guardas una
clave en **Ajustes → Tiques de compra**.

**Qué.** Los nombres abreviados de los artículos impresos en un tique, y el
nombre del comercio. No la foto, no los importes, no las fechas y no el resto
del libro mayor. Una petición más puede enviar palabras de categoría ya
guardadas en el teléfono — palabras como « pollo », sin comercio, importe ni
fecha — para archivarlas en una lista fija de familias de productos.

**Cómo.** Creas una clave en
[Google AI Studio](https://aistudio.google.com) y la guardas en Ajustes. La app
llama entonces a la API Gemini de Google
(`generativelanguage.googleapis.com`) con esa clave. Una etiqueta ya respondida
una vez se queda en el teléfono y no se vuelve a enviar.

**Por qué.** Para convertir una abreviatura de caja en un nombre de producto y
una categoría, que se vuelven a escribir en el archivo local.

**Quién.** Google, según las condiciones de la API Gemini que se aplican a la
clave que creaste. Nosotros no recibimos el texto. Google es el proveedor de
IA de esta función.

**Cuánto tiempo, y cómo detenerlo.** Google conserva lo que dicen esas
condiciones. Nosotros no fijamos ese plazo y no tenemos una copia en un
servidor nuestro. La lectura permanece en la base de datos local hasta que
eliminas la app. **Ajustes → Tiques de compra → Retirer** borra la clave del
teléfono y detiene las peticiones siguientes. El botón se llama Retirer. No
borra las lecturas ya guardadas en el teléfono, y no borra lo que Google ya
recibió. Borra o rota la clave también en Google AI Studio si quieres que
Google deje de aceptarla.

## Yahoo Finance

**Qué.** Un símbolo de cotización, como `CW8.PA`. Cuando buscas un valor, el
texto que escribiste. No la cantidad, no el valor y no el nombre de la cuenta.

**Cómo.**

- En el iPhone, una actualización del libro mayor pide a Yahoo un precio por
  cada posición que tiene un símbolo. Guardar un símbolo pregunta de inmediato.
  El campo de búsqueda pregunta cuando buscas. La app no lo hace en la descarga
  en segundo plano de la mañana.
- En el Mac, y en un servidor que tú alojes, Yahoo solo se usa si pones el
  proveedor de precios en Yahoo. El ajuste predeterminado está desactivado, y
  esas versiones no hacen entonces ninguna petición de cotización.

La petición va a `query1.finance.yahoo.com`. No hay clave de API. La conexión
también lleva la dirección de red y un user agent, como cualquier petición
HTTPS. La app no añade un nombre ni un identificador de cuenta.

**Por qué.** Para mostrar un precio y, en el iPhone, para encontrar la
cotización que coincide con lo que escribiste.

**Quién.** Yahoo. No nosotros.

**Cuánto tiempo, y cómo detenerlo.** Los precios se escriben en el archivo
local y permanecen hasta que eliminas la app. Yahoo conserva sus propios
registros según su política de privacidad. No tenemos una cuenta de Yahoo con
la que borrarlos. En el iPhone, elimina la posición para detener más peticiones
de precio sobre ella, y no busques si no quieres que se envíe el texto. En el
Mac y en tu servidor, vuelve a poner el proveedor de precios en `none`.

## Sitios de los comercios

Solo iPhone. Activado de forma predeterminada.

**Qué.** Ningún campo del libro mayor se adjunta a la petición. La app carga
`https://` más el dominio del comercio, y después el icono que esa página
nombra. La petición parece un navegador que pide esa dirección: la propia
dirección, la dirección de red del teléfono y un user agent de navegador. Las
cookies no se guardan ni se envían.

**Cómo.** Mientras **Ajustes → Categorías y comercios → Logos de los comercios**
está activado, y un comercio tiene un sitio conocido o un sitio que escribiste.
La imagen se pide la primera vez que hace falta.

**Por qué.** Para dibujar el icono de ese comercio. Nada más.

**Quién.** El sitio de ese comercio, y quien lo aloja. No un servicio de
logotipos, y no nosotros.

**Cuánto tiempo, y cómo detenerlo.** La imagen permanece en la caché de la app
hasta que iOS borra las cachés o eliminas la app. Un sitio sin un icono
utilizable no se vuelve a pedir durante siete días. Los registros del sitio son
suyos; nosotros no podemos borrarlos. Desactiva **Logos de los comercios** para
detener las peticiones nuevas.

## Tu propio servidor

Opcional. Si apuntas BabiBo a un servidor que tú operas, la app lee y escribe
allí el libro mayor. Esa máquina es tuya. Quita la dirección del servidor en
Ajustes para detenerlo. Borra lo que el servidor guardó en esa máquina.

## Face ID

Si activas el bloqueo de la app, BabiBo pide a iOS que te verifique. iOS
responde sí o no. Tus datos biométricos nunca llegan a la app, y no se envían a
nadie.

## Menores

BabiBo no está dirigido a menores.

## Cambios

Cualquier cambio de esta política se registra en
<https://github.com/LePhuongTrung/babobi-PRIVACY>, donde su historial es
público.

Esta página está en español. La misma política en inglés es PRIVACY.md en la
raíz. Los demás idiomas de la app están en una carpeta con el código del
idioma.

## Contacto

No hay una cuenta de BabiBo que borrar, porque nosotros no guardamos ninguna.
Eliminar la app elimina el archivo local. Para los datos que un destinatario ya
tiene, usa el camino indicado en la sección de ese destinatario.

Preguntas: <babibo.support@lephuongtrung.id.vn>
