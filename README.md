# Caso Clínica Santa Lucía

**Sergio Colque Ponce**
Código: 2022073503
SI-084 · Auditoría de Sistemas · Unidad II

Plan de auditoría del canal digital de la Clínica Santa Lucía y evidencias del reconocimiento.

## Archivos

- [Plan en Word](SI084-EXPRAC-U2-ColquePonceSergio.docx)
- [Plan en PDF](SI084-EXPRAC-U2-ColquePonceSergio.pdf)
- [PLAN.md](PLAN.md)
- [Evidencias E1 a E8](evidencias/)
- [Documentos del caso](documentos/)

## Ejecutar

Desde la carpeta del proyecto:

```bash
docker compose up -d --wait
docker compose ps
```

| Servicio | Dirección |
|---|---|
| Portal | http://127.0.0.1:8080/ |
| Citas | http://127.0.0.1:8080/citas/ |
| Pruebas | http://127.0.0.1:8081/ |
| API | http://127.0.0.1:8088/ |

Para detener los servicios:

```bash
docker compose down
```

## Verificar las evidencias

En Git Bash:

```bash
sha256sum -c evidencias/SHA256SUMS.txt
```
