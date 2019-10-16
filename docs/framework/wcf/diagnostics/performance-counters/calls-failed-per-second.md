---
title: Nombre d'appels ayant échoué par seconde
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: e7c0b53f4c2b1a7e87a5791b44e452ec9146c459
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321124"
---
# <a name="calls-failed-per-second"></a>Nombre d'appels ayant échoué par seconde
Nom du compteur : appels ayant échoué par seconde  
  
## <a name="description"></a>Description  
 Nombre d'appels à cette opération avec des exceptions non prises en charge par seconde.  
  
 Ce compteur est du type de compteur de performance [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l’aide de la formule suivante.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 Ce compteur est incrémenté chaque fois qu’il y a une exception non gérée dans cette opération.  
  
## <a name="see-also"></a>Voir aussi

- [Spécification et gestion des erreurs dans les contrats et les services](../../specifying-and-handling-faults-in-contracts-and-services.md)
