---
title: Mémoire et étendues
ms.date: 10/03/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Memory<T>
- Span<T>
- buffers"
- pipeline processing
ms.openlocfilehash: c60c08d27c0e41228a15e8acdf01a9af28a23762
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201971"
---
# <a name="memory--and-span-related-types"></a><span data-ttu-id="737eb-102">Types liés à la mémoire et l’étendue</span><span class="sxs-lookup"><span data-stu-id="737eb-102">Memory- and span-related types</span></span>

<span data-ttu-id="737eb-103">À compter de .NET Core 2,1, .NET comprend un certain nombre de types interdépendants qui représentent une région contiguë fortement typée de mémoire arbitraire.</span><span class="sxs-lookup"><span data-stu-id="737eb-103">Starting with .NET Core 2.1, .NET includes a number of interrelated types that represent a contiguous, strongly typed region of arbitrary memory.</span></span> <span data-ttu-id="737eb-104">notamment :</span><span class="sxs-lookup"><span data-stu-id="737eb-104">These include:</span></span>

- <span data-ttu-id="737eb-105"><xref:System.Span%601?displayProperty=nameWithType>, un type utilisé pour accéder à une zone contiguë de mémoire.</span><span class="sxs-lookup"><span data-stu-id="737eb-105"><xref:System.Span%601?displayProperty=nameWithType>, a type that is used to access a contiguous region of memory.</span></span> <span data-ttu-id="737eb-106">Une instance <xref:System.Span%601> peut être sauvegardée par un tableau de type `T`, un objet <xref:System.String>, une mémoire tampon allouée avec [stackalloc](../../csharp/language-reference/operators/stackalloc.md), ou un pointeur vers une mémoire non managée.</span><span class="sxs-lookup"><span data-stu-id="737eb-106">A <xref:System.Span%601> instance can be backed by an array of type `T`, a <xref:System.String>, a buffer allocated with [stackalloc](../../csharp/language-reference/operators/stackalloc.md), or a pointer to unmanaged memory.</span></span> <span data-ttu-id="737eb-107">Comme elle doit être allouée sur la pile, elle comporte plusieurs restrictions.</span><span class="sxs-lookup"><span data-stu-id="737eb-107">Because it has to be allocated on the stack, it has a number of restrictions.</span></span> <span data-ttu-id="737eb-108">Par exemple, un champ dans une classe ne peut pas être de type <xref:System.Span%601>, et l’étendue ne peut pas être utilisée dans des opérations asynchrones.</span><span class="sxs-lookup"><span data-stu-id="737eb-108">For example, a field in a class cannot be of type <xref:System.Span%601>, nor can span be used in asynchronous operations.</span></span>

- <span data-ttu-id="737eb-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, une version immuable de la structure <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="737eb-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Span%601> structure.</span></span>

- <span data-ttu-id="737eb-110"><xref:System.Memory%601?displayProperty=nameWithType>, une zone contiguë de mémoire qui est allouée sur le segment managé plutôt que sur la pile.</span><span class="sxs-lookup"><span data-stu-id="737eb-110"><xref:System.Memory%601?displayProperty=nameWithType>, a contiguous region of memory that is allocated on the managed heap rather than the stack.</span></span> <span data-ttu-id="737eb-111">Une instance <xref:System.Memory%601> peut être sauvegardée par un tableau de type `T` ou un <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="737eb-111">A <xref:System.Memory%601> instance can be backed by an array of type `T` or a <xref:System.String>.</span></span> <span data-ttu-id="737eb-112">Comme elle peut être stockée sur le tas managé, <xref:System.Memory%601> ne présente aucune limite pour <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="737eb-112">Because it can be stored on the managed heap, <xref:System.Memory%601> has none of the limitations of <xref:System.Span%601>.</span></span>

- <span data-ttu-id="737eb-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, une version immuable de la structure <xref:System.Memory%601>.</span><span class="sxs-lookup"><span data-stu-id="737eb-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Memory%601> structure.</span></span>

- <span data-ttu-id="737eb-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, qui alloue des blocs de mémoire fortement typés d’un pool de mémoire à un propriétaire.</span><span class="sxs-lookup"><span data-stu-id="737eb-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, which allocates strongly typed blocks of memory from a memory pool to an owner.</span></span> <span data-ttu-id="737eb-115">Les instances <xref:System.Buffers.IMemoryOwner%601> peuvent être louées à partir du pool en appelant <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> puis replacées dans le pool en appelant <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="737eb-115"><xref:System.Buffers.IMemoryOwner%601> instances can be rented from the pool by calling <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> and released back to the pool by calling <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="737eb-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, qui représente le propriétaire d’un bloc de mémoire et gère la durée de vie.</span><span class="sxs-lookup"><span data-stu-id="737eb-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, which represents the owner of a block of memory and controls its lifetime management.</span></span>

- <span data-ttu-id="737eb-117"><xref:System.Buffers.MemoryManager%601>, une classe de base abstraite qui peut être utilisée pour remplacer l’implémentation de <xref:System.Memory%601> afin de sauvegarder <xref:System.Memory%601> par des types supplémentaires, par exemple des descripteurs sécurisés.</span><span class="sxs-lookup"><span data-stu-id="737eb-117"><xref:System.Buffers.MemoryManager%601>, an abstract base class that can be used to replace the implementation of <xref:System.Memory%601> so that <xref:System.Memory%601> can be backed by additional types, such as safe handles.</span></span> <span data-ttu-id="737eb-118"><xref:System.Buffers.MemoryManager%601> s’applique à des scénarios avancés.</span><span class="sxs-lookup"><span data-stu-id="737eb-118"><xref:System.Buffers.MemoryManager%601> is intended for advanced scenarios.</span></span>

- <span data-ttu-id="737eb-119"><xref:System.ArraySegment%601>, un wrapper pour un certain nombre d’éléments de tableau commençant à un index particulier.</span><span class="sxs-lookup"><span data-stu-id="737eb-119"><xref:System.ArraySegment%601>, a wrapper for a particular number of array elements starting at a particular index.</span></span>

- <span data-ttu-id="737eb-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>, une collection de méthodes d’extension pour la conversion de chaînes, de tableaux et de segments de tableau en blocs <xref:System.Memory%601>.</span><span class="sxs-lookup"><span data-stu-id="737eb-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>, a collection of extension methods for converting strings, arrays, and array segments to <xref:System.Memory%601> blocks.</span></span>

> [!NOTE]
> <span data-ttu-id="737eb-121">Pour les frameworks antérieurs, <xref:System.Span%601> et <xref:System.Memory%601> sont disponibles dans le [package System.Memory NuGet](https://www.nuget.org/packages/System.Memory/).</span><span class="sxs-lookup"><span data-stu-id="737eb-121">For earlier frameworks, <xref:System.Span%601> and <xref:System.Memory%601> are available in the [System.Memory NuGet package](https://www.nuget.org/packages/System.Memory/).</span></span>

<span data-ttu-id="737eb-122">Pour plus d'informations, consultez l'espace de noms <xref:System.Buffers?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="737eb-122">For more information, see the <xref:System.Buffers?displayProperty=nameWithType> namespace.</span></span>

## <a name="working-with-memory-and-span"></a><span data-ttu-id="737eb-123">Utilisation de la mémoire et de l’étendue</span><span class="sxs-lookup"><span data-stu-id="737eb-123">Working with memory and span</span></span>

<span data-ttu-id="737eb-124">Étant donné que les types liés à la mémoire et à l’étendue servent généralement à stocker les données dans un pipeline de traitement, il est important que les développeurs suivent un ensemble de meilleures pratiques lorsqu’ils utilisent <xref:System.Span%601>, <xref:System.Memory%601> et des types connexes.</span><span class="sxs-lookup"><span data-stu-id="737eb-124">Because the memory- and span-related types are typically used to store data in a processing pipeline, it is important that developers follow a set of best practices when using <xref:System.Span%601>, <xref:System.Memory%601>, and related types.</span></span> <span data-ttu-id="737eb-125">Ces meilleures pratiques sont documentées [dans \<T> \<T> les instructions relatives à l’utilisation de la mémoire et de l’étendue](memory-t-usage-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="737eb-125">These best practices are documented in [Memory\<T> and Span\<T> usage guidelines](memory-t-usage-guidelines.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="737eb-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="737eb-126">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>
