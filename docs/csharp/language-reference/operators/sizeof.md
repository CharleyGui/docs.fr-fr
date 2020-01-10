---
title: sizeof, opérateur- Référence C#
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: c88f205a616587e5437bf4fc81bcbdcbbc19a9ac
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712635"
---
# <a name="sizeof-operator-c-reference"></a><span data-ttu-id="af3f3-102">sizeof, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="af3f3-102">sizeof operator (C# reference)</span></span>

<span data-ttu-id="af3f3-103">L’opérateur `sizeof` retourne le nombre d’octets occupés par une variable d’un type donné.</span><span class="sxs-lookup"><span data-stu-id="af3f3-103">The `sizeof` operator returns the number of bytes occupied by a variable of a given type.</span></span> <span data-ttu-id="af3f3-104">L’argument de l’opérateur `sizeof` doit être le nom d’un [type non managé](../builtin-types/unmanaged-types.md) ou d’un paramètre de type qui est [contraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) comme type non managé.</span><span class="sxs-lookup"><span data-stu-id="af3f3-104">The argument to the `sizeof` operator must be the name of an [unmanaged type](../builtin-types/unmanaged-types.md) or a type parameter that is [constrained](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to be an unmanaged type.</span></span>

<span data-ttu-id="af3f3-105">L’opérateur `sizeof` nécessite un contexte [unsafe](../keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="af3f3-105">The `sizeof` operator requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="af3f3-106">Toutefois, les expressions présentées dans le tableau suivant sont évaluées au moment de la compilation par rapport aux valeurs de constante correspondantes et ne nécessitent pas de contexte unsafe :</span><span class="sxs-lookup"><span data-stu-id="af3f3-106">However, the expressions presented in the following table are evaluated in compile time to the corresponding constant values and don't require an unsafe context:</span></span>

|<span data-ttu-id="af3f3-107">Expression</span><span class="sxs-lookup"><span data-stu-id="af3f3-107">Expression</span></span>|<span data-ttu-id="af3f3-108">Valeur constante</span><span class="sxs-lookup"><span data-stu-id="af3f3-108">Constant value</span></span>|
|---------|---------------|
|`sizeof(sbyte)`|<span data-ttu-id="af3f3-109">1</span><span class="sxs-lookup"><span data-stu-id="af3f3-109">1</span></span>|
|`sizeof(byte)`|<span data-ttu-id="af3f3-110">1</span><span class="sxs-lookup"><span data-stu-id="af3f3-110">1</span></span>|
|`sizeof(short)`|<span data-ttu-id="af3f3-111">2</span><span class="sxs-lookup"><span data-stu-id="af3f3-111">2</span></span>|
|`sizeof(ushort)`|<span data-ttu-id="af3f3-112">2</span><span class="sxs-lookup"><span data-stu-id="af3f3-112">2</span></span>|
|`sizeof(int)`|<span data-ttu-id="af3f3-113">4</span><span class="sxs-lookup"><span data-stu-id="af3f3-113">4</span></span>|
|`sizeof(uint)`|<span data-ttu-id="af3f3-114">4</span><span class="sxs-lookup"><span data-stu-id="af3f3-114">4</span></span>|
|`sizeof(long)`|<span data-ttu-id="af3f3-115">8</span><span class="sxs-lookup"><span data-stu-id="af3f3-115">8</span></span>|
|`sizeof(ulong)`|<span data-ttu-id="af3f3-116">8</span><span class="sxs-lookup"><span data-stu-id="af3f3-116">8</span></span>|
|`sizeof(char)`|<span data-ttu-id="af3f3-117">2</span><span class="sxs-lookup"><span data-stu-id="af3f3-117">2</span></span>|
|`sizeof(float)`|<span data-ttu-id="af3f3-118">4</span><span class="sxs-lookup"><span data-stu-id="af3f3-118">4</span></span>|
|`sizeof(double)`|<span data-ttu-id="af3f3-119">8</span><span class="sxs-lookup"><span data-stu-id="af3f3-119">8</span></span>|
|`sizeof(decimal)`|<span data-ttu-id="af3f3-120">16</span><span class="sxs-lookup"><span data-stu-id="af3f3-120">16</span></span>|
|`sizeof(bool)`|<span data-ttu-id="af3f3-121">1</span><span class="sxs-lookup"><span data-stu-id="af3f3-121">1</span></span>|

<span data-ttu-id="af3f3-122">Vous n’avez pas non plus besoin d’utiliser un contexte unsafe quand l’opérande de l’opérateur `sizeof` est le nom d’un type [enum](../builtin-types/enum.md).</span><span class="sxs-lookup"><span data-stu-id="af3f3-122">You also don't need to use an unsafe context when the operand of the `sizeof` operator is the name of an [enum](../builtin-types/enum.md) type.</span></span>

<span data-ttu-id="af3f3-123">L’exemple suivant illustre l’utilisation de l’opérateur `sizeof` :</span><span class="sxs-lookup"><span data-stu-id="af3f3-123">The following example demonstrates the usage of the `sizeof` operator:</span></span>

[!code-csharp[sizeof examples](~/samples/csharp/language-reference/operators/SizeOfOperator.cs)]

<span data-ttu-id="af3f3-124">L’opérateur `sizeof` retourne un nombre d’octets qui seraient alloués par la Common Language Runtime dans la mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="af3f3-124">The `sizeof` operator returns a number of bytes that would be allocated by the common language runtime in managed memory.</span></span> <span data-ttu-id="af3f3-125">Pour les types [struct](../keywords/struct.md), cette valeur comprend le remplissage, comme le montre l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="af3f3-125">For [struct](../keywords/struct.md) types, that value includes any padding, as the preceding example demonstrates.</span></span> <span data-ttu-id="af3f3-126">Le résultat de l’opérateur `sizeof` peut différer de celui de la méthode <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>, qui retourne la taille d’un type dans la mémoire *non managée*.</span><span class="sxs-lookup"><span data-stu-id="af3f3-126">The result of the `sizeof` operator might differ from the result of the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, which returns the size of a type in *unmanaged* memory.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="af3f3-127">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="af3f3-127">C# language specification</span></span>

<span data-ttu-id="af3f3-128">Pour plus d’informations, consultez la section [Opérateur sizeof](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="af3f3-128">For more information, see [The sizeof operator](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="af3f3-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af3f3-129">See also</span></span>

- [<span data-ttu-id="af3f3-130">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="af3f3-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="af3f3-131">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="af3f3-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="af3f3-132">Opérateurs associés au pointeur</span><span class="sxs-lookup"><span data-stu-id="af3f3-132">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="af3f3-133">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="af3f3-133">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="af3f3-134">Types liés à la mémoire et à l’étendue</span><span class="sxs-lookup"><span data-stu-id="af3f3-134">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="af3f3-135">Génériques en .NET</span><span class="sxs-lookup"><span data-stu-id="af3f3-135">Generics in .NET</span></span>](../../../standard/generics/index.md)
