---
title: Tableau des conversions numériques implicites - Référence C#
ms.custom: seodec18
ms.date: 09/05/2018
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: 9c3efe1dbea355e8bc00ef44e08efcc9d0e0bdca
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424180"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="98c55-102">Tableau des conversions numériques implicites (référence C#)</span><span class="sxs-lookup"><span data-stu-id="98c55-102">Implicit numeric conversions table (C# Reference)</span></span>

<span data-ttu-id="98c55-103">Le tableau suivant montre les conversions implicites prédéfinies entre les types numériques .NET.</span><span class="sxs-lookup"><span data-stu-id="98c55-103">The following table shows the predefined implicit conversions between .NET numeric types.</span></span>
  
|<span data-ttu-id="98c55-104">From</span><span class="sxs-lookup"><span data-stu-id="98c55-104">From</span></span>|<span data-ttu-id="98c55-105">À</span><span class="sxs-lookup"><span data-stu-id="98c55-105">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="98c55-106">sbyte</span><span class="sxs-lookup"><span data-stu-id="98c55-106">sbyte</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="98c55-107">`short`, `int`, `long`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="98c55-107">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="98c55-108">byte</span><span class="sxs-lookup"><span data-stu-id="98c55-108">byte</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="98c55-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="98c55-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="98c55-110">char</span><span class="sxs-lookup"><span data-stu-id="98c55-110">char</span></span>](char.md)|<span data-ttu-id="98c55-111">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="98c55-111">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="98c55-112">short</span><span class="sxs-lookup"><span data-stu-id="98c55-112">short</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="98c55-113">`int`, `long`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="98c55-113">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="98c55-114">ushort</span><span class="sxs-lookup"><span data-stu-id="98c55-114">ushort</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="98c55-115">`int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="98c55-115">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="98c55-116">int</span><span class="sxs-lookup"><span data-stu-id="98c55-116">int</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="98c55-117">`long`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="98c55-117">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="98c55-118">uint</span><span class="sxs-lookup"><span data-stu-id="98c55-118">uint</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="98c55-119">`long`, `ulong`, `float`, `double` ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="98c55-119">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="98c55-120">long</span><span class="sxs-lookup"><span data-stu-id="98c55-120">long</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="98c55-121">`float`, `double`ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="98c55-121">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="98c55-122">ulong</span><span class="sxs-lookup"><span data-stu-id="98c55-122">ulong</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="98c55-123">`float`, `double`ou `decimal`</span><span class="sxs-lookup"><span data-stu-id="98c55-123">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="98c55-124">float</span><span class="sxs-lookup"><span data-stu-id="98c55-124">float</span></span>](float.md)|`double`|  
  
## <a name="remarks"></a><span data-ttu-id="98c55-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="98c55-125">Remarks</span></span>  

- <span data-ttu-id="98c55-126">Un [type intégral](../builtin-types/integral-numeric-types.md) est implicitement convertible en [type à virgule flottante](floating-point-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="98c55-126">Any [integral type](../builtin-types/integral-numeric-types.md) is implicitly convertible to any [floating-point type](floating-point-types-table.md).</span></span>

- <span data-ttu-id="98c55-127">La précision, et non la magnitude, peut être perdue dans les conversions de `int`, `uint`, `long` ou `ulong` à `float`, et de `long` ou `ulong` à `double`.</span><span class="sxs-lookup"><span data-stu-id="98c55-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`, `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
- <span data-ttu-id="98c55-128">Il n’existe aucune conversion implicite vers les types `char`, `byte` et `sbyte`.</span><span class="sxs-lookup"><span data-stu-id="98c55-128">There are no implicit conversions to the `char`, `byte`, and `sbyte` types.</span></span>  

- <span data-ttu-id="98c55-129">Il n’existe aucune conversion implicite à partir des types `double` et `decimal`.</span><span class="sxs-lookup"><span data-stu-id="98c55-129">There are no implicit conversions from the `double` and `decimal` types.</span></span>
  
- <span data-ttu-id="98c55-130">Il n’existe aucune conversion implicite entre le type `decimal` et le type `float` ou `double`.</span><span class="sxs-lookup"><span data-stu-id="98c55-130">There are no implicit conversions between the `decimal` type and the `float` or `double` types.</span></span>  
  
- <span data-ttu-id="98c55-131">La valeur d’une expression constante de type `int` (par exemple, une valeur représentée par un littéral intégral) peut être convertie en `sbyte`, `byte`, `short`, `ushort`, `uint` ou `ulong`, à condition qu’elle se trouve dans la plage du type de destination :</span><span class="sxs-lookup"><span data-stu-id="98c55-131">A value of a constant expression of type `int` (for example, a value represented by an integral literal) can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided it's within the range of the destination type:</span></span>

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

<span data-ttu-id="98c55-132">Pour plus d’informations sur les conversions implicites, consultez la section [Conversions implicites](~/_csharplang/spec/conversions.md#implicit-conversions) de la [Spécification du langage C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="98c55-132">For more information about implicit conversions, see the [Implicit conversions](~/_csharplang/spec/conversions.md#implicit-conversions) section of the [C# language specification](../language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="98c55-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98c55-133">See also</span></span>

- [<span data-ttu-id="98c55-134">Référence C#</span><span class="sxs-lookup"><span data-stu-id="98c55-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="98c55-135">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="98c55-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="98c55-136">Types intégraux</span><span class="sxs-lookup"><span data-stu-id="98c55-136">Integral types</span></span>](../builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="98c55-137">Tableau des types à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="98c55-137">Floating-point types table</span></span>](floating-point-types-table.md)
- [<span data-ttu-id="98c55-138">Tableaux des types intégrés</span><span class="sxs-lookup"><span data-stu-id="98c55-138">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="98c55-139">Tableau des conversions numériques explicites</span><span class="sxs-lookup"><span data-stu-id="98c55-139">Explicit numeric conversions table</span></span>](explicit-numeric-conversions-table.md)
- [<span data-ttu-id="98c55-140">Cast et conversions de types</span><span class="sxs-lookup"><span data-stu-id="98c55-140">Casting and type conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
