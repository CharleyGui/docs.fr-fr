---
title: 'NETSDK1022 : des éléments en double ont été inclus.'
description: Comment résoudre le message d’élément en double basé sur les includes par défaut.
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1022
ms.openlocfilehash: 46c3d7d451e7c9e5b456b6e4e45054c3a4844386
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445785"
---
# <a name="netsdk1022-duplicate-items-were-included"></a>NETSDK1022 : des éléments en double ont été inclus.

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .NET 2.1.100 et versions ultérieures

À compter de Visual Studio 15,3, le kit de développement logiciel (SDK) .NET comprend automatiquement les éléments du répertoire du projet par défaut.  Cela comprend `Compile` les `Content` cibles et.  Cela doit vraiment nettoyer votre fichier projet et réduire la complexité que vous y avez.

Vous pouvez rétablir le comportement antérieur en affectant à la propriété correcte la valeur false.

Exemple pour les `Compile` éléments :

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
