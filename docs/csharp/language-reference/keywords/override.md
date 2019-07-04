---
title: override, modificateur - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: cedce26373c49d33ee17602b621f71ef6732d145
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401547"
---
# <a name="override-c-reference"></a>override (référence C#)

Le modificateur `override` est nécessaire pour étendre ou modifier l’implémentation abstraite ou virtuelle d’une méthode, d’une propriété, d’un indexeur ou d’un événement hérités.

## <a name="example"></a>Exemples

Dans cet exemple, la classe `Square` doit fournir une implémentation substituée de `Area`, car `Area` est héritée de la classe abstraite `ShapesClass` :

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

Une méthode `override` fournit une nouvelle implémentation d’un membre hérité d’une classe de base. La méthode substituée par une déclaration `override` est appelée méthode de base substituée. La méthode de base substituée doit avoir la même signature que la méthode `override`. Pour plus d’informations sur l’héritage, consultez [Héritage](../../programming-guide/classes-and-structs/inheritance.md).

Vous ne pouvez pas surcharger une méthode statique ou non virtuelle. La méthode de base substituée doit être `virtual`, `abstract` ou `override`.

Une déclaration `override` ne peut pas changer l’accessibilité de la méthode `virtual`. Les deux méthodes `override` et `virtual` doivent avoir le même [modificateur de niveau d’accès](access-modifiers.md).

Vous ne pouvez pas utiliser les modificateurs `new`, `static` ou `virtual` pour modifier une méthode `override`.

Une déclaration de propriété de substitution doit spécifier exactement les mêmes modificateur d’accès, type et nom que la propriété héritée, et la propriété substituée doit être `virtual`, `abstract` ou `override`.

Pour plus d’informations sur l’utilisation du mot clé `override`, consultez [Gestion de version avec les mots clés override et new](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) et [Savoir quand utiliser les mots clés override et new](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="example"></a>Exemples

Cet exemple définit une classe de base nommée `Employee` et une classe dérivée nommée `SalesEmployee`. La classe `SalesEmployee` inclut un champ supplémentaire (`salesbonus`) et substitue la méthode `CalculatePay` afin de la prendre en compte.

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Héritage](../../programming-guide/classes-and-structs/inheritance.md)
- [Mots clés C#](index.md)
- [Modificateurs](modifiers.md)
- [abstract](abstract.md)
- [virtual](virtual.md)
- [new (modificateur)](new-modifier.md)
- [Polymorphisme](../../programming-guide/classes-and-structs/polymorphism.md)
