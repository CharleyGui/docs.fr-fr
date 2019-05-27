---
title: unsafe, mot clé -Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: bca12c1dd8c79a5ae17e4a9b7b75d3c7b302fb89
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65875875"
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="b375c-102">unsafe (référence C#)</span><span class="sxs-lookup"><span data-stu-id="b375c-102">unsafe (C# Reference)</span></span>

<span data-ttu-id="b375c-103">Le mot clé `unsafe` désigne un contexte non sécurisé, qui est requis pour toute opération impliquant des pointeurs.</span><span class="sxs-lookup"><span data-stu-id="b375c-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="b375c-104">Pour plus d’informations, consultez l’article [Pointeurs et code unsafe](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="b375c-104">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="b375c-105">Vous pouvez utiliser le modificateur `unsafe` dans la déclaration d’un type ou d’un membre.</span><span class="sxs-lookup"><span data-stu-id="b375c-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="b375c-106">Toute l’étendue de texte du type ou du membre est ainsi considérée comme un contexte unsafe.</span><span class="sxs-lookup"><span data-stu-id="b375c-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="b375c-107">Par exemple, ce qui suit est une méthode déclarée avec le modificateur `unsafe` :</span><span class="sxs-lookup"><span data-stu-id="b375c-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="b375c-108">La portée du contexte unsafe s’étend de la liste de paramètres à la fin de la méthode, de sorte que les pointeurs peuvent également être utilisés dans la liste de paramètres :</span><span class="sxs-lookup"><span data-stu-id="b375c-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

<span data-ttu-id="b375c-109">Vous pouvez également avoir recours à un bloc unsafe pour utiliser un code unsafe dans ce bloc.</span><span class="sxs-lookup"><span data-stu-id="b375c-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="b375c-110">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b375c-110">For example:</span></span>

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="b375c-111">Pour compiler du code unsafe, vous devez spécifier l’option de compilateur [`-unsafe`](../compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="b375c-111">To compile unsafe code, you must specify the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="b375c-112">Le code unsafe n’est pas vérifiable par le service CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="b375c-112">Unsafe code is not verifiable by the common language runtime.</span></span>

## <a name="example"></a><span data-ttu-id="b375c-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="b375c-113">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a><span data-ttu-id="b375c-114">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="b375c-114">C# language specification</span></span>

<span data-ttu-id="b375c-115">Pour plus d’informations, voir [Code unsafe](~/_csharplang/spec/unsafe-code.md) dans la [spécification du langage C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="b375c-115">For more information, see [Unsafe code](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="b375c-116">La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="b375c-116">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="b375c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b375c-117">See also</span></span>

- [<span data-ttu-id="b375c-118">Référence C#</span><span class="sxs-lookup"><span data-stu-id="b375c-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b375c-119">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="b375c-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b375c-120">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="b375c-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b375c-121">fixed, instruction</span><span class="sxs-lookup"><span data-stu-id="b375c-121">fixed Statement</span></span>](fixed-statement.md)
- [<span data-ttu-id="b375c-122">Pointeurs et code unsafe</span><span class="sxs-lookup"><span data-stu-id="b375c-122">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="b375c-123">Mémoires tampons de taille fixe</span><span class="sxs-lookup"><span data-stu-id="b375c-123">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
