---
title: Nouveautés de F# 4,7- F# Guide
description: Bénéficiez d’une vue d’ensemble des nouvelles F# fonctionnalités disponibles dans 4,7.
ms.date: 11/27/2019
ms.openlocfilehash: 203b258466cb9f1f50215ecf8884e92e7e86416b
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644067"
---
# <a name="whats-new-in-f-47"></a>Nouveautés de F# 4,7

F#4,7 ajoute plusieurs améliorations au F# langage.

## <a name="get-started"></a>Prise en main

F#4,7 est disponible dans toutes les distributions .NET Core et les outils Visual Studio. [Commencez avec F# ](../get-started/index.md) pour en savoir plus.

## <a name="language-version"></a>Version du langage

Le F# compilateur 4,7 introduit la possibilité de définir votre version de langage effective par le biais d’une propriété dans votre fichier projet :

```xml
<PropertyGroup>
    <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Vous pouvez lui affecter les valeurs `4.6`, `4.7`, `latest`et `preview`. La valeur par défaut est `latest`,

Si vous lui affectez la valeur `preview`, votre compilateur activera toutes les F# fonctionnalités d’aperçu qui sont implémentées dans votre compilateur.

## <a name="implicit-yields"></a>Rendements implicites

Vous n’avez plus besoin d’appliquer le mot clé `yield` dans des tableaux, des listes, des séquences ou des expressions de calcul où le type peut être déduit. Dans l’exemple suivant, les deux expressions nécessitaient l’instruction `yield` pour chaque entrée F# antérieure à 4,7 :

```fsharp
let s = seq { 1; 2; 3; 4; 5 }

let daysOfWeek includeWeekend =
    [ 
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then 
            "Saturday"
            "Sunday"
    ] 
```

Si vous introduisez un seul mot clé de `yield`, un `yield` doit également être appliqué à chaque autre élément.

Les rendements implicites ne sont pas activés lorsqu’ils sont utilisés dans une expression qui utilise également `yield!` pour effectuer une opération d’aplatissement d’une séquence. Dans ce cas, vous devez continuer à utiliser `yield` aujourd’hui.

## <a name="wildcard-identifiers"></a>Identificateurs génériques

Dans F# le code impliquant des classes, l’auto-identificateur doit toujours être explicite dans les déclarations de membre. Toutefois, dans les cas où l’auto-identificateur n’est jamais utilisé, il est traditionnellement conventionnel d’utiliser un trait de soulignement double pour indiquer les auto-identificateurs sans ID. Vous pouvez maintenant utiliser un trait de soulignement unique :

```fsharp
type C() =
    member _.M() = ()
```

Cela s’applique également aux boucles `for` :

```fsharp
for _ in 1..10 do printfn "Hello!"
```

## <a name="indentation-relaxations"></a>Assouplissements de la mise en retrait

Avant le F# 4,7, les exigences en matière de mise en retrait pour le constructeur principal et les arguments membres statiques nécessitaient une mise en retrait excessive. Ils n’ont à présent qu’une seule étendue de mise en retrait :

```fsharp
type OffsideCheck(a:int,
    b:int, c:int,
    d:int) = class end

type C() =
    static member M(a:int,
        b:int, c:int,
        d:int) = 1
```
