---
title: Utilisation des NAT et des pare-feu
ms.date: 03/30/2017
helpviewer_keywords:
- firewalls [WCF]
- NATs [WCF]
ms.assetid: 74db0632-1bf0-428b-89c8-bd53b64332e7
ms.openlocfilehash: bab29d738c7562753a826b47c03867eeebac4372
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558977"
---
# <a name="working-with-nats-and-firewalls"></a>Utilisation des NAT et des pare-feu
Il arrive fréquemment que les client et serveur d'une connexion réseau ne disposent pas d'une voie de communication directe et ouverte. Les paquets sont filtrés, acheminés, analysés et transformés par les ordinateurs de point de terminaison ainsi que par les ordinateurs intermédiaires sur le réseau. Ces ordinateurs intermédiaires, qui participent à la communication, sont notamment les applications de traduction d'adresses réseau (Network address translation, NAT) et les pare-feu.  
  
 Les transports Windows Communication Foundation (WCF) et MEP (message Exchange patterns) réagissent différemment à, la présence de nat et de pare-feu. Cette rubrique présente la manière dont ces deux types d'applications fonctionnent dans des topologies de réseau similaires. Des recommandations relatives à des combinaisons spécifiques de transports WCF et de MEP sont fournies pour améliorer la robustesse de vos applications pour les NAT et les pare-feu sur le réseau.  
  
## <a name="how-nats-affect-communication"></a>Répercussions des applications NAT sur les communications  
 Le mécanisme NAT a été créé pour permettre à plusieurs ordinateurs de partager une même adresse IP externe. Un NAT de remappage de port mappe une adresse IP interne et un port de connexion à une adresse IP externe à laquelle une nouveau numéro de port est attribué. Le nouveau numéro de port permet alors à la NAT de mettre en relation le trafic reçu en retour avec la communication originale. Les ordinateurs personnels des particuliers disposent dans la plupart des cas d'une adresse IP acheminable uniquement de manière privée et doivent donc utiliser un NAT pour assurer l'acheminement public de leurs paquets.  
  
 Les NAT n'offrent pas de cordon de sécurité. Cependant, les configurations NAT les plus courantes empêchent l'adressage direct des ordinateurs internes. Ce principe protège les ordinateurs internes des connexions indésirables, mais rend difficile le développement d'applications serveur devant renvoyer de manière asynchrone des données au client. Les NAT réécrivent les adresses figurant dans les paquets pour donner l'impression que les connexions transportant ces paquets émanent d'un ordinateur NAT. C'est pourquoi lorsque le serveur tente de rouvrir la connexion avec le client, il échoue. Si le serveur utilise l'adresse visible du client, sa tentative échoue car cette adresse ne peut pas être acheminée publiquement. Si le serveur utiliser l'adresse NAT du client, sa tentative échoue également car aucune application n'est à l'écoute des connexions depuis l'ordinateur NAT.  
  
 Certaines configurations NAT prennent en charge les règles de transfert afin de permettre aux ordinateurs externes de se connecter à certains ordinateurs internes. Les modalités de configuration de cette option varient en fonction des applications NAT. En outre, demander aux utilisateurs finaux de modifier leur configuration NAT est déconseillé pour la plupart des applications. Un grand nombre d'utilisateurs finaux ne peuvent ou ne souhaitent pas modifier leur configuration NAT pour une application particulière.  
  
## <a name="how-firewalls-affect-communication"></a>Répercussions des pare-feu sur les communications  
 Un *pare-feu* est un logiciel ou un périphérique matériel qui applique des règles au trafic transitant pour décider s’il faut autoriser ou refuser le passage. Les pare-feu peuvent être configurés de sorte à examiner les flux entrants et/ou sortants du trafic. Ils forment un cordon de sécurité sur le réseau considéré, au niveau des ses extrémités ou au niveau de l'hôte de point de terminaison. Les professionnels utilisent depuis longtemps les pare-feu pour protéger leurs serveurs des attaques malveillantes. Depuis l’introduction du pare-feu personnel dans Windows XP SP2, le nombre d’utilisateurs privés derrière un pare-feu a considérablement augmenté. C'est pourquoi, lors d'une connexion, il y a de grandes chances qu'aux deux extrémités un pare-feu examine les paquets.  
  
 Il existe une grande variété de pare-feu tant sur le plan de leur complexité que sur le plan des fonctionnalités qu'ils utilisent pour examiner les paquets. Les pare-feu de base appuient leur décision d'accorder ou non le droit d'entrée aux paquets en examinant les adresse de destination et de source ainsi que les ports qui y figurent. Les pare-feu plus élaborés examinent également le contenu des paquets pour prendre leur décision. Un grand nombre de configurations différents sont possibles pour ces pare-feu et ils sont souvent utilisés dans le cadre d'applications spécialisées.  
  
 Les pare-feu des ordinateurs personnels sont le plus souvent configurés de manière à interdire les connexions entrantes lorsqu'une connexion sortante n'a pas été établie au préalable vers ces ordinateurs. Dans le cadre professionnel, la configuration standard des pare-feu est celle consistant à interdire les connexions entrantes sur tous les ports sauf sur un groupe de ports spécifié. Par exemple, un pare-feu peut empêcher les connexions sur tous les ports sauf sur les ports 80 et 443 afin d'assurer les services HTTP et HTTPS. Les pare-feu managés sont utilisés à la fois par les professionnels et les particuliers. Ils permettent à un utilisateur ou à un processus approuvé de modifier leur configuration. Ce type de pare-feu se rencontre le plus fréquemment chez les particuliers puisque l'utilisation de leur réseau n'est régie par aucune politique d'entreprise.  
  
## <a name="using-teredo"></a>Utilisation de Teredo  

 Teredo est une technologie de transition IPv6 qui permet l'adressabilité directe des ordinateurs se trouvant derrière une application NAT. Cette technologie utilise un serveur pouvant être acheminé publiquement pour rendre publiques les éventuelles connexions afférentes. Le serveur Teredo sert de point de rencontre aux applications client et serveur et leur permet ainsi d'échanger leurs informations de connexion respectives. Les ordinateurs concernés demandent ensuite à obtenir une adresse Teredo temporaire et les paquets sont acheminés via le réseau existant. La prise en charge de Teredo dans WCF nécessite l’activation de la prise en charge D’ipv6 et de Teredo dans le système d’exploitation. Les systèmes d’exploitation Windows XP et versions ultérieures prennent en charge Teredo. Les systèmes d’exploitation Windows Vista et versions ultérieures prennent en charge IPv6 par défaut et demandent uniquement à l’utilisateur d’activer Teredo. Windows XP SP2 et Windows Server 2003 requièrent que l’utilisateur active à la fois IPv6 et Teredo. Pour plus d’informations, voir [vue d’ensemble de Teredo](/previous-versions/windows/it-pro/windows-xp/bb457011(v=technet.10)).  
  
## <a name="choosing-a-transport-and-message-exchange-pattern"></a>Sélection d’un transport et d’un modèle d’échange de messages  
 La sélection d'un transport et d'un MEP s'effectue en trois étapes :  
  
1. Analysez l'adressabilité des ordinateurs de point de terminaison. L'adressabilité des serveurs d'entreprise est en principe directe, tandis que l'adressabilité des ordinateurs des utilisateurs finaux est en général bloquée par des NAT. Si les deux point de terminaison se trouvent derrière une application NAT, par exemple dans le cadre d'une situation pair-à-pair entre deux utilisateurs finaux, vous aurez peut-être besoin de la technologie Teredo pour assurer l'adressabilité.  
  
2. Analysez les restrictions en termes de protocole et de port en vigueur sur les ordinateurs de point de terminaison. Les servers d'entreprise sont généralement protégés par des pare-feu puissants qui bloquent un grand nombre de ports. Toutefois, les ports 80 et 443 sont fréquemment maintenus ouverts pour laisser passer les trafics HTTP et HTTPS. Ces types de restrictions ne sont généralement pas appliqués aux ordinateurs des utilisateurs finaux, mais il se peut que ces ordinateurs se trouvent derrière un pare-feu autorisant uniquement les connexions sortantes. Certains pare-feu permettent aux applications figurant sur le point de terminaison d'ouvrir de manière sélective certaines connexions.  
  
3. Calculez les transports et les MEP autorisés par l'adressabilité et les restrictions de port en vigueur sur le réseau.  
  
 La topologie la plus fréquente pour les applications client et serveur est la suivante : les clients se trouvent derrière une application NAT sans Teredo et un pare-feu autorisant uniquement les connexions sortantes tandis que les serveurs se trouvent derrière un pare-feu puissant, mais peuvent être adressés directement. Dans une telle situation, un transport TCP associé à un MEP duplex et un transport HTTP associé à un MEP demande-réponse fonctionneront correctement. La topologie la plus fréquente pour les applications pair-à-pair est la suivante : les deux points de terminaison se trouvent à la fois derrière une application NAT et un pare-feu. Dans une telle situation ainsi que dans les cas où la topologie du réseau n'est pas connue, prenez en compte les recommandations suivantes :  
  
- N'utilisez pas de transports doubles. Un transport double ouvre plusieurs connexions, réduisant ainsi les chances d'établir une connexion réussie.  
  
- Assurez la prise en charge des canaux d'arrière sur la connexion d'origine. L'utilisation de canaux d'arrière, notamment avec les transports TCP en mode duplex, permet d'ouvrir un nombre de connexions moindre, augmentant ainsi les chances d'établir une connexion réussie.  
  
- Utilisez un service accessible pour inscrire les points de terminaison ou relayer le trafic. L'utilisation d'un service de connexion accessible de manière universelle, par exemple un serveur Teredo, augmente considérablement les chances d'établir une connexion réussie lorsque la topologie réseau est restreinte ou inconnue.  
  
 Les tableaux suivants examinent les MEP unidirectionnel, demande-réponse et duplex, ainsi que le TCP standard, TCP avec Teredo et les transports HTTP standard et doubles dans WCF.  
  
|Adressabilité|Serveur Direct|Serveur Direct avec parcours NAT|Serveur NAT|Serveur NAT avec parcours NAT|  
|--------------------|-------------------|--------------------------------------|----------------|-----------------------------------|  
|Client direct|Tout transport et MEP|Tout transport et MEP|Non pris en charge.|Non pris en charge.|  
|Client direct avec parcours NAT|Tout transport et MEP|Tout transport et MEP|Non pris en charge.|TCP avec Teredo et tout MEP. Windows Vista dispose d’une option de configuration à l’ensemble de l’ordinateur pour prendre en charge HTTP avec Teredo.|  
|Client NAT|Tout transport non double et tout MEP. Un MEP duplex nécessite un transport TCP.|Tout transport non double et tout MEP. Un MEP duplex nécessite un transport TCP.|Non pris en charge.|Non pris en charge.|  
|Client NAT avec parcours NAT|Tout transport non double et tout MEP. Un MEP duplex nécessite un transport TCP.|Tout transport sauf HTTP double et tout MEP. Un MEP duplex nécessite un transport TCP. Un transport TCP double nécessite Teredo. Windows Vista dispose d’une option de configuration à l’ensemble de l’ordinateur pour prendre en charge HTTP avec Teredo.|Non pris en charge.|TCP avec Teredo et tout MEP. Windows Vista dispose d’une option de configuration à l’ensemble de l’ordinateur pour prendre en charge HTTP avec Teredo.|  
  
|Restrictions de pare-feu|Serveur ouvert|Serveur avec pare-feu managé|Serveur avec pare-feu autorisant uniquement HTTP|Serveur avec pare-feu autorisant uniquement les connexions sortantes|  
|---------------------------|-----------------|----------------------------------|-------------------------------------|-----------------------------------------|  
|Client ouvert|Tout transport et MEP|Tout transport et MEP|Tout transport HTTP et MEP|Non pris en charge.|  
|Client avec pare-feu managé|Tout transport non double et tout MEP. Un MEP duplex nécessite un transport TCP.|Tout transport non double et tout MEP. Un MEP duplex nécessite un transport TCP.|Tout transport HTTP et MEP|Non pris en charge.|  
|Client avec pare-feu autorisant uniquement HTTP|Tout transport HTTP et MEP|Tout transport HTTP et MEP|Tout transport HTTP et MEP|Non pris en charge.|  
|Client avec pare-feu autorisant uniquement les connexions sortantes|Tout transport non double et tout MEP. Un MEP duplex nécessite un transport TCP.|Tout transport non double et tout MEP. Un MEP duplex nécessite un transport TCP.|Tout transport HTTP et tout MEP non duplex.|Non pris en charge.|
