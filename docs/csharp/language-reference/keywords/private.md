---
title: private, mot clé - Référence C#
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: a13e9ef18b0f6452c3ff1497dc97110bc21c433d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715196"
---
# <a name="private-c-reference"></a>private (référence C#)

Le mot clé `private` est un modificateur d’accès de membre.

> Cette page traite de l’accès `private`. Le `private` mot clé fait [`private protected`](./private-protected.md) également partie du modificateur d’accès.

L’accès privé est le niveau d’accès le moins permissif. Les membres privés sont accessibles uniquement dans le corps de la classe ou le struct dans lequel ils sont déclarés, comme dans cet exemple :

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

Les types imbriqués dans le même corps peuvent également accéder à ces membres privés.

Référencer un membre privé en dehors d'une classe ou d'un struct où il est déclaré serait à l'origine d'une erreur de compilation.

Pour obtenir une comparaison de `private` et des autres modificateurs d’accès, consultez [Niveaux d’accessibilité](accessibility-levels.md) et [Modificateurs d’accès](../../programming-guide/classes-and-structs/access-modifiers.md).

## <a name="example"></a> Exemple

Dans cet exemple, la classe `Employee` contient deux membres de données privés, `name` et `salary`. S’agissant de membres privés, ils sont accessibles uniquement par les méthodes membres. Les méthodes publiques `GetName` et `Salary` sont ajoutées pour permettre un accès contrôlé aux membres privés. Le membre `name` est accessible via une méthode publique et le membre `salary` est accessible via une propriété publique en lecture seule. (Pour plus d’informations, consultez [Propriétés](../../programming-guide/classes-and-structs/properties.md).)

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a>spécification du langage C#  

Pour plus d’informations, consultez [Accessibilité déclarée](~/_csharplang/spec/basic-concepts.md#declared-accessibility) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.

## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [Modificateurs d’accès](access-modifiers.md)
- [Niveaux d’accessibilité](accessibility-levels.md)
- [Modificateurs](index.md)
- [public](public.md)
- [Protégé](protected.md)
- [Interne](internal.md)
