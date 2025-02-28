# SchoolConnectAI
This project would combine school location data with geospatial information to create a connectivity visualization and planning tool for schools in remote areas.

Analizando los recursos disponibles para el hackathon, veo varias opciones que serían adecuadas para principiantes. Te recomendaría enfocarte en la **Pista 2: Diseño de Red y Planificación Estratégica** con un proyecto que aproveche los recursos más accesibles y user-friendly.

# Proyecto Recomendado para Principiantes: "SchoolConnectAI"

Este proyecto combinaría datos de ubicación de escuelas con información geoespacial para crear una herramienta de visualización y planificación de conectividad para escuelas en zonas remotas.

## Recursos Clave (User-Friendly)

1. **Giga School Location Data**: Datos de geolocalización de escuelas que están bien estructurados y accesibles a través de una API
   - Enlace: https://maps.giga.global/docs/explore-api
   - Ideal para principiantes porque tiene documentación y formato estructurado

2. **OpenStreetMap**: Datos geoespaciales de fácil acceso que no requieren conocimientos técnicos avanzados
   - Enlace: https://www.openstreetmap.org/#map=6/40.00/-2.48
   - Plataforma visual intuitiva con muchas herramientas de soporte

4. **Ookla Speedtest**: Datos de rendimiento de internet que son sencillos de entender y visualizar
   - Enlace: https://registry.opendata.aws/speedtest-global-performance/
   - Formato estandarizado que facilita la integración

## Herramientas Recomendadas para Principiantes



# Herramientas Recomendadas para Principiantes

## Plataformas de Desarrollo

### 1. Streamlit
- **¿Por qué es amigable?** Permite crear aplicaciones web interactivas con Python puro, sin necesidad de conocimientos de HTML/CSS/JavaScript
- **Uso en el proyecto:** Desarrollar un dashboard interactivo para visualizar datos de conectividad de escuelas
- **Curva de aprendizaje:** Muy baja (si ya conoces Python básico)
- **Ejemplo de código básico:**
```python
import streamlit as st
import pandas as pd
import plotly.express as px

st.title('SchoolConnectAI - Análisis de Conectividad')

# Cargar datos (ejemplo)
df = pd.read_csv('datos_escuelas.csv')

# Filtros interactivos
pais = st.selectbox('Selecciona un país:', df['pais'].unique())
datos_filtrados = df[df['pais'] == pais]

# Visualización 
fig = px.scatter_mapbox(datos_filtrados, 
                        lat="latitud", lon="longitud", 
                        color="velocidad_internet",
                        hover_name="nombre_escuela",
                        zoom=5)
fig.update_layout(mapbox_style="open-street-map")
st.plotly_chart(fig)
```

### 2. Folium
- **¿Por qué es amigable?** Biblioteca Python para crear mapas interactivos con una API sencilla
- **Uso en el proyecto:** Visualizar la ubicación de escuelas y la cobertura de red en diferentes regiones
- **Curva de aprendizaje:** Baja (requiere conocimientos básicos de Python)

## Herramientas de Procesamiento de Datos

### 1. Pandas
- **¿Por qué es amigable?** API intuitiva para manipulación de datos tabulares
- **Uso en el proyecto:** Procesar y limpiar datos de escuelas y conectividad
- **Curva de aprendizaje:** Media (conceptos básicos son fáciles de aprender)

### 2. GeoPandas
- **¿Por qué es amigable?** Extensión de Pandas para trabajar con datos geoespaciales
- **Uso en el proyecto:** Análisis espacial de ubicaciones de escuelas
- **Curva de aprendizaje:** Media (si ya conoces Pandas)

## Visualización

### 1. Plotly Express
- **¿Por qué es amigable?** Crea gráficos interactivos con pocas líneas de código
- **Uso en el proyecto:** Visualizar métricas de conectividad y costos
- **Curva de aprendizaje:** Baja

### 2. Matplotlib
- **¿Por qué es amigable?** Biblioteca estándar para visualización en Python
- **Uso en el proyecto:** Gráficos estáticos para el análisis de datos
- **Curva de aprendizaje:** Media


## Plan de Proyecto en 3 Días

**Viernes:**
1. **Configuración** (2-3 horas)
   - Instalar Python y las bibliotecas necesarias (Streamlit, Pandas, Folium)
   - Configurar un repositorio GitHub

2. **Recopilación de datos** (3-4 horas)
   - Descargar datos de ubicación de escuelas de Giga
   - Obtener datos de OpenStreetMap para una región específica
   - Conseguir datos de velocidad de internet de Ookla (si están disponibles)

**Sábado:**
1. **Procesamiento de datos** (4-5 horas)
   - Limpiar y estructurar los datos recopilados
   - Crear un dataset combinado con información de escuelas y conectividad

2. **Desarrollo de funcionalidades básicas** (5-6 horas)
   - Crear un mapa interactivo que muestre ubicaciones de escuelas
   - Implementar filtros básicos por región/país
   - Añadir indicadores de conectividad actual

**Domingo:**
1. **Implementación de funcionalidades avanzadas** (3-4 horas)
   - Añadir recomendaciones simples para mejorar la conectividad
   - Implementar cálculos básicos de costos

2. **Desarrollo de la interfaz** (2-3 horas)
   - Mejorar la interfaz de usuario con Streamlit
   - Añadir elementos interactivos

3. **Finalización y presentación** (3-4 horas)
   - Preparar la presentación
   - Hacer una demostración en vivo
   - Envío final del proyecto

## Estructura del Proyecto

```text
schoolconnectai/
│
├── app/                      # Aplicación principal
│   ├── app.py                # Punto de entrada de Streamlit
│   ├── pages/                # Páginas adicionales de la aplicación
│   │   ├── dashboard.py      # Dashboard principal
│   │   ├── analysis.py       # Análisis detallado
│   │   └── recommendations.py # Recomendaciones de conectividad
│   └── utils/                # Utilidades
│       ├── data_loader.py    # Funciones para cargar datos
│       ├── visualization.py  # Funciones de visualización
│       └── analysis.py       # Funciones de análisis
│
├── data/                     # Datos
│   ├── raw/                  # Datos sin procesar
│   └── processed/            # Datos procesados
│
├── notebooks/                # Jupyter notebooks para exploración
│   ├── data_exploration.ipynb
│   └── model_testing.ipynb
│
├── tests/                    # Pruebas unitarias
│
├── README.md                 # Documentación principal
├── requirements.txt          # Dependencias
└── setup.py                  # Configuración del paquete

```

## Código Básico para Comenzar

```python
# app.py - Archivo principal de la aplicación

import streamlit as st
import pandas as pd
import folium
from streamlit_folium import folium_static
import plotly.express as px
import requests
import json

# Configuración de la página
st.set_page_config(
    page_title="SchoolConnectAI",
    page_icon="🏫",
    layout="wide"
)

# Título y descripción
st.title("SchoolConnectAI: Conectando Escuelas en Áreas Remotas")
st.markdown("""
Esta herramienta ayuda a optimizar la conectividad de las escuelas en regiones desatendidas
mediante el análisis de datos geoespaciales y recomendaciones basadas en IA.
""")

# Función para cargar datos de escuelas (simulado para el hackathon)
@st.cache_data  # Caché para mejorar rendimiento
def load_sample_data():
    # En un proyecto real, aquí cargarías datos de la API de Giga
    # Para el hackathon, usamos datos de ejemplo
    data = {
        "school_id": range(1, 101),
        "name": [f"Escuela {i}" for i in range(1, 101)],
        "latitude": [41.3851 + (i/500) for i in range(1, 101)],  # Barcelona como centro
        "longitude": [2.1734 + (i/500) for i in range(1, 101)],
        "has_internet": [i % 3 != 0 for i in range(1, 101)],  # 2/3 tienen internet
        "internet_speed": [0 if i % 3 == 0 else (5 + i % 20) for i in range(1, 101)],
        "students": [100 + i * 10 for i in range(1, 101)],
        "region": [f"Región {(i % 5) + 1}" for i in range(1, 101)]
    }
    return pd.DataFrame(data)

# Cargar datos
schools_df = load_sample_data()

# Barra lateral con filtros
st.sidebar.header("Filtros")
selected_region = st.sidebar.multiselect(
    "Selecciona Región(es):",
    options=schools_df["region"].unique(),
    default=schools_df["region"].unique()[0]
)

# Filtrar datos según selección
filtered_df = schools_df[schools_df["region"].isin(selected_region)]

# Mostrar estadísticas básicas
st.header("Estadísticas de Conectividad")
col1, col2, col3 = st.columns(3)

with col1:
    total_schools = len(filtered_df)
    st.metric("Total de Escuelas", total_schools)

with col2:
    connected = filtered_df["has_internet"].sum()
    st.metric("Escuelas Conectadas", f"{connected} ({int(connected/total_schools*100)}%)")

with col3:
    avg_speed = filtered_df[filtered_df["internet_speed"] > 0]["internet_speed"].mean()
    st.metric("Velocidad Media (Mbps)", f"{avg_speed:.1f}")

# Crear mapa interactivo
st.header("Mapa de Escuelas")

# Crear mapa base centrado en la media de las coordenadas
map_center = [filtered_df["latitude"].mean(), filtered_df["longitude"].mean()]
m = folium.Map(location=map_center, zoom_start=10)

# Añadir marcadores para cada escuela
for _, row in filtered_df.iterrows():
    # Color basado en si tiene internet
    color = "green" if row["has_internet"] else "red"
    # Popup con información
    popup_text = f"""
    <b>{row['name']}</b><br>
    Estudiantes: {row['students']}<br>
    Internet: {'Sí' if row['has_internet'] else 'No'}<br>
    Velocidad: {row['internet_speed']} Mbps
    """
    # Añadir marcador
    folium.Marker(
        location=[row["latitude"], row["longitude"]],
        popup=folium.Popup(popup_text, max_width=300),
        icon=folium.Icon(color=color)
    ).add_to(m)

# Mostrar mapa en Streamlit
folium_static(m, width=1000)

# Visualizaciones adicionales
st.header("Análisis de Conectividad")

col1, col2 = st.columns(2)

with col1:
    # Gráfico de barras por región
    fig1 = px.bar(
        filtered_df.groupby("region").agg(
            escuelas_total=("school_id", "count"),
            escuelas_conectadas=("has_internet", "sum")
        ).reset_index(),
        x="region",
        y=["escuelas_total", "escuelas_conectadas"],
        title="Conectividad por Región",
        labels={"value": "Número de Escuelas", "region": "Región", "variable": "Tipo"}
    )
    st.plotly_chart(fig1, use_container_width=True)

with col2:
    # Histograma de velocidades
    fig2 = px.histogram(
        filtered_df[filtered_df["internet_speed"] > 0],
        x="internet_speed",
        nbins=20,
        title="Distribución de Velocidades de Internet",
        labels={"internet_speed": "Velocidad (Mbps)", "count": "Número de Escuelas"}
    )
    st.plotly_chart(fig2, use_container_width=True)

# Sección de recomendaciones
st.header("Recomendaciones de Conectividad")

# Simulación simple de recomendaciones
st.subheader("Escuelas Prioritarias para Conectividad")
priority_schools = filtered_df[
    (filtered_df["has_internet"] == False) & 
    (filtered_df["students"] > 150)
].sort_values(by="students", ascending=False).head(5)

if not priority_schools.empty:
    st.dataframe(
        priority_schools[["name", "region", "students"]],
        use_container_width=True
    )
    
    # Visualizar escuelas prioritarias en el mapa
    st.subheader("Ubicación de Escuelas Prioritarias")
    priority_map = folium.Map(location=map_center, zoom_start=10)
    
    for _, row in priority_schools.iterrows():
        folium.Marker(
            location=[row["latitude"], row["longitude"]],
            popup=row["name"],
            icon=folium.Icon(color="purple", icon="star")
        ).add_to(priority_map)
    
    folium_static(priority_map, width=1000)
else:
    st.write("No hay escuelas prioritarias en las regiones seleccionadas.")

# Notas finales
st.markdown("---")
st.markdown("""
### Próximos pasos recomendados:
1. Integrar datos reales de la API de Giga
2. Mejorar los algoritmos de recomendación con técnicas de IA
3. Añadir estimaciones de costos para diferentes soluciones de conectividad
""")

# Footer
st.markdown("---")
st.markdown("Desarrollado para el AI for Connectivity Hackathon II | 2025")

```

## Consejos para Principiantes

1. **Comienza con el MVP (Producto Mínimo Viable)**: Enfócate primero en crear una versión básica pero funcional que muestre las ubicaciones de las escuelas y su estado de conectividad.

2. **Utiliza herramientas visuales**: Streamlit y Folium son extremadamente amigables para principiantes y te permiten crear visualizaciones impresionantes con poco código.

3. **Aprovecha los datos de muestra**: Si tienes problemas para acceder a las APIs, crea datos de muestra que representen el problema que estás intentando resolver.

4. **Colabora y pide ayuda**: Aprovecha la presencia de mentores en el hackathon y no dudes en pedir orientación.

5. **Enfócate en la presentación**: A veces, una buena presentación y demostración pueden compensar las limitaciones técnicas del proyecto.

Esta propuesta es perfecta para principiantes porque:
- Utiliza herramientas Python de alto nivel con poca configuración
- Se basa en datos estructurados y bien documentados
- Puede comenzar con visualizaciones básicas y luego añadir complejidad
- Produce un resultado visualmente impactante con relativamente poco código

¿Te gustaría que profundice en algún aspecto específico de esta propuesta?
