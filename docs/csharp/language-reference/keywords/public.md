---
description: public, mot clé - Référence C#
title: public, mot clé - Référence C#
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 90c1d2a1d9efcdf57f914f4318bf7a743d3f37ec
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938466"
---
# <a name="public-c-reference"></a><span data-ttu-id="613c0-103">public (référence C#)</span><span class="sxs-lookup"><span data-stu-id="613c0-103">public (C# Reference)</span></span>

<span data-ttu-id="613c0-104">Le mot clé `public` est un modificateur d’accès pour les types et les membres de types.</span><span class="sxs-lookup"><span data-stu-id="613c0-104">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="613c0-105">L’accès public est le niveau d’accès le plus permissif.</span><span class="sxs-lookup"><span data-stu-id="613c0-105">Public access is the most permissive access level.</span></span> <span data-ttu-id="613c0-106">Il n’existe pas de restrictions d’accès aux membres publics, comme dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="613c0-106">There are no restrictions on accessing public members, as in this example:</span></span>

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

<span data-ttu-id="613c0-107">Pour plus d’informations, consultez [Modificateurs d’accès](../../programming-guide/classes-and-structs/access-modifiers.md) et [Niveaux d’accessibilité](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="613c0-107">See [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](accessibility-levels.md) for more information.</span></span>

## <a name="example"></a><span data-ttu-id="613c0-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="613c0-108">Example</span></span>

<span data-ttu-id="613c0-109">Dans l’exemple suivant, deux classes sont déclarées, `PointTest` et `Program`.</span><span class="sxs-lookup"><span data-stu-id="613c0-109">In the following example, two classes are declared, `PointTest` and `Program`.</span></span> <span data-ttu-id="613c0-110">L’accès aux membres publics `x` et `y` de `PointTest` s’effectue directement à partir de `Program`.</span><span class="sxs-lookup"><span data-stu-id="613c0-110">The public members `x` and `y` of `PointTest` are accessed directly from `Program`.</span></span>

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

<span data-ttu-id="613c0-111">Si vous remplacez le niveau d’accès `public` par [private](private.md) ou [protected](protected.md), le message d’erreur suivant s’affiche :</span><span class="sxs-lookup"><span data-stu-id="613c0-111">If you change the `public` access level to [private](private.md) or [protected](protected.md), you will get the error message:</span></span>

<span data-ttu-id="613c0-112">'PointTest.y' est inaccessible en raison de son niveau de protection.</span><span class="sxs-lookup"><span data-stu-id="613c0-112">'PointTest.y' is inaccessible due to its protection level.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="613c0-113">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="613c0-113">C# language specification</span></span>  

<span data-ttu-id="613c0-114">Pour plus d’informations, consultez [Accessibilité déclarée](~/_csharplang/spec/basic-concepts.md#declared-accessibility) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="613c0-114">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="613c0-115">La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="613c0-115">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="613c0-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="613c0-116">See also</span></span>

- [<span data-ttu-id="613c0-117">Référence C#</span><span class="sxs-lookup"><span data-stu-id="613c0-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="613c0-118">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="613c0-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="613c0-119">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="613c0-119">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="613c0-120">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="613c0-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="613c0-121">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="613c0-121">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="613c0-122">Niveaux d'accessibilité</span><span class="sxs-lookup"><span data-stu-id="613c0-122">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="613c0-123">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="613c0-123">Modifiers</span></span>](index.md)
- [<span data-ttu-id="613c0-124">priv</span><span class="sxs-lookup"><span data-stu-id="613c0-124">private</span></span>](private.md)
- [<span data-ttu-id="613c0-125">protected</span><span class="sxs-lookup"><span data-stu-id="613c0-125">protected</span></span>](protected.md)
- [<span data-ttu-id="613c0-126">intérieurs</span><span class="sxs-lookup"><span data-stu-id="613c0-126">internal</span></span>](internal.md)
