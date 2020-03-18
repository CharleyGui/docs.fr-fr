---
title: Types imbriqués - Guide de programmation C#
ms.date: 02/08/2020
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 12e44ccc1254424c152a238c8390f133550fa54c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626488"
---
# <a name="nested-types-c-programming-guide"></a>Types imbriqués (guide de programmation C#)

Un type défini au sein d’une [classe,](../../language-reference/keywords/class.md) [d’une struction ou d’une](../../language-reference/builtin-types/struct.md) [interface](../../language-reference/keywords/interface.md) s’appelle un type imbriqué. Par exemple

[!code-csharp[DeclareNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedClass)]

Que le type externe soit une classe, une interface ou une struct, les types imbriqués sont par défaut à [privés;](../../language-reference/keywords/private.md) ils ne sont accessibles qu’à partir de leur type de contenant. Dans l’exemple précédent, la classe `Nested` est inaccessible aux types externes.

Vous pouvez aussi spécifier un [modificateur d’accès](../../language-reference/keywords/access-modifiers.md) pour définir l’accessibilité d’un type imbriqué, comme ceci :

- Les types imbriqués d’une **classe** peuvent être [public](../../language-reference/keywords/public.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), [private](../../language-reference/keywords/private.md) ou [private protected](../../language-reference/keywords/private-protected.md).

   Cependant, le fait de définir une classe imbriquée `protected`, `protected internal` ou `private protected` à l’intérieur d’une [classe sealed](../../language-reference/keywords/sealed.md) a pour effet de générer l’avertissement de compilateur [CS0628](../../misc/cs0628.md), « nouveau membre protected déclaré dans une classe sealed ».
  
- Les types imbriqués d’un **struct** peuvent être [public](../../language-reference/keywords/public.md), [internal](../../language-reference/keywords/internal.md) ou [private](../../language-reference/keywords/private.md).

L’exemple suivant fait passer le type de la classe `Nested` à public :

[!code-csharp[PublicNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#PublicNestedClass)]

Le type imbriqué (ou interne) peut accéder au type conteneur (ou externe). Pour accéder au type conteneur, passez-le en tant qu’argument au constructeur du type imbriqué. Par exemple :

[!code-csharp[DeclareNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedInstance)]

Un type imbriqué a accès à tous les membres qui sont accessibles à son type conteneur. Il peut accéder aux membres privés et protégés du type conteneur, y compris à tous les membres protégés hérités.

Dans la déclaration précédente, le nom complet de classe `Nested` est `Container.Nested`. Il s'agit du nom utilisé pour créer une instance de la classe imbriquée, comme suit :

[!code-csharp[UseNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#UseNestedInstance)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes et structs](./index.md)
- [Modificateurs d’accès](./access-modifiers.md)
- [Constructeurs](./constructors.md)
