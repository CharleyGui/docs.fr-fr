---
title: Types non managés - Référence C#
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 25aa42ba8c8f0023b4f818feb2edbb325f805fb6
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374116"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="f0b98-102">Types non managés (référence C#)</span><span class="sxs-lookup"><span data-stu-id="f0b98-102">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="f0b98-103">Un type est un **type non managé** s’il s’agit de l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="f0b98-103">A type is an **unmanaged type** if it's any of the following types:</span></span>

- <span data-ttu-id="f0b98-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` ou `bool`</span><span class="sxs-lookup"><span data-stu-id="f0b98-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="f0b98-105">Tout type [enum](../keywords/enum.md)</span><span class="sxs-lookup"><span data-stu-id="f0b98-105">Any [enum](../keywords/enum.md) type</span></span>
- <span data-ttu-id="f0b98-106">Tout type [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md)</span><span class="sxs-lookup"><span data-stu-id="f0b98-106">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="f0b98-107">Tout type [struct](../keywords/struct.md) défini par l’utilisateur qui contient des champs de types non managés uniquement et C# , dans 7,3 et les versions antérieures, n’est pas un type construit (un type qui inclut au moins un argument de type)</span><span class="sxs-lookup"><span data-stu-id="f0b98-107">Any user-defined [struct](../keywords/struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span></span>

<span data-ttu-id="f0b98-108">À compter de C# 7.3, vous pouvez utiliser la [`unmanaged`contrainte](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) pour spécifier qu’un paramètre de type est un type non managé « non-pointer ».</span><span class="sxs-lookup"><span data-stu-id="f0b98-108">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer unmanaged type.</span></span>

<span data-ttu-id="f0b98-109">À C# partir de 8,0, un type struct *construit* qui contient des champs de types non managés uniquement est également non managé, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f0b98-109">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span></span>

[!code-csharp[unmanaged constructed types](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#ProgramExample)]

<span data-ttu-id="f0b98-110">Un struct générique peut être la source des types construits non managés et non managés.</span><span class="sxs-lookup"><span data-stu-id="f0b98-110">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span></span> <span data-ttu-id="f0b98-111">L’exemple précédent définit un struct `Coords<T>` générique et présente les exemples de types construits non managés.</span><span class="sxs-lookup"><span data-stu-id="f0b98-111">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span></span> <span data-ttu-id="f0b98-112">L’exemple de n’est `Coords<object>`pas un type non managé.</span><span class="sxs-lookup"><span data-stu-id="f0b98-112">The example of not an unmanaged type is `Coords<object>`.</span></span> <span data-ttu-id="f0b98-113">Elle n’est pas non plus gérée, car elle contient les `object` champs du type, qui ne sont pas non managés.</span><span class="sxs-lookup"><span data-stu-id="f0b98-113">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span></span> <span data-ttu-id="f0b98-114">Si vous souhaitez que *tous les* types construits soient des types non managés, `unmanaged` utilisez la contrainte dans la définition d’un struct générique :</span><span class="sxs-lookup"><span data-stu-id="f0b98-114">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span></span>

[!code-csharp[unmanaged constraint in type definition](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a><span data-ttu-id="f0b98-115">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="f0b98-115">C# language specification</span></span>

<span data-ttu-id="f0b98-116">Pour plus d’informations, consultez la section [Types de pointeur](~/_csharplang/spec/unsafe-code.md#pointer-types) de la [Spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="f0b98-116">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f0b98-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0b98-117">See also</span></span>

- [<span data-ttu-id="f0b98-118">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="f0b98-118">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f0b98-119">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="f0b98-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="f0b98-120">Types liés à la mémoire et à l’étendue</span><span class="sxs-lookup"><span data-stu-id="f0b98-120">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="f0b98-121">Opérateur sizeof</span><span class="sxs-lookup"><span data-stu-id="f0b98-121">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="f0b98-122">Opérateur stackalloc</span><span class="sxs-lookup"><span data-stu-id="f0b98-122">stackalloc operator</span></span>](../operators/stackalloc.md)
