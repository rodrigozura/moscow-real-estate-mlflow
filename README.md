# Parcial: entorno de trabajo

Este proyecto utiliza un entorno virtual de Python y MLflow para registrar experimentos localmente.

## Requisitos

- Windows
- Python 3.12 instalado
- PowerShell

## Crear el entorno virtual

Abrir PowerShell dentro de la carpeta `Parcial`:

```powershell
py -3.12 -m venv .venv
```

Si PowerShell bloquea la activación de scripts, habilitarla solo para la sesión actual:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

## Activar el entorno

```powershell
./.venv/Scripts/Activate.ps1
```

Cuando el entorno esté activo, la terminal mostrará `(.venv)` al comienzo de la línea.

## Instalar dependencias

Con el entorno activado:

```powershell
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

Verificar la instalación:

```powershell
python -c "import mlflow; print(mlflow.__version__)"
```

## Levantar MLflow

Con el entorno activado y ubicado en la carpeta `Parcial`, ejecutar:

```powershell
mlflow server --host 127.0.0.1 --port 5000 --backend-store-uri sqlite:///mlflow.db
```

Abrir la interfaz en:

```text
http://127.0.0.1:5000
```

El archivo `mlflow.db` guardará la información de los experimentos. El servidor debe permanecer abierto mientras se ejecutan los notebooks o scripts que registran runs.

Para detenerlo, presionar `Ctrl+C` en la terminal donde está ejecutándose.

## Usar MLflow desde Python

Los notebooks o scripts deben apuntar al servidor local:

```python
import mlflow

mlflow.set_tracking_uri("http://127.0.0.1:5000")
```

## Próximas sesiones

Cada vez que se vuelva a trabajar en el proyecto:

```powershell
cd "C:/Users/Rodrigo/Documents/Facultad/Analisis de datos/Parcial"
./.venv/Scripts/Activate.ps1
mlflow server --host 127.0.0.1 --port 5000 --backend-store-uri sqlite:///mlflow.db
```
