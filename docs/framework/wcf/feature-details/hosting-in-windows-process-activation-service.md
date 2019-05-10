---
title: Hébergement dans le service d'activation de processus de Windows (WAS, Windows Process Activation Service)
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], WAS
ms.assetid: d2b9d226-15b7-41fc-8c9a-cb651ac20ecd
ms.openlocfilehash: baa931b64e64c9c2f73ac07424b2cfd1868e725b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613292"
---
# <a name="hosting-in-windows-process-activation-service"></a>Hébergement dans le service d'activation de processus de Windows (WAS, Windows Process Activation Service)
Le Service de l’Activation des processus Windows (WAS) gère l’activation et la durée de vie du processus de travail qui contiennent des applications à héberger des services de Windows Communication Foundation (WCF). Le modèle de processus WAS généralise le modèle de processus [!INCLUDE[iis601](../../../../includes/iis601-md.md)] pour le serveur HTTP en supprimant la dépendance envers le protocole HTTP. Ainsi, les services WCF à utiliser les protocoles HTTP et non-HTTP, tel que Net.TCP, dans un environnement d’hébergement qui prend en charge l’activation basée sur le message et offre la possibilité d’héberger un grand nombre d’applications sur un ordinateur donné.  
  
 Pour plus d’informations sur la création d’un service WCF qui s’exécute dans l’environnement d’hébergement WAS, consultez [Comment : Héberger un Service WCF dans WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
 Le modèle de processus WAS fournit plusieurs fonctionnalités qui permettent aux applications d’être hébergées de façon plus fiable, plus maniable et plus efficace au niveau de l’utilisation des ressources :  
  
- L’activation basée sur message des applications et les applications de processus de travail démarrent et s’arrêtent dynamiquement en réponse aux éléments de travail entrants qui arrivent, via des protocoles réseau HTTP et non-HTTP.  
  
- Application fiable et recyclage des processus de travail pour maintenir l'intégrité de l'exécution d'applications.  
  
- Configuration et gestion centralisées de l'application.  
  
- Permet aux applications de tirer parti du modèle de processus IIS sans requérir d'espace mémoire pour le déploiement d'une installation IIS complète.  
  
 Pour plus d’informations sur les fonctionnalités WAS, consultez [IIS 7.0 Beta : IIS 7.0 Web Administration](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
 [Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=196496) fonctionne avec [!INCLUDE[iisver](../../../../includes/iisver-md.md)] et Service de l’Activation des processus Windows (WAS) pour fournir une environnement pour les services NET4 WCF et WF d’hébergement d’applications riches. Ces avantages incluent la gestion du cycle de vie de processus, le recyclage de processus, l'hébergement partagé, la protection rapide contre les incidents, les processus parallèles, l'activation à la demande et le contrôle d'état. Pour plus d’informations, consultez [fonctionnalités d’hébergement d’AppFabric](https://go.microsoft.com/fwlink/?LinkId=196494) et [Concepts d’hébergement AppFabric](https://go.microsoft.com/fwlink/?LinkId=196495).  
  
## <a name="elements-of-the-was-addressing-model"></a>Éléments du modèle d'adressage WAS  
 Les applications ont des adresses d'URI (Uniform Resource Identifier) qui sont en fait des unités de code dont la durée de vie et l'environnement d'exécution sont gérés par le serveur. Une instance de serveur WAS unique peut loger de nombreuses applications différentes. Serveurs organisent les applications en groupes appelés *sites*. Dans un site, les applications sont réorganisées d'une façon hiérarchique reflétant la structure des URI qui servent d'adresses externes.  
  
 Les adresses d’application se composent de deux parties : un préfixe URI de base et une adresse relative spécifique à l’application (chemin d’accès) qui fournit l’adresse externe pour une application en cas d’association. Le préfixe URI de base est construit à partir de la liaison du site et est utilisé pour toutes les applications sous le site. Adresses d’application sont ensuite créées en prenant des fragments de chemin d’accès spécifique à l’application (par exemple, « / /applicationone ») et en les ajoutant au préfixe URI de base (par exemple, « NET.TCP://localhost ») pour arriver à l’URI d’application complète.  
  
 Le tableau suivant illustre plusieurs scénarios d'adressage possibles pour les sites WAS avec des liaisons de site HTTP et non-HTTP.  
  
|Scénario|Liaisons de site|Chemin d’application|URI d'application de base|  
|--------------|-------------------|----------------------|---------------------------|  
|HTTP uniquement|http : * : 80 :\*|/appTwo|http://localhost/appTwo/|  
|À la fois HTTP et non-HTTP|http : * : 80 :\*<br /><br /> net.tcp: 808:\*|/appTwo|http://localhost/appTwo/<br />net.tcp://localhost/appTwo/|  
|Non-HTTP uniquement|net.pipe: *|/appThree|net.pipe://appThree/|  
  
 Les services et les ressources dans une application peuvent également être adressés. Dans une application, les ressources d'application sont adressées relativement au chemin d'accès d'application de base. Par exemple, supposez qu'un site sur un nom d'ordinateur contoso.com aie des liaisons de site pour les protocoles HTTP et Net.TCP à la fois. Supposez également que le site contienne une application située dans /Billing, qui expose un service à GetOrders.svc. Dans ce cas, si le service GetOrders.svc a exposé un point de terminaison avec une adresse relative de SecureEndpoint, le point de terminaison du service est exposé aux deux URI suivants :  
  
- `http://contoso.com/Billing/GetOrders.svc/SecureEndpoint`
- `net.tcp://contoso.com/Billing/GetOrders.svc/SecureEndpoint`
  
## <a name="the-was-runtime"></a>Exécution WAS  
 Les applications sont organisées en sites pour les besoins d'adressage et de gestion. Au moment de l'exécution, les applications sont également groupées ensemble dans des pools d'applications. Un pool d'applications peut loger de nombreuses applications différentes à partir de nombreux sites différents. Toutes les applications à l'intérieur d'un pool d'applications partagent un jeu commun de caractéristiques d'exécution. Par exemple, elles s'exécutent toutes sous la même version CRL (Common Language Runtime) et elles partagent toutes une identité de processus commune. Chaque pool d'applications correspond à une instance d'un processus de travail (w3wp.exe). Chaque application gérée qui s'exécute dans un pool d'applications partagé est isolée des autres applications au moyen d'un AppDomain CLR.  
  
## <a name="see-also"></a>Voir aussi

- [Architecture d’activation WAS](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)
- [Configuration du service WAS pour une utilisation avec WCF](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [Guide pratique pour Installer et configurer les composants d’Activation WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)
- [Guide pratique pour Héberger un Service WCF dans WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)
- [Fonctionnalités d’hébergement de Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=201276)
