---
title: unsafe, mot clé -Référence C#
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: ef98809eae0329c028dfb318c4a437aae4736db1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712986"
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="a5501-102">unsafe (référence C#)</span><span class="sxs-lookup"><span data-stu-id="a5501-102">unsafe (C# Reference)</span></span>

<span data-ttu-id="a5501-103">Le mot clé `unsafe` désigne un contexte non sécurisé, qui est requis pour toute opération impliquant des pointeurs.</span><span class="sxs-lookup"><span data-stu-id="a5501-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="a5501-104">Pour plus d’informations, consultez [Pointeurs et code unsafe](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="a5501-104">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="a5501-105">Vous pouvez utiliser le modificateur `unsafe` dans la déclaration d’un type ou d’un membre.</span><span class="sxs-lookup"><span data-stu-id="a5501-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="a5501-106">Toute l’étendue de texte du type ou du membre est ainsi considérée comme un contexte unsafe.</span><span class="sxs-lookup"><span data-stu-id="a5501-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="a5501-107">Par exemple, ce qui suit est une méthode déclarée avec le modificateur `unsafe` :</span><span class="sxs-lookup"><span data-stu-id="a5501-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="a5501-108">La portée du contexte unsafe s’étend de la liste de paramètres à la fin de la méthode, de sorte que les pointeurs peuvent également être utilisés dans la liste de paramètres :</span><span class="sxs-lookup"><span data-stu-id="a5501-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

<span data-ttu-id="a5501-109">Vous pouvez également avoir recours à un bloc unsafe pour utiliser un code unsafe dans ce bloc.</span><span class="sxs-lookup"><span data-stu-id="a5501-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="a5501-110">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="a5501-110">For example:</span></span>

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="a5501-111">Pour compiler le code dangereux, vous devez spécifier l’option [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compilateur.</span><span class="sxs-lookup"><span data-stu-id="a5501-111">To compile unsafe code, you must specify the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="a5501-112">Le code unsafe n’est pas vérifiable par le service CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="a5501-112">Unsafe code is not verifiable by the common language runtime.</span></span>

## <a name="example"></a><span data-ttu-id="a5501-113"> Exemple</span><span class="sxs-lookup"><span data-stu-id="a5501-113">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a><span data-ttu-id="a5501-114">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="a5501-114">C# language specification</span></span>

<span data-ttu-id="a5501-115">Pour plus d’informations, voir [Code unsafe](~/_csharplang/spec/unsafe-code.md) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="a5501-115">For more information, see [Unsafe code](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="a5501-116">La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="a5501-116">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5501-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5501-117">See also</span></span>

- [<span data-ttu-id="a5501-118">Référence C</span><span class="sxs-lookup"><span data-stu-id="a5501-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a5501-119">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="a5501-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a5501-120">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="a5501-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a5501-121">fixed, instruction</span><span class="sxs-lookup"><span data-stu-id="a5501-121">fixed Statement</span></span>](fixed-statement.md)
- [<span data-ttu-id="a5501-122">Pointeurs et code unsafe</span><span class="sxs-lookup"><span data-stu-id="a5501-122">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="a5501-123">Tampons de taille fixe</span><span class="sxs-lookup"><span data-stu-id="a5501-123">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
