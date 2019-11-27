---
title: Mémoires tampons de taille fixe - Guide de programmation C#
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 33af43a69587ffaadd7fcb42fa1d30ee9fc41989
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429403"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="894e9-102">Mémoires tampons de taille fixe (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="894e9-102">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="894e9-103">En C#, vous pouvez utiliser l’instruction [fixed](../../language-reference/keywords/fixed-statement.md) pour créer une mémoire tampon avec un tableau de taille fixe dans une structure de données.</span><span class="sxs-lookup"><span data-stu-id="894e9-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="894e9-104">Les mémoires tampons de taille fixe sont utiles quand vous écrivez des méthodes qui sont interopérables avec les sources de données d’autres langages ou plateformes.</span><span class="sxs-lookup"><span data-stu-id="894e9-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="894e9-105">Le tableau fixe peut accepter tous les attributs ou modificateurs qui sont autorisés pour les membres de structures régulières.</span><span class="sxs-lookup"><span data-stu-id="894e9-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="894e9-106">La seule restriction est que le tableau doit être de type `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float` ou `double`.</span><span class="sxs-lookup"><span data-stu-id="894e9-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="894e9-107">Notes</span><span class="sxs-lookup"><span data-stu-id="894e9-107">Remarks</span></span>

<span data-ttu-id="894e9-108">Dans du code safe, un struct C# qui contient un tableau ne contient pas les éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="894e9-108">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="894e9-109">Le struct contient une référence aux éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="894e9-109">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="894e9-110">Vous pouvez incorporer un tableau de taille fixe dans un [struct](../../language-reference/keywords/struct.md) quand il est utilisé dans un bloc de code [unsafe](../../language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="894e9-110">You can embed an array of fixed size in a [struct](../../language-reference/keywords/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="894e9-111">Le `struct` suivant a une taille de 8 octets.</span><span class="sxs-lookup"><span data-stu-id="894e9-111">The following `struct` is 8 bytes in size.</span></span> <span data-ttu-id="894e9-112">Le tableau `pathName` est une référence :</span><span class="sxs-lookup"><span data-stu-id="894e9-112">The `pathName` array is a reference:</span></span>

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

<span data-ttu-id="894e9-113">Un `struct` peut contenir un tableau incorporé dans du code unsafe.</span><span class="sxs-lookup"><span data-stu-id="894e9-113">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="894e9-114">Dans l’exemple suivant, le tableau `fixedBuffer` a une taille fixe.</span><span class="sxs-lookup"><span data-stu-id="894e9-114">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="894e9-115">Utilisez une instruction `fixed` pour établir un pointeur vers le premier élément.</span><span class="sxs-lookup"><span data-stu-id="894e9-115">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="894e9-116">Accédez aux éléments du tableau par le biais de ce pointeur.</span><span class="sxs-lookup"><span data-stu-id="894e9-116">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="894e9-117">L’instruction `fixed` épingle le champ de l’instance `fixedBuffer` à un emplacement spécifique de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="894e9-117">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

<span data-ttu-id="894e9-118">La taille du tableau `char` de 128 éléments est de 256 octets.</span><span class="sxs-lookup"><span data-stu-id="894e9-118">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="894e9-119">Les mémoires tampons [char](../../language-reference/builtin-types/char.md) de taille fixe acceptent toujours deux octets par caractère, quel que soit l’encodage.</span><span class="sxs-lookup"><span data-stu-id="894e9-119">Fixed size [char](../../language-reference/builtin-types/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="894e9-120">Ceci est vrai même lorsque les mémoires tampons char sont marshalées vers des méthodes ou des structs d’API avec `CharSet = CharSet.Auto` ou `CharSet = CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="894e9-120">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="894e9-121">Pour plus d'informations, consultez <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="894e9-121">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="894e9-122">L’exemple précédent montre comment accéder aux champs `fixed` sans épinglage, ce qui est possible à compter de C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="894e9-122">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span></span>

<span data-ttu-id="894e9-123">Un autre tableau courant de taille fixe est le tableau [bool](../../language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="894e9-123">Another common fixed-size array is the [bool](../../language-reference/keywords/bool.md) array.</span></span> <span data-ttu-id="894e9-124">La taille des éléments d’un tableau `bool` est toujours d’un octet.</span><span class="sxs-lookup"><span data-stu-id="894e9-124">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="894e9-125">Les tableaux `bool` ne conviennent pas à la création de tableaux d’octets ou de mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="894e9-125">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

> [!NOTE]
> <span data-ttu-id="894e9-126">Le compilateur C# et le common language runtime (CLR) ne contrôlent pas le dépassement de la mémoire tampon de sécurité, sauf pour la mémoire créée à l’aide de [stackalloc](../../language-reference/operators/stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="894e9-126">Except for memory created by using [stackalloc](../../language-reference/operators/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="894e9-127">Comme toujours pour le code unsafe, la prudence est recommandée.</span><span class="sxs-lookup"><span data-stu-id="894e9-127">As with all unsafe code, use caution.</span></span>

<span data-ttu-id="894e9-128">Les mémoires tampons unsafe diffèrent des tableaux normaux à différents niveaux :</span><span class="sxs-lookup"><span data-stu-id="894e9-128">Unsafe buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="894e9-129">Les mémoires tampons unsafe peuvent uniquement être utilisées dans un contexte unsafe.</span><span class="sxs-lookup"><span data-stu-id="894e9-129">You can only use unsafe buffers in an unsafe context.</span></span>
- <span data-ttu-id="894e9-130">Les mémoires tampons unsafe sont toujours des vecteurs ou des tableaux unidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="894e9-130">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="894e9-131">La déclaration du tableau doit inclure un nombre, tel que `char id[8]`.</span><span class="sxs-lookup"><span data-stu-id="894e9-131">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="894e9-132">Vous ne pouvez pas utiliser `char id[]`.</span><span class="sxs-lookup"><span data-stu-id="894e9-132">You cannot use `char id[]`.</span></span>
- <span data-ttu-id="894e9-133">Les mémoires tampons unsafe peuvent uniquement être des champs d’instance de structs dans un contexte unsafe.</span><span class="sxs-lookup"><span data-stu-id="894e9-133">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>

## <a name="see-also"></a><span data-ttu-id="894e9-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="894e9-134">See also</span></span>

- [<span data-ttu-id="894e9-135">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="894e9-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="894e9-136">Pointeurs et code unsafe</span><span class="sxs-lookup"><span data-stu-id="894e9-136">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="894e9-137">fixed, instruction</span><span class="sxs-lookup"><span data-stu-id="894e9-137">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="894e9-138">Interopérabilité</span><span class="sxs-lookup"><span data-stu-id="894e9-138">Interoperability</span></span>](../interop/index.md)
