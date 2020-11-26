---
title: Files d'attente dans Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF]
ms.assetid: 43008409-1bb4-4bd4-85d7-862c8f10ae20
ms.openlocfilehash: d63b03e519484ad6ec90b4267a49b77738593e45
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244650"
---
# <a name="queues-in-windows-communication-foundation"></a>Files d'attente dans Windows Communication Foundation

Les rubriques de cette section traitent de la prise en charge de Windows Communication Foundation (WCF) pour les files d’attente. WCF prend en charge la mise en file d’attente en tirant parti de Microsoft Message Queuing (précédemment appelé MSMQ) comme un transport et active les scénarios suivants :  
  
- Applications faiblement couplées. Les applications émettrices peuvent envoyer des messages aux files d'attente sans avoir besoin de savoir si l'application réceptrice est disponible pour traiter le message. La file d'attente permet l'indépendance du traitement, ce qui signifie que l'application émettrice peut envoyer des messages à la file d'attente à un taux de qui ne dépend pas de la rapidité avec laquelle les applications réceptrices peuvent traiter les messages. La disponibilité globale du système augmente lorsque l'envoi de messages à une file d'attente n'est pas fortement couplé au traitement du message.  
  
- Isolation de défaillance. Les applications qui envoient des messages à une file d'attente ou en reçoivent peuvent échouer sans impact mutuel. Par exemple, si l'application réceptrice échoue, l'application émettrice peut continuer à envoyer des messages à la file d'attente. Lorsque le récepteur est de nouveau en service, il peut traiter les messages de la file d'attente. L'isolation de défaillance augmente la fiabilité globale du système et sa disponibilité.  
  
- Nivellement de charge. Les applications émettrices peuvent submerger de messages les applications réceptrices. Les files d'attente peuvent gérer la production de messages et les taux consommation incompatibles afin qu'un récepteur ne soit pas submergé.  
  
- Opérations hors circuit. L'envoi, la réception et le traitement d'opérations peut se faire hors circuit en cas de communication sur des réseaux à forte latence ou à disponibilité limitée, comme dans le cas des appareils mobiles. Les files d'attente permettent à ces opérations de se poursuivre, même lorsque les points de terminaison sont déconnectés. Lorsque la connexion est rétablie, la file d'attente envoie des messages à l'application réceptrice.  
  
 Pour utiliser la fonctionnalité files d’attente dans une application WCF, vous pouvez utiliser l’une des liaisons standard, ou vous pouvez créer une liaison personnalisée si l’une des liaisons standard ne répond pas à vos exigences. Pour plus d’informations sur les liaisons standard pertinentes et la manière d’en choisir une, consultez [Comment : échanger des messages avec des points de terminaison WCF et des applications de Message Queuing](how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md). Pour plus d’informations sur la création de liaisons personnalisées, consultez [Liaisons personnalisées](../extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>Dans cette section  

 [Vue d'ensemble des files d'attente](queues-overview.md)  
 Vue d'ensemble des concepts de la mise en file d'attente des messages.  
  
 [Mise en file d'attente dans WCF](queuing-in-wcf.md)  
 Vue d’ensemble de la prise en charge des files d’attente WCF.  
  
 [Procédure : échanger des messages mis en file d’attente avec des points de terminaison WCF](how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 Explique comment utiliser la <xref:System.ServiceModel.NetMsmqBinding> classe pour communiquer entre un client WCF et un service WCF.  
  
 [Procédure : échanger des messages avec des points de terminaison WCF et des applications Message Queuing](how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 Explique comment utiliser le <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> pour communiquer entre les applications WCF et Message Queuing.  
  
 [Regroupement de messages mis en file d'attente dans une session](grouping-queued-messages-in-a-session.md)  
 Explique comment grouper des messages dans une file d'attente pour faciliter le traitement des messages corrélés par une application réceptrice unique.  
  
 [Traitement par lots des messages dans une transaction](batching-messages-in-a-transaction.md)  
 Explique comment traiter par lots les messages dans une transaction.  
  
 [Utilisation de files d'attente de lettres mortes pour gérer des défaillances de transfert de messages](using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 Explique comment gérer les échecs de transfert des messages et de livraison à l'aide des files d'attente de lettres mortes et comment traiter des messages de la file d'attente de lettres mortes.  
  
 [Gestion des messages incohérents](poison-message-handling.md)  
 Explique comment gérer les messages incohérents (messages qui ont dépassé le nombre maximal de tentatives de livraison à l'application réceptrice).  
  
 [Différences entre les fonctionnalités de mise en file d’attente dans Windows Vista, Windows Server 2003 et Windows XP](diff-in-queue-in-vista-server-2003-windows-xp.md)  
 Résume les différences de la fonctionnalité files d’attente WCF entre Windows Vista, Windows Server 2003 et Windows XP.  
  
 [Sécurisation des messages à l'aide de la sécurité de transport](securing-messages-using-transport-security.md)  
 Décrit comment utiliser la sécurité de transport pour sécuriser des messages mis en file d'attente.  
  
 [Sécurisation des messages à l'aide de la sécurité de message](securing-messages-using-message-security.md)  
 Décrit comment utiliser la sécurité des messages pour sécuriser des messages mis en file d'attente.  
  
 [Résolution des problèmes de messagerie en file d'attente](troubleshooting-queued-messaging.md)  
 Explique comment résoudre les problèmes courants de mise en file d'attente.  
  
 [Meilleures pratiques pour les communications mises en file d'attente](best-practices-for-queued-communication.md)  
 Décrit les meilleures pratiques pour l’utilisation de la communication en file d’attente WCF.  
