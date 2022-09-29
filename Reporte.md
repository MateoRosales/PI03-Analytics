![HenryLogo](https://d31uz8lwfmyn8g.cloudfront.net/Assets/logo-henry-white-lg.png)

# **DATA SCIENCE - 03**

## **Proyecto Individual 3 - Mateo Rosales - 29/09/2022**

### **Informe**


En el desarrollo del siguiente trabajo se generó un dashboard interactivo con información de diferentes criptomonedas. Para disponer de la información necesaria se utilizó la RestAPI de `FTX`.

Se trabajó directamente con conexión a la API y se seleccionaron 10 criptomonedas consideradas relevantes con su actividad en el corriente año 2022. Posteriormente se creó un informe Dashboard con la herramienta `PowerBI`.

En dicho informe se generó la siguiente información:

* Gráfico de lineas con datos del presente año de las criptomonedas con opción de filtrado por fecha en el que se puede observar el valor de cierre por día (close), el mayor valor diario que tomo la criptomoneda (high) y  el menor valor diario (low). Todo expresado en dólares estounidenses (USD).

* `Media móvil`: valor promedio de los datos tomados desde un determinado punto en el tiempo que constituye una serie de promedios. Puede personalizarse entre 1 y 60 días. Medida en USD.

* Gráfico de barras con el `volumen de transacción` diaria de cada criptomoneda. Esto representa la cantidad de interacciones, compras y ventas, por día de cada criptomoneda expresado en USD. Puede filtrarse por período de tiempo dentro del corriente año.

* `Desviación estándar` de los movimientos de la criptomoneda en el período seleccionado expresada en USD. Representa el equivalente a la raíz cuadrada de la varianza.

* `Calculadora financiera`: conversor entre cualquiera de las criptomonedas presentes en el informe y dólares estadounidenses (USD).

### **Criptomonedas seleccionadas**

* BNB: Binance
* BTC: Bitcoin
* DAI: Dai
* DOGE: DogeCoin
* DOT: Polkadot
* ETH: Ethereum
* MATIC: Polygon
* SHIB: Shiba Inu
* SOL: Solana
* USDT: Tether




### **Manejo de datos**


Para la realización del informe se tomaron datos de la RestAPI de FTX con los siguientes parámetros en el URL:

`https://ftx.com/api//markets/{market_name}/candles?resolution={resolution}&start_time={start_time}`

* market_name: codigo de cada mercado, por ejemplo BTC/USD.
* resolution: 86400, representa un período anual;
* start_time: 1640926800, valor que representa el primer día del corriente año.


Las tablas obtenidas disponían de las siguientes columnas:

* Success: columna que indicaba la conexión satisfactoria, no se tuvo en cuenta;
* ``StartTime``: fecha del período (día); 
* Time: fecha expresada en segundos, dicha columna no se tuvo en consideración;
* Open: valor de inicio del período, no se tuvo en cuenta;
* ``High``: mayor valor en el período;
* ``Low``: menor valor en el período;
* ``Close``: valor de cierre del período;
* ``Volume``: volumen de transacciones en el período.

Se sustrajeron las columna de Time y de Success y se agregó una nueva columna denominada ``Personalizado`` en la que se agregó el código de la criptomoneda a cada fila. De esta manera se anexaron todas las tablas y con un filtro aplicado sobre la columna Personalizado se pudieron discriminar los datos.

Luego, para la relaización de la calculadora financiera se elaboró una ``tabla`` con dos columnas. La primera con los códigos de las criptomonedas y la segunda con los valores tomados del cierre del último período de cada criptomoneda. De esta manera se puede filtrar a través de la primera columna y por medio de un parámetro obtener el resultado según la cantidad de USD que se desee calcular.

Se generó además una ``medida`` para poder calcular la media móvil que depende directamente de un parámetro personalizable en el dashboard. Pudiendo así modificar el período de tiempo a calcular en la media.