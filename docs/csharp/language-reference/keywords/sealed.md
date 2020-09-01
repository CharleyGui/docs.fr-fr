---
description: modificateur sealed - Référence C#
title: modificateur sealed - Référence C#
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: 5b945503c6f6546f571a2422ae77760da0363b08
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136965"
---
# <a name="sealed-c-reference"></a><span data-ttu-id="55ef3-103">sealed (référence C#)</span><span class="sxs-lookup"><span data-stu-id="55ef3-103">sealed (C# Reference)</span></span>

<span data-ttu-id="55ef3-104">Lorsqu’il est appliqué à une classe, le modificateur `sealed` empêche les autres classes d’en hériter.</span><span class="sxs-lookup"><span data-stu-id="55ef3-104">When applied to a class, the `sealed` modifier prevents other classes from inheriting from it.</span></span> <span data-ttu-id="55ef3-105">Dans l’exemple suivant, la classe `B` hérite de la classe `A`, mais aucune classe ne peut hériter de la classe `B`.</span><span class="sxs-lookup"><span data-stu-id="55ef3-105">In the following example, class `B` inherits from class `A`, but no class can inherit from class `B`.</span></span>

```csharp
class A {}
sealed class B : A {}
```

<span data-ttu-id="55ef3-106">Vous pouvez également utiliser le modificateur `sealed` sur une méthode ou une propriété qui substitue une méthode ou une propriété virtuelle dans une classe de base.</span><span class="sxs-lookup"><span data-stu-id="55ef3-106">You can also use the `sealed` modifier on a method or property that overrides a virtual method or property in a base class.</span></span> <span data-ttu-id="55ef3-107">Ainsi, vous pouvez autoriser les classes à dériver de votre classe et les empêcher de substituer des méthodes ou des propriétés virtuelles spécifiques.</span><span class="sxs-lookup"><span data-stu-id="55ef3-107">This enables you to allow classes to derive from your class and prevent them from overriding specific virtual methods or properties.</span></span>

## <a name="example"></a><span data-ttu-id="55ef3-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="55ef3-108">Example</span></span>

<span data-ttu-id="55ef3-109">Dans l’exemple suivant, `Z` hérite de `Y` mais `Z` ne peut pas substituer la fonction virtuelle `F` qui est déclarée dans `X` et scellée (sealed) dans `Y`.</span><span class="sxs-lookup"><span data-stu-id="55ef3-109">In the following example, `Z` inherits from `Y` but `Z` cannot override the virtual function `F` that is declared in `X` and sealed in `Y`.</span></span>

[!code-csharp[csrefKeywordsModifiers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#16)]

<span data-ttu-id="55ef3-110">Lorsque vous définissez de nouvelles méthodes ou propriétés dans une classe, vous pouvez empêcher les classes dérivées de les substituer en ne les déclarant pas comme [virtuelles](virtual.md).</span><span class="sxs-lookup"><span data-stu-id="55ef3-110">When you define new methods or properties in a class, you can prevent deriving classes from overriding them by not declaring them as [virtual](virtual.md).</span></span>

<span data-ttu-id="55ef3-111">Une erreur consiste à utiliser le modificateur [abstract](abstract.md) avec une classe sealed, car une classe abstraite doit être héritée par une classe qui fournit une implémentation des méthodes ou des propriétés abstraites.</span><span class="sxs-lookup"><span data-stu-id="55ef3-111">It is an error to use the [abstract](abstract.md) modifier with a sealed class, because an abstract class must be inherited by a class that provides an implementation of the abstract methods or properties.</span></span>

<span data-ttu-id="55ef3-112">Lorsqu’il est appliqué à une méthode ou une propriété, le modificateur `sealed` doit toujours être utilisé avec [override](override.md).</span><span class="sxs-lookup"><span data-stu-id="55ef3-112">When applied to a method or property, the `sealed` modifier must always be used with [override](override.md).</span></span>

<span data-ttu-id="55ef3-113">Comme les structs sont implicitement sealed, ils ne peuvent pas être hérités.</span><span class="sxs-lookup"><span data-stu-id="55ef3-113">Because structs are implicitly sealed, they cannot be inherited.</span></span>

<span data-ttu-id="55ef3-114">Pour plus d’informations, consultez [Héritage](../../programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="55ef3-114">For more information, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="55ef3-115">Pour plus d’exemples, consultez [Classes abstract et sealed et membres de classe](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="55ef3-115">For more examples, see [Abstract and Sealed Classes and Class Members](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="55ef3-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="55ef3-116">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#17)]

<span data-ttu-id="55ef3-117">Dans l’exemple précédent, vous pouvez essayer d’hériter de la classe sealed à l’aide de l’instruction suivante :</span><span class="sxs-lookup"><span data-stu-id="55ef3-117">In the previous example, you might try to inherit from the sealed class by using the following statement:</span></span>

`class MyDerivedC: SealedClass {}   // Error`

<span data-ttu-id="55ef3-118">Le résultat est un message d’erreur :</span><span class="sxs-lookup"><span data-stu-id="55ef3-118">The result is an error message:</span></span>

`'MyDerivedC': cannot derive from sealed type 'SealedClass'`

## <a name="remarks"></a><span data-ttu-id="55ef3-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="55ef3-119">Remarks</span></span>

<span data-ttu-id="55ef3-120">Pour déterminer s’il faut sceller une classe, une méthode ou une propriété, vous devez généralement prendre en compte les deux points suivants :</span><span class="sxs-lookup"><span data-stu-id="55ef3-120">To determine whether to seal a class, method, or property, you should generally consider the following two points:</span></span>

- <span data-ttu-id="55ef3-121">Les avantages potentiels dont les classes dérivées peuvent bénéficier grâce à la possibilité de personnaliser votre classe.</span><span class="sxs-lookup"><span data-stu-id="55ef3-121">The potential benefits that deriving classes might gain through the ability to customize your class.</span></span>

- <span data-ttu-id="55ef3-122">Le risque que les classes dérivées puissent modifier vos classes de telle manière qu’elles ne fonctionnent plus correctement ou comme prévu.</span><span class="sxs-lookup"><span data-stu-id="55ef3-122">The potential that deriving classes could modify your classes in such a way that they would no longer work correctly or as expected.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="55ef3-123">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="55ef3-123">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="55ef3-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55ef3-124">See also</span></span>

- [<span data-ttu-id="55ef3-125">Référence C#</span><span class="sxs-lookup"><span data-stu-id="55ef3-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="55ef3-126">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="55ef3-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="55ef3-127">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="55ef3-127">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="55ef3-128">Classes statiques et membres de classe statique</span><span class="sxs-lookup"><span data-stu-id="55ef3-128">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [<span data-ttu-id="55ef3-129">Classes abstract et sealed et membres de classe</span><span class="sxs-lookup"><span data-stu-id="55ef3-129">Abstract and Sealed Classes and Class Members</span></span>](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="55ef3-130">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="55ef3-130">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="55ef3-131">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="55ef3-131">Modifiers</span></span>](index.md)
- [<span data-ttu-id="55ef3-132">remplacer</span><span class="sxs-lookup"><span data-stu-id="55ef3-132">override</span></span>](override.md)
- [<span data-ttu-id="55ef3-133">virtual</span><span class="sxs-lookup"><span data-stu-id="55ef3-133">virtual</span></span>](virtual.md)
