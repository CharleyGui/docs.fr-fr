---
title: Hébergement dans les services IIS (Internet Information Services)
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
ms.openlocfilehash: 2e0fb579897797b732859692092665225a0d6168
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76919354"
---
# <a name="host-in-internet-information-services"></a>Héberger dans Internet Information Services

L’une des options d’hébergement des services Windows Communication Foundation (WCF) se trouve à l’intérieur d’une application Internet Information Services (IIS). Ce modèle d’hébergement est similaire au modèle utilisé par les services Web des services Web ASP.NET et ASP.NET (ASMX).

## <a name="versions-of-iis"></a>Versions d'IIS

WCF peut être hébergé sur les versions suivantes d’IIS sur les systèmes d’exploitation suivants :

- IIS 5,1 sur Windows XP SP2. Cet environnement est utile pour la conception et le développement d’applications hébergées par IIS qui sont ensuite déployées sur un système d’exploitation serveur tel que Windows Server 2003.

- IIS 6.0 sous Windows Server 2003. IIS 6.0 inclut un modèle de processus avancé qui améliore l'évolutivité, la fiabilité et l'isolement des applications. Cet environnement convient au déploiement de production de services WCF qui utilisent la communication HTTP exclusivement.

- IIS 7.0 sous Windows Vista et Windows Server 2008. IIS 7,0 fournit le même modèle de processus avancé qu’IIS 6,0, mais utilise le service d’activation des processus Windows (WAS) pour permettre l’activation et la communication réseau via des protocoles autres que HTTP. Cet environnement est adapté au développement de services WCF qui communiquent sur tout protocole réseau pris en charge par WCF (y compris HTTP, net. TCP, net. pipe et net. MSMQ). Pour plus d’informations sur WAS, consultez [hébergement dans le service d’activation des processus Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).

- [Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff384253(v=azure.10)) fonctionne avec IIS 7,0 et le service d’activation des processus Windows (was) pour fournir un environnement d’hébergement d’applications riche pour les services WCF et WF NET4. Ces avantages incluent la gestion du cycle de vie de processus, le recyclage de processus, l'hébergement partagé, la protection rapide contre les incidents, les processus parallèles, l'activation à la demande et le contrôle d'état. Pour plus d’informations, consultez [fonctionnalités d’hébergement AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10)) et [concepts d’hébergement AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677371(v=azure.10)).

## <a name="benefits-of-iis-hosting"></a>Avantages de l’hébergement IIS

L’hébergement des services WCF dans IIS présente plusieurs avantages :

- Les services WCF hébergés dans IIS sont déployés et gérés comme n’importe quel autre type d’application IIS, y compris les applications ASP.NET et ASMX.

- IIS assure l'activation de processus, la gestion de l'intégrité et le recyclage des fonctions afin d'accroître la fiabilité des applications hébergées.

- Comme ASP.NET, les services WCF hébergés dans ASP.NET peuvent tirer parti du modèle d’hébergement partagé ASP.NET dans lequel plusieurs applications résident dans un processus de travail courant pour améliorer la densité du serveur et l’évolutivité.

- Les services WCF hébergés dans IIS utilisent le même modèle de compilation dynamique que ASP.NET 2,0, ce qui simplifie le développement et le déploiement des services hébergés.

Lorsque vous décidez d’héberger des services WCF dans IIS, il est important de se souvenir que IIS 5,1 et IIS 6,0 sont limités à la communication HTTP uniquement. Pour plus d’informations sur le choix d’un environnement d’hébergement, consultez [services d’hébergement](../../../../docs/framework/wcf/hosting-services.md).

## <a name="deploy-an-iis-hosted-wcf-service"></a>Déployer un service WCF hébergé par IIS

Le développement et le déploiement d’un service WCF hébergé par IIS se composent des tâches suivantes :

- Assurez-vous qu’IIS, ASP.NET, WCF et le composant d’activation HTTP WCF sont correctement installés et inscrits.

- Créer une application IIS ou réutiliser une application ASP.NET existante.

- Créez un fichier. svc pour le service WCF.

- Déployer l'implémentation de service vers l'application IIS.

- Configurez le service WCF.

Pour une description de chacune de ces tâches, consultez [déploiement d’un service WCF hébergé par Internet Information Services](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).

## <a name="wcf-services-and-aspnet"></a>Services WCF et ASP.NET

Les services WCF peuvent être hébergés côte à côte avec ASP.NET ou en mode de compatibilité ASP.NET, dans lequel les services peuvent tirer pleinement parti des fonctionnalités fournies par la plateforme d’application Web ASP.NET. Pour plus d’informations sur ces fonctionnalités, consultez [services WCF et ASP.net](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).

## <a name="see-also"></a>Voir aussi

- [Extension de l’hébergement à l’aide de ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)
- [Déploiement d’un service WCF hébergé dans Internet Information Services](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)
- [Services WCF et ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [Bonnes pratiques pour l’hébergement dans Internet Information Services](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
- [Configuration des services Internet Information Services 7.0 pour Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/configuring-iis-for-wcf.md)
- [Fonctionnalités d’hébergement de Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
