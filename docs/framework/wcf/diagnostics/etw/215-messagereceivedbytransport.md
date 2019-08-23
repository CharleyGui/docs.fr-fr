---
title: 215 - MessageReceivedByTransport
ms.date: 03/30/2017
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
ms.openlocfilehash: aa1ad30526aa65501e5d9875d3877631ca00879b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964188"
---
# <a name="215---messagereceivedbytransport"></a>215 - MessageReceivedByTransport
## <a name="properties"></a>Properties  
  
|||  
|-|-|  
|ID|215|  
|Mots clés|Dépannage, ServiceModel|  
|Niveau|Information|  
|Canal|Microsoft-Windows-Application Server-Applications/Analyse|  
  
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
|HostReference|`xs:string`|Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web. Son format est défini en tant que «nom du site Web&#124;chemin d’accès&#124;virtuel du service de chemin d’accès virtuel ServiceName». Exemple : 'Default Web site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
