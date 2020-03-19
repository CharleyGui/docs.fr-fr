---
title: Quoi de neuf dans le guide F 4.7 - Guide de F
description: Obtenez un aperçu des nouvelles fonctionnalités disponibles dans le F 4.7.
ms.date: 11/27/2019
ms.openlocfilehash: 7a6e744a398719bcb55d168dd700459e0b122dd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185877"
---
# <a name="whats-new-in-f-47"></a><span data-ttu-id="35b07-103">Quoi de neuf dans F 4.7</span><span class="sxs-lookup"><span data-stu-id="35b07-103">What's new in F# 4.7</span></span>

<span data-ttu-id="35b07-104">F 4.7 ajoute de multiples améliorations à la langue F.</span><span class="sxs-lookup"><span data-stu-id="35b07-104">F# 4.7 adds multiple improvements to the F# language.</span></span>

## <a name="get-started"></a><span data-ttu-id="35b07-105">Prise en main</span><span class="sxs-lookup"><span data-stu-id="35b07-105">Get started</span></span>

<span data-ttu-id="35b07-106">F 4.7 est disponible dans toutes les distributions .NET Core et l’outillage Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="35b07-106">F# 4.7 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="35b07-107">[Commence avec F pour](../get-started/index.md) en savoir plus.</span><span class="sxs-lookup"><span data-stu-id="35b07-107">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="language-version"></a><span data-ttu-id="35b07-108">Version du langage</span><span class="sxs-lookup"><span data-stu-id="35b07-108">Language version</span></span>

<span data-ttu-id="35b07-109">Le compilateur F 4.7 introduit la possibilité de définir votre version linguistique efficace via une propriété dans votre dossier de projet :</span><span class="sxs-lookup"><span data-stu-id="35b07-109">The F# 4.7 compiler introduces the ability to set your effective language version via a property in your project file:</span></span>

```xml
<PropertyGroup>
    <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="35b07-110">Vous pouvez le définir `4.6` `4.7`aux `latest`valeurs `preview`, , , et .</span><span class="sxs-lookup"><span data-stu-id="35b07-110">You can set it to the values `4.6`, `4.7`, `latest`, and `preview`.</span></span> <span data-ttu-id="35b07-111">Par défaut, il s’agit de `latest`.</span><span class="sxs-lookup"><span data-stu-id="35b07-111">The default is `latest`.</span></span>

<span data-ttu-id="35b07-112">Si vous le `preview`définissez, votre compilateur activera toutes les fonctionnalités de prévisualisation de FMD qui sont implémentées dans votre compilateur.</span><span class="sxs-lookup"><span data-stu-id="35b07-112">If you set it to `preview`, your compiler will activate all F# preview features that are implemented in your compiler.</span></span>

## <a name="implicit-yields"></a><span data-ttu-id="35b07-113">Rendements implicites</span><span class="sxs-lookup"><span data-stu-id="35b07-113">Implicit yields</span></span>

<span data-ttu-id="35b07-114">Vous n’avez plus `yield` besoin d’appliquer le mot clé dans les tableaux, les listes, les séquences ou les expressions de calcul où le type peut être déduit.</span><span class="sxs-lookup"><span data-stu-id="35b07-114">You no longer need to apply the `yield` keyword in arrays, lists, sequences, or computation expressions where the type can be inferred.</span></span> <span data-ttu-id="35b07-115">Dans l’exemple suivant, `yield` les deux expressions nécessitaient l’énoncé pour chaque entrée avant le F 4.7 :</span><span class="sxs-lookup"><span data-stu-id="35b07-115">In the following example, both expressions required the `yield` statement for each entry prior to F# 4.7:</span></span>

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

<span data-ttu-id="35b07-116">Si vous introduisez un seul `yield` mot `yield` clé, tous les autres éléments doivent également s’y être appliqués.</span><span class="sxs-lookup"><span data-stu-id="35b07-116">If you introduce a single `yield` keyword, every other item must also have `yield` applied to it.</span></span>

<span data-ttu-id="35b07-117">Les rendements implicites ne sont pas `yield!` activés lorsqu’ils sont utilisés dans une expression qui utilise également pour faire quelque chose comme aplatir une séquence.</span><span class="sxs-lookup"><span data-stu-id="35b07-117">Implicit yields are not activated when used in an expression that also uses `yield!` to do something like flatten a sequence.</span></span> <span data-ttu-id="35b07-118">Vous devez continuer `yield` à utiliser aujourd’hui dans ces cas.</span><span class="sxs-lookup"><span data-stu-id="35b07-118">You must continue to use `yield` today in these cases.</span></span>

## <a name="wildcard-identifiers"></a><span data-ttu-id="35b07-119">Identifiants Wildcard</span><span class="sxs-lookup"><span data-stu-id="35b07-119">Wildcard identifiers</span></span>

<span data-ttu-id="35b07-120">Dans le code F impliquant les classes, l’auto-identifiant doit toujours être explicite dans les déclarations des membres.</span><span class="sxs-lookup"><span data-stu-id="35b07-120">In F# code involving classes, the self-identifier needs to always be explicit in member declarations.</span></span> <span data-ttu-id="35b07-121">Mais dans les cas où l’auto-identifiant n’est jamais utilisé, il a toujours été convention d’utiliser un double-underscore pour indiquer un auto-identifiants sans nom.</span><span class="sxs-lookup"><span data-stu-id="35b07-121">But in cases where the self-identifier is never used, it has traditionally been convention to use a double-underscore to indicate a nameless self-identifiers.</span></span> <span data-ttu-id="35b07-122">Vous pouvez maintenant utiliser un seul soulignement :</span><span class="sxs-lookup"><span data-stu-id="35b07-122">You can now use a single underscore:</span></span>

```fsharp
type C() =
    member _.M() = ()
```

<span data-ttu-id="35b07-123">Cela s’applique également pour `for` les boucles:</span><span class="sxs-lookup"><span data-stu-id="35b07-123">This also applies for `for` loops:</span></span>

```fsharp
for _ in 1..10 do printfn "Hello!"
```

## <a name="indentation-relaxations"></a><span data-ttu-id="35b07-124">Relaxations d’indentation</span><span class="sxs-lookup"><span data-stu-id="35b07-124">Indentation relaxations</span></span>

<span data-ttu-id="35b07-125">Avant le F 4.7, les exigences d’indentation pour les arguments des constructeurs primaires et des membres statiques nécessitaient une indentation excessive.</span><span class="sxs-lookup"><span data-stu-id="35b07-125">Prior to F# 4.7, the indentation requirements for primary constructor and static member arguments required excessive indentation.</span></span> <span data-ttu-id="35b07-126">Ils n’ont maintenant besoin que d’une seule portée d’indentation :</span><span class="sxs-lookup"><span data-stu-id="35b07-126">They now only require a single indentation scope:</span></span>

```fsharp
type OffsideCheck(a:int,
    b:int, c:int,
    d:int) = class end

type C() =
    static member M(a:int,
        b:int, c:int,
        d:int) = 1
```
