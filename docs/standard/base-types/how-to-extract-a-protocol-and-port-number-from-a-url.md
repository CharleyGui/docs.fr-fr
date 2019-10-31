---
title: "Comment : extraire un protocole et un numéro de port d'une URL"
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
ms.assetid: ab7f62b3-6d2c-4efb-8ac6-28600df5fd5c
ms.openlocfilehash: f2704e3fb5ceb68609a475d52e11030177ad760b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138720"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a><span data-ttu-id="d2899-102">Comment : extraire un protocole et un numéro de port d'une URL</span><span class="sxs-lookup"><span data-stu-id="d2899-102">How to: Extract a Protocol and Port Number from a URL</span></span>
<span data-ttu-id="d2899-103">L’exemple suivant montre comment extraire un protocole et un numéro de port d’une URL.</span><span class="sxs-lookup"><span data-stu-id="d2899-103">The following example extracts a protocol and port number from a URL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2899-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="d2899-104">Example</span></span>  
 <span data-ttu-id="d2899-105">L’exemple utilise la méthode <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> pour retourner le protocole, suivi d’un signe deux-points, lui-même suivi du numéro de port.</span><span class="sxs-lookup"><span data-stu-id="d2899-105">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method to return the protocol followed by a colon followed by the port number.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 <span data-ttu-id="d2899-106">Le modèle d’expression régulière `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` peut être interprété comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="d2899-106">The regular expression pattern `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` can be interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="d2899-107">Motif</span><span class="sxs-lookup"><span data-stu-id="d2899-107">Pattern</span></span>|<span data-ttu-id="d2899-108">Description</span><span class="sxs-lookup"><span data-stu-id="d2899-108">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="d2899-109">Commence la recherche de correspondance au début de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="d2899-109">Begin the match at the start of the string.</span></span>|  
|`(?<proto>\w+)`|<span data-ttu-id="d2899-110">Mettre en correspondance un ou plusieurs caractères alphabétiques.</span><span class="sxs-lookup"><span data-stu-id="d2899-110">Match one or more word characters.</span></span> <span data-ttu-id="d2899-111">Nommer ce groupe `proto`.</span><span class="sxs-lookup"><span data-stu-id="d2899-111">Name this group `proto`.</span></span>|  
|`://`|<span data-ttu-id="d2899-112">Mettre en correspondance un signe deux-points suivi de deux barres obliques.</span><span class="sxs-lookup"><span data-stu-id="d2899-112">Match a colon followed by two slash marks.</span></span>|  
|`[^/]+?`|<span data-ttu-id="d2899-113">Mettre en correspondance une ou plusieurs occurrences (mais le moins possible) de tout caractère autre qu’une barre oblique.</span><span class="sxs-lookup"><span data-stu-id="d2899-113">Match one or more occurrences (but as few as possible) of any character other than a slash mark.</span></span>|  
|`(?<port>:\d+)?`|<span data-ttu-id="d2899-114">Mettre en correspondance zéro ou une occurrence d’un signe deux-points suivi d’un ou de plusieurs caractères de chiffre.</span><span class="sxs-lookup"><span data-stu-id="d2899-114">Match zero or one occurrence of a colon followed by one or more digit characters.</span></span> <span data-ttu-id="d2899-115">Nommer ce groupe `port`.</span><span class="sxs-lookup"><span data-stu-id="d2899-115">Name this group `port`.</span></span>|  
|`/`|<span data-ttu-id="d2899-116">Mettre en correspondance une barre oblique.</span><span class="sxs-lookup"><span data-stu-id="d2899-116">Match a slash mark.</span></span>|  
  
 <span data-ttu-id="d2899-117">La méthode <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> étend la séquence de remplacement `${proto}${port}`, qui concatène la valeur des deux groupes nommés capturés dans le modèle d’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="d2899-117">The <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method expands the `${proto}${port}` replacement sequence, which concatenates the value of the two named groups captured in the regular expression pattern.</span></span> <span data-ttu-id="d2899-118">Elle est plus pratique que la concaténation explicite des chaînes récupérées de l’objet de collection retourné par la propriété <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d2899-118">It is a convenient alternative to explicitly concatenating the strings retrieved from the collection object returned by the <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="d2899-119">L’exemple utilise la méthode <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> avec deux substitutions, `${proto}` et `${port}`, pour inclure les groupes capturés dans la chaîne de sortie.</span><span class="sxs-lookup"><span data-stu-id="d2899-119">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method with two substitutions, `${proto}` and `${port}`, to include the captured groups in the output string.</span></span> <span data-ttu-id="d2899-120">Vous pouvez à la place récupérer les groupes capturés de l’objet <xref:System.Text.RegularExpressions.GroupCollection> de la mise en correspondance, comme le montre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="d2899-120">You can retrieve the captured groups from the match's <xref:System.Text.RegularExpressions.GroupCollection> object instead, as the following code shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d2899-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2899-121">See also</span></span>

- [<span data-ttu-id="d2899-122">Expressions régulières .NET</span><span class="sxs-lookup"><span data-stu-id="d2899-122">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
