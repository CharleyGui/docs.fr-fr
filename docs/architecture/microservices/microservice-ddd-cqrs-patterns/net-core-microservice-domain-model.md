---
title: Implémentation d’un modèle de domaine de microservice avec .NET
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Accéder aux détails d’implémentation d’un modèle de domaine orienté DDD.
ms.date: 01/13/2021
ms.openlocfilehash: 9689058b77701eee35ef018ed2e3f18bd648b0f4
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188268"
---
# <a name="implement-a-microservice-domain-model-with-net-core"></a>Implémenter un modèle de domaine de microservice avec .NET Core

Dans la section précédente, les modèles et principes fondamentaux de conception d’un modèle de domaine ont été expliqués. À présent, il est temps d’explorer les différentes façons d’implémenter le modèle de domaine à l’aide du code .NET (code C simple \# ) et EF Core. Votre modèle de domaine sera composé simplement de votre code. Il présentera seulement les exigences en matière de modèle EF Core, mais pas de dépendances réelles sur EF. Vous ne devez pas avoir de dépendances dures ni de références à EF Core ou n’importe quel autre ORM dans votre modèle de domaine.

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a>Structure de modèle de domaine dans une bibliothèque .NET Standard personnalisée

L’organisation des dossiers utilisée pour l’application de référence eShopOnContainers montre le modèle DDD pour l’application. Vous pouvez trouver qu’une organisation des dossiers différente communique plus clairement les choix de conception effectués pour votre application. Comme vous pouvez le voir dans la figure 7-10, il existe deux agrégats dans le modèle de domaine de commandes : l’agrégat des commandes et l’agrégat des acheteurs. Chaque agrégat est un groupe d’entités de domaine et d’objets de valeur, bien que vous puissiez également avoir un agrégat composé d’une entité de domaine unique (la racine d’agrégat ou l’entité racine).

:::image type="complex" source="./media/net-core-microservice-domain-model/ordering-microservice-container.png" alt-text="Capture d’écran du projet Ordering. Domain dans Explorateur de solutions.":::
La vue Explorateur de solutions pour le projet Ordering. Domain, qui affiche le dossier AggregatesModel contenant les dossiers BuyerAggregate et OrderAggregate, chacun contenant ses classes d’entité, ses fichiers objet de valeur, etc.
:::image-end:::

**Figure 7-10.** Structure de modèle de domaine pour le microservice de commandes dans eShopOnContainers

En outre, la couche de modèle de domaine inclut les contrats de dépôt (interfaces) qui représentent les exigences en matière d’infrastructure de votre modèle de domaine. En d’autres termes, ces interfaces indiquent les dépôts et les méthodes que la couche d’infrastructure doit implémenter. Il est essentiel que l’implémentation des dépôts soit placée en dehors de la couche de modèle de domaine dans la bibliothèque de couches d’infrastructure, de sorte que la couche de modèle de domaine n’est pas « contaminée » par l’API ou les classes des technologies d’infrastructure, comme Entity Framework.

Vous pouvez également voir un dossier [SeedWork](https://martinfowler.com/bliki/Seedwork.html) qui contient des classes de base personnalisées que vous pouvez utiliser comme base pour vos entités de domaine et objets de valeur, de sorte que vous n’avez pas de code redondant dans la classe d’objets de chaque domaine.

## <a name="structure-aggregates-in-a-custom-net-standard-library"></a>Structurer des agrégats dans une bibliothèque .NET Standard personnalisée

Un agrégat fait référence à un cluster d’objets de domaine regroupés pour assurer une cohérence transactionnelle. Ces objets peuvent être des instances d’entités (un exemple est la racine d’agrégat ou l’entité racine) ainsi que tous les autres objets de valeur.

La cohérence transactionnelle signifie qu’il est certain qu’un agrégat est cohérent et à jour à la fin d’une action métier. Par exemple, l’agrégat des commandes du modèle de domaine de microservice de commandes eShopOnContainers est composé comme indiqué dans la figure 7-11.

:::image type="complex" source="./media/net-core-microservice-domain-model/vs-solution-explorer-order-aggregate.png" alt-text="Capture d’écran du dossier OrderAggregate et de ses classes.":::
Vue détaillée du dossier OrderAggregate : Address.cs est un objet de valeur, IOrderRepository est une interface de référentiel, Order.cs est une racine d’agrégat, OrderItem.cs est une entité enfant et OrderStatus.cs est une classe d’énumération.
:::image-end:::

**Figure 7-11.** Agrégat des commandes dans une solution Visual Studio

Si vous ouvrez l’un des fichiers dans un dossier d’agrégats, vous pouvez voir comment il est marqué en tant qu’interface ou classe de base personnalisée, comme un objet entité ou de valeur, tel qu’implémenté dans le dossier [SeedWork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork).

## <a name="implement-domain-entities-as-poco-classes"></a>Implémenter des entités de domaine en tant que classes OCT

Vous implémentez un modèle de domaine dans .NET en créant des classes OCT qui implémentent vos entités de domaine. Dans l’exemple suivant, la classe Order est définie comme une entité et également comme une racine d’agrégat. Étant donné que la classe Order dérive de la classe de base Entity, elle peut réutiliser le code commun lié aux entités. Gardez à l’esprit que ces classes de base et interfaces sont définies par vous dans le projet de modèle de domaine ; il s’agit donc de votre code et non d’un code d’infrastructure provenant d’un ORM tel qu’EF.

```csharp
// COMPATIBLE WITH ENTITY FRAMEWORK CORE 5.0
// Entity is a custom base class with the ID
public class Order : Entity, IAggregateRoot
{
    private DateTime _orderDate;
    public Address Address { get; private set; }
    private int? _buyerId;

    public OrderStatus OrderStatus { get; private set; }
    private int _orderStatusId;

    private string _description;
    private int? _paymentMethodId;

    private readonly List<OrderItem> _orderItems;
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;

    public Order(string userId, Address address, int cardTypeId, string cardNumber, string cardSecurityNumber,
            string cardHolderName, DateTime cardExpiration, int? buyerId = null, int? paymentMethodId = null)
    {
        _orderItems = new List<OrderItem>();
        _buyerId = buyerId;
        _paymentMethodId = paymentMethodId;
        _orderStatusId = OrderStatus.Submitted.Id;
        _orderDate = DateTime.UtcNow;
        Address = address;

        // ...Additional code ...
    }

    public void AddOrderItem(int productId, string productName,
                            decimal unitPrice, decimal discount,
                            string pictureUrl, int units = 1)
    {
        //...
        // Domain rules/logic for adding the OrderItem to the order
        // ...

        var orderItem = new OrderItem(productId, productName, unitPrice, discount, pictureUrl, units);

        _orderItems.Add(orderItem);

    }
    // ...
    // Additional methods with domain rules/logic related to the Order aggregate
    // ...
}
```

Il est important de noter qu’il s’agit d’une entité de domaine implémentée comme une classe OCT. Elle n’a aucune dépendance directe sur Entity Framework Core ni un autre framework d’infrastructure. Cette implémentation est telle qu’elle devrait être dans DDD, juste le code C# qui implémente un modèle de domaine.

En outre, la classe est décorée avec une interface nommée IAggregateRoot. Cette interface est une interface vide, parfois appelée *interface de marqueur*, qui est utilisée uniquement pour indiquer que cette classe d’entité est également une racine d’agrégat.

Une interface de marqueur est parfois considérée comme un anti-modèle ; toutefois, il s’agit également d’un moyen adéquat pour marquer une classe, en particulier quand cette interface peut évoluer. Un attribut peut représenter l’autre choix pour le marqueur, mais il est plus rapide d’afficher la classe de base (Entity) en regard de l’interface IAggregate au lieu de placer un marqueur d’attribut Aggregate au-dessus de la classe. Il s’agit d’une question de préférences dans tous les cas.

Le fait d’avoir une racine d’agrégat signifie que la majeure partie du code lié à la cohérence et aux règles d’entreprise des entités de l’agrégat doit être implémentée en tant que méthodes dans la classe racine d’agrégat d’ordre (par exemple, AddOrderItem lors de l’ajout d’un objet OrderItem à l’agrégat). Vous ne devez pas créer ni mettre à jour des objets OrderItems indépendamment ou directement ; la classe AggregateRoot doit garder le contrôle et assurer la cohérence de toutes les opérations de mise à jour par rapport à ses entités enfants.

## <a name="encapsulate-data-in-the-domain-entities"></a>Encapsuler des données dans les entités de domaine

Un problème courant avec les modèles d’entité est qu’ils exposent des propriétés de navigation de collection en tant que types de listes accessibles publiquement. Cela permet à tout développeur collaborateur de manipuler le contenu de ces types de collections, de contourner ainsi des règles métier importantes relatives à la collection et de laisser éventuellement l’objet dans un état non valide. La solution consiste à exposer un accès en lecture seule aux collections associées et à fournir explicitement des méthodes qui définissent des moyens par lesquels les clients peuvent les manipuler.

Dans le code précédent, notez que beaucoup d’attributs sont en lecture seule ou privés, et peuvent uniquement être mis à jour par les méthodes de classe. Toute mise à jour tient donc compte des invariants de domaine d’entreprise et de la logique spécifiée dans les méthodes de classe.

Par exemple, en suivant les modèles DDD, **vous ne devez *pas* effectuer les opérations suivantes** à partir de toute méthode de gestionnaire de commandes ou classe de couche d’application (en fait, il est normalement impossible pour vous de les effectuer) :

```csharp
// WRONG ACCORDING TO DDD PATTERNS – CODE AT THE APPLICATION LAYER OR
// COMMAND HANDLERS
// Code in command handler methods or Web API controllers
//... (WRONG) Some code with business logic out of the domain classes ...
OrderItem myNewOrderItem = new OrderItem(orderId, productId, productName,
    pictureUrl, unitPrice, discount, units);

//... (WRONG) Accessing the OrderItems collection directly from the application layer // or command handlers
myOrder.OrderItems.Add(myNewOrderItem);
//...
```

Dans ce cas, la méthode Add est purement une opération permettant d’ajouter des données, avec un accès direct à la collection OrderItems. Par conséquent, une grande partie de la logique de domaine, des règles ou des validations liées à cette opération avec les entités enfants est répartie sur la couche d’application (gestionnaires de commandes et contrôleurs d’API web).

Si vous examinez la racine d’agrégat, elle ne peut pas garantir ses invariants, sa validité ni sa cohérence. Vous obtiendrez finalement un code spaghetti ou un code de script transactionnel.

Pour suivre les modèles DDD, les entités ne doivent pas avoir de méthodes setter publiques dans aucune propriété. Les modifications apportées à une entité doivent être pilotées par des méthodes explicites avec un langage omniprésent clair sur la modification effectuée.

En outre, les collections dans l’entité (par exemple, les articles de la commande) doivent être des propriétés en lecture seule (méthode AsReadOnly abordée plus loin). Vous devez pouvoir effectuer la mise à jour uniquement à partir des méthodes de classe de la racine d’agrégat ou des méthodes de l’entité enfant.

Comme vous pouvez le voir dans le code de la racine d’agrégat Order, tous les accesseurs set doivent être privés ou au moins en lecture seule en externe, de sorte que toute opération sur les données de l’entité ou ses entités enfants doit être effectuée par le biais de méthodes dans la classe d’entité. La cohérence est ainsi assurée de manière contrôlée et orientée objet au lieu d’implémenter un code de script transactionnel.

L’extrait de code suivant montre la façon correcte de coder la tâche d’ajout d’un objet OrderItem à l’agrégat Order.

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object's business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

Dans cet extrait, une grande partie des validations ou de la logique relatives à la création d’un objet OrderItem est sous le contrôle de la racine d’agrégat Order, dans la méthode AddOrderItem, en particulier les validations et logique liées à d’autres éléments dans l’agrégat. Par exemple, vous pouvez obtenir le même article suite à plusieurs appels à AddOrderItem. Dans cette méthode, vous pouvez examiner les articles et regrouper les mêmes articles dans un seul objet OrderItem avec plusieurs unités. En outre, s’il existe différents montants de remise alors que l’ID de produit est le même, vous devez probablement appliquer la remise la plus élevée. Ce principe s’applique à toute autre logique de domaine pour l’objet OrderItem.

En outre, la nouvelle opération OrderItem(params) sera également contrôlée et effectuée par la méthode AddOrderItem à partir de la racine d’agrégat Order. Par conséquent, une grande partie des validations ou de la logique liées à cette opération (en particulier tout ce qui a un impact sur la cohérence entre les autres entités enfants) est regroupée à un seul endroit au sein de la racine d’agrégat. Il s’agit de l’objectif ultime du modèle de racine d’agrégat.

Quand vous utilisez Entity Framework Core 1.1 ou version ultérieure, une entité DDD peut être mieux exprimée, car elle permet un [mappage à des champs](/ef/core/modeling/backing-field) en plus des propriétés. Cela est utile quand vous protégez des collections d’entités enfants ou d’objets de valeur. Avec cette amélioration, vous pouvez utiliser de simples champs privés au lieu de propriétés, et vous pouvez implémenter toute mise à jour de la collection de champs dans les méthodes publiques et fournir un accès en lecture seule via la méthode AsReadOnly.

Dans DDD, vous souhaitez mettre à jour l’entité uniquement par le biais des méthodes de l’entité (ou du constructeur) afin de contrôler tout invariant et la cohérence des données, de sorte que les propriétés sont définies uniquement avec un accesseur Get. Les propriétés sont associées à des champs privés. Les membres privés sont uniquement accessibles à partir de la classe. Toutefois, il existe une exception : EF Core doit également définir ces champs (afin de pouvoir retourner l’objet avec les valeurs appropriées).

### <a name="map-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a>Mapper des propriétés avec uniquement des accesseurs get aux champs de la table de base de données

Le mappage de propriétés aux colonnes de la table de base de données n’est pas une responsabilité de domaine, mais fait partie de la couche d’infrastructure et de persistance. Nous le signalons ici uniquement pour que vous soyez informé des nouvelles fonctionnalités dans EF Core 1.1 ou version ultérieure liées au mode de modélisation des entités. D’autres détails sur ce sujet sont décrits dans la section relative à l’infrastructure et la persistance.

Quand vous utilisez EF Core 1.0 ou une version ultérieure, dans le DbContext, vous devez mapper, les propriétés qui sont définies uniquement avec des méthodes getter aux champs réels de la table de base de données. Pour ce faire, utilisez la méthode HasField de la classe PropertyBuilder.

### <a name="map-fields-without-properties"></a>Mapper des champs sans propriétés

Avec la fonctionnalité dans EF Core 1.1 ou version ultérieure permettant de mapper des colonnes aux champs, il est également possible de ne pas utiliser de propriétés. Au lieu de cela, vous pouvez juste mapper des colonnes d’une table aux champs. Cette fonctionnalité est couramment utilisée dans le cadre des champs privés pour un état interne qui ne doit pas être accessible depuis l’extérieur de l’entité.

Par exemple, dans l’exemple de code OrderAggregate précédent, il existe plusieurs champs privés, tels que le champ `_paymentMethodId`, sans propriété associée pour une méthode setter ou un accesseur Get. Ce champ peut également être calculé dans la logique métier de la commande et utilisé à partir des méthodes de la commande, mais il doit également être conservé dans la base de données. Ainsi, dans EF Core (depuis la version 1.1), il existe un moyen de mapper un champ sans une propriété associée à une colonne dans la base de données. Cela est également expliqué dans la section [Couche d’infrastructure](ddd-oriented-microservice.md#the-infrastructure-layer) de ce guide.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Vaughn Vernon. Modélisation des agrégats avec DDD et Entity Framework.** Notez qu’il ne s’agit *pas* d’Entity Framework Core. \
  <https://kalele.io/blog-posts/modeling-aggregates-with-ddd-and-entity-framework/>

- **Julie Lerman. Points de données-codage pour la conception de Domain-Driven : conseils pour les développeurs de Data-Focused** \
  <https://docs.microsoft.com/archive/msdn-magazine/2013/august/data-points-coding-for-domain-driven-design-tips-for-data-focused-devs>

- **UDI Dahan. Comment créer des modèles de domaine entièrement encapsulés** \
  <https://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/>

> [!div class="step-by-step"]
> [Précédent](microservice-domain-model.md) 
>  [Suivant](seedwork-domain-model-base-classes-interfaces.md)
