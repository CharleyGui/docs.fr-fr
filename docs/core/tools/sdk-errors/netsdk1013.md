---
title: 'NETSDK1013 : la valeur TargetFramework n’a pas été reconnue.'
description: Comment déterminer et définir une valeur TargetFramework valide
author: marcpop
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1013
ms.openlocfilehash: 915ac22ad822d17c082498b469acbfb3f1a93efc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717867"
---
# <a name="netsdk1013-the-targetframework-value-was-not-recognized"></a>NETSDK1013 : la valeur TargetFramework n’a pas été reconnue

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) 3.1.100 .net Core et versions ultérieures

Le kit de développement logiciel (SDK) tente d’analyser les valeurs fournies dans le fichier projet pour `<TargetFramework>` ou `<TargetFrameworks>` dans une valeur connue.  Si la valeur n’est pas reconnue, `TargetFrameworkIdentifier` la `TargetFrameworkVersion` valeur ou peut être définie sur une chaîne vide ou `Unsupported` .

Pour résoudre ce dernier, vérifiez l’orthographe de votre `TargetFramework` valeur dans la liste des [frameworks pris en charge](../../../standard/frameworks.md).
Vous pouvez également définir les `TargetFrameworkIdentifier` `TargetFrameworkVersion` Propriétés et directement dans votre fichier projet.

```xml
<PropertyGroup Condition="'$(TargetFrameworkIdentifier)' == ''">
  <TargetFrameworkIdentifier>.NETCOREAPP</TargetFrameworkIdentifier>
  <TargetFrameworkVersion>3.1</TargetFrameworkVersion>
</PropertyGroup>
```
