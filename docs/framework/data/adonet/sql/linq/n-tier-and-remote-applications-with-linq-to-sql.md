---
title: Applications multicouches et distantes avec LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
ms.openlocfilehash: 6758ae23c25d8e7a4255d0a784cccd1eb404bfe7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174301"
---
# <a name="n-tier-and-remote-applications-with-linq-to-sql"></a>Applications multicouches et distantes avec LINQ to SQL
Vous pouvez créer des applications multicouches qui utilisent [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. En règle [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] générale, le contexte des données, les classes d’entités et la logique de construction de requêtes sont situés au niveau intermédiaire sous forme de couche d’accès aux données (DAL). La logique métier et toutes les données non persistantes peuvent être implémentées entièrement dans des classes et des méthodes partielles et le contexte de données, ou ils peuvent être implémentés dans des classes distinctes.

 Le niveau client ou la couche Présentation appelle des méthodes sur l'interface distante de la couche intermédiaire, et la couche Data Access sur cette couche exécutera des requêtes ou des procédures stockées qui sont mappées aux méthodes <xref:System.Data.Linq.DataContext>. La couche intermédiaire retourne les données aux clients généralement sous la forme de représentations XML d'entités ou objets proxy.

 Sur la couche intermédiaire, les entités sont créées par le contexte de données, qui suit leur état et gère le chargement et la soumission différés des modifications à partir de et vers la base de données. Ces entités sont "attachées" au `DataContext`. Toutefois, après que les entités ont été envoyées vers une autre couche par le biais de la sérialisation, elles deviennent détachées, ce qui signifie que `DataContext` ne suit plus leur état. Les entités que le client renvoie pour les mises à jour doivent être préalablement rattachées au contexte de données pour que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] puisse soumettre les modifications à la base de données. Le client est chargé de renvoyer les valeurs et/ou horodatages d'origine à la couche intermédiaire si ceux-ci sont requis pour les contrôles d'accès concurrentiel optimiste.

 Dans les applications ASP.NET, <xref:System.Web.UI.WebControls.LinqDataSource> gère la plus grande part de cette complexité. Pour plus d’informations, voir [LinqDataSource Web Server Control Overview](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100)).

## <a name="additional-resources"></a>Ressources supplémentaires
 Pour plus d'informations sur l'implémentation des applications multicouches qui utilisent [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], consultez les rubriques suivantes :

- [Applications multicouches LINQ to SQL avec ASP.NET](linq-to-sql-n-tier-with-aspnet.md)

- [Applications multicouches LINQ to SQL avec les services web](linq-to-sql-n-tier-with-web-services.md)

- [Implémentation de la logique métier dans les applications multiniveaux](implementing-business-logic-linq-to-sql.md)

- [Récupération de données et opérations CUD dans les applications multicouches (LINQ to SQL)](data-retrieval-and-cud-operations-in-n-tier-applications.md)

 Pour plus d’informations sur les applications à n-tier qui utilisent ADO.NET DataSets, voir [Work with datasets dans des applications à n-tier](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).

## <a name="see-also"></a>Voir aussi

- [Informations de base](background-information.md)
