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
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a>Procédure : extraire un protocole et un numéro de port d’une URL
L’exemple suivant montre comment extraire un protocole et un numéro de port d’une URL.  

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a>Exemple  
 L’exemple utilise la méthode <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> pour retourner le protocole, suivi d’un signe deux-points, lui-même suivi du numéro de port.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 Le modèle d’expression régulière `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` peut être interprété comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`^`|Commence la recherche de correspondance au début de la chaîne.|  
|`(?<proto>\w+)`|Mettre en correspondance un ou plusieurs caractères alphabétiques. Nommer ce groupe `proto`.|  
|`://`|Mettre en correspondance un signe deux-points suivi de deux barres obliques.|  
|`[^/]+?`|Mettre en correspondance une ou plusieurs occurrences (mais le moins possible) de tout caractère autre qu’une barre oblique.|  
|`(?<port>:\d+)?`|Mettre en correspondance zéro ou une occurrence d’un signe deux-points suivi d’un ou de plusieurs caractères de chiffre. Nommer ce groupe `port`.|  
|`/`|Mettre en correspondance une barre oblique.|  
  
 La méthode <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> étend la séquence de remplacement `${proto}${port}`, qui concatène la valeur des deux groupes nommés capturés dans le modèle d’expression régulière. Elle est plus pratique que la concaténation explicite des chaînes récupérées de l’objet de collection retourné par la propriété <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType>.  
  
 L’exemple utilise la méthode <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> avec deux substitutions, `${proto}` et `${port}`, pour inclure les groupes capturés dans la chaîne de sortie. Vous pouvez à la place récupérer les groupes capturés de l’objet <xref:System.Text.RegularExpressions.GroupCollection> de la mise en correspondance, comme le montre le code suivant.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- [Expressions régulières .NET](regular-expressions.md)
