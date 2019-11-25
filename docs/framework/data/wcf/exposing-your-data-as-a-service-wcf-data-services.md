---
title: Exposition de vos données comme service (services de données WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- getting started, WCF Data Services
- WCF Data Services, getting started
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
ms.openlocfilehash: 71f26d7d41d112e13e6a77f0927c61d51b176b27
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975311"
---
# <a name="expose-your-data-as-a-service-wcf-data-services"></a>Exposer vos données en tant que service (WCF Data Services)

WCF Data Services s’intègre à Visual Studio pour vous permettre de définir plus facilement des services afin d’exposer vos données en tant que flux Open Data Protocol (OData). La création d’un service de données qui expose un flux OData implique les étapes de base suivantes :

1. **Définissez le modèle de données.** WCF Data Services prend en charge en mode natif les modèles de données basés sur le [Entity Framework ADO.net](../adonet/ef/index.md). Pour plus d’informations, consultez [Comment : créer un service de données à l’aide d’une source de données ADO.NET Entity Framework](create-a-data-service-using-an-adonet-ef-data-wcf.md).

     WCF Data Services prend également en charge les modèles de données basés sur des objets common language runtime (CLR) qui retournent une instance de l’interface <xref:System.Linq.IQueryable%601>. Vous pouvez ainsi déployer des services de données basés sur les listes, les tableaux et les collections du .NET Framework. Pour permettre les opérations de création, lecture, mise à jour et suppression sur ces structures de données, vous devez également implémenter l'interface <xref:System.Data.Services.IUpdatable>. Pour plus d’informations, consultez [Comment : créer un service de données à l’aide du fournisseur de réflexion](create-a-data-service-using-rp-wcf-data-services.md).

     Pour les scénarios plus avancés, WCF Data Services comprend un ensemble de fournisseurs qui vous permettent de définir un modèle de données basé sur des types de données à liaison tardive. Pour plus d’informations, consultez [fournisseurs de services de données personnalisés](custom-data-service-providers-wcf-data-services.md).

2. **Créez le service de données.** Le service de données le plus basique expose une classe qui hérite de la classe <xref:System.Data.Services.DataService%601> , avec un type `T` qui est le nom qualifié par l'espace de noms du conteneur d'entités. Pour plus d'informations, consultez [Defining WCF Data Services](defining-wcf-data-services.md).

3. **Configurez le service de données.** Par défaut, WCF Data Services désactive l’accès aux ressources exposées par un conteneur d’entités. L’interface <xref:System.Data.Services.DataServiceConfiguration> vous permet de configurer l’accès aux ressources et aux opérations de service, de spécifier la version prise en charge d’OData et de définir d’autres comportements à l’ensemble du service, tels que les comportements de traitement par lot ou le nombre maximal d’entités qui peuvent être retournées dans une réponse unique. Pour plus d’informations, consultez [configuration du service de données](configuring-the-data-service-wcf-data-services.md).

Pour obtenir un exemple de création d’un service de données simple basé sur l’exemple de base de données Northwind, consultez [démarrage rapide](quickstart-wcf-data-services.md).

## <a name="see-also"></a>Voir aussi

- [Bien démarrer](getting-started-with-wcf-data-services.md)
- [Vue d’ensemble](wcf-data-services-overview.md)
