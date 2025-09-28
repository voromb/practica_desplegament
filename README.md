# Guía de Comandos - Práctica Git Flow

## Implementación completa de Git Flow

### Objetivo
Documentar todos los comandos Git utilizados en la implementación del proyecto siguiendo la metodología Git Flow.

---

## 🔧 Comandos Utilizados por Fases

### INICIO - Configuración del Repositorio

#### Usuario 1 - Crear y configurar el repositorio
```bash
# Clonar repositorio
git clone https://github.com/voromb/practica_desplegament.git
cd practica_desplegament

# Crear rama principal
git checkout -b main

# Crear rama de desarrollo
git checkout -b develop

# Subir rama main al remoto
git push -u origin main

# Subir rama develop al remoto
git push -u origin develop
```

---

### DESARROLLO - Features

#### Usuario 1 - Feature estructura inicial
```bash
# Posicionarse en develop
git checkout develop

# Crear feature branch
git checkout -b feature/estructura-inicial

# Crear estructura de carpetas
mkdir css js
touch index.html css/styles.css js/script.js

# Añadir cambios al staging
git add .

# Primer commit
git commit -m "feat(usuario1): crear estructura inicial del proyecto

- Añadido index.html con estructura básica
- Creadas carpetas css y js
- Implementado header, nav y footer"

# Verificar estado
git status

# Segundo commit después de más cambios
git add index.html
git commit -m "feat(usuario1): añadir contenido completo al home

- Descripción detallada del curso
- Estructura de navegación mejorada
- Footer con información adicional"

# Subir feature al remoto
git push -u origin feature/estructura-inicial

# Merge a develop (después del Pull Request en GitHub)
git checkout develop
git merge feature/estructura-inicial
git push origin develop
```

#### Usuario 2 - Features de contenido y atributos HTML
```bash
# Actualizar develop
git checkout develop
git pull origin develop

# FEATURE 1: Contenido HTML
git checkout -b feature/contingutHTML

# Hacer cambios en archivos...
git add .
git commit -m "feat(usuario2): implementar sección modificar contenido HTML

- Añadidos ejemplos de manipulación DOM
- Código JavaScript documentado
- Explicaciones detalladas de cada ejemplo"

git push -u origin feature/contingutHTML

# FEATURE 2: Atributos HTML
git checkout develop
git checkout -b feature/atributsHTML

# Hacer cambios en archivos...
git add .
git commit -m "feat(usuario2): implementar sección modificar atributos HTML

- Ejemplos de setAttribute y getAttribute
- Manipulación de clases con classList
- Casos de uso prácticos"

git push -u origin feature/atributsHTML
```

#### Usuario 3 - Feature estilos CSS
```bash
# Actualizar develop
git checkout develop
git pull origin develop

# Crear feature
git checkout -b feature/estilsCSS

# Hacer cambios en archivos...
git add .
git commit -m "feat(usuario3): implementar sección modificar estilos CSS

- Ejemplos de manipulación de style
- Cambios dinámicos de CSS con JavaScript
- Animaciones y transiciones"

git push -u origin feature/estilsCSS
```

#### Merge de todas las features
```bash
# Posicionarse en develop
git checkout develop

# Merge de cada feature
git merge feature/contingutHTML
git merge feature/atributsHTML
git merge feature/estilsCSS

# Push de develop actualizado
git push origin develop
```

---

### RELEASE - Versión 1.0

#### Usuario 3 - Crear release
```bash
# Desde develop crear release
git checkout develop
git checkout -b release/v1.0

# Crear archivo de versión
echo "v1.0" > VERSION

# Commit de release
git add VERSION
git commit -m "chore(usuario3): preparar release v1.0

- Versión estable con todas las secciones
- Lista para producción"

# Subir release
git push -u origin release/v1.0

# Merge a main
git checkout main
git pull origin main
git merge release/v1.0
git push origin main

# Crear tag
git tag -a v1.0 -m "Versión 1.0 - Primera release estable"
git push origin v1.0

# Back-merge a develop
git checkout develop
git merge main
git push origin develop
```

---

### HOTFIX - Correcciones urgentes

#### Usuario 1 - Hotfix para mejoras
```bash
# Desde main crear hotfix
git checkout main
git checkout -b hotfix/milloresV_1_0

# Hacer cambios urgentes en archivos...
git add .
git commit -m "hotfix(usuario1): mejoras en la sección de contenido v1.0

- Mejorado el diseño de la sección de contenido HTML
- Ajustes de estilos para mejor visualización
- Corrección de pequeños bugs"

# Subir hotfix
git push -u origin hotfix/milloresV_1_0

# Merge a main
git checkout main
git merge hotfix/milloresV_1_0
git push origin main

# Crear nuevo tag
git tag -a v1.0.1 -m "Versión 1.0.1 - Hotfix con mejoras"
git push origin v1.0.1

# Back-merge a develop
git checkout develop
git merge main
git push origin develop

# Eliminar rama hotfix
git branch -d hotfix/milloresV_1_0
git push origin --delete hotfix/milloresV_1_0
```

---

### DOCUMENTACIÓN - GitHub Pages

```bash
# Crear rama para documentación
git checkout -b gh-pages

# Crear archivo de documentación
touch README.md

# Crear carpeta para imágenes
mkdir media

# Añadir todo el contenido
git add .
git commit -m "docs: añadir documentación completa del proyecto"
git push -u origin gh-pages

# Si hay conflictos con archivos existentes
git stash push -m "guardando archivos temporales"
git checkout gh-pages
git stash pop  # recuperar si es necesario

# Para cambiar el archivo principal
mv ejercicio.md index.md  # GitHub Pages busca index.md primero
git add .
git commit -m "docs: configurar ejercicio como página principal"
git push origin gh-pages
```

---

## Comandos

### Gestión de ramas
```bash
# Ver todas las ramas (locales y remotas)
git branch -a

# Eliminar rama local
git branch -d nombre-rama

# Eliminar rama remota
git push origin --delete nombre-rama

# Cambiar entre ramas
git checkout nombre-rama

# Crear y cambiar a nueva rama
git checkout -b nueva-rama
```

### Sincronización
```bash
# Traer cambios del remoto
git pull origin nombre-rama

# Subir cambios al remoto
git push origin nombre-rama

# Establecer upstream al pushear
git push -u origin nombre-rama
```

### Gestión de commits
```bash
# Ver historial de commits
git log --oneline --graph --all

# Ver estado actual
git status

# Ver diferencias
git diff

# Deshacer último commit (mantiene cambios)
git reset --soft HEAD~1

# Deshacer cambios en archivo
git checkout -- archivo
```

### Tags
```bash
# Crear tag anotado
git tag -a v1.0 -m "Mensaje del tag"

# Subir tags al remoto
git push origin v1.0

# Subir todos los tags
git push origin --tags

# Ver todos los tags
git tag -l

# Eliminar tag local
git tag -d v1.0

# Eliminar tag remoto
git push origin --delete v1.0
```

### Resolución de problemas
```bash
# Si la rama local está desactualizada
git checkout main
git pull origin main

# Guardar cambios temporalmente
git stash
git stash pop  # recuperar cambios

# Forzar checkout (CUIDADO: pierde cambios)
git checkout -f nombre-rama

# Resolver conflictos de merge
git merge nombre-rama
# Editar archivos con conflictos
git add .
git commit -m "fix: resolver conflictos de merge"
```

---

## Resumen

```
main ─────────────────────────────────────► v1.0 ──────► v1.0.1
  │                                            ▲            ▲
  └──► develop ─────────────────────────────►  │            │
         │                                     │            │
         ├──► feature/estructura-inicial ──►   │            │
         │                                     │            │
         ├──► feature/contingutHTML ────────►  │            │
         │                                     │            │
         ├──► feature/atributsHTML ─────────►  │            │
         │                                     │            │
         ├──► feature/estilsCSS ────────────►  │            │
         │                                     │            │
         └──► release/v1.0 ─────────────────►  │            │
                                                            │
         hotfix/milloresV_1_0 ─────────────────────────────►
```

## 🔗 Enlaces del Proyecto

- **Repositorio**: https://github.com/voromb/practica_desplegament
- **GitHub Pages**: https://voromb.github.io/practica_desplegament/
- **Metodología**: [Git Flow](https://nvie.com/posts/a-successful-git-branching-model/)

---

## Importantes

1. **Conventional Commits**: Todos los commits siguen el formato:
   - `feat`: Nueva funcionalidad
   - `fix`: Corrección de bugs
   - `docs`: Documentación
   - `chore`: Tareas de mantenimiento
   - `hotfix`: Correcciones urgentes

2. **Formato de commit**:
   ```
   tipo(usuario): descripción breve
   
   - Detalle 1
   - Detalle 2
   ```

3. **Siempre hacer pull antes de empezar**: 
   ```bash
   git checkout develop
   git pull origin develop
   ```

4. **No trabajar directamente en main o develop**: Siempre usar feature branches

---

*Documentación creada para la Práctica 1 - Sistemas de Control de Versiones*
*Curso: Desplegament DAW*
*Repositorio: voromb/practica_desplegament*
