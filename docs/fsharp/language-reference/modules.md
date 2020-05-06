---
title: Modules
description: 'Découvrez comment un module F # est un regroupement de code F #, tel que des valeurs, des types et des valeurs de fonction, dans un programme F #.'
ms.date: 04/24/2017
ms.openlocfilehash: 5f99bbd8069478bf0c7db2800ae545f31926728a
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794362"
---
# <a name="modules"></a>Modules

Dans le contexte du langage F #, un *module* est un regroupement de code f #, tel que des valeurs, des types et des valeurs de fonction, dans un programme f #. Le regroupement de code en modules vous permet de centraliser le code connexe et d’éviter les conflits de nom dans votre programme.

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

Un module F # est un regroupement de constructions de code F #, telles que des types, des valeurs, des valeurs de fonction `do` et du code dans des liaisons. Elle est implémentée en tant que classe common language runtime (CLR) qui n’a que des membres statiques. Il existe deux types de déclarations de module, selon que le fichier entier est inclus dans le module : une déclaration de module de niveau supérieur et une déclaration de module locale. Une déclaration de module de niveau supérieur comprend l’intégralité du fichier dans le module. Une déclaration de module de niveau supérieur ne peut apparaître qu’en tant que première déclaration dans un fichier.

Dans la syntaxe de la déclaration de module de niveau supérieur, l' *espace de noms qualifié* facultatif est la séquence de noms d’espaces de noms imbriqués qui contient le module. Il n’est pas nécessaire que l’espace de noms qualifié soit précédemment déclaré.

Vous n’avez pas besoin de mettre en retrait les déclarations dans un module de niveau supérieur. Vous devez mettre en retrait toutes les déclarations dans les modules locaux. Dans une déclaration de module locale, seules les déclarations mises en retrait sous cette déclaration de module font partie du module.

Si un fichier de code ne commence pas par une déclaration de module de niveau supérieur ou une déclaration d’espace de noms, le contenu entier du fichier, y compris les modules locaux, devient partie intégrante d’un module de niveau supérieur créé implicitement qui porte le même nom que le fichier, sans l’extension, avec la première lettre convertie en majuscules. Par exemple, considérez le fichier suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6601.fs)]

Ce fichier est compilé comme s’il avait été écrit de cette manière :

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6602.fs)]

Si vous avez plusieurs modules dans un fichier, vous devez utiliser une déclaration de module locale pour chaque module. Si un espace de noms englobant est déclaré, ces modules font partie de l’espace de noms englobant. Si un espace de noms englobant n’est pas déclaré, les modules deviennent partie intégrante du module de niveau supérieur créé implicitement. L’exemple de code suivant montre un fichier de code qui contient plusieurs modules. Le compilateur crée implicitement un module de niveau supérieur nommé `Multiplemodules`, et `MyModule1` et `MyModule2` sont imbriqués dans ce module de niveau supérieur.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6603.fs)]

Si vous avez plusieurs fichiers dans un projet ou dans une compilation unique, ou si vous générez une bibliothèque, vous devez inclure une déclaration d’espace de noms ou une déclaration de module en haut du fichier. Le compilateur F # détermine un nom de module implicitement lorsqu’il n’existe qu’un seul fichier dans un projet ou une ligne de commande de compilation, et que vous créez une application.

Le *modificateur Accessibility* peut être l’un des suivants : `public`, `private`, `internal`. Pour obtenir plus d'informations, voir [Contrôle d'accès](access-control.md). La valeur par défaut est public.

## <a name="referencing-code-in-modules"></a>Référencement du code dans des modules

Quand vous référencez des fonctions, des types et des valeurs d’un autre module, vous devez utiliser un nom qualifié ou ouvrir le module. Si vous utilisez un nom qualifié, vous devez spécifier les espaces de noms, le module et l’identificateur de l’élément de programme souhaité. Vous séparez chaque partie du chemin d’accès qualifié par un point (.), comme suit.

`Namespace1.Namespace2.ModuleName.Identifier`

Vous pouvez ouvrir le module ou un ou plusieurs des espaces de noms pour simplifier le code. Pour plus d’informations sur l’ouverture des espaces de noms et des modules, consultez [déclarations d’importation `open` : mot clé](import-declarations-the-open-keyword.md).

L’exemple de code suivant affiche un module de niveau supérieur qui contient tout le code jusqu’à la fin du fichier.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6604.fs)]

Pour utiliser ce code à partir d’un autre fichier dans le même projet, vous utilisez des noms qualifiés ou vous ouvrez le module avant d’utiliser les fonctions, comme indiqué dans les exemples suivants.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a>Modules imbriqués

Les modules peuvent être imbriqués. Les modules internes doivent être mis en retrait en ce qui concerne les déclarations de modules externes pour indiquer qu’il s’agit de modules internes, et non de nouveaux modules. Par exemple, comparez les deux exemples suivants. Module `Z` est un module interne dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6607.fs)]

Toutefois, `Z` le module est un frère `Y` du module dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6608.fs)]
Module `Z` est également un module frère dans le code suivant, car il n’est pas mis en retrait en ce qui concerne les `Y`autres déclarations dans le module.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6609.fs)]
Enfin, si le module externe n’a pas de déclaration et est immédiatement suivi par une autre déclaration de module, la nouvelle déclaration de module est supposée être un module interne, mais le compilateur vous avertit si la deuxième définition de module n’est pas mise en retrait plus loin que la première.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6610.fs)]
Pour éliminer l’avertissement, mettez en retrait le module interne.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6611.fs)]
Si vous souhaitez que tout le code d’un fichier se trouve dans un module externe unique et que vous souhaitiez des modules internes, le module externe ne nécessite pas le signe égal, et les déclarations, y compris les déclarations de module interne, qui seront insérées dans le module externe n’ont pas besoin d’être mises en retrait. Les déclarations à l’intérieur des déclarations de module interne doivent être mises en retrait. Le code suivant illustre ce cas.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a>Modules récursifs

F # 4,1 introduit la notion de modules qui permettent à tous les codes contenus d’être mutuellement récursifs.  Cette opération est effectuée `module rec`via.  L’utilisation `module rec` de peut atténuer les difficultés liées à l’impossibilité d’écrire du code mutuellement référentiel entre les types et les modules.  Voici un exemple :

```fsharp
module rec RecursiveModule =
    type Orientation = Up | Down
    type PeelState = Peeled | Unpeeled

    // This exception depends on the type below.
    exception DontSqueezeTheBananaException of Banana

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

Notez que l’exception `DontSqueezeTheBananaException` et la classe `Banana` font toutes les deux référence.  En outre, le module `BananaHelpers` et la classe `Banana` font également référence l’un à l’autre.  Cela ne serait pas possible d’exprimer en F # Si vous avez supprimé `rec` le mot clé `RecursiveModule` du module.

Cette fonctionnalité est également possible dans les [espaces de noms](namespaces.md) avec F # 4,1.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F #](index.md)
- [Espaces de noms](namespaces.md)
- [F # RFC FS-1009-autoriser les types et les modules mutuellement référentiels sur des étendues plus grandes au sein des fichiers](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
