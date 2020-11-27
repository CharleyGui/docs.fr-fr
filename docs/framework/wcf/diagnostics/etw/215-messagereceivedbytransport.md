---
title: 215 - MessageReceivedByTransport
ms.date: 03/30/2017
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
ms.openlocfilehash: 2f247e751a0690f13d059eff29d633c6d047775d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279075"
---
# <a name="215---messagereceivedbytransport"></a>215 - MessageReceivedByTransport

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|id|215|  
|Mots clés|Dépannage, ServiceModel|  
|Level|Informations|  
|Channel|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  

 Cet événement se produit lorsqu'un transport basé sur TCP reçoit un message. Notez qu'au niveau du transport, plusieurs messages peuvent être échangés entre clients et services pour une seule opération. Cela peut être dû au comportement d'infrastructure, la sécurité étant un bon exemple. Par conséquent, le nombre d'événements `MessageReceivedByTransport` émis varie en fonction de la liaison de votre service et de sa configuration.  
  
> [!NOTE]
> Cet événement n'est pas émis pour les transports unidirectionnels.  
  
## <a name="message"></a>Message  

 Le transport a reçu un message de '%1'.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|Adresse d'écoute|`xs:string`|Adresse qui a reçu le message.|  
|HostReference|`xs:string`|Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web. Son format est défini en tant que « chemin d’accès virtuel de l’application nom du site Web&#124;chemin d’accès virtuel du service&#124;ServiceName ». Exemple : « Default Web site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService ».|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
