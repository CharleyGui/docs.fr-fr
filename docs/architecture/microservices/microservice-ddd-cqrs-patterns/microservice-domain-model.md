---
title: Conception d’un modèle de domaine de microservice
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Comprendre les concepts clés de la conception d’un modèle de domaine orienté DDD.
ms.date: 01/30/2020
ms.openlocfilehash: 628fb5c76362ec8f48367b3d69d16ea6ebd24f09
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77502334"
---
# <a name="design-a-microservice-domain-model"></a>Concevoir un modèle de domaine de microservice

*Définir un seul modèle de domaine complet pour chaque microservice métier ou contexte délimité*

Votre objectif consiste à créer un seul modèle de domaine cohésif pour chaque microservice métier ou contexte limité. N’oubliez pas, toutefois, qu’un contexte limité ou microservice métier peuvent parfois se composer de plusieurs services physiques qui partagent un modèle de domaine unique. Le modèle de domaine doit capturer les règles, le comportement, le langage informatique de l’entreprise et les contraintes du contexte limité ou microservice métier unique qu’il représente.

## <a name="the-domain-entity-pattern"></a>Le modèle Entité de domaine

Les entités représentent des objets de domaine. Elles sont principalement définies par leur identité, leur continuité et leur persistance dans le temps et non uniquement par les attributs qui les composent. Comme le décrit Eric Evans, « un objet principalement défini par son identité est appelé entité ». Les entités sont très importantes dans le modèle de domaine, puisqu’elles constituent la base d’un modèle. Par conséquent, vous devez les identifier et les concevoir soigneusement.

*L’identité d’une entité peut traverser plusieurs microservices ou contextes limités.*

La même identité (c’est-à-dire la même valeur `Id`, mais peut-être pas la même entité de domaine) peut être modélisée dans plusieurs contextes délimités ou microservices. Toutefois, cela n’implique pas que la même entité, avec les mêmes attributs et la même logique, peut être implémentée dans plusieurs contextes limités. En effet, les entités incluses dans chaque contexte limité limitent leurs attributs et comportements à ceux nécessaires dans le domaine du contexte limité.

Par exemple, l’entité Buyer peut avoir la plupart des attributs d’une personne définis dans l’entité User dans le profil ou microservice d’identité, notamment son identité. Mais l’entité Buyer dans le microservice de passation de commandes peut avoir moins d’attributs, car seules certaines données sur l’acheteur sont liées au processus de commande. Le contexte de chaque microservice ou contexte limité exerce un impact sur son modèle de domaine.

*Les entités de domaine doivent implémenter un comportement en plus des attributs de données.*

Une entité de domaine en conception pilotée par le domaine (Domain Driver Design, DDD) doit implémenter la logique de domaine ou le comportement lié aux données de l’entité (objet auquel vous accédez dans la mémoire). Par exemple, dans le cadre d’une classe d’entité de commande, vous devez implémenter la logique et les opérations métier en tant que méthodes pour des tâches comme l’ajout d’un article, la validation des données et le calcul du total. Les méthodes de l’entité s’occupent des invariants et des règles de l’entité au lieu de répartir ces règles dans toute la couche Application.

La figure 7-8 illustre une entité de domaine qui implémente non seulement des attributs de données, mais aussi des opérations ou des méthodes avec une logique de domaine associée.

![Diagramme montrant le modèle d’une entité de domaine.](./media/microservice-domain-model/domain-entity-pattern.png)

**Figure 7-8**. Exemple de conception d’entité de domaine qui implémente des données en plus d’un comportement

Une entité de modèle de domaine implémente des comportements via des méthodes : autrement dit, il ne s’agit pas d’un modèle « passif ». Bien entendu, vous pouvez parfois avoir des entités qui n’implémentent pas de logique dans le cadre de la classe d’entité. Cela peut se produire dans les entités enfants au sein d’un agrégat si l’entité enfant n’a pas de logique spéciale, car la plupart de la logique est définie dans la racine d’agrégat. Si vous avez un microservice complexe qui contient beaucoup de logique implémentée dans les classes de service au lieu des entités de domaine, vous risquez de vous retrouver avec le modèle de domaine anémique, décrit dans la section suivante.

### <a name="rich-domain-model-versus-anemic-domain-model"></a>Modèle de domaine riche et modèle de domaine anémique

Dans son billet [AnemicDomainModel](https://martinfowler.com/bliki/AnemicDomainModel.html), Martin Fowler décrit un modèle de domaine anémique de la façon suivante :

Le symptôme de base d’un modèle de domaine anémique est qu’à première vue, il ressemble à la réalité. Il s’agit d’objets souvent nommés d’après les noms figurant dans l’espace de domaine. Ces objets sont connectés avec les riches relations et structure que présentent les véritables modèles de domaine. L’imposture apparaît quand vous examinez le comportement et que vous réalisez qu’il n’y a pas vraiment de comportement sur ces objets, ce qui en fait ni plus ni moins des contenants de méthodes getter et setter.

Bien entendu, quand vous utilisez un modèle de domaine anémique, il est utilisé à partir d’un ensemble d’objets de service (généralement nommé *couche métier*) qui capture toute la logique métier ou du domaine. La couche métier est posée sur le modèle de données et utilise ce dernier simplement comme des données.

Le modèle de domaine anémique est simplement une conception de style procédural. Les objets d’entité anémique ne sont pas des objets réels, car ils n’ont pas de comportement (méthodes). Ils contiennent uniquement des propriétés de données et ne correspondent donc pas à une conception orientée objet. En plaçant tout le comportement dans des objets de service (la couche métier), vous finissez par obtenir du [code spaghetti](https://en.wikipedia.org/wiki/Spaghetti_code) ou des [scripts de transaction](https://martinfowler.com/eaaCatalog/transactionScript.html). Vous perdez donc les avantages liés au modèle de domaine.

Quand même, si votre microservice ou contexte limité est très simple (un service CRUD), le modèle de domaine anémique sous la forme d’objets d’entité avec seulement des propriétés de données peut vous suffire, et l’implémentation de modèles DDD plus complexes peut ne pas valoir le coup. Dans ce cas, il s’agit simplement d’un modèle de persistance, car vous avez intentionnellement créé une entité avec des données uniquement pour les besoins de CRUD.

C’est pourquoi les architectures des microservices conviennent parfaitement à une approche à plusieurs architectures dépendant de chaque contexte limité. Par exemple, dans eShopOnContainers, le microservice de passation de commandes implémente des modèles DDD, contrairement au microservice de catalogue, qui est un simple service CRUD.

Certaines personnes disent que le modèle de domaine anémique est un anti-modèle. Il dépend vraiment de ce que vous implémentez. Si le microservice que vous créez est suffisamment simple (par exemple, un service CRUD), le modèle de domaine anémique n’est pas un anti-modèle. Toutefois, si vous avez besoin de vous confronter à la complexité du domaine d’un microservice dont le grand nombre de règles d’entreprise est en constante évolution, le modèle de domaine anémique peut être un anti-modèle pour ce microservice ou contexte limité. Dans ce cas, une conception en tant que modèle riche avec des entités contenant des données en plus d’un comportement, ainsi que l’implémentation de modèles DDD supplémentaires (agrégats, objets de valeur, etc.) peut offrir des avantages énormes pour le succès à long terme d’un tel microservice.

#### <a name="additional-resources"></a>Ressources supplémentaires

- **DevIQ. Entité de domaine** \
  <https://deviq.com/entity/>

- **Martin Fowler. Le modèle de domaine** \
  <https://martinfowler.com/eaaCatalog/domainModel.html>

- **Martin Fowler. Le modèle anémique de domaine** \
  <https://martinfowler.com/bliki/AnemicDomainModel.html>

### <a name="the-value-object-pattern"></a>Le modèle Objet de valeur

Comme l’a noté Eric Evans, « de nombreux objets n’ont pas d’identité conceptuelle. Ces objets décrivent certaines caractéristiques d’une chose ».

Une entité nécessite une identité, mais il existe de nombreux objets dans un système qui n’en ont pas besoin, comme le modèle Objet de valeur. Un objet de valeur est un objet sans identité conceptuelle qui décrit un aspect de domaine. Ce sont des objets que vous instanciez pour représenter des éléments de conception qui ne vous concernent que temporairement. Il vous importe de savoir *ce* qu’ils sont, pas *qui* ils sont. Les nombres et les chaînes en sont des exemples, mais il peut aussi s’agir de concepts plus généraux comme des groupes d’attributs.

Une entité dans un microservice peut ne pas être une entité dans un autre microservice, puisque dans le deuxième cas, le contexte limité peut avoir une signification différente. Par exemple, une adresse dans une application de commerce électronique peut ne pas avoir du tout d’identité, puisqu’elle peut représenter uniquement un groupe d’attributs du profil de client d’une personne ou d’une entreprise. Dans ce cas, l’adresse doit être classée en tant qu’objet de valeur. Toutefois, dans une application destinée à un fournisseur d’énergie électrique, l’adresse du client peut s’avérer importante pour le domaine d’entreprise. Par conséquent, l’adresse doit avoir une identité pour que le système de facturation puisse être directement lié à l’adresse. Dans cet exemple, une adresse doit être classée en tant qu’entité de domaine.

Une personne désignée par un prénom et un nom est généralement une entité, car elle a une identité, même si ce prénom et ce nom coïncident avec un autre ensemble de valeurs, par exemple s’ils font également référence à une autre personne.

Les objets de valeur sont difficiles à gérer dans les bases de données relationnelles et les OUM comme Entity Framework (EF), tandis que dans les bases de données orientées vers les documents, ils sont plus faciles à implémenter et à utiliser.

EF Core 2.0 et les versions ultérieures comprennent la fonction [Entités possédées](https://devblogs.microsoft.com/dotnet/announcing-entity-framework-core-2-0/#owned-entities-and-table-splitting) qui facilite la manipulation d’objets à valeur ajoutée, comme nous le verrons en détail plus tard.

#### <a name="additional-resources"></a>Ressources supplémentaires

- **Martin Fowler. Modèle d’objet de valeur** \
  <https://martinfowler.com/bliki/ValueObject.html>

- **Objet de valeur** \
  <https://deviq.com/value-object/>

- **Objets de valeur dans le développement piloté par les tests** \
  [https://leanpub.com/tdd-ebook/read\#leanpub-auto-value-objects](https://leanpub.com/tdd-ebook/read#leanpub-auto-value-objects)

- **Eric Evans. Conception axée sur le domaine : s’attaquer à la complexité au cœur du logiciel.** (Livre incluant une discussion sur les objets de valeur) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

### <a name="the-aggregate-pattern"></a>Le modèle Agrégat

Un modèle de domaine contient des clusters d’entités de données et de processus différents qui peuvent contrôler une partie importante des fonctionnalités, comme le déroulement des commandes ou l’inventaire. Un agrégat est une unité DDD plus fine qui décrit un cluster ou groupe d’entités et de comportements pouvant être traité comme une unité cohésive.

En règle générale, vous définissez un agrégat selon les transactions dont vous avez besoin. Une commande qui contient aussi une liste d’articles constitue un exemple classique. Un article correspond généralement à une entité. Mais il s’agit d’une entité enfant au sein de l’agrégat de commande, qui contient aussi l’entité de commande en tant qu’entité racine, généralement appelée racine d’agrégat.

Il peut s’avérer difficile d’identifier les agrégats. Un agrégat est un groupe d’objets qui doivent être cohérents ensemble, mais vous ne pouvez pas simplement choisir un groupe d’objets et les appeler agrégat. Vous devez commencer avec un concept de domaine et réfléchir aux entités utilisées dans les transactions les plus courantes liées à ce concept. Ce sont ces entités devant être cohérentes du point de vue transactionnel qui forment un agrégat. Réfléchir aux opérations transactionnelles constitue probablement la meilleure façon d’identifier des agrégats.

### <a name="the-aggregate-root-or-root-entity-pattern"></a>Le modèle Racine d’agrégat ou Entité racine

Un agrégat se compose d’au moins une entité : la racine d’agrégat, également appelée entité racine ou entité principale. De plus, il peut avoir plusieurs entités enfants et objets de valeur, qui fonctionnent tous ensemble pour implémenter le comportement et les transactions nécessaires.

Une racine d’agrégat a pour but de garantir la cohérence de l’agrégat ; elle doit être le seul point d’entrée pour les mises à jour de l’agrégat par le biais de méthodes ou d’opérations dans la classe de racine d’agrégat. Vous devez apporter des modifications aux entités au sein de l’agrégat uniquement par le biais de la racine d’agrégat. Celle-ci protège la cohérence de l’agrégat, en tenant compte de tous les invariants et de toutes les règles de cohérence à respecter dans votre agrégat. Si vous modifiez séparément une entité enfant ou un objet de valeur, la racine d’agrégat ne peut pas vérifier que l’agrégat est dans un état valide. Il serait alors comme une table avec un pied qui bouge. Le maintien de la cohérence est le principal but de la racine d’agrégat.

Dans la figure 7-9, vous pouvez voir des exemples d’agrégats, comme l’agrégat Buyer (Acheteur), qui contient une seule entité (la racine d’agrégat Buyer). L’agrégat de commande (Order) contient plusieurs entités et un objet de valeur.

![Diagramme comparant un agrégat d’acheteur et un agrégat de commande.](./media/microservice-domain-model/buyer-order-aggregate-pattern.png)

**Figure 7-9**. Exemples d’agrégats avec une seule entité ou plusieurs entités

Un modèle de domaine DDD est composé d’agrégats ; un agrégat peut avoir une ou plusieurs entités, et inclure aussi des objets de valeur. Notez que l’agrégat d’acheteur (Buyer) peut avoir des entités enfants supplémentaires, en fonction de votre domaine, comme c’est le cas dans le microservice de passation de commandes dans l’application de référence eShopOnContainers. La figure 7-9 illustre un cas où l’acheteur a une seule entité, qui est un exemple d’agrégat contenant seulement une racine d’agrégat.

Afin de maintenir la séparation des agrégats et de conserver des limites claires entre eux, il est conseillé, dans un modèle de domaine DDD, d’interdire la navigation directe entre les agrégats et d’implémenter uniquement le champ de clé étrangère comme dans le [modèle de domaine du microservice de passation de commandes](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs) dans eShopOnContainers. L’entité de commande (Order) a uniquement un champ de clé étrangère pour l’acheteur, mais pas de propriété de navigation EF Core, comme le montre le code suivant :

```csharp
public class Order : Entity, IAggregateRoot
{
    private DateTime _orderDate;
    public Address Address { get; private set; }
    private int? _buyerId; //FK pointing to a different aggregate root
    public OrderStatus OrderStatus { get; private set; }
    private readonly List<OrderItem> _orderItems;
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;
    // ... Additional code
}
```

L’identification et l’utilisation des agrégats nécessitent des recherches et de l’expérience. Pour plus d’informations, consultez la liste suivante de ressources supplémentaires.

#### <a name="additional-resources"></a>Ressources supplémentaires

- **Vaughn Vernon. Conception d’agrégat efficace - Partie I : Modélisation d’un agrégat unique** (à partir de <http://dddcommunity.org/>)
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_1.pdf>

- **Vaughn Vernon. Conception d’agrégats efficaces - Partie II : Faire en sorte que les agrégats fonctionnent ensemble** (à partir de <http://dddcommunity.org/>)
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf>

- **Vaughn Vernon. Conception d’agrégats efficaces - Partie III : Obtenir l’aperçu par la découverte** (de <http://dddcommunity.org/>)
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_3.pdf>

- **Sergey Grybniak. Modèles de conception tactique DDD** \
  <https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part>

- **Chris Richardson. Développer des microservices transactionnels à l’aide d’agrégats** \
  <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson>

- **DevIQ. Le modèle d’agrégat** \
  <https://deviq.com/aggregate-pattern/>

>[!div class="step-by-step"]
>[Suivant précédent](ddd-oriented-microservice.md)
>[Next](net-core-microservice-domain-model.md)
