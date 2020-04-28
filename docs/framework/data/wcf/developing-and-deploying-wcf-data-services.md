---
title: Développer et déployer WCF Data Services
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- deploying [WCF Data Services
- developing applications [WCF Data Services]
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
ms.openlocfilehash: 1dc9f3d261738a6dff0339c094c7aba5e32680ee
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200052"
---
# <a name="develop-and-deploy-wcf-data-services"></a>Développez et déployez des WCF Data Services

Cet article fournit des informations sur le développement et le déploiement de WCF Data Services. Pour plus d’informations sur les WCF Data Services, consultez [prise en main](getting-started-with-wcf-data-services.md) et [vue d’ensemble](wcf-data-services-overview.md).

## <a name="develop-wcf-data-services"></a>Développez WCF Data Services

Lorsque vous utilisez WCF Data Services pour créer un service de données qui prend en charge le Open Data Protocol (OData), vous devez effectuer les tâches de base suivantes lors du développement :

1. **Définir le modèle de données**

     WCF Data Services prend en charge un large éventail de fournisseurs de services de données qui vous permettent de définir un modèle de données basé sur des données provenant de diverses sources de données, des bases de données relationnelles aux types de données à liaison tardive. Pour plus d’informations, consultez [Data Services des fournisseurs](data-services-providers-wcf-data-services.md).

2. **Créer le service de données**

     Le service de données le plus basique expose une classe qui hérite de la classe <xref:System.Data.Services.DataService%601> , avec un type `T` qui est le nom qualifié par l'espace de noms du conteneur d'entités. Pour plus d'informations, consultez [Defining WCF Data Services](defining-wcf-data-services.md).

3. **Configurer le service de données**

     Par défaut, WCF Data Services désactive l’accès aux ressources exposées par un conteneur d’entités. L' <xref:System.Data.Services.DataServiceConfiguration> interface vous permet de configurer l’accès aux ressources et aux opérations de service, de spécifier la version prise en charge d’OData et de définir d’autres comportements à l’ensemble du service, tels que les comportements de traitement par lot ou le nombre maximal d’entités qui peuvent être retournées dans un flux de réponse unique. Pour plus d’informations, consultez [configuration du service de données](configuring-the-data-service-wcf-data-services.md).

Cet article traite principalement du développement et du déploiement de services de données à l’aide de Visual Studio. Pour plus d’informations sur la flexibilité offerte par WCF Data Services pour exposer vos données en tant que flux OData, consultez [définition d’WCF Data Services](defining-wcf-data-services.md).

### <a name="choose-a-development-web-server"></a>Choisir un serveur Web de développement

Lorsque vous développez un service de données WCF comme une application ASP.NET ou un site Web ASP.NET à l’aide de Visual Studio 2015, vous avez le choix entre plusieurs serveurs Web sur lesquels exécuter le service de données pendant le développement. Les serveurs Web suivants s’intègrent à Visual Studio pour faciliter le test et le débogage de vos services de données sur l’ordinateur local.

1. **Serveur IIS local**

     Lorsque vous créez un service de données qui est une application ASP.NET ou un site Web ASP.NET qui s’exécute sur Internet Information Services (IIS), nous vous recommandons de développer et de tester votre service de données à l’aide d’IIS sur l’ordinateur local. L'exécution du service de données sur IIS facilite le suivi des demandes HTTP pendant le débogage. Cela vous permet également de prédéterminer les droits nécessaires à IIS pour accéder aux fichiers, aux bases de données et aux autres ressources requis par le service de données. Pour exécuter votre service de données sur IIS, assurez-vous qu’IIS et Windows Communication Foundation (WCF) sont installés et configurés correctement et accordez l’accès aux comptes IIS dans le système de fichiers et les bases de données. Pour plus d'informations, consultez [How to: Develop a WCF Data Service Running on IIS](how-to-develop-a-wcf-data-service-running-on-iis.md).

    > [!NOTE]
    > Vous devez exécuter Visual Studio avec des droits d’administrateur pour permettre à l’environnement de développement de configurer le serveur IIS local.

2. **Serveur de développement Visual Studio**

     Visual Studio comprend un serveur Web intégré, le Serveur Visual Studio Development, qui est le serveur Web par défaut pour les projets ASP.NET. Ce serveur Web est conçu pour exécuter des projets ASP.NET sur l’ordinateur local pendant le développement. Le Guide de [démarrage rapide WCF Data Services](quickstart-wcf-data-services.md) montre comment créer un service de données qui s’exécute dans le serveur Visual Studio Development.

     Tenez compte des limitations suivantes lorsque vous utilisez l’Serveur Visual Studio Development pour développer le service de données :

    - Ce serveur est uniquement accessible sur l'ordinateur local.

    - Ce serveur écoute sur `localhost` et sur un port spécifique, non sur le port 80, qui est le port par défaut des messages HTTP. Pour plus d'informations, voir [Serveurs web dans Visual Studio pour les projets web ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/58wxa9w5(v=vs.120)).

    - Ce serveur exécute le service de données dans le contexte de votre compte utilisateur actuel. Par exemple, si vous exécutez en tant qu’utilisateur de niveau administrateur, un service de données qui s’exécute dans le Serveur Visual Studio Development aura des privilèges de niveau administrateur. Par conséquent, le service de données pourra accéder à des ressources pour lesquelles il ne possède pas de droits d'accès si déployé sur un serveur IIS.

    - Ce serveur n'inclut pas les fonctionnalités supplémentaires d'IIS, telles que l'authentification.

    - Ce serveur ne peut pas gérer les flux HTTP en bloc, qui sont envoyés par défaut par le client WCF Data Services lors de l’accès à des données binaires volumineuses à partir du service de données. Pour plus d’informations, consultez la page [fournisseur de streaming](streaming-provider-wcf-data-services.md).

    - Ce serveur a des problèmes de traitement du caractère`.`point () dans une URL, même si ce caractère est pris en charge par WCF Data Services dans les valeurs de clés.

    > [!TIP]
    > Même si vous pouvez utiliser la Serveur Visual Studio Development pour tester vos services de données pendant le développement, vous devez les tester à nouveau après le déploiement sur un serveur Web qui exécute IIS.

3. **Environnement de développement Azure**

     Azure Tools pour Visual Studio comprend un ensemble intégré d’outils pour le développement de services Azure dans Visual Studio. Grâce à ces outils, vous pouvez développer un service de données qui peut être déployé sur Azure, et vous pouvez tester le service de données sur l’ordinateur local avant le déploiement. Utilisez ces outils lorsque vous utilisez Visual Studio pour développer un service de données qui s’exécute sur la plateforme Azure. Pour plus d’informations sur l’installation des outils, consultez [Azure Tools pour Visual Studio 2015](../../../azure/sdk/vs2015-install.md). Pour plus d’informations sur le développement d’un service de données qui s’exécute sur Azure, consultez la publication [déploiement d’un service OData dans Azure](https://docs.microsoft.com/archive/blogs/astoriateam/deploying-an-odata-service-in-windows-azure).

### <a name="development-tips"></a>Conseils de développement

Lorsque vous développez un service de données, tenez compte des points suivants :

- Si vous envisagez d’authentifier les utilisateurs ou de restreindre l’accès pour des utilisateurs spécifiques, déterminez les exigences de sécurité de votre service de données. Pour plus d'informations, consultez [Securing WCF Data Services](securing-wcf-data-services.md).

- Un programme d’inspection HTTP peut être utile lors du débogage d’un service de données en vous permettant d’inspecter le contenu des messages de demande et de réponse. N'importe quel analyseur de paquets réseau en mesure d'afficher des paquets bruts peut être utilisé pour inspecter des demandes et des réponses HTTP à partir du service de données.

- Lors du débogage d’un service de données, vous souhaiterez peut-être obtenir plus d’informations sur une erreur du service de données qu’au cours d’opérations normales. Pour obtenir davantage d'informations sur l'erreur à partir du service de données, affectez à la propriété <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> dans <xref:System.Data.Services.DataServiceConfiguration> la valeur `true` et affectez à la propriété <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> de l'attribut <xref:System.ServiceModel.Description.ServiceDebugBehavior> sur la classe de service de données la valeur `true`. Pour plus d’informations, consultez le [WCF Data Services de débogage](https://docs.microsoft.com/archive/blogs/phaniraj/debugging-wcf-data-services)de publication. Vous pouvez également activer le suivi dans WCF pour afficher les exceptions levées dans la couche de messagerie HTTP. Pour plus d'informations, consultez [Configuring Tracing](../../wcf/diagnostics/tracing/configuring-tracing.md).

- Un service de données est généralement développé comme un projet d’application ASP.NET, mais vous pouvez également créer un service de données en tant que projet de site Web ASP.NET dans Visual Studio. Pour plus d’informations sur les différences entre les deux types de projets, consultez [projets d’application Web et projets de site Web dans Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd547590(v=vs.110)).

- Lorsque vous créez un service de données à l’aide de la boîte de dialogue **Ajouter un nouvel élément** dans Visual Studio, le service de données est hébergé par ASP.net dans IIS. Alors que ASP.NET et IIS sont l’hôte par défaut pour un service de données, les autres options d’hébergement sont prises en charge. Pour plus d’informations, consultez [hébergement du service de données](hosting-the-data-service-wcf-data-services.md).

## <a name="deploy-wcf-data-services"></a>Déployer WCF Data Services

WCF Data Service permet de choisir le processus qui héberge le service de données. Vous pouvez utiliser Visual Studio pour déployer un service de données sur les plateformes suivantes :

- **Serveur Web hébergé par IIS**

    Lorsqu’un service de données est développé en tant que projet ASP.NET, il peut être déployé sur un serveur Web IIS à l’aide des processus de déploiement ASP.NET standard. Visual Studio fournit les technologies de déploiement suivantes pour ASP.NET, selon le type de projet ASP.NET qui héberge le service de données que vous déployez.

  - **Technologies de déploiement des applications Web ASP.NET**

    - [Comment : créer un package de déploiement Web dans Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd465323(v=vs.110))

    - [Comment : déployer un projet Web à l’aide de la publication en un clic dans Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd465337(v=vs.110))

  - **Technologies de déploiement des sites Web ASP.NET**

    - [Comment : copier des fichiers de site Web avec l’outil Copier le site Web](https://docs.microsoft.com/previous-versions/aspnet/c95809c0(v=vs.100))

    - [Comment : publier des sites Web](https://docs.microsoft.com/previous-versions/aspnet/20yh9f1b(v=vs.100))

    - [Procédure pas à pas : déploiement d’une application Web ASP.NET à l’aide de XCOPY](https://docs.microsoft.com/previous-versions/aspnet/f735abw9(v=vs.100))

     Pour plus d’informations sur les options de déploiement pour une application ASP.NET, consultez [vue d’ensemble du déploiement Web pour Visual Studio et ASP.net](https://docs.microsoft.com/previous-versions/aspnet/dd394698(v=vs.110)).

    > [!TIP]
    > Avant de tenter de déployer le service de données sur IIS, testez le déploiement sur un serveur Web qui exécute IIS. Pour plus d'informations, consultez [How to: Develop a WCF Data Service Running on IIS](how-to-develop-a-wcf-data-service-running-on-iis.md).

- **Azure**

     Vous pouvez déployer un service de données sur Azure à l’aide d' [Azure Tools pour Visual Studio](../../../azure/sdk/vs2015-install.md). Pour plus d’informations sur le déploiement d’un service de données sur Azure, consultez [déploiement d’un service OData dans Azure](https://docs.microsoft.com/archive/blogs/astoriateam/deploying-an-odata-service-in-windows-azure).

### <a name="deployment-considerations"></a>Points à prendre en considération pour le déploiement

Tenez compte des éléments suivants lors du déploiement d’un service de données :

- Lorsque vous déployez un service de données qui utilise le fournisseur de Entity Framework pour accéder à une base de données SQL Server, vous devrez peut-être également propager des structures de données, des données, ou les deux avec votre déploiement de service de données. Visual Studio peut créer automatiquement des scripts (fichiers. Sql) pour effectuer cette opération dans la base de données de destination, et ces scripts peuvent être inclus dans le package de déploiement Web d’une application ASP.NET. Pour plus d’informations, consultez [Comment : déployer une base de données avec un projet d’application Web](https://docs.microsoft.com/previous-versions/dd465343(v=vs.100)). Pour un site Web ASP.NET, vous pouvez le faire à l’aide de l' **Assistant Publication de base de données** dans Visual Studio. Pour plus d’informations, consultez [publication d’un SQL Database](https://docs.microsoft.com/previous-versions/aspnet/bb907585(v=vs.100)).

- Étant donné que WCF Data Services comprend une implémentation WCF de base, vous pouvez utiliser Windows Server AppFabric pour surveiller un service de données déployé sur IIS exécuté sur Windows Server. Pour plus d’informations sur l’utilisation de Windows Server AppFabric pour surveiller un service de données, consultez le [WCF Data Services de suivi de la publication avec Windows Server AppFabric](https://docs.microsoft.com/archive/blogs/rjacobs/tracking-wcf-data-services-with-windows-server-appfabric).

## <a name="see-also"></a>Voir aussi

- [Hébergement du service de données](hosting-the-data-service-wcf-data-services.md)
- [Securing WCF Data Services](securing-wcf-data-services.md)
- [Définition des services de données WCF](defining-wcf-data-services.md)
