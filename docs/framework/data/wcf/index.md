---
title: WCF Data Services 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 017fe2177cf824d461b4c51ea805f75b6ddbe064
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779991"
---
# <a name="wcf-data-services-45"></a>WCF Data Services 4.5

WCF Data Services (autrefois appelé « ADO.NET Data Services ») est un composant de la .NET Framework qui vous permet de créer des services qui utilisent le [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] pour exposer et consommer des données sur le Web ou l’intranet à l’aide de la sémantique de l’état de la [représentation transfert (REST)](https://go.microsoft.com/fwlink/?LinkId=113919). OData expose les données sous forme de ressources adressables par des URI. Les données sont accessibles et modifiables à l'aide des verbes HTTP standard GET, PUT, POST et DELETE. OData utilise les conventions de relation d’entité de la [Entity Data Model](../adonet/entity-data-model.md) pour exposer des ressources sous la forme d’ensembles d’entités liés par des associations.

WCF Data Services utilise le protocole OData pour l’adressage et la mise à jour des ressources. De cette façon, vous pouvez accéder à ces services à partir de n’importe quel client qui prend en charge OData. OData vous permet de demander et d’écrire des données dans les ressources à l’aide de formats de transfert connus : Atom, un ensemble de normes pour l’échange et la mise à jour de données au format XML, et JavaScript Object Notation (JSON), un format d’échange de données textuel utilisé largement dans les applications AJAX.

WCF Data Services pouvez exposer des données provenant de différentes sources en tant que flux OData. Les outils Visual Studio facilitent la création d’un service OData à l’aide d’un modèle de données ADO.NET Entity Framework. Vous pouvez également créer des flux OData basés sur des classes common language runtime (CLR) et même des données à liaison tardive ou non typées.

WCF Data Services comprend également un ensemble de bibliothèques clientes, un pour les applications clientes générales .NET Framework et une autre pour les applications basées sur Silverlight. Ces bibliothèques clientes fournissent un modèle de programmation basé sur les objets lorsque vous accédez à un flux OData à partir d’environnements tels que les .NET Framework et Silverlight.

## <a name="where-should-i-start"></a>Où est-ce que je dois démarrer ?

En fonction de vos centres d’intérêt, vous pouvez vous familiariser avec WCF Data Services dans l’une des rubriques suivantes.

Je veux rentrer dans le vif du sujet...

- [Démarrage rapide](quickstart-wcf-data-services.md)

- [Prise en main](getting-started-with-wcf-data-services.md)

- [Démarrage rapide avec Silverlight](https://go.microsoft.com/fwlink/?LinkID=192782)

- [Démarrage rapide avec Silverlight pour le développement de Windows Phone](https://go.microsoft.com/fwlink/?LinkID=214535)

Montrez-moi un peu de code...

- [Démarrage rapide](quickstart-wcf-data-services.md)

- [Guide pratique pour Exécuter des requêtes de service de données](how-to-execute-data-service-queries-wcf-data-services.md)

- [Guide pratique pour Lier des données à des éléments Windows Presentation Foundation](bind-data-to-wpf-elements-wcf-data-services.md)

Je souhaite en savoir plus sur OData...

- [Intitulé Présentation d’OData](https://go.microsoft.com/fwlink/?LinkId=220867)

- [Site web Open Data Protocol](https://go.microsoft.com/fwlink/?LinkID=184554)

- [OData SDK](https://go.microsoft.com/fwlink/?LinkID=185248)

- [OData Forum Aux Questions](https://go.microsoft.com/fwlink/?LinkId=185867)

Je souhaite regarder des vidéos...

- [Guide du débutant sur WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=220864)

- [Vidéos du développeur WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=220861)

- [OData Site Web des développeurs](https://go.microsoft.com/fwlink/?LinkId=185866)

Je souhaite voir des exemples de bout en bout...

- [Exemples de documentation WCF Data Services dans la galerie d’exemples MSDN](https://go.microsoft.com/fwlink/?LinkID=220865)

- [Autres exemples WCF Data Services dans la galerie d’exemples MSDN](https://go.microsoft.com/fwlink/?LinkId=220866)

- [OData SDK](https://go.microsoft.com/fwlink/?LinkID=185248)

Qu'en est-il de l'intégration avec Visual Studio ?

- [Génération de la bibliothèque cliente du service de données](generating-the-data-service-client-library-wcf-data-services.md)

- [Création du service de données](creating-the-data-service.md)

- [Fournisseur Entity Framework](entity-framework-provider-wcf-data-services.md)

Comment puis-je l'utiliser ?

- [Vue d’ensemble](wcf-data-services-overview.md)

- [Intitulé Présentation d’OData](https://go.microsoft.com/fwlink/?LinkId=220867)

- [Scénarios d’application](application-scenarios-wcf-data-services.md)

Je souhaite utiliser Silverlight...

- [Démarrage rapide avec Silverlight](https://go.microsoft.com/fwlink/?LinkID=192782)

- [WCF Data Services (Silverlight)](https://go.microsoft.com/fwlink/?LinkID=143149)

- [Prise en main de Silverlight](https://go.microsoft.com/fwlink/?LinkId=148366)

Je souhaite utiliser LINQ...

- [Interrogation du service de données](querying-the-data-service-wcf-data-services.md)

- [Considérations sur LINQ](linq-considerations-wcf-data-services.md)

- [Guide pratique pour Exécuter des requêtes de service de données](how-to-execute-data-service-queries-wcf-data-services.md)

J’ai encore besoin d’informations supplémentaires...

- [Blog de l’équipe WCF Data Services](https://go.microsoft.com/fwlink/?LinkID=150511)

- [Ressources](wcf-data-services-resources.md)

- [Centre de développement WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=220868)

- [Site web Open Data Protocol](https://go.microsoft.com/fwlink/?LinkID=184554)

## <a name="in-this-section"></a>Dans cette section

[Vue d’ensemble](wcf-data-services-overview.md)

Fournit une vue d’ensemble des fonctionnalités et fonctionnalités disponibles dans WCF Data Services.

[Nouveautés de WCF Data Services 5,0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))

Décrit les nouvelles fonctionnalités de WCF Data Services et la prise en charge des nouvelles fonctionnalités OData.

[Prise en main](getting-started-with-wcf-data-services.md)

Décrit comment exposer et consommer des flux OData à l’aide de WCF Data Services.

[Définition de WCF Data Services](defining-wcf-data-services.md)

Décrit comment créer et configurer un service de données qui expose des flux OData.

[Bibliothèque cliente WCF Data Services](wcf-data-services-client-library.md)

Décrit comment utiliser des bibliothèques clientes pour consommer des flux OData à partir d’une application cliente .NET Framework.

## <a name="see-also"></a>Voir aussi

- [Representational State Transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)
