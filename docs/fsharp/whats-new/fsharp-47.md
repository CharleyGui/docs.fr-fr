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
# <a name="whats-new-in-f-47"></a>Quoi de neuf dans F 4.7

F 4.7 ajoute de multiples améliorations à la langue F.

## <a name="get-started"></a>Prise en main

F 4.7 est disponible dans toutes les distributions .NET Core et l’outillage Visual Studio. [Commence avec F pour](../get-started/index.md) en savoir plus.

## <a name="language-version"></a>Version du langage

Le compilateur F 4.7 introduit la possibilité de définir votre version linguistique efficace via une propriété dans votre dossier de projet :

```xml
<PropertyGroup>
    <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Vous pouvez le définir `4.6` `4.7`aux `latest`valeurs `preview`, , , et . Par défaut, il s’agit de `latest`.

Si vous le `preview`définissez, votre compilateur activera toutes les fonctionnalités de prévisualisation de FMD qui sont implémentées dans votre compilateur.

## <a name="implicit-yields"></a>Rendements implicites

Vous n’avez plus `yield` besoin d’appliquer le mot clé dans les tableaux, les listes, les séquences ou les expressions de calcul où le type peut être déduit. Dans l’exemple suivant, `yield` les deux expressions nécessitaient l’énoncé pour chaque entrée avant le F 4.7 :

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

Si vous introduisez un seul `yield` mot `yield` clé, tous les autres éléments doivent également s’y être appliqués.

Les rendements implicites ne sont pas `yield!` activés lorsqu’ils sont utilisés dans une expression qui utilise également pour faire quelque chose comme aplatir une séquence. Vous devez continuer `yield` à utiliser aujourd’hui dans ces cas.

## <a name="wildcard-identifiers"></a>Identifiants Wildcard

Dans le code F impliquant les classes, l’auto-identifiant doit toujours être explicite dans les déclarations des membres. Mais dans les cas où l’auto-identifiant n’est jamais utilisé, il a toujours été convention d’utiliser un double-underscore pour indiquer un auto-identifiants sans nom. Vous pouvez maintenant utiliser un seul soulignement :

```fsharp
type C() =
    member _.M() = ()
```

Cela s’applique également pour `for` les boucles:

```fsharp
for _ in 1..10 do printfn "Hello!"
```

## <a name="indentation-relaxations"></a>Relaxations d’indentation

Avant le F 4.7, les exigences d’indentation pour les arguments des constructeurs primaires et des membres statiques nécessitaient une indentation excessive. Ils n’ont maintenant besoin que d’une seule portée d’indentation :

```fsharp
type OffsideCheck(a:int,
    b:int, c:int,
    d:int) = class end

type C() =
    static member M(a:int,
        b:int, c:int,
        d:int) = 1
```
