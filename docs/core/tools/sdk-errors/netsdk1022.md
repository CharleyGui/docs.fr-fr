---
title: 'NETSDK1022 : des éléments en double ont été inclus.'
description: Comment résoudre le message d’élément en double basé sur les includes par défaut.
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1022
ms.openlocfilehash: c2bdbbb5503e5e4f6e6826f95f5a2cb08c908ceb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717866"
---
# <a name="netsdk1022-duplicate-items-were-included"></a>NETSDK1022 : des éléments en double ont été inclus.

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) 2.1.100 .net Core et versions ultérieures

À compter de Visual Studio 2017/MSBuild version 15,3, le kit de développement logiciel (SDK) .NET comprend automatiquement les éléments du répertoire du projet par défaut.  Cela comprend `Compile` les `Content` cibles et.  Cela doit vraiment nettoyer votre fichier projet et réduire la complexité que vous y avez.

Vous pouvez rétablir le comportement antérieur en affectant à la propriété correcte la valeur false.

Exemple pour les `Compile` éléments :

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
