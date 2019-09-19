---
title: Paramètres de type résolus statiquement
description: Découvrez comment utiliser un F# paramètre de type résolu statiquement, qui est remplacé par un type réel au moment de la compilation plutôt qu’au moment de l’exécution.
ms.date: 05/16/2016
ms.openlocfilehash: bc3310192cdaa5ae4862b8aee46b6152f61da38a
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082923"
---
# <a name="statically-resolved-type-parameters"></a>Paramètres de type résolus statiquement

Un *paramètre de type résolu statiquement* est un paramètre de type qui est remplacé par un type réel au moment de la compilation plutôt qu’au moment de l’exécution. Elles sont précédées d’un symbole de signe insertion (^).

## <a name="syntax"></a>Syntaxe

```fsharp
ˆtype-parameter
```

## <a name="remarks"></a>Notes

Dans le F# langage, il existe deux genres distincts de paramètres de type. Le premier type est le paramètre de type générique standard. Celles-ci sont indiquées par une apostrophe ('), `'T` comme `'U`dans et. Ils sont équivalents aux paramètres de type générique dans d’autres langages de .NET Framework. L’autre type est résolu statiquement et est indiqué par un symbole de signe insertion, comme `^T` dans `^U`et.

Les paramètres de type résolus statiquement sont principalement utiles avec les contraintes de membre, qui sont des contraintes qui vous permettent de spécifier qu’un argument de type doit avoir un membre ou des membres particuliers pour être utilisé. Il n’existe aucun moyen de créer ce type de contrainte à l’aide d’un paramètre de type générique standard.

Le tableau suivant récapitule les similitudes et les différences entre les deux genres de paramètres de type.

|Fonctionnalité|Générique|Résolu statiquement|
|-------|-------|-------------------|
|Syntaxe|`'T`, `'U`|`^T`, `^U`|
|Temps de résolution|En cours d’exécution|Temps de compilation|
|Contraintes de membre|Ne peut pas être utilisé avec des contraintes de membre.|Peut être utilisé avec des contraintes de membre.|
|Génération de code|Un type (ou une méthode) avec des paramètres de type générique standard entraîne la génération d’un type ou d’une méthode générique unique.|Plusieurs instanciations de types et de méthodes sont générées, une pour chaque type requis.|
|Utiliser avec les types|Peut être utilisé sur les types.|Ne peut pas être utilisé sur les types.|
|Utiliser avec des fonctions inline|Non. Une fonction inline ne peut pas être paramétrée avec un paramètre de type générique standard.|Oui. Les paramètres de type résolus statiquement ne peuvent pas être utilisés sur des fonctions ou des méthodes qui ne sont pas Inline.|

De F# nombreuses fonctions de bibliothèque principales, en particulier les opérateurs, ont des paramètres de type résolus statiquement. Ces fonctions et opérateurs sont inline et produisent une génération de code efficace pour les calculs numériques.

Les méthodes inline et les fonctions qui utilisent des opérateurs, ou utilisent d’autres fonctions qui ont des paramètres de type résolus statiquement, peuvent également utiliser des paramètres de type résolus statiquement eux-mêmes. Souvent, l’inférence de type déduit que ces fonctions inline ont des paramètres de type résolus statiquement. L’exemple suivant illustre une définition d’opérateur qui est déduite pour avoir un paramètre de type résolu statiquement.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

Le type résolu de `(+@)` est basé sur l’utilisation `(+)` de et `(*)`, les deux ayant provoqué l’inférence de type pour déduire les contraintes de membre sur les paramètres de type résolus statiquement. Le type résolu, comme indiqué dans l' F# interpréteur, est le suivant.

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

La sortie est la suivante.

```console
2
1.500000
```

À partir F# de 4,1, vous pouvez également spécifier des noms de types concrets dans des signatures de paramètre de type résolues statiquement.  Dans les versions antérieures du langage, le nom de type pouvait être inféré en fait par le compilateur, mais il n’a pas pu être spécifié dans la signature.  À partir F# de 4,1, vous pouvez également spécifier des noms de types concrets dans des signatures de paramètre de type résolues statiquement. Voici un exemple :

```fsharp
let inline konst x _ = x

type CFunctor() = 
    static member inline fmap (f: ^a -> ^b, a: ^a list) = List.map f a
    static member inline fmap (f: ^a -> ^b, a: ^a option) =
        match a with
        | None -> None
        | Some x -> Some (f x)

    // default implementation of replace
    static member inline replace< ^a, ^b, ^c, ^d, ^e when ^a :> CFunctor and (^a or ^d): (static member fmap: (^b -> ^c) * ^d -> ^e) > (a, f) =
        ((^a or ^d) : (static member fmap : (^b -> ^c) * ^d -> ^e) (konst a, f))

    // call overridden replace if present
    static member inline replace< ^a, ^b, ^c when ^b: (static member replace: ^a * ^b -> ^c)>(a: ^a, f: ^b) =
        (^b : (static member replace: ^a * ^b -> ^c) (a, f))

let inline replace_instance< ^a, ^b, ^c, ^d when (^a or ^c): (static member replace: ^b * ^c -> ^d)> (a: ^b, f: ^c) =
        ((^a or ^c): (static member replace: ^b * ^c -> ^d) (a, f))

// Note the concrete type 'CFunctor' specified in the signature
let inline replace (a: ^a) (f: ^b): ^a0 when (CFunctor or  ^b): (static member replace: ^a *  ^b ->  ^a0) =
    replace_instance<CFunctor, _, _, _> (a, f)
```

## <a name="see-also"></a>Voir aussi

- [Génériques](index.md)
- [Inférence de type](../type-inference.md)
- [Généralisation automatique](automatic-generalization.md)
- [Contraintes](constraints.md)
- [Fonctions inline](../functions/inline-functions.md)
