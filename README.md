\# cameia-voz



Servicio de Voz de CAMEIA. Prepara transcripción, métricas de prosodia y síntesis de voz para las entrevistas sin conservar audio o video de forma permanente.



> \*\*Estado:\*\* repositorio base creado. No se informó un issue específico de implementación para el Sprint 1; las tecnologías descritas pertenecen a la línea base arquitectónica y requieren validación técnica antes de activarse.



\## Alcance actual



\- Reservar la fuente oficial del servicio especializado de voz.

\- Definir límites de privacidad, integración y evidencia.

\- Evitar incorporar dependencias pesadas en los servicios Java.



No debe comenzar una implementación completa sin issue, responsable, ambiente y criterios medibles.



\## Responsabilidades previstas



\- Transcribir audio con marcas de tiempo por palabra.

\- Calcular métricas acústicas y de prosodia aprobadas.

\- Sintetizar la voz del entrevistador según el modo autorizado.

\- Entregar resultados al servicio de Entrevista mediante un contrato versionado.

\- Procesar archivos de manera temporal y eliminarlos después de la operación.



No interpreta la calidad semántica de las respuestas ni persiste sesiones, audio o video.



\## Contexto arquitectónico



```mermaid

flowchart LR

&#x20;   E\[cameia-entrevista] --> V\[cameia-voz]

&#x20;   V -. transcripción prevista .-> W\[WhisperX]

&#x20;   V -. prosodia prevista .-> O\[openSMILE/eGeMAPS]

&#x20;   V -. entreno previsto .-> P\[Piper]

&#x20;   V -. simulación prevista .-> T\[Google Cloud Text-to-Speech]

&#x20;   V --> E

```



\## Tecnología prevista



| Elemento | Línea base |

|---|---|

| Lenguaje | Python; versión pendiente de fijar |

| Framework | FastAPI; versión pendiente de fijar |

| Transcripción | WhisperX/faster-whisper |

| Prosodia | openSMILE con eGeMAPS |

| Síntesis | Piper y Google Cloud Text-to-Speech según modo |

| Ejecución objetivo | Contenedor independiente en Cloud Run |



Las versiones deben fijarse en el manifiesto y lockfile que adopte el equipo después de una prueba reproducible.



\## Ejecución local



```text

Issue técnico: pendiente de crear/asignar

Instalación: pendiente

Pruebas: pendiente

Build: pendiente

Inicio: pendiente

Health check: pendiente

```



\## Configuración, privacidad y calidad



\- No guardar audios, videos, CV, tokens, credenciales ni `.env` en Git.

\- Procesar audio temporal con eliminación verificable.

\- Definir límites de tamaño, formato, duración, timeout y concurrencia antes de exponer el servicio.

\- Medir calidad, latencia, memoria y costo con muestra identificada.

\- No declarar GPU, modelos o capacidad hasta comprobar el ambiente real.



\## Contribución



\- `main` es estable y solo recibe promociones `develop → main` mediante Merge commit.

\- `develop` integra ramas `CA-<numero>-<descripcion-kebab-case>` mediante Squash.

\- Todo cambio ordinario entra mediante PR y revisión distinta del autor; la rama `CA-\*` se elimina después.



\## Cuándo actualizar este README



Actualizarlo en el mismo PR que cambie propósito, stack, comandos, variables, modelos, formatos, contrato con Entrevista, privacidad, métricas, despliegue o responsables. Si no aplica, justificarlo en el PR.



