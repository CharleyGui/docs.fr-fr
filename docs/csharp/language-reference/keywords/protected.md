---
description: protected, mot clé - Référence C#
title: protected, mot clé - Référence C#
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: af0c7ab5ebb6980bb0381e46fd38e9470f3a2152
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90536754"
---
# <a name="protected-c-reference"></a><span data-ttu-id="5e954-103">protected (référence C#)</span><span class="sxs-lookup"><span data-stu-id="5e954-103">protected (C# Reference)</span></span>

<span data-ttu-id="5e954-104">Le mot clé `protected` est un modificateur d’accès de membre.</span><span class="sxs-lookup"><span data-stu-id="5e954-104">The `protected` keyword is a member access modifier.</span></span>

 > <span data-ttu-id="5e954-105">Cette page traite de l’accès `protected`.</span><span class="sxs-lookup"><span data-stu-id="5e954-105">This page covers `protected` access.</span></span> <span data-ttu-id="5e954-106">Le `protected` mot clé fait également partie des [`protected internal`](protected-internal.md) [`private protected`](private-protected.md) modificateurs d’accès et.</span><span class="sxs-lookup"><span data-stu-id="5e954-106">The `protected` keyword is also part of the [`protected internal`](protected-internal.md) and [`private protected`](private-protected.md) access modifiers.</span></span>

<span data-ttu-id="5e954-107">Un membre protégé est accessible dans sa classe et par les instances de la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="5e954-107">A protected member is accessible within its class and by derived class instances.</span></span>

<span data-ttu-id="5e954-108">Pour obtenir une comparaison de `protected` et des autres modificateurs d’accès, consultez [Niveaux d’accessibilité](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="5e954-108">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="5e954-109"> Exemple</span><span class="sxs-lookup"><span data-stu-id="5e954-109">Example</span></span>

<span data-ttu-id="5e954-110">Un membre protégé d’une classe de base est accessible dans une classe dérivée uniquement si l’accès s’effectue par le biais du type de la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="5e954-110">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="5e954-111">Prenons l’exemple de l’extrait de code suivant :</span><span class="sxs-lookup"><span data-stu-id="5e954-111">For example, consider the following code segment:</span></span>

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

<span data-ttu-id="5e954-112">L’instruction `a.x = 10` génère une erreur, car elle est appelée dans la méthode statique Main, et pas dans une instance de la classe B.</span><span class="sxs-lookup"><span data-stu-id="5e954-112">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>

<span data-ttu-id="5e954-113">Les membres de struct ne peuvent pas être protégés, car le struct ne peut pas être hérité.</span><span class="sxs-lookup"><span data-stu-id="5e954-113">Struct members cannot be protected because the struct cannot be inherited.</span></span>

## <a name="example"></a><span data-ttu-id="5e954-114"> Exemple</span><span class="sxs-lookup"><span data-stu-id="5e954-114">Example</span></span>

<span data-ttu-id="5e954-115">Dans cet exemple, la classe `DerivedPoint` est dérivée de `Point`.</span><span class="sxs-lookup"><span data-stu-id="5e954-115">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="5e954-116">Vous pouvez donc accéder aux membres protégés de la classe de base directement à partir de la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="5e954-116">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

<span data-ttu-id="5e954-117">Si vous changez les niveaux d’accès de `x` et `y` à [private](private.md), le compilateur affiche les messages d’erreur suivants :</span><span class="sxs-lookup"><span data-stu-id="5e954-117">If you change the access levels of `x` and `y` to [private](private.md), the compiler will issue the error messages:</span></span>

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a><span data-ttu-id="5e954-118">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="5e954-118">C# language specification</span></span>  

<span data-ttu-id="5e954-119">Pour plus d’informations, consultez [Accessibilité déclarée](~/_csharplang/spec/basic-concepts.md#declared-accessibility) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="5e954-119">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="5e954-120">La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="5e954-120">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e954-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e954-121">See also</span></span>

- [<span data-ttu-id="5e954-122">Référence C#</span><span class="sxs-lookup"><span data-stu-id="5e954-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5e954-123">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="5e954-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5e954-124">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="5e954-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="5e954-125">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="5e954-125">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="5e954-126">Niveaux d'accessibilité</span><span class="sxs-lookup"><span data-stu-id="5e954-126">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="5e954-127">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="5e954-127">Modifiers</span></span>](index.md)
- [<span data-ttu-id="5e954-128">public</span><span class="sxs-lookup"><span data-stu-id="5e954-128">public</span></span>](public.md)
- [<span data-ttu-id="5e954-129">private</span><span class="sxs-lookup"><span data-stu-id="5e954-129">private</span></span>](private.md)
- [<span data-ttu-id="5e954-130">intérieurs</span><span class="sxs-lookup"><span data-stu-id="5e954-130">internal</span></span>](internal.md)
- <span data-ttu-id="5e954-131">[Problèmes de sécurité pour les mots clés virtuels internes](/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5e954-131">[Security concerns for internal virtual keywords](/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
