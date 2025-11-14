---
title: Guardar cambios temporalmente en memoria con git stash
description: Cómo guardar cambios en memoria.
sidebar:
    label: git stash (Guardar Cambios en Memoria)
    order: 13
---

Una situacion bastante comun al trabajar con Git es que se tienen cambios en el area de trabajo (working directory) que no se quieren commitear aun, pero se necesita cambiar de rama o hacer alguna otra operacion que requiere un area de trabajo limpia. Para estos casos, Git proporciona el comando `git stash`, que permite guardar temporalmente los cambios en memoria y restaurarlos posteriormente.

## Guardar cambios en memoria

```bash
git stash
git stash save "Mensaje del stash"  --opcional 
```
Esto guarda los cambios actuales en memoria y restaura el area de trabajo al ultimo commit.


## Listar stashes guardados

```bash
git stash list
```

![Ejemplo uso de git stash list](@assets/Git_Github/git-stash-ejemplo.png)


:::note
Cuando se guarda un stash, Git crea un arreglo en el cual se van guardando los stashes, cada uno con un identificador unico (ejemplo: `stash@{0}`, `stash@{1}`, etc.) y un mensaje opcional que describe el contenido del stash (en caso de que se proporcionara este al momento de guardar el stash).

Este se guarda como una **Pila (LIFO)** donde cada stash que entra pasa a la primera posicion `stash@{0}` y los almacenados aumentan.
:::

![Vista de pilas de stash](@assets/Git_Github/git-stash-ejemplo2.png)


## Aplicar un stash guardado

para obtener los cambios guardados en un stash y aplicarlos al area de trabajo actual, se puede utilizar los comandos `git stash apply` o `git stash pop`.

**la difenrencia entre ambos es que `git stash apply` aplica los cambios del stash pero lo mantiene en la lista de stashes guardados, mientras que `git stash pop` aplica los cambios y elimina el stash de la lista.**

Esto para las situaciones donde los cambios guardados en el stash pueden llevar a causar conflictos con los cambios actuales en el area de trabajo o se quieren llevar a otra rama, se quieren seguir probando, entre otroas situaciones.

```bash
git stash apply stash@{<num_stash>}      -- Aplica el stash sin eliminarlo
git stash pop stash@{<num_stash>}        -- Aplica el stash y lo elimina
```

Si no se especifica un stash, se aplica el mas reciente (`stash@{0}`).

![Ejemplo uso de git stash pop](@assets/Git_Github/git-stash-pop.png)


## Enviar stash a otra rama

```bash
git stash branch <nombre de la rama> stash@{<num_stash>} 
```

## Eliminar stashes guardados

```bash
git stash drop stash@{<num_stash>}   -- Elimina un stash especifico
git stash clear                      -- Elimina todos los stashes guardados
```
