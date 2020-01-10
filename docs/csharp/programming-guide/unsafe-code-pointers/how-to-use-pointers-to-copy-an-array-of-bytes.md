---
title: Guide pratique pour utiliser des pointeurs pour copier un tableau d' C# octets-Guide de programmation
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 4929699c2d1e07b16d4694cff79f9b1394b1de38
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75698454"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a><span data-ttu-id="97b93-102">Comment utiliser des pointeurs pour copier un tableau d’octets (C# Guide de programmation)</span><span class="sxs-lookup"><span data-stu-id="97b93-102">How to use pointers to copy an array of bytes (C# Programming Guide)</span></span>

<span data-ttu-id="97b93-103">L’exemple suivant utilise des pointeurs pour copier des octets d’un tableau à un autre.</span><span class="sxs-lookup"><span data-stu-id="97b93-103">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="97b93-104">Cet exemple utilise le mot clé [unsafe](../../language-reference/keywords/unsafe.md), qui vous permet d’utiliser des pointeurs dans la méthode `Copy`.</span><span class="sxs-lookup"><span data-stu-id="97b93-104">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="97b93-105">L’instruction [fixed](../../language-reference/keywords/fixed-statement.md) permet de déclarer des pointeurs vers les tableaux source et de destination.</span><span class="sxs-lookup"><span data-stu-id="97b93-105">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="97b93-106">L’instruction `fixed`*épingle* l’emplacement des tableaux source et de destination en mémoire pour que ceux-ci ne soient pas déplacés par l’opération de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="97b93-106">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="97b93-107">Les blocs de mémoire des tableaux sont libérés quand le bloc `fixed` est effectué.</span><span class="sxs-lookup"><span data-stu-id="97b93-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="97b93-108">Comme la méthode `Copy` dans cet exemple utilise le mot clé `unsafe`, elle doit être compilée avec l’option de compilateur [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="97b93-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="97b93-109">Cet exemple accède aux éléments des deux tableaux au moyen d’index et non au moyen d’un second pointeur non managé.</span><span class="sxs-lookup"><span data-stu-id="97b93-109">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="97b93-110">La déclaration des pointeurs `pSource` et `pTarget` épingle les tableaux.</span><span class="sxs-lookup"><span data-stu-id="97b93-110">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="97b93-111">Cette fonctionnalité est disponible à compter de C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="97b93-111">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="97b93-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="97b93-112">Example</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="97b93-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97b93-113">See also</span></span>

- [<span data-ttu-id="97b93-114">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="97b93-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="97b93-115">Pointeurs et code unsafe</span><span class="sxs-lookup"><span data-stu-id="97b93-115">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="97b93-116">-unsafe (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="97b93-116">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [<span data-ttu-id="97b93-117">Nettoyage de la mémoire</span><span class="sxs-lookup"><span data-stu-id="97b93-117">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
