---
title: Énumérations
description: 'Découvrez comment utiliser des énumérations F # à la place de littéraux pour rendre votre code plus lisible et plus facile à gérer.'
ms.date: 08/15/2020
ms.openlocfilehash: 5f298691ce48a06c203930c7742cf007c819dc33
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812105"
---
# <a name="enumerations"></a><span data-ttu-id="baa28-103">Énumérations</span><span class="sxs-lookup"><span data-stu-id="baa28-103">Enumerations</span></span>

<span data-ttu-id="baa28-104">Les *énumérations*, également appelées « *enums*», sont des types intégraux où les étiquettes sont assignées à un sous-ensemble des valeurs.</span><span class="sxs-lookup"><span data-stu-id="baa28-104">*Enumerations*, also known as *enums*, , are integral types where labels are assigned to a subset of the values.</span></span> <span data-ttu-id="baa28-105">Vous pouvez les utiliser à la place de littéraux pour rendre le code plus lisible et plus facile à gérer.</span><span class="sxs-lookup"><span data-stu-id="baa28-105">You can use them in place of literals to make code more readable and maintainable.</span></span>

## <a name="syntax"></a><span data-ttu-id="baa28-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="baa28-106">Syntax</span></span>

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a><span data-ttu-id="baa28-107">Notes</span><span class="sxs-lookup"><span data-stu-id="baa28-107">Remarks</span></span>

<span data-ttu-id="baa28-108">Une énumération ressemble à une union discriminée qui a des valeurs simples, sauf que les valeurs peuvent être spécifiées.</span><span class="sxs-lookup"><span data-stu-id="baa28-108">An enumeration looks much like a discriminated union that has simple values, except that the values can be specified.</span></span> <span data-ttu-id="baa28-109">Les valeurs sont généralement des entiers qui commencent à 0 ou 1, ou des entiers qui représentent des positions de bits.</span><span class="sxs-lookup"><span data-stu-id="baa28-109">The values are typically integers that start at 0 or 1, or integers that represent bit positions.</span></span> <span data-ttu-id="baa28-110">Si une énumération est destinée à représenter des positions de bits, vous devez également utiliser l’attribut [Flags](xref:System.FlagsAttribute) .</span><span class="sxs-lookup"><span data-stu-id="baa28-110">If an enumeration is intended to represent bit positions, you should also use the [Flags](xref:System.FlagsAttribute) attribute.</span></span>

<span data-ttu-id="baa28-111">Le type sous-jacent de l’énumération est déterminé à partir du littéral utilisé. ainsi, par exemple, vous pouvez utiliser des littéraux avec un suffixe, tel que `1u` , `2u` , et ainsi de suite, pour un type entier non signé ( `uint32` ).</span><span class="sxs-lookup"><span data-stu-id="baa28-111">The underlying type of the enumeration is determined from the literal that is used, so that, for example, you can use literals with a suffix, such as `1u`, `2u`, and so on, for an unsigned integer (`uint32`) type.</span></span>

<span data-ttu-id="baa28-112">Quand vous faites référence aux valeurs nommées, vous devez utiliser le nom du type d’énumération lui-même en tant que qualificateur, autrement dit, `enum-name.value1` et pas seulement `value1` .</span><span class="sxs-lookup"><span data-stu-id="baa28-112">When you refer to the named values, you must use the name of the enumeration type itself as a qualifier, that is, `enum-name.value1`, not just `value1`.</span></span> <span data-ttu-id="baa28-113">Ce comportement diffère de celui des unions discriminées.</span><span class="sxs-lookup"><span data-stu-id="baa28-113">This behavior differs from that of discriminated unions.</span></span> <span data-ttu-id="baa28-114">Cela est dû au fait que les énumérations ont toujours l’attribut [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html) .</span><span class="sxs-lookup"><span data-stu-id="baa28-114">This is because enumerations always have the [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html) attribute.</span></span>

<span data-ttu-id="baa28-115">Le code suivant illustre la déclaration et l’utilisation d’une énumération.</span><span class="sxs-lookup"><span data-stu-id="baa28-115">The following code shows the declaration and use of an enumeration.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

<span data-ttu-id="baa28-116">Vous pouvez facilement convertir des énumérations au type sous-jacent à l’aide de l’opérateur approprié, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="baa28-116">You can easily convert enumerations to the underlying type by using the appropriate operator, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

<span data-ttu-id="baa28-117">Les types énumérés peuvent avoir l’un des types sous-jacents suivants : `sbyte` , `byte` , `int16` , `uint16` , `int32` , `uint32` , `int64` ,, `uint16` `uint64` et `char` .</span><span class="sxs-lookup"><span data-stu-id="baa28-117">Enumerated types can have one of the following underlying types: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, and `char`.</span></span> <span data-ttu-id="baa28-118">Les types énumération sont représentés dans le .NET Framework en tant que types hérités de qui `System.Enum` , à son tour, sont hérités de `System.ValueType` .</span><span class="sxs-lookup"><span data-stu-id="baa28-118">Enumeration types are represented in the .NET Framework as types that are inherited from `System.Enum`, which in turn is inherited from `System.ValueType`.</span></span> <span data-ttu-id="baa28-119">Par conséquent, il s’agit de types de valeur situés sur la pile ou inline dans l’objet conteneur, et toute valeur du type sous-jacent est une valeur valide de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="baa28-119">Thus, they are value types that are located on the stack or inline in the containing object, and any value of the underlying type is a valid value of the enumeration.</span></span> <span data-ttu-id="baa28-120">Cela est important quand vous utilisez des critères spéciaux sur des valeurs d’énumération, car vous devez fournir un modèle qui intercepte les valeurs sans nom.</span><span class="sxs-lookup"><span data-stu-id="baa28-120">This is significant when pattern matching on enumeration values, because you have to provide a pattern that catches the unnamed values.</span></span>

<span data-ttu-id="baa28-121">La `enum` fonction de la bibliothèque F # peut être utilisée pour générer une valeur d’énumération, même une valeur autre que l’une des valeurs nommées prédéfinies.</span><span class="sxs-lookup"><span data-stu-id="baa28-121">The `enum` function in the F# library can be used to generate an enumeration value, even a value other than one of the predefined, named values.</span></span> <span data-ttu-id="baa28-122">Vous utilisez la `enum` fonction comme suit.</span><span class="sxs-lookup"><span data-stu-id="baa28-122">You use the `enum` function as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

<span data-ttu-id="baa28-123">La fonction par défaut `enum` fonctionne avec le type `int32` .</span><span class="sxs-lookup"><span data-stu-id="baa28-123">The default `enum` function works with type `int32`.</span></span> <span data-ttu-id="baa28-124">Par conséquent, il ne peut pas être utilisé avec des types d’énumération qui ont d’autres types sous-jacents.</span><span class="sxs-lookup"><span data-stu-id="baa28-124">Therefore, it cannot be used with enumeration types that have other underlying types.</span></span> <span data-ttu-id="baa28-125">Au lieu de cela, utilisez ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="baa28-125">Instead, use the following.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]

<span data-ttu-id="baa28-126">En outre, les cas des enums sont toujours émis en tant que `public` .</span><span class="sxs-lookup"><span data-stu-id="baa28-126">Additionally, cases for enums are always emitted as `public`.</span></span> <span data-ttu-id="baa28-127">C’est pourquoi ils s’alignent avec C# et le reste de la plate-forme .NET.</span><span class="sxs-lookup"><span data-stu-id="baa28-127">This is so that they align with C# and the rest of the .NET platform.</span></span>

## <a name="see-also"></a><span data-ttu-id="baa28-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="baa28-128">See also</span></span>

- [<span data-ttu-id="baa28-129">Informations de référence sur le langage F #</span><span class="sxs-lookup"><span data-stu-id="baa28-129">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="baa28-130">Cast et conversions</span><span class="sxs-lookup"><span data-stu-id="baa28-130">Casting and Conversions</span></span>](casting-and-conversions.md)
