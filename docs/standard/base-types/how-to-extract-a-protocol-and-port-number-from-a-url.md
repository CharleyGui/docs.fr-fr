---
title: 'Procédure : extraire un protocole et un numéro de port d’une URL'
ms.date: 06/30/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET regular expressions, examples
- regular expressions [.NET], examples
- pattern-matching with regular expressions, examples
ms.assetid: ab7f62b3-6d2c-4efb-8ac6-28600df5fd5c
ms.openlocfilehash: 9c0ab3cc0d3bcbee1a28d53215a17840be216172
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888545"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a><span data-ttu-id="68533-102">Procédure : extraire un protocole et un numéro de port d’une URL</span><span class="sxs-lookup"><span data-stu-id="68533-102">How to: Extract a Protocol and Port Number from a URL</span></span>
<span data-ttu-id="68533-103">L’exemple suivant montre comment extraire un protocole et un numéro de port d’une URL.</span><span class="sxs-lookup"><span data-stu-id="68533-103">The following example extracts a protocol and port number from a URL.</span></span>  

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a><span data-ttu-id="68533-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="68533-104">Example</span></span>  
 <span data-ttu-id="68533-105">L’exemple utilise la méthode <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> pour retourner le protocole, suivi d’un signe deux-points, lui-même suivi du numéro de port.</span><span class="sxs-lookup"><span data-stu-id="68533-105">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method to return the protocol followed by a colon followed by the port number.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 <span data-ttu-id="68533-106">Le modèle d’expression régulière `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` peut être interprété comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="68533-106">The regular expression pattern `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` can be interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="68533-107">Modèle</span><span class="sxs-lookup"><span data-stu-id="68533-107">Pattern</span></span>|<span data-ttu-id="68533-108">Description</span><span class="sxs-lookup"><span data-stu-id="68533-108">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="68533-109">Commence la recherche de correspondance au début de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="68533-109">Begin the match at the start of the string.</span></span>|  
|`(?<proto>\w+)`|<span data-ttu-id="68533-110">Mettre en correspondance un ou plusieurs caractères alphabétiques.</span><span class="sxs-lookup"><span data-stu-id="68533-110">Match one or more word characters.</span></span> <span data-ttu-id="68533-111">Nommer ce groupe `proto`.</span><span class="sxs-lookup"><span data-stu-id="68533-111">Name this group `proto`.</span></span>|  
|`://`|<span data-ttu-id="68533-112">Mettre en correspondance un signe deux-points suivi de deux barres obliques.</span><span class="sxs-lookup"><span data-stu-id="68533-112">Match a colon followed by two slash marks.</span></span>|  
|`[^/]+?`|<span data-ttu-id="68533-113">Mettre en correspondance une ou plusieurs occurrences (mais le moins possible) de tout caractère autre qu’une barre oblique.</span><span class="sxs-lookup"><span data-stu-id="68533-113">Match one or more occurrences (but as few as possible) of any character other than a slash mark.</span></span>|  
|`(?<port>:\d+)?`|<span data-ttu-id="68533-114">Mettre en correspondance zéro ou une occurrence d’un signe deux-points suivi d’un ou de plusieurs caractères de chiffre.</span><span class="sxs-lookup"><span data-stu-id="68533-114">Match zero or one occurrence of a colon followed by one or more digit characters.</span></span> <span data-ttu-id="68533-115">Nommer ce groupe `port`.</span><span class="sxs-lookup"><span data-stu-id="68533-115">Name this group `port`.</span></span>|  
|`/`|<span data-ttu-id="68533-116">Mettre en correspondance une barre oblique.</span><span class="sxs-lookup"><span data-stu-id="68533-116">Match a slash mark.</span></span>|  
  
 <span data-ttu-id="68533-117">La méthode <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> étend la séquence de remplacement `${proto}${port}`, qui concatène la valeur des deux groupes nommés capturés dans le modèle d’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="68533-117">The <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method expands the `${proto}${port}` replacement sequence, which concatenates the value of the two named groups captured in the regular expression pattern.</span></span> <span data-ttu-id="68533-118">Elle est plus pratique que la concaténation explicite des chaînes récupérées de l’objet de collection retourné par la propriété <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="68533-118">It is a convenient alternative to explicitly concatenating the strings retrieved from the collection object returned by the <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="68533-119">L’exemple utilise la méthode <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> avec deux substitutions, `${proto}` et `${port}`, pour inclure les groupes capturés dans la chaîne de sortie.</span><span class="sxs-lookup"><span data-stu-id="68533-119">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method with two substitutions, `${proto}` and `${port}`, to include the captured groups in the output string.</span></span> <span data-ttu-id="68533-120">Vous pouvez à la place récupérer les groupes capturés de l’objet <xref:System.Text.RegularExpressions.GroupCollection> de la mise en correspondance, comme le montre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="68533-120">You can retrieve the captured groups from the match's <xref:System.Text.RegularExpressions.GroupCollection> object instead, as the following code shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="68533-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68533-121">See also</span></span>

- [<span data-ttu-id="68533-122">Expressions régulières .NET</span><span class="sxs-lookup"><span data-stu-id="68533-122">.NET Regular Expressions</span></span>](regular-expressions.md)
