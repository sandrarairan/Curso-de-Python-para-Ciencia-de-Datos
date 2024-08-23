Curso en platzi
En este proyecto, utilizaremos el dataset **online_retail.csv** para limpiar, analizar y visualizar datos, con el objetivo de obtener información valiosa para los stakeholders de una empresa.

Paso 1. Instalación y Configuración
Antes de comenzar, asegúrate de tener instalados los paquetes necesarios. Puedes instalarlos utilizando pip:

pip install numpy pandas matplotlib
Paso 2. Cargar los Datos
Importa las librerías necesarias y carga el dataset:

import pandas as pd

# Cargar el dataset
df = pd.read_csv('ruta/al/archivo/online_retail.csv')
Paso 3. Exploración Inicial de los Datos
Explorar los datos es esencial para entender su estructura, identificar patrones y detectar posibles problemas. Esta fase nos ayuda a formular hipótesis y definir el enfoque del análisis.

# Mostrar las primeras filas del dataframe
print(df.head())

# Información general del dataframe
print(df.info())

# Estadísticas descriptivas
print(df.describe())

Paso 4. Limpieza de Datos
La limpieza de datos elimina errores e inconsistencias, asegurando que los análisis sean precisos y confiables. Datos sucios pueden llevar a conclusiones incorrectas y afectar negativamente la toma de decisiones.

Eliminar datos nulos:

# Eliminar filas con valores nulos
df.dropna(inplace=True)
Eliminar duplicados:

# Eliminar filas duplicadas
df.drop_duplicates(inplace=True)
Filtrar datos incorrectos:

# Filtrar registros con cantidades negativas
df = df[df['Quantity'] > 0]
Paso 5. Análisis Exploratorio de Datos (EDA)
El análisis exploratorio o EDA nos permite comprender mejor nuestros datos y descubrir relaciones, patrones o anomalías. Esta etapa es crucial para preparar el terreno para el análisis más profundo y la modelización.

Distribución de las ventas por país:

# Ventas por país
ventas_pais = df['Country'].value_counts()
print(ventas_pais
Productos más vendidos:

# Top 10 productos más vendidos
top_productos = df['Description'].value_counts().head(10)
print(top_productos)
Paso 6. Visualización de Datos
Las visualizaciones son esenciales para comunicar hallazgos de manera clara y efectiva. Facilitan la comprensión de patrones y tendencias que podrían no ser evidentes en una tabla de datos.

Gráfico de barras de ventas por país:

import matplotlib.pyplot as plt

# Gráfico de barras
ventas_pais.plot(kind='bar', figsize=(12, 6))
plt.title('Ventas por País')
plt.xlabel('País')
plt.ylabel('Número de Ventas')
plt.show()
Gráfico de productos más vendidos:

# Gráfico de barras de productos más vendidos
top_productos.plot(kind='bar', figsize=(12, 6))
plt.title('Top 10 Productos Más Vendidos')
plt.xlabel('Producto')
plt.ylabel('Cantidad Vendida')
plt.show()
Paso 7. Generar Informes
Los informes sintetizan el análisis y presentan los hallazgos de manera estructurada. Son fundamentales para comunicar los resultados a los stakeholders y apoyar la toma de decisiones basada en datos.

Resumen del análisis:

# Crear un resumen del análisis
resumen = {
    'Total Ventas': df['Quantity'].sum(),
    'Total Clientes': df['CustomerID'].nunique(),
    'Ventas por País': ventas_pais.to_dict(),
    'Top Productos': top_productos.to_dict()
}

# Guardar el resumen en un archivo
import json
with open('resumen_analisis.json', 'w') as f:
    json.dump(resumen, f, indent=4)

print("Resumen del análisis guardado en 'resumen_analisis.json'")
Paso 8. Creación de Nuevas Columnas e Insights Adicionales
La creación de nuevas columnas nos permite derivar información adicional y realizar análisis más profundos. Podemos generar métricas clave que faciliten la interpretación de los datos y la toma de decisiones.

Calcular el monto total de cada transacción:

# Crear una nueva columna para el monto total de cada transacción
df['TotalAmount'] = df['Quantity'] * df['UnitPrice']
Identificar las fechas con mayor número de ventas:

# Convertir la columna 'InvoiceDate' a formato datetime
df['InvoiceDate'] = pd.to_datetime(df['InvoiceDate'])

# Crear una nueva columna para el día de la semana
df['DayOfWeek'] = df['InvoiceDate'].dt.day_name()

# Ventas por día de la semana
ventas_dia = df['DayOfWeek'].value_counts()
print(ventas_dia)
Calcular las ventas mensuales:

# Crear una nueva columna para el mes
df['Month'] = df['InvoiceDate'].dt.month

# Ventas mensuales
ventas_mensuales = df.groupby('Month')['TotalAmount'].sum()
print(ventas_mensuales)
Visualización de las ventas mensuales:

# Gráfico de líneas de ventas mensuales
ventas_mensuales.plot(kind='line', figsize=(12, 6))
plt.title('Ventas Mensuales')
plt.xlabel('Mes')
plt.ylabel('Monto Total de Ventas')
plt.show()
A lo largo del curso, hemos recorrido los pasos esenciales para limpiar y analizar datos utilizando Python; con el dataset online_retail.csv, aplicamos buenas prácticas de programación y análisis, y generamos información valiosa que puede ser utilizada por los stakeholders para tomar decisiones informadas.
¡Te invito a seguir explorando y aplicando estos conceptos en tus propios proyectos para desarrollar tus habilidades en ciencia de datos!

Para crear un portafolio de Análisis de Datos sigue estas recomendaciones:
A la hora de armar un portafolio de análisis de datos con cualquier dataset, ten en cuenta lo siguiente:

Conoce el área y el objetivo: Antes de comenzar, asegúrate de entender el contexto y los objetivos del análisis. ¿Qué preguntas necesitas responder? ¿Quiénes son los stakeholders?
Explora los datos: Realiza una exploración inicial para familiarizarte con la estructura y el contenido del dataset. Puedes identificar posibles problemas o áreas de interés.
Limpia los datos: La calidad de los datos es crucial. Asegúrate de eliminar valores nulos, duplicados y cualquier dato que no sea válido.
Realiza un análisis exploratorio: Utiliza técnicas de análisis exploratorio para descubrir patrones, tendencias y relaciones en los datos.
Crea nuevas columnas: Deriva nuevas métricas y columnas que puedan aportar valor al análisis.
Visualiza los datos: Utiliza gráficos y visualizaciones para comunicar tus hallazgos de manera efectiva. Asegúrate de que sean claras y fáciles de interpretar.
Genera informes: Documenta tus hallazgos y conclusiones en informes estructurados. Esto facilitará la comunicación con los stakeholders y respaldará tus recomendaciones.
Sé claro y conciso: Utiliza nombres descriptivos para variables y columnas. Asegúrate de que tu código y tus informes sean fáciles de seguir y entender.
Itera y mejora: El análisis de datos es un proceso iterativo. Revisa tus resultados, solicita feedback y mejora continuamente tu trabajo.
