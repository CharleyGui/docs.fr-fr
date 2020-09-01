---
description: override, modificateur - Référence C#
title: override, modificateur - Référence C#
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 51ca806310214981b7ff24a796fe078d902dca4d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134456"
---
# <a name="override-c-reference"></a><span data-ttu-id="4a7ac-103">override (référence C#)</span><span class="sxs-lookup"><span data-stu-id="4a7ac-103">override (C# Reference)</span></span>

<span data-ttu-id="4a7ac-104">Le modificateur `override` est nécessaire pour étendre ou modifier l’implémentation abstraite ou virtuelle d’une méthode, d’une propriété, d’un indexeur ou d’un événement hérités.</span><span class="sxs-lookup"><span data-stu-id="4a7ac-104">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>

## <a name="example"></a><span data-ttu-id="4a7ac-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="4a7ac-105">Example</span></span>

<span data-ttu-id="4a7ac-106">Dans cet exemple, la `Square` classe doit fournir une implémentation substituée de `GetArea` , car `GetArea` est héritée de la classe abstraite `Shape` :</span><span class="sxs-lookup"><span data-stu-id="4a7ac-106">In this example, the `Square` class must provide an overridden implementation of `GetArea` because `GetArea` is inherited from the abstract `Shape` class:</span></span>

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

<span data-ttu-id="4a7ac-107">Une méthode `override` fournit une nouvelle implémentation d’un membre hérité d’une classe de base.</span><span class="sxs-lookup"><span data-stu-id="4a7ac-107">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="4a7ac-108">La méthode substituée par une déclaration `override` est appelée méthode de base substituée.</span><span class="sxs-lookup"><span data-stu-id="4a7ac-108">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="4a7ac-109">La méthode de base substituée doit avoir la même signature que la méthode `override`.</span><span class="sxs-lookup"><span data-stu-id="4a7ac-109">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="4a7ac-110">Pour plus d’informations sur l’héritage, consultez [Héritage](../../programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="4a7ac-110">For information about inheritance, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="4a7ac-111">Vous ne pouvez pas surcharger une méthode statique ou non virtuelle.</span><span class="sxs-lookup"><span data-stu-id="4a7ac-111">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="4a7ac-112">La méthode de base substituée doit être `virtual`, `abstract` ou `override`.</span><span class="sxs-lookup"><span data-stu-id="4a7ac-112">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="4a7ac-113">Une déclaration `override` ne peut pas changer l’accessibilité de la méthode `virtual`.</span><span class="sxs-lookup"><span data-stu-id="4a7ac-113">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="4a7ac-114">Les deux méthodes `override` et `virtual` doivent avoir le même [modificateur de niveau d’accès](access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="4a7ac-114">Both the `override` method and the `virtual` method must have the same [access level modifier](access-modifiers.md).</span></span>

<span data-ttu-id="4a7ac-115">Vous ne pouvez pas utiliser les modificateurs `new`, `static` ou `virtual` pour modifier une méthode `override`.</span><span class="sxs-lookup"><span data-stu-id="4a7ac-115">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>

<span data-ttu-id="4a7ac-116">Une déclaration de propriété de substitution doit spécifier exactement les mêmes modificateur d’accès, type et nom que la propriété héritée, et la propriété substituée doit être `virtual`, `abstract` ou `override`.</span><span class="sxs-lookup"><span data-stu-id="4a7ac-116">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="4a7ac-117">Pour plus d’informations sur l’utilisation du mot clé `override`, consultez [Gestion de version avec les mots clés override et new](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) et [Savoir quand utiliser les mots clés override et new](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="4a7ac-117">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="example"></a><span data-ttu-id="4a7ac-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="4a7ac-118">Example</span></span>

<span data-ttu-id="4a7ac-119">Cet exemple définit une classe de base nommée `Employee` et une classe dérivée nommée `SalesEmployee`.</span><span class="sxs-lookup"><span data-stu-id="4a7ac-119">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="4a7ac-120">La classe `SalesEmployee` inclut un champ supplémentaire (`salesbonus`) et substitue la méthode `CalculatePay` afin de la prendre en compte.</span><span class="sxs-lookup"><span data-stu-id="4a7ac-120">The `SalesEmployee` class includes an extra field, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="4a7ac-121">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="4a7ac-121">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="4a7ac-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a7ac-122">See also</span></span>

- [<span data-ttu-id="4a7ac-123">Référence C#</span><span class="sxs-lookup"><span data-stu-id="4a7ac-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4a7ac-124">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="4a7ac-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4a7ac-125">Héritage</span><span class="sxs-lookup"><span data-stu-id="4a7ac-125">Inheritance</span></span>](../../programming-guide/classes-and-structs/inheritance.md)
- [<span data-ttu-id="4a7ac-126">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="4a7ac-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="4a7ac-127">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="4a7ac-127">Modifiers</span></span>](index.md)
- [<span data-ttu-id="4a7ac-128">abstraction</span><span class="sxs-lookup"><span data-stu-id="4a7ac-128">abstract</span></span>](abstract.md)
- [<span data-ttu-id="4a7ac-129">virtual</span><span class="sxs-lookup"><span data-stu-id="4a7ac-129">virtual</span></span>](virtual.md)
- [<span data-ttu-id="4a7ac-130">new (modificateur)</span><span class="sxs-lookup"><span data-stu-id="4a7ac-130">new (modifier)</span></span>](new-modifier.md)
- [<span data-ttu-id="4a7ac-131">Polymorphisme</span><span class="sxs-lookup"><span data-stu-id="4a7ac-131">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
