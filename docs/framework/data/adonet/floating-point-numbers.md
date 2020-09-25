---
title: Nombres à virgule flottante
ms.date: 03/30/2017
ms.assetid: 73c218c6-1c44-4402-a167-4f6262629a91
ms.openlocfilehash: 754338ce842fdfccb8c3874e63a75a3aa2fe3eb3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169555"
---
# <a name="floating-point-numbers"></a>Nombres à virgule flottante

Cette rubrique décrit certains des problèmes que les développeurs rencontrent fréquemment lorsqu’ils travaillent avec des nombres à virgule flottante dans ADO.NET. Ces problèmes sont dus à la façon dont les ordinateurs stockent les nombres à virgule flottante et ne sont pas spécifiques à un fournisseur particulier tel que <xref:System.Data.SqlClient> ou <xref:System.Data.OracleClient> .  
  
 Généralement, les nombres à virgule flottante n'ont pas de représentation binaire exacte. L'ordinateur stocke à la place une approximation du nombre. À différents moments, différents nombres en chiffres binaires peuvent être utilisés pour représenter le même nombre. Lorsqu'un nombre à virgule flottante est converti d'une représentation à une autre, ses chiffres les moins significatifs peuvent varier légèrement. Généralement, une conversion se produit lorsqu'un nombre est casté d'un type à un autre. La variation survient que la conversion ait lieu dans une base de données, entre des types représentant des valeurs de base de données ou entre des types. En raison de ces modifications, des nombres qui devraient logiquement être égaux peuvent présenter des disparités au niveau de leurs chiffres les moins significatifs et par conséquent avoir des valeurs différentes. Le nombre de chiffres de précision peut être plus grand ou plus petit que prévu pour un nombre. Lorsqu'il est sous forme de chaîne, le nombre risque de ne pas présenter la valeur prévue.  
  
 Pour minimiser ces effets, vous devez choisir parmi les différents types numériques disponibles celui qui se rapproche le plus de la valeur d'origine. Par exemple, si vous utilisez SQL Server, la valeur numérique exacte peut changer si vous convertissez une valeur Transact-SQL de type réel en valeur de type float. Dans le .NET Framework, la conversion <xref:System.Single> d’un en un <xref:System.Double> peut également produire des résultats inattendus. Dans ces deux cas, une stratégie efficace consiste à appliquer le même type numérique à toutes les valeurs de l'application. Vous pouvez également recourir à un type décimal à précision fixe, ou convertir des nombres à virgule flottante en type décimal à précision fixe avant de les utiliser.  
  
 Pour contourner les problèmes de comparaison d'égalité, vous pouvez coder l'application de manière à ce que les variations des chiffres les moins significatifs soient ignorées. Par exemple, au lieu de comparer deux nombres pour vérifier s'ils sont égaux, vous pouvez les soustraire. Si la différence est comprise dans une fourchette d'arrondi acceptable, l'application peut traiter ces nombres comme s'ils étaient identiques.  
  
## <a name="see-also"></a>Voir aussi

- [Pourquoi les nombres à virgule flottante peuvent perdre la précision](/cpp/build/why-floating-point-numbers-may-lose-precision)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
