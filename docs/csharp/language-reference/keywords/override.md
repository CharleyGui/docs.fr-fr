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
# <a name="override-c-reference"></a><span data-ttu-id="049f5-103">override (référence C#)</span><span class="sxs-lookup"><span data-stu-id="049f5-103">override (C# reference)</span></span>

<span data-ttu-id="049f5-104">Le modificateur `override` est nécessaire pour étendre ou modifier l’implémentation abstraite ou virtuelle d’une méthode, d’une propriété, d’un indexeur ou d’un événement hérités.</span><span class="sxs-lookup"><span data-stu-id="049f5-104">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>

<span data-ttu-id="049f5-105">Dans l’exemple suivant, la `Square` classe doit fournir une implémentation substituée de `GetArea` , car `GetArea` est héritée de la classe abstraite `Shape` :</span><span class="sxs-lookup"><span data-stu-id="049f5-105">In the following example, the `Square` class must provide an overridden implementation of `GetArea` because `GetArea` is inherited from the abstract `Shape` class:</span></span>

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

<span data-ttu-id="049f5-106">Une `override` méthode fournit une nouvelle implémentation de la méthode héritée d’une classe de base.</span><span class="sxs-lookup"><span data-stu-id="049f5-106">An `override` method provides a new implementation of the method inherited from a base class.</span></span> <span data-ttu-id="049f5-107">La méthode substituée par une déclaration `override` est appelée méthode de base substituée.</span><span class="sxs-lookup"><span data-stu-id="049f5-107">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="049f5-108">Une `override` méthode doit avoir la même signature que la méthode de base substituée.</span><span class="sxs-lookup"><span data-stu-id="049f5-108">An `override` method must have the same signature as the overridden base method.</span></span> <span data-ttu-id="049f5-109">À compter de C# 9,0, les `override` méthodes prennent en charge les types de retour covariants.</span><span class="sxs-lookup"><span data-stu-id="049f5-109">Beginning with C# 9.0, `override` methods support covariant return types.</span></span> <span data-ttu-id="049f5-110">En particulier, le type de retour d’une `override` méthode peut dériver du type de retour de la méthode de base correspondante.</span><span class="sxs-lookup"><span data-stu-id="049f5-110">In particular, the return type of an `override` method can derive from the return type of the corresponding base method.</span></span> <span data-ttu-id="049f5-111">Dans C# 8,0 et les versions antérieures, les types de retour d’une `override` méthode et la méthode de base substituée doivent être identiques.</span><span class="sxs-lookup"><span data-stu-id="049f5-111">In C# 8.0 and earlier, the return types of an `override` method and the overridden base method must be the same.</span></span>

<span data-ttu-id="049f5-112">Vous ne pouvez pas surcharger une méthode statique ou non virtuelle.</span><span class="sxs-lookup"><span data-stu-id="049f5-112">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="049f5-113">La méthode de base substituée doit être `virtual`, `abstract` ou `override`.</span><span class="sxs-lookup"><span data-stu-id="049f5-113">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="049f5-114">Une déclaration `override` ne peut pas changer l’accessibilité de la méthode `virtual`.</span><span class="sxs-lookup"><span data-stu-id="049f5-114">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="049f5-115">Les deux méthodes `override` et `virtual` doivent avoir le même [modificateur de niveau d’accès](access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="049f5-115">Both the `override` method and the `virtual` method must have the same [access level modifier](access-modifiers.md).</span></span>

<span data-ttu-id="049f5-116">Vous ne pouvez pas utiliser les modificateurs `new`, `static` ou `virtual` pour modifier une méthode `override`.</span><span class="sxs-lookup"><span data-stu-id="049f5-116">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>

<span data-ttu-id="049f5-117">Une déclaration de propriété de substitution doit spécifier exactement le même modificateur d’accès, le même type et le même nom que la propriété héritée.</span><span class="sxs-lookup"><span data-stu-id="049f5-117">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property.</span></span> <span data-ttu-id="049f5-118">À compter de C# 9,0, les propriétés de substitution en lecture seule prennent en charge les types de retour covariants.</span><span class="sxs-lookup"><span data-stu-id="049f5-118">Beginning with C# 9.0, read-only overriding properties support covariant return types.</span></span> <span data-ttu-id="049f5-119">La propriété substituée doit être `virtual` , `abstract` ou `override` .</span><span class="sxs-lookup"><span data-stu-id="049f5-119">The overridden property must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="049f5-120">Pour plus d’informations sur l’utilisation du mot clé `override`, consultez [Gestion de version avec les mots clés override et new](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) et [Savoir quand utiliser les mots clés override et new](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="049f5-120">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span> <span data-ttu-id="049f5-121">Pour plus d’informations sur l’héritage, consultez [Héritage](../../programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="049f5-121">For information about inheritance, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

## <a name="example"></a><span data-ttu-id="049f5-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="049f5-122">Example</span></span>

<span data-ttu-id="049f5-123">Cet exemple définit une classe de base nommée `Employee` et une classe dérivée nommée `SalesEmployee`.</span><span class="sxs-lookup"><span data-stu-id="049f5-123">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="049f5-124">La classe `SalesEmployee` inclut un champ supplémentaire (`salesbonus`) et substitue la méthode `CalculatePay` afin de la prendre en compte.</span><span class="sxs-lookup"><span data-stu-id="049f5-124">The `SalesEmployee` class includes an extra field, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="049f5-125">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="049f5-125">C# language specification</span></span>

<span data-ttu-id="049f5-126">Pour plus d’informations, consultez la section [méthodes de substitution](~/_csharplang/spec/classes.md#override-methods) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="049f5-126">For more information, see the [Override methods](~/_csharplang/spec/classes.md#override-methods) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="049f5-127">Pour plus d’informations sur les types de retour covariants, consultez la [Remarque relative](~/_csharplang/proposals/csharp-9.0/covariant-returns.md)à la proposition de fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="049f5-127">For more information about covariant return types, see the [feature proposal note](~/_csharplang/proposals/csharp-9.0/covariant-returns.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="049f5-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="049f5-128">See also</span></span>

- [<span data-ttu-id="049f5-129">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="049f5-129">C# reference</span></span>](../index.md)
- [<span data-ttu-id="049f5-130">Héritage</span><span class="sxs-lookup"><span data-stu-id="049f5-130">Inheritance</span></span>](../../programming-guide/classes-and-structs/inheritance.md)
- [<span data-ttu-id="049f5-131">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="049f5-131">C# keywords</span></span>](index.md)
- [<span data-ttu-id="049f5-132">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="049f5-132">Modifiers</span></span>](index.md)
- [<span data-ttu-id="049f5-133">abstraction</span><span class="sxs-lookup"><span data-stu-id="049f5-133">abstract</span></span>](abstract.md)
- [<span data-ttu-id="049f5-134">virtuels</span><span class="sxs-lookup"><span data-stu-id="049f5-134">virtual</span></span>](virtual.md)
- [<span data-ttu-id="049f5-135">new (modificateur)</span><span class="sxs-lookup"><span data-stu-id="049f5-135">new (modifier)</span></span>](new-modifier.md)
- [<span data-ttu-id="049f5-136">Polymorphisme</span><span class="sxs-lookup"><span data-stu-id="049f5-136">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
