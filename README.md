# API Biblioteca

API REST con FastAPI para gestionar usuarios, autores, libros y préstamos.

## Requisitos

- Python 3.11+
- Dependencias de `requirements.txt`

## Inicio rápido

```powershell
py -m venv .venv
.\\.venv\\Scripts\\Activate.ps1
py -m pip install -r requirements.txt
Copy-Item .env.example .env
py -m alembic upgrade head
py -m uvicorn app.main:app --reload
```

Abra la documentación interactiva en `http://127.0.0.1:8000/docs`.

## Seguridad

Las rutas protegidas usan OAuth2/Bearer JWT. El primer usuario registrado recibe el rol `admin`; los siguientes se crean como `usuario`.

## API REST

- `GET /authors` y `GET /authors/{author_id}`: consultar autores.
- `POST /authors`, `PATCH /authors/{author_id}` y `DELETE /authors/{author_id}`: administrar autores (solo administrador).
- `GET /books`, `GET /books/{book_id}`: consultar libros, con búsqueda, filtro por ISBN y paginación.
- `POST /books`, `PUT /books/{book_id}` y `DELETE /books/{book_id}`: administrar libros (solo administrador).
- `POST /loans`: registrar un préstamo.
- `GET /loans/me`: consultar los préstamos del usuario autenticado.
- `GET /loans`: consultar todos los préstamos (solo administrador).
- `GET /loans/{loan_id}`: consultar un préstamo.
- `PATCH /loans/{loan_id}`: cambiar la fecha de devolución.
- `DELETE /loans/{loan_id}`: cancelar un préstamo activo.
- `POST /loans/{loan_id}/return`: devolver un préstamo.
- `PATCH /users/me`: actualizar el perfil del usuario autenticado.
- `GET /users`, `GET /users/{user_id}`, `PATCH /users/{user_id}` y `DELETE /users/{user_id}`: administración de usuarios.

## Pruebas

```powershell
py -m pytest -q
```
