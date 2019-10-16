---
title: 'Point de terminaison : appels ayant échoué par seconde'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: 9634f8a170bb2fae2f15c3f00dcabb95d512c74e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321456"
---
# <a name="endpoint-calls-failed-per-second"></a>Point de terminaison : appels ayant échoué par seconde
Nom du compteur : appels ayant échoué par seconde.  
  
## <a name="description"></a>Description  
 Nombre d'appels ayant des exceptions non traitées et reçus par ce point de terminaison en une seconde.  
  
 Ce compteur est du type de compteur de performance [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l’aide de la formule suivante.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 Ce compteur est incrémenté à chaque exception non traitée à ce point de terminaison.  
  
## <a name="see-also"></a>Voir aussi

- [Spécification et gestion des erreurs dans les contrats et les services](../../specifying-and-handling-faults-in-contracts-and-services.md)
