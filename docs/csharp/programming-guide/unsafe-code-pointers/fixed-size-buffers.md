---
title: Mémoires tampons de taille fixe - Guide de programmation C#
ms.date: 04/23/2020
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 5920dd125ded34969d60feb299568b56402056ab
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140552"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="536c8-102">Mémoires tampons de taille fixe (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="536c8-102">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="536c8-103">En C#, vous pouvez utiliser l’instruction [fixed](../../language-reference/keywords/fixed-statement.md) pour créer une mémoire tampon avec un tableau de taille fixe dans une structure de données.</span><span class="sxs-lookup"><span data-stu-id="536c8-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="536c8-104">Les mémoires tampons de taille fixe sont utiles quand vous écrivez des méthodes qui sont interopérables avec les sources de données d’autres langages ou plateformes.</span><span class="sxs-lookup"><span data-stu-id="536c8-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="536c8-105">Le tableau fixe peut accepter tous les attributs ou modificateurs qui sont autorisés pour les membres de structures régulières.</span><span class="sxs-lookup"><span data-stu-id="536c8-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="536c8-106">La seule restriction est que le tableau doit être de type `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float` ou `double`.</span><span class="sxs-lookup"><span data-stu-id="536c8-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="536c8-107">Notes </span><span class="sxs-lookup"><span data-stu-id="536c8-107">Remarks</span></span>

<span data-ttu-id="536c8-108">Dans du code safe, un struct C# qui contient un tableau ne contient pas les éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="536c8-108">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="536c8-109">Le struct contient une référence aux éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="536c8-109">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="536c8-110">Vous pouvez incorporer un tableau de taille fixe dans un [struct](../../language-reference/builtin-types/struct.md) quand il est utilisé dans un bloc de code [unsafe](../../language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="536c8-110">You can embed an array of fixed size in a [struct](../../language-reference/builtin-types/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="536c8-111">La taille de l' `struct` élément suivant ne dépend pas du nombre d’éléments du tableau, `pathName` car est une référence :</span><span class="sxs-lookup"><span data-stu-id="536c8-111">Size of the following `struct` doesn't depend on the number of elements in the array, since `pathName` is a reference:</span></span>

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

<span data-ttu-id="536c8-112">Un `struct` peut contenir un tableau incorporé dans du code unsafe.</span><span class="sxs-lookup"><span data-stu-id="536c8-112">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="536c8-113">Dans l’exemple suivant, le tableau `fixedBuffer` a une taille fixe.</span><span class="sxs-lookup"><span data-stu-id="536c8-113">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="536c8-114">Utilisez une instruction `fixed` pour établir un pointeur vers le premier élément.</span><span class="sxs-lookup"><span data-stu-id="536c8-114">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="536c8-115">Accédez aux éléments du tableau par le biais de ce pointeur.</span><span class="sxs-lookup"><span data-stu-id="536c8-115">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="536c8-116">L’instruction `fixed` épingle le champ de l’instance `fixedBuffer` à un emplacement spécifique de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="536c8-116">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

<span data-ttu-id="536c8-117">La taille du tableau `char` de 128 éléments est de 256 octets.</span><span class="sxs-lookup"><span data-stu-id="536c8-117">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="536c8-118">Les mémoires tampons [char](../../language-reference/builtin-types/char.md) de taille fixe acceptent toujours deux octets par caractère, quel que soit l’encodage.</span><span class="sxs-lookup"><span data-stu-id="536c8-118">Fixed size [char](../../language-reference/builtin-types/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="536c8-119">Ceci est vrai même lorsque les mémoires tampons char sont marshalées vers des méthodes ou des structs d’API avec `CharSet = CharSet.Auto` ou `CharSet = CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="536c8-119">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="536c8-120">Pour plus d’informations, consultez <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="536c8-120">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="536c8-121">L’exemple précédent montre comment accéder aux champs `fixed` sans épinglage, ce qui est possible à compter de C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="536c8-121">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span></span>

<span data-ttu-id="536c8-122">Un autre tableau courant de taille fixe est le tableau [bool](../../language-reference/builtin-types/bool.md).</span><span class="sxs-lookup"><span data-stu-id="536c8-122">Another common fixed-size array is the [bool](../../language-reference/builtin-types/bool.md) array.</span></span> <span data-ttu-id="536c8-123">La taille des éléments d’un tableau `bool` est toujours d’un octet.</span><span class="sxs-lookup"><span data-stu-id="536c8-123">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="536c8-124">Les tableaux `bool` ne conviennent pas à la création de tableaux d’octets ou de mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="536c8-124">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

<span data-ttu-id="536c8-125">Les mémoires tampons de taille fixe sont <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType>compilées avec le, qui indique au Common Language Runtime (CLR) qu’un type contient un tableau non managé susceptible de provoquer un dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="536c8-125">Fixed size buffers are compiled with the <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType>, which instructs the common language runtime (CLR) that a type contains an unmanaged array that can potentially overflow.</span></span> <span data-ttu-id="536c8-126">Cela est similaire à la mémoire créée à l’aide de [stackalloc](../../language-reference/operators/stackalloc.md), qui active automatiquement les fonctionnalités de détection de dépassement de mémoire tampon dans le CLR.</span><span class="sxs-lookup"><span data-stu-id="536c8-126">This is similar to memory created using [stackalloc](../../language-reference/operators/stackalloc.md), which automatically enables buffer overrun detection features in the CLR.</span></span> <span data-ttu-id="536c8-127">L’exemple précédent montre comment une mémoire tampon de taille fixe peut exister `unsafe struct`dans un.</span><span class="sxs-lookup"><span data-stu-id="536c8-127">The previous example shows how a fixed size buffer could exist in an `unsafe struct`.</span></span>

```csharp
internal unsafe struct Buffer
{
    public fixed char fixedBuffer[128];
}
```

<span data-ttu-id="536c8-128">Le compilateur qui a généré `Buffer`C# pour, est attribué comme suit :</span><span class="sxs-lookup"><span data-stu-id="536c8-128">The compiler generated C# for `Buffer`, is attributed as follows:</span></span>

```csharp
internal struct Buffer
{
    [StructLayout(LayoutKind.Sequential, Size = 256)]
    [CompilerGenerated]
    [UnsafeValueType]
    public struct <fixedBuffer>e__FixedBuffer
    {
        public char FixedElementField;
    }

    [FixedBuffer(typeof(char), 128)]
    public <fixedBuffer>e__FixedBuffer fixedBuffer;
}
```

<span data-ttu-id="536c8-129">Les mémoires tampons de taille fixe diffèrent des tableaux normaux des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="536c8-129">Fixed size buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="536c8-130">Peut uniquement être utilisé dans un contexte non [sécurisé](../../language-reference/keywords/unsafe.md) .</span><span class="sxs-lookup"><span data-stu-id="536c8-130">May only be used in an [unsafe](../../language-reference/keywords/unsafe.md) context.</span></span>
- <span data-ttu-id="536c8-131">Peut uniquement être des champs d’instance de structs.</span><span class="sxs-lookup"><span data-stu-id="536c8-131">May only be instance fields of structs.</span></span>
- <span data-ttu-id="536c8-132">Il s’agit toujours de vecteurs, ou de tableaux unidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="536c8-132">They're always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="536c8-133">La déclaration doit inclure la longueur, telle que `fixed char id[8]`.</span><span class="sxs-lookup"><span data-stu-id="536c8-133">The declaration should include the length, such as `fixed char id[8]`.</span></span> <span data-ttu-id="536c8-134">Vous ne pouvez pas utiliser `fixed char id[]`.</span><span class="sxs-lookup"><span data-stu-id="536c8-134">You cannot use `fixed char id[]`.</span></span>

## <a name="see-also"></a><span data-ttu-id="536c8-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="536c8-135">See also</span></span>

- [<span data-ttu-id="536c8-136">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="536c8-136">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="536c8-137">Pointeurs et code unsafe</span><span class="sxs-lookup"><span data-stu-id="536c8-137">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="536c8-138">fixed, instruction</span><span class="sxs-lookup"><span data-stu-id="536c8-138">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="536c8-139">Interopérabilité</span><span class="sxs-lookup"><span data-stu-id="536c8-139">Interoperability</span></span>](../interop/index.md)
