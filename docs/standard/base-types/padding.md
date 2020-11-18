---
title: Remplissage de chaînes dans .NET
description: Découvrez comment remplir des chaînes dans .NET. Utilisez les méthodes String. PadLeft et String. PadRight pour ajouter des caractères de début ou de fin pour atteindre une longueur totale spécifiée.
ms.date: 03/15/2018
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strings [.NET], padding
- white space
- PadRight method
- PadLeft method
- padding strings
ms.assetid: 84a9f142-3244-4c90-ba02-21af9bbaff71
ms.openlocfilehash: 9931db1e76e3737ab3803400928169b30c3ecbda
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94822943"
---
# <a name="padding-strings-in-net"></a>Remplissage de chaînes dans .NET

Utilisez l’une des méthodes <xref:System.String> suivantes pour créer une chaîne qui se compose d’une chaîne d’origine remplie à l’aide de caractères de début ou de fin sur une longueur totale spécifiée. Le caractère de remplissage peut être un espace ou un caractère spécifié. La chaîne résultante apparaît alignée à droite ou à gauche. Si la longueur de la chaîne d’origine est déjà égale ou supérieure à la longueur totale souhaitée, les méthodes de remplissage retournent la chaîne d’origine inchangée. Pour plus d’informations, consultez les sections **Retours** des deux surcharges des méthodes <xref:System.String.PadLeft%2A?displayProperty=nameWithType> et <xref:System.String.PadRight%2A?displayProperty=nameWithType>.
  
|Nom de la méthode|Utilisation|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|Remplit une chaîne à l’aide de caractères de début sur une longueur totale spécifiée.|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|Remplit une chaîne à l’aide de caractères de fin sur une longueur totale spécifiée.|  
  
## <a name="padleft"></a>PadLeft  
 La méthode <xref:System.String.PadLeft%2A?displayProperty=nameWithType> crée une chaîne en concaténant suffisamment de caractères de remplissage de début à une chaîne d’origine pour atteindre une longueur totale spécifiée. La méthode <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> utilise l’espace blanc comme caractère de remplissage et la méthode <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> vous permet de spécifier votre propre caractère de remplissage.  
  
 L’exemple de code suivant utilise la méthode <xref:System.String.PadLeft%2A> pour créer une chaîne longue de vingt caractères. L’exemple affiche « `--------Hello World!` » sur la console.  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a>PadRight  
 La méthode <xref:System.String.PadRight%2A?displayProperty=nameWithType> crée une chaîne en concaténant suffisamment de caractères de remplissage de fin à une chaîne d’origine pour atteindre une longueur totale spécifiée. La méthode <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> utilise l’espace blanc comme caractère de remplissage et la méthode <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> vous permet de spécifier votre propre caractère de remplissage.  
  
 L’exemple de code suivant utilise la méthode <xref:System.String.PadRight%2A> pour créer une chaîne longue de vingt caractères. L’exemple affiche « `Hello World!--------` » sur la console.  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a>Voir aussi

- [Opérations de chaînes de base](basic-string-operations.md)
