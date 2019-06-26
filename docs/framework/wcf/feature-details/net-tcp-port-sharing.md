---
title: Partage de ports Net.TCP
ms.date: 03/30/2017
helpviewer_keywords:
- port activation [WCF]
- port sharing [WCF]
ms.assetid: f13692ee-a179-4439-ae72-50db9534eded
ms.openlocfilehash: 4d7f28c692c7eb3527a851c6456473afc20a9aeb
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402466"
---
# <a name="nettcp-port-sharing"></a>Partage de ports Net.TCP
Windows Communication Foundation (WCF) fournit un nouveau protocole réseau basé sur TCP (net.tcp://) pour une communication hautes performances. WCF introduit également un nouveau composant système, le Service de partage Net.TCP Port qui permet le partage de ports net.tcp à travers plusieurs processus utilisateur.  
  
## <a name="background-and-motivation"></a>Contexte et motivation  
 Lorsque le protocole TCP/IP a été introduit pour la première fois, seul un petit nombre de protocoles d'application l'utilisaient. TCP/IP utilisait les numéros de port pour différencier les applications en assignant un numéro de port unique à 16 bits à chaque protocole d'application. Par exemple, le trafic HTTP d'aujourd'hui est standardisé pour utiliser le port TCP 80, le protocole SMTP utilise le port TCP 25 et le protocole FTP utilise les ports TCP 20 et 21. D'autres applications utilisant TCP comme transport peuvent choisir un autre numéro de port disponible, par convention ou par le biais d'une standardisation formelle.  
  
 L'utilisation des numéros de port pour différencier les applications posait des problèmes de sécurité. Les pare-feu sont généralement configurés pour bloquer le trafic TCP sur tous les ports à l'exception de quelques points d'entrée connus ; par conséquent, le déploiement d'une application qui utilise un port non standard est souvent compliqué voire impossible en raison de la présence de pare-feu d'entreprise et personnels. Les applications pouvant communiquer sur des ports connus standard, déjà autorisés, réduisent la zone exposée aux attaques externes. De nombreuses applications réseau utilisent le protocole HTTP parce que la plupart des pare-feu sont configurés par défaut pour autoriser le trafic sur le port TCP 80.  
  
 Le modèle HTTP.SYS dans lequel le trafic pour de nombreuses applications HTTP différentes est multiplexé sur un port TCP unique, est devenu le standard sur la plate-forme Windows. Cela fournit un point de contrôle commun aux administrateurs de pare-feu tout en permettant aux développeurs d'applications de réduire le coût de déploiement lié à la génération des nouvelles applications pouvant utiliser le réseau.  
  
 La capacité de partager des ports à travers plusieurs applications HTTP a longtemps été une fonctionnalité des services IIS (Internet Information Services). Toutefois, il était uniquement avec l’introduction de HTTP. SYS (le noyau écouteur de protocole HTTP) avec IIS 6.0, que cette infrastructure a été pleinement généralisée. D'une façon générale, HTTP.SYS permet aux processus utilisateur arbitraires de partager les ports TCP dédiés au trafic HTTP. Cette capacité permet à de nombreuses applications HTTP de coexister sur le même ordinateur physique dans des processus séparés et isolés, tout en partageant l'infrastructure réseau requise pour envoyer et recevoir le trafic sur le port TCP 80. Le Service de partage de ports Net.TCP active le même type de partage de ports pour les applications net.tcp.  
  
## <a name="port-sharing-architecture"></a>Architecture de partage de ports  
 L’architecture de partage de Port dans WCF a trois composants principaux :  
  
- Un processus de travail : Tout processus qui communique sur net.tcp:// en utilisant des ports partagés.  
  
- Le transport TCP de WCF : Implémente le protocole net.tcp://.  
  
- Le Service de partage de ports Net.TCP : Permet à plusieurs processus de travail de partager le même port TCP.  
  
 Le Service de partage de ports Net.TCP est un service Windows en mode utilisateur qui accepte les connexions net.tcp:// pour le compte des processus de travail qui se connectent à travers lui. Lorsqu'une connexion de socket arrive, le service de partage de ports inspecte le flux des message entrants pour obtenir son adresse de destination. En fonction de cette adresse, le service de partage de ports peut router le flux des données vers l'application qui finalement les traite.  
  
 Lorsqu’un service WCF qui utilise le partage s’ouvre de ports net.tcp://, l’infrastructure de transport TCP de WCF n’ouvre pas directement un socket TCP dans le processus d’application. À la place, l'infrastructure de transport enregistre l'URI (Uniform Resource Identifier) de l'adresse de base de service auprès du Service de partage de ports Net.TCP et attend que le service écoute les messages pour son compte.  Le service de partage de ports distribue des messages adressés au service de l'application quand ils arrivent.  
  
## <a name="installing-port-sharing"></a>Installation du partage de ports  
 Le Service de partage de Port Net.TCP est disponible sur tous les systèmes d’exploitation qui prennent en charge de WinFX, mais le service n’est pas activé par défaut. Comme précaution de sécurité, un administrateur doit activer manuellement le Service de partage de ports Net.TCP avant la première utilisation. Le Service de partage de ports Net.TCP expose les options de configuration qui vous permettent de manipuler plusieurs caractéristiques des sockets réseau possédés par le service de partage de ports. Pour plus d'informations, voir [Procédure : Activer le Service de partage de ports Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).  
  
## <a name="using-nettcp-port-sharing-in-an-application"></a>Utilisation du partage de ports Net.tcp dans une application  
 Le moyen le plus simple à utiliser dans votre application WCF de partage de ports net.tcp:// consiste à exposer un service à l’aide de la <xref:System.ServiceModel.NetTcpBinding> , puis d’activer le Service de partage de ports Net.TCP à l’aide de la <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> propriété.  
  
 Pour plus d’informations sur la manière de procéder, consultez [Guide pratique pour Configurer un Service WCF à utiliser le Port partage](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md).  
  
## <a name="security-implications-of-port-sharing"></a>Conséquences sur la sécurité du partage de ports  
 Bien que le Service de partage de ports Net.TCP fournisse une couche de traitement entre les applications et le réseau, les applications qui utilisent ce service doivent néanmoins être sécurisées comme si elles écoutaient directement le réseau. Spécifiquement, les applications qui utilisent le partage de ports doivent évaluer les privilèges de processus sous lesquels elles s'exécutent. Envisagez d'exécuter votre application à l'aide du compte de service réseau intégré, qui s'exécute avec le jeu minime de privilèges de processus requis pour la communication réseau.  
  
## <a name="see-also"></a>Voir aussi

- [Configuration du service de partage de ports Net.TCP](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
- [Hébergement](../../../../docs/framework/wcf/feature-details/hosting.md)
- [Guide pratique pour Configurer un Service WCF à utiliser le Port de partage](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md)
- [Guide pratique pour Activer le Service de partage de ports Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
