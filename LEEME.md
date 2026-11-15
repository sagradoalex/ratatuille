# Ratatuille — planificador de cocina en casa

Ratatuille convierte tu IA (Claude o ChatGPT) en el planificador de comidas de tu casa. Cada semana te da:

- **un plan de comidas** para toda la familia, que dice quién come qué cada día, quién lo cocina y a qué hora, y de dónde sale cada ración;
- **recetas** pensadas para el tiempo, la mano y las máquinas de quien cocina, comprobadas para que den tiempo;
- **qué sacar y qué guardar** cada día;
- **la lista de la compra**, con solo lo que falta, por pasillos;
- **un panel** en el móvil para toda la casa.

Siempre parte de **lo que ya tienes en casa**, y se adapta a las edades, alergias, gustos y horarios de cada uno.

**Lo que te pide:** unos 15 minutos para configurarlo y **20 minutos a la semana**, todos el mismo día. Nada más es obligatorio.

👉 **[Guía del sistema](https://sagradoalex.github.io/ratatuille/)**: actores, flujos y casos de uso, para entenderlo antes de empezar. · **[Panel de ejemplo](https://sagradoalex.github.io/ratatuille/panel-ejemplo.html)**: lo que verá tu casa, con una familia inventada.

---

## Qué necesitas

- Una suscripción **de pago** a **Claude** o a **ChatGPT**.
- Esta carpeta, descargada (botón **Code → Download ZIP** en GitHub) y descomprimida.

## Cómo empezar

### Con Claude (recomendado: el panel se comparte con un enlace)

1. En claude.ai, crea un **proyecto** nuevo. Llámalo, por ejemplo, «Cocina de casa».
2. En **Instrucciones del proyecto**, pega el contenido de `sistema/ARRANQUE.md`.
3. En **Archivos del proyecto**, sube todos los archivos de la carpeta `sistema/` y de `sistema/plantillas/`.
4. Abre una conversación en el proyecto y escribe: **«Empezamos»**.

### Con ChatGPT

1. En ChatGPT, crea un **proyecto** nuevo.
2. En sus **instrucciones**, pega el contenido de `sistema/ARRANQUE.md`.
3. Sube los archivos de `sistema/` y de `sistema/plantillas/`.
4. Abre una conversación en el proyecto y escribe: **«Empezamos»**.

En ChatGPT, el panel es un archivo (`panel.html`) que descargas y mandas por WhatsApp a quien lo necesite.

### Si tu IA puede trabajar con carpetas

Si usas una IA que lee y escribe en una carpeta de tu ordenador (por ejemplo, Claude Code), ábrela en esta carpeta y escribe «Empezamos». Guardará tus datos en `mi-casa/` sin que tengas que subir nada.

## Cada semana

1. **El día de planificación**, escribe **«Plan de la semana»**. Te enseñará lo que cree que ha pasado y solo tendrás que corregir (5 minutos). Después te propone el plan y la lista (15 minutos).
2. **Si usas un proyecto de chat**, al terminar te dirá qué archivo actualizado tienes que **sustituir** en el proyecto. Hazlo: es su memoria.
3. **Compra** con la pestaña Compra del panel.

Todo lo demás es opcional: avisar de un cambio («Cambio: el miércoles somos 6»), tachar en la compra o que quien cocina marque lo que ha hecho.

## Qué hay en esta carpeta

| | |
|---|---|
| `sistema/ARRANQUE.md` | El texto para las instrucciones del proyecto |
| `sistema/INSTRUCCIONES.md` | Cómo piensa y trabaja Ratatuille. Está escrito para que lo entienda una persona |
| `sistema/ONBOARDING.md` | Las preguntas para configurar tu casa |
| `sistema/SEGURIDAD.md` | Conservación, alergias, bebés y niños |
| `sistema/ETAPAS.md` | Cómo cambia la comida con la edad |
| `sistema/DATOS.md` | Cómo se guardan tus datos |
| `sistema/plantillas/` | Plantillas de los datos y del panel (con datos de ejemplo de una familia inventada) |
| `mi-casa/` | **Tus datos.** Los crea Ratatuille. No están en el repositorio |

## Actualizar a una versión nueva

Sustituye la carpeta `sistema/` (y `LEEME.md`, `VERSION` y `CAMBIOS.md`) por la nueva. **No toques `mi-casa/`** ni tus archivos `estado.md`, `recetario.md` e `historico.md`. Ratatuille te dirá qué ha cambiado.

## Importante

Licencia: [CC BY-NC 4.0](LICENCIA.md). Puedes usarlo y compartirlo citando la fuente, sin fines comerciales.

Ratatuille **no es consejo médico ni nutricional**. Sigue las guías oficiales (AESAN) y unas reglas de seguridad prudentes, pero las alergias graves, las dietas por enfermedad y la alimentación de los bebés se deciden con vuestro profesional sanitario. **Las etiquetas de los productos las lees tú.**
