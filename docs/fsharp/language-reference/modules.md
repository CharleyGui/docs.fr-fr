---
title: Modules
description: Découvrez comment un F# module est un regroupement de F# de code, tels que les valeurs, les types et les valeurs de fonction dans une F# programme.
ms.date: 04/24/2017
ms.openlocfilehash: 07ea1eb9ed06988a780fd3c5acccbc8383a4dc55
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641779"
---
# <a name="modules"></a>Modules

Dans le contexte de la F# langage, un *module* est un regroupement de F# de code, tels que les valeurs, les types et les valeurs de fonction dans une F# programme. Le regroupement de code en modules vous permet de centraliser le code connexe et d’éviter les conflits de nom dans votre programme.

## <a name="syntax"></a>Syntaxe

```fsharp
// Top-level module declaration.
module [accessibility-modifier] [qualified-namespace.]module-name
declarations
// Local module declaration.
module [accessibility-modifier] module-name =
    declarations
```

## <a name="remarks"></a>Notes

Un F# module est un regroupement de F# constructions de code telles que les types, les valeurs, les valeurs de fonction et les code dans `do` liaisons. Il est implémenté comme une classe du common language runtime (CLR) qui comporte uniquement des membres statiques. Il existe deux types de déclarations de module, selon que la totalité du fichier est inclus dans le module : une déclaration de module de niveau supérieur et une déclaration de module locale. Une déclaration de module de niveau supérieur comprend la totalité du fichier dans le module. Une déclaration de module de niveau supérieur peut apparaître uniquement comme la première déclaration dans un fichier.

Dans la syntaxe pour la déclaration de module de niveau supérieur, le paramètre facultatif *espace de noms qualifié* est la séquence de noms de l’espace de noms imbriqué qui contient le module. L’espace de noms qualifié ne devra pas être déclaré précédemment.

Il est inutile de mettre en retrait les déclarations dans un module de niveau supérieur. Vous avez à mettre en retrait toutes les déclarations dans les modules locaux. Dans une déclaration de module locale, seules les déclarations sont mises en retrait sous cette déclaration de module font partie du module.

Si un fichier de code ne commence pas par une déclaration de module de niveau supérieur ou une déclaration d’espace de noms, tout le contenu du fichier, y compris tous les modules locaux, devient partie d’un module de niveau supérieur créé implicitement qui porte le même nom que le fichier, sans l’extension, avec la première lettre en majuscules. Par exemple, considérez le fichier suivant.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6601.fs)]

Ce fichier est compilé comme s’il était écrit de cette manière :

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6602.fs)]

Si vous avez plusieurs modules dans un fichier, vous devez utiliser une déclaration de module locale pour chaque module. Si un espace de noms englobant est déclaré, ces modules font partie de l’espace de noms englobant. Si un espace de noms englobant n’est pas déclaré, les modules deviennent partie intégrante du module de niveau supérieur créé implicitement. L’exemple de code suivant montre un fichier de code qui contient plusieurs modules. Le compilateur crée implicitement un module de niveau supérieur nommé `Multiplemodules`, et `MyModule1` et `MyModule2` sont imbriqués dans ce module de niveau supérieur.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6603.fs)]

Si vous avez plusieurs fichiers dans un projet ou dans une seule compilation, ou si vous générez une bibliothèque, vous devez inclure une déclaration d’espace de noms ou module en haut du fichier. Le F# compilateur détermine uniquement un nom de module implicitement lorsqu’il existe un seul fichier dans une ligne de commande de compilation ou de projet, et que vous créez une application.

Le *-modificateur d’accessibilité* peut prendre l’une des opérations suivantes : `public`, `private`, `internal`. Pour plus d’informations, consultez [Contrôle d’accès](access-control.md). La valeur par défaut est « public ».

## <a name="referencing-code-in-modules"></a>Code de référencement dans des Modules

Lorsque vous référencez des fonctions, des types et des valeurs à partir d’un autre module, vous devez utiliser un nom qualifié ou ouvrez le module. Si vous utilisez un nom qualifié, vous devez spécifier les espaces de noms, le module et l’identificateur de l’élément de programme. Vous séparez chaque partie du chemin d’accès qualifié par un point (.), comme suit.

`Namespace1.Namespace2.ModuleName.Identifier`

Vous pouvez ouvrir le module ou un ou plusieurs des espaces de noms pour simplifier le code. Pour plus d’informations sur les espaces de noms ouverture et de modules, consultez [déclarations d’importation : Le `open` mot clé](import-declarations-the-open-keyword.md).

L’exemple de code suivant montre un module de niveau supérieur qui contient tout le code jusqu'à la fin du fichier.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6604.fs)]

Pour utiliser ce code à partir d’un autre fichier dans le même projet, vous utiliser des noms qualifiés ou ouvrir le module avant d’utiliser les fonctions, comme indiqué dans les exemples suivants.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a>Modules imbriqués

Les modules peuvent être imbriqués. Modules internes doivent être mises en retrait en ce qui concerne les déclarations de module externe pour indiquer qu’ils sont des modules internes, pas de nouveaux modules. Par exemple, comparez les deux exemples suivants. Module `Z` est un module interne dans le code suivant.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6607.fs)]

Mais le module `Z` est un frère du module `Y` dans le code suivant.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6608.fs)]
Module `Z` est également un module frère dans le code suivant, car il n’est pas mis en retrait en ce qui concerne les autres déclarations de module `Y`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6609.fs)]
Enfin, si le module externe a pas de déclarations et est suivi immédiatement par une autre déclaration de module, la nouvelle déclaration de module est considéré comme un module interne, mais le compilateur vous avertit si la deuxième définition de module n’est pas mis en retrait règle le première.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6610.fs)]
Pour éliminer l’avertissement, mettre en retrait le module interne.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6611.fs)]
Si vous souhaitez tout le code dans un fichier dans un seul module externe et vous souhaitez que les modules internes, le module externe ne requiert pas le signe égal, et les déclarations, y compris toutes les déclarations de module interne qui iront dans le module externe n’ont pas à être mis en retrait. Déclarations dans les déclarations de module interne doivent être mis en retrait. Le code suivant illustre ce cas.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a>Modules récursive

F#4.1 introduit la notion de modules qui permettent la relation contenant-contenu tout le code d’être mutuellement récursives.  Cette opération est effectuée `module rec`.  Utilisation de `module rec` peuvent atténuer certains problèmes rencontrés dans l’impossibilité d’écrire du code mutuellement référentielle entre les types et les modules.  Voici un exemple de ceci :

```fsharp
module rec RecursiveModule =
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

Notez que l’exception `DontSqueezeTheBananaException` et la classe `Banana` tous deux se font mutuellement référence.  En outre, le module `BananaHelpers` et la classe `Banana` également se font mutuellement référence.  Cela ne serait pas possible d’exprimer dans F# si vous avez supprimé le `rec` mot clé à partir de la `RecursiveModule` module.

Cette fonctionnalité est également possible dans [espaces de noms](namespaces.md) avec F# 4.1.

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)
- [Espaces de noms](namespaces.md)
- [F#RFC FS-1009 - autoriser les types mutuellement référentielles et des modules sur des étendues plus grandes dans les fichiers](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
