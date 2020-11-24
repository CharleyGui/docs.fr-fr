---
title: 'Procédure : afficher les millisecondes dans les valeurs de date et d’heure'
description: Dans cet article, vous allez apprendre à inclure un composant « milliseconde » d’une date et d’une heure dans des chaînes de date et d’heure mises en forme dans .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTime.ToString method
- displaying date and time data
- time [.NET], milliseconds
- dates [.NET], milliseconds
- milliseconds [.NET]
ms.assetid: ae1a0610-90b9-4877-8eb6-4e30bc5e00cf
ms.openlocfilehash: 722334c324f663ba46a3c861885d4221fc566b8d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681260"
---
# <a name="how-to-display-milliseconds-in-date-and-time-values"></a>Procédure : afficher les millisecondes dans les valeurs de date et d’heure

Les méthodes de mise en forme de date et d’heure par défaut, telles que <xref:System.DateTime.ToString?displayProperty=nameWithType>, incluent les heures, les minutes et les secondes d’une valeur d’heure, mais excluent son composant « millisecondes ». Cette rubrique montre comment inclure le composant « millisecondes » d’une date et d’une heure dans des chaînes de date et d’heure mises en forme.  
  
### <a name="to-display-the-millisecond-component-of-a-datetime-value"></a>Pour afficher le composant « millisecondes » d’une valeur DateTime  
  
1. Si la date est représentée sous forme de chaîne, convertissez-la en une valeur <xref:System.DateTime> ou <xref:System.DateTimeOffset> en utilisant la méthode <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> ou <xref:System.DateTimeOffset.Parse%28System.String%29?displayProperty=nameWithType> statique.  
  
2. Pour extraire la représentation sous forme de chaîne du composant « millisecondes » d’une heure, appelez la méthode <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> ou <xref:System.DateTimeOffset.ToString%2A> de la valeur de date et d’heure, puis transmettez le modèle de format personnalisé `fff` ou `FFF` seul ou avec d’autres spécificateurs de format personnalisé comme paramètre de `format`.  
  
## <a name="example"></a>Exemple  

 L’exemple affiche le composant « milliseconde » d’une valeur <xref:System.DateTime> et d’une valeur <xref:System.DateTimeOffset> sur la console, à la fois seul et inclus dans une chaîne de date et d’heure plus longue.  
  
 [!code-csharp[Formatting.HowTo.Millisecond#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#1)]
 [!code-vb[Formatting.HowTo.Millisecond#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#1)]  
  
 Le modèle de format `fff` inclut les zéros de fin éventuels dans la valeur en millisecondes. Le modèle de format `FFF` les supprime. L’exemple suivant illustre cette différence.  
  
 [!code-csharp[Formatting.HowTo.Millisecond#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#2)]
 [!code-vb[Formatting.HowTo.Millisecond#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#2)]  
  
 Quand vous définissez un spécificateur de format personnalisé complet qui inclut le composant « millisecondes » d’une date et d’une heure, vous pouvez être confronté au problème suivant : le format défini peut être un format codé en dur qui ne correspond pas à la disposition des éléments d’heure dans la culture actuelle de l’application. Une meilleure solution consiste à récupérer l’un des modèles d’affichage de la date et de l’heure définis par l’objet <xref:System.Globalization.DateTimeFormatInfo> de la culture actuelle et à le modifier pour inclure les millisecondes. L’exemple illustre également cette approche. Il récupère de la propriété <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> le modèle de date et d’heure complet de la culture actuelle, puis insère le modèle personnalisé `.ffff` après son modèle des secondes. Notez que l’exemple utilise une expression régulière pour effectuer cette opération dans un seul appel de méthode.  
  
 Vous pouvez également utiliser un spécificateur de format personnalisé pour afficher une partie fractionnaire des secondes autre que les millisecondes. Par exemple, le spécificateur de format personnalisé `f` ou `F` affiche les dixièmes de seconde, le spécificateur de format personnalisé `ff` ou `FF` affiche les centièmes de seconde, tandis que le spécificateur de format personnalisé `ffff` ou `FFFF` affiche les dix millièmes de seconde. La partie fractionnaire d’une milliseconde est tronquée au lieu d’être arrondie dans la chaîne retournée. Ces spécificateurs de format sont utilisés dans l’exemple suivant.  
  
 [!code-csharp[Formatting.HowTo.Millisecond#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#3)]
 [!code-vb[Formatting.HowTo.Millisecond#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#3)]  
  
> [!NOTE]
> Il est possible d’afficher de très petites unités fractionnaires d’une seconde, telles que les dix millièmes de seconde ou les cent millièmes de seconde. Toutefois, ces valeurs peuvent ne pas être significatives. La précision des valeurs de date et d'heure dépend de la résolution de l'horloge système. Sur Windows NT 3,5 et versions ultérieures, ainsi que sur les systèmes d’exploitation Windows Vista, la résolution de l’horloge est d’environ 10-15 millisecondes.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Globalization.DateTimeFormatInfo>
- [Chaînes de format de date et d'heure personnalisées](custom-date-and-time-format-strings.md)
