## 1. MATRIZ DE PATRONES
Tabla de patrones identificados
#	Patrón Identificado	Equipo 1	Equipo 4	Equipo 6
1	Reactivación de código legacy	✔	—	—
2	Despliegue sin controles (canary, rollback)	✔	—	—
3	Ausencia de límites operacionales	✔	—	—
4	Falta de monitoreo en tiempo real	✔	—	✔
5	Overflow / mal manejo de tipos	—	✔	—
6	Reutilización insegura de código	—	✔	—
7	Falta de simulación en condiciones reales	—	✔	—
8	Redundancia homogénea (backup = primario)	—	✔	—
9	Validación incorrecta de reglas de negocio	—	—	✔
10	Sin alarmas por valores atípicos	—	—	✔
11	Pruebas insuficientes en pricing / tarifas	—	—	✔
12	Dependencia en sistemas legacy	—	—	✔
## 2. TABLA DE CONSECUENCIAS
Tipo de Consecuencia	Descripción	Casos Relacionados	Ejemplo
Económica	Pérdidas monetarias directas	1, 6	$440M Knight; miles de boletos casi gratis
Operativa	Fallo total de misión o servicio	4	Cohete destruido a los 37 s
Reputacional	Pérdida de confianza pública	1, 6	Crisis mediática y escrutinio
Legal / Regulatoria	Demandas o investigaciones	1	Revisión de SEC por colapso del mercado
Seguridad / Vida Humana	Riesgo físico directo	4	Falla catastrófica del Ariane 5
Técnica	Fallo de sistema, corrupción de datos	Todos	Activación de flags, overflow, reglas rotas
## 3. DIAGRAMA DE CAUSAS RAÍZ (Texto Descriptivo)
Causa A – Cambios no controlados en producción

Casos conectados:

Knight Capital (equipo 1)

United Airlines (equipo 6)

Ariane 5 (equipo 4 – software heredado sin control)

Conexión:
Cambios aplicados sin validación real, sin canary, sin rollback y sin verificar compatibilidad.

Causa B – Asunciones incorrectas sobre el entorno real

Casos conectados:

Ariane 5: aceleración fuera del rango

Knight Capital: flags legacy no contemplados

United Airlines: precios mínimos no validados

Conexión:
El sistema “asumió” condiciones ideales que no se cumplen en producción.

Causa C – Monitoreo insuficiente

Casos conectados:

Knight: 45 min sin detectar operaciones erróneas

United: miles de tickets vendidos sin alerta

Ariane 5: fallo no identificado antes del vuelo

Conexión:
Sin alertas ni telemetría, la falla escala sin control.

Causa D – Pruebas incompletas o no representativas

Casos conectados:

Knight: faltaron pruebas end-to-end reales

Ariane 5: sin pruebas de rango ni simulación realista

United: sin pruebas de pricing extremo

Conexión:
Las pruebas no representaron las condiciones reales donde el software opera.

Causa E – Confianza excesiva en automatización

Casos conectados:

Knight: bots ejecutando miles de operaciones

Ariane 5: dos sistemas con el mismo bug

United: precios generados automáticamente

Conexión:
Automatización sin límites ni supervisión humana.

## 4. SÍNTESIS CRÍTICA
4.1 Patrones universales (presentes en TODAS las industrias)
1. Cambios aplicados sin controles

Ejemplos:

Knight: activación de código viejo

Ariane 5: software heredado sin verificación

United: reglas de precio aplicadas sin validación
Universalidad: ocurre en cualquier sistema con despliegues o configuraciones.

2. Falta de validación de límites

Ejemplos:

Knight: sin límites de órdenes

Ariane: overflow por rango numérico

United: precios $0 no detectados
Universalidad: todo software recibe entradas fuera del rango esperado.

3. Monitoreo deficiente

Ejemplos:

Knight: 45 minutos sin intervención

Ariane: fallo no detectado antes del lanzamiento

United: precios anómalos vendidos por horas
Universalidad: sin visibilidad, el error escala.

4. Pruebas que no representan la realidad

Ejemplos:

Knight: staging ≠ producción

Ariane: simulación insuficiente

United: no probaron casos extremos de pricing
Universalidad: pasa cuando se confía ciegamente en ambientes “simulados”.

5. Automatización sin salvaguardas

Ejemplos:

Knight: bots de trading sin límite

Ariane: redundancia homogénea

United: pricing automático sin alertas
Universalidad: la automatización amplifica errores a gran escala.

4.2 ¿Qué hace que un desastre sea catastrófico y no manejable?
Desastre Catastrófico

Escala automática sin límites

Impacto inmediato

Fallo total de misión

No hay “modo seguro”

No existe contención

Ejemplos:

Ariane 5: destrucción total

Knight Capital: $440M en minutos

Desastre Manejable

Hay límites naturales del daño

Da tiempo de reaccionar

No afecta misión crítica

Puede compensarse económicamente

Ejemplo:

United Airlines: costoso pero sin riesgo ni impacto mortal

4.3 Comparación: ¿Por qué Knight quebró pero United no?
Factor	Knight Capital	United Airlines
Límites del daño	No existían	Sí, precio del ticket
Automatización	Desbocada	Moderada
Velocidad del error	Segundos	Horas
Naturaleza del negocio	Trading (tiempo real)	Venta de tickets
Riesgo sistémico	Altísimo	Medio

➡ Knight falló con software sin límites. United falló en una función comercial, no crítica.

## 5. Tabla de Pruebas vs Desastres vs Aplicación al Login
Tipo de Prueba	Desastres que habría prevenido	Aplicación a nuestro login
Carga	Knight, United	Verificar miles de inicios simultáneos
Integración	Knight, United	Validar BD + roles + correo
Seguridad	General	SQLi, fuerza bruta, sesiones
Edge cases	Ariane, United	Emails vacíos, formatos incorrectos
Regresión	Knight	Evitar que cambios rompan autenticación
Usabilidad	United	Mensajes claros y accesibles
Code Review	Ariane	Revisar conversión de tipos, validaciones
Multiplataforma	United	Desktop, móvil y navegadores
## 6. Caso más aterrador y reflexión personal
Caso elegido: Ariane 5 (Equipo 4)
¿Por qué es el más aterrador?

Un solo error de conversión numérica destruyó un cohete de $370M.

La redundancia no ayudó porque ambos sistemas tenían el mismo bug.

Es un caso donde una mala decisión de software afecta el mundo físico.

No hay “rollback”: el fallo es irreversible.

Conexión con mi práctica como programador

Me recuerda probar conversiones, límites y excepciones.

Me obliga a nunca confiar ciegamente en código heredado.

Refuerza la idea de que una pequeña omisión puede causar un fallo enorme.

