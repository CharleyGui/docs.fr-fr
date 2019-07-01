---
title: base, mot clé - Référence C#
ms.custom: seodec18
description: Découvrez le mot clé base, qui sert à accéder aux membres de la classe de base à partir d’une classe dérivée en C#.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: 2ef0d07aed595fa630459171482e0b0849aed877
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401592"
---
# <a name="base-c-reference"></a><span data-ttu-id="f7789-103">base (référence C#)</span><span class="sxs-lookup"><span data-stu-id="f7789-103">base (C# Reference)</span></span>

<span data-ttu-id="f7789-104">Le mot clé `base` sert à accéder aux membres de la classe de base à partir d’une classe dérivée :</span><span class="sxs-lookup"><span data-stu-id="f7789-104">The `base` keyword is used to access members of the base class from within a derived class:</span></span>

- <span data-ttu-id="f7789-105">Il appelle une méthode de la classe de base qui a été substituée par une autre méthode.</span><span class="sxs-lookup"><span data-stu-id="f7789-105">Call a method on the base class that has been overridden by another method.</span></span>

- <span data-ttu-id="f7789-106">Il spécifie quel constructeur de classe de base doit être appelé lors de la création d’instances de la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="f7789-106">Specify which base-class constructor should be called when creating instances of the derived class.</span></span>

<span data-ttu-id="f7789-107">L’accès à une classe de base est autorisé uniquement dans un constructeur, une méthode d’instance ou un accesseur de propriété d’instance.</span><span class="sxs-lookup"><span data-stu-id="f7789-107">A base class access is permitted only in a constructor, an instance method, or an instance property accessor.</span></span>

<span data-ttu-id="f7789-108">L’utilisation du mot clé `base` à partir d’une méthode statique est une erreur.</span><span class="sxs-lookup"><span data-stu-id="f7789-108">It is an error to use the `base` keyword from within a static method.</span></span>

<span data-ttu-id="f7789-109">La classe de base accessible est la classe de base spécifiée dans la déclaration de classe.</span><span class="sxs-lookup"><span data-stu-id="f7789-109">The base class that is accessed is the base class specified in the class declaration.</span></span> <span data-ttu-id="f7789-110">Par exemple, si vous spécifiez `class ClassB : ClassA`, les membres de ClassA sont accessibles à partir de ClassB, quelle que soit la classe de base de ClassA.</span><span class="sxs-lookup"><span data-stu-id="f7789-110">For example, if you specify `class ClassB : ClassA`, the members of ClassA are accessed from ClassB, regardless of the base class of ClassA.</span></span>

## <a name="example"></a><span data-ttu-id="f7789-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="f7789-111">Example</span></span>

<span data-ttu-id="f7789-112">Dans cet exemple, la classe de base `Person` et la classe dérivée `Employee` ont toutes les deux une méthode nommée `Getinfo`.</span><span class="sxs-lookup"><span data-stu-id="f7789-112">In this example, both the base class, `Person`, and the derived class, `Employee`, have a method named `Getinfo`.</span></span> <span data-ttu-id="f7789-113">En utilisant le mot clé `base`, vous pouvez appeler la méthode `Getinfo` de la classe de base à partir de la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="f7789-113">By using the `base` keyword, it is possible to call the `Getinfo` method on the base class, from within the derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#1)]

<span data-ttu-id="f7789-114">Pour obtenir d’autres exemples, consultez [new](new-modifier.md), [virtual](virtual.md) et [override](override.md).</span><span class="sxs-lookup"><span data-stu-id="f7789-114">For additional examples, see [new](new-modifier.md), [virtual](virtual.md), and [override](override.md).</span></span>

## <a name="example"></a><span data-ttu-id="f7789-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="f7789-115">Example</span></span>

<span data-ttu-id="f7789-116">Cet exemple montre comment spécifier le constructeur de classe de base qui est appelé lors de la création d’instances d’une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="f7789-116">This example shows how to specify the base-class constructor called when creating instances of a derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="f7789-117">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="f7789-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f7789-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7789-118">See also</span></span>

- [<span data-ttu-id="f7789-119">Référence C#</span><span class="sxs-lookup"><span data-stu-id="f7789-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="f7789-120">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="f7789-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="f7789-121">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="f7789-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="f7789-122">this</span><span class="sxs-lookup"><span data-stu-id="f7789-122">this</span></span>](../../../csharp/language-reference/keywords/this.md)
