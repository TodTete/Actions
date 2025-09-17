# 🚀 GitHub Actions - Ejemplo Sencillo

Este repositorio muestra cómo utilizar **GitHub Actions** para automatizar tareas dentro de un proyecto en GitHub.  
GitHub Actions permite crear **flujos de trabajo (workflows)** que se ejecutan automáticamente en respuesta a eventos como *push*, *pull request* o incluso en un horario definido.

---

## 📂 Estructura del Repositorio

```

.github/
└── workflows/
└── ci.yml   # Archivo principal del workflow
README.md

````

---

## ⚙️ ¿Cómo funciona?

1. Cada flujo de trabajo se define dentro de la carpeta `.github/workflows/`.
2. El archivo YAML (`ci.yml`) describe:
   - **Eventos** que activan el flujo (ej. `push`, `pull_request`).
   - **Jobs** o trabajos que se ejecutan (ej. pruebas, despliegues).
   - **Steps** o pasos concretos (ej. instalar dependencias, ejecutar comandos).
3. GitHub ejecuta el flujo en un **runner** (una máquina virtual en la nube).

---

## 📄 Ejemplo de Workflow

Este flujo de trabajo se ejecuta cada vez que alguien hace un **push** en la rama `main`.  
Instala dependencias de Node.js y corre pruebas automatizadas.

```yaml
name: CI - Pruebas Node.js

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  build:
    runs-on: ubuntu-latest
    
    steps:
      - name: 📥 Clonar el repositorio
        uses: actions/checkout@v4

      - name: 🔧 Configurar Node.js
        uses: actions/setup-node@v4
        with:
          node-version: "18"

      - name: 📦 Instalar dependencias
        run: npm install

      - name: 🧪 Ejecutar pruebas
        run: npm test
````

---

## ▶️ Cómo probarlo

1. Crea la carpeta `.github/workflows/` en tu repositorio.
2. Añade el archivo `ci.yml` con el contenido anterior.
3. Haz un **commit y push** a tu repositorio.
4. Ve a la pestaña **Actions** en GitHub y observa cómo se ejecuta el workflow.

---

## 🌟 Beneficios de GitHub Actions

* Automatización de tareas repetitivas.
* Integración y entrega continua (CI/CD).
* Compatibilidad con múltiples lenguajes y entornos.
* Marketplace con miles de *actions* reutilizables.

---

## 📌 Recursos útiles

* [Documentación oficial de GitHub Actions](https://docs.github.com/actions)
* [Marketplace de Actions](https://github.com/marketplace?type=actions)

---
