---
title: 'Modification avec rupture : ca2014 : ne pas utiliser stackalloc dans les boucles'
description: En savoir plus sur la modification avec rupture dans .NET 5,0 provoquée par l’activation de la règle d’analyse du code ca2014.
ms.date: 09/03/2020
ms.openlocfilehash: 7ad6203c0edd930bbbe43cdb8df0413cba833d8e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760815"
---
# <a name="warning-ca2014-do-not-use-stackalloc-in-loops"></a>AVERTISSEMENT ca2014 : ne pas utiliser stackalloc dans les boucles

La règle de l’analyseur de code .NET [ca2014](/visualstudio/code-quality/ca2014) est activée, par défaut, à partir de .net 5,0. Il génère un avertissement de génération pour tout code C# dans lequel une expression [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) est utilisée à l’intérieur d’une boucle.

## <a name="change-description"></a>Description de la modification

À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET comprend des [analyseurs de code source .net](../../../../fundamentals/code-analysis/overview.md). Plusieurs de ces règles sont activées par défaut, y compris [ca2014](/visualstudio/code-quality/ca2014). Si votre projet contient du code qui enfreint cette règle et est configuré pour traiter les avertissements comme des erreurs, cette modification risque de perturber votre génération.

La règle ca2014 recherche le code C# dans lequel une [expression stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) est utilisée à l’intérieur d’une boucle. [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) alloue de la mémoire à partir du frame de pile actuel. La mémoire n’est pas libérée tant que l’appel de la méthode en cours n’est pas retourné, ce qui peut entraîner un dépassement de capacité de la pile. Comme vous ne pouvez pas intercepter les exceptions de dépassement de capacité de la pile, l’application se termine en cas de dépassement de capacité de pile.

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="recommended-action"></a>Action recommandée

- Évitez d’utiliser [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) dans les boucles. Allouez le bloc de mémoire en dehors de la boucle et réutilisez-le à l’intérieur de la boucle. Pour plus d’informations, consultez [ca2014](/visualstudio/code-quality/ca2014).

- Pour désactiver complètement l’analyse du code, affectez `EnableNETAnalyzers` à `false` la valeur dans votre fichier projet. Pour plus d’informations, consultez [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).

## <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
