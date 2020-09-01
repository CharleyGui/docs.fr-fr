---
description: unsafe, mot clé -Référence C#
title: unsafe, mot clé -Référence C#
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: 2e047a4cff77877862c5cbbb5e49eb1a75b42499
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141957"
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="cee86-103">unsafe (référence C#)</span><span class="sxs-lookup"><span data-stu-id="cee86-103">unsafe (C# Reference)</span></span>

<span data-ttu-id="cee86-104">Le mot clé `unsafe` désigne un contexte non sécurisé, qui est requis pour toute opération impliquant des pointeurs.</span><span class="sxs-lookup"><span data-stu-id="cee86-104">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="cee86-105">Pour plus d’informations, consultez [Pointeurs et code unsafe](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="cee86-105">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="cee86-106">Vous pouvez utiliser le modificateur `unsafe` dans la déclaration d’un type ou d’un membre.</span><span class="sxs-lookup"><span data-stu-id="cee86-106">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="cee86-107">Toute l’étendue de texte du type ou du membre est ainsi considérée comme un contexte unsafe.</span><span class="sxs-lookup"><span data-stu-id="cee86-107">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="cee86-108">Par exemple, ce qui suit est une méthode déclarée avec le modificateur `unsafe` :</span><span class="sxs-lookup"><span data-stu-id="cee86-108">For example, the following is a method declared with the `unsafe` modifier:</span></span>

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="cee86-109">La portée du contexte unsafe s’étend de la liste de paramètres à la fin de la méthode, de sorte que les pointeurs peuvent également être utilisés dans la liste de paramètres :</span><span class="sxs-lookup"><span data-stu-id="cee86-109">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

<span data-ttu-id="cee86-110">Vous pouvez également avoir recours à un bloc unsafe pour utiliser un code unsafe dans ce bloc.</span><span class="sxs-lookup"><span data-stu-id="cee86-110">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="cee86-111">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="cee86-111">For example:</span></span>

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="cee86-112">Pour compiler du code unsafe, vous devez spécifier l' [`-unsafe`](../compiler-options/unsafe-compiler-option.md) option du compilateur.</span><span class="sxs-lookup"><span data-stu-id="cee86-112">To compile unsafe code, you must specify the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="cee86-113">Le code unsafe n’est pas vérifiable par le service CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="cee86-113">Unsafe code is not verifiable by the common language runtime.</span></span>

## <a name="example"></a><span data-ttu-id="cee86-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="cee86-114">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a><span data-ttu-id="cee86-115">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="cee86-115">C# language specification</span></span>

<span data-ttu-id="cee86-116">Pour plus d’informations, voir [Code unsafe](~/_csharplang/spec/unsafe-code.md) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="cee86-116">For more information, see [Unsafe code](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="cee86-117">La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="cee86-117">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="cee86-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cee86-118">See also</span></span>

- [<span data-ttu-id="cee86-119">Référence C#</span><span class="sxs-lookup"><span data-stu-id="cee86-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cee86-120">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="cee86-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cee86-121">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="cee86-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="cee86-122">fixed, instruction</span><span class="sxs-lookup"><span data-stu-id="cee86-122">fixed Statement</span></span>](fixed-statement.md)
- [<span data-ttu-id="cee86-123">Pointeurs et code unsafe</span><span class="sxs-lookup"><span data-stu-id="cee86-123">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="cee86-124">Mémoires tampons de taille fixe</span><span class="sxs-lookup"><span data-stu-id="cee86-124">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
