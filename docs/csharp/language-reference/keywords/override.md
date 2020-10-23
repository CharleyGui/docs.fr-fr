---
description: override, modificateur - Référence C#
title: override, modificateur - Référence C#
ms.date: 10/22/2020
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 618200183348e68a4600adb9592a635f61f6a875
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434874"
---
# <a name="override-c-reference"></a>override (référence C#)

Le modificateur `override` est nécessaire pour étendre ou modifier l’implémentation abstraite ou virtuelle d’une méthode, d’une propriété, d’un indexeur ou d’un événement hérités.

Dans l’exemple suivant, la `Square` classe doit fournir une implémentation substituée de `GetArea` , car `GetArea` est héritée de la classe abstraite `Shape` :

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

Une `override` méthode fournit une nouvelle implémentation de la méthode héritée d’une classe de base. La méthode substituée par une déclaration `override` est appelée méthode de base substituée. Une `override` méthode doit avoir la même signature que la méthode de base substituée. À compter de C# 9,0, les `override` méthodes prennent en charge les types de retour covariants. En particulier, le type de retour d’une `override` méthode peut dériver du type de retour de la méthode de base correspondante. Dans C# 8,0 et les versions antérieures, les types de retour d’une `override` méthode et la méthode de base substituée doivent être identiques.

Vous ne pouvez pas surcharger une méthode statique ou non virtuelle. La méthode de base substituée doit être `virtual`, `abstract` ou `override`.

Une déclaration `override` ne peut pas changer l’accessibilité de la méthode `virtual`. Les deux méthodes `override` et `virtual` doivent avoir le même [modificateur de niveau d’accès](access-modifiers.md).

Vous ne pouvez pas utiliser les modificateurs `new`, `static` ou `virtual` pour modifier une méthode `override`.

Une déclaration de propriété de substitution doit spécifier exactement le même modificateur d’accès, le même type et le même nom que la propriété héritée. À compter de C# 9,0, les propriétés de substitution en lecture seule prennent en charge les types de retour covariants. La propriété substituée doit être `virtual` , `abstract` ou `override` .

Pour plus d’informations sur l’utilisation du mot clé `override`, consultez [Gestion de version avec les mots clés override et new](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) et [Savoir quand utiliser les mots clés override et new](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md). Pour plus d’informations sur l’héritage, consultez [Héritage](../../programming-guide/classes-and-structs/inheritance.md).

## <a name="example"></a>Exemple

Cet exemple définit une classe de base nommée `Employee` et une classe dérivée nommée `SalesEmployee`. La classe `SalesEmployee` inclut un champ supplémentaire (`salesbonus`) et substitue la méthode `CalculatePay` afin de la prendre en compte.

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [méthodes de substitution](~/_csharplang/spec/classes.md#override-methods) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

Pour plus d’informations sur les types de retour covariants, consultez la [Remarque relative](~/_csharplang/proposals/csharp-9.0/covariant-returns.md)à la proposition de fonctionnalité.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Héritage](../../programming-guide/classes-and-structs/inheritance.md)
- [Mots clés C#](index.md)
- [Modificateurs](index.md)
- [abstraction](abstract.md)
- [virtuels](virtual.md)
- [new (modificateur)](new-modifier.md)
- [Polymorphisme](../../programming-guide/classes-and-structs/polymorphism.md)
