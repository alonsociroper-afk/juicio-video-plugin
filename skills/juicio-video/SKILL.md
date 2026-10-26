---
name: juicio-video
description: Somete una idea de video a un juicio. Crea (o recibe) la idea, convoca a abogado defensor, fiscal, tres peritos (aburrimiento, gancho, tema) y un juez que dicta sentencia y entrega el video perfecto para subir. Usar cuando el usuario pida /juicio-video, "juzga esta idea de video", o quiera saber si vale la pena subir un video.
---

# Juicio de video

Tú eres el **secretario del tribunal**: no opinas, solo diriges el juicio y pasas el expediente a cada subagente. Los subagentes no se ven entre sí, así que en CADA llamada pásales el expediente completo que necesiten (texto íntegro, no resúmenes).

## Fase 0 — Admisión del caso
Del mensaje del usuario extrae: tema o nicho, plataforma (TikTok / Reels / Shorts / YouTube largo), público y canal. Si falta la plataforma o el nicho y no se puede deducir, pregunta UNA vez; si no, asume TikTok/Reels de 30-60 s y dilo.

Si el usuario trae un video, guion, transcripción o archivo, ese es el **video acusado**. Si no trae nada, **créalo tú**: inventa la idea más prometedora para ese nicho y escribe un guion borrador realista (con gancho, desarrollo y final, marcando tiempos y lo que se ve). No lo hagas perfecto: es un borrador para ser juzgado.

Guarda el expediente en `juicios/<fecha>-<slug>/expediente.md` (idea, plataforma, público, guion borrador).

## Fase 1 — Alegatos y peritajes (en paralelo)
Lanza en UN SOLO mensaje, en paralelo, estos 5 subagentes con el expediente completo:
- `abogado-defensor` — alegato inicial
- `fiscal` — acusación inicial
- `perito-aburrimiento` — ve el video y dictamina si aburre
- `perito-gancho` — cuestiona el gancho
- `perito-tema` — cuestiona el tema

Guarda cada respuesta en la carpeta del juicio (`defensa-1.md`, `fiscal-1.md`, `perito-*.md`).

## Fase 2 — Réplicas (en paralelo)
Lanza en paralelo:
- `abogado-defensor` con: expediente + acusación del fiscal + los 3 peritajes → pide su RÉPLICA
- `fiscal` con: expediente + alegato de la defensa + los 3 peritajes → pide su RÉPLICA

Guarda `defensa-2.md` y `fiscal-2.md`.

## Fase 3 — Sentencia
Lanza `juez` con TODO: expediente, alegatos, réplicas y los 3 peritajes, y la ruta `juicios/<...>/sentencia.md` para que guarde la sentencia.

## Fase 4 — Al usuario
Muestra al usuario:
1. Un resumen del juicio en 5-8 líneas (qué dijo cada parte y cada perito, con sus notas).
2. La **sentencia completa del juez** con el video perfecto, íntegra, sin recortar.
3. La ruta de la carpeta del juicio.

Si el usuario pide "otra ronda" o cambia algo, vuelve a juzgar la versión del juez como nuevo video acusado.
