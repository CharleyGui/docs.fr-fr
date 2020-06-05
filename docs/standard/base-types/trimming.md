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
- strings [.NET Framework], removing characters
- Remove method
- TrimEnd method
- Trim method
- trimming characters
- TrimStart method
- removing characters
ms.assetid: ab248dab-70d4-4413-81c6-542d153fd195
ms.openlocfilehash: 630fe6b51d151d1f1384f2e3cde62750c303d883
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446891"
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a>Suppression d’espaces et de caractères dans .NET
Si vous analysez une phrase en mots individuels, vous risquez d’obtenir des mots incluant des espaces vides (également appelés espaces blancs) à chaque extrémité du mot. Dans ce cas, vous pouvez utiliser l’une des méthodes de suppression de la classe **System.String** pour supprimer n’importe quel nombre d’espaces ou d’autres caractères à partir d’une position spécifiée dans la chaîne. Le tableau suivant décrit les méthodes de suppression disponibles.  
  
|Nom de la méthode|Utilisation|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|Supprime les espaces blancs ou caractères spécifiés dans un tableau de caractères à partir du début et la fin d’une chaîne.|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|Supprime les caractères spécifiés dans un tableau de caractères à partir de la fin d’une chaîne.|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|Supprime les caractères spécifiés dans un tableau de caractères à partir du début d’une chaîne.|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|Supprime un nombre spécifié de caractères à partir de la position d’index spécifiée dans une chaîne.|  
  
## <a name="trim"></a>SupprEspace

 Vous pouvez facilement supprimer les espaces blancs situés aux deux extrémités d’une chaîne à l’aide de la méthode <xref:System.String.Trim%2A?displayProperty=nameWithType>, comme indiqué dans l’exemple suivant.  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 Vous pouvez également supprimer les caractères que vous spécifiez dans un tableau de caractères à partir du début et de la fin d’une chaîne. L’exemple suivant permet de supprimer les espaces blancs, les points et les astérisques.  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a>TrimEnd

 La méthode **String.TrimEnd** supprime les caractères à partir de la fin d’une chaîne, créant ainsi un objet String. Un tableau de caractères est passé à cette méthode pour spécifier les caractères à supprimer. L’ordre des éléments dans le tableau de caractères n’affecte pas l’opération de suppression. La suppression s’arrête lorsqu’un caractère non spécifié dans le tableau est trouvé.  
  
 L’exemple suivant supprime les dernières lettres d’une chaîne à l’aide de la méthode **TrimEnd** . Dans cet exemple, la position du caractère `'r'` et du caractère `'W'` est inversée pour illustrer que l’ordre des caractères dans le tableau n’a pas d’importance. Remarquez que ce code supprime le dernier mot de `MyString` plus une partie du premier.  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 Ce code affiche `He` dans la console.  
  
 L’exemple suivant supprime le dernier mot d’une chaîne à l’aide de la méthode **TrimEnd**. Dans ce code, une virgule suit le mot `Hello` et, étant donné que la virgule n’est pas spécifiée dans le tableau de caractères à supprimer, la suppression s’arrête au niveau de la virgule.  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 Ce code affiche `Hello,` dans la console.  
  
## <a name="trimstart"></a>TrimStart

 La méthode **String.TrimStart** est similaire à la méthode **String.TrimEnd**, si ce n’est qu’elle crée une chaîne en supprimant les caractères à partir du début d’un objet string existant. Un tableau de caractères est passé à la méthode **TrimStart** pour spécifier les caractères à supprimer. Comme avec la méthode **TrimEnd**, l’ordre des éléments dans le tableau de caractères n’affecte pas l’opération de suppression. La suppression s’arrête lorsqu’un caractère non spécifié dans le tableau est trouvé.  
  
 L’exemple suivant supprime le premier mot d’une chaîne. Dans cet exemple, la position du caractère `'l'` et du caractère `'H'` est inversée pour illustrer que l’ordre des caractères dans le tableau n’a pas d’importance.  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 Ce code affiche `World!` dans la console.  
  
## <a name="remove"></a>Supprimer

 La méthode <xref:System.String.Remove%2A?displayProperty=nameWithType> supprime un nombre spécifié de caractères en commençant à la position spécifiée dans une chaîne existante. Cette méthode suppose un index de base zéro.  
  
 L’exemple suivant supprime dix caractères d’une chaîne en commençant à la position cinq d’un index de base zéro de la chaîne.  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
## <a name="replace"></a>Replace

 Vous pouvez également supprimer un caractère spécifié ou une sous-chaîne spécifiée d’une chaîne en appelant la méthode <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> et en spécifiant une chaîne vide (<xref:System.String.Empty?displayProperty=nameWithType>) comme valeur de remplacement. L’exemple suivant supprime toutes les virgules d’une chaîne.  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a>Voir aussi

- [Opérations de chaînes de base](basic-string-operations.md)
