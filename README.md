## Problema:
La falta de conectividad digital actúa como un multiplicador de brechas territoriales en salud, educación y oportunidades laborales.

Hasta ahora tenemos 5 datasets oficiales descargados desde GEO Perú:
1. GeoPeru-instituciones_educativas.xlsx
2. GeoPeru-instituciones_salud.xlsx
3. GeoPeru-peru_distritos.xlsx
4. GeoPeru-peru_provincias.xlsx
5. GeoPeru-peru_departamentos.xlsx

Estos datasets cubren parcialmente, pero de forma importante, las dimensiones centrales del problema:
```
conectividad + salud + educación + pobreza/NBI + empleo/PEA + territorio
```
*** Aca podemos abarcar tmb a la pobreza y empleo como el efecto de la falta de conectividad***

## 1. Dataset: GeoPeru-instituciones_educativas.xlsx
### Qué cubre
Este dataset cubre la dimensión de educación.

### Nos permite saber:
- Dónde están las instituciones educativas.
- En qué distrito, provincia y departamento están.
- Qué nivel/modalidad educativa tienen.
- A qué UGEL pertenecen.
- Qué tipo de gestión tienen.
- Si son escolarizadas o no escolarizadas.

### Variables importantes:
- cod_dpto
- nom_dpto
- cod_prov
- nom_prov
- cod_dist
- nom_dist
- codmod
- cod_local
- nivmod_cod
- nivmod_val
- form_valor
- gene_valor
- gesdep_val
- turn_valor
- ugel_iduge
- ugel_nouge
- nlatie
- nlongie
- fuente

### Cómo aporta al problema
Este dataset nos ayuda a responder:
> ¿Qué distritos tienen baja conectividad y además concentran instituciones educativas que podrían verse afectadas por esa brecha?

También nos permite construir indicadores como:
- cantidad de instituciones educativas por distrito
- cantidad de instituciones educativas por nivel educativo
- cantidad de instituciones educativas públicas/privadas
- cantidad de instituciones educativas rurales/urbanas si esa variable aparece o se puede derivar

### Estado actual
Este dataset parece estar bastante limpio para una primera fase.
Las columnas educativas revisadas tienen valores controlados y sin nulos relevantes:
- nivmod_cod
- nivmod_val
- form_valor
- gene_valor
- gesdep_val
- turn_valor
- ugel_nouge

## 2. Dataset: GeoPeru-instituciones_salud.xlsx
### Qué cubre
Este dataset cubre dos dimensiones muy importantes:
- salud
- conectividad en establecimientos de salud

Es uno de los datasets más valiosos para nuestro problema.

### Variables importantes de salud
- cod_dpto
- nom_dpto
- cod_prov
- nom_prov
- cod_dist
- nom_dist
- tipo_estab
- clasificac
- est_nombre
- institucio
- est_estado
- est_situac
- cod_ipress
- x_gis
- y_gis
- fuente

### Variables importantes de conectividad
- internet
- tecno
- cant_mb
- vel_baj
- vel_sub
- operador
- p_mes
- conect
- cod_conect

### Cómo aporta al problema
Este dataset nos permite responder:
> ¿Qué establecimientos de salud tienen o no tienen internet?

Y también:
> ¿En qué distritos la baja conectividad puede afectar la capacidad de atención, gestión, telemedicina, citas digitales, reportes o servicios digitales de salud?

Podemos construir indicadores como:
- cantidad de establecimientos de salud por distrito
- cantidad de establecimientos con internet por distrito
- cantidad de establecimientos sin internet por distrito
- porcentaje de establecimientos de salud conectados
- velocidad promedio de bajada
- velocidad promedio de subida
- tipo de tecnología usada
- operador predominante

### Estado actual
Este dataset es muy útil, pero necesita limpieza.
Las columnas más limpias son:
- conect
- tipo_estab
- clasificac

La columna conect es especialmente útil porque tiene solo tres valores:
- Tiene
- No tiene
- Sin información

Pero estas columnas necesitan limpieza fuerte:
- internet
- tecno
- operador

¿Por qué?
Porque mezclan texto libre, tecnologías, errores de escritura y nombres repetidos.

Ejemplo:
- INTERNET POR CABLE
- INTERNET PO CABLE
- CABLE
- CABLE/WIFI
- WIFI
- RADIO ENLACE
- MODEM TECNOLOGIA 4G
- FIBRA
- SATELITAL
- Sin información
- NO

Por eso ya definimos que vamos a crear columnas limpias como:
- conect_clean
- internet_clean
- tecno_clean
- operador_clean

## 3. Dataset: GeoPeru-peru_distritos.xlsx
### Qué cubre
Este es el dataset territorial más importante porque trabaja a nivel de distrito.

Cubre varias dimensiones:
- territorio
- población
- hogares
- vivienda
- pobreza/NBI
- conectividad de hogares
- celular
- internet
- educación básica de la población
- salud/seguro
- PEA y empleo

### Variables territoriales
- cod_dpto
- nom_dpto
- cod_prov
- nom_prov
- cod_dist
- nom_dist

### Variables poblacionales
- pob_total
- total_pers
- num_hog
- num_viv_pa
- num_viv_op

### Variables de pobreza / NBI
- almenosuna
- almenosu_1
- nbi1_abs
- nbi1_porc
- nbi2_abs
- nbi2_porc
- nbi3_abs
- nbi3_porc
- nbi4_abs
- nbi4_porc
- nbi5_abs
- nbi5_porc

### Variables de conectividad
- hs_tcelu
- phs_tcelu
- hs_inter
- phs_inter

### Variables laborales
- pet
- pea
- peao
- pead
- pei
- p_pet
- p_pea
- p_pea_o
- p_pea_d
- p_pei

### Variables educativas/sociales
- p_lees_si
- p_lees_no
- p_af_sis
- p_af_ning
- p_dni
- p_no_docum

### Cómo aporta al problema
Este dataset nos permite construir el corazón del índice.

Nos ayuda a responder:
- ¿Qué distritos tienen menor conectividad?
- ¿Qué distritos tienen más pobreza o necesidades básicas insatisfechas?
- ¿Qué distritos tienen menor acceso a celular o internet?
- ¿Qué distritos tienen mayor población vulnerable?
- ¿Qué distritos tienen menor participación económica o más desempleo?

### Estado actual
Este dataset parece muy útil y bastante limpio numéricamente, pero hay una alerta importante:

Todavía debemos confirmar el significado exacto de:
- phs_inter
- phs_tcelu
- hs_inter
- hs_tcelu

Porque phs_inter muestra valores muy altos, como 96%, 99% o 100%. Eso podría significar varias cosas, por ejemplo:
- porcentaje de hogares con internet
- porcentaje de hogares sin internet
- porcentaje relacionado a otra base
- variable invertida

Entonces, no debemos reportarlo todavía como “% de hogares con internet” hasta validarlo.

Lo correcto para el reporte sería decir:
> El dataset distrital incluye variables asociadas a internet y telefonía celular en hogares, pero se encuentra pendiente validar el significado exacto de dichas columnas mediante diccionario de datos o cálculo comparativo con variables absolutas.

## 4. Dataset: GeoPeru-peru_provincias.xlsx
### Qué cubre
Este dataset cubre casi las mismas variables que el dataset distrital, pero agregadas a nivel de provincia.

Incluye:
- población
- hogares
- viviendas
- NBI
- internet
- celular
- PEA
- educación básica
- salud/seguro
- documentación
- grupos etarios

### Cómo aporta al problema
Sirve para hacer análisis agregado por provincia.
Pero su uso principal ahora será de validación.
Nos permite comprobar si al sumar los distritos obtenemos los mismos totales provinciales.

Ejemplo:
> sumatoria de pob_total distrital por provincia
> vs
> pob_total oficial provincial

### Estado actual
No será nuestra base principal.

La usaremos para:
- validar agregaciones
- crear mapas/resúmenes provinciales
- presentar resultados más fáciles de comunicar

## 5. Dataset: GeoPeru-peru_departamentos.xlsx
### Qué cubre
Este dataset cubre las mismas variables principales, pero a nivel de departamento.

Incluye:
- población
- hogares
- viviendas
- NBI
- internet
- celular
- PEA
- educación básica
- salud/seguro
- documentación
- grupos etarios

### Cómo aporta al problema
Sirve para una vista macro nacional.

Nos permite responder:
- ¿Qué departamentos concentran mayor vulnerabilidad digital?
- ¿Qué departamentos tienen mayores brechas sociales asociadas?

Pero no debe ser la base principal porque el nivel departamental es demasiado general.

### Estado actual
Lo usaremos para:
- validación
- resúmenes nacionales
- ranking departamental
- visualización ejecutiva

## Presupuesto Ejecutado
Porta de busqueda por municipalidades
https://apps5.mineco.gob.pe/transparencia/Navegador/default.aspx?y=2026&ap=ActProy

## Dimensiones cubiertas del problema
| Dimensión del problema                                           |                         ¿Tenemos data? | Dataset fuente                                         | Estado                      |
| ---------------------------------------------------------------- | -------------------------------------: | ------------------------------------------------------ | --------------------------- |
| Territorio / ubigeo                                              |                                     Sí | distritos, provincias, departamentos, salud, educación | Cubierto                    |
| Conectividad de hogares                                          | Sí, pero pendiente validar significado | peru_distritos                                         | Parcialmente cubierto       |
| Conectividad en salud                                            |                                     Sí | instituciones_salud                                    | Cubierto, requiere limpieza |
| Salud                                                            |                                     Sí | instituciones_salud                                    | Cubierto                    |
| Educación                                                        |                                     Sí | instituciones_educativas                               | Cubierto                    |
| Pobreza / NBI                                                    |                                     Sí | peru_distritos                                         | Cubierto                    |
| Población / hogares                                              |                                     Sí | peru_distritos                                         | Cubierto                    |
| Trabajo / PEA                                                    |                                     Sí | peru_distritos                                         | Cubierto básico             |
| Capacitación laboral                                             |                          No confirmado | falta buscar                                           | Pendiente                   |
| Infraestructura digital externa: antenas, fibra, cobertura móvil |                          No confirmado | falta buscar                                           | Pendiente                   |
| Límites geográficos para mapas                                   |                                Parcial | depende si tenemos geometría o solo tablas             | Pendiente                   |

## Conclusion de lo quetenemos hasta ahora
> 5 datasets oficiales desde GEO Perú: instituciones educativas, instituciones de salud, indicadores distritales, indicadores provinciales e indicadores departamentales.

> Estos datasets permiten cubrir una primera base de análisis para el problema de conectividad como multiplicador de brechas, ya que contienen información territorial por ubigeo, variables de conectividad en hogares, conectividad en establecimientos de salud, oferta educativa, oferta sanitaria, pobreza/NBI, población, hogares y variables laborales básicas como PEA.

> El dataset distrital será usado como base principal del análisis, debido a que permite observar brechas a mayor nivel de detalle territorial. Los datasets provinciales y departamentales se usarán como fuentes de validación y agregación para reportes ejecutivos.

> La información de instituciones de salud es especialmente relevante porque incluye variables de conectividad como internet, tecnología, velocidad, operador y estado de conexión. Sin embargo, algunas columnas requieren limpieza porque contienen valores escritos de forma no estandarizada.

> La información de instituciones educativas se encuentra en mejor estado para una primera fase, ya que sus variables principales de nivel/modalidad, gestión, turno y UGEL presentan categorías controladas.

### Siguientes pasos:
- Validar el significado exacto de las variables de conectividad del dataset distrital y se limpiarán las columnas de conectividad del dataset de salud.
- Construir una matriz de cobertura para identificar si aún falta incorporar capas adicionales, especialmente infraestructura digital como fibra óptica, antenas, cobertura móvil o centros de capacitación laboral.

## Qué nos falta:
Hasta ahora tenemos una base inicial sólida para una primera versión del análisis. PEro un esta pendiente:

### 1. Diccionario de datos
Para saber exactamente qué significan:
- phs_inter
- hs_inter
- phs_tcelu
- hs_tcelu
- almenosuna
- almenosu_1

### 2. Infraestructura digital real
Sería ideal encontrar datos de:
- fibra óptica
- antenas
- cobertura móvil
- banda ancha
- centros poblados conectados
- proyectos PRONATEL / MTC

Esto reforzaría mucho la propuesta.

### 3. Capacitación laboral
Todavía no tenemos una capa clara de:
- centros de capacitación
- programas laborales
- centros de empleo
- CETPRO vinculados a capacitación laboral

Aunque parte de esto puede aproximarse con educación técnico-productiva en instituciones_educativas.

### 4. Geometrías para mapas
Los Excel tienen códigos territoriales y algunas coordenadas, pero necesitamos confirmar si tenemos geometría completa de distritos/provincias/departamentos.

Para hacer mapas buenos, necesitamos límites territoriales en formato:

- GeoJSON
- SHP
- GeoPackage

