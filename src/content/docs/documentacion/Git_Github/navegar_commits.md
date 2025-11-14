---
title: Moverse entre commits en Git
description: Cómo movernos entre commits para revisar cambios específicos.
sidebar:
    label: Navegar entre commits
    order: 14
---

En Git, es común necesitar moverse entre diferentes commits para revisar cambios específicos o estados anteriores del proyecto. Esto se puede lograr utilizando el comando `git checkout` o `git switch`.

## Moverse a un commit específico

```bash
git checkout <hash_del_commit>
git switch --detach <hash_del_commit>
```
:::caution
Esto cambiará el estado del repositorio al commit especificado. Ten en cuenta que estarás en un estado "detached HEAD", lo que significa que no estás en ninguna rama.

Es importante recordar que si tienes cambios sin commitear en tu area de trabajo, Git no te permitira hacer checkout a otro commit hasta que los guardes o los descartes.

Tambien si realizas cambios en este estado y deseas conservarlos, deberas crear una nueva rama y commitear los cambios ahi.
:::

## Volver a la rama principal
```bash
git checkout nombre_de_la_rama
git switch nombre_de_la_rama
```

![Ejemplo de cambio head entre commits](@assets/Git_Github/git-navegacion-commits.png)