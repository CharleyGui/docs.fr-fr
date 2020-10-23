---
description: 'En savoir plus sur les types non managés dans C #'
title: Types non managés - Référence C#
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 4374872af13c94e1a1af6b9f2c431f076c6f7dff
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471797"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="e419b-103">Types non managés (référence C#)</span><span class="sxs-lookup"><span data-stu-id="e419b-103">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="e419b-104">Un type est un **type non managé** s’il s’agit de l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="e419b-104">A type is an **unmanaged type** if it's any of the following types:</span></span>

- <span data-ttu-id="e419b-105">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` ou `bool`</span><span class="sxs-lookup"><span data-stu-id="e419b-105">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="e419b-106">Tout type [enum](enum.md)</span><span class="sxs-lookup"><span data-stu-id="e419b-106">Any [enum](enum.md) type</span></span>
- <span data-ttu-id="e419b-107">Tout type [pointeur](../../programming-guide/unsafe-code-pointers/pointer-types.md)</span><span class="sxs-lookup"><span data-stu-id="e419b-107">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="e419b-108">Tout type [struct](struct.md) défini par l’utilisateur qui contient des champs de types non managés uniquement et, en C# 7,3 et antérieur, n’est pas un type construit (un type qui inclut au moins un argument de type)</span><span class="sxs-lookup"><span data-stu-id="e419b-108">Any user-defined [struct](struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span></span>

<span data-ttu-id="e419b-109">À compter de C# 7,3, vous pouvez utiliser la [ `unmanaged` contrainte](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) pour spécifier qu’un paramètre de type est un type non managé qui n’est pas un pointeur, non Nullable.</span><span class="sxs-lookup"><span data-stu-id="e419b-109">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer, non-nullable unmanaged type.</span></span>

<span data-ttu-id="e419b-110">À compter de C# 8,0, un type struct *construit* qui contient des champs de types non managés uniquement est également non managé, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="e419b-110">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span></span>

[!code-csharp[unmanaged constructed types](snippets/shared/UnmanagedTypes.cs#ProgramExample)]

<span data-ttu-id="e419b-111">Un struct générique peut être la source des types construits non managés et non managés.</span><span class="sxs-lookup"><span data-stu-id="e419b-111">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span></span> <span data-ttu-id="e419b-112">L’exemple précédent définit un struct générique `Coords<T>` et présente les exemples de types construits non managés.</span><span class="sxs-lookup"><span data-stu-id="e419b-112">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span></span> <span data-ttu-id="e419b-113">L’exemple de n’est pas un type non managé `Coords<object>` .</span><span class="sxs-lookup"><span data-stu-id="e419b-113">The example of not an unmanaged type is `Coords<object>`.</span></span> <span data-ttu-id="e419b-114">Elle n’est pas non plus gérée, car elle contient les champs du `object` type, qui ne sont pas non managés.</span><span class="sxs-lookup"><span data-stu-id="e419b-114">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span></span> <span data-ttu-id="e419b-115">Si vous souhaitez que *tous les* types construits soient des types non managés, utilisez la `unmanaged` contrainte dans la définition d’un struct générique :</span><span class="sxs-lookup"><span data-stu-id="e419b-115">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span></span>

[!code-csharp[unmanaged constraint in type definition](snippets/shared/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a><span data-ttu-id="e419b-116">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="e419b-116">C# language specification</span></span>

<span data-ttu-id="e419b-117">Pour plus d’informations, consultez la section [Types de pointeur](~/_csharplang/spec/unsafe-code.md#pointer-types) de la [Spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="e419b-117">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e419b-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e419b-118">See also</span></span>

- [<span data-ttu-id="e419b-119">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="e419b-119">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e419b-120">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="e419b-120">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="e419b-121">Types liés à la mémoire et à l’étendue</span><span class="sxs-lookup"><span data-stu-id="e419b-121">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="e419b-122">Opérateur sizeof</span><span class="sxs-lookup"><span data-stu-id="e419b-122">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="e419b-123">stackalloc</span><span class="sxs-lookup"><span data-stu-id="e419b-123">stackalloc</span></span>](../operators/stackalloc.md)
