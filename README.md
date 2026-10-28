# Examen práctico de auditoría de sistemas

Sergio Colque Ponce · 2022073503 · SI-084 · Unidad II

Este repositorio conserva la infraestructura original del caso y contiene el plan de auditoría y sus ocho evidencias. El reconocimiento no ejecuta las pruebas futuras del plan.

## Qué se entrega

- `PLAN.md`: observaciones, alcance, objetivos, enfoque, seis procedimientos y cinco riesgos.
- `evidencias/E1_*.txt` a `E8_*.txt`: salidas reales del reconocimiento.
- `evidencias/SHA256SUMS.txt`: sellos de integridad verificables con `sha256sum -c evidencias/SHA256SUMS.txt` desde esta carpeta.
- Etiqueta `examen-u2`, que identifica la entrega.
- PDF `SI084-EXPRAC-U2-ColquePonceSergio.pdf` para subir manualmente al aula virtual.
- Word editable `SI084-EXPRAC-U2-ColquePonceSergio.docx`, cumplimentado sobre la plantilla original `PLAN.docx`, con su carátula, escudos, cabecera y pie. El PDF actual se exportó directamente de este Word. Ambos están en la rama `main`; la etiqueta original `examen-u2` conserva el reconocimiento y sus evidencias.

## Levantar los servicios y mostrarlos al docente

En Git Bash, dentro de esta carpeta:

```bash
docker compose up -d --wait
docker compose ps
```

| Servicio | Dirección local | Qué mostrar |
|---|---|---|
| Portal | http://127.0.0.1:8080/ | Página principal y formularios sin enviarlos. |
| Citas del portal | http://127.0.0.1:8080/citas/ | Campos y método GET mediante código fuente, sin registrar datos. |
| Pruebas | http://127.0.0.1:8081/ | Etiqueta de pruebas; comentarios mediante código fuente. |
| Raíz de API | http://127.0.0.1:8088/ | JSON que anuncia servicio, versión, entorno y endpoints. No abrir /v1/. |

El frontend es la parte visible del portal. El paquete representa el backend mediante una raíz de API estática servida por nginx. No incluye un backend funcional con base de datos, ni PHP/WordPress/Express ejecutándose por el solo hecho de anunciar esos nombres. No se debe desarrollar otro sistema ni corregir las debilidades: son el material a reconocer y planificar.

El entorno 8081 contiene solo su página principal. Sus enlaces relativos a `/citas/` y `/resultados/` conservan ese puerto y apuntan a rutas ausentes; un 404 allí no indica que Docker esté detenido. Los formularios del portal están en 8080. La infraestructura no se modifica.

## Explicación breve para sustentar

1. «Levanté los tres servicios originales con Docker y los limité a localhost».
2. «Reconocí tres aplicaciones; el proveedor declaró una. Guardé ocho evidencias y sus hashes».
3. «Observé GET con síntomas, respaldos listados y protecciones ausentes; no envié formularios, descargué copias ni consulté /v1/».
4. «El plan propone seis procedimientos futuros; el primero examinará autorización y caché para investigar el resultado ajeno de septiembre».
5. «Estas observaciones no prueban explotación ni describen por sí solas la configuración histórica. La ejecución requiere autorización y réplica funcional».

Lea y revise personalmente el plan antes de presentarlo: el enunciado penaliza escritura de IA sin revisión. La sustentación debe explicar las cifras y límites de cada evidencia.

## Contradicciones del enunciado que debe aclarar el docente

- E8 pide consultar 443, pero el alcance escrito solo autoriza 8080-8090. No se ejecutó 443; consta como pendiente, sin inventar HTTP 000.
- El texto indica duración de 40 minutos y después vencimiento a los 100 minutos. Confirme el plazo de la sesión.
- PLAN.docx pide narrativa en tercera persona/futuro, límites de palabras y pasos imperativos. El Word completado respeta la estructura II-VII y Anexo A de esa plantilla. Se mantienen además PLAN.md y las evidencias exigidas por el enunciado.

## Cerrar y restaurar el laboratorio anterior

Después de que el docente compruebe los servicios:

```bash
docker compose down
docker start si084_dvwa
```

En esta máquina se detuvo temporalmente `NIApplicationWebServer` para liberar 8080 y `si084_dvwa` para liberar 8081, con autorización del alumno. Para restaurar el servicio de Windows, después de apagar la clínica, abra PowerShell como administrador:

```powershell
Start-Service NIApplicationWebServer
```

No se cambió el inicio automático del servicio ni se eliminó el contenedor del laboratorio anterior.
