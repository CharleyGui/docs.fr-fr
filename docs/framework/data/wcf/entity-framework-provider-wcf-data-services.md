---
title: Fournisseur Entity Framework (services de données WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
ms.openlocfilehash: cb7bd7e793f73fc34057150ee5217dba6653237e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172643"
---
# <a name="entity-framework-provider-wcf-data-services"></a>Fournisseur Entity Framework (services de données WCF)

Comme WCF Data Services, le Entity Framework ADO.NET est basé sur le Entity Data Model, qui est un type de modèle de relation d’entité. Le Entity Framework traduit les opérations par rapport à son implémentation du Entity Data Model, appelé *modèle conceptuel*, en opérations équivalentes sur une source de données. Ainsi, les Entity Framework un fournisseur idéal pour les services de données basés sur les données relationnelles, et toute base de données qui a un fournisseur de données qui prend en charge le Entity Framework peut être utilisée avec WCF Data Services. Pour obtenir la liste des sources de données qui prennent actuellement en charge le Entity Framework, consultez [fournisseurs Entity Framework](/ef/ef6/fundamentals/providers/).
  
 Dans un modèle conceptuel, le conteneur d'entités est la racine du service. Vous devez définir un modèle conceptuel dans Entity Framework avant que les données puissent être exposées par un service de données. Pour plus d’informations, consultez [Comment : créer un service de données à l’aide d’une source de données ADO.NET Entity Framework](create-a-data-service-using-an-adonet-ef-data-wcf.md).  
  
 WCF Data Services prend en charge le modèle d’accès concurrentiel optimiste en vous permettant de définir un jeton d’accès concurrentiel pour une entité. Ce jeton d'accès concurrentiel, qui inclut une ou plusieurs propriétés de l'entité, est utilisé par le service de données pour déterminer si une modification a eu lieu dans les données demandées, mises à jour ou supprimées. Lorsque les valeurs du jeton obtenues de l'eTag dans la demande diffèrent des valeurs actuelles de l'entité, le service de données déclenche une exception. Pour indiquer qu’une propriété fait partie du jeton d’accès concurrentiel, vous devez appliquer l’attribut `ConcurrencyMode="Fixed"` dans le modèle de données défini par le fournisseur Entity Framework. Le jeton d'accès concurrentiel ne peut pas inclure une propriété de clé ou de navigation. Pour plus d’informations, consultez [mise à jour du service de données](updating-the-data-service-wcf-data-services.md).  
  
 Pour en savoir plus sur le Entity Framework, consultez [Entity Framework vue d’ensemble](../adonet/ef/overview.md).  
  
## <a name="see-also"></a>Voir aussi

- [Fournisseurs de services de données](data-services-providers-wcf-data-services.md)
- [Fournisseur de réflexion](reflection-provider-wcf-data-services.md)
- [Entity Data Model](../adonet/entity-data-model.md)
