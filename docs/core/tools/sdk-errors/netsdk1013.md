---
title: 'NETSDK1013 : la valeur TargetFramework n’a pas été reconnue.'
description: Comment déterminer et définir une valeur TargetFramework valide
author: marcpop
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1013
ms.openlocfilehash: bcaed878b663f8bc957e8469ffd78caa9babf710
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445771"
---
# <a name="netsdk1013-the-targetframework-value-was-not-recognized"></a>NETSDK1013 : la valeur TargetFramework n’a pas été reconnue

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net 3.1.100 et versions ultérieures

Le kit de développement logiciel (SDK) tente d’analyser les valeurs fournies dans le fichier projet pour `<TargetFramework>` ou `<TargetFrameworks>` dans une valeur connue.  Si la valeur n’est pas reconnue, `TargetFrameworkIdentifier` la `TargetFrameworkVersion` valeur ou peut être définie sur une chaîne vide ou `Unsupported` .

Pour résoudre ce dernier, vérifiez l’orthographe de votre `TargetFramework` valeur dans la liste des [frameworks pris en charge](../../../standard/frameworks.md).
Vous pouvez également définir les `TargetFrameworkIdentifier` `TargetFrameworkVersion` Propriétés et directement dans votre fichier projet.

```xml
<PropertyGroup Condition="'$(TargetFrameworkIdentifier)' == ''">
  <TargetFrameworkIdentifier>.NETCOREAPP</TargetFrameworkIdentifier>
  <TargetFrameworkVersion>3.1</TargetFrameworkVersion>
</PropertyGroup>
```
