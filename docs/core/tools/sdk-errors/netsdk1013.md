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
# <a name="netsdk1013-the-targetframework-value-was-not-recognized"></a><span data-ttu-id="98dd7-103">NETSDK1013 : la valeur TargetFramework n’a pas été reconnue</span><span class="sxs-lookup"><span data-stu-id="98dd7-103">NETSDK1013: The TargetFramework value was not recognized</span></span>

<span data-ttu-id="98dd7-104">**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) 3.1.100 .net Core et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="98dd7-104">**This article applies to:** ✔️ .NET Core 3.1.100 SDK and later versions</span></span>

<span data-ttu-id="98dd7-105">Le kit de développement logiciel (SDK) tente d’analyser les valeurs fournies dans le fichier projet pour `<TargetFramework>` ou `<TargetFrameworks>` dans une valeur connue.</span><span class="sxs-lookup"><span data-stu-id="98dd7-105">The SDK tries to parse the values provided in the project file for `<TargetFramework>` or `<TargetFrameworks>` into a well known value.</span></span>  <span data-ttu-id="98dd7-106">Si la valeur n’est pas reconnue, `TargetFrameworkIdentifier` la `TargetFrameworkVersion` valeur ou peut être définie sur une chaîne vide ou `Unsupported` .</span><span class="sxs-lookup"><span data-stu-id="98dd7-106">If the value is not recognized, the `TargetFrameworkIdentifier` or `TargetFrameworkVersion` value may be set to an empty string or `Unsupported`.</span></span>

<span data-ttu-id="98dd7-107">Pour résoudre ce dernier, vérifiez l’orthographe de votre `TargetFramework` valeur dans la liste des [frameworks pris en charge](../../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="98dd7-107">To resolve this, check the spelling of your `TargetFramework` value from the list of [supported frameworks](../../../standard/frameworks.md).</span></span>
<span data-ttu-id="98dd7-108">Vous pouvez également définir les `TargetFrameworkIdentifier` `TargetFrameworkVersion` Propriétés et directement dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="98dd7-108">You can also set the `TargetFrameworkIdentifier` and `TargetFrameworkVersion` properties directly in your project file.</span></span>

```xml
<PropertyGroup Condition="'$(TargetFrameworkIdentifier)' == ''">
  <TargetFrameworkIdentifier>.NETCOREAPP</TargetFrameworkIdentifier>
  <TargetFrameworkVersion>3.1</TargetFrameworkVersion>
</PropertyGroup>
```
