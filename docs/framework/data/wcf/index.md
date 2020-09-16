---
title: WCF Data Services 4.5
description: En savoir plus sur WCF Data Services, un composant .NET Framework qui prend en charge les services pour exposer et consommer des données à l’aide de la sémantique REST.
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: c36967236c40efbf432d554c3f551aea22cfb148
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549677"
---
# <a name="wcf-data-services-45"></a>WCF Data Services 4.5

WCF Data Services (autrefois appelé « ADO.NET Data Services ») est un composant de la .NET Framework qui vous permet de créer des services qui utilisent le Open Data Protocol (OData) pour exposer et consommer des données sur le Web ou l’intranet à l’aide de la sémantique de [Representational State Transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm). OData expose les données sous forme de ressources adressables par des URI. Les données sont accessibles et modifiables à l'aide des verbes HTTP standard GET, PUT, POST et DELETE. OData utilise les conventions de relation d’entité de la [Entity Data Model](../adonet/entity-data-model.md) pour exposer des ressources sous la forme d’ensembles d’entités liés par des associations.

WCF Data Services utilise le protocole OData pour l’adressage et la mise à jour des ressources. De cette façon, vous pouvez accéder à ces services à partir de n’importe quel client qui prend en charge OData. OData vous permet de demander et d’écrire des données dans les ressources à l’aide de formats de transfert connus : Atom, un ensemble de normes pour l’échange et la mise à jour de données au format XML, et le format JSON (JavaScript Object Notation), un format d’échange de données textuel utilisé largement dans les applications AJAX.

WCF Data Services pouvez exposer des données provenant de différentes sources en tant que flux OData. Les outils Visual Studio facilitent la création d’un service OData à l’aide d’un modèle de données ADO.NET Entity Framework. Vous pouvez également créer des flux OData basés sur des classes common language runtime (CLR) et même des données à liaison tardive ou non typées.

WCF Data Services comprend également un ensemble de bibliothèques clientes, un pour les applications clientes générales .NET Framework et une autre pour les applications basées sur Silverlight. Ces bibliothèques clientes fournissent un modèle de programmation basé sur des objets lorsque vous accédez à un flux OData depuis des environnements tels que .NET Framework et Silverlight.

## <a name="where-should-i-start"></a>Où est-ce que je dois démarrer ?

En fonction de vos centres d’intérêt, vous pouvez vous familiariser avec WCF Data Services dans l’une des rubriques suivantes.

Je veux rentrer dans le vif du sujet...

- [Démarrage rapide](quickstart-wcf-data-services.md)

- [Prise en main](getting-started-with-wcf-data-services.md)

Montrez-moi un peu de code...

- [Démarrage rapide](quickstart-wcf-data-services.md)

- [Procédure : Exécuter les requêtes de services de données](how-to-execute-data-service-queries-wcf-data-services.md)

- [Procédure : Lier des données aux éléments Windows Presentation Foundation](bind-data-to-wpf-elements-wcf-data-services.md)

Je souhaite en savoir plus sur OData...

- [Livre blanc : présentation d’OData](https://download.microsoft.com/download/E/5/A/E5A59052-EE48-4D64-897B-5F7C608165B8/IntroducingOData.pdf)
- [Site Web Open Data Protocol](https://www.odata.org/)
- [Kit de développement logiciel (SDK) OData](https://www.odata.org/ecosystem/)

Je souhaite voir des exemples de bout en bout...

- [Démarrage rapide WCF Data Services](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))
- [OData SDK-exemple de code](https://www.odata.org/ecosystem/#sdk)

Qu'en est-il de l'intégration avec Visual Studio ?

- [Génération de la bibliothèque cliente du service de données](generating-the-data-service-client-library-wcf-data-services.md)

- [Création du service de données](creating-the-data-service.md)

- [Fournisseur Entity Framework](entity-framework-provider-wcf-data-services.md)

À quoi sert PIM ?

- [Vue d'ensemble](wcf-data-services-overview.md)

- [Scénarios d’application](application-scenarios-wcf-data-services.md)

Je souhaite utiliser LINQ...

- [Interrogation du service de données](querying-the-data-service-wcf-data-services.md)

- [Considérations sur LINQ](linq-considerations-wcf-data-services.md)

- [Procédure : Exécuter les requêtes de services de données](how-to-execute-data-service-queries-wcf-data-services.md)

J’ai encore besoin d’informations supplémentaires...

- [Blog de l’équipe WCF Data Services](/archive/blogs/astoriateam/)

- [Ressources](wcf-data-services-resources.md)

## <a name="in-this-section"></a>Dans cette section

[Vue d'ensemble](wcf-data-services-overview.md)

Fournit une vue d’ensemble des fonctionnalités et fonctionnalités disponibles dans WCF Data Services.

[Nouveautés de WCF Data Services 5,0](/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))

Décrit les nouvelles fonctionnalités de WCF Data Services et la prise en charge des nouvelles fonctionnalités OData.

[Prise en main](getting-started-with-wcf-data-services.md)

Décrit comment exposer et consommer des flux OData à l’aide de WCF Data Services.

[Définition des services de données WCF](defining-wcf-data-services.md)

Décrit comment créer et configurer un service de données qui expose des flux OData.

[Bibliothèque client services de données WCF](wcf-data-services-client-library.md)

Décrit comment utiliser des bibliothèques clientes pour consommer des flux OData à partir d’une application cliente .NET Framework.

## <a name="see-also"></a>Voir aussi

- [Representational State Transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)
