---
title: Extensibilité des canaux
ms.date: 03/30/2017
ms.assetid: 4cc3b20b-778a-4ae8-b58c-a3822fb13065
ms.openlocfilehash: 9dbae26a548bdc8a8cfb05a3dd90db91475b55ba
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600631"
---
# <a name="channels-extensibility"></a>Extensibilité des canaux
Cette section contient des exemples qui illustrent des canaux personnalisés.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Local Channel](local-channel.md)  
 Illustre le canal local, un canal de transport WCF utilisé pour la communication au sein du même domaine d’application.  
  
 [Reliable Secure Profile](reliable-secure-profile.md)  
 Montre comment composer WCF et Reliable Secure Profile (RSP).  
  
 [Custom Channel Dispatcher](custom-channel-dispatcher.md)  
 Montre comment générer la pile de canaux de façon personnalisée en implémentant <xref:System.ServiceModel.ServiceHostBase> directement et comment créer un répartiteur de canal personnalisé dans un environnement avec hôte Web.  
  
 [Canal de segmentation](chunking-channel.md)  
 Montre comment limiter la quantité de mémoire utilisée pour mettre en mémoire tampon des messages volumineux envoyés à l’aide de WCF.
  
 [HttpCookieSession](httpcookiesession.md)  
 Montre comment générer un canal de protocole personnalisé pour utiliser des cookies HTTP pour la gestion des sessions.  
  
 [Custom Message Interceptor](custom-message-interceptor.md)  
 Montre comment implémenter un élément de liaison personnalisé qui crée des fabriques et des écouteurs de canaux pour intercepter tous les messages entrants et sortants à un point spécifique de la pile d’exécution.
