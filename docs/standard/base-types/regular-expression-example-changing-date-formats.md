---
title: "Exemple d'expression régulière : modification des formats de date"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: 5fcc75a5-09d7-45ae-a4c0-9ad6085ac83d
ms.openlocfilehash: 358e26957747073fec9dfe9eb0d404cb438afaf9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73084183"
---
# <a name="regular-expression-example-changing-date-formats"></a><span data-ttu-id="3a569-102">Exemple d'expression régulière : modification des formats de date</span><span class="sxs-lookup"><span data-stu-id="3a569-102">Regular Expression Example: Changing Date Formats</span></span>
<span data-ttu-id="3a569-103">L’exemple de <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> code suivant utilise la méthode pour remplacer les dates qui ont le formulaire *mm*/*dd*/*yy* avec des dates qui ont le formulaire *dd*-*mm*-*yy*.</span><span class="sxs-lookup"><span data-stu-id="3a569-103">The following code example uses the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to replace dates that have the form *mm*/*dd*/*yy* with dates that have the form *dd*-*mm*-*yy*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a569-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="3a569-104">Example</span></span>  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 <span data-ttu-id="3a569-105">Le code suivant montre comment la méthode `MDYToDMY` peut être appelée dans une application.</span><span class="sxs-lookup"><span data-stu-id="3a569-105">The following code shows how the `MDYToDMY` method can be called in an application.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a><span data-ttu-id="3a569-106">Commentaires</span><span class="sxs-lookup"><span data-stu-id="3a569-106">Comments</span></span>  
 <span data-ttu-id="3a569-107">Le modèle d'expression régulière `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` est interprété comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="3a569-107">The regular expression pattern  `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="3a569-108">Modèle</span><span class="sxs-lookup"><span data-stu-id="3a569-108">Pattern</span></span>|<span data-ttu-id="3a569-109">Description</span><span class="sxs-lookup"><span data-stu-id="3a569-109">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="3a569-110">Commencer la correspondance à la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="3a569-110">Begin the match at a word boundary.</span></span>|  
|`(?<month>\d{1,2})`|<span data-ttu-id="3a569-111">Mettre en correspondance un ou deux chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="3a569-111">Match one or two decimal digits.</span></span> <span data-ttu-id="3a569-112">Il s’agit du groupe capturé `month`.</span><span class="sxs-lookup"><span data-stu-id="3a569-112">This is the `month` captured group.</span></span>|  
|`/`|<span data-ttu-id="3a569-113">Mettre en correspondance la barre oblique.</span><span class="sxs-lookup"><span data-stu-id="3a569-113">Match the slash mark.</span></span>|  
|`(?<day>\d{1,2})`|<span data-ttu-id="3a569-114">Mettre en correspondance un ou deux chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="3a569-114">Match one or two decimal digits.</span></span> <span data-ttu-id="3a569-115">Il s’agit du groupe capturé `day`.</span><span class="sxs-lookup"><span data-stu-id="3a569-115">This is the `day` captured group.</span></span>|  
|`/`|<span data-ttu-id="3a569-116">Mettre en correspondance la barre oblique.</span><span class="sxs-lookup"><span data-stu-id="3a569-116">Match the slash mark.</span></span>|  
|`(?<year>\d{2,4})`|<span data-ttu-id="3a569-117">Mettre en correspondance de deux à quatre chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="3a569-117">Match from two to four decimal digits.</span></span> <span data-ttu-id="3a569-118">Il s’agit du groupe capturé `year`.</span><span class="sxs-lookup"><span data-stu-id="3a569-118">This is the `year` captured group.</span></span>|  
|`\b`|<span data-ttu-id="3a569-119">Terminer la correspondance à la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="3a569-119">End the match at a word boundary.</span></span>|  
  
 <span data-ttu-id="3a569-120">Le modèle `${day}-${month}-${year}` définit la chaîne de remplacement comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="3a569-120">The pattern `${day}-${month}-${year}` defines the replacement string as shown in the following table.</span></span>  
  
|<span data-ttu-id="3a569-121">Modèle</span><span class="sxs-lookup"><span data-stu-id="3a569-121">Pattern</span></span>|<span data-ttu-id="3a569-122">Description</span><span class="sxs-lookup"><span data-stu-id="3a569-122">Description</span></span>|  
|-------------|-----------------|  
|`$(day)`|<span data-ttu-id="3a569-123">Ajouter la chaîne capturée par le groupe de capture `day`.</span><span class="sxs-lookup"><span data-stu-id="3a569-123">Add the string captured by the `day` capturing group.</span></span>|  
|`-`|<span data-ttu-id="3a569-124">Ajouter un trait d’union.</span><span class="sxs-lookup"><span data-stu-id="3a569-124">Add a hyphen.</span></span>|  
|`$(month)`|<span data-ttu-id="3a569-125">Ajouter la chaîne capturée par le groupe de capture `month`.</span><span class="sxs-lookup"><span data-stu-id="3a569-125">Add the string captured by the `month` capturing group.</span></span>|  
|`-`|<span data-ttu-id="3a569-126">Ajouter un trait d’union.</span><span class="sxs-lookup"><span data-stu-id="3a569-126">Add a hyphen.</span></span>|  
|`$(year)`|<span data-ttu-id="3a569-127">Ajouter la chaîne capturée par le groupe de capture `year`.</span><span class="sxs-lookup"><span data-stu-id="3a569-127">Add the string captured by the `year` capturing group.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3a569-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a569-128">See also</span></span>

- [<span data-ttu-id="3a569-129">Expressions régulières .NET</span><span class="sxs-lookup"><span data-stu-id="3a569-129">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
