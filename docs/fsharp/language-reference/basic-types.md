---
title: Types de base
description: 'Découvrez les principaux types de base utilisés dans le langage F #.'
ms.date: 08/15/2020
ms.openlocfilehash: 659ac8424c62985affcca1741e1b2a74c9c3ee8d
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557696"
---
# <a name="basic-types"></a><span data-ttu-id="0a416-103">Types de base</span><span class="sxs-lookup"><span data-stu-id="0a416-103">Basic types</span></span>

<span data-ttu-id="0a416-104">Cette rubrique répertorie les types de base définis en langage F #.</span><span class="sxs-lookup"><span data-stu-id="0a416-104">This topic lists the basic types that are defined in the F# language.</span></span> <span data-ttu-id="0a416-105">Ces types sont les plus fondamentaux en F #, formant la base de presque tous les programmes F #.</span><span class="sxs-lookup"><span data-stu-id="0a416-105">These types are the most fundamental in F#, forming the basis of nearly every F# program.</span></span> <span data-ttu-id="0a416-106">Il s’agit d’un sur-ensemble de types primitifs .NET.</span><span class="sxs-lookup"><span data-stu-id="0a416-106">They are a superset of .NET primitive types.</span></span>

|<span data-ttu-id="0a416-107">Type</span><span class="sxs-lookup"><span data-stu-id="0a416-107">Type</span></span>|<span data-ttu-id="0a416-108">Type .NET</span><span class="sxs-lookup"><span data-stu-id="0a416-108">.NET type</span></span>|<span data-ttu-id="0a416-109">Description</span><span class="sxs-lookup"><span data-stu-id="0a416-109">Description</span></span>|<span data-ttu-id="0a416-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="0a416-110">Example</span></span>|
|----|---------|-----------|-------|
|`bool`|<xref:System.Boolean>|<span data-ttu-id="0a416-111">Les valeurs possibles sont `true` et `false`.</span><span class="sxs-lookup"><span data-stu-id="0a416-111">Possible values are `true` and `false`.</span></span>|`true`/`false`|
|`byte`|<xref:System.Byte>|<span data-ttu-id="0a416-112">Valeurs comprises entre 0 et 255.</span><span class="sxs-lookup"><span data-stu-id="0a416-112">Values from 0 to 255.</span></span>|`1uy`|
|`sbyte`|<xref:System.SByte>|<span data-ttu-id="0a416-113">Valeurs comprises entre-128 et 127.</span><span class="sxs-lookup"><span data-stu-id="0a416-113">Values from -128 to 127.</span></span>|`1y`|
|`int16`|<xref:System.Int16>|<span data-ttu-id="0a416-114">Valeurs comprises entre-32768 et 32767.</span><span class="sxs-lookup"><span data-stu-id="0a416-114">Values from -32768 to 32767.</span></span>|`1s`|
|`uint16`|<xref:System.UInt16>|<span data-ttu-id="0a416-115">Valeurs comprises entre 0 et 65535.</span><span class="sxs-lookup"><span data-stu-id="0a416-115">Values from 0 to 65535.</span></span>|`1us`|
|`int`|<xref:System.Int32>|<span data-ttu-id="0a416-116">Valeurs comprises entre-2 147 483 648 et 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="0a416-116">Values from -2,147,483,648 to 2,147,483,647.</span></span>|`1`|
|`uint`|<xref:System.UInt32>|<span data-ttu-id="0a416-117">Valeurs comprises entre 0 et 4 294 967 295.</span><span class="sxs-lookup"><span data-stu-id="0a416-117">Values from 0 to 4,294,967,295.</span></span>|`1u`|
|`int64`|<xref:System.Int64>|<span data-ttu-id="0a416-118">Valeurs comprises entre-9223372036854775808 et 9 223 372 036 854 775 807.</span><span class="sxs-lookup"><span data-stu-id="0a416-118">Values from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.</span></span>|`1L`|
|`uint64`|<xref:System.UInt64>|<span data-ttu-id="0a416-119">Valeurs comprises entre 0 et 18446744073709551615.</span><span class="sxs-lookup"><span data-stu-id="0a416-119">Values from 0 to 18,446,744,073,709,551,615.</span></span>|`1UL`|
|`nativeint`|<xref:System.IntPtr>|<span data-ttu-id="0a416-120">Pointeur natif en tant qu’entier signé.</span><span class="sxs-lookup"><span data-stu-id="0a416-120">A native pointer as a signed integer.</span></span>|`nativeint 1`|
|`unativeint`|<xref:System.UIntPtr>|<span data-ttu-id="0a416-121">Pointeur natif sous la forme d’un entier non signé.</span><span class="sxs-lookup"><span data-stu-id="0a416-121">A native pointer as an unsigned integer.</span></span>|`unativeint 1`|
|`decimal`|<xref:System.Decimal>|<span data-ttu-id="0a416-122">Type de données à virgule flottante qui contient au moins 28 chiffres significatifs.</span><span class="sxs-lookup"><span data-stu-id="0a416-122">A floating point data type that has at least 28 significant digits.</span></span>|`1.0`|
|<span data-ttu-id="0a416-123">`float`, `double`</span><span class="sxs-lookup"><span data-stu-id="0a416-123">`float`, `double`</span></span>|<xref:System.Double>|<span data-ttu-id="0a416-124">Type à virgule flottante 64 bits.</span><span class="sxs-lookup"><span data-stu-id="0a416-124">A 64-bit floating point type.</span></span>|`1.0`|
|<span data-ttu-id="0a416-125">`float32`, `single`</span><span class="sxs-lookup"><span data-stu-id="0a416-125">`float32`, `single`</span></span>|<xref:System.Single>|<span data-ttu-id="0a416-126">Type à virgule flottante 32 bits.</span><span class="sxs-lookup"><span data-stu-id="0a416-126">A 32-bit floating point type.</span></span>|`1.0f`|
|`char`|<xref:System.Char>|<span data-ttu-id="0a416-127">Valeurs de caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="0a416-127">Unicode character values.</span></span>|`'c'`|
|`string`|<xref:System.String>|<span data-ttu-id="0a416-128">Texte Unicode.</span><span class="sxs-lookup"><span data-stu-id="0a416-128">Unicode text.</span></span>|`"str"`|
|`unit`|<span data-ttu-id="0a416-129">Non applicable</span><span class="sxs-lookup"><span data-stu-id="0a416-129">not applicable</span></span>|<span data-ttu-id="0a416-130">Indique l’absence d’une valeur réelle.</span><span class="sxs-lookup"><span data-stu-id="0a416-130">Indicates the absence of an actual value.</span></span> <span data-ttu-id="0a416-131">Le type a une seule valeur formelle, ce qui est indiqué `()` .</span><span class="sxs-lookup"><span data-stu-id="0a416-131">The type has only one formal value, which is denoted `()`.</span></span> <span data-ttu-id="0a416-132">La valeur d’unité, `()` , est souvent utilisée comme un espace réservé dans lequel une valeur est nécessaire, mais aucune valeur réelle n’est disponible ou logique.</span><span class="sxs-lookup"><span data-stu-id="0a416-132">The unit value, `()`, is often used as a placeholder where a value is needed but no real value is available or makes sense.</span></span>|`()`|

> [!NOTE]
> <span data-ttu-id="0a416-133">Vous pouvez effectuer des calculs avec des entiers trop grands pour le type d’entier 64 bits à l’aide du type [bigint](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-bigint.html) .</span><span class="sxs-lookup"><span data-stu-id="0a416-133">You can perform computations with integers too big for the 64-bit integer type by using the [bigint](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-bigint.html) type.</span></span> <span data-ttu-id="0a416-134">`bigint` n’est pas considéré comme un type de base ; Il s’agit d’une abréviation pour `System.Numerics.BigInteger` .</span><span class="sxs-lookup"><span data-stu-id="0a416-134">`bigint` is not considered a basic type; it is an abbreviation for `System.Numerics.BigInteger`.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a416-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a416-135">See also</span></span>

- [<span data-ttu-id="0a416-136">Informations de référence sur le langage F #</span><span class="sxs-lookup"><span data-stu-id="0a416-136">F# Language Reference</span></span>](index.md)
