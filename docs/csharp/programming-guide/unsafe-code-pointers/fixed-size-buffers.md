---
title: Mémoires tampons de taille fixe - Guide de programmation C#
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 6770497b23212f1786b4f4a620ed2b650079c44b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157024"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="b0449-102">Mémoires tampons de taille fixe (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="b0449-102">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="b0449-103">En C#, vous pouvez utiliser l’instruction [fixed](../../language-reference/keywords/fixed-statement.md) pour créer une mémoire tampon avec un tableau de taille fixe dans une structure de données.</span><span class="sxs-lookup"><span data-stu-id="b0449-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="b0449-104">Les mémoires tampons de taille fixe sont utiles quand vous écrivez des méthodes qui sont interopérables avec les sources de données d’autres langages ou plateformes.</span><span class="sxs-lookup"><span data-stu-id="b0449-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="b0449-105">Le tableau fixe peut accepter tous les attributs ou modificateurs qui sont autorisés pour les membres de structures régulières.</span><span class="sxs-lookup"><span data-stu-id="b0449-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="b0449-106">La seule restriction est que le tableau doit être de type `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float` ou `double`.</span><span class="sxs-lookup"><span data-stu-id="b0449-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="b0449-107">Notes </span><span class="sxs-lookup"><span data-stu-id="b0449-107">Remarks</span></span>

<span data-ttu-id="b0449-108">Dans du code safe, un struct C# qui contient un tableau ne contient pas les éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="b0449-108">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="b0449-109">Le struct contient une référence aux éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="b0449-109">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="b0449-110">Vous pouvez incorporer un tableau de taille fixe dans un [struct](../../language-reference/builtin-types/struct.md) quand il est utilisé dans un bloc de code [unsafe](../../language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="b0449-110">You can embed an array of fixed size in a [struct](../../language-reference/builtin-types/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="b0449-111">La taille `struct` de ce qui suit ne dépend pas `pathName` du nombre d’éléments dans le tableau, puisqu’il s’agit d’une référence :</span><span class="sxs-lookup"><span data-stu-id="b0449-111">Size of the following `struct` doesn't depend on the number of elements in the array, since `pathName` is a reference:</span></span>

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

<span data-ttu-id="b0449-112">Un `struct` peut contenir un tableau incorporé dans du code unsafe.</span><span class="sxs-lookup"><span data-stu-id="b0449-112">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="b0449-113">Dans l’exemple suivant, le tableau `fixedBuffer` a une taille fixe.</span><span class="sxs-lookup"><span data-stu-id="b0449-113">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="b0449-114">Utilisez une instruction `fixed` pour établir un pointeur vers le premier élément.</span><span class="sxs-lookup"><span data-stu-id="b0449-114">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="b0449-115">Accédez aux éléments du tableau par le biais de ce pointeur.</span><span class="sxs-lookup"><span data-stu-id="b0449-115">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="b0449-116">L’instruction `fixed` épingle le champ de l’instance `fixedBuffer` à un emplacement spécifique de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="b0449-116">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

<span data-ttu-id="b0449-117">La taille du tableau `char` de 128 éléments est de 256 octets.</span><span class="sxs-lookup"><span data-stu-id="b0449-117">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="b0449-118">Les mémoires tampons [char](../../language-reference/builtin-types/char.md) de taille fixe acceptent toujours deux octets par caractère, quel que soit l’encodage.</span><span class="sxs-lookup"><span data-stu-id="b0449-118">Fixed size [char](../../language-reference/builtin-types/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="b0449-119">Ceci est vrai même lorsque les mémoires tampons char sont marshalées vers des méthodes ou des structs d’API avec `CharSet = CharSet.Auto` ou `CharSet = CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="b0449-119">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="b0449-120">Pour plus d’informations, consultez <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="b0449-120">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="b0449-121">L’exemple précédent montre comment accéder aux champs `fixed` sans épinglage, ce qui est possible à compter de C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="b0449-121">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span></span>

<span data-ttu-id="b0449-122">Un autre tableau courant de taille fixe est le tableau [bool](../../language-reference/builtin-types/bool.md).</span><span class="sxs-lookup"><span data-stu-id="b0449-122">Another common fixed-size array is the [bool](../../language-reference/builtin-types/bool.md) array.</span></span> <span data-ttu-id="b0449-123">La taille des éléments d’un tableau `bool` est toujours d’un octet.</span><span class="sxs-lookup"><span data-stu-id="b0449-123">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="b0449-124">Les tableaux `bool` ne conviennent pas à la création de tableaux d’octets ou de mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="b0449-124">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

> [!NOTE]
> <span data-ttu-id="b0449-125">Le compilateur C# et le common language runtime (CLR) ne contrôlent pas le dépassement de la mémoire tampon de sécurité, sauf pour la mémoire créée à l’aide de [stackalloc](../../language-reference/operators/stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="b0449-125">Except for memory created by using [stackalloc](../../language-reference/operators/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="b0449-126">Comme toujours pour le code unsafe, la prudence est recommandée.</span><span class="sxs-lookup"><span data-stu-id="b0449-126">As with all unsafe code, use caution.</span></span>

<span data-ttu-id="b0449-127">Les mémoires tampons unsafe diffèrent des tableaux normaux à différents niveaux :</span><span class="sxs-lookup"><span data-stu-id="b0449-127">Unsafe buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="b0449-128">Les mémoires tampons unsafe peuvent uniquement être utilisées dans un contexte unsafe.</span><span class="sxs-lookup"><span data-stu-id="b0449-128">You can only use unsafe buffers in an unsafe context.</span></span>
- <span data-ttu-id="b0449-129">Les mémoires tampons unsafe sont toujours des vecteurs ou des tableaux unidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="b0449-129">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="b0449-130">La déclaration du tableau doit inclure un nombre, tel que `char id[8]`.</span><span class="sxs-lookup"><span data-stu-id="b0449-130">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="b0449-131">Vous ne pouvez pas utiliser `char id[]`.</span><span class="sxs-lookup"><span data-stu-id="b0449-131">You cannot use `char id[]`.</span></span>
- <span data-ttu-id="b0449-132">Les mémoires tampons unsafe peuvent uniquement être des champs d’instance de structs dans un contexte unsafe.</span><span class="sxs-lookup"><span data-stu-id="b0449-132">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0449-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0449-133">See also</span></span>

- [<span data-ttu-id="b0449-134">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="b0449-134">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b0449-135">Pointeurs et code unsafe</span><span class="sxs-lookup"><span data-stu-id="b0449-135">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="b0449-136">fixed, instruction</span><span class="sxs-lookup"><span data-stu-id="b0449-136">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="b0449-137">Interopérabilité</span><span class="sxs-lookup"><span data-stu-id="b0449-137">Interoperability</span></span>](../interop/index.md)
