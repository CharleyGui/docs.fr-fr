---
title: System.Math, méthodes
ms.date: 03/30/2017
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
ms.openlocfilehash: e91c8ea95d21288ad2577f1550333febd448766d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158199"
---
# <a name="systemmath-methods"></a>System.Math, méthodes

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ne prend pas en charge les méthodes <xref:System.Math> suivantes.  
  
- <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a>Différences par rapport à .NET  

 Le .NET Framework présente une sémantique d'arrondi différente de SQL Server. La <xref:System.Math.Round%2A> méthode dans la .NET Framework effectue *un arrondi bancaire*, où les nombres se terminent par 0,5 arrondit au chiffre pair le plus proche et non au chiffre supérieur suivant. Par exemple, 2,5 est arrondi à 2 et 3,5 à 4. Cette technique permet d’éviter les écarts systématiques vers des valeurs supérieures dans les transactions de données importantes.  
  
 Dans SQL, la fonction `ROUND` arrondit toujours vers le chiffre supérieur. Ainsi, 2,5 est arrondi à 3 (contre 2 dans le .NET Framework).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] passe par la sémantique `ROUND` de SQL et ne tente pas d'implémenter l'arrondi bancaire.  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions et types de données](data-types-and-functions.md)
