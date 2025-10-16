# microfrontend-prototype

Main container for prototyping microfrontend

## Setup con Git Submodules

### Configurazione iniziale

1. **GitHub**: Crea repo microfrontend-prototype (central repo)
2. **Local**: `git clone microfrontend-prototype`
3. **GitHub**: Crea repo micro-fe-1 (primo submodulo)

### Aggiungere submodule

```bash
cd microfrontend-prototype
git submodule add https://github.com/Joschavai/micro-fe-1
```

Questo comando aggiunge il submodule ai submodules: verifica file `.gitmodules` in microfrontend-prototype

### Configurare il progetto nel submodule

```bash
cd micro-fe-1
yarn create vite .  # (per esempio)
cd ..  # ora sono in microfrontend-prototype
git add .
git commit -m "Adding first submodule"
git push
```

Verifica su GitHub che tutto sia stato caricato correttamente.

### Lavorare nel submodule

```bash
cd micro-fe-1
git add .
git commit -m "my first commit"
git push
```

Ora devi committare anche nel parent MICROFRONTEND-PROTOTYPE

```bash
cd ..
git status // vedrai la modifica del child
git add .
git commit -m "Update child module"
git push
```

A questo punto consiglio di confrontare i commit dei relativi modules con quelli su github

**Nota importante**: I repository sono separati nel senso che anche su GitHub sono repo ben distinte ma hanno una reference tramite git submodules.

## Clonare il progetto

Quando cloni un progetto con submodules, i submodules inizialmente saranno vuoti:

```bash
# Clona il progetto
git clone microfrontend-prototype

# Change directory per entrare nel progetto
cd microfrontend-prototype

# Questo scaricherà i file presenti nei moduli
git submodule update --init

# Entra nel submodule
cd micro-fe-1

# Il nome del branch sarà quello di un commit, quindi fai checkout al branch principale
git checkout main
```

## Rimuovere un submodule

Per rimuovere completamente un submodule dal progetto ([riferimento](https://gist.github.com/myusuf3/7f645819ded92bda6677)):

```bash
# Rimuovi la voce del submodule da .git/config
git submodule deinit -f path/to/submodule

# Rimuovi la directory del submodule da .git/modules del superproject
rm -rf .git/modules/path/to/submodule

# Rimuovi la voce in .gitmodules e la directory del submodule
git rm -f path/to/submodule
```

**Note**
Un submodule può chiaramente contenere un altro submodule

**Video tutorial utile**
https://www.youtube.com/watch?v=gSlXo2iLBro
