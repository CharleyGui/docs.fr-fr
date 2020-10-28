---
title: Suppression d’espaces et de caractères dans .NET
description: Apprenez à supprimer les espaces vides à partir du début ou de la fin d’une chaîne, ou à supprimer un nombre quelconque d’espaces ou de caractères à partir d’une position spécifiée dans la chaîne dans .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strings [.NET], removing characters
- Remove method
- TrimEnd method
- Trim method
- trimming characters
- TrimStart method
- removing characters
ms.assetid: ab248dab-70d4-4413-81c6-542d153fd195
ms.openlocfilehash: d0057d503474f3f6ff886acda3ce1d72fb3ebe21
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888592"
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a><span data-ttu-id="21c65-103">Suppression d’espaces et de caractères dans .NET</span><span class="sxs-lookup"><span data-stu-id="21c65-103">Trimming and Removing Characters from Strings in .NET</span></span>
<span data-ttu-id="21c65-104">Si vous analysez une phrase en mots individuels, vous risquez d’obtenir des mots incluant des espaces vides (également appelés espaces blancs) à chaque extrémité du mot.</span><span class="sxs-lookup"><span data-stu-id="21c65-104">If you are parsing a sentence into individual words, you might end up with words that have blank spaces (also called white spaces) on either end of the word.</span></span> <span data-ttu-id="21c65-105">Dans ce cas, vous pouvez utiliser l’une des méthodes de suppression de la classe **System.String** pour supprimer n’importe quel nombre d’espaces ou d’autres caractères à partir d’une position spécifiée dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="21c65-105">In this situation, you can use one of the trim methods in the **System.String** class to remove any number of spaces or other characters from a specified position in the string.</span></span> <span data-ttu-id="21c65-106">Le tableau suivant décrit les méthodes de suppression disponibles.</span><span class="sxs-lookup"><span data-stu-id="21c65-106">The following table describes the available trim methods.</span></span>  
  
|<span data-ttu-id="21c65-107">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="21c65-107">Method name</span></span>|<span data-ttu-id="21c65-108">Utilisation</span><span class="sxs-lookup"><span data-stu-id="21c65-108">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|<span data-ttu-id="21c65-109">Supprime les espaces blancs ou caractères spécifiés dans un tableau de caractères à partir du début et la fin d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="21c65-109">Removes white spaces or characters specified in an array of characters from the beginning and end of a string.</span></span>|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|<span data-ttu-id="21c65-110">Supprime les caractères spécifiés dans un tableau de caractères à partir de la fin d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="21c65-110">Removes characters specified in an array of characters from the end of a string.</span></span>|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|<span data-ttu-id="21c65-111">Supprime les caractères spécifiés dans un tableau de caractères à partir du début d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="21c65-111">Removes characters specified in an array of characters from the beginning of a string.</span></span>|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="21c65-112">Supprime un nombre spécifié de caractères à partir de la position d’index spécifiée dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="21c65-112">Removes a specified number of characters from a specified index position in a string.</span></span>|  
  
## <a name="trim"></a><span data-ttu-id="21c65-113">Supprimer les espaces</span><span class="sxs-lookup"><span data-stu-id="21c65-113">Trim</span></span>

 <span data-ttu-id="21c65-114">Vous pouvez facilement supprimer les espaces blancs situés aux deux extrémités d’une chaîne à l’aide de la méthode <xref:System.String.Trim%2A?displayProperty=nameWithType>, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="21c65-114">You can easily remove white spaces from both ends of a string by using the <xref:System.String.Trim%2A?displayProperty=nameWithType> method, as shown in the following example.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 <span data-ttu-id="21c65-115">Vous pouvez également supprimer les caractères que vous spécifiez dans un tableau de caractères à partir du début et de la fin d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="21c65-115">You can also remove characters that you specify in a character array from the beginning and end of a string.</span></span> <span data-ttu-id="21c65-116">L’exemple suivant permet de supprimer les espaces blancs, les points et les astérisques.</span><span class="sxs-lookup"><span data-stu-id="21c65-116">The following example removes white-space characters, periods, and asterisks.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a><span data-ttu-id="21c65-117">TrimEnd</span><span class="sxs-lookup"><span data-stu-id="21c65-117">TrimEnd</span></span>

 <span data-ttu-id="21c65-118">La méthode **String.TrimEnd** supprime les caractères à partir de la fin d’une chaîne, créant ainsi un objet String.</span><span class="sxs-lookup"><span data-stu-id="21c65-118">The **String.TrimEnd** method removes characters from the end of a string, creating a new string object.</span></span> <span data-ttu-id="21c65-119">Un tableau de caractères est passé à cette méthode pour spécifier les caractères à supprimer.</span><span class="sxs-lookup"><span data-stu-id="21c65-119">An array of characters is passed to this method to specify the characters to be removed.</span></span> <span data-ttu-id="21c65-120">L’ordre des éléments dans le tableau de caractères n’affecte pas l’opération de suppression.</span><span class="sxs-lookup"><span data-stu-id="21c65-120">The order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="21c65-121">La suppression s’arrête lorsqu’un caractère non spécifié dans le tableau est trouvé.</span><span class="sxs-lookup"><span data-stu-id="21c65-121">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="21c65-122">L’exemple suivant supprime les dernières lettres d’une chaîne à l’aide de la méthode **TrimEnd** .</span><span class="sxs-lookup"><span data-stu-id="21c65-122">The following example removes the last letters of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="21c65-123">Dans cet exemple, la position du caractère `'r'` et du caractère `'W'` est inversée pour illustrer que l’ordre des caractères dans le tableau n’a pas d’importance.</span><span class="sxs-lookup"><span data-stu-id="21c65-123">In this example, the position of the `'r'` character and the `'W'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span> <span data-ttu-id="21c65-124">Remarquez que ce code supprime le dernier mot de `MyString` plus une partie du premier.</span><span class="sxs-lookup"><span data-stu-id="21c65-124">Notice that this code removes the last word of `MyString` plus part of the first.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 <span data-ttu-id="21c65-125">Ce code affiche `He` dans la console.</span><span class="sxs-lookup"><span data-stu-id="21c65-125">This code displays `He` to the console.</span></span>  
  
 <span data-ttu-id="21c65-126">L’exemple suivant supprime le dernier mot d’une chaîne à l’aide de la méthode **TrimEnd** .</span><span class="sxs-lookup"><span data-stu-id="21c65-126">The following example removes the last word of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="21c65-127">Dans ce code, une virgule suit le mot `Hello` et, étant donné que la virgule n’est pas spécifiée dans le tableau de caractères à supprimer, la suppression s’arrête au niveau de la virgule.</span><span class="sxs-lookup"><span data-stu-id="21c65-127">In this code, a comma follows the word `Hello` and, because the comma is not specified in the array of characters to trim, the trim ends at the comma.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 <span data-ttu-id="21c65-128">Ce code affiche `Hello,` dans la console.</span><span class="sxs-lookup"><span data-stu-id="21c65-128">This code displays `Hello,` to the console.</span></span>  
  
## <a name="trimstart"></a><span data-ttu-id="21c65-129">TrimStart</span><span class="sxs-lookup"><span data-stu-id="21c65-129">TrimStart</span></span>

 <span data-ttu-id="21c65-130">La méthode **String.TrimStart** est similaire à la méthode **String.TrimEnd** , si ce n’est qu’elle crée une chaîne en supprimant les caractères à partir du début d’un objet string existant.</span><span class="sxs-lookup"><span data-stu-id="21c65-130">The **String.TrimStart** method is similar to the **String.TrimEnd** method except that it creates a new string by removing characters from the beginning of an existing string object.</span></span> <span data-ttu-id="21c65-131">Un tableau de caractères est passé à la méthode **TrimStart** pour spécifier les caractères à supprimer.</span><span class="sxs-lookup"><span data-stu-id="21c65-131">An array of characters is passed to the **TrimStart** method to specify the characters to be removed.</span></span> <span data-ttu-id="21c65-132">Comme avec la méthode **TrimEnd** , l’ordre des éléments dans le tableau de caractères n’affecte pas l’opération de suppression.</span><span class="sxs-lookup"><span data-stu-id="21c65-132">As with the **TrimEnd** method, the order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="21c65-133">La suppression s’arrête lorsqu’un caractère non spécifié dans le tableau est trouvé.</span><span class="sxs-lookup"><span data-stu-id="21c65-133">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="21c65-134">L’exemple suivant supprime le premier mot d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="21c65-134">The following example removes the first word of a string.</span></span> <span data-ttu-id="21c65-135">Dans cet exemple, la position du caractère `'l'` et du caractère `'H'` est inversée pour illustrer que l’ordre des caractères dans le tableau n’a pas d’importance.</span><span class="sxs-lookup"><span data-stu-id="21c65-135">In this example, the position of the `'l'` character and the `'H'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 <span data-ttu-id="21c65-136">Ce code affiche `World!` dans la console.</span><span class="sxs-lookup"><span data-stu-id="21c65-136">This code displays `World!` to the console.</span></span>  
  
## <a name="remove"></a><span data-ttu-id="21c65-137">Supprimer</span><span class="sxs-lookup"><span data-stu-id="21c65-137">Remove</span></span>

 <span data-ttu-id="21c65-138">La méthode <xref:System.String.Remove%2A?displayProperty=nameWithType> supprime un nombre spécifié de caractères en commençant à la position spécifiée dans une chaîne existante.</span><span class="sxs-lookup"><span data-stu-id="21c65-138">The <xref:System.String.Remove%2A?displayProperty=nameWithType> method removes a specified number of characters that begin at a specified position in an existing string.</span></span> <span data-ttu-id="21c65-139">Cette méthode suppose un index de base zéro.</span><span class="sxs-lookup"><span data-stu-id="21c65-139">This method assumes a zero-based index.</span></span>  
  
 <span data-ttu-id="21c65-140">L’exemple suivant supprime dix caractères d’une chaîne en commençant à la position cinq d’un index de base zéro de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="21c65-140">The following example removes ten characters from a string beginning at position five of a zero-based index of the string.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
## <a name="replace"></a><span data-ttu-id="21c65-141">Replace</span><span class="sxs-lookup"><span data-stu-id="21c65-141">Replace</span></span>

 <span data-ttu-id="21c65-142">Vous pouvez également supprimer un caractère spécifié ou une sous-chaîne spécifiée d’une chaîne en appelant la méthode <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> et en spécifiant une chaîne vide (<xref:System.String.Empty?displayProperty=nameWithType>) comme valeur de remplacement.</span><span class="sxs-lookup"><span data-stu-id="21c65-142">You can also remove a specified character or substring from a string by calling the <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> method and specifying an empty string (<xref:System.String.Empty?displayProperty=nameWithType>) as the replacement.</span></span> <span data-ttu-id="21c65-143">L’exemple suivant supprime toutes les virgules d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="21c65-143">The following example removes all commas from a string.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="21c65-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21c65-144">See also</span></span>

- [<span data-ttu-id="21c65-145">Opérations de chaînes de base</span><span class="sxs-lookup"><span data-stu-id="21c65-145">Basic String Operations</span></span>](basic-string-operations.md)
