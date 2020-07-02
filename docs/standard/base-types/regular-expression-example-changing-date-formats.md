---
title: "Exemple d'expression régulière : modification des formats de date"
ms.date: 06/30/2020
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
ms.openlocfilehash: 3b657ac6c88a1ee846f7f1d2156a18fd34621808
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803948"
---
# <a name="regular-expression-example-changing-date-formats"></a><span data-ttu-id="c3185-102">Exemple d'expression régulière : modification des formats de date</span><span class="sxs-lookup"><span data-stu-id="c3185-102">Regular Expression Example: Changing Date Formats</span></span>
<span data-ttu-id="c3185-103">L’exemple de code suivant utilise la <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> méthode pour remplacer les dates au format *mm* / *JJ* / *AA* par les dates au format *JJ* - *mm* - *AA*.</span><span class="sxs-lookup"><span data-stu-id="c3185-103">The following code example uses the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to replace dates that have the form *mm*/*dd*/*yy* with dates that have the form *dd*-*mm*-*yy*.</span></span>  

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a><span data-ttu-id="c3185-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="c3185-104">Example</span></span>  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 <span data-ttu-id="c3185-105">Le code suivant montre comment la méthode `MDYToDMY` peut être appelée dans une application.</span><span class="sxs-lookup"><span data-stu-id="c3185-105">The following code shows how the `MDYToDMY` method can be called in an application.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a><span data-ttu-id="c3185-106">Commentaires</span><span class="sxs-lookup"><span data-stu-id="c3185-106">Comments</span></span>  
 <span data-ttu-id="c3185-107">Le modèle d'expression régulière `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` est interprété comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="c3185-107">The regular expression pattern  `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="c3185-108">Modèle</span><span class="sxs-lookup"><span data-stu-id="c3185-108">Pattern</span></span>|<span data-ttu-id="c3185-109">Description</span><span class="sxs-lookup"><span data-stu-id="c3185-109">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="c3185-110">Commencer la correspondance à la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="c3185-110">Begin the match at a word boundary.</span></span>|  
|`(?<month>\d{1,2})`|<span data-ttu-id="c3185-111">Mettre en correspondance un ou deux chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="c3185-111">Match one or two decimal digits.</span></span> <span data-ttu-id="c3185-112">Il s’agit du groupe capturé `month`.</span><span class="sxs-lookup"><span data-stu-id="c3185-112">This is the `month` captured group.</span></span>|  
|`/`|<span data-ttu-id="c3185-113">Mettre en correspondance la barre oblique.</span><span class="sxs-lookup"><span data-stu-id="c3185-113">Match the slash mark.</span></span>|  
|`(?<day>\d{1,2})`|<span data-ttu-id="c3185-114">Mettre en correspondance un ou deux chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="c3185-114">Match one or two decimal digits.</span></span> <span data-ttu-id="c3185-115">Il s’agit du groupe capturé `day`.</span><span class="sxs-lookup"><span data-stu-id="c3185-115">This is the `day` captured group.</span></span>|  
|`/`|<span data-ttu-id="c3185-116">Mettre en correspondance la barre oblique.</span><span class="sxs-lookup"><span data-stu-id="c3185-116">Match the slash mark.</span></span>|  
|`(?<year>\d{2,4})`|<span data-ttu-id="c3185-117">Mettre en correspondance de deux à quatre chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="c3185-117">Match from two to four decimal digits.</span></span> <span data-ttu-id="c3185-118">Il s’agit du groupe capturé `year`.</span><span class="sxs-lookup"><span data-stu-id="c3185-118">This is the `year` captured group.</span></span>|  
|`\b`|<span data-ttu-id="c3185-119">Terminer la correspondance à la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="c3185-119">End the match at a word boundary.</span></span>|  
  
 <span data-ttu-id="c3185-120">Le modèle `${day}-${month}-${year}` définit la chaîne de remplacement comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="c3185-120">The pattern `${day}-${month}-${year}` defines the replacement string as shown in the following table.</span></span>  
  
|<span data-ttu-id="c3185-121">Modèle</span><span class="sxs-lookup"><span data-stu-id="c3185-121">Pattern</span></span>|<span data-ttu-id="c3185-122">Description</span><span class="sxs-lookup"><span data-stu-id="c3185-122">Description</span></span>|  
|-------------|-----------------|  
|`$(day)`|<span data-ttu-id="c3185-123">Ajouter la chaîne capturée par le groupe de capture `day`.</span><span class="sxs-lookup"><span data-stu-id="c3185-123">Add the string captured by the `day` capturing group.</span></span>|  
|`-`|<span data-ttu-id="c3185-124">Ajouter un trait d’union.</span><span class="sxs-lookup"><span data-stu-id="c3185-124">Add a hyphen.</span></span>|  
|`$(month)`|<span data-ttu-id="c3185-125">Ajouter la chaîne capturée par le groupe de capture `month`.</span><span class="sxs-lookup"><span data-stu-id="c3185-125">Add the string captured by the `month` capturing group.</span></span>|  
|`-`|<span data-ttu-id="c3185-126">Ajouter un trait d’union.</span><span class="sxs-lookup"><span data-stu-id="c3185-126">Add a hyphen.</span></span>|  
|`$(year)`|<span data-ttu-id="c3185-127">Ajouter la chaîne capturée par le groupe de capture `year`.</span><span class="sxs-lookup"><span data-stu-id="c3185-127">Add the string captured by the `year` capturing group.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c3185-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3185-128">See also</span></span>

- [<span data-ttu-id="c3185-129">Expressions régulières .NET</span><span class="sxs-lookup"><span data-stu-id="c3185-129">.NET Regular Expressions</span></span>](regular-expressions.md)
