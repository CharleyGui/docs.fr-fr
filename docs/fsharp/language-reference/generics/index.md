---
title: Génériques
description: Découvrez comment utiliser F# des fonctions et des types génériques, qui vous permettent d’écrire du code qui fonctionne avec divers types sans code répétitif.
ms.date: 05/16/2016
ms.openlocfilehash: 5d6e57762095e44836425f90d21a6c1dc71edaaa
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666695"
---
# <a name="generics"></a>Génériques

Les valeurs de fonctions, méthodes, propriétés et types d’agrégats F# comme les classes, les enregistrements et les unions discriminées peuvent être *génériques*. Les constructions génériques contiennent au moins un paramètre de type généralement fourni par l’utilisateur de la construction générique. Les types et les fonctions génériques vous permettent d’écrire le code qui fonctionne avec plusieurs types, sans que ce dernier ne soit répété pour chaque type. En F#, il est très simple d’affecter à votre code un caractère générique. En effet, celui-ci est souvent et implicitement déduit pour devenir générique par l’inférence de type et les mécanismes de généralisation automatique du compilateur.

## <a name="syntax"></a>Syntaxe

```fsharp
// Explicitly generic function.
let function-name<type-parameters> parameter-list =
function-body

// Explicitly generic method.
[ static ] member object-identifer.method-name<type-parameters> parameter-list [ return-type ] =
method-body

// Explicitly generic class, record, interface, structure,
// or discriminated union.
type type-name<type-parameters> type-definition
```

## <a name="remarks"></a>Notes

La déclaration d’un type ou d’une fonction explicitement générique s’apparente considérablement à celle d’un type ou d’une fonction non générique, sauf pour la spécification (et l’utilisation) des paramètres de type (entre crochets pointus après le nom du type ou de la fonction).

Les déclarations sont souvent implicitement génériques. Si vous ne spécifiez pas complètement le type de tous les paramètres utilisés pour composer un type ou une fonction, le compilateur tente de déduire le type de chaque paramètre, valeur et variable du code que vous écrivez. Pour plus d’informations, consultez [Inférence de type](../type-inference.md). Si le code de votre type ou fonction n’exerce pas de contrainte sur les types de paramètres, le type ou la fonction est implicitement générique. Le terme « *généralisation automatique* » désigne ce processus. La généralisation automatique présente des limites. Par exemple, si le compilateur F# ne parvient pas à déduire les types d’une construction générique, il signale une erreur qui fait référence à une restriction appelée « *restriction de valeur* ». Dans ce cas, vous devrez peut-être ajouter des annotations de type. Pour plus d’informations sur la généralisation automatique et sur la restriction de valeur, ainsi que sur la modification de votre code pour traiter le problème, consultez [Généralisation automatique](automatic-generalization.md).

Dans la syntaxe précédente, *type-parameters* est une liste de paramètres avec la virgule comme séparateur qui représentent des types inconnus, dont chacun commence par un guillemet simple, éventuellement avec une clause de contrainte qui limite encore davantage les types susceptibles d’être utilisés pour ce type de paramètre. Pour en savoir plus sur la syntaxe concernant les clauses de contraintes de plusieurs genres et obtenir d’autres informations sur les contraintes, consultez [Contraintes](constraints.md).

*type-definition* dans la syntaxe est identique à la définition de type pour un type non générique. Cela inclut les paramètres de constructeur pour un type de classe, une clause `as` facultative, le symbole égal, les champs d’enregistrement, la clause `inherit`, les sélections pour une union discriminée, les liaisons `let` et `do`, les définitions de membres et tout autre élément autorisé dans une définition de type non générique.

Les autres éléments de syntaxe sont identiques à ceux de types et de fonctions non génériques. Par exemple, *object-identifier* est un identificateur qui représente l’objet conteneur lui-même.

Les propriétés, champs et constructeurs ne peuvent pas être plus génériques que le type englobant. De plus, les valeurs d’un module ne peuvent pas être génériques.

## <a name="implicitly-generic-constructs"></a>Constructions implicitement génériques

Quand le compilateur F# déduit les types dans votre code, il traite automatiquement toute fonction susceptible d’être générique en tant que telle. Si vous spécifiez un type explicitement, comme un type de paramètre, cela empêche toute généralisation automatique.

Dans l’exemple de code suivant, `makeList` est générique, même si ni celui-ci ni ses paramètres ne sont explicitement déclarés comme étant génériques.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1700.fs)]

La signature de la fonction est déduite pour être `'a -> 'a -> 'a list`. Dans cet exemple, notez que `a` et `b` sont déduits pour avoir le même type. Cela est dû au fait qu’ils sont regroupés dans une liste et que tous les éléments d’une même liste doivent être du même type.

Vous pouvez également affecter un caractère générique à une fonction en utilisant la syntaxe contenant des guillemets simples dans une annotation de type, afin d’indiquer qu’un type de paramètre est un paramètre de type générique. Dans le code suivant, `function1` est générique car ses paramètres sont déclarés de cette manière, comme des paramètres de type.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1701.fs)]

## <a name="explicitly-generic-constructs"></a>Constructions explicitement génériques

Vous pouvez également rendre une fonction générique en déclarant explicitement ses paramètres de type entre crochets pointus (`<type-parameter>`). Le code suivant illustre ce comportement :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1703.fs)]

## <a name="using-generic-constructs"></a>Utilisation de constructions génériques

Quand vous utilisez des fonctions ou des méthodes génériques, il est possible que vous n’ayez pas à spécifier les arguments de type. Le compilateur utilise l’inférence de type pour déduire les arguments de type appropriés. S’il y a toujours une ambiguïté, vous pouvez fournir des arguments de type entre crochets pointus, en séparant plusieurs arguments de type par des virgules.

Le code suivant présente l’utilisation des fonctions définies aux sections précédentes.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1702.fs)]

> [!NOTE]
> Il existe deux manières de faire référence à un type générique sur la base du nom. Par exemple, `list<int>` et `int list` sont deux manières de faire référence à un type générique `list` qui dispose d’un argument de type unique `int`. Cette dernière forme n’est traditionnellement utilisée qu’avec des types F# intégrés, comme `list` et `option`. S’il existe plusieurs arguments de type, vous utilisez en principe la syntaxe `Dictionary<int, string>`, mais vous pouvez également utiliser la syntaxe `(int, string) Dictionary`.

## <a name="wildcards-as-type-arguments"></a>Caractères génériques utilisés comme arguments de type

Pour spécifier qu’un argument de type doit être déduit par le compilateur, vous pouvez utiliser le trait de soulignement ou le caractère générique (`_`) à la place d’un argument de type nommé. Ceci est illustré dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1704.fs)]

## <a name="constraints-in-generic-types-and-functions"></a>Contraintes concernant les types et fonctions génériques

Dans une définition de type ou de fonction générique, vous ne pouvez utiliser que les constructions connues pour être disponibles sur le paramètre de type générique. Cette exigence est imposée pour activer la vérification des appels de fonction et de méthode lors de la compilation. Si vous déclarez vos paramètres de type explicitement, vous pouvez appliquer une contrainte explicite à un paramètre de type générique pour notifier le compilateur que certaines méthodes et fonctions sont disponibles. Toutefois, si vous autorisez le compilateur F# à déduire vos types de paramètre génériques, il détermine les contraintes appropriées pour vous. Pour plus d’informations, consultez [Contraintes](constraints.md).

## <a name="statically-resolved-type-parameters"></a>Paramètres de type résolus statiquement

Il existe deux genres de paramètres de type qui peuvent être utilisés dans des programmes F#. Les premiers correspondent aux paramètres de type générique du genre décrit dans les précédentes sections. Ce premier genre de paramètre de type équivaut aux paramètres de type générique utilisés dans des langages tels que Visual Basic et C#. L’autre genre de paramètre de type est spécifique à F# et est appelé *type de paramètre résolu statiquement*. Pour plus d’informations sur ces constructions, consultez [Paramètres de type résolus statiquement](statically-resolved-type-parameters.md).

## <a name="examples"></a>Exemples

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1705.fs)]

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage](../index.md)
- [Types](../fsharp-types.md)
- [Paramètres de type résolus statiquement](statically-resolved-type-parameters.md)
- [Génériques](../../../standard/generics/index.md)
- [Généralisation automatique](automatic-generalization.md)
- [Contraintes](constraints.md)
