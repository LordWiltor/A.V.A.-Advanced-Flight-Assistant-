# A.V.A. (ASISTENTE DE VUELO AVANZADO): Manual Oficial de Usuario y Guía de Despliegue
- **Versión:** v2.5 ES
- **Archivo:** `README.md`
- **Unvierso:** X3: Terran Conflict (v3.2 / v3.4 Vanilla + Official Bonus Pack)

================================================================================
ÍNDICE GENERAL
================================================================================
1. Manifiesto y Visión General (¿Qué es A.V.A.?)
2. Arquitectura del Sistema y Mapa de Archivos (ava_0xx_ a ava_2xx_)
3. Guía de Despliegue Rápido (Instalación, Plataformas Recomendadas y OCR)
4. El Ciclo de Vuelo y Escalabilidad (Día a Día, Multimodalidad y Cierre Seguro)
5. Gestión de Mods y Parches (ava_002_mods_*.txt)
6. Taller de Creación de Personalidades (SDK de Voz Capa 2)
7. Arquitectura Bilingüe Nativa (ES / EN) y Localización Internacional

================================================================================
1. MANIFIESTO Y VISIÓN GENERAL (¿QUÉ ES A.V.A.?)
================================================================================

A.V.A. (Asistente de Vuelo Avanzado) es un copiloto táctico inteligente, calculador industrial y computadora de a bordo diseñado para operar mediante Modelos de Lenguaje Avanzados (LLMs) integrado directamente en tus sesiones de simulación de *X3: Terran Conflict*.

### La Filosofía de las Tres Capas
A diferencia de los asistentes conversacionales genéricos que inventan datos o rompen la ambientación, A.V.A. se apoya en una arquitectura de Separación Estricta de Responsabilidades:
* **Capa 0 (El Motor y los Datos):** La verdad técnica inmutable del simulador, sus fórmulas matemáticas deterministas y su catálogo balístico, astronómico y económico.
* **Capa 1 (La Memoria de Partida):** El cuaderno de bitácora dinámico que registra tu identidad, créditos, naves, complejos, reputación y sectores explorados.
* **Capa 2 (La Interfaz de Voz):** La identidad y estilo de comunicación del copiloto (con el modelo oficial Betty por defecto), 100% intercambiable sin alterar los cálculos.

### La Regla de Oro (Jerarquía Inquebrantable)
> **Capa 0 (Motor y Datos) > Capa 1 (Tu Partida) > Capa 2 (Personalidad)**
A.V.A. tiene prohibición absoluta de alucinar o inventar datos. Si una nave no puede equipar un arma, si un escudo supera la potencia del generador de la nave o si el piloto no tiene créditos suficientes en su bitácora, el sistema alertará con rigor matemático sin importar lo permisiva o dramática que sea la personalidad activa.

================================================================================
2. ARQUITECTURA DEL SISTEMA Y MAPA DE ARCHIVOS
================================================================================

El ecosistema se organiza mediante una nomenclatura centesimal estricta (`ava_0xx_` a `ava_2xx_`) combinada con un sufijo de idioma obligatorio (`_ES.txt` para la rama en español, `_EN.txt` para la rama en inglés).

*(Nota Crítica de Nomenclatura: Los módulos del proyecto llevan obligatoriamente sufijo de idioma; los archivos maestros del motor de juego como `Globals.txt`, `hq.xml`, `start.xml`, `gamestarts.xml` o `TShips` jamás llevan sufijo).*

### 🧠 Capa 0: Sistema Base y Datos Maestros (Rango 000 a 099)
* `ava_000_core_ES.txt`: El "cerebro" lógico. Algoritmos de cálculo (DPS Neto, eficiencia térmica de escudos, complejos N-1, fórmulas PHQ, tasación de venta y consumo de salto).
* `ava_001_index_ES.txt`: Enrutador general y glosario enciclopédico (IS vs OOS, MK3, catálogo v4.1.01 del Bonus Pack con costes y requisitos).
* `ava_002_mods_ES.txt`: Capa de parches delta. Registra modificaciones instaladas que pisan con prioridad absoluta al juego base (ej. TD_MiniMod).
* `ava_002_mods_EXAMPLE_ES.txt`: Archivo de ejemplo con modificaciones reales documentadas (TD_MiniMod y librerías de Cycrow).
* `ava_003_db_weapons_ES.txt`: Catálogo de 37 láseres, 35 misiles (con índice táctico) y 6 escudos.
* `ava_004_db_ships_ES.txt`: Catálogo de 329 naves oficiales, arcos de torretas agrupadas, generadores, bodegas y astilleros.
* `ava_005_db_economy_ES.txt`: 98 mercancías, 49 software/mejoras, 303 fábricas y 41 dársenas.
* `ava_006_db_universe_ES.txt`: Cartografía de 231 sectores fijos (+ UFJD), conexiones puertas/TOA, asteroides, 19 naves abandonadas y 12 cajas secretas.
* `ava_007_db_mechanics_ES.txt`: Constantes de Globals.txt, Cuartel General (hq.xml), 31 rangos, 16 reputaciones y abordaje con marines.
* `ava_008_db_corporations_ES.txt`: 8 corporaciones, 25 naves de recompensa, 18 inicios oficiales (start.xml / gamestarts.xml) y naves sobrecargadas (*Overtuned*).
* `ava_009_db_plots_ES.txt`: Árbol de dependencias y guías paso a paso de las 9 tramas oficiales.
* `ava_INSTRUCTIONS_ES.txt`: **Bundle Compilado Maestro**. Fusión optimizada sin cabeceras redundantes de `ava_000_core_ES.txt`, `ava_100_log_core_ES.txt` y `ava_201_persona_betty_ES.txt`, listo para copiar en un solo paso al System Prompt.

*(Existe una rama espejo en inglés con idéntica estructura y sufijo `_EN.txt` para simulaciones nativas en inglés).*

### 💾 Capa 1: Estado y Persistencia de Campaña (Rango 100 a 199)
* `ava_100_log_core_ES.txt`: Gestor de memoria. Regula la ingesta del vector de estado, onboarding asistido, enclavamiento de seguridad (*Safety Interlock*) y reporte en 2 bloques.
* `ava_101_log_campaign_ES.txt`: El archivo maestro vivo de tu partida (Datos del piloto, objetivos por fases, créditos, ubicación, inventario y mapa).
* `ava_101_log_campaign_EXAMPLE_ES.txt`: Archivo de ejemplo con una campaña real en curso planificada al detalle (Proyecto Atlantis).
* `ava_102_log_campaign_TEMPLATE_ES.txt`: Plantilla neutra universal en blanco de reserva o reinicio en disco.

### 🎭 Capa 2: Interfaz de Voz y Personalidad (Rango 200 a 299)
* `ava_200_persona_TEMPLATE_ES.txt`: SDK y molde universal para crear nuevas personalidades compatibles (con variables de tratamiento y cierre).
* `ava_201_persona_betty_ES.txt`: Personalidad oficial predeterminada de Betty (diegética, confidente, apasionada del lore, oficial táctico y soporte OCR).

================================================================================
3. GUÍA DE DESPLIEGUE RÁPIDO (INSTALACIÓN Y REQUISITOS)
================================================================================

### Plataforma Óptima Recomendada: Google AI Studio (Modelos Gemini)
Aunque A.V.A. funciona en cualquier LLM moderno con ventana de contexto amplia (Claude Projects, ChatGPT Plus), **Google AI Studio (utilizando modelos Gemini 1.5 Flash o Gemini 1.5 Pro)** es la plataforma idónea por tres ventajas determinantes:
1. **Ventana de Contexto Masiva (1M a 2M tokens):** Permite cargar los 9 archivos de datos completos a la vez sin pérdida de atención ni necesidad de recortar tablas.
2. **Multimodalidad Nativa y OCR de Cabina:** Puedes pegar capturas de pantalla del juego directamente con `Ctrl + V`. Gemini lee al segundo los créditos, rangos y naves de tus menús `P` y `R` sin que tengas que teclear números.
3. **Persistencia de Proyecto y Prompt Caching:** Creas y guardas tu prompt una sola vez. Las instrucciones quedan cacheadas y las respuestas posteriores tardan milisegundos consumiendo un coste mínimo.

---

### MÉTODOS DE INSTALACIÓN

#### MÉTODO A: Plataformas con Instrucciones del Sistema (AI Studio, Claude Projects, Custom GPTs) — Recomendado
1. **Instrucciones del Sistema (System Prompt):**
   Abre el archivo compilado **`ava_INSTRUCTIONS_ES.txt`** (o `ava_INSTRUCTIONS_EN.txt` si juegas en inglés), pulsa `Ctrl + A`, `Ctrl + C` y pégalo en la caja de *System Instructions*.
   *(Alternativa modular: si prefieres usar otra personalidad o editar módulos por separado, pega en su lugar el contenido de `ava_000_core_ES.txt`, `ava_100_log_core_ES.txt` y tu personalidad elegida).*
2. **Archivos de Conocimiento / Contexto:**
   Sube a la sección de archivos del proyecto:
   • Los 9 archivos de datos maestros de tu idioma: desde `ava_001_index_ES.txt` hasta `ava_009_db_plots_ES.txt`.
   • Tu archivo de partida activa: `ava_101_log_campaign_ES.txt`.
   • ⚠️ *ADVERTENCIA:* NO subas `ava_102_log_campaign_TEMPLATE_ES.txt`, `ava_200_persona_TEMPLATE_ES.txt`, `ava_002_mods_EXAMPLE_ES.txt` ni `ava_101_log_campaign_EXAMPLE_ES.txt`. Son plantillas de reserva y ejemplos en tu disco duro.

#### MÉTODO B: Chat Convencional (Arrastrar y Soltar)
1. Inicia un nuevo chat con la IA.
2. Arrastra a la ventana los 9 archivos de datos (`ava_001_` a `ava_009_` de tu idioma) y tu bitácora `ava_101_log_campaign_ES.txt`.
3. Pega el texto de `ava_INSTRUCTIONS_ES.txt` en el primer mensaje seguido de:  
   *«Sistemas de a bordo vinculados. Inicia el protocolo de lectura de bitácora».*

---

### El Primer Despegue (Onboarding Asistido)
* **Partida Nueva (Rama A):** Dile a A.V.A.: *«Iniciamos una campaña nueva desde el segundo cero»*. Te pedirá tu título, nombre, inicio elegido y gran objetivo, y autocompilará tu bitácora incorporando la **Sección 0 (Datos del Piloto)** y tu equipo de serie de fábrica.
* **Partida en Curso (Rama B):** Dile a A.V.A.: *«A.V.A., inicializa una campaña en curso para mi partida avanzada»*. Te formulará 3 preguntas sobre tu tecla 'P', tramas y flota, deduciendo tus rangos automáticamente.

================================================================================
4. EL CICLO DE VUELO Y ESCALABILIDAD (CÓMO SE JUEGA EN EL DÍA A DÍA)
================================================================================

### A. Apertura de Sesión
Al arrancar cada sesión de juego, saluda a tu copiloto. A.V.A. ejecutará la **Lectura Obligatoria de Estado (Paso 0)**: asimilará tu título, bio, saldo disponible, nave insignia, ubicación táctica y metas en curso.

### B. Durante el Vuelo
Juega libremente sin interrumpir tu partida. Consulta cualquier duda táctica en lenguaje natural:
* **Combate y Balística:** Cálculo de DPS Neto frente a recarga pasiva de escudos y consumo de munición física en OOS.
* **Finanzas y Tasación:** Regla del 100% de venta en Dársenas de Equipo frente al 50% residual al vender naves equipadas en Astilleros.
* **Logística y Complejos:** Regla de $N-1$ CCKs, producción de minas por escalones discretos y bucles cerrados de Silicio/Cristales.
* **Navegación:** Restricción de aceleradores transorbitales TOA y cálculo exacto de células de salto.

### C. Cierre de Sesión y Enclavamiento de Seguridad (Safety Interlock)
Al terminar tu jornada de juego, el sistema cuenta con un **mecanismo de seguridad para evitar que la IA invente datos**:

#### 🔹 El Atajo Maestro: La Telemetría Visual (OCR en 10 Segundos) — ¡Recomendado!
1. En el juego, antes de salir, pulsa **`P`** (Ficha de Piloto con créditos, rangos y reputaciones) y **`R`** (Lista de Propiedades si compraste o moviste naves).
2. Haz una captura rápida con **`Windows + Shift + S`**.
3. Ve a tu chat (en Google AI Studio) y pulsa **`Ctrl + V`** para pegar la imagen directamente.
4. Escribe: *«Betty, cerramos sesión con esta telemetría. Hoy hemos cumplido [X tarea]. Dame los dos bloques».*
*La IA leerá los datos directamente de la imagen por OCR sin que tengas que teclear ningún número.*

#### 🔹 ¿Y si pides cerrar sin aportar datos? (Safety Interlock)
Si simplemente dices: *«Betty, cerramos por hoy»*, A.V.A. **detendrá la compilación** para evitar alucinaciones y te responderá dentro del rol:  
*«Entendido, mi [título]. Asegurando sistemas de maniobra y activando protocolo de fondeo en estación. Para que pueda compilar el informe oficial en los bancos de memoria de a bordo, facilítame la telemetría de la jornada: puedes proyectarme una captura óptica directa de tus paneles de vuelo (teclas P y R) o bien dictarme tu saldo final, sector actual y las naves que hayamos reclamado o vendido hoy».*

#### 🔹 El Copiado en Dos Bloques
Una vez aportada la telemetría, A.V.A. te entregará dos bloques de código Markdown limpios:
* **BLOQUE 1 (Estado Global):** Selecciona entre `<!-- BLOQUE DE ESTADO GLOBAL - INICIO -->` y `<!-- BLOQUE DE ESTADO GLOBAL - FIN -->` en tu archivo `ava_101_log_campaign_ES.txt` y sobrescribe la Sección 2 completa.
* **BLOQUE 2 (Historial Sesión #X):** Sustituye la fila del Índice Rápido (Sección 3) y añade la entrada detallada con las notas del copiloto al final de la Sección 4.

================================================================================
5. GESTIÓN DE MODS Y PARCHES (ava_002_mods_*.txt)
================================================================================

A.V.A. utiliza una Capa Delta de Sobrescritura: los 9 archivos de datos maestros se mantienen 100% Vanilla puros. Cualquier mod instalado (como el multiplicador de almacenes de dársenas *TD_MiniMod* o utilidades de *Cycrow*) se registra en `ava_002_mods_ES.txt` (o `_EN.txt`).

### Regla de Oro de Prioridad
Cualquier parámetro registrado en `ava_002_mods_*.txt` **PISA e invalida automáticamente** al dato Vanilla en los cálculos del copiloto, citándolo dentro del rol como *"Protocolo de Modificación de Ingeniería [Nombre]"* o *"Sobrescritura de Firmware Activa"*.

================================================================================
6. TALLER DE CREACIÓN DE PERSONALIDADES (SDK DE VOZ CAPA 2)
================================================================================

Puedes cambiar la voz, modismos y trato de A.V.A. en cualquier momento creando un archivo a partir de `ava_200_persona_TEMPLATE_ES.txt`:
* `TRATAMIENTO_JERÁRQUICO`: Admite resolución dinámica con `[Título]` y `[Nombre]` definidos en la Sección 0 de la bitácora.
* `TIPO_INMERSIÓN`: Elige entre `DIEGÉTICA` (habla siempre desde dentro de la cabina sin romper la cuarta pared) o `NO_DIEGÉTICA` (guía técnico de videojuego).
* `ESTILO_INTERLOCK_CIERRE`: Define cómo tu personaje solicita la telemetría si pides cerrar en vacío (ej. dulzura protocolaria, rudeza militar Split o contabilidad mercante Teladi).
* Para activarla: Sustituye el módulo de Betty en tu System Prompt por el texto de tu nueva personalidad.

================================================================================
7. ARQUITECTURA BILINGÜE NATIVA (ES / EN) Y LOCALIZACIÓN INTERNACIONAL
================================================================================

El ecosistema A.V.A. v2.5 se apoya en una **arquitectura dual nativa y certificada** compuesta por dos ramas completamente desarrolladas e independientes:

### 1. Las Dos Ramas Oficiales Certificadas

#### 🇪🇸 Rama Oficial en Español (`*_ES.txt`)
* Diseñada para simulaciones jugadas con el texto de *X3: Terran Conflict* en español.
* Actúa como Fuente de Verdad técnica e histórica original del proyecto.
* Incorpora la nomenclatura oficial del juego en castellano (*Cuna de Leyenda*, *Lanzador de Plasma*, *Láser Reparador*, etc.).

#### 🇬🇧 Rama Oficial en Inglés (`*_EN.txt`)
* Diseñada para simulaciones jugadas en inglés nativo.
* Realiza una **purga total de residuos bilingües**, entregando textos limpios redactados en inglés nativo técnico.
* Utiliza con exactitud milimétrica las cadenas oficiales canónicas del motor de juego (`secret containers`, `The Moon`, `Patriarch's Conclusion`, `Notus Hauler`, etc.).
* Adapta los separadores numéricos al estándar anglosajón (comas para millares, puntos decimales y punto y coma para desgloses numéricos).

### 2. Despliegue para Jugadores de Otros Idiomas (DE, FR, RU, etc.)
Los jugadores de otras comunidades idiomáticas pueden desplegar A.V.A. de dos formas:
1. **Despliegue Plug & Play vía LLM:** Carga la rama en inglés (`*_EN.txt`) y habla con A.V.A. en tu idioma natal (alemán, francés, etc.). El LLM procesará las tablas en inglés y te responderá en tu idioma nativo con total precisión matemática.
2. **Localización Dedicada:** Si deseas traducir tu propio paquete en disco, utiliza la rama `*_EN.txt` como plantilla base neutral, manteniendo los identificadores unívocos del motor (`SS_SH_*`, `SS_LASER_*`, `SS_FAC_*`) sin alterar.