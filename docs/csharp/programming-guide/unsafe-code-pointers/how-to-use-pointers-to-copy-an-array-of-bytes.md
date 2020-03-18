---
title: Comment utiliser des pointeurs pour copier un tableau d’octets - Guide de programmation C
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 4929699c2d1e07b16d4694cff79f9b1394b1de38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75698454"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a><span data-ttu-id="c0d5c-102">Comment utiliser des pointeurs pour copier un tableau d’octets (Guide de programmation C)</span><span class="sxs-lookup"><span data-stu-id="c0d5c-102">How to use pointers to copy an array of bytes (C# Programming Guide)</span></span>

<span data-ttu-id="c0d5c-103">L’exemple suivant utilise des pointeurs pour copier des octets d’un tableau à un autre.</span><span class="sxs-lookup"><span data-stu-id="c0d5c-103">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="c0d5c-104">Cet exemple utilise le mot clé [unsafe](../../language-reference/keywords/unsafe.md), qui vous permet d’utiliser des pointeurs dans la méthode `Copy`.</span><span class="sxs-lookup"><span data-stu-id="c0d5c-104">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="c0d5c-105">L’instruction [fixed](../../language-reference/keywords/fixed-statement.md) permet de déclarer des pointeurs vers les tableaux source et de destination.</span><span class="sxs-lookup"><span data-stu-id="c0d5c-105">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="c0d5c-106">L’instruction `fixed`*épingle* l’emplacement des tableaux source et de destination en mémoire pour que ceux-ci ne soient pas déplacés par l’opération de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="c0d5c-106">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="c0d5c-107">Les blocs de mémoire des tableaux sont libérés quand le bloc `fixed` est effectué.</span><span class="sxs-lookup"><span data-stu-id="c0d5c-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="c0d5c-108">Comme la méthode `Copy` dans cet exemple utilise le mot clé `unsafe`, elle doit être compilée avec l’option de compilateur [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="c0d5c-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="c0d5c-109">Cet exemple accède aux éléments des deux tableaux au moyen d’index et non au moyen d’un second pointeur non managé.</span><span class="sxs-lookup"><span data-stu-id="c0d5c-109">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="c0d5c-110">La déclaration des pointeurs `pSource` et `pTarget` épingle les tableaux.</span><span class="sxs-lookup"><span data-stu-id="c0d5c-110">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="c0d5c-111">Cette fonctionnalité est disponible à compter de C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="c0d5c-111">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="c0d5c-112"> Exemple</span><span class="sxs-lookup"><span data-stu-id="c0d5c-112">Example</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="c0d5c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0d5c-113">See also</span></span>

- [<span data-ttu-id="c0d5c-114">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="c0d5c-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c0d5c-115">Pointeurs et code unsafe</span><span class="sxs-lookup"><span data-stu-id="c0d5c-115">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="c0d5c-116">-unsafe (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="c0d5c-116">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [<span data-ttu-id="c0d5c-117">Garbage collection</span><span class="sxs-lookup"><span data-stu-id="c0d5c-117">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
