---
title: Hébergement dans les services IIS (Internet Information Services)
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
ms.openlocfilehash: 8563662a4408d0425e92b960301311ce5d423f9d
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025750"
---
# <a name="hosting-in-internet-information-services"></a>Hébergement dans les services IIS (Internet Information Services)
Une option pour l’hébergement des services Windows Communication Foundation (WCF) est à l’intérieur d’une application Internet Information Services (IIS). Ce modèle d’hébergement est similaire au modèle utilisé par ASP.NET et les Services Web ASP.NET (ASMX) de services Web.  
  
## <a name="versions-of-iis"></a>Versions d'IIS  
 WCF peut être hébergé sur les versions suivantes d’IIS sur les systèmes d’exploitation suivants :  
  
- IIS 5.1 sur [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]. Cet environnement est utile pour la conception et développement d'applications hébergées par IIS et déployées ultérieurement sur un système d'exploitation de serveur tel que [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
- [!INCLUDE[iis601](../../../../includes/iis601-md.md)] sur [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]. [!INCLUDE[iis601](../../../../includes/iis601-md.md)] fournit un modèle de processus avancé qui offre une évolutivité, une fiabilité et une isolation d'application améliorées. Cet environnement convient pour le déploiement de production de services WCF qui utilisent la communication HTTP exclusivement.  
  
- IIS 7.0 sur [!INCLUDE[wv](../../../../includes/wv-md.md)] et [!INCLUDE[lserver](../../../../includes/lserver-md.md)]. ISS 7.0 fournit le même modèle de processus avancé que [!INCLUDE[iis601](../../../../includes/iis601-md.md)], mais il utilise le service d'activation de processus de Windows (WAS) pour autoriser l'activation et la communication réseau sur des protocoles autres que HTTP. Cet environnement est adapté au développement de services WCF qui communiquent via des protocoles réseau pris en charge par WCF (y compris HTTP, net.tcp, net.pipe et net.msmq). Pour plus d’informations sur WAS, consultez [hébergement dans Windows Process Activation Service](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
- [Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=196496) fonctionne avec [!INCLUDE[iisver](../../../../includes/iisver-md.md)] et Service de l’Activation des processus Windows (WAS) pour fournir une environnement pour les services NET4 WCF et WF d’hébergement d’applications riches. Ces avantages incluent la gestion du cycle de vie de processus, le recyclage de processus, l'hébergement partagé, la protection rapide contre les incidents, les processus parallèles, l'activation à la demande et le contrôle d'état. Pour plus d’informations, consultez [fonctionnalités d’hébergement d’AppFabric](https://go.microsoft.com/fwlink/?LinkId=196494) et [Concepts d’hébergement AppFabric](https://go.microsoft.com/fwlink/?LinkId=196495).  
  
## <a name="benefits-of-iis-hosting"></a>Avantages de l'hébergement IIS  
 Hébergement de services WCF dans IIS présente plusieurs avantages :  
  
- Les services WCF hébergés dans IIS sont déployés et gérés comme tout autre type d’application IIS, y compris les applications ASP.NET et ASMX.  
  
- IIS assure l'activation de processus, la gestion de l'intégrité et le recyclage des fonctions afin d'accroître la fiabilité des applications hébergées.  
  
- Comme ASP.NET, les services WCF hébergés dans ASP.NET peuvent tirer parti du modèle d’hébergement partagé ASP.NET où plusieurs applications résident dans un processus de travail courants pour l’évolutivité et la densité de serveur améliorée.  
  
- Les services WCF hébergés dans IIS utilisent le même modèle de compilation dynamique comme ASP.NET 2.0, ce qui simplifie le développement et le déploiement des services hébergés.  
  
 Lorsque vous décidez d’héberger des services WCF dans IIS, il est important de se rappeler que IIS 5.1 et [!INCLUDE[iis601](../../../../includes/iis601-md.md)] sont limités à la communication HTTP uniquement. Pour plus d’informations sur le choix d’un environnement d’hébergement, consultez [Services d’hébergement](../../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="deploying-an-iis-hosted-wcf-service"></a>Déploiement d'un service WCF hébergé par IIS  
 Développement et déploiement d’un service WCF hébergé par IIS consiste à effectuer les tâches suivantes :  
  
- Vérifiez que IIS, ASP.NET, WCF et le composant d’activation HTTP WCF sont correctement installés et inscrits.  
  
- Créer une nouvelle application IIS ou réutiliser une application ASP.NET existante.  
  
- Créez un fichier .svc pour le service WCF.  
  
- Déployer l'implémentation de service vers l'application IIS.  
  
- Configurer le service WCF.  
  
 Pour une description de chacune de ces tâches, consultez [déploiement d’un Service de WCF sont](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).  
  
## <a name="wcf-services-and-aspnet"></a>Services WCF et ASP.NET  
 Les services WCF peuvent être hébergés soit côte-à-côte avec ASP.NET ou en Mode de compatibilité ASP.NET dans lequel les services peuvent profiter pleinement des fonctionnalités fournies par la plate-forme d’application Web ASP.NET. Pour une description de ces fonctionnalités, consultez [Services WCF et ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
## <a name="see-also"></a>Voir aussi

- [Extension de l’hébergement à l’aide de ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)
- [Déploiement d’un service WCF hébergé dans Internet Information Services](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)
- [Services WCF et ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [Bonnes pratiques pour l’hébergement dans Internet Information Services](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
- [Configuration des services Internet Information Services 7.0 pour Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/configuring-iis-for-wcf.md)
- [Fonctionnalités d’hébergement de Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=201276)
