---
title: 'NETSDK1022 : des éléments en double ont été inclus.'
description: Comment résoudre le message d’élément en double basé sur les includes par défaut.
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1022
ms.openlocfilehash: bc803f5316bf09c12c563f1a63b8385d1be4e9ce
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506634"
---
# <a name="netsdk1022-duplicate-items-were-included"></a>NETSDK1022 : des éléments en double ont été inclus.

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .NET 2.1.100 et versions ultérieures

À compter de Visual Studio 2017/MSBuild version 15,3, le kit de développement logiciel (SDK) .NET comprend automatiquement les éléments du répertoire du projet par défaut.  Cela comprend `Compile` les `Content` cibles et.  Cela doit vraiment nettoyer votre fichier projet et réduire la complexité que vous y avez.

Vous pouvez rétablir le comportement antérieur en affectant à la propriété correcte la valeur false.

Exemple pour les `Compile` éléments :

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
