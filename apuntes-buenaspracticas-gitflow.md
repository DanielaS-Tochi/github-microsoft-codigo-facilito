# Buenas prácticas & 🔀 GitHub Flow vs GitFlow  

## 📚 Contenido

### 📝 Buenas prácticas
- [Buenas prácticas en commits](#-buenas-prácticas-en-commits)  
- [Conventional Commits](#-conventional-commits)  

### 🚀 GitFlow
- [¿Qué es GitFlow?](#-qué-es-gitflow)  
- [Tipos de ramas en GitFlow](#-tipos-de-ramas-en-gitflow)  
- [Ejemplo práctico de uso](#-ejemplo-práctico-de-uso)  
- [¿Y la rama staging?](#-y-la-rama-staging)  
- [Tabla resumen de ramas](#-tabla-resumen-de-ramas)  

### 🔀 GitHub Flow
- [¿Qué es GitHub Flow?](#-qué-es-github-flow)  
- [Flujo de trabajo en GitHub Flow](#-flujo-de-trabajo-en-github-flow)  

### ⚖️ Comparaciones y recomendaciones
- [GitHub Flow vs GitFlow](#-github-flow-vs-gitflow)  
- [¿Qué estrategia me conviene usar?](#-qué-estrategia-me-conviene-usar)  

---

## 📝 Buenas prácticas en commits

- 🧠 Mensajes claros y descriptivos.  
- 🧩 Commits pequeños y enfocados.  
- 🕒 Usa tiempo presente: `"Corrige error..."` en lugar de `"Corrigió..."`.  
- 🔗 Incluye referencias a tickets o issues.  
- 🧼 Evita cambios no relacionados en el mismo commit.  

💡 **Ejemplo:**
```bash
git commit -m "Añade validación de email en el formulario de registro"
```

---

## 📖 Conventional Commits

Definen un formato estándar para los mensajes de commit. Esto ayuda a automatizar changelogs, versionado y revisión de cambios.

### 📌 Formato básico:
```bash
<tipo>[alcance opcional]: <descripción>

[cuerpo opcional]

[pie de mensaje opcional]
```

### 🔖 Tipos comunes:

| Tipo     | Propósito                                         |
|----------|---------------------------------------------------|
| feat     | Nueva funcionalidad                               |
| fix      | Corrección de errores                             |
| docs     | Cambios en documentación                          |
| style    | Cambios de formato, sin afectar funcionalidad     |
| refactor | Refactorización sin cambiar comportamiento        |
| test     | Añadir/modificar pruebas                          |
| chore    | Tareas de mantenimiento/configuración             |

✅ **Ejemplo:**
```bash
git commit -m "feat(auth): añade soporte para autenticación con Google"
```

🧠 **Ventaja:** Mejora la trazabilidad y la colaboración entre desarrolladores.

---

## 🚀 ¿Qué es GitFlow?

GitFlow es un modelo de ramificación en Git, propuesto por Vincent Driessen, que define una estrategia clara para trabajar en equipo y lanzar versiones estables del software.

Su estructura define varias ramas con roles específicos para mantener organizado el ciclo de desarrollo.

---

## ⚙️ Tipos de ramas en GitFlow

GitFlow define cinco ramas principales:

- **main**: Contiene el código en producción, siempre estable.  
- **develop**: Integra todas las funcionalidades nuevas.  
- **feature/***: Se crean desde `develop` para trabajar nuevas características.  
- **release/***: Preparan versiones para producción. Se crean desde `develop` y se fusionan en `main` y `develop`.  
- **hotfix/***: Se crean desde `main` para corregir errores críticos. También se fusionan en `main` y `develop`.

---

## 🧪 Ejemplo práctico de uso

### 🛠 Crear una funcionalidad (feature)
```bash
git checkout develop
git checkout -b feature/login-feature
# trabajar en el código...
git add .
git commit -m "Implementa la funcionalidad de inicio de sesión"
git checkout develop
git merge feature/login-feature
git branch -d feature/login-feature
```

### 📦 Preparar una nueva versión (release)
```bash
git checkout develop
git checkout -b release/v1.0
# pruebas y ajustes...
git checkout main
git merge release/v1.0
git checkout develop
git merge release/v1.0
git branch -d release/v1.0
```

### 🧯 Corregir errores críticos (hotfix)
```bash
git checkout main
git checkout -b hotfix/fix-login-bug
# corregir el bug...
git add .
git commit -m "Corrige error en login"
git checkout main
git merge hotfix/fix-login-bug
git checkout develop
git merge hotfix/fix-login-bug
git branch -d hotfix/fix-login-bug
```

🧹 **Consejo:** Eliminar las ramas `feature`, `release` y `hotfix` tras su integración ayuda a mantener limpio el historial.

---

## 🧐 ¿Y la rama staging?

La rama `staging` no forma parte del modelo GitFlow oficial, pero algunos equipos la incorporan como puente entre `develop` y `main`.

**¿Para qué sirve una rama staging?**
- Realizar pruebas finales antes del despliegue.
- Simular el entorno de producción.
- Servir como entorno de QA.

⚠️ **Importante:** Su uso depende del flujo de trabajo del equipo y no es obligatorio en GitFlow.

---

## ✅ Tabla resumen de ramas

| Rama     | ¿En GitFlow oficial? | Propósito                                          |
|----------|----------------------|----------------------------------------------------|
| main     | ✅                   | Producción                                         |
| develop  | ✅                   | Desarrollo e integración                           |
| feature  | ✅                   | Nuevas funcionalidades                             |
| release  | ✅                   | Preparar lanzamientos                              |
| hotfix   | ✅                   | Corregir bugs críticos en producción               |
| staging  | ❌ (personalizado)   | Entorno previo a producción para pruebas finales   |

---

## 🔀 ¿Qué es GitHub Flow?

GitHub Flow es una estrategia de ramificación más simple que GitFlow, ideal para equipos que trabajan con entregas continuas o despliegues frecuentes. Solo requiere dos tipos de ramas:

- **main**: Contiene el código desplegable.  
- **feature/***: Se crean desde `main` para desarrollar nuevas funcionalidades o corregir errores.

---

## ⚙️ Flujo de trabajo en GitHub Flow

1. Crear una rama `feature` desde `main`.  
2. Trabajar en la nueva funcionalidad o corrección.  
3. Hacer pruebas y revisar el código.  
4. Realizar un Pull Request (PR).  
5. Revisar y aprobar el PR.  
6. Fusionar en `main` y desplegar.

🚀 **Importante:** No existen ramas `develop`, `release` ni `hotfix` como en GitFlow.

---

## ⚖️ GitHub Flow vs GitFlow

| Característica         | GitFlow                               | GitHub Flow                          |
|------------------------|----------------------------------------|--------------------------------------|
| Ramas principales      | main, develop                          | main                                 |
| Ramas adicionales      | feature/*, release/*, hotfix/*         | feature/*                            |
| Enfoque                | Planificación de versiones, QA manual | Entregas continuas, despliegues rápidos |
| Ideal para             | Equipos con ciclos de desarrollo largos | Equipos ágiles, con despliegues frecuentes |
| Automatización requerida | Baja                                 | Alta (tests y CI/CD)                |
| Complejidad            | Media-alta                             | Baja                                 |
| Control de calidad     | Alto (QA y revisiones manuales)       | Requiere rigor en revisión y testing |

---

## 🤔 ¿Qué estrategia me conviene usar?

| Situación                                                  | Estrategia recomendada |
|------------------------------------------------------------|-------------------------|
| Tienes equipo de QA y lanzamientos planificados por sprints | GitFlow                |
| Necesitas entregar rápido y con frecuencia                 | GitHub Flow            |
| Tu empresa maneja datos sensibles o sectores regulados     | GitFlow                |
| Cuentas con pruebas automatizadas y CI/CD                  | GitHub Flow            |

🎯 **Conclusión:**  
No hay una única estrategia correcta. La elección dependerá del tipo de proyecto, la madurez del equipo y los recursos disponibles.