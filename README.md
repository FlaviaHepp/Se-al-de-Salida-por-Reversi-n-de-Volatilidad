# 📉Señal de Salida por Reversión de Volatilidad

## 📌Descripción del Proyecto

Este proyecto identifica señales tempranas de salida (venta) combinando momentum extremo y normalización del riesgo de cola.
La lógica se basa en un fenómeno frecuente en mercados financieros: una tendencia alcista pierde fuerza justo cuando desaparece el riesgo extremo, marcando un posible punto de inflexión.

El enfoque une indicadores técnicos clásicos (RSI) con métricas avanzadas de riesgo (Kurtosis), permitiendo detectar reversiones más limpias y menos ruidosas.

## 🎯Objetivo

Detectar acciones que:
- Estaban fuertemente sobrecompradas (RSI > 75)
- Comienzan a perder momentum (RSI decreciente)
- Presentan una caída significativa del riesgo de cola (Kurtosis < 4.0)

👉 Esta combinación sugiere que el mercado ya absorbió los shocks extremos y que la tendencia previa puede estar agotándose.

## 🧠Insight Clave

Las mejores señales de salida no ocurren en el pico del riesgo, sino cuando el riesgo extremo desaparece.

Cuando la kurtosis cae, el mercado se “normaliza”.
Si esto ocurre al mismo tiempo que el RSI comienza a descender desde niveles extremos, suele anticipar una reversión de tendencia más estable.

## 🛠️Metodología

- Preparación de datos
- Se combinan precios diarios con indicadores técnicos.
- Se calcula el RSI previo usando LAG.
- Condiciones de activación
- RSI del día anterior > 75 (sobrecompra extrema)
- RSI actual < RSI anterior (pérdida de momentum)
- Kurtosis < 4.0 (normalización del riesgo de cola)

## ☑️Resultado

Se genera una alerta explícita de “Reversión de Volatilidad” para cada ticker que cumple las condiciones.

## 📊Output Esperado
ticker_id	fecha	close	rsi_14	kurtosis	señal
AAPL	2024-01-15	182.4	68.2	3.6	Alerta: Reversión de Volatilidad

## 💼Valor de Negocio

- Mejora el timing de salida en estrategias long
- Reduce exposición justo cuando el mercado deja de pagar primas por riesgo
- Complementa sistemas basados solo en RSI o medias móviles

Útil para:
- Trading discrecional avanzado
- Filtros de riesgo en estrategias cuantitativas
- Gestión activa de portafolios

🧩 Requisitos de Datos

- precios_diarios
- ticker_id, fecha, open, close
- indicadores_tecnicos
- rsi_14, kurtosis
- Base de datos compatible con SQL Server / T-SQL (uso de LAG, DATEADD, STDEV).

## 🚀Posibles Extensiones

- Validar rendimiento a 3, 5 y 10 días post-señal
- Filtrar por sector o volatilidad histórica
- Integrar volumen para confirmar distribución institucional
- Combinar con eventos corporativos (earnings, downgrades)

## ⚠️Disclaimer

Este análisis es educativo y exploratorio.
No constituye recomendación de inversión ni asesoramiento financiero.

## 👤Autora
Flavia Hepp Proyecto de SQL aplicó un análisis de riesgo basado en eventos.
***
📊 **No todos los dividendos impactan igual… depende del sector**

Cuando una empresa paga dividendos, el mercado suele ajustar el precio.
Pero ese ajuste no es uniforme.

👉 Analicé el **impacto de eventos de dividendos en el precio de apertura**, midiendo el *gap* respecto al cierre del día anterior.

💡 **Insight clave:**
Hay sectores donde los dividendos generan **gaps más pronunciados**, lo que revela una mayor sensibilidad del mercado a este tipo de evento.

---

📈 **¿Qué medí?**

* Precio de apertura el día del evento
* Precio de cierre del día previo
* Gap porcentual (*Open vs. Close previo*)
* Promedio por sector

---

🧠 **¿Cómo interpretarlo?**

* Mayor gap → mayor ajuste del mercado al dividendo
* Menor gap → evento más “descontado”
* Diferencias sectoriales → distintos perfiles de inversores y expectativas

---

⚡ **¿Por qué importa?**

Porque permite entender:

* Qué sectores son más sensibles a flujos de caja
* Dónde el mercado reacciona de forma más abrupta
* Cómo ajustar estrategias *event-driven* según contexto

---

📌 Pregunta para la comunidad:
¿Consideran el impacto de dividendos al operar… o lo ven como un ajuste puramente técnico?

#QuantFinance #Trading #DataScience #StockMarket #Dividends #Analytics #SQL #Investing
