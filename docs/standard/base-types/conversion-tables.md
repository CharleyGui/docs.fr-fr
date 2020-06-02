---
title: Table de conversion de type dans .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- widening conversions
- narrowing conversions
- type conversion, table
- converting types, narrowing conversions
- converting types, widening conversions
- base types, converting
- tables [.NET Framework], type conversions
- data types [.NET Framework], converting
ms.assetid: 0ea65c59-85eb-4a52-94ca-c36d3bd13058
ms.openlocfilehash: bb696c65078a5dae0b81a48bffc786d2257496c3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290563"
---
# <a name="type-conversion-tables-in-net"></a>Table de conversion de type dans .NET
Une conversion étendue se produit quand une valeur d’un type est convertie en un autre type de taille égale ou supérieure. Une conversion restrictive se produit quand une valeur d’un type est convertie en une valeur d’un autre type de taille inférieure. Les tableaux de cette rubrique illustrent les comportements propres aux deux types de conversion.  
  
## <a name="widening-conversions"></a>conversions étendues  
 Le tableau suivant décrit les conversions étendues qui peuvent être effectuées sans perte d’informations.  
  
|Type|Peut être converti sans perte de données en|  
|----------|-------------------------------------------|  
|<xref:System.Byte>|<xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.SByte>|<xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int16>|<xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.UInt16>|<xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Char>|<xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int32>|<xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.UInt32>|<xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int64>|<xref:System.Decimal>|  
|<xref:System.UInt64>|<xref:System.Decimal>|  
|<xref:System.Single>|<xref:System.Double>|  
  
 Certaines conversions étendues à <xref:System.Single> ou <xref:System.Double> peuvent entraîner une perte de précision. Le tableau suivant décrit les conversions étendues qui entraînent parfois une perte d’informations.  
  
|Type|Peut être converti en|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.UInt64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.Decimal>|<xref:System.Single>, <xref:System.Double>|  
  
## <a name="narrowing-conversions"></a>conversions restrictives  
 Une conversion restrictive en <xref:System.Single> ou <xref:System.Double> peut entraîner une perte d’informations. Si le type cible ne peut pas exprimer correctement la grandeur de la source, le type résultant est défini sur la constante `PositiveInfinity` ou `NegativeInfinity`. `PositiveInfinity` est obtenu en divisant un nombre positif par zéro et est également retourné quand la valeur d’un <xref:System.Single> ou d’un <xref:System.Double> dépasse la valeur du champ `MaxValue`. `NegativeInfinity` est obtenu en divisant un nombre négatif par zéro et est également retourné quand la valeur d’un <xref:System.Single> ou d’un <xref:System.Double> descend en dessous de la valeur du champ `MinValue`. Une conversion d’un <xref:System.Double> en <xref:System.Single> peut avoir pour résultat `PositiveInfinity` ou `NegativeInfinity`.  
  
 Une conversion restrictive peut également entraîner une perte d’informations pour d’autres types de données. Toutefois, une <xref:System.OverflowException>est levée si la valeur d’un type en cours de conversion se situe en dehors de la plage spécifiée par les champs `MaxValue` et `MinValue` du type cible, et la conversion est vérifiée par le runtime pour garantir que la valeur du type cible ne dépasse pas sa valeur `MaxValue` ou `MinValue`. Les conversions effectuées avec la classe <xref:System.Convert?displayProperty=nameWithType> sont toujours vérifiées de cette façon.  
  
 Le tableau suivant répertorie les conversions qui lèvent une <xref:System.OverflowException> à l’aide de <xref:System.Convert?displayProperty=nameWithType> ou de toute conversion contrôlée si la valeur du type converti se situe en dehors de la plage définie du type résultant.  
  
|Type|Peut être converti en|  
|----------|-------------------------|  
|<xref:System.Byte>|<xref:System.SByte>|  
|<xref:System.SByte>|<xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>|  
|<xref:System.Int16>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16>|  
|<xref:System.UInt16>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>|  
|<xref:System.Int32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32>|  
|<xref:System.UInt32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>|  
|<xref:System.Int64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64>|  
|<xref:System.UInt64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>|  
|<xref:System.Decimal>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Single>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Double>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Convert?displayProperty=nameWithType>
- [Conversion de type dans .NET](type-conversion.md)
