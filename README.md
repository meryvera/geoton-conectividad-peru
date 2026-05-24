# Primera etapa de análisis GEOTÓN Perú 2026
Índice Territorial de Vulnerabilidad Digital Compuesta
## 0. Contexto del proyecto

Estamos participando en la GEOTÓN Perú 2026, concurso orientado al uso de datos georreferenciados de GEO Perú para analizar problemáticas territoriales y proponer soluciones innovadoras con valor público. Las bases indican que la propuesta debe identificar un problema territorial concreto, usar al menos un conjunto de datos de GEO Perú, realizar análisis territorial, presentar hallazgos y proponer una solución o mejora coherente con los datos utilizados. También se exige un anexo visual obligatorio, como mapa, gráfico, tablero, lámina o prototipo.

#### La categoría elegida es:

### Territorio Conectado

#### El problema que estamos abordando es:

La falta de conectividad digital no es solo una brecha aislada. Es un cuello de botella que amplifica otras brechas territoriales, especialmente en salud, educación y capacitación laboral.

#### La hipótesis central es:

Los distritos con mayor brecha digital, mayor vulnerabilidad social, menor conectividad en salud, mayor ruralidad educativa y fragilidad laboral requieren priorización territorial para intervenciones públicas de conectividad digital.

## 1. Datasets utilizados

Hasta esta primera etapa se están utilizando 5 datasets oficiales descargados desde GEO Perú:

1. GeoPeru-peru_distritos.xlsx
2. GeoPeru-peru_provincias.xlsx
3. GeoPeru-peru_departamentos.xlsx
4. GeoPeru-instituciones_educativas.xlsx
5. GeoPeru-instituciones_salud.xlsx

El análisis principal se está construyendo a nivel distrital, porque el distrito permite identificar brechas territoriales con mayor precisión que el departamento o la provincia.

## 2. Dataset: GeoPeru-peru_distritos.xlsx
### 2.1. Rol del dataset

Este es el dataset principal del análisis.

Contiene información territorial, social, demográfica, de vivienda, servicios básicos, brecha digital, salud, educación básica y empleo a nivel de distrito.

Es la base sobre la cual se construye el Índice Territorial de Vulnerabilidad Digital Compuesta.

### 2.2. Cobertura
- Nivel territorial: distrito
- Total aproximado: 1,874 distritos
- Fuente base: INEI, Censos Nacionales 2017

### 2.3. Variables importantes para el análisis
| Variable     | Significado                                                        | Uso en el análisis                                 |
| ------------ | ------------------------------------------------------------------ | -------------------------------------------------- |
| `cod_dpto`   | Código de departamento                                             | Identificación territorial                         |
| `nom_dpto`   | Nombre del departamento                                            | Agrupación departamental                           |
| `cod_prov`   | Código de provincia                                                | Identificación territorial                         |
| `nom_prov`   | Nombre de provincia                                                | Agrupación provincial                              |
| `cod_dist`   | Código de distrito / ubigeo distrital                              | Llave principal para cruces                        |
| `nom_dist`   | Nombre del distrito                                                | Identificación del territorio                      |
| `total_pers` | Total de personas                                                  | Medición de población expuesta                     |
| `num_hog`    | Número de hogares                                                  | Base para interpretar brechas en hogares           |
| `almenosuna` | Cantidad de población/hogares con al menos una NBI                 | Vulnerabilidad estructural                         |
| `almenosu_1` | Porcentaje con al menos una NBI                                    | Variable principal de vulnerabilidad social        |
| `nbi1_abs`   | Valor absoluto de NBI 1                                            | Análisis complementario                            |
| `nbi1_porc`  | Porcentaje asociado a NBI 1                                        | Vulnerabilidad social                              |
| `nbi2_abs`   | Valor absoluto de NBI 2                                            | Análisis complementario                            |
| `nbi2_porc`  | Porcentaje asociado a NBI 2                                        | Vulnerabilidad social                              |
| `nbi3_abs`   | Valor absoluto de NBI 3                                            | Análisis complementario                            |
| `nbi3_porc`  | Porcentaje asociado a NBI 3                                        | Vulnerabilidad social                              |
| `nbi4_abs`   | Valor absoluto de NBI 4                                            | Análisis complementario                            |
| `nbi4_porc`  | Porcentaje asociado a NBI 4                                        | Vulnerabilidad social                              |
| `nbi5_abs`   | Valor absoluto de NBI 5                                            | Análisis complementario                            |
| `nbi5_porc`  | Porcentaje asociado a NBI 5                                        | Vulnerabilidad social                              |
| `vs_agua_rp` | Viviendas sin acceso adecuado a agua por red pública               | Carencia básica                                    |
| `pvs_agua_r` | Porcentaje de viviendas sin acceso adecuado a agua por red pública | Score social                                       |
| `vs_sh`      | Viviendas sin servicio higiénico adecuado                          | Carencia básica                                    |
| `pvs_sh`     | Porcentaje de viviendas sin servicio higiénico adecuado            | Score social                                       |
| `vs_aelec`   | Viviendas sin alumbrado eléctrico                                  | Carencia básica crítica para uso de tecnología     |
| `pvs_aelec`  | Porcentaje de viviendas sin alumbrado eléctrico                    | Score social                                       |
| `hs_pclptb`  | Hogares SIN PC/laptop/tablet                                       | Brecha de equipamiento digital                     |
| `phs_pclptb` | Porcentaje de hogares SIN PC/laptop/tablet                         | Score digital                                      |
| `hs_tcelu`   | Hogares SIN teléfono celular                                       | Brecha de acceso móvil                             |
| `phs_tcelu`  | Porcentaje de hogares SIN teléfono celular                         | Score digital                                      |
| `hs_inter`   | Hogares SIN internet                                               | Brecha digital principal                           |
| `phs_inter`  | Porcentaje de hogares SIN internet                                 | Score digital                                      |
| `pet`        | Población en edad de trabajar                                      | Contexto laboral                                   |
| `pea`        | Población económicamente activa                                    | Contexto laboral                                   |
| `peao`       | PEA ocupada                                                        | Contexto laboral                                   |
| `pead`       | PEA desocupada                                                     | Fragilidad laboral                                 |
| `p_pea_d`    | Porcentaje de PEA desocupada                                       | Score laboral                                      |
| `pei`        | Población económicamente inactiva                                  | Fragilidad laboral                                 |
| `p_pei`      | Porcentaje de población económicamente inactiva                    | Score laboral                                      |
| `p_ge_15a29` | Porcentaje de población de 15 a 29 años                            | Potencial grupo objetivo para capacitación digital |
| `p_af_sis`   | Porcentaje afiliado al SIS                                         | Contexto de vulnerabilidad sanitaria               |
| `p_af_ning`  | Porcentaje sin afiliación a seguro de salud                        | Vulnerabilidad sanitaria                           |
| `p_lees_no`  | Porcentaje de población que no sabe leer                           | Brecha educativa básica                            |


### 2.4. Corrección importante sobre variables digitales

Una corrección metodológica clave del proyecto es que las variables:

- hs_tcelu
- phs_tcelu
- hs_inter
- phs_inter
- hs_pclptb
- phs_pclptb

no significan hogares con acceso, sino hogares sin acceso.

Por tanto:
| Variable     | Interpretación correcta                    |
| ------------ | ------------------------------------------ |
| `hs_tcelu`   | Hogares SIN teléfono celular               |
| `phs_tcelu`  | Porcentaje de hogares SIN teléfono celular |
| `hs_inter`   | Hogares SIN internet                       |
| `phs_inter`  | Porcentaje de hogares SIN internet         |
| `hs_pclptb`  | Hogares SIN PC/laptop/tablet               |
| `phs_pclptb` | Porcentaje de hogares SIN PC/laptop/tablet |


Esto es muy importante porque en el índice:

> Mientras mayor sea phs_inter, phs_tcelu o phs_pclptb, mayor es la vulnerabilidad digital.

No se debe invertir la variable.

### 2.5. Insights importantes del dataset distrital

Este dataset permite demostrar que la brecha digital no está aislada. Puede cruzarse con:

- pobreza estructural;
- falta de servicios básicos;
- falta de electricidad;
- población joven;
- empleo/desempleo;
- acceso a salud;
- territorios rurales y dispersos.

El dataset distrital es suficiente para construir una primera versión del índice, porque contiene variables directas de hogares sin internet, sin celular y sin dispositivos digitales.

## 3. Dataset: GeoPeru-peru_provincias.xlsx
### 3.1. Rol del dataset

Este dataset permite analizar el problema a nivel provincial.

No es el nivel principal del índice, pero sirve para resumir, comparar y comunicar hallazgos entre provincias.

### 3.2. Cobertura
- Nivel territorial: provincia
- Total aproximado: 196 provincias
- Fuente base: INEI, Censos Nacionales 2017

### 3.3. Variables importantes
| Variable     | Significado                                     | Uso en el análisis               |
| ------------ | ----------------------------------------------- | -------------------------------- |
| `cod_dpto`   | Código del departamento                         | Agrupación territorial           |
| `nom_dpto`   | Nombre del departamento                         | Agrupación departamental         |
| `cod_prov`   | Código de provincia                             | Llave provincial                 |
| `nom_prov`   | Nombre de provincia                             | Identificación                   |
| `num_dist`   | Número de distritos dentro de la provincia      | Contexto territorial             |
| `sup_tot`    | Superficie territorial                          | Contexto de dispersión           |
| `pob_total`  | Población total                                 | Población expuesta               |
| `num_hog`    | Número de hogares                               | Contexto de hogares              |
| `almenosu_1` | Porcentaje con al menos una NBI                 | Vulnerabilidad social provincial |
| `phs_tcelu`  | Porcentaje de hogares SIN celular               | Brecha digital                   |
| `phs_inter`  | Porcentaje de hogares SIN internet              | Brecha digital principal         |
| `phs_pclptb` | Porcentaje de hogares SIN PC/laptop/tablet      | Brecha de equipamiento           |
| `p_pea_d`    | Porcentaje de PEA desocupada                    | Fragilidad laboral               |
| `p_pei`      | Porcentaje de población económicamente inactiva | Fragilidad laboral               |
| `p_af_sis`   | Porcentaje afiliado al SIS                      | Vulnerabilidad sanitaria         |
| `p_af_ning`  | Porcentaje sin seguro de salud                  | Vulnerabilidad sanitaria         |


### 3.4. Insight importante

El nivel provincial sirve para una visualización intermedia:

> ¿Qué provincias concentran distritos con alta vulnerabilidad digital compuesta?

Sin embargo, no se recomienda construir el índice principal a nivel provincial porque podría ocultar diferencias internas importantes entre distritos.

## 4. Dataset: GeoPeru-peru_departamentos.xlsx
### 4.1. Rol del dataset

Este dataset permite una lectura macro nacional.

Sirve para comparar departamentos y comunicar hallazgos generales.

### 4.2. Cobertura
- Nivel territorial: departamento
- Total: 25 departamentos
- Fuente base: INEI, Censos Nacionales 2017

### 4.3. Variables importantes
| Variable     | Significado                                     | Uso en el análisis       |
| ------------ | ----------------------------------------------- | ------------------------ |
| `cod_dpto`   | Código de departamento                          | Llave departamental      |
| `nom_dpto`   | Nombre del departamento                         | Identificación           |
| `num_prov`   | Número de provincias                            | Contexto territorial     |
| `num_dist`   | Número de distritos                             | Contexto territorial     |
| `sup_tot`    | Superficie territorial                          | Contexto de dispersión   |
| `pob_total`  | Población total                                 | Población expuesta       |
| `num_hog`    | Número de hogares                               | Contexto de hogares      |
| `almenosu_1` | Porcentaje con al menos una NBI                 | Vulnerabilidad social    |
| `phs_tcelu`  | Porcentaje de hogares SIN celular               | Brecha digital           |
| `phs_inter`  | Porcentaje de hogares SIN internet              | Brecha digital principal |
| `phs_pclptb` | Porcentaje de hogares SIN PC/laptop/tablet      | Brecha de equipamiento   |
| `p_pea_d`    | Porcentaje de PEA desocupada                    | Fragilidad laboral       |
| `p_pei`      | Porcentaje de población económicamente inactiva | Fragilidad laboral       |
| `p_af_sis`   | Porcentaje afiliado al SIS                      | Vulnerabilidad sanitaria |


### 4.4. Insight importante

El nivel departamental es útil para el dashboard porque permite responder:

> ¿Qué departamentos tienen mayor vulnerabilidad digital compuesta promedio?

En esta etapa, los departamentos con mayor vulnerabilidad suelen concentrarse en zonas amazónicas, altoandinas y rurales.

## 5. Dataset: GeoPeru-instituciones_salud.xlsx
### 5.1. Rol del dataset

Este dataset permite medir la conectividad de los establecimientos de salud.

Es clave para la hipótesis del proyecto, porque muestra que la brecha digital no solo afecta a los hogares, sino también a la capacidad operativa de los servicios públicos de salud.

### 5.2. Cobertura
- Nivel: establecimiento de salud
- Total aproximado: 9,254 establecimientos
- Cobertura distrital observada en el cruce: 1,861 distritos
- Hay 13 ubigeos del dataset distrital que no tienen registro en el dataset de salud

### 5.3. Variables importantes
| Variable     | Significado                                                | Uso en el análisis               |
| ------------ | ---------------------------------------------------------- | -------------------------------- |
| `cod_dpto`   | Código de departamento                                     | Cruce territorial                |
| `nom_dpto`   | Nombre del departamento                                    | Agrupación                       |
| `cod_prov`   | Código de provincia                                        | Cruce territorial                |
| `nom_prov`   | Nombre de provincia                                        | Agrupación                       |
| `cod_dist`   | Código de distrito                                         | Llave para cruzar con distritos  |
| `nom_dist`   | Nombre del distrito                                        | Identificación                   |
| `est_ubigeo` | Ubigeo del establecimiento                                 | Validación territorial           |
| `tipo_estab` | Tipo de establecimiento                                    | Clasificación del servicio       |
| `clasificac` | Clasificación del establecimiento                          | Análisis de oferta sanitaria     |
| `ctg_codigo` | Categoría del establecimiento                              | Nivel/categoría del servicio     |
| `est_nombre` | Nombre del establecimiento                                 | Identificación                   |
| `institucio` | Institución responsable                                    | Contexto institucional           |
| `est_direcc` | Dirección                                                  | Ubicación                        |
| `x_gis`      | Coordenada X / longitud                                    | Georreferenciación               |
| `y_gis`      | Coordenada Y / latitud                                     | Georreferenciación               |
| `est_estado` | Estado del establecimiento                                 | Control de vigencia              |
| `est_situac` | Situación del establecimiento                              | Control de calidad               |
| `est_condic` | Condición del establecimiento                              | Control de calidad               |
| `tecno`      | Tecnología de conectividad                                 | Análisis de conectividad         |
| `cant_mb`    | Cantidad de megabytes / capacidad reportada                | Calidad de conexión              |
| `internet`   | Información de internet                                    | Conectividad                     |
| `vel_baj`    | Velocidad de bajada                                        | Calidad de conexión              |
| `vel_sub`    | Velocidad de subida                                        | Calidad de conexión              |
| `operador`   | Operador del servicio                                      | Análisis de proveedores          |
| `conect`     | Estado de conectividad: tiene / no tiene / sin información | Variable central del score salud |


### 5.4. Variables derivadas para el índice

A partir del dataset de salud se creó una agregación por distrito:
| Variable derivada           | Significado                                       |
| --------------------------- | ------------------------------------------------- |
| `total_eess`                | Total de establecimientos de salud en el distrito |
| `eess_sin_conectividad`     | Establecimientos de salud sin conectividad        |
| `eess_con_conectividad`     | Establecimientos de salud con conectividad        |
| `eess_sin_info`             | Establecimientos sin información de conectividad  |
| `pct_eess_sin_conectividad` | Porcentaje de establecimientos sin conectividad   |
| `score_salud`               | Riesgo sanitario asociado a conectividad          |


### 5.5. Criterio para los 13 ubigeos sin dato de salud

El dataset de distritos tiene 1,874 ubigeos, pero el dataset de salud solo cubre 1,861 distritos.

Por eso hay 13 ubigeos sin match de salud.

Para esta primera versión metodológica:
| Campo                       | Valor asignado |
| --------------------------- | -------------: |
| `total_eess`                |              0 |
| `eess_sin_conectividad`     |              0 |
| `eess_con_conectividad`     |              0 |
| `pct_eess_sin_conectividad` |              1 |
| `score_salud`               |              1 |


La justificación es:

> Si un distrito no tiene establecimiento de salud registrado en el dataset descargado, se considera alta vulnerabilidad sanitaria para efectos del índice.

Esta es una decisión metodológica defendible en una primera etapa, pero debe quedar documentada como supuesto.

### 5.6. Insight importante

El dataset de salud permite demostrar una parte fuerte de la hipótesis:

> Existen territorios donde los hogares tienen alta brecha digital y, al mismo tiempo, los establecimientos de salud tienen baja o nula conectividad. En esos casos, la falta de internet afecta tanto a la ciudadanía como a la capacidad del Estado para prestar servicios.

## 6. Dataset: GeoPeru-instituciones_educativas.xlsx
### 6.1. Rol del dataset

Este dataset permite identificar la oferta educativa por distrito.

No contiene una variable directa de conectividad escolar, por lo tanto, no permite afirmar qué colegios tienen o no internet.

Sin embargo, sí permite medir exposición educativa territorial, especialmente ruralidad educativa.

### 6.2. Cobertura
- Nivel: institución educativa
- Total aproximado: 172,750 registros
- Cobertura distrital: 1,874 distritos
- Fuente base: MINEDU, padrón de instituciones y programas educativos

### 6.3. Variables importantes
| Variable     | Significado                        | Uso en el análisis                      |
| ------------ | ---------------------------------- | --------------------------------------- |
| `id`         | Identificador del registro         | Control                                 |
| `codmod`     | Código modular                     | Identificación educativa                |
| `cod_local`  | Código local educativo             | Identificación                          |
| `cod_dpto`   | Código de departamento             | Cruce territorial                       |
| `nom_dpto`   | Nombre de departamento             | Agrupación                              |
| `cod_prov`   | Código de provincia                | Cruce territorial                       |
| `nom_prov`   | Nombre de provincia                | Agrupación                              |
| `cod_dist`   | Código de distrito                 | Llave para cruce                        |
| `nom_dist`   | Nombre del distrito                | Identificación                          |
| `dircen`     | Dirección del centro educativo     | Ubicación                               |
| `cenpob`     | Centro poblado                     | Contexto territorial                    |
| `nlatie`     | Latitud                            | Georreferenciación                      |
| `nlongie`    | Longitud                           | Georreferenciación                      |
| `esta_val`   | Estado de la institución educativa | Filtrar instituciones activas           |
| `areaval`    | Área: urbana o rural               | Variable clave para ruralidad educativa |
| `gesdep_val` | Tipo de gestión/dependencia        | Análisis de gestión                     |
| `nivmod_val` | Nivel o modalidad educativa        | Análisis de oferta educativa            |
| `form_valor` | Forma educativa                    | Contexto educativo                      |
| `gene_valor` | Género atendido                    | Contexto                                |
| `turn_valor` | Turno                              | Contexto                                |
| `ugel_direg` | Código o referencia DRE/UGEL       | Gestión educativa                       |
| `ugel_dreno` | Nombre DRE                         | Gestión educativa                       |
| `ugel_iduge` | Código UGEL                        | Gestión educativa                       |
| `ugel_nouge` | Nombre UGEL                        | Gestión educativa                       |


### 6.4. Variables derivadas para el índice

A partir del dataset educativo se creó una agregación por distrito:
| Variable derivada        | Significado                                                 |
| ------------------------ | ----------------------------------------------------------- |
| `total_iiee_registradas` | Total de instituciones educativas registradas, activas o no |
| `iiee_activas`           | Instituciones educativas activas, rurales + urbanas         |
| `iiee_rurales_activas`   | Instituciones educativas activas ubicadas en área rural     |
| `iiee_urbanas_activas`   | Instituciones educativas activas ubicadas en área urbana    |
| `pct_iiee_rural_activa`  | Porcentaje de instituciones activas que son rurales         |
| `score_educacion`        | Exposición educativa rural                                  |


### 6.5. Criterio metodológico importante

No se deben contar todas las instituciones rurales sin filtrar.

> La variable correcta para el índice es:

Instituciones educativas rurales activas.

Por tanto:

> iiee_rurales_activas = instituciones educativas con estado activo y área rural

Y:

> iiee_activas = instituciones educativas activas rurales + urbanas

El porcentaje usado es:

> pct_iiee_rural_activa = iiee_rurales_activas / iiee_activas

### 6.6. Insight importante

El dataset educativo no mide conectividad escolar directamente.

Por eso, el score educativo no debe presentarse como:

> colegios sin internet

Debe presentarse como:

> exposición educativa rural ante brechas de conectividad territorial.

La explicación correcta es:

> En esta primera versión, la dimensión educativa se aproxima mediante la proporción de instituciones educativas activas rurales, debido a que el dataset educativo descargado no contiene una variable directa de conectividad por institución educativa.

## 7. Dataset derivado: indice_distrital
### 7.1. Rol del dataset

El dataset indice_distrital es una tabla construida a partir de los datasets anteriores.

Su objetivo es consolidar, por distrito, las variables necesarias para calcular:

1. scores unitarios;
2. índice final;
3. nivel de riesgo;
4. prioridad de intervención.

### 7.2. Estructura principal
| Campo                              | Significado                                            |
| ---------------------------------- | ------------------------------------------------------ |
| `ubigeo_txt`                       | Código ubigeo distrital en formato texto de 6 dígitos  |
| `departamento`                     | Nombre del departamento                                |
| `provincia`                        | Nombre de provincia                                    |
| `distrito`                         | Nombre del distrito                                    |
| `poblacion`                        | Población total                                        |
| `hogares`                          | Número de hogares                                      |
| `pct_hogares_sin_internet`         | Porcentaje de hogares sin internet                     |
| `pct_hogares_sin_celular`          | Porcentaje de hogares sin celular                      |
| `pct_hogares_sin_pc_laptop_tablet` | Porcentaje de hogares sin PC/laptop/tablet             |
| `pct_al_menos_1_nbi`               | Porcentaje con al menos una NBI                        |
| `pct_nbi2`                         | Porcentaje de NBI 2                                    |
| `pct_sin_agua_red`                 | Porcentaje sin acceso adecuado a agua por red          |
| `pct_sin_servicio_higienico`       | Porcentaje sin servicio higiénico adecuado             |
| `pct_sin_electricidad`             | Porcentaje sin alumbrado eléctrico                     |
| `pct_pea_desocupada`               | Porcentaje de PEA desocupada                           |
| `pct_pei`                          | Porcentaje de población económicamente inactiva        |
| `pct_jovenes_15_29`                | Porcentaje de población joven de 15 a 29 años          |
| `total_eess`                       | Total de establecimientos de salud                     |
| `eess_sin_conectividad`            | Establecimientos de salud sin conectividad             |
| `eess_con_conectividad`            | Establecimientos de salud con conectividad             |
| `pct_eess_sin_conectividad`        | Porcentaje de establecimientos sin conectividad        |
| `iiee_activas`                     | Instituciones educativas activas                       |
| `iiee_rurales_activas`             | Instituciones educativas rurales activas               |
| `pct_iiee_rural_activa`            | Porcentaje de instituciones activas rurales            |
| `score_digital`                    | Score de brecha digital                                |
| `score_social`                     | Score de vulnerabilidad social                         |
| `score_salud`                      | Score de vulnerabilidad sanitaria/conectividad salud   |
| `score_educacion`                  | Score de exposición educativa rural                    |
| `score_laboral`                    | Score de fragilidad laboral                            |
| `indice_final`                     | Índice Territorial de Vulnerabilidad Digital Compuesta |
| `nivel_riesgo`                     | Clasificación: bajo, medio, alto, crítico              |
| `prioridad`                        | Clasificación de intervención                          |


## 8. Criterios para calcular los scores unitarios

Todos los scores fueron diseñados para tomar valores entre:

> 0 = menor vulnerabilidad
1 = mayor vulnerabilidad

La lógica general es:

> Mientras más alto el score, mayor vulnerabilidad del distrito en esa dimensión.

## 9. Score digital
### 9.1. Pregunta que responde

¿Qué tan excluido digitalmente está el distrito?

### 9.2. Variables usadas
| Variable                           | Peso | Justificación                                                          |
| ---------------------------------- | ---: | ---------------------------------------------------------------------- |
| `pct_hogares_sin_internet`         |  50% | Es la variable más directa del problema                                |
| `pct_hogares_sin_pc_laptop_tablet` |  30% | Sin dispositivo, el acceso digital es limitado                         |
| `pct_hogares_sin_celular`          |  20% | El celular permite acceso mínimo, pero no reemplaza conectividad plena |


### 9.3. Fórmula conceptual
```
score_digital =
(pct_hogares_sin_internet * 0.50
+ pct_hogares_sin_celular * 0.20
+ pct_hogares_sin_pc_laptop_tablet * 0.30) / 100
```

### 9.4. Interpretación
Un score digital alto significa que el distrito combina:

- muchos hogares sin internet;
- muchos hogares sin dispositivos adecuados;
- muchos hogares sin teléfono celular.

Este es el componente central del índice.

## 10. Score social
### 10.1. Pregunta que responde

¿Qué tan vulnerable socialmente es el distrito?

### 10.2. Variables usadas
| Variable                     | Peso | Justificación                                     |
| ---------------------------- | ---: | ------------------------------------------------- |
| `pct_al_menos_1_nbi`         |  35% | Resume vulnerabilidad estructural general         |
| `pct_sin_agua_red`           |  20% | Carencia básica fuerte                            |
| `pct_sin_servicio_higienico` |  20% | Precariedad sanitaria                             |
| `pct_sin_electricidad`       |  15% | Condición crítica para uso tecnológico            |
| `pct_nbi2`                   |  10% | Complemento de vulnerabilidad habitacional/social |


### 10.3. Fórmula conceptual
```
score_social =
(pct_al_menos_1_nbi * 0.35
+ pct_sin_agua_red * 0.20
+ pct_sin_servicio_higienico * 0.20
+ pct_sin_electricidad * 0.15
+ pct_nbi2 * 0.10) / 100
```

### 10.4. Interpretación

Un score social alto significa que la brecha digital ocurre en un territorio donde también existen carencias estructurales.

Esto fortalece la hipótesis de que:

> La falta de internet amplifica otras brechas cuando aparece junto con pobreza, carencias básicas y falta de infraestructura mínima.

## 11. Score salud
### 11.1. Pregunta que responde

¿Qué tan débil es la conectividad de salud en el distrito?

### 11.2. Variables usadas
| Variable                    | Uso                                                                   |
| --------------------------- | --------------------------------------------------------------------- |
| `total_eess`                | Identifica si el distrito tiene establecimientos de salud registrados |
| `pct_eess_sin_conectividad` | Mide la proporción de establecimientos sin conectividad               |


### 11.3. Fórmula conceptual
```
si total_eess = 0:
    score_salud = 1
si total_eess > 0:
    score_salud = pct_eess_sin_conectividad
```

### 11.4. Interpretación
| Caso                                              | Score salud |
| ------------------------------------------------- | ----------: |
| No hay establecimientos de salud registrados      |           1 |
| Todos los establecimientos están sin conectividad |           1 |
| La mitad no tiene conectividad                    |         0.5 |
| Todos tienen conectividad                         |           0 |


### 11.5. Supuesto metodológico

Los 13 distritos sin registro en el dataset de salud fueron tratados como casos de alta vulnerabilidad sanitaria.

Este supuesto debe explicarse en la exposición:

> Los distritos sin registro en el dataset de salud fueron considerados con score_salud alto, ya que representan ausencia de oferta sanitaria registrada en la fuente descargada o falta de cobertura de información para ese territorio.

## 12. Score educación
### 12.1. Pregunta que responde

¿Qué tan expuesta está la oferta educativa del distrito a condiciones rurales?

### 12.2. Variables usadas
| Variable                | Uso                                            |
| ----------------------- | ---------------------------------------------- |
| `iiee_activas`          | Total de instituciones educativas activas      |
| `iiee_rurales_activas`  | Instituciones educativas activas rurales       |
| `pct_iiee_rural_activa` | Proporción rural de la oferta educativa activa |


### 12.3. Fórmula conceptual
```
si iiee_activas = 0:
    score_educacion = 1
si iiee_activas > 0:
    score_educacion = pct_iiee_rural_activa
12.4. Interpretación
Caso	Score educación
No hay instituciones educativas activas	1
Todas las instituciones activas son rurales	1
La mitad son rurales	0.5
Todas son urbanas	0
```

### 12.5. Supuesto metodológico

Este score no mide internet en colegios.

Mide exposición educativa rural.

La explicación correcta es:

> Debido a que el dataset educativo no contiene una variable directa de conectividad escolar, se utiliza la proporción de instituciones educativas activas rurales como proxy de exposición territorial educativa.

## 13. Score laboral
### 13.1. Pregunta que responde

> ¿Qué tan frágil es la situación laboral del distrito?

### 13.2. Variables usadas
| Variable             | Peso | Justificación                                  |
| -------------------- | ---: | ---------------------------------------------- |
| `pct_pea_desocupada` |  60% | Mide presión laboral directa                   |
| `pct_pei`            |  40% | Mide población fuera de la actividad económica |


### 13.3. Fórmula conceptual
```
score_laboral =
(pct_pea_desocupada * 0.60
+ pct_pei * 0.40) / 100
```

### 13.4. Interpretación

Un score laboral alto significa que el distrito tiene mayor fragilidad laboral.

La conexión con el proyecto es:

> Donde existe baja conectividad y fragilidad laboral, se reducen las oportunidades de capacitación digital, empleabilidad, acceso a servicios digitales del Estado y conexión con mercados.

## 14. Índice final
### 14.1. Pregunta que responde

> ¿Qué tan vulnerable es el distrito cuando se combinan brecha digital, vulnerabilidad social, salud, educación y trabajo?

### 14.2. Componentes y pesos
| Componente        | Peso | Justificación                                             |
| ----------------- | ---: | --------------------------------------------------------- |
| `score_digital`   |  35% | Es el centro del problema                                 |
| `score_social`    |  25% | La pobreza amplifica la brecha digital                    |
| `score_salud`     |  20% | La conectividad afecta la capacidad de atención sanitaria |
| `score_educacion` |  10% | Mide exposición educativa rural                           |
| `score_laboral`   |  10% | Mide fragilidad para capacitación y empleabilidad         |


### 14.3. Fórmula conceptual
```
indice_final =
(score_digital * 0.35)
+ (score_social * 0.25)
+ (score_salud * 0.20)
+ (score_educacion * 0.10)
+ (score_laboral * 0.10)
```

### 14.4. Interpretación

El índice final toma valores entre 0 y 1:

|       Valor | Interpretación                         |
| ----------: | -------------------------------------- |
| Cercano a 0 | Menor vulnerabilidad digital compuesta |
| Cercano a 1 | Mayor vulnerabilidad digital compuesta |


El índice no mide solo internet.

> Mide:

Dónde la falta de conectividad digital coincide con vulnerabilidad social, problemas de conectividad en salud, ruralidad educativa y fragilidad laboral.

## 15. Nivel de riesgo
### 15.1. Criterio usado

El nivel de riesgo se calcula a partir del indice_final.
|  Índice final | Nivel de riesgo |
| ------------: | --------------- |
|   0.75 a 1.00 | Crítico         |
| 0.60 a 0.7499 | Alto            |
| 0.40 a 0.5999 | Medio           |
| 0.00 a 0.3999 | Bajo            |



### 15.2. Fórmula conceptual
```
si indice_final >= 0.75:
    nivel_riesgo = "Crítico"
si indice_final >= 0.60:
    nivel_riesgo = "Alto"
si indice_final >= 0.40:
    nivel_riesgo = "Medio"
si indice_final < 0.40:
    nivel_riesgo = "Bajo"
```

### 15.3. Nota metodológica

Estos niveles no son categorías oficiales del Estado.

Son una clasificación metodológica propia del proyecto para ordenar los distritos según su vulnerabilidad digital compuesta.

La forma correcta de explicarlo es:

> Los niveles de riesgo fueron definidos mediante umbrales metodológicos internos para clasificar el índice compuesto en cuatro grupos: bajo, medio, alto y crítico.

## 16. Prioridad de intervención
### 16.1. Pregunta que responde

> ¿Dónde debería intervenir primero el Estado?

### 16.2. Criterio recomendado
| Prioridad   | Criterio                             |
| ----------- | ------------------------------------ |
| Prioridad 1 | Riesgo crítico + alta brecha digital |
| Prioridad 2 | Riesgo crítico                       |
| Prioridad 3 | Riesgo alto                          |
| Observación | Riesgo medio o bajo                  |


### 16.3. Fórmula conceptual
```
si nivel_riesgo = "Crítico" y score_digital >= 0.75:
    prioridad = "Prioridad 1"
si nivel_riesgo = "Crítico":
    prioridad = "Prioridad 2"
si nivel_riesgo = "Alto":
    prioridad = "Prioridad 3"
si nivel_riesgo = "Medio" o "Bajo":
    prioridad = "Observación"
```

### 16.4. Justificación

Se recomienda usar score_digital como criterio de prioridad porque el foco del proyecto es conectividad.

No se recomienda depender solo de la población, porque en Perú existen distritos rurales pequeños con alta vulnerabilidad territorial que podrían quedar invisibilizados si solo se prioriza por cantidad de habitantes.

## 17. Dashboard mínimo para esta primera etapa

El dashboard mínimo debe responder cuatro preguntas:

### 17.1. ¿Qué tan grave es el problema a nivel nacional?

Visuales recomendados:

- Total de distritos analizados
- Índice promedio nacional
- Índice máximo
- Índice mínimo
- Cantidad de distritos críticos
- Cantidad de distritos prioridad 1

### 17.2. ¿Cómo se distribuye el riesgo?

Visuales recomendados:

Tabla o gráfico de barras por nivel de riesgo:
- Bajo
- Medio
- Alto
- Crítico

### 17.3. ¿Dónde se concentra la vulnerabilidad?

Visuales recomendados:

- Top 20 distritos con mayor índice final
- Top departamentos por índice promedio
- Ranking de provincias o distritos críticos
### 17.4. ¿Dónde intervenir primero?

Visuales recomendados:

- Tabla de distritos Prioridad 1
- Tabla de distritos Prioridad 2
- Filtro por departamento
- Filtro por nivel de riesgo
## 18. Fórmulas corregidas para el dashboard en Google Sheets

En el archivo actual, las columnas clave son:

| Columna | Campo             |
| ------- | ----------------- |
| `Z`     | `score_digital`   |
| `AA`    | `score_social`    |
| `AB`    | `score_salud`     |
| `AC`    | `score_educacion` |
| `AD`    | `score_laboral`   |
| `AE`    | `indice_final`    |
| `AF`    | `nivel_riesgo`    |
| `AG`    | `prioridad`       |


### 18.1. Total de distritos
```
=COUNTA(indice_distrital!A2:A)
```

### 18.2. Distritos con índice válido
```
=COUNT(indice_distrital!AE2:AE)
```
### 18.3. Distritos con índice no válido
```
=COUNTA(indice_distrital!A2:A)-COUNT(indice_distrital!AE2:AE)
```

### 18.4. Índice promedio nacional
```
=AVERAGE(FILTER(indice_distrital!AE2:AE;ISNUMBER(indice_distrital!AE2:AE)))
```

### 18.5. Índice máximo
```
=MAX(FILTER(indice_distrital!AE2:AE;ISNUMBER(indice_distrital!AE2:AE)))
```

### 18.6. Índice mínimo
```
=MIN(FILTER(indice_distrital!AE2:AE;ISNUMBER(indice_distrital!AE2:AE)))
```

### 18.7. Distritos críticos
```
=COUNTIF(indice_distrital!AF2:AF;"Crítico")
```

### 18.8. Distritos Prioridad 1
```
=COUNTIF(indice_distrital!AG2:AG;"Prioridad 1")
```

### 18.9. Top 20 distritos más vulnerables
```
=QUERY(
  indice_distrital!A2:AG;
  "select B,C,D,E,Z,AA,AB,AE,AF,AG
   where AE is not null
   order by AE desc
   limit 20";
  0
)
```

### 18.10. Top departamentos por índice promedio
```
=QUERY(
  indice_distrital!A2:AG;
  "select B, count(B), avg(AE), sum(E)
   where AE is not null
   group by B
   order by avg(AE) desc
   label B 'Departamento',
         count(B) 'Distritos',
         avg(AE) 'Índice promedio',
         sum(E) 'Población total'";
  0
)
```

### 18.11. Distritos Prioridad 1
```
=QUERY(
  indice_distrital!A2:AG;
  "select B,C,D,E,Z,AB,AE,AG
   where AG = 'Prioridad 1'
   order by AE desc";
  0
)
```

### 18.12. Distritos sin dato de salud
```
=QUERY(
  indice_distrital!A2:AG;
  "select B,C,D,R,AB,AE,AF,AG
   where R = 0
   order by AE desc";
  0
)
```

## 19. Insights importantes para exponer
### 19.1. Insight 1: La conectividad digital es una brecha multiplicadora

El problema no debe presentarse solo como falta de internet.

Debe presentarse así:

> La falta de conectividad digital limita simultáneamente el acceso a educación, salud, capacitación laboral, empleo y servicios públicos digitales.

### 19.2. Insight 2: El índice permite priorizar territorios

El índice ayuda a pasar de una lectura general del problema a una herramienta de decisión.

No solo dice:

> Hay brecha digital.

Sino:

> Estos distritos deberían ser priorizados porque concentran varias brechas al mismo tiempo.

### 19.3. Insight 3: La salud conectada es un factor crítico

El dataset de salud muestra que la conectividad de establecimientos de salud es una dimensión territorial importante.

Un distrito puede tener hogares sin internet y, además, establecimientos de salud sin conectividad.

Eso genera una doble vulnerabilidad:

- ciudadanía con bajo acceso digital;
- servicios públicos con baja capacidad digital.

### 19.4. Insight 4: La educación requiere una segunda etapa de datos

El dataset educativo permite medir ruralidad educativa, pero no conectividad escolar directa.

Por eso, en la primera etapa usamos ruralidad educativa como proxy.

Para una segunda etapa, sería recomendable buscar datos adicionales sobre:

- colegios con internet;
- velocidad de internet escolar;
- conectividad por UGEL;
- programas de conectividad educativa.

### 19.5. Insight 5: Los 5 datasets son suficientes para una primera versión, pero no para la versión final robusta

Los 5 datasets cubren:

- base territorial;
- vulnerabilidad social;
- brecha digital de hogares;
- oferta educativa;
- oferta sanitaria;
- conectividad en salud.

Pero todavía faltan datos sobre:

- cobertura móvil;
- fibra óptica;
- internet fijo;
- red dorsal;
- infraestructura vial;
- centros de capacitación;
- programas sociales;
- inversión pública;
- conectividad educativa directa.

## 20. Capas adicionales recomendadas para próximas etapas

Para fortalecer la propuesta, se recomienda descargar o revisar capas de GEO Perú relacionadas con:
| Capa / categoría              | Utilidad                                                   |
| ----------------------------- | ---------------------------------------------------------- |
| Infraestructura               | Red vial, accesibilidad, equipamiento territorial          |
| Salud                         | Validar más capas de servicios o conectividad              |
| Educación                     | Buscar conectividad educativa directa                      |
| Pobreza                       | Complementar NBI con pobreza monetaria u otros indicadores |
| Trabajo                       | Capacitación laboral, empleo, oferta productiva            |
| Programas Sociales            | Identificar territorios con alta vulnerabilidad social     |
| Económico                     | Actividad económica y potencial productivo                 |
| Financiero                    | Inclusión financiera y acceso a servicios                  |
| GEO Servicios                 | Posibles servicios georreferenciados complementarios       |
| Telecomunicaciones, si existe | Cobertura móvil, fibra, antenas, red dorsal                |



## 21. Limitaciones metodológicas de esta primera etapa

Es importante reconocer las limitaciones para que la propuesta sea honesta y defendible.

### 21.1. Datos de conectividad del hogar

La conectividad de hogares proviene del Censo 2017, por lo tanto, puede no reflejar completamente la situación actual.

Aun así, sirve como línea base territorial.

### 21.2. Datos de salud

El dataset de salud no cubre 13 ubigeos encontrados en el dataset distrital.

Se asignó score_salud = 1 a esos casos como supuesto metodológico.

### 21.3. Datos de educación

El dataset educativo no tiene conectividad escolar directa.

Se usó ruralidad educativa activa como variable proxy.

### 21.4. Datos laborales

El componente laboral usa PEA desocupada y PEI como aproximación.

Para una versión más sólida, se deberían incorporar datos de capacitación laboral, empleo juvenil, CETPRO, institutos o programas de empleabilidad.

## 22. Narrativa recomendada para la exposición

Una forma clara de presentar esta primera etapa sería:

> En esta primera etapa construimos un Índice Territorial de Vulnerabilidad Digital Compuesta a nivel distrital. El índice combina cinco dimensiones: brecha digital del hogar, vulnerabilidad social, conectividad en establecimientos de salud, exposición educativa rural y fragilidad laboral. El objetivo no es medir solamente falta de internet, sino identificar territorios donde la desconexión digital amplifica otras brechas de acceso a servicios públicos, educación, salud y oportunidades laborales.

Luego:

> El índice toma valores entre 0 y 1. Los valores más altos indican mayor vulnerabilidad. A partir del índice clasificamos los distritos en cuatro niveles de riesgo: bajo, medio, alto y crítico. Además, definimos prioridades de intervención para identificar dónde debería enfocarse primero una política pública de conectividad con enfoque territorial.

Y finalmente:

> Esta primera versión demuestra que la conectividad debe ser entendida como infraestructura habilitante. No solo conecta hogares: también condiciona la capacidad del Estado para brindar servicios, la posibilidad de estudiar, capacitarse, trabajar y acceder a oportunidades.

## 23. Conclusión de esta primera etapa

Con los 5 datasets actuales ya se puede sostener una primera versión válida del análisis.

La propuesta tiene coherencia porque:

1. usa datos oficiales de GEO Perú;
2. trabaja a nivel distrital;
3. cruza brecha digital con vulnerabilidad social;
4. incorpora salud y educación;
5. genera un índice interpretable;
6. permite priorizar territorios;
7. produce insumos para un dashboard mínimo;
8. puede convertirse en una propuesta de valor público.

La siguiente etapa debería enfocarse en dos cosas:

1. mejorar el dashboard visual;
2. incorporar capas adicionales de conectividad, infraestructura y capacitación laboral para fortalecer la propuesta final.