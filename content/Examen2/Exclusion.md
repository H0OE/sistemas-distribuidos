
---
title: 🪴 Sección crítica
---
Existen múltiples características que un sistema distribuido debe de cumplir, como:
- confiabilidad
- disponibilidad
- apertura
- integridad de información

Dentro de la integridad de información, un problema relevante son las condiciones de competencia que se generan al tener recursos compartidos. Por esta razón, el tema de la **exclusión mutua** se vuelve de sumo interés. 

Este problema debe de ser resuelto para asegurar el acceso de forma correcta a los recursos compartidos, con la finalidad de mantener la integridad y consistencia en los datos.

## Deadlock
Cada proceso debe de pedir permiso para poder entrar en la región crítica y debe de liberarla después de haberla ocupado en su ejecución, para permitir, a otro proceso, entrar a la región crítica. Un algoritmo de exclusión mutua se define como el mecanismo

Para poder asegurar que solo un proceso esté en la región crítica, debe de asegurar que no existan deadlocks.

## Región crítica

