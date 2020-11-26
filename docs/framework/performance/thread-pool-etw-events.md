---
title: Événements ETW de pool de threads
description: Passez en revue les événements ETW de pool de threads, qui collectent des informations sur les threads dans .NET. Les événements de pool de threads sont les événements de pool de threads de travail ou d’e/s.
ms.date: 03/30/2017
helpviewer_keywords:
- thread pool events [.NET Framework]
- ETW, thread pool events (CLR)
ms.assetid: f2a21e3a-3b6c-4433-97f3-47ff16855ecc
ms.openlocfilehash: 8b00c20e82ee1b1efa6a8a123e66a4cfc239143b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236167"
---
# <a name="thread-pool-etw-events"></a>Événements ETW de pool de threads

Ces événements collectent des informations sur les threads de travail et d'E/S.  
  
 Il existe deux groupes d'événements de pool de threads :  
  
- Les[événements du pool de threads de travail](#worker-thread-pool-events), qui fournissent des informations sur la manière dont une application utilise le pool de threads, et l'effet des charges de travail sur le contrôle d'accès concurrentiel.  
  
- Les[événements du pool de threads d'E/S](#io-thread-events), qui fournissent des informations sur les threads d'E/S créés, retirés, non retirés ou terminés dans le pool de threads.  

## <a name="worker-thread-pool-events"></a>événements du pool de threads de travail

 Ces événements sont liés au pool de threads de travail du runtime et fournissent des notifications pour les événements de thread (par exemple, quand un thread est créé ou arrêté). Le pool de threads de travail utilise un algorithme flexible pour le contrôle d’accès concurrentiel, où le nombre de threads est calculé en fonction du débit mesuré. Les événements du pool de threads de travail peuvent être utilisés pour comprendre comment une application utilise le pool de threads et l'effet que certaines charges de travail peuvent avoir sur le contrôle d'accès concurrentiel.  
  
### <a name="threadpoolworkerthreadstart-and-threadpoolworkerthreadstop"></a>ThreadPoolWorkerThreadStart et ThreadPoolWorkerThreadStop  

 Le tableau ci-dessous indique le mot clé et le niveau de ces événements. (Pour plus d'informations, consultez [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)  
  
|Mot clé pour déclencher l'événement|Level|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informatif (4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID de l’événement|Moment du déclenchement|  
|-|-|-|  
|`ThreadPoolWorkerThreadStart`|50|Un thread de travail est créé.|  
|`ThreadPoolWorkerThreadStop`|51|Un thread de travail est arrêté.|  
|`ThreadPoolWorkerThreadRetirementStart`|52|Un thread de travail est retiré.|  
|`ThreadPoolWorkerThreadRetirementStop`|53|Un thread de travail retiré redevient actif.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|ActiveWorkerThreadCount|win:UInt32|Nombre de threads de travail disponibles pour traiter le travail, y compris ceux qui sont déjà en cours d’utilisation.|  
|RetiredWorkerThreadCount|win:UInt32|Nombre de threads de travail qui ne sont pas disponibles pour traiter le travail, mais qui sont gardés en réserve au cas où des threads supplémentaires seraient requis ultérieurement.|  
|ClrInstanceID|Win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
### <a name="threadpoolworkerthreadadjustment"></a>ThreadPoolWorkerThreadAdjustment  

 Ces événements de pool de threads fournissent des informations permettant de comprendre et de déboguer le comportement de l'algorithme d'injection de thread (contrôle d'accès concurrentiel). Ces informations sont utilisées en interne par le pool de threads de travail.  
  
#### <a name="threadpoolworkerthreadadjustmentsample"></a>ThreadPoolWorkerThreadAdjustmentSample  

 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Level|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informatif (4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID de l’événement|Description|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentSample`|54|Fait référence à la collecte d'informations pour un exemple. Autrement dit, une mesure de débit avec un certain niveau d’accès concurrentiel à un instant donné.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|Débit|win:Double|Nombre d'achèvements par unité de temps|  
|ClrInstanceID|Win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
#### <a name="threadpoolworkerthreadadjustmentadjustment"></a>ThreadPoolWorkerThreadAdjustmentAdjustment  

 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Level|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informatif (4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID de l’événement|Description|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|55|Enregistre une modification dans le contrôle, quand l'algorithme d'injection de thread (hill-climbing) détermine qu'une modification du niveau d'accès concurrentiel a eu lieu.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|AverageThroughput|win:Double|Débit moyen d'un échantillon de mesures|  
|NewWorkerThreadCount|win:UInt32|Nouveau nombre de threads de travail actifs|  
|Motif|win:UInt32|Raison de l'ajustement<br /><br /> 0x00 – Préchauffage<br /><br /> 0x01 – Initialisation<br /><br /> 0x02 – Déplacement aléatoire<br /><br /> 0x03 – Déplacement vers le haut<br /><br /> 0x04 – Point de changement<br /><br /> 0x05 – Stabilisation<br /><br /> 0x06 – Privation<br /><br /> 0x07 – Thread expiré|  
|ClrInstanceID|Win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
#### <a name="threadpoolworkerthreadadjustmentstats"></a>ThreadPoolWorkerThreadAdjustmentStats  

 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Level|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informatif (4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID de l’événement|Description|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentStats`|56|Rassemble des données sur le pool de threads.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|Duration|win:Double|Durée, en secondes, pendant laquelle ces statistiques ont été collectées.|  
|Débit|win:Double|Nombre moyen d'achèvements par seconde au cours de cet intervalle.|  
|ThreadWave|win:Double|Réservé à un usage interne.|  
|ThroughputWave|win:Double|Réservé à un usage interne.|  
|ThroughputErrorEstimate|win:Double|Réservé à un usage interne.|  
|AverageThroughputErrorEstimate|win:Double|Réservé à un usage interne.|  
|ThroughputRatio|win:Double|Amélioration relative du débit provoquée par les variations du nombre de threads de travail actifs au cours de cet intervalle.|  
|Confiance|win:Double|Mesure de la validité du champ ThroughputRatio.|  
|NewcontrolSetting|win:Double|Nombre de threads de travail actifs qui servira de référence pour les futures variations du nombre de threads actifs.|  
|NewThreadWaveMagnitude|Win:UInt16|Importance des futures variations du nombre de threads actifs.|  
|ClrInstanceID|Win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  

## <a name="io-thread-events"></a>Événements de thread d'E/S  

 Ces événements de pool de threads se produisent pour les threads du pool de threads d'E/S (ports de terminaison), qui est asynchrone.  
  
### <a name="iothreadcreate_v1"></a>IOThreadCreate_V1  

 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Level|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informatif (4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID de l’événement|Moment du déclenchement|  
|-|-|-|  
|`IOThreadCreate_V1`|44|Un thread d'E/S est créé dans le pool de threads.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|Count|win:UInt64|Nombre de threads d'E/S, y compris le nouveau thread.|  
|NumRetired|win:UInt64|Nombre de threads de travail retirés|  
|ClrInstanceID|Win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
### <a name="iothreadretire_v1"></a>IOThreadRetire_V1  

 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Level|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informatif (4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID de l’événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`IOThreadRetire_V1`|46|Un thread d'E/S devient candidat au retrait.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|Count|win:UInt64|Nombre de threads d'E/S restant dans le pool de threads|  
|NumRetired|win:UInt64|Nombre de threads d'E/S retirés|  
|ClrInstanceID|Win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
### <a name="iothreadunretire_v1"></a>IOThreadUnretire_V1  

 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Level|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informatif (4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID de l’événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`IOThreadUnretire_V1`|47|Le retrait d’un thread d'E/S est annulé en raison d'une E/S qui se produit au cours d’une période d'attente après que le thread est devenu un candidat au retrait.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|Count|win:UInt64|Nombre de threads d'E/S dans le pool de threads, y compris celui-ci|  
|NumRetired|win:UInt64|Nombre de threads d'E/S retirés|  
|ClrInstanceID|Win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
### <a name="iothreadterminate"></a>IOThreadTerminate  

 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Level|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informatif (4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID de l’événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`IOThreadTerminate`|45|Un thread d’e/s se termine dans le pool de threads.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|Count|win:UInt64|Nombre de threads d'E/S restant dans le pool de threads|  
|NumRetired|win:UInt64|Nombre de threads d'E/S retirés|  
|ClrInstanceID|Win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
## <a name="see-also"></a>Voir aussi

- [Événements ETW du CLR](clr-etw-events.md)
