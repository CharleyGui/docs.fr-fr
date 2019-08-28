---
title: Compteurs de performance de point de terminaison
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: 2352bc82998c8e87e72f331104446bac4fcb9fda
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040583"
---
# <a name="endpoint-performance-counters"></a>Compteurs de performance de point de terminaison
Les compteurs de performance de point de terminaison capturent des données qui révèlent comment un point de terminaison accepte des messages. Ils se trouvent sous l'objet de performance `ServiceModelEndpoint 4.0.0.0` dans l'affichage de l'analyseur de performances. Les instances sont nommées à l’aide du modèle suivant :  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 Les données sont semblables à celles recueillies pour des opérations individuelles, mais sont regroupées uniquement sur l'ensemble du point de terminaison.  
  
> [!CAUTION]
> La longueur du nom d'une instance de compteur de performance est limitée. Lorsqu’un nom d’instance de compteur Windows Communication Foundation (WCF) dépasse la longueur maximale, WCF remplace une partie du nom de l’instance par une valeur de hachage.  
  
## <a name="see-also"></a>Voir aussi

- [Compteurs de performance](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
