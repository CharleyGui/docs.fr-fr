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
# <a name="regular-expression-example-changing-date-formats"></a>Exemple d'expression régulière : modification des formats de date
L’exemple de <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> code suivant utilise la méthode pour remplacer les dates qui ont le formulaire *mm*/*dd*/*yy* avec des dates qui ont le formulaire *dd*-*mm*-*yy*.  
  
## <a name="example"></a> Exemple  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 Le code suivant montre comment la méthode `MDYToDMY` peut être appelée dans une application.  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a>Commentaires  
 Le modèle d'expression régulière `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` est interprété comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer la correspondance à la limite d'un mot.|  
|`(?<month>\d{1,2})`|Mettre en correspondance un ou deux chiffres décimaux. Il s’agit du groupe capturé `month`.|  
|`/`|Mettre en correspondance la barre oblique.|  
|`(?<day>\d{1,2})`|Mettre en correspondance un ou deux chiffres décimaux. Il s’agit du groupe capturé `day`.|  
|`/`|Mettre en correspondance la barre oblique.|  
|`(?<year>\d{2,4})`|Mettre en correspondance de deux à quatre chiffres décimaux. Il s’agit du groupe capturé `year`.|  
|`\b`|Terminer la correspondance à la limite d'un mot.|  
  
 Le modèle `${day}-${month}-${year}` définit la chaîne de remplacement comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`$(day)`|Ajouter la chaîne capturée par le groupe de capture `day`.|  
|`-`|Ajouter un trait d’union.|  
|`$(month)`|Ajouter la chaîne capturée par le groupe de capture `month`.|  
|`-`|Ajouter un trait d’union.|  
|`$(year)`|Ajouter la chaîne capturée par le groupe de capture `year`.|  
  
## <a name="see-also"></a>Voir aussi

- [Expressions régulières .NET](../../../docs/standard/base-types/regular-expressions.md)
