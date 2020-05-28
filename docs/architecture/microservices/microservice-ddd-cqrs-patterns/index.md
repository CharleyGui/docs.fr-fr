---
title: Lutte contre la complexité d’entreprise dans un microservice disposant des modèles DDD et CQRS
description: Architecture des Microservices .NET pour les applications .NET en conteneur | Comprendre comment gérer des scénarios professionnels complexes en appliquant modèles DDD et CQRS
ms.date: 10/08/2018
ms.openlocfilehash: 852073548a66fbe568fc5c2531342db944d5a8b0
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144641"
---
# <a name="tackle-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a>Lutter contre la complexité d’entreprise dans un microservice disposant des modèles DDD et CQRS

*Concevoir un modèle de domaine pour chaque microservice ou contexte délimité qui reflète la compréhension du domaine d’entreprise.*

Cette section s’intéresse à des microservices plus avancés que vous implémentez quand vous avez besoin de vous attaquer à des sous-systèmes ou microservices complexes relevant de la connaissance d’experts du domaine avec des règles d’entreprise en constante évolution. Les modèles d’architecture utilisés dans cette section sont basés sur les approches de la conception pilotée par domaine (DDD, Domain-Driven Design) et de la séparation des responsabilités dans les commandes et requêtes (CQRS, Command and Query Responsibility Segregation), comme illustré dans la figure 7-1.

:::image type="complex" source="./media/index/internal-versus-external-architecture.png" alt-text="Diagramme comparant les modèles d’architecture externes et internes.":::
Différence entre une architecture externe (modèles de microservices, passerelles d’API, communications résilientes, pub/sub, etc.) et une architecture interne (modèles pilotés par les données/CRUD, DDD, injection de dépendances, multiples bibliothèques, etc.)
:::image-end:::

**Figure 7-1**. Modèles d’architecture de microservice externe ou interne pour chaque microservice

Toutefois, la plupart des techniques liées aux microservices pilotés par des données, comme la manière d’implémenter un service API Web ASP.NET Core ou d’exposer des métadonnées Swagger avec Swashbuckle ou NSwag, sont également applicables aux microservices plus avancés implémentés en interne avec des modèles DDD. Cette section est une extension des sections précédentes, car la plupart des pratiques expliquées précédemment s’appliquent également ici ou à tout type de microservice.

Tout d’abord, cette section fournit des détails sur les modèles CQRS simplifiés utilisés dans l’application de référence eShopOnContainers. Ensuite, vous obtiendrez une vue d’ensemble des techniques DDD qui vous permettent de rechercher des modèles courants que vous pouvez réutiliser dans vos applications.

DDD est un large sujet avec un ensemble complet de ressources d’apprentissage. Vous pouvez commencer avec des ouvrages comme [Domain-Driven Design](https://domainlanguage.com/ddd/) d’Eric Evans et d’autres documents de Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard et de nombreux autres experts en DDD/CQRS. Mais avant tout, vous devez essayer d’apprendre à appliquer des techniques DDD à partir des conversations, tableaux blancs et sessions de modélisation que vous tenez avec des experts de votre domaine d’entreprise concret.

#### <a name="additional-resources"></a>Ressources supplémentaires

##### <a name="ddd-domain-driven-design"></a>DDD (Domain-Driven Design)

- **Eric Evans. Langue du domaine** \
  <https://domainlanguage.com/>

- **Martin Fowler. Conception pilotée par le domaine** \
  <https://martinfowler.com/tags/domain%20driven%20design.html>

- **Jimmy bogard. Renforcement de votre domaine : une introduction** \
  <https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/>

##### <a name="ddd-books"></a>Ouvrages DDD

- **Eric Evans. Conception pilotée par domaine : la complexité du cœur du logiciel** \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- **Eric Evans. Référence de conception pilotée par domaine : définitions et résumés de modèles** \
  <https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/>

- **Vaughn Vernon. Implémentation de la conception pilotée par le domaine** \
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- **Vaughn Vernon. Conception pilotée par le domaine distillée** \
  <https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/>

- **Jimmy Nilsson. Application de la conception et des modèles pilotés par domaine** \
  <https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/>

- **Cesar de la Torre. Guide d’architecture orientée domaine N à couches avec .NET** \
  <https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/>

- **Avram et Floyd Marinescu. Conception pilotée par domaine rapide** \
  <https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/>

- **Scott Millett, ajustement Nick-modèles, principes et pratiques de conception pilotée par le domaine** \
  <https://www.wiley.com/Patterns%2C+Principles%2C+and+Practices+of+Domain+Driven+Design-p-9781118714706>

##### <a name="ddd-training"></a>Formation DDD

- **Julie Lerman et Steve Smith. Notions de base de la conception pilotée par domaine** \
  <https://bit.ly/PS-DDD>

>[!div class="step-by-step"]
>[Précédent](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md) 
> [Suivant](apply-simplified-microservice-cqrs-ddd-patterns.md)
