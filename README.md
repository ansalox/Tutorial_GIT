# Subir un proyecto a GitHub por primera vez

Una vez configurado Git (`user.name` y `user.email`), el siguiente paso es conectar nuestro proyecto local con un repositorio en GitHub.

---

## Paso 1. Inicializar Git

Convierte la carpeta actual en un repositorio Git.

```bash
git init
```

> Este comando crea la carpeta oculta `.git`, donde Git almacenará todo el historial del proyecto.

---

## Paso 2. Verificar el estado del proyecto

Permite conocer qué archivos están siendo rastreados y cuáles aún no.

```bash
git status
```

Ejemplo de salida:

```text
On branch main

No commits yet

Untracked files:
    index.html
    app.js
```

---

## Paso 3. Agregar el repositorio remoto

Conecta el proyecto local con el repositorio creado en GitHub.

```bash
git remote add origin https://github.com/Usuario/MiProyecto.git
```

### Explicación

- **origin** → Nombre que recibe el repositorio remoto.
- **https://github.com/Usuario/MiProyecto.git** → URL del repositorio en GitHub.

---

## Paso 4. Verificar el repositorio remoto

Confirma que el repositorio remoto quedó correctamente configurado.

```bash
git remote -v
```

Ejemplo:

```text
origin  https://github.com/Usuario/MiProyecto.git (fetch)
origin  https://github.com/Usuario/MiProyecto.git (push)
```

---

## Paso 5. Agregar todos los archivos

Prepara todos los archivos para el próximo commit.

```bash
git add .
```

> El punto (`.`) significa **todos los archivos de la carpeta actual**.

---

## Paso 6. Crear el primer commit

Guarda una fotografía del estado actual del proyecto.

```bash
git commit -m "Primer commit"
```

---

## Paso 7. Enviar el proyecto a GitHub

Sube el proyecto al repositorio remoto.

```bash
git push -u origin main
```

### Explicación

- **push** → Envía los cambios.
- **-u** → Vincula la rama local con la rama remota.
- **origin** → Nombre del repositorio remoto.
- **main** → Rama que será enviada.

Una vez ejecutado este comando, en los siguientes envíos solo necesitarás:

```bash
git push
```

---

#  Trabajar con una rama diferente de `main`

Una buena práctica es no desarrollar directamente sobre la rama principal.

---

## Paso 1. Crear una nueva rama

```bash
git checkout -b desarrollo
```

o utilizando el comando moderno de Git:

```bash
git switch -c desarrollo
```

Este comando:

- Crea la rama.
- Cambia automáticamente a ella.

---

## Paso 2. Verificar la rama actual

```bash
git branch
```

Ejemplo:

```text
* desarrollo
  main
```

El asterisco (`*`) indica la rama actual.

---

## Paso 3. Realizar cambios

Edita normalmente tus archivos.

---

## Paso 4. Agregar los cambios

```bash
git add .
```

---

## Paso 5. Crear un commit

```bash
git commit -m "Se agrega módulo de autenticación"
```

---

## Paso 6. Subir la rama a GitHub

```bash
git push -u origin desarrollo
```

A partir de este momento bastará con ejecutar:

```bash
git push
```

---

#  Subir cambios al día siguiente

Supongamos que ayer ya subiste el proyecto y hoy realizaste nuevas modificaciones.

---

## Paso 1. Revisar el estado

```bash
git status
```

---

## Paso 2. Ver exactamente qué cambió

```bash
git diff
```

Este comando muestra línea por línea las modificaciones realizadas.

---

## Paso 3. Preparar los archivos

```bash
git add .
```

---

## Paso 4. Crear un nuevo commit

```bash
git commit -m "Se corrige validación del formulario"
```

---

## Paso 5. Descargar los cambios del servidor (recomendado)

Si trabajas en una rama diferente:

```bash
git pull origin desarrollo
```

Si trabajas directamente sobre `main`:

```bash
git pull origin main
```

---

## Paso 6. Subir los cambios

```bash
git push
```

---

#  Revertir cambios

Git permite deshacer cambios dependiendo del momento en el que te encuentres.

---

## Caso 1. Cancelar un `git add`

Si agregaste archivos por error:

```bash
git reset .
```

Los archivos seguirán existiendo, simplemente dejarán de estar preparados para el commit.

---

## Caso 2. Ver los cambios antes del commit

```bash
git diff
```

Muy útil para revisar qué será enviado.

---

## Caso 3. Modificar el último commit

Si olvidaste agregar un archivo o deseas cambiar el mensaje del commit:

```bash
git commit --amend
```

---

## Caso 4. Eliminar un archivo del repositorio

```bash
git rm nombreArchivo.txt
```

Después deberás realizar un nuevo commit.

---

#  Obtener cambios del repositorio remoto

## Descargar cambios sin modificar tu rama

```bash
git fetch origin main
```

Solo descarga la información del servidor.

No modifica tu proyecto local.

---

## Descargar y fusionar cambios

```bash
git pull origin main
```

Este comando equivale a ejecutar:

```text
git fetch
+
git merge
```

---

#  Administración de ramas

## Ver todas las ramas locales

```bash
git branch
```

---

## Crear una nueva rama

```bash
git checkout -b desarrollo
```

---

## Eliminar una rama

```bash
git branch -D desarrollo
```

---

# 🔀 Rebase

El rebase permite mover los commits de una rama encima de otra para mantener un historial más limpio.

---

## Ejecutar un rebase

```bash
git rebase main
```

---

## Continuar después de resolver conflictos

```bash
git rebase --continue
```

---

## Omitir un commit conflictivo

```bash
git rebase --skip
```

---

## Cancelar completamente el rebase

```bash
git rebase --abort
```

---

#  Administración de repositorios remotos

## Ver los repositorios configurados

```bash
git remote -v
```

---

## Ver información detallada del remoto

```bash
git remote show origin
```

---

## Cambiar la URL del repositorio remoto

```bash
git remote set-url origin https://github.com/Usuario/NuevoRepositorio.git
```

---

## Eliminar el repositorio remoto

```bash
git remote remove origin
```

También puede escribirse como:

```bash
git remote rm origin
```

---

## Limpiar referencias remotas eliminadas

```bash
git remote prune origin
```

---

# 📜 Historial de commits

## Ver el historial resumido

```bash
git log --graph --oneline --decorate
```

Ejemplo:

```text
* 1f82f8a Se agrega login
* b23d1aa Primer commit
```

---

#  Tags (Versiones)

Los tags permiten marcar versiones importantes del proyecto.

---

## Crear un tag

```bash
git tag -a v0.0.1 -m "Primera versión"
```

---

## Ver todos los tags

```bash
git tag
```

---

## Ver la información de un tag

```bash
git show v0.0.1
```

---

## Enviar los tags a GitHub

```bash
git push --tags
```

---

#  Flujo de trabajo recomendado

## Primera vez

```text
git init
       │
       ▼
git remote add origin URL
       │
       ▼
git status
       │
       ▼
git add .
       │
       ▼
git commit -m "Primer commit"
       │
       ▼
git push -u origin main
```

---

## Trabajo diario

```text
git pull
     │
     ▼
Editar archivos
     │
     ▼
git status
     │
     ▼
git diff
     │
     ▼
git add .
     │
     ▼
git commit -m "Descripción del cambio"
     │
     ▼
git push
```
