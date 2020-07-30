---
title: Guide pratique pour utiliser des pointeurs pour copier un tableau d’octets-Guide de programmation C#
description: Découvrez comment utiliser des pointeurs pour copier un tableau d’octets. Consultez un exemple de code et les ressources supplémentaires disponibles.
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 70ab1441d25ea69afb2244bd94bd404a3e32838d
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381786"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a><span data-ttu-id="ea99d-104">Comment utiliser des pointeurs pour copier un tableau d’octets (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="ea99d-104">How to use pointers to copy an array of bytes (C# Programming Guide)</span></span>

<span data-ttu-id="ea99d-105">L’exemple suivant utilise des pointeurs pour copier des octets d’un tableau à un autre.</span><span class="sxs-lookup"><span data-stu-id="ea99d-105">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="ea99d-106">Cet exemple utilise le mot clé [unsafe](../../language-reference/keywords/unsafe.md), qui vous permet d’utiliser des pointeurs dans la méthode `Copy`.</span><span class="sxs-lookup"><span data-stu-id="ea99d-106">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="ea99d-107">L’instruction [fixed](../../language-reference/keywords/fixed-statement.md) permet de déclarer des pointeurs vers les tableaux source et de destination.</span><span class="sxs-lookup"><span data-stu-id="ea99d-107">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="ea99d-108">L’instruction `fixed`*épingle* l’emplacement des tableaux source et de destination en mémoire pour que ceux-ci ne soient pas déplacés par l’opération de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="ea99d-108">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="ea99d-109">Les blocs de mémoire des tableaux sont libérés quand le bloc `fixed` est effectué.</span><span class="sxs-lookup"><span data-stu-id="ea99d-109">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="ea99d-110">Comme la méthode `Copy` dans cet exemple utilise le mot clé `unsafe`, elle doit être compilée avec l’option de compilateur [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="ea99d-110">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="ea99d-111">Cet exemple accède aux éléments des deux tableaux au moyen d’index et non au moyen d’un second pointeur non managé.</span><span class="sxs-lookup"><span data-stu-id="ea99d-111">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="ea99d-112">La déclaration des pointeurs `pSource` et `pTarget` épingle les tableaux.</span><span class="sxs-lookup"><span data-stu-id="ea99d-112">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="ea99d-113">Cette fonctionnalité est disponible à compter de C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="ea99d-113">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="ea99d-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="ea99d-114">Example</span></span>

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="ea99d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea99d-115">See also</span></span>

- [<span data-ttu-id="ea99d-116">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="ea99d-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ea99d-117">Pointeurs et code unsafe</span><span class="sxs-lookup"><span data-stu-id="ea99d-117">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="ea99d-118">-unsafe (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="ea99d-118">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [<span data-ttu-id="ea99d-119">Garbage collection</span><span class="sxs-lookup"><span data-stu-id="ea99d-119">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
