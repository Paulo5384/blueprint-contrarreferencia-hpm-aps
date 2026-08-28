# Blueprint — Contrarreferencia y Continuidad Asistencial HPM–APS

Mapa de servicios interactivo que cruza actores, rutas de gestión y objetos de gestión MGIAA a lo largo del circuito de contrarreferencia (CR), desde la decisión clínica hasta el cierre del ciclo.

**Hospital Puerto Montt · Servicio de Salud del Reloncaví**
Navegadores en Red / Unidad de Gestión Territorial (UGT)

## Qué contiene

- **9 etapas** (T0–T8): Decisión clínica → Emisión CR → Envío → Recepción → Revisión y decisión → Gestión → Vinculación → Atención/continuidad → Cierre.
- **Trayectoria y actores**: Persona/cuidador, Especialista HPM, Sistema HPM/RCE, CODE APS, enlace ECICEP, Gestión de casos APS, SOME, Equipo clínico APS — con línea de interacción y badges de frontstage/backstage.
- **Responsabilidad primaria** por etapa.
- **3 rutas de gestión de la CR**: informativa 🔵, con acción requerida 🟠, prioritaria/crítica 🔴 — como lente de lectura transversal, no como reescritura del rol de cada actor.
- **Objeto de gestión MGIAA**: demanda / oferta / trayectoria / articulación-continuidad.
- **Reglas del proceso**: 6 preguntas de control por etapa.
- **Datos, tiempos, alertas y escalamiento**: evidencia mínima, hitos T0–T8, tiempos de gestión, alertas y responsables de escalamiento.

## Funcionalidad

- Edición inline de celdas, filas y columnas (insertar antes/después, eliminar).
- Tags de calidad: fortaleza, precaución, red flag, referencia.
- Badge de estado AS-IS/TO-BE por celda (existe / no existe / no sabemos / propuesta) — clic para ciclar.
- Colapsar/expandir capas individualmente o todas de una vez.
- Guardado de versiones con nombre y notas, autoguardado cada 3 minutos.
- Dos perfiles de acceso: **Visualizador** (solo lectura) y **Editor** (contraseña `hpm`).
- Vista de impresión.

## Estado del guardado

Las versiones se guardan en **Firebase Firestore** (proyecto `blueprint-cr-hpm`, colección `versiones_cr`) — sincroniza entre dispositivos y entre editores en tiempo real. Autoguardado cada 3 minutos mientras haya cambios sin guardar.

**Nota de seguridad:** las reglas de Firestore están abiertas (`allow read, write: if true`) porque el control de acceso real lo da el perfil Editor con contraseña dentro del propio blueprint, no Firebase Auth. El `apiKey` visible en el código no es secreto — es normal en apps Firebase del lado del cliente — pero cualquiera con la URL de Firestore podría leer o escribir la colección directamente. Aceptable para un taller interno; no usar así si el contenido fuera sensible o de acceso restringido por ley.

## Base normativa y conceptual

- ORD. N°2301 — Sobre el registro y gestión de contrarreferencia en la atención de especialidad médica y odontológica.
- Protocolo de referencia y contrarreferencia 2025–2030, Res. Exenta N°6041-2025.
- Documento Rector MGIAA v2.0 (Modelo de Gobernanza Integral de la Atención Abierta).

## Uso

Abrir `index.html` directamente en el navegador, o servir como sitio estático (GitHub Pages / Netlify) — no requiere build ni dependencias externas.
