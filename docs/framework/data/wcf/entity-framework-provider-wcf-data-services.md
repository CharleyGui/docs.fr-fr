---
title: Fournisseur Entity Framework (services de données WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
ms.openlocfilehash: 5a40eeafafef56902a9ae5037e6bc946b598f752
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854080"
---
# <a name="entity-framework-provider-wcf-data-services"></a>Fournisseur Entity Framework (services de données WCF)
Comme [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], ADO.NET Entity Framework est basé sur Entity Data Model qui est un type de modèle de relation d’entité. Le Entity Framework traduit les opérations par rapport à son implémentation du Entity Data Model, appelé *modèle conceptuel*, en opérations équivalentes sur une source de données. Cela fait d’Entity Framework un fournisseur idéal pour les services de données basés sur les données relationnelles, et toute base de données dont le fournisseur de données prend en charge Entity Framework peut être utilisée avec [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Pour obtenir la liste des sources de données qui prennent actuellement en charge le Entity Framework, consultez [fournisseurs tiers pour le Entity Framework](https://go.microsoft.com/fwlink/?LinkId=143699).  
  
 Dans un modèle conceptuel, le conteneur d'entités est la racine du service. Vous devez définir un modèle conceptuel dans Entity Framework avant que les données puissent être exposées par un service de données. Pour plus d’informations, consultez [Guide pratique pour Créez un service de données à l’aide d’une](create-a-data-service-using-an-adonet-ef-data-wcf.md)Source de données ADO.NET Entity Framework.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]prend en charge le modèle d’accès concurrentiel optimiste en vous permettant de définir un jeton d’accès concurrentiel pour une entité. Ce jeton d'accès concurrentiel, qui inclut une ou plusieurs propriétés de l'entité, est utilisé par le service de données pour déterminer si une modification a eu lieu dans les données demandées, mises à jour ou supprimées. Lorsque les valeurs du jeton obtenues de l'eTag dans la demande diffèrent des valeurs actuelles de l'entité, le service de données déclenche une exception. Pour indiquer qu’une propriété fait partie du jeton d’accès concurrentiel, vous devez appliquer l’attribut `ConcurrencyMode="Fixed"` dans le modèle de données défini par le fournisseur Entity Framework. Le jeton d'accès concurrentiel ne peut pas inclure une propriété de clé ou de navigation. Pour plus d’informations, consultez [mise à jour du service de données](updating-the-data-service-wcf-data-services.md).  
  
 Pour en savoir plus sur le Entity Framework, consultez [Entity Framework vue d’ensemble](../adonet/ef/overview.md).  
  
## <a name="see-also"></a>Voir aussi

- [Fournisseurs de services de données](data-services-providers-wcf-data-services.md)
- [Fournisseur de réflexion](reflection-provider-wcf-data-services.md)
- [Entity Data Model](../adonet/entity-data-model.md)
