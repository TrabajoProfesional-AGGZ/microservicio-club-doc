# 🗄️ Gestión de Base de Datos y Migraciones (Alembic)

Este microservicio utiliza **SQLAlchemy** como ORM y **Alembic** para el control de versiones de la base de datos PostgreSQL. 
Nuestra base de datos utiliza un enfoque de aislamiento lógico, por lo que todas las tablas de este servicio viven exclusivamente dentro del esquema `ms_club`.

Sigue esta guía para configurar tu entorno local y entender el flujo de trabajo de las migraciones.

---

## 🛠️ 1. Configuración Inicial (Primer día)

Cuando clones este repositorio por primera vez, tu base de datos local (o tu rama de desarrollo en Neon) estará vacía. Para armar la estructura, sigue estos pasos:

1. **Configurar venv**
    Crea y activa tu entorno virtual:
    ```bash
    python -m venv .venv
    source .venv/bin/activate  # En Windows: .venv\Scripts\activate
    ```
2. **Instala las dependencias:**
   Asegúrate de tener tu entorno virtual activo e instala los requerimientos
   ```bash
   pip install -r requirements.txt
   ```
3. **Configura tu conexión a la base de datos:**
   Edita tu archivo `.env` con la URL de conexión a tu base de datos local o a tu rama de desarrollo en Neon.
    ```env
    DATABASE_URL=postgresql://usuario:contraseña@localhost:5432/tu_base_de_datos
    ```
4. **Crea la estructura inicial de la base de datos:**
   Ejecuta el siguiente comando para crear el esquema `ms_club` y las tablas iniciales:
   ```bash
    alembic upgrade head
    ```
    Esto aplicará todas las migraciones existentes y dejará tu base de datos lista para el desarrollo.

## 🔄 2. Flujo de Trabajo para Migraciones
Cuando necesites hacer cambios en la estructura de la base de datos (crear nuevas tablas, modificar columnas, etc.), sigue este flujo:
1. **Crea una nueva migración:**
   Usa el comando de Alembic para generar una nueva migración. Asegúrate de proporcionar un mensaje descriptivo.
   ```bash
   alembic revision -m "Descripción de la migración"
   ```
2. **Edita la migración:**
   Abre el archivo generado en `alembic/versions/` y define los cambios en la función `upgrade()` y, si es necesario, en `downgrade()`.
3. **Aplica la migración:**
   Ejecuta el comando para aplicar la migración a tu base de datos.
   ```bash
   alembic upgrade head
   ```
4. **Verifica los cambios:**
   Asegúrate de que los cambios se hayan aplicado correctamente revisando tu base de datos con una herramienta como `psql` o PgAdmin.
5. **Commit y Push:**
   Una vez que la migración esté funcionando correctamente, haz commit de tus cambios y push a tu rama de desarrollo.
   ```bash
   git add .
   git commit -m "Agrega nueva migración para [descripción]"
   git push origin tu-rama
   ```
