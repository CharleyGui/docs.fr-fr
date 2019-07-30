---
title: Types non managés - Référence C#
ms.date: 07/23/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 2b675be5dbc61006725549f4b69284326650401d
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512076"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="0e598-102">Types non managés (référence C#)</span><span class="sxs-lookup"><span data-stu-id="0e598-102">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="0e598-103">Un **type non managé** est un type qui n’est ni un type référence ni un type construit (type comprenant au moins un argument de type) et qui ne contient pas de champs de type référence ou de type construit, quel que soit le niveau d’imbrication.</span><span class="sxs-lookup"><span data-stu-id="0e598-103">An **unmanaged type** is any type that isn't a reference type or constructed type (a type that includes at least one type argument), and doesn't contain reference type or constructed type fields at any level of nesting.</span></span> <span data-ttu-id="0e598-104">En d’autres termes, un type non managé est l’un des suivants :</span><span class="sxs-lookup"><span data-stu-id="0e598-104">In other words, an unmanaged type is one of the following:</span></span>

- <span data-ttu-id="0e598-105">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` ou `bool`</span><span class="sxs-lookup"><span data-stu-id="0e598-105">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="0e598-106">Tout type [enum](../keywords/enum.md)</span><span class="sxs-lookup"><span data-stu-id="0e598-106">Any [enum](../keywords/enum.md) type</span></span>
- <span data-ttu-id="0e598-107">Tout type [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md)</span><span class="sxs-lookup"><span data-stu-id="0e598-107">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="0e598-108">Tout type [struct](../keywords/struct.md) défini par l’utilisateur n’étant pas un type construit et contenant des champs de types non managés uniquement</span><span class="sxs-lookup"><span data-stu-id="0e598-108">Any user-defined [struct](../keywords/struct.md) type that is not a constructed type and contains fields of unmanaged types only</span></span>

<span data-ttu-id="0e598-109">À compter de C# 7.3, vous pouvez utiliser la [`unmanaged`contrainte](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) pour spécifier qu’un paramètre de type est un type non managé « non-pointer ».</span><span class="sxs-lookup"><span data-stu-id="0e598-109">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer unmanaged type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0e598-110">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="0e598-110">C# language specification</span></span>

<span data-ttu-id="0e598-111">Pour plus d’informations, consultez la section [Types de pointeur](~/_csharplang/spec/unsafe-code.md#pointer-types) de la [Spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="0e598-111">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0e598-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e598-112">See also</span></span>

- [<span data-ttu-id="0e598-113">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="0e598-113">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0e598-114">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="0e598-114">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="0e598-115">Types liés à la mémoire et à l’étendue</span><span class="sxs-lookup"><span data-stu-id="0e598-115">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="0e598-116">Opérateur sizeof</span><span class="sxs-lookup"><span data-stu-id="0e598-116">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="0e598-117">Opérateur stackalloc</span><span class="sxs-lookup"><span data-stu-id="0e598-117">stackalloc operator</span></span>](../operators/stackalloc.md)
