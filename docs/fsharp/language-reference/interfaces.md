---
title: Interfaces
description: Découvrez comment F# les interfaces spécifient des jeux de membres associés que d’autres classes implémentent.
ms.date: 05/16/2016
ms.openlocfilehash: 8f054a668ad0fbc2453a45883e8052471280eca3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627652"
---
# <a name="interfaces"></a>Interfaces

Les *interfaces* spécifient des ensembles de membres associés que d’autres classes implémentent.

## <a name="syntax"></a>Syntaxe

```fsharp
// Interface declaration:
[ attributes ]
type [accessibility-modifier] interface-name =
    [ interface ]     [ inherit base-interface-name ...]
    abstract member1 : [ argument-types1 -> ] return-type1
    abstract member2 : [ argument-types2 -> ] return-type2
    ...
[ end ]

// Implementing, inside a class type definition:
interface interface-name with
    member self-identifier.member1argument-list = method-body1
    member self-identifier.member2argument-list = method-body2

// Implementing, by using an object expression:
[ attributes ]
let class-name (argument-list) =
    { new interface-name with
        member self-identifier.member1argument-list = method-body1
        member self-identifier.member2argument-list = method-body2
        [ base-interface-definitions ]
    }
    member-list
```

## <a name="remarks"></a>Notes

Les déclarations d’interface ressemblent aux déclarations de classe, à ceci près qu’aucun membre n’est implémenté. Au lieu de cela, tous les membres sont abstraits, comme `abstract`indiqué par le mot clé. Vous ne fournissez pas de corps de méthode pour les méthodes abstraites. Toutefois, vous pouvez fournir une implémentation par défaut en incluant également une définition distincte du membre en tant que méthode avec le `default` mot clé. Cela revient à créer une méthode virtuelle dans une classe de base dans d’autres langages .NET. Une telle méthode virtuelle peut être substituée dans les classes qui implémentent l’interface.

L’accessibilité par défaut pour les `public`interfaces est.

Vous pouvez éventuellement attribuer un nom à chaque paramètre de méthode à F# l’aide d’une syntaxe normale:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

Dans l’exemple `ISprintable` ci-dessus `Print` , la méthode a un seul paramètre du `string` type portant le `format`nom.

Il existe deux façons d’implémenter des interfaces: en utilisant des expressions d’objet et des types de classe. Dans les deux cas, le type de classe ou l’expression d’objet fournit des corps de méthode pour les méthodes abstraites de l’interface. Les implémentations sont spécifiques à chaque type qui implémente l’interface. Par conséquent, les méthodes d’interface sur des types différents peuvent être différentes les unes des autres.

Les mots `interface` clés `end`et, qui marquent le début et la fin de la définition, sont facultatifs lorsque vous utilisez la syntaxe simplifiée. Si vous n’utilisez pas ces mots clés, le compilateur tente de déduire si le type est une classe ou une interface en analysant les constructions que vous utilisez. Si vous définissez un membre ou utilisez une autre syntaxe de classe, le type est interprété comme une classe.

Le style de codage .NET consiste à commencer toutes les interfaces en `I`majuscules.

## <a name="implementing-interfaces-by-using-class-types"></a>Implémentation d’interfaces à l’aide de types de classe

Vous pouvez implémenter une ou plusieurs interfaces dans un type de classe en `interface` utilisant le mot clé, le nom de l’interface `with` et le mot clé, suivis par les définitions de membres d’interface, comme indiqué dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

Les implémentations d’interface sont héritées, de sorte que toutes les classes dérivées n’ont pas besoin de les réimplémenter.

## <a name="calling-interface-methods"></a>Appeler des méthodes d’interface

Les méthodes d’interface peuvent être appelées uniquement par le biais de l’interface, et non par l’intermédiaire d’un objet du type qui implémente l’interface. Par conséquent, vous devrez peut-être effectuer une conversion vers le type d' `:>` interface à l' `upcast` aide de l’opérateur ou de l’opérateur pour appeler ces méthodes.

Pour appeler la méthode d’interface quand vous avez un objet de `SomeClass`type, vous devez effectuer un upcast de l’objet vers le type d’interface, comme indiqué dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

Une alternative consiste à déclarer une méthode sur l’objet qui effectue un upcast et appelle la méthode d’interface, comme dans l’exemple suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a>Implémentation d’interfaces à l’aide d’expressions d’objet

Les expressions d’objet fournissent un bref moyen d’implémenter une interface. Elles sont utiles lorsque vous n’avez pas besoin de créer un type nommé et que vous souhaitez simplement un objet qui prend en charge les méthodes d’interface, sans aucune méthode supplémentaire. Une expression d’objet est illustrée dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a>Héritage de l'interface

Les interfaces peuvent hériter d’une ou de plusieurs interfaces de base.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)
- [Expressions d'objet](object-expressions.md)
- [Classes](classes.md)
