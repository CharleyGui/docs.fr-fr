---
title: Développer et déployer WCF Data Services
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- deploying [WCF Data Services
- developing applications [WCF Data Services]
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
ms.openlocfilehash: 4591175da5078a194bfe69884701e5432a0c38a3
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389730"
---
# <a name="develop-and-deploy-wcf-data-services"></a>Développer et déployer des services de données WCF

Cet article fournit des informations sur l’élaboration et le déploiement de WCF Data Services. Pour plus d’informations de base sur les services de données WCF, voir [Getting Started](getting-started-with-wcf-data-services.md) et [Aperçu](wcf-data-services-overview.md).

## <a name="develop-wcf-data-services"></a>Développer des services de données WCF

Lorsque vous utilisez WCF Data Services pour créer un service de données qui prend en charge le protocole de données ouvertes (OData), vous devez effectuer les tâches de base suivantes pendant le développement :

1. **Définir le modèle de données**

     WCF Data Services prend en charge une variété de fournisseurs de services de données qui vous permettent de définir un modèle de données basé sur les données provenant de diverses sources de données, des bases de données relationnelles aux types de données en retard. Pour plus d’informations, voir [Fournisseurs de services de données](data-services-providers-wcf-data-services.md).

2. **Créer le service de données**

     Le service de données le plus basique expose une classe qui hérite de la classe <xref:System.Data.Services.DataService%601> , avec un type `T` qui est le nom qualifié par l'espace de noms du conteneur d'entités. Pour plus d'informations, consultez [Defining WCF Data Services](defining-wcf-data-services.md).

3. **Configurer le service de données**

     Par défaut, WCF Data Services désactive l’accès aux ressources exposées par un conteneur d’entités. L’interface <xref:System.Data.Services.DataServiceConfiguration> vous permet de configurer l’accès aux ressources et aux opérations de service, de spécifier la version prise en charge d’OData et de définir d’autres comportements à l’échelle du service, tels que les comportements de lotage ou le nombre maximum d’entités qui peuvent être retournées dans un flux de réponse unique. Pour plus d’informations, voir [Configuring the Data Service](configuring-the-data-service-wcf-data-services.md).

Cet article couvre principalement le développement et le déploiement de services de données en utilisant Visual Studio. Pour plus d’informations sur la flexibilité fournie par WCF Data Services pour exposer vos données sous forme d’aliments OData, voir [Définir WCF Data Services](defining-wcf-data-services.md).

### <a name="choose-a-development-web-server"></a>Choisissez un serveur Web de développement

Lorsque vous développez un service de données WCF en tant qu’application ASP.NET ou ASP.NET site Web en utilisant Visual Studio 2015, vous avez le choix des serveurs Web sur lesquels exécuter le service de données pendant le développement. Les serveurs Web suivants s’intègrent à Visual Studio pour faciliter le test et le débogé de vos services de données sur l’ordinateur local.

1. **Serveur IIS local**

     Lorsque vous créez un service de données qui est une application ASP.NET ou ASP.NET site Web qui s’exécute sur les services d’information Internet (IIS), nous vous recommandons de développer et de tester votre service de données en utilisant l’IIS sur l’ordinateur local. L'exécution du service de données sur IIS facilite le suivi des demandes HTTP pendant le débogage. Elle permet également de prédéfinir les droits requis par IIS pour accéder aux fichiers, aux bases de données et aux autres ressources requises par le service de données. Pour exécuter votre service de données sur l’IIS, assurez-vous que l’IIS et windows Communication Foundation (WCF) sont installés et configurés correctement et accordez l’accès aux comptes IIS dans le système de fichiers et les bases de données. Pour plus d'informations, consultez [How to: Develop a WCF Data Service Running on IIS](how-to-develop-a-wcf-data-service-running-on-iis.md).

    > [!NOTE]
    > Vous devez exécuter Visual Studio avec les droits d’administrateur pour permettre à l’environnement de développement de configurer le serveur IIS local.

2. **Serveur de développement Visual Studio**

     Visual Studio comprend un serveur Web intégré, le Visual Studio Development Server, qui est le serveur Web par défaut pour ASP.NET projets. Ce serveur Web est conçu pour exécuter ASP.NET projets sur l’ordinateur local pendant le développement. Le [quickstart de WCF Data Services](quickstart-wcf-data-services.md) montre comment créer un service de données qui s’exécute dans le serveur de développement de studio visuel.

     Vous devez être conscient des limites suivantes lorsque vous utilisez le serveur de développement visual studio pour développer le service de données :

    - Ce serveur est uniquement accessible sur l'ordinateur local.

    - Ce serveur écoute sur `localhost` et sur un port spécifique, non sur le port 80, qui est le port par défaut des messages HTTP. Pour plus d'informations, voir [Serveurs web dans Visual Studio pour les projets web ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/58wxa9w5(v=vs.120)).

    - Ce serveur exécute le service de données dans le contexte de votre compte utilisateur actuel. Par exemple, si vous exécutez en tant qu’utilisateur au niveau de l’administrateur, un service de données fonctionnant dans le serveur de développement visual studio aura des privilèges au niveau de l’administrateur. Par conséquent, le service de données pourra accéder à des ressources pour lesquelles il ne possède pas de droits d'accès si déployé sur un serveur IIS.

    - Ce serveur n'inclut pas les fonctionnalités supplémentaires d'IIS, telles que l'authentification.

    - Ce serveur ne peut pas gérer les flux HTTP en morceaux, qui sont envoyés par défaut par le client WCF Data Services lors de l’accès à de grandes données binaires à partir du service de données. Pour plus d’informations, voir [Streaming Provider](streaming-provider-wcf-data-services.md).

    - Ce serveur a des problèmes`.`avec le traitement de la période ( ) caractère dans une URL, même si ce personnage est pris en charge par WCF Data Services dans les valeurs clés.

    > [!TIP]
    > Même si vous pouvez utiliser le serveur de développement visual studio pour tester vos services de données pendant le développement, vous devez les tester à nouveau après déploiement sur un serveur Web qui est en cours d’exécution IIS.

3. **Environnement de développement Microsoft Azure**

     Windows Azure Tools for Visual Studio comprend un ensemble intégré d’outils pour développer les services Windows Azure dans Visual Studio. Avec ces outils, vous pouvez développer un service de données pouvant être déployé sur Microsoft Azure, et vous pouvez le tester sur l'ordinateur local avant son déploiement. Utilisez ces outils lorsque vous utilisez Visual Studio pour développer un service de données qui s’exécute sur la plate-forme Windows Azure. Pour plus d’informations sur l’installation des outils, voir [outils Azure pour Visual Studio 2015](../../../azure/sdk/vs2015-install.md). Pour plus d’informations sur le développement d’un service de données qui s’exécute sur Windows Azure, voir le post [Déployer un service OData dans Windows Azure](https://docs.microsoft.com/archive/blogs/astoriateam/deploying-an-odata-service-in-windows-azure).

### <a name="development-tips"></a>Conseils de développement

Considérez ce qui suit lorsque vous développez un service de données :

- Si vous prévoyez d’authentifier les utilisateurs ou de restreindre l’accès pour des utilisateurs spécifiques, déterminez les exigences de sécurité de votre service de données. Pour plus d'informations, consultez [Securing WCF Data Services](securing-wcf-data-services.md).

- Un programme d’inspection HTTP peut être utile lors de la débogage d’un service de données en vous permettant d’inspecter le contenu des messages de demande et de réponse. N'importe quel analyseur de paquets réseau en mesure d'afficher des paquets bruts peut être utilisé pour inspecter des demandes et des réponses HTTP à partir du service de données.

- Lorsque vous débogiez un service de données, vous pouvez obtenir plus d’informations sur une erreur du service de données que lors d’une opération régulière. Pour obtenir davantage d'informations sur l'erreur à partir du service de données, affectez à la propriété <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> dans <xref:System.Data.Services.DataServiceConfiguration> la valeur `true` et affectez à la propriété <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> de l'attribut <xref:System.ServiceModel.Description.ServiceDebugBehavior> sur la classe de service de données la valeur `true`. Pour plus d’informations, voir le post [Debugging WCF Data Services](https://docs.microsoft.com/archive/blogs/phaniraj/debugging-wcf-data-services). Vous pouvez également activer le traçage dans WCF pour afficher les exceptions soulevées dans la couche de messagerie HTTP. Pour plus d'informations, consultez [Configuring Tracing](../../wcf/diagnostics/tracing/configuring-tracing.md).

- Un service de données est généralement développé comme un projet d’application ASP.NET, mais vous pouvez également créer votre service de données comme un projet de site Web ASP.NET dans Visual Studio. Pour plus d’informations sur les différences entre les deux types de projets, consultez [Web Les projets d’applications Web par rapport aux projets de sites Web dans Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd547590(v=vs.110)).

- Lorsque vous créez un service de données en utilisant la boîte de dialogue **Add New Item** dans Visual Studio, le service de données est hébergé par ASP.NET dans IIS. Bien que ASP.NET et IIS soit l’hôte par défaut d’un service de données, d’autres options d’hébergement sont prises en charge. Pour plus d’informations, voir [Hébergement du service de données](hosting-the-data-service-wcf-data-services.md).

## <a name="deploy-wcf-data-services"></a>Déployer WCF Data Services

WCF Data Service permet de choisir le processus qui héberge le service de données. Vous pouvez utiliser Visual Studio pour déployer un service de données sur les plates-formes suivantes :

- **Serveur Web hébergé par IIS**

    Lorsqu’un service de données est développé en tant que projet ASP.NET, il peut être déployé sur un serveur Web DE l’IIS en utilisant les processus de déploiement ASP.NET standard.  Visual Studio fournit les technologies de déploiement suivantes pour ASP.NET, en fonction du type de projet ASP.NET qui héberge le service de données que vous déployez.

  - **Technologies de déploiement des applications Web ASP.NET**

    - [Comment : créer un package de déploiement Web dans Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd465323(v=vs.110))

    - [Comment : Déployer un projet Web à l’aide d’un seul clic Publier dans Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd465337(v=vs.110))

  - **Technologies de déploiement des sites Web ASP.NET**

    - [Comment : Copier les fichiers du site Web avec l’outil de site Web Copy](https://docs.microsoft.com/previous-versions/aspnet/c95809c0(v=vs.100))

    - [Comment : Publier des sites Web](https://docs.microsoft.com/previous-versions/aspnet/20yh9f1b(v=vs.100))

    - [Procédure pas à pas : Déploiement d’une application Web ASP.NET à l’aide de XCOPY](https://docs.microsoft.com/previous-versions/aspnet/f735abw9(v=vs.100))

     Pour plus d’informations sur les options de déploiement d’une application ASP.NET, consultez [l’aperçu du déploiement Web pour Visual Studio et ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/dd394698(v=vs.110)).

    > [!TIP]
    > Avant de tenter de déployer le service de données sur IIS, testez le déploiement sur un serveur Web qui exécute IIS. Pour plus d'informations, consultez [How to: Develop a WCF Data Service Running on IIS](how-to-develop-a-wcf-data-service-running-on-iis.md).

- **Windows Azure**

     Vous pouvez déployer un service de données vers Windows Azure en utilisant Windows Azure Tools pour Visual Studio. Vous pouvez télécharger les outils Windows Azure pour Visual Studio à partir du [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkID=201848). Pour plus d’informations sur le déploiement d’un service de données sur Windows Azure, voir le post [Déployer un service OData dans Windows Azure](https://docs.microsoft.com/archive/blogs/astoriateam/deploying-an-odata-service-in-windows-azure).

### <a name="deployment-considerations"></a>Points à prendre en considération pour le déploiement

Considérez ce qui suit lors du déploiement d’un service de données :

- Lorsque vous déployez un service de données qui utilise le fournisseur De cadre d’entité pour accéder à une base de données SQL Server, vous devrez peut-être également propager des structures de données, des données ou les deux avec le déploiement de votre service de données. Visual Studio peut créer automatiquement des scripts (.fichiers sql) pour ce faire dans la base de données de destination, et ces scripts peuvent être inclus dans le paquet de déploiement Web d’une application ASP.NET. Pour plus d’informations, voir [Comment : Déployer une base de données avec un projet d’application Web](https://docs.microsoft.com/previous-versions/dd465343(v=vs.100)). Pour un site Web ASP.NET, vous pouvez le faire en utilisant le **Database Publishing Wizard** dans Visual Studio. Pour plus d’informations, voir [Publier une base de données SQL](https://docs.microsoft.com/previous-versions/aspnet/bb907585(v=vs.100)).

- Étant donné que WCF Data Services inclut une implémentation WCF de base, vous pouvez utiliser Windows Server AppFabric pour surveiller un service de données déployé sur IIS fonctionnant sur Windows Server. Pour plus d’informations sur l’utilisation de Windows Server AppFabric pour surveiller un service de données, voir le post [Tracking WCF Data Services avec Windows Server AppFabric](https://docs.microsoft.com/archive/blogs/rjacobs/tracking-wcf-data-services-with-windows-server-appfabric).

## <a name="see-also"></a>Voir aussi

- [Hébergement du service de données](hosting-the-data-service-wcf-data-services.md)
- [Securing WCF Data Services](securing-wcf-data-services.md)
- [Définition des services de données WCF](defining-wcf-data-services.md)
