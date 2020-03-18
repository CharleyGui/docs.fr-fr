---
title: Types non managés - Référence C#
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 8a4599514115aa21f17c32848ce203fea704072e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846460"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="e10da-102">Types non managés (référence C#)</span><span class="sxs-lookup"><span data-stu-id="e10da-102">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="e10da-103">Un type est un **type non menté** s’il s’agit de l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="e10da-103">A type is an **unmanaged type** if it's any of the following types:</span></span>

- <span data-ttu-id="e10da-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` ou `bool`</span><span class="sxs-lookup"><span data-stu-id="e10da-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="e10da-105">Tout type [enum](enum.md)</span><span class="sxs-lookup"><span data-stu-id="e10da-105">Any [enum](enum.md) type</span></span>
- <span data-ttu-id="e10da-106">Tout type [de pointeur](../../programming-guide/unsafe-code-pointers/pointer-types.md)</span><span class="sxs-lookup"><span data-stu-id="e10da-106">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="e10da-107">Tout type [de struction](struct.md) défini par l’utilisateur qui ne contient que des champs de types non traités et, dans C 7.3 et plus tôt, n’est pas un type construit (un type qui comprend au moins un argument de type)</span><span class="sxs-lookup"><span data-stu-id="e10da-107">Any user-defined [struct](struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span></span>

<span data-ttu-id="e10da-108">En commençant par le C 7.3, vous pouvez utiliser la [ `unmanaged` contrainte](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) pour spécifier qu’un paramètre de type est un type non-pointeur et non-nullable non managérétique.</span><span class="sxs-lookup"><span data-stu-id="e10da-108">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer, non-nullable unmanaged type.</span></span>

<span data-ttu-id="e10da-109">Commençant par le C 8.0, un type de struct *construit* qui contient des champs de types non managéraux seulement n’est également non managéré, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="e10da-109">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span></span>

[!code-csharp[unmanaged constructed types](snippets/UnmanagedTypes.cs#ProgramExample)]

<span data-ttu-id="e10da-110">Une struct générique peut être la source de types construits non mentés et non non mentés.</span><span class="sxs-lookup"><span data-stu-id="e10da-110">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span></span> <span data-ttu-id="e10da-111">L’exemple précédent définit une `Coords<T>` struction générique et présente les exemples de types construits non mentés.</span><span class="sxs-lookup"><span data-stu-id="e10da-111">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span></span> <span data-ttu-id="e10da-112">L’exemple de ne pas un `Coords<object>`type non-gestion est .</span><span class="sxs-lookup"><span data-stu-id="e10da-112">The example of not an unmanaged type is `Coords<object>`.</span></span> <span data-ttu-id="e10da-113">Ce n’est pas unmanaged parce `object` qu’il a les champs du type, qui n’est pas non gestion.</span><span class="sxs-lookup"><span data-stu-id="e10da-113">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span></span> <span data-ttu-id="e10da-114">Si vous voulez que *tous les* types construits `unmanaged` soient des types non gémandés, utilisez la contrainte dans la définition d’une struct générique :</span><span class="sxs-lookup"><span data-stu-id="e10da-114">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span></span>

[!code-csharp[unmanaged constraint in type definition](snippets/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a><span data-ttu-id="e10da-115">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="e10da-115">C# language specification</span></span>

<span data-ttu-id="e10da-116">Pour plus d’informations, consultez la section [Types de pointeur](~/_csharplang/spec/unsafe-code.md#pointer-types) de la [Spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="e10da-116">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e10da-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e10da-117">See also</span></span>

- [<span data-ttu-id="e10da-118">Référence C#</span><span class="sxs-lookup"><span data-stu-id="e10da-118">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e10da-119">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="e10da-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="e10da-120">Types liés à la mémoire et à la travée</span><span class="sxs-lookup"><span data-stu-id="e10da-120">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="e10da-121">sizeof, opérateur</span><span class="sxs-lookup"><span data-stu-id="e10da-121">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="e10da-122">Opérateur stackalloc</span><span class="sxs-lookup"><span data-stu-id="e10da-122">stackalloc operator</span></span>](../operators/stackalloc.md)
