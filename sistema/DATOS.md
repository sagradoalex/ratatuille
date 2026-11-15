# Ratatuille — cómo se guardan los datos de la casa

> Los datos de cada casa viven en `mi-casa/`, **nunca en `sistema/`**: así se puede actualizar el sistema sin tocarlos. Este documento fija su formato, para que cualquier IA, y cualquier versión futura del sistema, los entienda igual.
> Las plantillas vacías están en `sistema/plantillas/`.

---

## 1. Modo completo: la carpeta `mi-casa/`

```
mi-casa/
├── configuracion.md        ← Todo lo del onboarding (plantilla: configuracion.md)
├── inventario.json         ← Lo que hay en casa (plantilla: inventario.json)
├── productos.json          ← Pasillo, formato de venta y conservación de cada producto
├── recetas/                ← Una ficha por receta (plantilla: receta.md), nombre-en-minusculas.md
├── semanas/AAAA-MM-DD.json ← Una por semana, por la fecha de su primer día (plantilla: semana.json)
├── compras.md              ← Histórico de listas y de lo que se compró
├── registro.md             ← Una nota por semana: qué pasó y qué se aprendió
└── panel.html              ← El panel publicado (plantilla: panel.html)
```

## 2. Modo chat: tres archivos

| Archivo | Qué lleva | Plantilla |
|---|---|---|
| `estado.md` | Configuración + inventario + productos + semana en curso (con su plan, sus sesiones y su compra) | `estado.md` |
| `recetario.md` | Índice arriba y todas las fichas debajo | `recetario.md` |
| `historico.md` | Una línea por semana y lo aprendido | `historico.md` |

Al terminar una conversación en la que algo cambió, la IA entrega **completo** cada archivo modificado, y solo esos.

---

## 3. Reglas de los datos

1. **Fechas** en formato `AAAA-MM-DD`; horas, `HH:MM` en 24 horas.
2. **Nada derivable se guarda**: ni edades, ni días que le quedan a un producto, ni «hace 3 semanas». Se guardan fechas y se calcula.
3. **Estado de cada dato de configuración**: `por defecto` o `confirmado`.
4. **Estado de cada artículo del inventario**: `ok` o `por confirmar`.
5. **Cantidades del inventario en su unidad natural** («2 pechugas», «medio paquete»), con una equivalencia aproximada en gramos o mililitros cuando sirva para cocinar (`"aprox_g": 400`).
6. **Básicos de despensa** (aceite, sal, especias, vinagre…): sin cantidad, con `hay`, `poco` o `no hay`.
7. **Nombres de personas**: el nombre o apodo, igual en todos los archivos.

---

## 4. `inventario.json`

```json
{
  "actualizado": "2026-11-19",
  "articulos": [
    {
      "producto": "pechuga de pollo",
      "cantidad": "2 piezas",
      "aprox_g": 400,
      "lugar": "congelador",
      "entrada": "2026-11-14",
      "cocinado": false,
      "raciones": null,
      "reservado_para": null,
      "estado": "ok"
    },
    {
      "producto": "lentejas con verduras",
      "cantidad": "3 tuppers",
      "lugar": "congelador",
      "entrada": "2026-11-09",
      "cocinado": true,
      "raciones": 3,
      "reservado_para": null,
      "estado": "ok"
    }
  ],
  "basicos": { "aceite de oliva": "hay", "sal": "hay", "arroz": "poco", "comino": "no hay" }
}
```

- `lugar`: `congelador`, `nevera` o `despensa`.
- `cocinado`: `true` si es comida **ya preparada** (tuppers, sobras, guisos), esté en la nevera o en el congelador; entonces `raciones` dice cuántas. Lo preparado se usa antes que cocinar más.
- `reservado_para`: la fecha y la comida de la semana en curso que lo necesita, o `null`. Lo reservado no se usa en el plan nuevo.
- La **caducidad no se guarda**: se calcula con `entrada` y `productos.json`, o con la fecha de la etiqueta si el gestor la da (`"caduca": "2026-11-21"`).

## 5. `productos.json`

```json
{
  "pechuga de pollo": {
    "pasillo": "carne y pescado",
    "formato_venta": "bandeja de 500 g",
    "temporada": "todo el año",
    "dias": { "nevera": 2, "congelador": 90 },
    "alergenos": []
  },
  "pan de molde": {
    "pasillo": "panadería",
    "formato_venta": "paquete de 450 g",
    "temporada": "todo el año",
    "dias": { "despensa": 7 },
    "alergenos": ["gluten"],
    "trazas_habituales": ["frutos de cáscara", "sésamo", "soja"]
  }
}
```

Crece con cada producto nuevo. Los días se ponen siempre con el criterio de `SEGURIDAD.md`, y ante la duda, el más prudente.

## 6. Receta: `recetas/nombre.md`

Ver `plantillas/receta.md`. La cabecera YAML lleva lo que usa el planificador; el cuerpo, lo que lee el cocinero. **Cada paso lleva tiempo de manos, tiempo de espera y recurso** (máquina o fuego): sin eso no se puede simular.

## 7. Semana: `semanas/AAAA-MM-DD.json`

Ver `plantillas/semana.json`. Guarda:
- `inicio` y `fin`;
- `comidas`: por día y comida, quién come y de dónde sale cada ración;
- `sesiones`: día, cocinero, inicio, fin, elaboraciones y línea de tiempo simulada;
- `reparto`: víspera, antes de cocinar, al servir, al terminar;
- `plan_b` por día, e `ideas`;
- `comprobador`: el resultado de C1–C14;
- `compra`: la lista generada;
- `cierre`: lo que pasó de verdad, se rellena en la actualización (qué se hizo, qué sobró, notas).

## 8. Datos del panel

El panel (`plantillas/panel.html`) **no calcula nada**: pinta lo que recibe. La IA rellena **solo** el bloque `<script id="datos" type="application/json">` con esta estructura (ver el ejemplo completo dentro de la plantilla):

| Campo | Qué es |
|---|---|
| `casa`, `actualizado`, `plataforma` | Nombre de la casa (sin apellidos), fecha y hora de la última publicación, y `claude` o `chatgpt` |
| `semana` | `inicio`, `fin` y `titulo` |
| `dias[]` | Por día: `fecha`, `ayer_listo[]`, `comidas[]` (cada una con `comida`, `hora` y `raciones[]` de `quien`, `plato`, `origen` y `aparte`), `sesiones[]` (`cocinero`, `inicio`, `fin`, `pasos[]` con `hora`, `paso`, `recurso` y `manos`), `guardar[]`, `manana[]`, `plan_b` e `ideas[]`. Un día sin nada: `"libre": "texto"` |
| `recetas[]` | Fichas resumidas: `nombre`, `tipo`, `manos_min`, `total_min`, `maquina`, `raciones`, `estado`, `tiempos`, `en_semana`, `ingredientes[]`, `pasos[]`, `adaptaciones[]`, `conservacion` |
| `compra` | `id` (único por compra), `titulo`, `fecha`, `tienda`, `revisar_en_casa[]` y `pasillos[]`, cada uno con `nombre` y `articulos[]` (`id`, `nombre`, `cantidad`, `para`, `etiqueta`) |
| `historico[]` | Por semana: `semana`, `planificado`, `hecho` y `nota` |
| `inventario` | `preparado[]` (comida ya hecha, esté donde esté), `nevera[]`, `congelador[]` y `despensa[]`, cada uno con `nombre`, `cantidad` y `estado` (`ok`, `pronto`, `urgente` o `por confirmar`). En `preparado`, la `cantidad` dice también dónde está («3 raciones, congelador») |
| `como_funciona` | `calendario[]` (`dia`, `que`, `quien`, `duracion`), `papeles[]`, `obligatorio[]`, `opcional[]`, `si_pasa[]` (`situacion`, `que_hacer`), `cambiar[]` y `primeras_semanas[]` |

En `raciones[]`, `aparte: true` marca a quien come distinto (bebé, alergia): el panel lo pinta en su propia línea.
