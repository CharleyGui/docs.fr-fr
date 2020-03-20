---
title: Activation dynamique du traçage analytique
ms.date: 03/30/2017
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
ms.openlocfilehash: 22d122f802e82c2aa04d72a996cb872e06fcaeaa
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674953"
---
# <a name="dynamically-enabling-analytic-tracing"></a>Activation dynamique du traçage analytique
À l'aide des outils fournis par le système d'exploitation Windows, vous pouvez activer ou désactiver de manière dynamique le suivi d'événements Windows (ETW). Pour [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] tous les services de la Windows Communication Foundation (WCF), le traçage analytique peut être activé et désactivé dynamiquement sans modifier le fichier Web.config de l’application ou redémarrer le service. Cela permet de ne pas perturber l'application qui émet les événements de suivi.  
  
 Les options de traçage WCF peuvent être configurées de la même manière. Par exemple, vous pouvez modifier le niveau de gravité **Erreur** en **Informations** sans porter atteinte à l'application. Cela peut s'effectuer à l'aide des outils suivants :  
  
- **Logman** : outil de ligne de commande pour configurer, contrôler et interroger les données de suivi. Pour plus d’informations, voir [Logman Create Trace](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc788036(v=ws.10)) et [Logman Update Trace](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc788128(v=ws.10)).  
  
- **Observateur d'événements** : outil d'administration graphique de Windows pour afficher les résultats du suivi. Pour plus d’informations, voir [WCF Services and Event Tracing for Windows](../../samples/wcf-services-and-event-tracing-for-windows.md) and Event [Viewer](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc766042(v=ws.11)).  
  
- **Perfmon** : outil d'administration graphique de Windows utilisant des compteurs pour analyser les compteurs de suivi et les effets du suivi sur les performances. Pour plus d’informations, voir [Créer un ensemble de collecte de données manuellement](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc766404(v=ws.11)).  
  
### <a name="keywords"></a>Mots clés  
 Lors de l'utilisation de la classe <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> , les messages de trace .NET Framework sont généralement filtrés en fonction du niveau de gravité (par exemple, Erreur, Avertissement et Informations). Le suivi ETW prend en charge le concept de niveau de gravité, mais introduit un nouveau mécanisme de filtre souple, utilisant des mots clés. Les mots clés sont des valeurs textuelles arbitraires qui permettent aux événements de suivi de fournir un contexte supplémentaire sur la signification de cet événement.  
  
 Pour le traçage analytique WCF, chaque événement trace a deux types de mots clés. Tout d'abord, chaque événement possède un ou plusieurs mots clés de scénario. Ces mots clés indiquent les scénarios que cet événement est destiné à prendre en charge. Il y a trois mots clés de scénario, chacun conçu pour un objectif spécifique, comme indiqué dans le tableau suivant. Le filtrage à l’aide de mots clés peut être modifié dynamiquement sans perturber le service WCF. Cela signifie que vous pouvez modifier de manière dynamique votre scénario de suivi actuel et la quantité d'informations de suivi que vous rassemblez. Par exemple, vous pouvez modifier `HealthMonitoring` en `Troubleshooting` et augmenter la granularité de l'événement de suivi.  
  
|Mot clé|Description|  
|-------------|-----------------|  
|`HealthMonitoring`|Suivi très léger, minimal qui vous permet de surveiller l'activité de votre service.|  
|`EndToEndMonitoring`|Événements utilisés pour prendre en charge le suivi du flux des messages.|  
|`Troubleshooting`|Événements plus granulaires autour des points d’extéabilité de WCF.|  
  
 Le deuxième groupe de mots clés définit quelle composante du cadre .NET a émis l’événement.  
  
|Mot clé|Description|  
|-------------|-----------------|  
|`UserEvents`|Événements émis par le code utilisateur et non par le cadre .NET.|  
|`ServiceModel`|Événements émis par le temps d’exécution WCF.|  
|`ServiceHost`|Événements émis par l'hôte de service.|  
|`WCFMessageLogging`|Événements d’enregistrement de messages WCF.|  
  
## <a name="see-also"></a>Voir aussi

- [WCF Services and Event Tracing for Windows](../../samples/wcf-services-and-event-tracing-for-windows.md)
