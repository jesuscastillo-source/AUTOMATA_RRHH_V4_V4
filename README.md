# Generador de Documentos RRHH — v4 (fuentes reales para el PDF)

⚠️ **Repo aparte, en desarrollo.** Construido sobre v3 (todo lo de antes:
cálculo de finiquito, negrita, Word/PDF separados). No reemplaces tu app en
producción con esta hasta probarla tú mismo.

## Qué cambia respecto a v3

El servidor no tenía Arial/Times New Roman reales (son de Microsoft, no se
pueden distribuir libremente) — usaba **Liberation Sans/Serif** como
sustituto, que a veces mide distinto en alto de línea y desbordaba el PDF a
una página extra, necesitando un ajuste más agresivo (5–18% de compresión)
para corregirlo.

Ahora la app trae incluidas (carpeta `fonts/`) **Arimo y Tinos** — fuentes
100% libres (licencia SIL Open Font License, sin restricciones, hechas por
Google específicamente para calzar en métricas con Arial y Times New Roman).
Se instalan solas la primera vez que arranca la app, sin depender de ningún
paquete del sistema ni de aceptar ninguna licencia externa.

**Resultado medido con tus documentos reales:**
- La Declaración Jurada de Fernanda necesitaba antes hasta 18% de ajuste
  para caber en 1 página — ahora solo necesita ~3%, mucho más parecido a
  cómo se ve en Word.
- Los 47 Contratos reales se generaron en 11.9s (antes ~15.9s) — más rápido,
  porque el sistema adaptativo necesita reintentar menos.
- Nada se rompió: mismo negrita, mismos campos completos, mismo cálculo de
  finiquito ($0 para Alicia, $1.006.370 para Elizabeth).

## Por qué no fuentes de Microsoft reales
Se evaluó instalar Arial/Times de verdad vía el paquete oficial
`ttf-mscorefonts-installer`, pero requiere aceptar una licencia de forma
interactiva durante la instalación — algo que `packages.txt` de Streamlit
Cloud no puede hacer (es solo una lista de paquetes, sin forma de responder
esa pregunta). Arimo/Tinos consiguen un resultado muy similar sin ese
problema, y sin depender de una descarga externa en cada despliegue.

---

