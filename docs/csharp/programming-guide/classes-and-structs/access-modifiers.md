---
title: Modificateurs d’accès - Guide de programmation C#
description: Tous les types et membres de type en C# ont un niveau d’accessibilité qui détermine s’ils peuvent être utilisés à partir d’un autre code. Passez en revue cette liste de modificateurs d’accès.
ms.date: 03/08/2020
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: d800116137e088a54edb221fb4f81ecd47b0278f
ms.sourcegitcommit: 2b878d7011306b215dbf3d5dc9c1e78355a6dcd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2021
ms.locfileid: "98757861"
---
# <a name="access-modifiers-c-programming-guide"></a>Modificateurs d’accès (Guide de programmation C#)

Tous les types et membres de type ont un niveau d’accessibilité. Le niveau d’accessibilité détermine s’ils peuvent être utilisés à partir d’un autre code de votre assembly ou d’autres assemblys. Utilisez les modificateurs d’accès suivants pour spécifier l’accessibilité d’un type ou d’un membre lorsque vous le déclarez :

- [public](../../language-reference/keywords/public.md): le type ou le membre est accessible par tout autre code du même assembly ou d’un autre assembly qui le référence.
- [privé](../../language-reference/keywords/private.md): le type ou le membre est accessible uniquement par le code dans le même `class` ou `struct` .
- [protégé](../../language-reference/keywords/protected.md): il est possible d’accéder au type ou au membre uniquement par du code dans le même `class` ou dans un `class` qui est dérivé de celui-ci `class` .
- [interne](../../language-reference/keywords/internal.md): le type ou le membre est accessible par n’importe quel code dans le même assembly, mais pas à partir d’un autre assembly.
- [protected internal](../../language-reference/keywords/protected-internal.md): le type ou le membre est accessible par n’importe quel code de l’assembly dans lequel il est déclaré, ou à partir d’un dérivé `class` dans un autre assembly.
- [protégé privé](../../language-reference/keywords/private-protected.md): le type ou le membre est accessible uniquement dans son assembly déclarant, par le code dans le même `class` ou dans un type dérivé de celui-ci `class` .

Les exemples suivants montrent comment spécifier des modificateurs d’accès sur un type et un membre :

[!code-csharp[PublicAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#PublicAccess)]

Tous les modificateurs d’accès ne sont pas valides pour tous les types ou membres dans tous les contextes. Dans certains cas, l’accessibilité d’un membre de type est restreinte par l’accessibilité de son type conteneur.

## <a name="class-and-struct-accessibility"></a>Accessibilité des classes et des structs  

Les classes et les structs déclarés directement dans un espace de noms (en d’autres termes, qui ne sont pas imbriqués dans d’autres classes ou structs) peuvent être `public` ou `internal` . `internal` est la valeur par défaut si aucun modificateur d’accès n’est spécifié.

Les membres de struct, y compris les classes et structs imbriqués, peuvent être déclarés `public` , `internal` ou `private` . Les membres de classe, y compris les classes et structs imbriqués, peuvent être `public` , `protected internal` , `protected` ,, `internal` `private protected` ou `private` . Les membres de classe et de struct, y compris les classes et structs imbriqués, ont `private` accès par défaut. Les types imbriqués privés ne sont pas accessibles à partir de l’extérieur du type conteneur.

Les classes dérivées ne peuvent pas avoir une accessibilité supérieure à leurs types de base. Vous ne pouvez pas déclarer une classe publique `B` qui dérive d’une classe interne `A` . Si cela est autorisé, cela aurait pour effet de rendre `A` public, car tous les `protected` `internal` membres ou de `A` sont accessibles à partir de la classe dérivée.

Vous pouvez autoriser d’autres assemblys spécifiques à accéder à vos types internes à l’aide de `InternalsVisibleToAttribute` . Pour plus d’informations, consultez [assemblys friend](../../../standard/assembly/friend.md).

## <a name="class-and-struct-member-accessibility"></a>Accessibilité des membres de classe et de struct  

Vous pouvez déclarer les membres de classe (notamment les classes et structs imbriqués) avec l’un des six types d’accès. Les membres de struct ne peuvent pas être déclarés en tant que `protected` , `protected internal` ou, car les `private protected` structs ne prennent pas en charge l’héritage.

Normalement, l’accessibilité d’un membre n’est pas supérieure à l’accessibilité du type qui le contient. Toutefois, un `public` membre d’une classe interne peut être accessible depuis l’extérieur de l’assembly si le membre implémente des méthodes d’interface ou remplace des méthodes virtuelles définies dans une classe de base publique.

Le type d’un champ, d’une propriété ou d’un événement de membre doit être au moins aussi accessible que le membre lui-même. De même, le type de retour et les types de paramètre d’une méthode, d’un indexeur ou d’un délégué doivent être au moins aussi accessibles que le membre lui-même. Par exemple, vous ne pouvez pas avoir de `public` méthode `M` qui retourne une classe `C` à moins que `C` ne soit également `public` . De même, vous ne pouvez pas avoir une `protected` propriété de type `A` si `A` est déclaré comme `private` .

Les opérateurs définis par l’utilisateur doivent toujours être déclarés comme `public` et `static` . Pour plus d’informations, consultez [Surcharge d’opérateur](../../language-reference/operators/operator-overloading.md).

Les finaliseurs ne peuvent pas avoir de modificateurs d’accessibilité.

Pour définir le niveau d’accès pour `class` un `struct` membre ou, ajoutez le mot clé approprié à la déclaration de membre, comme indiqué dans l’exemple suivant.

[!code-csharp[MethodAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#MethodAccess)]

## <a name="other-types"></a>Autres types

Les interfaces déclarées directement dans un espace de noms peuvent être `public` ou `internal` et, tout comme les classes et les structs, les interfaces ont par défaut `internal` accès. Les membres d’interface sont `public` par défaut, car l’objectif d’une interface est de permettre à d’autres types d’accéder à une classe ou un struct. Les déclarations de membres d’interface peuvent inclure n’importe quel modificateur d’accès. Cela est très utile pour les méthodes statiques afin de fournir les implémentations courantes nécessaires à tous les implémenteurs d’une classe.

Les membres de l’énumération sont toujours `public` , et aucun modificateur d’accès ne peut être appliqué.

Les délégués se comportent comme des classes et des structs. Par défaut, ils ont `internal` accès lorsqu’ils sont déclarés directement dans un espace de noms, et sont `private` accessibles lorsqu’ils sont imbriqués.

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes et structs](./index.md)
- [Interfaces](../interfaces/index.md)
- [priv](../../language-reference/keywords/private.md)
- [public](../../language-reference/keywords/public.md)
- [intérieurs](../../language-reference/keywords/internal.md)
- [protected](../../language-reference/keywords/protected.md)
- [protected internal](../../language-reference/keywords/protected-internal.md)
- [protégé privé](../../language-reference/keywords/private-protected.md)
- [class](../../language-reference/keywords/class.md)
- [modélis](../../language-reference/builtin-types/struct.md)
- [interface](../../language-reference/keywords/interface.md)
