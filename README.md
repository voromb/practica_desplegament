# Documentació del Projecte — Metodologia Git Flow

## Objectiu del projecte
Aquest projecte té com a finalitat implementar una pàgina web educativa per mostrar exemples d'interacció entre **JavaScript i HTML/CSS**, seguint una **metodologia professional de treball en equip amb Git Flow**.

---

## Introducció a Git i Git Flow

### Què és Git?
Git és un sistema de control de versions distribuït que permet gestionar l'evolució del codi font i col·laborar entre diversos programadors sense perdre l'historial de canvis.

### Què és Git Flow?
Git Flow és una metodologia de treball basada en **branques estructurades**, ideal per equips. Utilitza diferents tipus d’extensions de branques:

| Tipus de branca | Propòsit |
|-----------------|---------|
| `main` / `master` | Versió estable en producció |
| `develop` | Zona de desenvolupament actiu |
| `feature/*` | Desenvolupament de funcionalitats |
| `release/*` | Preparació d'una versió oficial |
| `hotfix/*` | Correccions urgents sobre producció |

Aquesta metodologia ens assegura que **sempre hi ha una versió estable**, mentre el desenvolupament continua de forma organitzada.

---

## Assignació de rols (simulació d'equip)

| Usuari | Rol assignat | Tasca |
|--------|-------------|-------|
| **Usuari 1 (Expert)** | Inicialització de Git Flow, estructura base, hotfix | `feature/estructura_inicial` i `hotfix/milloresV_1_0` |
| **Usuari 2** | Desenvolupament de contingut HTML | `feature/contingutHTML` i `feature/atributsHTML` |
| **Usuari 3** | Desenvolupament CSS i generació de release | `feature/estilsCSS` i `release/v1.0` |

---

## Procés complet — Captures numerades (1 a 20)

### **1. Creació de carpeta i clonació del repositori**
```bash
git clone https://github.com/voromb/practica_desplegament.git
```

2. Inicialització de Git Flow

```bash
git flow init
```

3. Creació d'estructura del projecte amb PowerShell

```bash
New-Item -ItemType Directory -Name css
New-Item -ItemType Directory -Name js
New-Item -ItemType Directory -Name docs
```


4. Commit inicial per assegurar canvis

```bash
git add .
git commit -m "feat(estructura): estructura inicial del projecte"
```


 ```bash
 5. Finalització de la feature estructura_inicial
git flow feature finish estructura_inicial
```

```bash
6. Inici de feature/contingutHTML
git flow feature start contingutHTML
```

```bash
7. Edició i commit de la secció contingut
git add contingut.html
git commit -m "feat(contingutHTML): afegir exemple d'interacció HTML"
```
```bash
8. Finalització de feature/contingutHTML
git flow feature finish contingutHTML
```
```bash
 9. Inici de feature/atributsHTML
git flow feature start atributsHTML
```
```bash
10. Commit de la funcionalitat d'atributs
git add atributs.html
git commit -m "feat(atributsHTML): exemple de canvi d'atributs HTML"
```

```bash
11. Finalització de feature/atributsHTML
git flow feature finish atributsHTML
```

```bash
12. Inici de feature/estilsCSS
git flow feature start estilsCSS
```

```bash
13. Commit de la funcionalitat CSS
git add estils.html
git commit -m "feat(estilsCSS): afegir exemple de canvi d'estils"
```

```bash
14. Finalització de feature/estilsCSS
git flow feature finish estilsCSS
```
```bash
15. Inici de release/v1.0
git flow release start v1.0
```

```bash

16. Tancament de release (merge + tag)
git flow release finish v1.0
```

```bash
17. Inici de hotfix/milloresV_1_0
git flow hotfix start milloresV_1_0
```

```bash
18. Commit del hotfix
git add contingut.html
git commit -m "fix(milloresV_1_0): ajustar text de contingut"
```

```bash
19. Finalització del hotfix
git flow hotfix finish milloresV_1_0
```

```bash
20. Publicació a GitHub (master, develop i tags)
git push origin master --tags
git push origin develop
```

