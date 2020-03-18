---
title: override, modificateur - Référence C#
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: acad3aa3b196c184132ad1acdf52b18a799b0896
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713246"
---
# <a name="override-c-reference"></a>override (référence C#)

Le modificateur `override` est nécessaire pour étendre ou modifier l’implémentation abstraite ou virtuelle d’une méthode, d’une propriété, d’un indexeur ou d’un événement hérités.

## <a name="example"></a> Exemple

Dans cet exemple, `Square` la classe doit fournir `GetArea` `GetArea` une mise en `Shape` œuvre primordiale de parce qu’est hérité de la classe abstraite:

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

Une méthode `override` fournit une nouvelle implémentation d’un membre hérité d’une classe de base. La méthode substituée par une déclaration `override` est appelée méthode de base substituée. La méthode de base substituée doit avoir la même signature que la méthode `override`. Pour plus d’informations sur l’héritage, consultez [Héritage](../../programming-guide/classes-and-structs/inheritance.md).

Vous ne pouvez pas surcharger une méthode statique ou non virtuelle. La méthode de base substituée doit être `virtual`, `abstract` ou `override`.

Une déclaration `override` ne peut pas changer l’accessibilité de la méthode `virtual`. Les deux méthodes `override` et `virtual` doivent avoir le même [modificateur de niveau d’accès](access-modifiers.md).

Vous ne pouvez pas utiliser les modificateurs `new`, `static` ou `virtual` pour modifier une méthode `override`.

Une déclaration de propriété de substitution doit spécifier exactement les mêmes modificateur d’accès, type et nom que la propriété héritée, et la propriété substituée doit être `virtual`, `abstract` ou `override`.

Pour plus d’informations sur l’utilisation du mot clé `override`, consultez [Gestion de version avec les mots clés override et new](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) et [Savoir quand utiliser les mots clés override et new](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="example"></a> Exemple

Cet exemple définit une classe de base nommée `Employee` et une classe dérivée nommée `SalesEmployee`. La classe `SalesEmployee` inclut un champ supplémentaire (`salesbonus`) et substitue la méthode `CalculatePay` afin de la prendre en compte.

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Héritage](../../programming-guide/classes-and-structs/inheritance.md)
- [Mots clés C#](index.md)
- [Modificateurs](index.md)
- [Abstrait](abstract.md)
- [Virtuel](virtual.md)
- [new (modificateur)](new-modifier.md)
- [Polymorphisme](../../programming-guide/classes-and-structs/polymorphism.md)
