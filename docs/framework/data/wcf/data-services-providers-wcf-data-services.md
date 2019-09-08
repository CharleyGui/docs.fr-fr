---
title: Fournisseurs de services de données (services de données WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: a0160b1b-3d9c-4cc8-8391-cb0986a60a41
ms.openlocfilehash: 7623c2b743d6a61362c8cf0e1228b4663c9e7d48
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780387"
---
# <a name="data-services-providers-wcf-data-services"></a>Fournisseurs de services de données (services de données WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]prend en charge plusieurs modèles de fournisseur pour exposer des [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] données sous forme de flux. Cette rubrique fournit les informations pour vous permettre de choisir le meilleur fournisseur [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] pour votre source de données.  
  
## <a name="data-source-providers"></a>Fournisseurs de sources de données  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]prend en charge les fournisseurs suivants pour définir le modèle de données d’un service de données.  
  
|Fournisseur|Description|  
|--------------|-----------------|  
|Fournisseur Entity Framework|Ce fournisseur utilise ADO.NET Entity Framework pour vous permettre d’utiliser des données relationnelles avec un service de données en définissant un modèle de données qui est mappé aux données relationnelles. Votre source de données peut être SQL Server ou toute autre source de données avec un support de fournisseur tiers pour Entity Framework. Vous devez utiliser le fournisseur Entity Framework lorsque vous avez une source de données relationnelles, telle qu’une base de données SQL Server. Pour plus d’informations, consultez [Entity Framework fournisseur](entity-framework-provider-wcf-data-services.md).|  
|Fournisseur de réflexion|Ce fournisseur utilise la réflexion pour vous permettre de définir un modèle de données basé sur des classes de données existantes qui peuvent être exposées comme des instances de l'interface <xref:System.Linq.IQueryable%601>. Les mises à jour sont activées en implémentant l'interface <xref:System.Data.Services.IUpdatable>. Vous devez utiliser ce fournisseur lorsque vous avez des classes de données statiques définies pendant l'exécution, telles que celles générées par LINQ to SQL ou définies par un DataSet typé. Pour plus d’informations, consultez la page [fournisseur de réflexion](reflection-provider-wcf-data-services.md).|  
|Fournisseurs de services de données personnalisés|[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] inclut un jeu de fournisseurs qui vous permet de définir dynamiquement  un modèle de données basé sur des types de données à liaison tardive. Vous devez implémenter ces interfaces lorsque les données exposées sont inconnues au moment de la conception de l’application ou lorsque les fournisseurs d’Entity Framework ou de réflexion ne sont pas suffisants. Pour plus d’informations, consultez [fournisseurs de services de données personnalisés](custom-data-service-providers-wcf-data-services.md).|  
  
## <a name="other-data-service-providers"></a>Autres fournisseurs de services de données  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]dispose du fournisseur de services de données supplémentaire suivant qui améliore les performances d’une source de données définie à l’aide de l’un des autres fournisseurs.  
  
|Fournisseur|Description|  
|--------------|-----------------|  
|Fournisseur de diffusion en continu|Ce fournisseur vous permet d'exposer des types de données d'objet blob (binary large object) à l'aide d'[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Un fournisseur de diffusion en continu est créé en implémentant l'interface <xref:System.Data.Services.Providers.IDataServiceStreamProvider>. Ce fournisseur peut être implémenté avec n'importe quel fournisseur de sources de données. Pour plus d’informations, consultez la page [fournisseur de streaming](streaming-provider-wcf-data-services.md).|  
  
## <a name="see-also"></a>Voir aussi

- [Définition de WCF Data Services](defining-wcf-data-services.md)
- [Configuration du service de données](configuring-the-data-service-wcf-data-services.md)
- [Hébergement du service de données](hosting-the-data-service-wcf-data-services.md)
