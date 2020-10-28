---
title: Conversion de types .NET en chaînes
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
ms.openlocfilehash: ca35af17a402dc901c02edf94099af1377e1160f
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687625"
---
# <a name="convert-net-types-to-strings"></a>Convertir des types .NET en chaînes

Si vous souhaitez convertir un type .NET en chaîne, utilisez la méthode **ToString** . La méthode **ToString** retourne une représentation sous forme de chaîne du type passé. Le tableau suivant répertorie les types .NET qui retournent une chaîne dans un format mappé aux spécifications de schéma XML (XSD).  
  
|Type .NET|Type de chaîne de retour|  
|-------------------------|--------------------------|  
|Boolean|"true", "false"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|DateTime|Le format est yyyy-MM-ddTHH:mm:sszzzzzz et ses sous-ensembles.|  
|Timespan|Le format est PnYnMnTnHnMnS. Par exemple, `P2Y10M15DT10H30M20S` est la durée de 2 années, 10 mois, 15 jours, 10 heures, 30 minutes et 20 secondes.|  
  
## <a name="see-also"></a>Voir aussi

- [Conversion des types de données XML](conversion-of-xml-data-types.md)
- [Conversion de chaînes en types de données .NET](converting-strings-to-dotnet-data-types.md)
