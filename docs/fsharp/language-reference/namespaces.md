---
title: Espaces de noms
description: Découvrez comment un F# espace de noms vous permet d’organiser le code en zones de fonctionnalités associées en vous permettant de joindre un nom à un regroupement d’éléments de programme.
ms.date: 12/08/2018
ms.openlocfilehash: a55da1592b04c64576b4c66de61b5ca137289a6f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425043"
---
# <a name="namespaces"></a>Espaces de noms

Un espace de noms vous permet d’organiser le code en zones de fonctionnalités associées en vous permettant de joindre un nom à F# un regroupement d’éléments de programme. Les espaces de noms sont généralement des éléments de F# niveau supérieur dans les fichiers.

## <a name="syntax"></a>Syntaxe

```fsharp
namespace [rec] [parent-namespaces.]identifier
```

## <a name="remarks"></a>Notes

Si vous souhaitez placer du code dans un espace de noms, la première déclaration du fichier doit déclarer l’espace de noms. Le contenu du fichier entier devient alors partie intégrante de l’espace de noms, à condition qu’il n’y ait plus de déclaration d’espaces de noms supplémentaire dans le fichier. Si tel est le cas, tout le code jusqu’à la déclaration d’espace de noms suivante est considéré comme étant dans le premier espace de noms.

Les espaces de noms ne peuvent pas contenir directement des valeurs et des fonctions. Au lieu de cela, les valeurs et les fonctions doivent être incluses dans les modules, et les modules sont inclus dans les espaces de noms. Les espaces de noms peuvent contenir des types, des modules.

Les commentaires de documentation XML peuvent être déclarés au-dessus d’un espace de noms, mais ils sont ignorés. Les directives de compilateur peuvent également être déclarées au-dessus d’un espace de noms.

Les espaces de noms peuvent être déclarés explicitement avec le mot clé namespace ou implicitement lors de la déclaration d’un module. Pour déclarer un espace de noms explicitement, utilisez le mot clé namespace suivi du nom de l’espace de noms. L’exemple suivant montre un fichier de code qui déclare un espace de noms `Widgets` avec un type et un module inclus dans cet espace de noms.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

Si le contenu entier du fichier se trouve dans un module, vous pouvez également déclarer implicitement des espaces de noms à l’aide du mot clé `module` et en fournissant le nouveau nom d’espace de noms dans le nom de module complet. L’exemple suivant montre un fichier de code qui déclare un espace de noms `Widgets` et un module `WidgetsModule`, qui contient une fonction.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

Le code suivant est équivalent au code précédent, mais le module est une déclaration de module locale. Dans ce cas, l’espace de noms doit apparaître sur sa propre ligne.

[!code-fsharp[Main](~/samples/snippets/fsharp/namespaces/snippet6402.fs)]

Si plusieurs modules sont requis dans le même fichier dans un ou plusieurs espaces de noms, vous devez utiliser des déclarations de module locales. Lorsque vous utilisez des déclarations de modules locaux, vous ne pouvez pas utiliser l’espace de noms qualifié dans les déclarations de module. Le code suivant montre un fichier qui a une déclaration d’espace de noms et deux déclarations de module locales. Dans ce cas, les modules sont contenus directement dans l’espace de noms ; Il n’existe aucun module créé implicitement qui porte le même nom que le fichier. Tout autre code dans le fichier, tel qu’une liaison de `do`, se trouve dans l’espace de noms, mais pas dans les modules internes. vous devez donc qualifier le membre du module `widgetFunction` à l’aide du nom du module.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

La sortie de cet exemple est la suivante.

```fsharp
Module1 10 20
Module2 5 6
```

Pour plus d’informations, consultez [modules](modules.md).

## <a name="nested-namespaces"></a>Espaces de noms imbriqués

Lorsque vous créez un espace de noms imbriqué, vous devez le qualifier entièrement. Sinon, vous créez un espace de noms de niveau supérieur. La mise en retrait est ignorée dans les déclarations d’espaces de noms.

L’exemple suivant montre comment déclarer un espace de noms imbriqué.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a>Espaces de noms dans les fichiers et les assemblys

Les espaces de noms peuvent s’étendre sur plusieurs fichiers dans un projet unique ou une compilation. Le terme *fragment d’espace de noms* décrit la partie d’un espace de noms qui est incluse dans un fichier. Les espaces de noms peuvent également s’étendre sur plusieurs assemblys. Par exemple, l’espace de noms `System` inclut l’intégralité du .NET Framework, qui s’étend sur de nombreux assemblys et contient de nombreux espaces de noms imbriqués.

## <a name="global-namespace"></a>Espace de noms global

Vous utilisez l’espace de noms prédéfini `global` pour placer les noms dans l’espace de noms de niveau supérieur .NET.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

Vous pouvez également utiliser global pour référencer l’espace de noms .NET de niveau supérieur, par exemple, pour résoudre les conflits de noms avec d’autres espaces de noms.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a>Espaces de noms récursifs

Les espaces de noms peuvent également être déclarés comme récursifs pour permettre à tous les codes contenus d’être mutuellement récursifs.  Cette opération s’effectue via `namespace rec`. L’utilisation de `namespace rec` peut atténuer les difficultés liées à l’impossibilité d’écrire du code mutuellement référentiel entre les types et les modules. Voici un exemple :

```fsharp
namespace rec MutualReferences

type Orientation = Up | Down
type PeelState = Peeled | Unpeeled

// This exception depends on the type below.
exception DontSqueezeTheBananaException of Banana

type BananaPeel() = class end

type Banana(orientation : Orientation) =
    member val IsPeeled = false with get, set
    member val Orientation = orientation with get, set
    member val Sides: PeelState list = [ Unpeeled; Unpeeled; Unpeeled; Unpeeled] with get, set

    member self.Peel() = BananaHelpers.peel self // Note the dependency on the BananaHelpers module.
    member self.SqueezeJuiceOut() = raise (DontSqueezeTheBananaException self) // This member depends on the exception above.

module BananaHelpers =
    let peel (b: Banana) =
        let flip (banana: Banana) =
            match banana.Orientation with
            | Up ->
                banana.Orientation <- Down
                banana
            | Down -> banana

        let peelSides (banana: Banana) =
            banana.Sides
            |> List.map (function
                         | Unpeeled -> Peeled
                         | Peeled -> Peeled)

        match b.Orientation with
        | Up ->   b |> flip |> peelSides
        | Down -> b |> peelSides
```

Notez que l’exception `DontSqueezeTheBananaException` et la classe `Banana` faire référence les unes aux autres.  En outre, le module `BananaHelpers` et la classe `Banana` également faire référence les uns aux autres. Cela ne serait pas possible d’exprimer F# dans si vous avez supprimé le mot clé `rec` de l’espace de noms `MutualReferences`.

Cette fonctionnalité est également disponible pour les [modules](modules.md)de niveau supérieur.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F#](index.md)
- [Modules](modules.md)
- [F#RFC FS-1009-autoriser les types et les modules mutuellement référentiels sur des étendues plus grandes au sein des fichiers](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
