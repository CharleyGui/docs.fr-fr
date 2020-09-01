---
description: private, mot clé - Référence C#
title: private, mot clé - Référence C#
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: e6f40712fd2cca6d7b1f64760f1c6c5dd5c71370
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139396"
---
# <a name="private-c-reference"></a><span data-ttu-id="d262b-103">private (référence C#)</span><span class="sxs-lookup"><span data-stu-id="d262b-103">private (C# Reference)</span></span>

<span data-ttu-id="d262b-104">Le mot clé `private` est un modificateur d’accès de membre.</span><span class="sxs-lookup"><span data-stu-id="d262b-104">The `private` keyword is a member access modifier.</span></span>

> <span data-ttu-id="d262b-105">Cette page traite de l’accès `private`.</span><span class="sxs-lookup"><span data-stu-id="d262b-105">This page covers `private` access.</span></span> <span data-ttu-id="d262b-106">Le `private` mot clé fait également partie du [`private protected`](./private-protected.md) modificateur d’accès.</span><span class="sxs-lookup"><span data-stu-id="d262b-106">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>

<span data-ttu-id="d262b-107">L’accès privé est le niveau d’accès le moins permissif.</span><span class="sxs-lookup"><span data-stu-id="d262b-107">Private access is the least permissive access level.</span></span> <span data-ttu-id="d262b-108">Les membres privés sont accessibles uniquement dans le corps de la classe ou le struct dans lequel ils sont déclarés, comme dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="d262b-108">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

<span data-ttu-id="d262b-109">Les types imbriqués dans le même corps peuvent également accéder à ces membres privés.</span><span class="sxs-lookup"><span data-stu-id="d262b-109">Nested types in the same body can also access those private members.</span></span>

<span data-ttu-id="d262b-110">Référencer un membre privé en dehors d'une classe ou d'un struct où il est déclaré serait à l'origine d'une erreur de compilation.</span><span class="sxs-lookup"><span data-stu-id="d262b-110">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>

<span data-ttu-id="d262b-111">Pour obtenir une comparaison de `private` et des autres modificateurs d’accès, consultez [Niveaux d’accessibilité](accessibility-levels.md) et [Modificateurs d’accès](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="d262b-111">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

## <a name="example"></a><span data-ttu-id="d262b-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="d262b-112">Example</span></span>

<span data-ttu-id="d262b-113">Dans cet exemple, la classe `Employee` contient deux membres de données privés, `name` et `salary`.</span><span class="sxs-lookup"><span data-stu-id="d262b-113">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="d262b-114">S’agissant de membres privés, ils sont accessibles uniquement par les méthodes membres.</span><span class="sxs-lookup"><span data-stu-id="d262b-114">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="d262b-115">Les méthodes publiques `GetName` et `Salary` sont ajoutées pour permettre un accès contrôlé aux membres privés.</span><span class="sxs-lookup"><span data-stu-id="d262b-115">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="d262b-116">Le membre `name` est accessible via une méthode publique et le membre `salary` est accessible via une propriété publique en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="d262b-116">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="d262b-117">(Pour plus d’informations, consultez [Propriétés](../../programming-guide/classes-and-structs/properties.md).)</span><span class="sxs-lookup"><span data-stu-id="d262b-117">(See [Properties](../../programming-guide/classes-and-structs/properties.md) for more information.)</span></span>

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a><span data-ttu-id="d262b-118">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="d262b-118">C# language specification</span></span>  

<span data-ttu-id="d262b-119">Pour plus d’informations, consultez [Accessibilité déclarée](~/_csharplang/spec/basic-concepts.md#declared-accessibility) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="d262b-119">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="d262b-120">La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="d262b-120">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="d262b-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d262b-121">See also</span></span>

- [<span data-ttu-id="d262b-122">Référence C#</span><span class="sxs-lookup"><span data-stu-id="d262b-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d262b-123">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="d262b-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d262b-124">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="d262b-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d262b-125">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="d262b-125">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="d262b-126">Niveaux d'accessibilité</span><span class="sxs-lookup"><span data-stu-id="d262b-126">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="d262b-127">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="d262b-127">Modifiers</span></span>](index.md)
- [<span data-ttu-id="d262b-128">public</span><span class="sxs-lookup"><span data-stu-id="d262b-128">public</span></span>](public.md)
- [<span data-ttu-id="d262b-129">protected</span><span class="sxs-lookup"><span data-stu-id="d262b-129">protected</span></span>](protected.md)
- [<span data-ttu-id="d262b-130">intérieurs</span><span class="sxs-lookup"><span data-stu-id="d262b-130">internal</span></span>](internal.md)
