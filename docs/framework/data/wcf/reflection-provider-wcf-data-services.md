---
title: Fournisseur de réflexion (services de données WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: ef5ba300-6d7c-455e-a7bd-d0cc6d211ad4
ms.openlocfilehash: c3e160f96be2a95262776994152a06b42b475887
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779806"
---
# <a name="reflection-provider-wcf-data-services"></a>Fournisseur de réflexion (services de données WCF)

En plus d’exposer des données d’un modèle de données via Entity Framework, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] peut exposer des données qui ne sont pas définies strictement dans un modèle basé sur une entité. Le fournisseur de réflexion expose des données dans les classes qui retournent des types implémentant l’interface <xref:System.Linq.IQueryable%601>. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] utilise la réflexion pour déduire un modèle de données pour ces classes et peut traduire des requêtes basées sur une adresse sur des ressources en requêtes LINQ (Language Integrated Query) en fonction des types <xref:System.Linq.IQueryable%601> exposés.

> [!NOTE]
> Vous pouvez utiliser la méthode <xref:System.Linq.Queryable.AsQueryable%2A> pour retourner une interface <xref:System.Linq.IQueryable%601> à partir des classes qui implémentent l'interface <xref:System.Collections.Generic.IEnumerable%601>. De cette manière, la plupart des types de collection génériques peuvent être utilisé comme une source de données pour votre service de données.

Le fournisseur de réflexion prend en charge des hiérarchies de types. Pour plus d’informations, consultez [Guide pratique pour Créez un service de données à l’aide](create-a-data-service-using-rp-wcf-data-services.md)du fournisseur de réflexion.

## <a name="inferring-the-data-model"></a>Déduction du modèle de données

Lorsque vous créez le service de données, le fournisseur déduit le modèle de données à l'aide de la réflexion. La liste suivante montre comment le fournisseur de réflexion déduit le modèle de données :

- Conteneur d'entités - classe qui expose les données en tant que propriétés qui retournent une instance <xref:System.Linq.IQueryable%601>. Lorsque vous adressez un modèle de données basé sur la réflexion, le conteneur d'entités représente la racine du service. Une seule classe de conteneur d'entités est prise en charge pour un espace de noms donné.

- Jeux d'entités - les propriétés qui retournent des instances <xref:System.Linq.IQueryable%601> sont traitées comme des jeux d'entités. Les jeux d'entités sont adressés directement comme des ressources dans la requête. Une seule propriété sur le conteneur d'entités peut retourner une instance <xref:System.Linq.IQueryable%601> d'un type donné.

- Types d'entité - type `T` du <xref:System.Linq.IQueryable%601> que retourne le jeu d'entités. Les classes qui appartiennent à une hiérarchie d'héritage sont traduites par le fournisseur de réflexion en une hiérarchie des types d'entités équivalente.

- Clés d'entité - chaque classe de données qui est un type d'entité doit avoir une propriété de clé. Cette propriété possède l'attribut <xref:System.Data.Services.Common.DataServiceKeyAttribute> (`[DataServiceKeyAttribute]`).

    > [!NOTE]
    > Vous devez appliquer uniquement l'attribut <xref:System.Data.Services.Common.DataServiceKeyAttribute> à une propriété qui peut être utilisée pour identifier de manière unique une instance du type d'entité. Cet attribut est ignoré en cas d'application à une propriété de navigation.

- Propriétés de type d'entité - outre la clé d'entité, le fournisseur de réflexion traite les propriétés de non-indexeur accessibles d'une classe qui est un type d'entité comme suit :

  - Si la propriété retourne un type primitif, il est supposé que la propriété est une propriété d'un type d'entité.

  - Si la propriété retourne un type qui est également un type d'entité, il est supposé que la propriété est une propriété de navigation qui représente la terminaison « un » d'une relation plusieurs-à-un ou un-à-un.

  - Si la propriété retourne un <xref:System.Collections.Generic.IEnumerable%601> d'un type d'entité, il est supposé que la propriété est une propriété de navigation qui représente la terminaison « plusieurs » d'une relation plusieurs-à-un ou un-à-plusieurs.

  - Si le type de retour de la propriété est un type de valeur, alors la propriété représente un type complexe.

> [!NOTE]
> Contrairement à un modèle de données basé sur le modèle relationnel d'entités, les modèles basés sur le fournisseur de réflexion ne comprennent pas de données relationnelles. Vous devez utiliser Entity Framework pour exposer des données relationnelles via [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].

## <a name="data-type-mapping"></a>Mappage des types de données

Lorsqu'un modèle de données est déduit des classes .NET Framework, les types primitifs dans le modèle de données sont mappés aux types de données .NET Framework comme suit:

|Types de données .NET Framework|Type de modèle de données|
|------------------------------|---------------------|
|<xref:System.Byte> `[]`|`Edm.Binary`|
|<xref:System.Boolean>|`Edm.Boolean`|
|<xref:System.Byte>|`Edm.Byte`|
|<xref:System.DateTime>|`Edm.DateTime`|
|<xref:System.Decimal>|`Edm.Decimal`|
|<xref:System.Double>|`Edm.Double`|
|<xref:System.Guid>|`Edm.Guid`|
|<xref:System.Int16>|`Edm.Int16`|
|<xref:System.Int32>|`Edm.Int32`|
|<xref:System.Int64>|`Edm.Int64`|
|<xref:System.SByte>|`Edm.SByte`|
|<xref:System.Single>|`Edm.Single`|
|<xref:System.String>|`Edm.String`|

> [!NOTE]
> Les types de valeurs Nullable .NET Framework sont mappés aux mêmes types de modèles de données que les types de valeurs correspondants auxquels il n'est pas possible d'affecter une valeur Null.

## <a name="enabling-updates-in-the-data-model"></a>Autorisation des mises à jour dans le modèle de données

Pour autoriser les mises à jour des données exposées via ce type de modèle de données, le fournisseur de réflexion définit une interface <xref:System.Data.Services.IUpdatable>. Cette interface instruit le service de données sur la manière de rendre les mises à jour persistantes aux types exposés. Pour permettre des mises à jour aux ressources définies par le modèle de données, la classe de conteneur d'entités doit implémenter l'interface <xref:System.Data.Services.IUpdatable>. Pour obtenir un exemple d’implémentation de l' <xref:System.Data.Services.IUpdatable> interface, consultez [procédure : Créez un service de données à l’aide d'](create-a-data-service-using-linq-to-sql-wcf.md)une Source de données LINQ to SQL.

L'interface <xref:System.Data.Services.IUpdatable> requiert que les membres suivants soient implémentés afin que les mises à jour puissent être propagées à la source de données à l'aide du fournisseur de réflexion :

|Membre|Description|
|------------|-----------------|
|<xref:System.Data.Services.IUpdatable.AddReferenceToCollection%2A>|Fournit les fonctionnalités pour ajouter un objet à une collection d'objets connexes accessibles depuis une propriété de navigation.|
|<xref:System.Data.Services.IUpdatable.ClearChanges%2A>|Fournit les fonctionnalités qui annulent des modifications en attente aux données.|
|<xref:System.Data.Services.IUpdatable.CreateResource%2A>|Fournit les fonctionnalités pour créer une ressource dans le conteneur spécifié.|
|<xref:System.Data.Services.IUpdatable.DeleteResource%2A>|Fournit les fonctionnalités pour supprimer une ressource.|
|<xref:System.Data.Services.IUpdatable.GetResource%2A>|Fournit les fonctionnalités pour récupérer une ressource identifiée par une requête et un nom de type spécifiques.|
|<xref:System.Data.Services.IUpdatable.GetValue%2A>|Fournit les fonctionnalités pour retourner la valeur d'une propriété d'une ressource.|
|<xref:System.Data.Services.IUpdatable.RemoveReferenceFromCollection%2A>|Fournit les fonctionnalités pour supprimer un objet d’une collection d’objets connexes accessibles depuis une propriété de navigation.|
|<xref:System.Data.Services.IUpdatable.ResetResource%2A>|Fournit les fonctionnalités pour mettre à jour une ressource spécifiée.|
|<xref:System.Data.Services.IUpdatable.ResolveResource%2A>|Fournit les fonctionnalités pour retourner la ressource représentée par une instance d'objet spécifique.|
|<xref:System.Data.Services.IUpdatable.SaveChanges%2A>|Fournit les fonctionnalités pour enregistrer toutes les modifications en attente.|
|<xref:System.Data.Services.IUpdatable.SetReference%2A>|Fournit les fonctionnalités pour définir une référence d'objet connexe à l'aide d'une propriété de navigation.|
|<xref:System.Data.Services.IUpdatable.SetValue%2A>|Fournit les fonctionnalités pour définir la valeur de la propriété d'une ressource.|

## <a name="handling-concurrency"></a>Gestion de l'accès concurrentiel

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] prend en charge un modèle d'accès concurrentiel optimiste en vous permettant de définir un jeton d'accès concurrentiel pour une entité. Ce jeton d'accès concurrentiel, qui inclut une ou plusieurs propriétés de l'entité, est utilisé par le service de données pour déterminer si une modification a eu lieu dans les données demandées, mises à jour ou supprimées. Lorsque les valeurs du jeton obtenues de l'eTag dans la demande diffèrent des valeurs actuelles de l'entité, le service de données déclenche une exception. L'objet <xref:System.Data.Services.ETagAttribute> est appliqué à un type d'entité pour définir un jeton d'accès concurrentiel dans le fournisseur de réflexion. Le jeton d'accès concurrentiel ne peut pas inclure une propriété de clé ou de navigation. Pour plus d’informations, consultez [mise à jour du service de données](updating-the-data-service-wcf-data-services.md).

## <a name="using-linq-to-sql-with-the-reflection-provider"></a>Utilisation de LINQ to SQL avec le fournisseur de réflexion

Comme Entity Framework est pris en charge en mode natif par défaut, il s'agit du fournisseur de données recommandé pour l'utilisation de données relationnelles avec [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Toutefois, vous pouvez utiliser le fournisseur de réflexion pour utiliser les classes LINQ to SQL avec un service de données. Les <xref:System.Data.Linq.Table%601> jeux de résultats qui sont retournés par <xref:System.Data.Linq.DataContext> les méthodes sur le généré par le LINQ to SQL concepteur objet relationnel (Concepteur O/ <xref:System.Linq.IQueryable%601> R) implémentent l’interface. Cela permet au fournisseur de réflexion d'accéder à ces méthodes et de retourner les données d'entité de SQL Server en utilisant les classes LINQ to SQL générées. Toutefois, comme LINQ to SQL n'implémente pas l'interface <xref:System.Data.Services.IUpdatable>, vous devez ajouter une classe partielle qui étend la classe partielle <xref:System.Data.Linq.DataContext> existante pour ajouter l'implémentation <xref:System.Data.Services.IUpdatable>. Pour plus d'informations, voir [Procédure : Créez un service de données à l’aide d'](create-a-data-service-using-linq-to-sql-wcf.md)une Source de données LINQ to SQL.

## <a name="see-also"></a>Voir aussi

- [Fournisseurs de services de données](data-services-providers-wcf-data-services.md)
