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
# <a name="whats-new-in-f-47"></a><span data-ttu-id="e319c-103">Nouveautés de F# 4,7</span><span class="sxs-lookup"><span data-stu-id="e319c-103">What's new in F# 4.7</span></span>

<span data-ttu-id="e319c-104">F#4,7 ajoute plusieurs améliorations au F# langage.</span><span class="sxs-lookup"><span data-stu-id="e319c-104">F# 4.7 adds multiple improvements to the F# language.</span></span>

## <a name="get-started"></a><span data-ttu-id="e319c-105">Prise en main</span><span class="sxs-lookup"><span data-stu-id="e319c-105">Get started</span></span>

<span data-ttu-id="e319c-106">F#4,7 est disponible dans toutes les distributions .NET Core et les outils Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e319c-106">F# 4.7 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="e319c-107">[Commencez avec F# ](../get-started/index.md) pour en savoir plus.</span><span class="sxs-lookup"><span data-stu-id="e319c-107">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="language-version"></a><span data-ttu-id="e319c-108">Version du langage</span><span class="sxs-lookup"><span data-stu-id="e319c-108">Language version</span></span>

<span data-ttu-id="e319c-109">Le F# compilateur 4,7 introduit la possibilité de définir votre version de langage effective par le biais d’une propriété dans votre fichier projet :</span><span class="sxs-lookup"><span data-stu-id="e319c-109">The F# 4.7 compiler introduces the ability to set your effective language version via a property in your project file:</span></span>

```xml
<PropertyGroup>
    <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="e319c-110">Vous pouvez lui affecter les valeurs `4.6`, `4.7`, `latest`et `preview`.</span><span class="sxs-lookup"><span data-stu-id="e319c-110">You can set it to the values `4.6`, `4.7`, `latest`, and `preview`.</span></span> <span data-ttu-id="e319c-111">La valeur par défaut est `latest`,</span><span class="sxs-lookup"><span data-stu-id="e319c-111">The default is `latest`.</span></span>

<span data-ttu-id="e319c-112">Si vous lui affectez la valeur `preview`, votre compilateur activera toutes les F# fonctionnalités d’aperçu qui sont implémentées dans votre compilateur.</span><span class="sxs-lookup"><span data-stu-id="e319c-112">If you set it to `preview`, your compiler will activate all F# preview features that are implemented in your compiler.</span></span>

## <a name="implicit-yields"></a><span data-ttu-id="e319c-113">Rendements implicites</span><span class="sxs-lookup"><span data-stu-id="e319c-113">Implicit yields</span></span>

<span data-ttu-id="e319c-114">Vous n’avez plus besoin d’appliquer le mot clé `yield` dans des tableaux, des listes, des séquences ou des expressions de calcul où le type peut être déduit.</span><span class="sxs-lookup"><span data-stu-id="e319c-114">You no longer need to apply the `yield` keyword in arrays, lists, sequences, or computation expressions where the type can be inferred.</span></span> <span data-ttu-id="e319c-115">Dans l’exemple suivant, les deux expressions nécessitaient l’instruction `yield` pour chaque entrée F# antérieure à 4,7 :</span><span class="sxs-lookup"><span data-stu-id="e319c-115">In the following example, both expressions required the `yield` statement for each entry prior to F# 4.7:</span></span>

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

<span data-ttu-id="e319c-116">Si vous introduisez un seul mot clé de `yield`, un `yield` doit également être appliqué à chaque autre élément.</span><span class="sxs-lookup"><span data-stu-id="e319c-116">If you introduce a single `yield` keyword, every other item must also have `yield` applied to it.</span></span>

<span data-ttu-id="e319c-117">Les rendements implicites ne sont pas activés lorsqu’ils sont utilisés dans une expression qui utilise également `yield!` pour effectuer une opération d’aplatissement d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="e319c-117">Implicit yields are not activated when used in an expression that also uses `yield!` to do something like flatten a sequence.</span></span> <span data-ttu-id="e319c-118">Dans ce cas, vous devez continuer à utiliser `yield` aujourd’hui.</span><span class="sxs-lookup"><span data-stu-id="e319c-118">You must continue to use `yield` today in these cases.</span></span>

## <a name="wildcard-identifiers"></a><span data-ttu-id="e319c-119">Identificateurs génériques</span><span class="sxs-lookup"><span data-stu-id="e319c-119">Wildcard identifiers</span></span>

<span data-ttu-id="e319c-120">Dans F# le code impliquant des classes, l’auto-identificateur doit toujours être explicite dans les déclarations de membre.</span><span class="sxs-lookup"><span data-stu-id="e319c-120">In F# code involving classes, the self-identifier needs to always be explicit in member declarations.</span></span> <span data-ttu-id="e319c-121">Toutefois, dans les cas où l’auto-identificateur n’est jamais utilisé, il est traditionnellement conventionnel d’utiliser un trait de soulignement double pour indiquer les auto-identificateurs sans ID.</span><span class="sxs-lookup"><span data-stu-id="e319c-121">But in cases where the self-identifier is never used, it has traditionally been convention to use a double-underscore to indicate a nameless self-identifiers.</span></span> <span data-ttu-id="e319c-122">Vous pouvez maintenant utiliser un trait de soulignement unique :</span><span class="sxs-lookup"><span data-stu-id="e319c-122">You can now use a single underscore:</span></span>

```fsharp
type C() =
    member _.M() = ()
```

<span data-ttu-id="e319c-123">Cela s’applique également aux boucles `for` :</span><span class="sxs-lookup"><span data-stu-id="e319c-123">This also applies for `for` loops:</span></span>

```fsharp
for _ in 1..10 do printfn "Hello!"
```

## <a name="indentation-relaxations"></a><span data-ttu-id="e319c-124">Assouplissements de la mise en retrait</span><span class="sxs-lookup"><span data-stu-id="e319c-124">Indentation relaxations</span></span>

<span data-ttu-id="e319c-125">Avant le F# 4,7, les exigences en matière de mise en retrait pour le constructeur principal et les arguments membres statiques nécessitaient une mise en retrait excessive.</span><span class="sxs-lookup"><span data-stu-id="e319c-125">Prior to F# 4.7, the indentation requirements for primary constructor and static member arguments required excessive indentation.</span></span> <span data-ttu-id="e319c-126">Ils n’ont à présent qu’une seule étendue de mise en retrait :</span><span class="sxs-lookup"><span data-stu-id="e319c-126">They now only require a single indentation scope:</span></span>

```fsharp
type OffsideCheck(a:int,
    b:int, c:int,
    d:int) = class end

type C() =
    static member M(a:int,
        b:int, c:int,
        d:int) = 1
```
