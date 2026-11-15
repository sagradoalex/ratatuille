# Ratatuille — seguridad alimentaria

> **Nivel 1 de la jerarquía: nada pasa por encima.** Ante la duda, siempre la opción prudente.
> Estas reglas no sustituyen a un profesional sanitario. Las alergias graves, las dietas por enfermedad y la alimentación del bebé se deciden con él.
> Fuentes al final. Donde no hay una cifra oficial, el valor es **prudente del sistema** y así se indica.

---

## 1. Conservación

| Regla | Valor | Origen |
|---|---|---|
| Enfriar lo cocinado | A la nevera **cuanto antes** y **nunca más de 2 horas** a temperatura ambiente. En raciones y en recipientes bajos, para que enfríe rápido | AESAN |
| Cocinado en nevera | **3 días** como máximo, contando el día en que se cocina | Prudente del sistema |
| Arroz y pasta cocinados | Enfriar enseguida y comer en **24 horas**. Recalentar una sola vez. *La toxina del* Bacillus cereus *no se destruye al recalentar: lo que la evita es enfriar rápido* | AESAN (riesgo); plazo prudente del sistema |
| Congelado casero | Hasta **3 meses** | Prudente del sistema (calidad) |
| Etiquetar lo que se guarda | Todo lo cocinado que se guarda, en la nevera o en el congelador, lleva etiqueta: **qué es, para quién (si va aparte), fecha de cocinado y fecha límite** | Prudente del sistema |
| Descongelar | **En la nevera**, desde la víspera. Nunca a temperatura ambiente | Práctica general |
| Lo descongelado | **No se vuelve a congelar** salvo que se cocine antes. Se come en 24 horas | Práctica general |
| Recalentar | Hasta que esté muy caliente en todo el plato. **Una sola vez** | Práctica general |
| Tupper sin nevera | Fuera del frío **2 horas como máximo**, o con **bolsa isotérmica y acumulador de frío**. Sin pescado, huevo poco hecho, mayonesa casera, lácteos frescos ni arroz | AESAN (2 h); prudente del sistema |
| Producto fresco | Lo que dice su fecha de caducidad. «Consumo preferente» es calidad, no seguridad | Etiquetado |

**Si un producto no está en la tabla**, se aplica la cifra más prudente de su grupo.

**En la simulación** (`INSTRUCCIONES.md` §9), el último bloque de cada sesión es **enfriar, repartir y guardar**, y tiene que caber en la ventana.

---

## 2. Alergias e intolerancias

1. **Filtran.** Una receta que lleva el alérgeno no entra para esa persona, ni como ingrediente ni como «un poco».
2. **Trazas.** Si la alergia es «ni trazas», también quedan fuera los productos que suelen llevarlas. La IA **no ve las etiquetas**, así que en la lista de la compra marca **«revisar etiqueta»** en lo que suele llevar trazas de un alérgeno de la casa: panadería y bollería, chocolate, cereales, galletas, salsas, embutidos.
3. **Leer la etiqueta es cosa de la familia.** La IA lo dice cuando hay alergias en casa.
4. **En la cocina**, la ración de quien tiene la alergia se prepara la primera o con utensilios limpios, y se guarda **aparte y etiquetada**.
5. **Los 14 alérgenos de declaración obligatoria** (para revisar recetas): gluten, crustáceos, huevo, pescado, cacahuete, soja, leche, frutos de cáscara, apio, mostaza, sésamo, sulfitos, altramuces y moluscos.

---

## 3. Bebés y niños

Las reglas por edad están en `ETAPAS.md`. Las que nunca se saltan:

| Regla | Hasta | Origen |
|---|---|---|
| **Sin sal ni azúcar añadidos.** Su ración se aparta **antes de sazonar** | 12 meses | AEP / AEPap |
| **Sin miel** (riesgo de botulismo) | 12 meses | AEP, OMS |
| **Sin leche de vaca como bebida principal** | 12 meses | AEP |
| **Sin espinaca ni acelga** (nitratos). Si se usan, no más del 20 % del puré | 12 meses | AESAN |
| **Espinaca o acelga: una ración al día como mucho**, y ninguna con una infección intestinal | 1–3 años | AESAN |
| **Sin pez espada, tiburón, atún rojo ni lucio** (mercurio) | 10 años | AESAN (2019) |
| **Esos cuatro pescados: 120 g al mes como mucho** | 10–14 años | AESAN (2019) |
| **Sin frutos secos enteros ni en trozos** (atragantamiento). **Sí molidos o en crema**, sin sal ni azúcar, desde los 6 meses | 6 años (prudente: las guías dicen entre 3 y 6) | AEPap y guías autonómicas |
| **Alimentos redondos y duros**: uvas, tomates cherry y similares, **cortados a lo largo en cuartos**; nada de palomitas ni caramelos duros | 5 años | Recomendación pediátrica general |
| **Estrenos**: un alimento nuevo cada pocos días, en casa y a una hora en que se le pueda vigilar; **nunca el mismo día que una receta nueva** | Mientras haya estrenos | Práctica pediátrica |
| **Alérgenos ya probados**: mantenerlos en la dieta con regularidad | — | AEP |

**La última palabra es del pediatra.** Si la familia dice que el pediatra ha indicado otra cosa, manda lo que diga el pediatra, y se apunta en la configuración con la fecha.

---

## 4. Embarazo

Si alguien de la casa está embarazada, la IA lo pregunta en la parte 2 del onboarding y aplica las recomendaciones de la AESAN para el embarazo (entre otras: sin pez espada, tiburón, atún rojo ni lucio; nada crudo o poco hecho de carne, pescado o huevo; lácteos pasteurizados). Avisa de que **la referencia es su matrona o su médico**.

---

## Fuentes

- AESAN — *Bacillus cereus*: https://www.aesan.gob.es/AECOSAN/web/seguridad_alimentaria/subdetalle/Bacillus_cereus.htm
- AESAN — Recomendaciones de consumo de pescado por mercurio (2019), recogidas por la AEP: https://static.aeped.es/cailm_recomendacionesaecosan_mercurio_6d78a38eb8.pdf
- AEP — Recomendaciones sobre alimentación complementaria (2018): https://www.aeped.es/sites/default/files/documentos/recomendaciones_aep_sobre_alimentacio_n_complementaria_nov2018_v3_final.pdf
- AEP En Familia — Alimentación complementaria: https://enfamilia.aeped.es/edades-etapas/alimentacion-complementaria-0
- AEPap — Alimentación de 6 a 24 meses: https://aepap.org/wp-content/uploads/2024/02/PSI-Alimentacion-de-6-a-24-meses.pdf

*Revisado el 2026-11-15. Revisar contra las fuentes en cada versión mayor del sistema.*
