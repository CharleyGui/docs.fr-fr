---
title: Contrats de routage
ms.date: 03/30/2017
ms.assetid: 9ceea7ae-ea19-4cf9-ba4f-d071e236546d
ms.openlocfilehash: 69dff2c82f67a16d51e11a92052c59672a054e04
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601073"
---
# <a name="routing-contracts"></a>Contrats de routage
Les contrats de routage définissent les modèles de messages que le service de routage peut traiter.  Chaque contrat est sans type et permet au service de recevoir un message sans connaissance du schéma ni de l'action du message. Cela permet au service de routage de router des messages de manière générique, sans configuration supplémentaire pour les caractéristiques sous-jacentes des messages routés.  
  
## <a name="routing-contracts"></a>Contrats de routage  
 Puisque le service de routage accepte un objet Message WCF générique, le plus important lorsque vous sélectionnez un contrat est de prendre en compte la forme du canal utilisé lors de la communication avec les clients et les services. Lors du traitement des messages, le service de routage utilise des pompes de messages symétriques, en conséquence, la forme du contrat entrant doit généralement correspondre à la forme du contrat sortant. Toutefois, dans certains cas, le répartiteur du modèle de service peut modifier les formes, par exemple quand le répartiteur convertit un canal duplex en un canal de demande-réponse, ou supprime la prise en charge de session d’un canal quand ce n’est pas nécessaire et n’est pas utilisé (c’est-à-dire, lorsque **SessionMode. allowed**, conversion d’un **IInputSessionChannel** en **IInputChannel**).  
  
 Pour prendre en charge ces pompes de messages, le service de routage fournit des contrats dans l'espace de noms <xref:System.ServiceModel.Routing>, qui doivent être utilisés lors de la définition des points de terminaison de service utilisés par le service de routage. Ces contrats sont sans type, ce qui autorise la réception de tout type ou action de message et permet au service de routage de gérer des messages sans connaître le schéma de message spécifique. Pour plus d’informations sur les contrats utilisés par le service de routage, consultez [routage des contrats](routing-contracts.md).  
  
 Les contrats fournis par le service de routage se trouvent dans l'espace de noms <xref:System.ServiceModel.Routing> et sont décrits dans le tableau suivant.  
  
|Contrat|Forme|Forme de canal|  
|--------------|-----------|-------------------|  
|<xref:System.ServiceModel.Routing.ISimplexDatagramRouter>|SessionMode = SessionMode.Allowed<br /><br /> AsyncPattern = true<br /><br /> IsOneWay = true|IInputChannel-> IOutputChannel|  
|<xref:System.ServiceModel.Routing.ISimplexSessionRouter>|SessionMode = SessionMode.Required<br /><br /> AsyncPattern = true<br /><br /> IsOneWay = true|IInputSessionChannel-> IOutputSessionChannel|  
|<xref:System.ServiceModel.Routing.IRequestReplyRouter>|SessionMode = SessionMode.Allowed<br /><br /> AsyncPattern = true|IReplyChannel-> IRequestChannel|  
|<xref:System.ServiceModel.Routing.IDuplexSessionRouter>|SessionMode=SessionMode.Required<br /><br /> CallbackContract=typeof(ISimplexSession)<br /><br /> AsyncPattern = true<br /><br /> IsOneWay = true<br /><br /> TransactionFlow(TransactionFlowOption.Allowed)|IDuplexSessionChannel-> IDuplexSessionChannel|  
  
## <a name="see-also"></a>Voir aussi

- [Service de routage](routing-service.md)
- [Introduction au routage](routing-introduction.md)
