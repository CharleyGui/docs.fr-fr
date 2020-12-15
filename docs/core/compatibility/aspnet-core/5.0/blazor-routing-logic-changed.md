---
title: 'Modification avec rupture : éblouissant : modifications apportées à la logique de routage dans les applications éblouissantes'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulé éblouissant : modifications apportées à la logique de routage dans les applications éblouissantes'
author: scottaddie
ms.author: scaddie
ms.date: 12/14/2020
ms.openlocfilehash: 4ab8289565c88b17eb204a11724bb12a09b033c2
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513522"
---
# <a name="blazor-route-precedence-logic-changed-in-blazor-apps"></a>Éblouissante : la logique de priorité des itinéraires a changé dans les applications éblouissantes

Un bogue dans l’implémentation du routage éblouissant a affecté le mode de détermination de la priorité des itinéraires. Ce bogue affecte les itinéraires ou itinéraires Catch-All avec des paramètres facultatifs dans votre application éblouissante.

## <a name="version-introduced"></a>Version introduite

5.0.1

## <a name="old-behavior"></a>Ancien comportement

Avec le comportement erroné, les itinéraires avec une priorité plus faible sont considérés et mis en correspondance avec les itinéraires avec une priorité plus élevée. Par exemple, l' `{*slug}` itinéraire est mis en correspondance avant `/customer/{id}` .

## <a name="new-behavior"></a>Nouveau comportement

Le comportement actuel correspond plus étroitement au comportement de routage défini dans les applications ASP.NET Core. L’infrastructure détermine d’abord la priorité de l’itinéraire pour chaque segment. La longueur de l’itinéraire est utilisée uniquement en tant que deuxième critère pour rompre les liens.

## <a name="reason-for-change"></a>Motif de modification

Le comportement d’origine est considéré comme un bogue dans l’implémentation. En guise d’objectif, le système de routage dans les applications éblouissantes doit se comporter de la même façon que le système de routage dans le reste de ASP.NET Core.

## <a name="recommended-action"></a>Action recommandée

Si vous effectuez une mise à niveau à partir de versions précédentes de éblouissant vers 5. x, utilisez l' `PreferExactMatches` attribut sur le `Router` composant. Cet attribut peut être utilisé pour choisir le comportement correct. Par exemple :

```razor
<Router AppAssembly="@typeof(Program).Assembly" PreferExactMatches="true">
```

Lorsque `PreferExactMatches` a la valeur `true` , la correspondance des itinéraires préfère les correspondances exactes par rapport aux caractères génériques.

## <a name="affected-apis"></a>API affectées

Aucun

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->
