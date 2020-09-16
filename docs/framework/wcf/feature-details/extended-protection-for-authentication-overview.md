---
title: Vue d'ensemble de la protection étendue de l'authentification
ms.date: 03/30/2017
ms.assetid: 3d2ceffe-a7bf-4bd9-a5a2-9406423bd7f8
ms.openlocfilehash: fdc42228077bbc703e2e7557c8d7fdb3ff57a150
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559263"
---
# <a name="extended-protection-for-authentication-overview"></a>Vue d'ensemble de la protection étendue de l'authentification
La protection étendue de l'authentification contribue à la protection contre les attaques de l'intercepteur (« man-in-the-middle ») au cours desquelles un intrus intercepte les informations d'identification d'un client et les transmet à un serveur.  
  
 Prenons l'exemple d'un scénario impliquant trois participants : un client, un serveur et un intercepteur. Le serveur présente l'URL `https://server`, l'intercepteur l'URL `https://attacker`. L'intercepteur fait croire au client qu'il accède au serveur, alors qu'il accède en fait à l'URL de l'intercepteur. L'intercepteur envoie alors une demande au serveur. Si l'intercepteur tente d'accéder à une ressource sécurisée, le serveur lui répond avec un en-tête WWW-Authenticate. L'intercepteur ne disposant pas des informations d'authentification, il envoie l'en-tête WWW-Authenticate au client. Le client envoie l'en-tête d'autorisation à l'intercepteur qui, à son tour, envoie l'en-tête au serveur et obtient ainsi l'accès aux ressources sécurisées grâce aux informations d'identification du client.  
  
 Actuellement, lorsqu’une application cliente s’authentifie elle-même au serveur à l’aide de Kerberos, de Digest ou de NTLM via le protocole HTTPS, un canal TLS (Transport Level Security) est d’abord établi, puis l’authentification a lieu à l’aide de ce canal. Toutefois, il n'existe aucune liaison entre la clé de session générée par SSL (Secure Sockets Layer) et celle générée au cours de l'authentification. Ainsi, dans le scénario précédent, si la communication a lieu via un canal TLS (tel qu'un canal HTTPS), deux canaux SSL sont créés : un entre le client et l'intercepteur et l'autre entre l'intercepteur et le serveur. Les informations d'identification du client sont d'abord envoyées au serveur via le canal SSL établi entre le client et l'intercepteur, puis via le canal entre l'intercepteur et le serveur. Une fois que les informations d'identification du client ont atteint le serveur, ce dernier procède à leur vérification sans remarquer que le canal par le biais duquel elles ont été envoyées émane de l'intercepteur, et non du client.  
  
 La solution consiste à utiliser un canal externe sécurisé TLS et un canal interne authentifié par le client, puis à transmettre un jeton de liaison de canal (CBT, Channel Binding Token) au serveur. Le CBT est une propriété du canal externe sécurisé TLS et permet d'établir la liaison entre le canal externe et une conversation via le canal interne authentifié par le client.  
  
 Dans le scénario précédent, le CBT du canal TLS client-intercepteur est fusionné avec les informations d'autorisation envoyées au serveur. Un serveur reconnaissant CBT compare le CBT contenu dans les informations d'authentification du client, qui correspond au canal client-intercepteur, avec le CBT joint au canal intercepteur-serveur. Un CBT est spécifique à la destination d'un canal, afin que le CBT client-intercepteur ne corresponde pas au CBT intercepteur-serveur. Cela permet au serveur de détecter l'attaque MITM de l'intercepteur et de refuser la demande d'authentification.  
  
 Côté client, aucun paramètre de configuration n'est requis. Une fois que le client a été mis à jour pour transmettre le CBT au serveur, il procède toujours de cette façon. Si le serveur a également été mis à jour, il peut être configuré de manière à utiliser le CBT ou à l'ignorer. S'il n'a pas été mis à jour, il l'ignore.  
  
 Le serveur peut présenter les niveaux de protection suivants :  
  
- Aucun. Aucune validation de liaison de canal n’est exécutée. Il s'agit du comportement de tous les serveurs qui n'ont pas été mis à jour.  
  
- Partial. Tous les clients qui ont été mis à jour doivent fournir les informations de liaison de canal au serveur. Les clients qui n'ont pas été mis à jour n'ont pas à le faire. Il s'agit d'une option intermédiaire qui permet la compatibilité des applications.  
  
- Complet. Tous les clients doivent fournir des informations de liaison de canal. Le serveur rejette les demandes d'authentification émanant des clients qui ne se soumettent pas à cette obligation.  
  
 Pour plus d'informations, consultez l'exemple Win7 CBT/Protection étendue.  
  
## <a name="see-also"></a>Voir aussi

- [Modèle de sécurité pour Windows Server AppFabric](/previous-versions/appfabric/ee677202(v=azure.10))
