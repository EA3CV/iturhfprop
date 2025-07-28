# QSO Propagation Predictor

Servidor de predicción de propagación HF basado en [ITURHFProp](https://github.com/EA3CV/iturhfprop), Redis y fuentes auxiliares como RBN y PSKReporter.

## 🚀 Funcionalidad

Este servidor expone una API HTTP (`/predict`) que recibe información de un posible QSO (indicativos, coordenadas, hora, frecuencia, modo) y devuelve una puntuación estimada de éxito, considerando múltiples factores:

- Modelado de propagación con ITURHFProp.
- Rutas de propagación por Short Path (SP) y Long Path (LP).
- Línea gris (Greyline).
- PSKReporter (detección reciente).
- Spots del Reverse Beacon Network (RBN).
- Caché con Redis opcional para mejorar rendimiento.

---

## 📦 Requisitos

- Docker + Docker Compose
- Acceso a red para usar PSKReporter y RBN

---

## 🔧 Configuración (`config.json`)

```json
{
  "redis_enabled": true,
  "redis_host": "itur_redis",
  "redis_port": 6379,
  "use_greyline": true,
  "use_rbn": true,
  "use_rbn_telnet": true,
  "use_pskreporter": true,
  "debug": false,
  "greyline_bonus": 10,
  "cache_ttl_seconds": 300,
  "rbn_ttl_seconds": 1200,
  "rbn_telnet_timeout": 180,
  "enable_mode_thresholds": true,
  "itur_defaults": {
    "tx": { "txp": 100, "ant": "D", "txg": 0 },
    "rx": { "ant": "D", "rxg": 0, "sdbw": -114 }
  },
  "rbn_cw": {
    "host": "telnet.reversebeacon.net",
    "port": 7000,
    "user": "EA3CV"
  },
  "rbn_digital": {
    "host": "telnet.reversebeacon.net",
    "port": 7001,
    "user": "EA3CV"
  }
}
