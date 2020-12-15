---
title: Comment effectuer une conversion entre des chaînes hexadécimales et des types numériques (Guide de programmation C#)
description: Découvrez comment effectuer une conversion entre des chaînes hexadécimales et des types numériques. Consultez des exemples de code et affichez des ressources disponibles supplémentaires.
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: 18021156af879f324993beca04531c8a822725db
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513235"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="246c3-104">Comment effectuer une conversion entre des chaînes hexadécimales et des types numériques (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="246c3-104">How to convert between hexadecimal strings and numeric types (C# Programming Guide)</span></span>

<span data-ttu-id="246c3-105">Ces exemples montrent comment effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="246c3-105">These examples show you how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="246c3-106">Obtenir la valeur hexadécimale de chaque caractère dans une chaîne ([string](../../language-reference/builtin-types/reference-types.md)).</span><span class="sxs-lookup"><span data-stu-id="246c3-106">Obtain the hexadecimal value of each character in a [string](../../language-reference/builtin-types/reference-types.md).</span></span>  
  
- <span data-ttu-id="246c3-107">Obtenir la valeur [char](../../language-reference/builtin-types/char.md) qui correspond à chaque valeur d’une chaîne hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="246c3-107">Obtain the [char](../../language-reference/builtin-types/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
- <span data-ttu-id="246c3-108">Convertir une `string` hexadécimale en [int](../../language-reference/builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="246c3-108">Convert a hexadecimal `string` to an [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
- <span data-ttu-id="246c3-109">Convertir une `string` hexadécimale en [float](../../language-reference/builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="246c3-109">Convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md).</span></span>  
  
- <span data-ttu-id="246c3-110">Convertir un tableau d’[octets](../../language-reference/builtin-types/integral-numeric-types.md) en `string` hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="246c3-110">Convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="246c3-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="246c3-111">Example</span></span>  

 <span data-ttu-id="246c3-112">Cet exemple génère la valeur hexadécimale de chaque caractère dans une `string`.</span><span class="sxs-lookup"><span data-stu-id="246c3-112">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="246c3-113">Il convertit d’abord la `string` en un tableau de caractères.</span><span class="sxs-lookup"><span data-stu-id="246c3-113">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="246c3-114">Ensuite, il appelle <xref:System.Convert.ToInt32%28System.Char%29> sur chaque caractère afin d’obtenir sa valeur numérique.</span><span class="sxs-lookup"><span data-stu-id="246c3-114">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="246c3-115">Pour finir, il représente le nombre sous forme hexadécimale dans une `string`.</span><span class="sxs-lookup"><span data-stu-id="246c3-115">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a><span data-ttu-id="246c3-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="246c3-116">Example</span></span>  

 <span data-ttu-id="246c3-117">Cet exemple analyse une `string` de valeurs hexadécimales et génère le caractère correspondant à chacune d’elles.</span><span class="sxs-lookup"><span data-stu-id="246c3-117">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="246c3-118">Tout d’abord, elle appelle la méthode [Split (char \[ \] )](xref:System.String.Split(System.Char[])) pour obtenir chaque valeur hexadécimale en tant qu’individu `string` dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="246c3-118">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="246c3-119">Il appelle ensuite <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> pour convertir la valeur hexadécimale en valeur décimale représentée sous la forme d’un [entier](../../language-reference/builtin-types/integral-numeric-types.md). Il montre deux façons différentes d’obtenir le caractère correspondant à ce code de caractère.</span><span class="sxs-lookup"><span data-stu-id="246c3-119">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../language-reference/builtin-types/integral-numeric-types.md). It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="246c3-120">La première technique utilise `string`, qui retourne le caractère correspondant à l’argument entier sous forme de <xref:System.Char.ConvertFromUtf32%28System.Int32%29>.</span><span class="sxs-lookup"><span data-stu-id="246c3-120">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="246c3-121">La deuxième technique effectue un cast explicite de l’`int` en [char](../../language-reference/builtin-types/char.md).</span><span class="sxs-lookup"><span data-stu-id="246c3-121">The second technique explicitly casts the `int` to a [char](../../language-reference/builtin-types/char.md).</span></span>  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a><span data-ttu-id="246c3-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="246c3-122">Example</span></span>  

 <span data-ttu-id="246c3-123">Cet exemple montre une autre façon de convertir un `string` hexadécimal en entier, en appelant la méthode <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29>.</span><span class="sxs-lookup"><span data-stu-id="246c3-123">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a><span data-ttu-id="246c3-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="246c3-124">Example</span></span>  

 <span data-ttu-id="246c3-125">L’exemple suivant montre comment convertir un `string` hexadécimal en [float](../../language-reference/builtin-types/floating-point-numeric-types.md) à l’aide de la classe <xref:System.BitConverter?displayProperty=nameWithType> et de la méthode <xref:System.UInt32.Parse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="246c3-125">The following example shows how to convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md) by using the <xref:System.BitConverter?displayProperty=nameWithType> class and the <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a><span data-ttu-id="246c3-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="246c3-126">Example</span></span>  

 <span data-ttu-id="246c3-127">L’exemple suivant montre comment convertir un tableau d’[octets](../../language-reference/builtin-types/integral-numeric-types.md) en chaîne hexadécimale à l’aide de la classe <xref:System.BitConverter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="246c3-127">The following example shows how to convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=nameWithType> class.</span></span>  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="246c3-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="246c3-128">See also</span></span>

- [<span data-ttu-id="246c3-129">Chaînes de format numériques standard</span><span class="sxs-lookup"><span data-stu-id="246c3-129">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="246c3-130">Types</span><span class="sxs-lookup"><span data-stu-id="246c3-130">Types</span></span>](./index.md)
- [<span data-ttu-id="246c3-131">Comment déterminer si une chaîne représente une valeur numérique</span><span class="sxs-lookup"><span data-stu-id="246c3-131">How to determine whether a string represents a numeric value</span></span>](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
