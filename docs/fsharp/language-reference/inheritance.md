---
title: Héritage
description: 'Découvrez comment spécifier des relations d’héritage F # à l’aide du mot clé « Inherit ».'
ms.date: 05/16/2016
ms.openlocfilehash: 5ab891a93528427a66e4eb8f7bfeccbf6e4d2c7e
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223840"
---
# <a name="inheritance"></a>Héritage

L’héritage est utilisé pour modéliser la relation « is-a », ou sous-typage, dans la programmation orientée objet.

## <a name="specifying-inheritance-relationships"></a>Spécification des relations d’héritage

Vous spécifiez des relations d’héritage à l’aide du `inherit` mot clé dans une déclaration de classe. La forme syntaxique de base est illustrée dans l’exemple suivant.

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

Une classe ne peut avoir qu’une seule classe de base directe. Si vous ne spécifiez pas de classe de base à l’aide du `inherit` mot clé, la classe hérite implicitement de `System.Object` .

## <a name="inherited-members"></a>Membres hérités

Si une classe hérite d’une autre classe, les méthodes et les membres de la classe de base sont disponibles pour les utilisateurs de la classe dérivée comme s’ils étaient des membres directs de la classe dérivée.

Les liaisons Let et les paramètres de constructeur sont privés pour une classe et, par conséquent, ne sont pas accessibles à partir des classes dérivées.

Le mot clé `base` est disponible dans les classes dérivées et fait référence à l’instance de classe de base. Elle est utilisée comme l’auto-identificateur.

## <a name="virtual-methods-and-overrides"></a>Méthodes et substitutions virtuelles

Les méthodes virtuelles (et les propriétés) fonctionnent un peu différemment en F # par rapport à d’autres langages .NET. Pour déclarer un nouveau membre virtuel, vous utilisez le `abstract` mot clé. Pour ce faire, vous devez fournir une implémentation par défaut pour cette méthode. Par conséquent, une définition complète d’une méthode virtuelle dans une classe de base suit ce modèle :

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

Et dans une classe dérivée, une substitution de cette méthode virtuelle suit ce modèle :

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

Si vous omettez l’implémentation par défaut dans la classe de base, la classe de base devient une classe abstraite.

L’exemple de code suivant illustre la déclaration d’une nouvelle méthode virtuelle `function1` dans une classe de base et comment la substituer dans une classe dérivée.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a>Constructeurs et héritage

Le constructeur pour la classe de base doit être appelé dans la classe dérivée. Les arguments pour le constructeur de classe de base apparaissent dans la liste d’arguments de la `inherit` clause. Les valeurs utilisées doivent être déterminées à partir des arguments fournis au constructeur de classe dérivée.

Le code suivant illustre une classe de base et une classe dérivée, où la classe dérivée appelle le constructeur de classe de base dans la clause inherit :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

Dans le cas de plusieurs constructeurs, le code suivant peut être utilisé. La première ligne des constructeurs de classe dérivée est la `inherit` clause, et les champs apparaissent en tant que champs explicites qui sont déclarés avec le `val` mot clé. Pour plus d’informations, consultez [champs explicites : le `val` mot clé](./members/explicit-fields-the-val-keyword.md).

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

Dans les cas où une modification mineure d’un type est requise, envisagez d’utiliser une expression d’objet comme alternative à l’héritage. L’exemple suivant illustre l’utilisation d’une expression d’objet comme alternative à la création d’un nouveau type dérivé :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

Pour plus d’informations sur les expressions d’objet, consultez [expressions d’objet](object-expressions.md).

Lorsque vous créez des hiérarchies d’objets, envisagez d’utiliser une union discriminée au lieu de l’héritage. Les unions discriminées peuvent également modéliser le comportement variable de différents objets qui partagent un type global commun. Une seule Union discriminée peut souvent éliminer le besoin d’un certain nombre de classes dérivées qui sont des variations mineures les unes des autres. Pour plus d’informations sur les unions discriminées, consultez [unions discriminées](discriminated-unions.md).

## <a name="see-also"></a>Voir aussi

- [Expressions d'objet](object-expressions.md)
- [Informations de référence sur le langage F #](index.md)
