# JSON Test Data Generator

Este proyecto es una utilidad de consola escrita en Python que genera archivos de datos de prueba en formato JSON según un esquema configurable.

## 🚀 Características

- Soporte para múltiples tipos de datos (`str`, `int`, `timestamp`)
- Prefijos configurables para los nombres de archivo (`count`, `random`, `uuid`)
- Multiprocesamiento para mejorar el rendimiento
- Esquemas definibles en línea o desde archivo JSON
- Limpieza opcional del directorio de salida
- Configuración desde archivo `.ini`
- Logging configurable
- Modo consola (sin generar archivos)

## 📁 Estructura del proyecto

``` 
capstone_project/
├── src/
│   ├── main.py # Punto de entrada del programa
│   ├── config.py # Carga y validación de configuración
│   ├── generator.py # Lógica de generación de datos
│   ├── schema_parser.py # Interpretación del esquema
│   ├── utils.py # Funciones auxiliares
│   └── logger.py # Configuración de logging
├── tests/ # Pruebas automatizadas
│   ├── test_config.py # Test módulo config
│   ├── test_generator.py # Test módulo generator
│   ├── test_logger.py # Test módulo logger
│   ├── test_schema_parser.py # Test módulo schema_parser
│   └── test_utils.py # Test módulo utils
├── default.ini # Configuración por defecto
├── requirements.txt # Dependencias del proyecto
├── schema.json # Formato de datos
└── README.md
```

## ⚙️ Instalación

1. Clonar el repositorio:

```bash
git clone git@github.com:mrjesusenrique/capstone_project.git
o
git clone https://github.com/mrjesusenrique/capstone_project.git
cd capstone_project

pip install -r requirements.txt

python -m venv venv
venv\Scripts\activate       # En Windows
source venv/bin/activate    # En Linux/macOS

python src/main.py --data_schema path/a/esquema.json [opciones]

python src/main.py --data_schema schema.json --files_count 10 --lines_per_file 100 --multiprocessing 4

{
  "date": "timestamp:",
  "name": "str:rand",
  "type": "str:['client', 'partner', 'government']",
  "age": "int:rand(1, 90)"
}

[DEFAULT]
path_to_save_files = ./output
files_count = 1
file_name = data
file_prefix = count
lines_per_file = 10
multiprocessing = 1
```

## ⚙️ ¿Cómo usar?

Enviando parámetros customizados
```bash
python -m src.main --data_schema schema.json --files_count 5 --lines_per_file 10 --multiprocessing 2
```

Sin parámetros para que tome los valores por defecto en default.ini
```bash
python -m src.main --data_schema schema.json
```

Prueba en consola sin generar archivos con datos
```bash
python -m src.main --data_schema schema.json --files_count 0 --lines_per_file 3
```

## ⚙️ Tests

Test Schema Parser
```bash
pytest tests/test_schema_parser.py -v
```

Test Utils
```bash
pytest tests/test_utils.py -v
```

Test Generator
```bash
pytest tests/test_generator.py -v
```

Test Config
```bash
pytest tests/test_config.py -v
```

Test Logger
```bash
pytest tests/test_logger.py -v
```
