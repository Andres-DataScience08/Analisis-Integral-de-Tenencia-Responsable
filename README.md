# Análisis Integral de Tenencia Responsable: Costos, Salud y Factores de Satisfacción en la Adopción de Mascotas

Por: Andrés Felipe Rodríguez Valbuena
Este repositorio contiene el proyecto final de análisis de datos desarrollado en Python. A través de un enfoque de *Data Storytelling*. Se investiga la realidad económica, biológica y conductual de la tenencia doméstica de animales, evaluando qué factores determinan una adopción exitosa y un hogar satisfecho.

---

## Estructura de los Datos

El conjunto de datos original es sintético y cuenta con **15,000 registros** y **36 variables** que capturan información multidimensional sobre la tenencia de mascotas. Tras el proceso de limpieza y depuración metodológica (eliminación selectiva de nulos en variables no imputables e imputación estratégica en variables auxiliares), la muestra final consolidada consta de **13,799 registros**, estructurados en 5 dimensiones principales:

1. **Identificación y Biología:** Especie, raza, clase de tamaño, edad, sexo y peso corporal ($kg$).
2. **Historial de Adopción y Hogar:** Fuente de adopción, fecha, grupo etario del adoptante, zona residencial y tamaño de la vivienda ($m^2$).
3. **Salud y Medicina Preventiva:** Vacunación, esterilización, microchip, seguros médicos y enfermedades crónicas.
4. **Rutina y Cuidados:** Frecuencia de visitas veterinarias, tipo de dieta, minutos de ejercicio diario y horas de sueño.
5. **Economía y Bienestar:** Desglose anual de gastos (comida, veterinaria, peluquería, juguetes, adiestramiento, seguro) y calificación de satisfacción del dueño (escala de 1 a 5).

---

## Diccionario de Variables

| Variable | Tipo de Dato | Unidad / Formato | Descripción |
| :--- | :---: | :---: | :--- |
| `pet_id` | Texto / ID | Alfanumérico | Identificador único del registro de la mascota. |
| `pet_name` | Texto | Categórico | Nombre de la mascota (*imputado como "desconocido" en ausentes*). |
| `species` | Categórico | Nominal | Especie animal (*Dog, Cat, Rabbit, Bird, Fish, Reptile, Small Mammal*). |
| `breed` | Texto | Nominal | Raza específica del animal. |
| `size_class` | Categórico | Ordinal | Tamaño corporal (*Small, Medium, Large, Giant*). |
| `age_years` | Numérico | Años | Edad de la mascota. |
| `gender` | Categórico | Nominal | Sexo del animal (*Male, Female, Unknown*). |
| `weight_kg` | Numérico | Kilogramos ($kg$) | Peso corporal de la mascota. |
| `adoption_source` | Categórico | Nominal | Origen de adopción (*Shelter, Breeder, Pet Store, etc.*). |
| `adoption_date` | Fecha | AAAA-MM-DD | Fecha en que se realizó la adopción. |
| `adoption_year` | Numérico | Año | Año de la adopción. |
| `adoption_month` | Numérico | Mes (1-12) | Mes de la adopción. |
| `owner_age_group` | Categórico | Rango | Grupo de edad del adoptante. |
| `owner_location_type` | Categórico | Nominal | Zona residencial (*Urban, Suburban, Rural*). |
| `household_size` | Numérico | $m^2$ | Tamaño de la vivienda del hogar adoptante. |
| `other_pets_in_household` | Numérico | Entero | Cantidad de otras mascotas presentes en el hogar. |
| `vaccinated` | Booleano | True / False | Estado de vacunación al día. |
| `spayed_neutered` | Booleano | True / False | Indica si el animal está esterilizado o castrado. |
| `microchipped` | Booleano | True / False | Indica si posee microchip de identificación activo. |
| `has_pet_insurance` | Booleano | True / False | Tenencia de póliza de seguro médico veterinario. |
| `chronic_condition` | Booleano | True / False | Diagnóstico de enfermedad o patología médica crónica. |
| `behavior_issues` | Booleano | True / False | Presencia de problemas conductuales reportados por el dueño. |
| `funny_habit` | Texto | Descriptivo | Hábitos o conductas particulares del animal. |
| `vet_visits_per_year` | Numérico | Entero | Frecuencia de visitas anuales al veterinario. |
| `diet_type` | Categórico | Nominal | Tipo de alimentación que consume la mascota. |
| `daily_exercise_minutes`| Numérico | Minutos | Tiempo diario dedicado a actividad física / paseos. |
| `sleep_hours_per_day` | Numérico | Horas | Horas de sueño promedio al día. |
| `training_classes_attended` | Booleano | True / False | Asistencia a clases formales de adiestramiento/entrenamiento. |
| `monthly_food_cost_usd` | Numérico | USD ($) | Gasto mensual en alimentación. |
| `annual_vet_cost_usd` | Numérico | USD ($) | Gasto anual acumulado en servicios veterinarios. |
| `annual_grooming_cost_usd` | Numérico | USD ($) | Gasto anual en peluquería, corte e higiene. |
| `annual_toys_accessories_cost_usd` | Numérico | USD ($) | Inversión anual en juguetes, jaulas, acuarios y accesorios. |
| `annual_training_cost_usd` | Numérico | USD ($) | Costo anual invertido en entrenamiento profesional. |
| `annual_insurance_cost_usd` | Numérico | USD ($) | Prima anual pagada por seguro de salud. |
| `total_annual_cost_usd` | Numérico | USD ($) | Costo anual global acumulado de la mascota. |
| `owner_satisfaction_rating`| Numérico | Escala 1 a 5 | Calificación de satisfacción general reportada por el adoptante. |

---

## Conclusiones Finales del Estudio

### 1. Economía de la Tenencia y Distribución del Gasto (Sección 1)
* **Brecha económica:** Mantener un perro (1,771 USD/año) cuesta el doble que un gato (932 USD/año) y hasta 8 veces más que un pez (223 USD/año), con una alta variabilidad determinada por el tamaño y raza.
* **Gastos fijos vs. Servicios:** La comida y la veterinaria consumen más del 70% del dinero en todos los animales. Los perros y gatos añaden gastos de servicio (adiestramiento, peluquería y seguros), mientras que las especies pequeñas concentran su inversión en accesorios de hábitat y veterinaria exótica.
* **El factor de riesgo médico:** Los outliers demuestran que una enfermedad crónica o cirugía eleva el gasto por encima de los 4,000–6,000 USD en cualquier especie, convirtiendo la salud en el principal riesgo financiero del adoptante.

### 2. Salud y Riesgo Financiero (Sección 2)
* **El seguro médico es el amortiguador financiero contra los gastos extremos:** Mientras que casi el 30% de los dueños de perros y gatos se protege mediante seguros contra los altos costos de enfermedades crónicas o accidentes, los dueños de animales pequeños y exóticos enfrentan una vulnerabilidad financiera total al asumir el costo médico de especialistas sin respaldo asegurado.

### 3. Rutina y Perfil de Cuidados (Sección 3)
* **La adopción responsable trasciende la capacidad económica:** Requiere compatibilidad con la agenda diaria del adoptante. Mientras que adoptar un gato, reptil o pez es compatible con jornadas laborales extensas y/o espacios reducidos, adoptar un perro impone un compromiso no negociable de al menos una hora diaria de actividad física para prevenir problemas de ansiedad y sedentarismo.

### 4. Factores Determinantes de la Satisfacción del Dueño (Sección 4)
* **La convivencia prima sobre el presupuesto:** Un perro de raza cara o una inversión de miles de USD en accesorios no garantizan una convivencia feliz si la mascota es destructiva o agresiva. La estabilidad emocional y la educación del animal son pilares en la satisfacción del adoptante.

### 5. Visión Integral y Correlación de Pearson (Sección 4)
* **Consolidación de la Tenencia Responsable:** El mapa de calor de Pearson consolida la visión integral de la tenencia responsable, es decir, mientras que los costos están gobernados por leyes biológicas objetivas (más peso-más alimento, mayor frecuencia médica-mayor gasto), la satisfacción no depende del poder adquisitivo, demostrando que la felicidad de convivir con una mascota no se compra con presupuesto, sino con educación y compatibilidad mutua.
