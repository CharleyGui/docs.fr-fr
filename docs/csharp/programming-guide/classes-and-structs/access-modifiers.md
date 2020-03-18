---
title: Modificateurs d’accès - Guide de programmation C#
ms.date: 03/08/2020
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: 749d53344a2518966cfa5d937069ba73dfd6be8f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628226"
---
# <a name="access-modifiers-c-programming-guide"></a>Modificateurs d’accès (Guide de programmation C#)

Tous les types et les membres de type ont un niveau d’accessibilité. Le niveau d’accessibilité contrôle s’ils peuvent être utilisés à partir d’autres codes de votre assemblage ou d’autres assemblages. Utilisez les modificateurs d’accès suivants pour spécifier l’accessibilité d’un type ou d’un membre lorsque vous le déclarez :

- [public](../../language-reference/keywords/public.md): Le type ou le membre peut être consulté par n’importe quel autre code dans la même assemblée ou une autre assemblée qui le fait référence.
- [privé](../../language-reference/keywords/private.md): Le type ou le membre ne `class` peut `struct`être consulté que par code dans le même ou .
- [protégé](../../language-reference/keywords/protected.md): Le type ou le membre ne `class`peut être `class` consulté que par `class`code dans le même, ou dans un qui est dérivé de cela .
- [interne](../../language-reference/keywords/internal.md): Le type ou le membre peut être consulté par n’importe quel code dans la même assemblée, mais pas à partir d’une autre assemblée.
- [protégé interne](../../language-reference/keywords/protected-internal.md): Le type ou le membre peut être consulté par n’importe quel `class` code dans l’assemblée dans lequel il est déclaré, ou de l’intérieur d’un dérivé dans une autre assemblée.
- [privé protégé](../../language-reference/keywords/private-protected.md): Le type ou le membre ne peut être consulté `class` qu’à l’intérieur `class`de son assemblage déclarant, par code dans le même ou dans un type qui en découle .

Les exemples suivants montrent comment spécifier des modificateurs d’accès sur un type et un membre :

[!code-csharp[PublicAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#PublicAccess)]

Tous les modificateurs d’accès ne sont pas valables pour tous les types ou membres dans tous les contextes. Dans certains cas, l’accessibilité d’un membre type est limitée par l’accessibilité de son type de contenant.

## <a name="class-and-struct-accessibility"></a>Accessibilité de classe et de struct  

Les classes et les structs déclarées directement dans un espace nom (en d’autres termes, qui ne sont pas imbriqués dans d’autres classes ou structs) peuvent être soit `public` ou `internal`. `Internal`est la valeur par défaut si aucun modificateur d’accès n’est spécifié.  

Les membres de la structure, y compris les `public` `internal`classes `private`et les structs imbriquées, peuvent être déclarés, , ou . Les membres de la classe, y compris `public` `protected internal`les `protected` `internal`classes `private protected`imbriquées et les structs, peuvent être , , , , ou `private`. Les membres de classe et de struct, `private` y compris les classes et les structs imbriquées, ont accès par défaut. Les types imbriqués privés ne sont pas accessibles de l’extérieur du type contenant.

Les classes dérivées ne peuvent pas avoir une plus grande accessibilité que leurs types de base. Vous ne pouvez pas `B` déclarer une classe publique `A`qui dérive d’une classe interne . Si elle est autorisée, elle `A` aurait pour `protected` `internal` effet `A` de rendre public, parce que tout ou tous les membres sont accessibles de la classe dérivée.

Vous pouvez activer d’autres assemblages spécifiques `InternalsVisibleToAttribute`pour accéder à vos types internes en utilisant le . Pour plus d’informations, voir [Assemblées d’amis](../../../standard/assembly/friend.md).

## <a name="class-and-struct-member-accessibility"></a>Accessibilité des membres de classe et de struct  

Vous pouvez déclarer les membres de classe (notamment les classes et structs imbriqués) avec l’un des six types d’accès. Les membres de la structure `protected` `protected internal`ne `private protected` peuvent pas être déclarés comme , , ou parce que les structs ne soutiennent pas l’héritage.

Normalement, l’accessibilité d’un membre n’est pas supérieure à l’accessibilité du type qui le contient. Toutefois, `public` un membre d’une classe interne peut être accessible de l’extérieur de l’assemblée si le membre implémente des méthodes d’interface ou l’emporte sur les méthodes virtuelles qui sont définies dans une classe de base publique.

Le type de tout champ, propriété ou événement membre doit être au moins aussi accessible que le membre lui-même. De même, le type de déclaration et les types de paramètres de toute méthode, indexateur ou délégué doivent être au moins aussi accessibles que le membre lui-même. Par exemple, vous ne `public` pouvez `M` pas avoir `C` `C` une `public`méthode qui renvoie une classe à moins qu’elle ne l’ait également fait. De même, vous ne `protected` pouvez `A` pas `A` avoir `private`une propriété de type si elle est déclarée comme .

Les opérateurs définis par `public` les `static`utilisateurs doivent toujours être déclarés comme et . Pour plus d’informations, consultez [Surcharge d’opérateur](../../language-reference/operators/operator-overloading.md).

Les finalisateurs ne peuvent pas avoir de modificateurs d’accessibilité.

Pour définir le niveau `class` `struct` d’accès pour un ou un membre, ajoutez le mot clé approprié à la déclaration du membre, comme indiqué dans l’exemple suivant.

[!code-csharp[MethodAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#MethodAccess)]

## <a name="other-types"></a>Autres types

Les interfaces déclarées directement `public` dans `internal` un espace nom peut être ou, `internal` tout comme les classes et les structs, les interfaces par défaut d’accès. Les membres `public` de l’interface sont par défaut parce que le but d’une interface est de permettre à d’autres types d’accéder à une classe ou à une struction. Les déclarations des membres de l’interface peuvent inclure n’importe quel modificateur d’accès. Ceci est plus utile pour les méthodes statiques pour fournir des implémentations communes nécessaires par tous les implémenteurs d’une classe.

Les membres de `public`l’énumération sont toujours, et aucun modificateur d’accès ne peut être appliqué.

Les délégués se comportent comme des classes et des structs. Par défaut, `internal` ils ont accès lorsqu’ils `private` sont déclarés directement dans un espace nominant, et l’accès lorsqu’ils sont imbriqués.

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes et structs](./index.md)
- [Interfaces](../interfaces/index.md)
- [Privé](../../language-reference/keywords/private.md)
- [public](../../language-reference/keywords/public.md)
- [Interne](../../language-reference/keywords/internal.md)
- [Protégé](../../language-reference/keywords/protected.md)
- [protected internal](../../language-reference/keywords/protected-internal.md)
- [private protected](../../language-reference/keywords/private-protected.md)
- [Classe](../../language-reference/keywords/class.md)
- [struct](../../language-reference/builtin-types/struct.md)
- [Interface](../../language-reference/keywords/interface.md)
