---
title: Héritage
description: Apprenez à spécifier les relations d’héritage de F à l’aide du mot clé « héritez ».
ms.date: 05/16/2016
ms.openlocfilehash: 5ab891a93528427a66e4eb8f7bfeccbf6e4d2c7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400287"
---
# <a name="inheritance"></a>Héritage

L’héritage est utilisé pour modéliser la relation « est-a », ou sous-typage, dans la programmation orientée objet.

## <a name="specifying-inheritance-relationships"></a>Spécifier les relations d’héritage

Vous spécifiez `inherit` les relations d’héritage en utilisant le mot clé dans une déclaration de classe. La forme syntaxique de base est indiquée dans l’exemple suivant.

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

Une classe peut avoir au plus une classe de base directe. Si vous ne spécifiez `inherit` pas une classe de `System.Object`base en utilisant le mot clé, la classe hérite implicitement de .

## <a name="inherited-members"></a>Membres hérités

Si une classe hérite d’une autre classe, les méthodes et les membres de la classe de base sont disponibles pour les utilisateurs de la classe dérivée comme s’ils étaient des membres directs de la classe dérivée.

Les fixations de laisser et les paramètres constructor sont privés d’une classe et, par conséquent, ne peuvent pas être consultées à partir de classes dérivées.

Le `base` mot clé est disponible dans les classes dérivées et se réfère à l’instance de classe de base. Il est utilisé comme l’auto-identifiant.

## <a name="virtual-methods-and-overrides"></a>Méthodes et remplacements virtuels

Les méthodes virtuelles (et les propriétés) fonctionnent un peu différemment en F par rapport à d’autres langues .NET. Pour déclarer un nouveau membre `abstract` virtuel, vous utilisez le mot clé. Vous le faites indépendamment du fait que vous fournissiez une implémentation par défaut pour cette méthode. Ainsi, une définition complète d’une méthode virtuelle dans une classe de base suit ce modèle :

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

Et dans une classe dérivée, un remplacement de cette méthode virtuelle suit ce modèle :

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

Si vous ometez l’implémentation par défaut dans la classe de base, la classe de base devient une classe abstraite.

L’exemple de code suivant illustre la `function1` déclaration d’une nouvelle méthode virtuelle dans une classe de base et comment la remplacer dans une classe dérivée.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a>Constructeurs et héritage

Le constructeur de la classe de base doit être appelé dans la classe dérivée. Les arguments en faveur du constructeur de la `inherit` catégorie de base figurent dans la liste d’arguments de la clause. Les valeurs utilisées doivent être déterminées à partir des arguments fournis au constructeur de classe dérivé.

Le code suivant montre une classe de base et une classe dérivée, où la classe dérivée appelle le constructeur de classe de base dans la clause d’hériter :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

Dans le cas de plusieurs constructeurs, le code suivant peut être utilisé. La première ligne des constructeurs `inherit` de classe dérivés est la clause, `val` et les champs apparaissent comme des champs explicites qui sont déclarés avec le mot clé. Pour plus d’informations, voir [Champs explicites: `val` Le mot clé](./members/explicit-fields-the-val-keyword.md).

```fsharp
type BaseClass =
    val string1 : string
    new (str) = { string1 = str }
    new () = { string1 = "" }

type DerivedClass =
    inherit BaseClass

    val string2 : string
    new (str1, str2) = { inherit BaseClass(str1); string2 = str2 }
    new (str2) = { inherit BaseClass(); string2 = str2 }

let obj1 = DerivedClass("A", "B")
let obj2 = DerivedClass("A")
```

## <a name="alternatives-to-inheritance"></a>Alternatives à l’héritage

Dans les cas où une modification mineure d’un type est nécessaire, envisagez d’utiliser une expression d’objet comme alternative à l’héritage. L’exemple suivant illustre l’utilisation d’une expression d’objet comme alternative à la création d’un nouveau type dérivé :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

Pour plus d’informations sur les expressions d’objets, voir [Expressions d’objets](object-expressions.md).

Lorsque vous créez des hiérarchies d’objets, envisagez d’utiliser une union discriminée au lieu de l’héritage. Les unions discriminées peuvent également modéliser le comportement varié de différents objets qui partagent un type global commun. Une union seule et discriminée peut souvent éliminer la nécessité d’un certain nombre de classes dérivées qui sont des variations mineures les unes des autres. Pour plus d’informations sur les syndicats discriminés, voir [Discriminated Unions](discriminated-unions.md).

## <a name="see-also"></a>Voir aussi

- [Expressions d'objet](object-expressions.md)
- [Référence linguistique F](index.md)
