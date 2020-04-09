---
title: Conception de la couche de persistance de l’infrastructure
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Explorer le modèle de référentiel dans la conception de la couche de persistance de l’infrastructure.
ms.date: 10/08/2018
ms.openlocfilehash: 1b2665e81ade60affa84563121c04bca08537f07
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988477"
---
# <a name="design-the-infrastructure-persistence-layer"></a>Concevoir la couche de persistance de l’infrastructure

Les composantes de persistance des données donnent accès aux données hébergées dans les limites d’un microservice (c’est-à-dire la base de données d’un microservice). Ils contiennent l’implémentation réelle des composants tels que les dépôts et les classes d’[unité de travail](https://martinfowler.com/eaaCatalog/unitOfWork.html), comme les objets <xref:Microsoft.EntityFrameworkCore.DbContext> Entity Framework (EF) personnalisés. EF DbContext implémente à la fois les modèles de référentiel et les modèles d’unité de travail.

## <a name="the-repository-pattern"></a>Le modèle Dépôt

Les dépôts sont des classes ou composants qui encapsulent la logique nécessaire pour accéder aux sources de données. Ils centralisent les fonctionnalités d’accès aux données communes, en fournissant une meilleure maintenabilité et en découplant l’infrastructure ou la technologie utilisée pour accéder aux bases de données à partir de la couche du modèle de domaine. Si vous utilisez un mappeur objet-relationnel (ORM, Object-Relational Mapper) comme Entity Framework, le code à implémenter est simplifié grâce à LINQ et à un typage fort. Ainsi, vous pouvez vous concentrer sur la logique de persistance des données plutôt que sur le raccordement de l’accès aux données.

Le modèle Dépôt est une façon bien décrite d’utiliser une source de données. Dans l’ouvrage [Patterns of Enterprise Application Architecture](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/), Martin Fowler décrit un dépôt comme suit :

> Un dépôt effectue les tâches d’un intermédiaire entre les couches du modèle de domaine et le mappage de données, en agissant d’une manière similaire à un ensemble d’objets de domaine dans la mémoire. Les objets clients génèrent des requêtes de façon déclarative et les envoient aux dépôts pour obtenir des réponses. D’un point de vue conceptuel, un dépôt encapsule un ensemble d’objets stockés dans la base de données et les opérations pouvant être effectuées sur ces derniers, en fournissant un moyen plus proche de la couche de persistance. Les dépôts, par ailleurs, prennent en charge l’objectif de séparation, claire et dans un seul sens, de la dépendance entre le domaine de travail et l’allocation ou le mappage de données.

### <a name="define-one-repository-per-aggregate"></a>Définir un seul dépôt par agrégat

Pour chaque agrégat ou racine d’agrégat, vous devez créer une seule classe de dépôt. Dans un microservice basé sur des modèles de conception pilotée par le domaine (DDD, Domain-Driven Design), le seul canal que vous devez utiliser pour mettre à jour la base de données doit être les référentiels. C’est parce qu’ils ont une relation en tête-à-un avec la racine globale, qui contrôle les invariants de l’agrégat et la cohérence transactionnelle. Il est possible d’interroger la base de données par le biais d’autres canaux (selon une approche CQRS par exemple), car les requêtes ne changent pas l’état de la base de données. Toutefois, la zone transactionnelle (à savoir les mises à jour) doit toujours être contrôlée par les dépôts et les racines d’agrégat.

En bref, un dépôt vous permet de renseigner les données en mémoire provenant de la base de données sous la forme d’entités de domaine. Une fois que les entités sont en mémoire, elles peuvent être modifiées et de nouveau rendues persistantes dans la base de données par le biais de transactions.

Comme indiqué précédemment, si vous utilisez le modèle architectural CQS/CQRS, les requêtes initiales sont effectuées par des requêtes latérales en dehors du modèle de domaine, effectuées par de simples instructions SQL à l’aide de Dapper. Cette approche est beaucoup plus souple que les dépôts, car vous pouvez interroger et joindre les tables dont vous avez besoin, et ces requêtes ne sont pas limitées par des règles issues des agrégats. Ces données accèdent à la couche présentation ou à l’application cliente.

Si l’utilisateur apporte des modifications, les données à mettre à jour passent de l’application cliente ou de la couche présentation à la couche Application (comme un service API web). Quand vous recevez une commande dans un gestionnaire de commandes, vous utilisez des référentiels pour obtenir de la base de données les données à mettre à jour. Vous les mettez à jour en mémoire avec les informations passées avec les commandes, puis vous ajoutez ou vous mettez à jour les données (entités de domaine) dans la base de données via une transaction.

Il est important de souligner à nouveau que vous devez définir seulement un référentiel pour chaque racine d’agrégat, comme illustré dans la figure 7-17. Pour atteindre l’objectif de la racine d’agrégat visant à maintenir la cohérence transactionnelle entre tous les objets au sein de l’agrégat, vous ne devez jamais créer un dépôt pour chaque table dans la base de données.

![Diagramme montrant les relations du domaine et d’autres infrastructures.](./media/infrastructure-persistence-layer-design/repository-aggregate-database-table-relationships.png)

**Figure 7-17**. Relation entre les dépôts, les agrégats et les tables de base de données

Le diagramme ci-dessus montre les relations entre les couches de domaine et d’infrastructure : Buyer Aggregate dépend de l’IBuyerRepository et Order Aggregate dépend des interfaces IOrderRepository, ces interfaces sont implémentées dans la couche d’infrastructure par les dépôts correspondants qui dépendent d’UnitOfWork, également mis en œuvre là, qui accède aux tables dans le niveau de données.

### <a name="enforce-one-aggregate-root-per-repository"></a>Appliquer une seule racine d’agrégat par référentiel

Il peut s’avérer très utile d’implémenter votre conception de dépôt de sorte à faire respecter la règle stipulant que seules les racines d’agrégat doivent avoir des dépôts. Vous pouvez créer un type de dépôt générique ou élémentaire qui limite le type des entités utilisées pour veiller à ce qu’elles aient l’interface de marqueur `IAggregateRoot`.

Ainsi, chaque classe de dépôt implémentée au niveau de la couche d’infrastructure implémente son propre contrat ou sa propre interface, comme le montre le code suivant :

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class OrderRepository : IOrderRepository
    {
      // ...
    }
}
```

Chaque interface de dépôt spécifique implémente l’interface IRepository générique :

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
    // ...
}
```

Toutefois, un meilleur moyen d’obliger le code à appliquer la convention selon laquelle chaque dépôt doit être lié à un seul agrégat consiste à implémenter un type de dépôt générique. De cette façon, il est explicite que vous utilisez un dépôt pour cibler un agrégat spécifique. Vous pouvez le faire facilement en implémentant une interface de base `IRepository` générique, comme dans le code suivant :

```csharp
public interface IRepository<T> where T : IAggregateRoot
{
    //....
}
```

### <a name="the-repository-pattern-makes-it-easier-to-test-your-application-logic"></a>Le modèle Dépôt facilite le test de votre logique d’application

Le modèle Dépôt vous permet de tester facilement votre application avec des tests unitaires. N’oubliez pas que les tests unitaires testent uniquement votre code, pas l’infrastructure, si bien que les abstractions de dépôt facilitent la réalisation de cet objectif.

Comme indiqué dans une section précédente, il est recommandé de définir et placer les interfaces de dépôt dans la couche du modèle de domaine pour que la couche Application telle que votre microservice d’API web, ne dépende pas directement de la couche d’infrastructure, dans laquelle vous avez implémenté les classes de dépôt réelles. Ce faisant et à l’aide de l’injection de dépendances dans les contrôleurs de votre API web, vous pouvez implémenter des dépôts fictifs qui retournent de fausses données au lieu des données de la base de données. Cette approche découplée vous permet de créer et d’exécuter des tests unitaires centrés sur la logique de votre application sans nécessiter de connectivité à la base de données.

Les connexions aux bases de données peuvent échouer et, ce qui est plus important, l’exécution de centaines de tests sur une base de données est mauvaise pour deux raisons. Tout d’abord, elle peut s’avérer très chronophage en raison du grand nombre de tests. Ensuite, les enregistrements de base de données peuvent changer et affecter les résultats de vos tests, qui peuvent ne pas être cohérents. Un test sur la base de données n’est pas un test unitaire, mais un test d’intégration. Vous devez effectuer de nombreux tests unitaires qui s’exécutent rapidement, mais un nombre moindre de tests d’intégration sur les bases de données.

En termes de séparation des responsabilités pour les tests unitaires, votre logique s’exécute sur des entités de domaine dans la mémoire. Elle suppose que la classe de dépôt les a remises. Une fois que votre logique modifie les entités de domaine, elle suppose que la classe de dépôt les stocke correctement. Il est important de créer des tests unitaires sur votre modèle de domaine et sa logique de domaine. Les racines d’agrégat correspondent aux limites de cohérence principales dans la conception DDD.

Les dépôts mis en œuvre dans eShopOnContainers s’appuient sur la mise en œuvre DbContext d’EF Core des modèles Repository et Unit of Work à l’aide de son tracker de changement, de sorte qu’ils ne duplifient pas cette fonctionnalité.

### <a name="the-difference-between-the-repository-pattern-and-the-legacy-data-access-class-dal-class-pattern"></a>La différence entre le modèle Dépôt et le modèle de la classe d’accès aux données héritée (classe DAL)

Un objet d’accès aux données exécute directement des opérations d’accès aux données et de persistance des données dans le stockage. Un référentiel marque les données avec les opérations à effectuer dans la mémoire d’une unité d’objet de travail (comme dans EF quand vous utilisez la classe <xref:Microsoft.EntityFrameworkCore.DbContext>), mais ces mises à jour ne sont pas effectuées immédiatement sur la base de données.

Une unité de travail est définie comme une transaction unique qui implique plusieurs opérations d’insertion, de mise à jour ou de suppression. En termes simples, cela signifie que, pour une action utilisateur spécifique, comme une inscription sur un site web, toutes les opérations d’insertion, de mise à jour et de suppression sont gérées dans une même transaction. Une telle gestion est plus efficace que de gérer plusieurs transactions de base de données d’une manière plus bavarde.

Ces multiples opérations de persistance sont effectuées ultérieurement en une seule action quand votre code de la couche Application la commande. La décision d’appliquer les modifications en mémoire au stockage réel de la base de données se base généralement sur le [modèle Unité de travail](https://martinfowler.com/eaaCatalog/unitOfWork.html). Dans EF, le modèle Unité de travail est implémenté en tant que <xref:Microsoft.EntityFrameworkCore.DbContext>.

Dans de nombreux cas, ce modèle ou cette façon d’appliquer des opérations dans le stockage peut augmenter les performances de l’application et réduire le risque d’incohérences. Cela réduit également le blocage des transactions dans les tables de base de données, car toutes les opérations prévues sont validées dans le cadre d’une seule transaction. Ce modèle est plus efficace que l’exécution de nombreuses opérations isolées sur la base de données. Par conséquent, le mappage relationnel objet (ORM) sélectionné peut optimiser l’exécution sur la base de données en regroupant plusieurs actions de mise à jour au sein de la même transaction, au lieu d’exécuter de nombreuses transactions distinctes de petite taille.

### <a name="repositories-shouldnt-be-mandatory"></a>Les dépôts ne doivent pas être obligatoires

Les dépôts personnalisés sont utiles pour les raisons citées précédemment. C’est l’approche utilisée pour le microservice de passation de commandes dans eShopOnContainers. Toutefois, il ne s’agit pas d’un modèle essentiel à implémenter dans une conception DDD ni même dans le cadre d’un développement .NET général.

Par exemple, Jimmy Bogard, en commentant directement le présent guide, a tenu les propos suivants :

> Ce sera probablement mon plus grand retour. Je ne suis vraiment pas un fan de dépôts, principalement parce qu’ils cachent les détails importants du mécanisme de persistance sous-jacente. C’est pourquoi je vais pour MediatR pour les commandes, aussi. Je peux utiliser toute la puissance de la couche de persistance et transmettre tout ce comportement de domaine à mes racines d’agrégat. Je ne veux généralement pas me moquer de mes dépôts - j’ai encore besoin d’avoir ce test d’intégration avec la vraie chose. Aller CQRS signifiait que nous n’avions plus vraiment besoin de dépôts.

Les référentiels peuvent être utiles, mais ils ne sont pas critiques pour votre conception pilotée par le domaine, comme le sont le modèle Agrégat et le modèle de domaine riche. Par conséquent, utilisez le modèle Dépôt ou ne l’utilisez pas, en fonction de vos besoins. Quoi qu’il en soit, vous allez utiliser le modèle de dépôt chaque fois que vous utilisez EF Core bien que, dans ce cas, le référentiel couvre l’ensemble du microservice ou le contexte délimité.

## <a name="additional-resources"></a>Ressources supplémentaires

### <a name="repository-pattern"></a>Modèle de référentiel

- **Edward Hieatt et Rob moi. Modèle de dépôt.** \
  <https://martinfowler.com/eaaCatalog/repository.html>

- **Le modèle de dépôt** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/ff649690(v=pandp.10)>

- **Eric Evans. Conception axée sur le domaine : s’attaquer à la complexité au cœur du logiciel.** (Un livre, qui inclut une présentation du modèle de référentiel) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

### <a name="unit-of-work-pattern"></a>Modèle Unité de travail

- **Martin Fowler. Modèle d’unité de travail.** \
  <https://martinfowler.com/eaaCatalog/unitOfWork.html>

- **Mise en œuvre du dépôt et de l’unité des modèles de travail dans une application MVC ASP.NET** \
  <https://docs.microsoft.com/aspnet/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

>[!div class="step-by-step"]
>[Suivant précédent](domain-events-design-implementation.md)
>[Next](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
