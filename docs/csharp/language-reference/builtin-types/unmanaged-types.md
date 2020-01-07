---
title: Types non managés - Référence C#
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 97aa4dd629e385dbe9641d82a7da21a0aaa63e92
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75342580"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="2e3b4-102">Types non managés (référence C#)</span><span class="sxs-lookup"><span data-stu-id="2e3b4-102">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="2e3b4-103">Un type est un **type non managé** s’il s’agit de l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="2e3b4-103">A type is an **unmanaged type** if it's any of the following types:</span></span>

- <span data-ttu-id="2e3b4-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` ou `bool`</span><span class="sxs-lookup"><span data-stu-id="2e3b4-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="2e3b4-105">Tout type [enum](enum.md)</span><span class="sxs-lookup"><span data-stu-id="2e3b4-105">Any [enum](enum.md) type</span></span>
- <span data-ttu-id="2e3b4-106">Tout type [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md)</span><span class="sxs-lookup"><span data-stu-id="2e3b4-106">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="2e3b4-107">Tout type [struct](../keywords/struct.md) défini par l’utilisateur qui contient des champs de types non managés uniquement et C# , dans 7,3 et les versions antérieures, n’est pas un type construit (un type qui inclut au moins un argument de type)</span><span class="sxs-lookup"><span data-stu-id="2e3b4-107">Any user-defined [struct](../keywords/struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span></span>

<span data-ttu-id="2e3b4-108">À partir C# de 7,3, vous pouvez utiliser la [contrainte`unmanaged`](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) pour spécifier qu’un paramètre de type est un type non managé non-pointeur, non Nullable.</span><span class="sxs-lookup"><span data-stu-id="2e3b4-108">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer, non-nullable unmanaged type.</span></span>

<span data-ttu-id="2e3b4-109">À C# partir de 8,0, un type struct *construit* qui contient des champs de types non managés uniquement est également non managé, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="2e3b4-109">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span></span>

[!code-csharp[unmanaged constructed types](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#ProgramExample)]

<span data-ttu-id="2e3b4-110">Un struct générique peut être la source des types construits non managés et non managés.</span><span class="sxs-lookup"><span data-stu-id="2e3b4-110">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span></span> <span data-ttu-id="2e3b4-111">L’exemple précédent définit une structure générique `Coords<T>` et présente les exemples de types construits non managés.</span><span class="sxs-lookup"><span data-stu-id="2e3b4-111">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span></span> <span data-ttu-id="2e3b4-112">L’exemple de type non managé est `Coords<object>`.</span><span class="sxs-lookup"><span data-stu-id="2e3b4-112">The example of not an unmanaged type is `Coords<object>`.</span></span> <span data-ttu-id="2e3b4-113">Elle n’est pas non plus gérée, car elle contient les champs du type de `object`, qui n’est pas non géré.</span><span class="sxs-lookup"><span data-stu-id="2e3b4-113">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span></span> <span data-ttu-id="2e3b4-114">Si vous souhaitez que *tous les* types construits soient des types non managés, utilisez la contrainte `unmanaged` dans la définition d’un struct générique :</span><span class="sxs-lookup"><span data-stu-id="2e3b4-114">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span></span>

[!code-csharp[unmanaged constraint in type definition](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a><span data-ttu-id="2e3b4-115">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="2e3b4-115">C# language specification</span></span>

<span data-ttu-id="2e3b4-116">Pour plus d’informations, consultez la section [Types de pointeur](~/_csharplang/spec/unsafe-code.md#pointer-types) de la [Spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="2e3b4-116">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2e3b4-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e3b4-117">See also</span></span>

- [<span data-ttu-id="2e3b4-118">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="2e3b4-118">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2e3b4-119">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="2e3b4-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="2e3b4-120">Types liés à la mémoire et à l’étendue</span><span class="sxs-lookup"><span data-stu-id="2e3b4-120">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="2e3b4-121">Opérateur sizeof</span><span class="sxs-lookup"><span data-stu-id="2e3b4-121">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="2e3b4-122">Opérateur stackalloc</span><span class="sxs-lookup"><span data-stu-id="2e3b4-122">stackalloc operator</span></span>](../operators/stackalloc.md)
