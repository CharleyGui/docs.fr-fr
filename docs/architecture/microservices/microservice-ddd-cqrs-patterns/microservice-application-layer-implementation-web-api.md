---
title: Implémentation de la couche Application de microservices à l’aide de l’API web
description: Comprendre l’injection de dépendances et les modèles de médiateur et leurs détails d’implémentation dans la couche d’application de l’API Web.
ms.date: 01/30/2020
ms.openlocfilehash: 3efa4939bb8762534af398d4e92361e81e668b85
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144602"
---
# <a name="implement-the-microservice-application-layer-using-the-web-api"></a>Implémenter la couche Application des microservices avec l’API web

## <a name="use-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a>Utiliser l’injection de dépendances pour injecter des objets d’infrastructure dans votre couche Application

Comme mentionné précédemment, la couche Application peut être implémentée dans le cadre de l’artefact (assembly) que vous générez, comme dans un projet d’API web ou un projet d’application web MVC. Dans le cas d’un microservice généré avec ASP.NET Core, la couche Application correspond habituellement à la bibliothèque de votre API web. Pour séparer ce qui vient d’ASP.NET Core (son infrastructure plus vos contrôleurs) de votre code de couche Application personnalisé, vous pouvez également placer votre couche Application dans une bibliothèque de classes distincte, mais ce n’est pas obligatoire.

Par exemple, le code de la couche Application du microservice Ordering est directement implémenté dans le cadre du projet **Ordering.API** (un projet d’API web ASP.NET Core), comme le montre la figure 7-23.

:::image type="complex" source="./media/microservice-application-layer-implementation-web-api/ordering-api-microservice.png" alt-text="Capture d’écran du microservice Ordering. API dans le Explorateur de solutions.":::
La vue Explorateur de solutions du microservice Ordering.API, montrant les sous-dossiers sous le dossier Application : Comportements, Commandes, DomainEventHandlers, IntegrationEvents, Modèles, Requêtes et Validations.
:::image-end:::

**Figure 7-23**. Couche Application dans le projet d’API web ASP.NET Core Ordering.API

ASP.NET Core inclut un simple [conteneur IoC intégré](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (représenté par l’interface IserviceProvider) qui prend en charge l’injection de constructeurs par défaut, et ASP.NET rend certains services disponibles par le biais de l’injection de dépendances. ASP.NET Core utilise le terme *service* pour tous les types que vous inscrivez, qui seront injectés par injection de dépendances. Vous configurez les services du conteneur intégré dans la méthode ConfigureServices de la classe Startup de votre application. Vos dépendances sont implémentées dans les services dont un type a besoin et que vous inscrivez dans le conteneur IoC.

En règle générale, vous injectez des dépendances qui implémentent des objets d’infrastructure. Un dépôt est une dépendance type à injecter. Mais vous pouvez injecter toutes vos autres dépendances d’infrastructure. Pour simplifier les implémentations, vous pouvez injecter directement votre objet de modèle Unité de travail (objet DbContext EF), car DBContext est également l’implémentation de vos objets de persistance d’infrastructure.

Dans l’exemple suivant, vous pouvez voir comment .NET Core injecte les objets de dépôt requis par le biais du constructeur. La classe est un gestionnaire de commandes, que nous allons expliquer dans la section suivante.

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

Elle utilise les dépôts injectés pour exécuter la transaction et rendre persistantes les modifications d’état. Il importe peu que cette classe soit un gestionnaire de commandes, une méthode de contrôleur de l’API web ASP.NET Core ou un [service d’application DDD](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/). Il s’agit en fin de compte d’une classe simple qui utilise des dépôts, des entités de domaine et une autre coordination des applications d’une manière similaire à un gestionnaire de commandes. L’injection de dépendances fonctionne de la même manière pour toutes les classes mentionnées, comme dans l’exemple qui utilise l’injection de dépendances selon le constructeur.

### <a name="register-the-dependency-implementation-types-and-interfaces-or-abstractions"></a>Inscrire les types et les interfaces ou les abstractions d’implémentation des dépendances

Avant d’utiliser les objets injectés par le biais de constructeurs, vous devez savoir où inscrire les interfaces et classes qui produisent les objets injectés dans vos classes d’application par le biais de l’injection de dépendances. (Comme l’injection de dépendances basée sur le constructeur, comme indiqué précédemment.)

#### <a name="use-the-built-in-ioc-container-provided-by-aspnet-core"></a>Utiliser le conteneur IoC intégré fourni par ASP.NET Core

Quand vous utilisez le conteneur IoC intégré fourni par ASP.NET Core, vous inscrivez les types à insérer dans la méthode ConfigureServices dans le fichier Startup.cs, comme dans le code suivant :

```csharp
// Registration of types into ASP.NET Core built-in container
public void ConfigureServices(IServiceCollection services)
{
    // Register out-of-the-box framework services.
    services.AddDbContext<CatalogContext>(c =>
        c.UseSqlServer(Configuration["ConnectionString"]),
        ServiceLifetime.Scoped);

    services.AddMvc();
    // Register custom application dependencies.
    services.AddScoped<IMyCustomRepository, MyCustomSQLRepository>();
}
```

Le modèle le plus courant pour inscrire des types dans un conteneur IoC consiste à inscrire une paire de types : une interface et sa classe d’implémentation associée. Ensuite, quand vous demandez un objet au conteneur IoC par le biais d’un constructeur, vous demandez un objet d’un certain type d’interface. Par exemple, dans l’exemple précédent, la dernière ligne indique que lorsqu’un des constructeurs dépendent d’IMyCustomRepository (interface ou abstraction), le conteneur IoC injecte une instance de la classe d’implémentation MyCustomSQLServerRepository.

#### <a name="use-the-scrutor-library-for-automatic-types-registration"></a>Utiliser la bibliothèque Scrutor pour l’inscription automatique des types

Quand vous utilisez l’injection de dépendances dans .NET Core, vous pouvez avoir envie d’analyser un assembly et d’inscrire automatiquement ses types par convention. Cette fonctionnalité n’est pas disponible dans ASP.NET Core pour le moment. Toutefois, vous pouvez utiliser la bibliothèque [Scrutor](https://github.com/khellang/Scrutor) à la place. Cette approche est pratique lorsque vous avez des dizaines de types à inscrire dans votre conteneur IoC.

#### <a name="additional-resources"></a>Ressources supplémentaires

- **Matthew King. Inscription de services avec scrutor** \
  <https://www.mking.net/blog/registering-services-with-scrutor>

- **Kristian Hellang. Scrutor.** Dépôt GitHub. \
  <https://github.com/khellang/Scrutor>

#### <a name="use-autofac-as-an-ioc-container"></a>Utiliser Autofac comme conteneur IoC

Vous pouvez également utiliser d’autres conteneurs IoC et les incorporer dans le pipeline ASP.NET Core, comme dans le microservice de passation de commandes dans eShopOnContainers, qui utilise [Autofac](https://autofac.org/). Quand vous utilisez Autofac, vous inscrivez généralement les types par le biais de modules, ce qui vous permet de fractionner les types d’inscription entre plusieurs fichiers selon leur emplacement, tout comme vous pourriez distribuer les types d’application dans plusieurs bibliothèques de classes.

Par exemple, voici le [module d’application Autofac](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) pour le projet d’[API web Ordering.API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) avec les types que vous avez besoin d’injecter.

```csharp
public class ApplicationModule : Autofac.Module
{
    public string QueriesConnectionString { get; }
    public ApplicationModule(string qconstr)
    {
        QueriesConnectionString = qconstr;
    }

    protected override void Load(ContainerBuilder builder)
    {
        builder.Register(c => new OrderQueries(QueriesConnectionString))
            .As<IOrderQueries>()
            .InstancePerLifetimeScope();
        builder.RegisterType<BuyerRepository>()
            .As<IBuyerRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<OrderRepository>()
            .As<IOrderRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<RequestManager>()
            .As<IRequestManager>()
            .InstancePerLifetimeScope();
   }
}
```

Autofac a également une fonctionnalité pour [analyser les assemblys et inscrire les types selon des conventions de nommage](https://autofac.readthedocs.io/en/latest/register/scanning.html).

Le processus et les concepts d’inscription sont très similaires à la façon dont vous pouvez inscrire des types auprès du conteneur IoC ASP.NET Core intégré, mais la syntaxe avec Autofac est un peu différente.

Dans l’exemple de code, l’abstraction IOrderRepository est inscrite de concert avec la classe d’implémentation OrderRepository. Cela signifie que chaque fois qu’un constructeur déclare une dépendance par le biais de l’abstraction ou de l’interface IOrderRepository, le conteneur IoC injecte une instance de la classe OrderRepository.

Le type d’étendue d’instance détermine la façon dont une instance est partagée entre les demandes du même service ou de la même dépendance. Lorsqu’une demande est effectuée pour une dépendance, le conteneur IoC peut retourner :

- Une instance unique par étendue de durée de vie (désignée dans le conteneur IoC ASP.NET Core comme *délimitée*).

- Une nouvelle instance par dépendance (désignée dans le conteneur IoC ASP.NET Core comme *temporaire*).

- Une instance unique partagée entre tous les objets à l’aide du conteneur IoC (désignée dans le conteneur IoC ASP.NET Core comme *singleton*).

#### <a name="additional-resources"></a>Ressources supplémentaires

- **Présentation de l’injection de dépendances dans ASP.NET Core** \
  [https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection](/aspnet/core/fundamentals/dependency-injection)

- **Autofac.** Documentation officielle. \
  <https://docs.autofac.org/en/latest/>

- **Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes - Cesar de la Torre.** \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="implement-the-command-and-command-handler-patterns"></a>Implémenter les modèles Command (Commande) et Command Handler (Gestionnaire de commandes)

Dans l’exemple d’injection de dépendances par le biais d’un constructeur mentionné dans la section précédente, le conteneur IoC injectait des dépôts par le biais d’un constructeur dans une classe. Mais où ont-ils été injectés exactement ? Dans une API Web simple (par exemple, le microservice de catalogue dans eShopOnContainers), vous les injectez au niveau des contrôleurs MVC, dans un constructeur de contrôleur, dans le cadre du pipeline de demande de ASP.NET Core. Toutefois, dans le code initial de cette section (la classe [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) du service Ordering.API dans eShopOnContainers), l’injection de dépendances s’effectue par le biais du constructeur d’un gestionnaire de commandes particulier. Expliquons ce qu’est un gestionnaire de commandes et pourquoi l’utiliser.

Le modèle Commande est intrinsèquement lié au modèle CQRS présenté précédemment dans le présent guide. Le modèle CQRS a deux côtés. Le premier côté concerne les requêtes, l’utilisation de requêtes simplifiées avec le micro ORM [Dapper](https://github.com/StackExchange/dapper-dot-net), précédemment décrit. Le second côté concerne les commandes, qui sont le point de départ des transactions et le canal d’entrée depuis l’extérieur du service.

Comme le montre la figure 7-24, le modèle se base sur l’acceptation des commandes du côté client, leur traitement en fonction des règles du modèle de domaine et enfin, sur la persistance des états avec les transactions.

![Diagramme montrant le workflow de haut niveau du client au niveau de la base de données.](./media/microservice-application-layer-implementation-web-api/high-level-writes-side.png)

**Figure 7-24**. Affichage de haut niveau des commandes ou « côté transactionnel » dans un modèle CQRS

La figure 7-24 montre que l’application d’interface utilisateur envoie une commande via l’API qui obtient à un `CommandHandler` , qui dépend du modèle de domaine et de l’infrastructure, pour mettre à jour la base de données.

### <a name="the-command-class"></a>La classe de commande

Une commande est une demande faite au système d’effectuer une action qui modifie son état. Les commandes sont impératives et doivent être traitées une seule fois.

Étant donné que les commandes sont impératives, leur nom commence généralement par un verbe (par exemple, « Create » ou « Update ») et elles peuvent inclure le type d’agrégat, comme CreateOrderCommand. Contrairement à un événement, une commande n’est pas un fait passé ; il s’agit uniquement d’une demande qui peut donc être refusée.

Les commandes peuvent provenir de l’interface utilisateur après qu’un utilisateur a lancé une demande ou d’un gestionnaire de processus quand ce dernier indique à un agrégat d’exécuter une action.

Une importante caractéristique d’une commande est qu’elle doit être traitée une seule fois par un seul récepteur. En effet, une commande est une action ou transaction unique que vous voulez effectuer dans l’application. Par exemple, la même commande de création d’une commande ne doit pas être traitée plusieurs fois. Il s’agit d’une différence importante entre les commandes et les événements. Les événements peuvent être traités plusieurs fois, car de nombreux systèmes ou microservices peuvent s’y intéresser.

De plus, il est important de traiter une commande une seule fois au cas où elle ne serait pas idempotente. Une commande est idempotente si elle peut être exécutée plusieurs fois sans que sont résultat ne soit modifié, soit en raison de sa nature, soit en raison de la manière dont le système la gère.

Il est conseillé de faire vos commandes et de mettre à jour idempotent quand cela se justifie dans les règles métier et les invariants de votre domaine. Autrement dit, pour utiliser le même exemple, si pour une raison quelconque (logique de nouvelle tentative, piratage, etc.), la même commande CreateOrder atteint votre système plusieurs fois, vous devez être en mesure de l’identifier et de veiller à ne pas créer plusieurs commandes. Pour cela, vous devez attacher une sorte d’identité dans les opérations et déterminer si la commande ou la mise à jour a déjà été traitée.

Vous envoyez une commande à un seul récepteur ; vous ne publiez pas une commande. La publication est destinée aux événements qui spécifient un fait : quelque chose s’est produit, qui peut intéresser les destinataires des événements. Dans le cas des événements, le serveur de publication n’a que faire de savoir quels récepteurs obtiennent l’événement ou ce qu’ils en font. Mais les choses sont différentes pour les événements d’intégration ou de domaine déjà présentés dans les sections précédentes.

Une commande est implémentée avec une classe qui contient des champs ou collections de données contenant toutes les informations nécessaires à son exécution. Une commande est un type spécial d’objet de transfert de données, particulièrement utilisé pour demander des modifications ou des transactions. La commande elle-même se base sur les informations exactes nécessaires à son traitement et rien de plus.

L’exemple suivant illustre la classe simplifiée `CreateOrderCommand` . Il s’agit d’une commande immuable utilisée dans le microservice de passation de commandes dans eShopOnContainers.

```csharp
// DDD and CQRS patterns comment
// Note that we recommend that you implement immutable commands
// In this case, immutability is achieved by having all the setters as private
// plus being able to update the data just once, when creating the object
// through the constructor.
// References on immutable commands:
// https://cqrs.nu/Faq
// https://docs.spine3.org/motivation/immutability.html
// http://blog.gauffin.org/2012/06/griffin-container-introducing-command-support/
// https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties
[DataContract]
public class CreateOrderCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    private readonly List<OrderItemDTO> _orderItems;
    [DataMember]
    public string City { get; private set; }
    [DataMember]
    public string Street { get; private set; }
    [DataMember]
    public string State { get; private set; }
    [DataMember]
    public string Country { get; private set; }
    [DataMember]
    public string ZipCode { get; private set; }
    [DataMember]
    public string CardNumber { get; private set; }
    [DataMember]
    public string CardHolderName { get; private set; }
    [DataMember]
    public DateTime CardExpiration { get; private set; }
    [DataMember]
    public string CardSecurityNumber { get; private set; }
    [DataMember]
    public int CardTypeId { get; private set; }
    [DataMember]
    public IEnumerable<OrderItemDTO> OrderItems => _orderItems;

    public CreateOrderCommand()
    {
        _orderItems = new List<OrderItemDTO>();
    }

    public CreateOrderCommand(List<BasketItem> basketItems, string city,
        string street,
        string state, string country, string zipcode,
        string cardNumber, string cardHolderName, DateTime cardExpiration,
        string cardSecurityNumber, int cardTypeId) : this()
    {
        _orderItems = MapToOrderItems(basketItems);
        City = city;
        Street = street;
        State = state;
        Country = country;
        ZipCode = zipcode;
        CardNumber = cardNumber;
        CardHolderName = cardHolderName;
        CardSecurityNumber = cardSecurityNumber;
        CardTypeId = cardTypeId;
        CardExpiration = cardExpiration;
    }

    public class OrderItemDTO
    {
        public int ProductId { get; set; }
        public string ProductName { get; set; }
        public decimal UnitPrice { get; set; }
        public decimal Discount { get; set; }
        public int Units { get; set; }
        public string PictureUrl { get; set; }
    }
}
```

En gros, la classe de commande contient toutes les données dont vous avez besoin pour effectuer une transaction commerciale à l’aide des objets du modèle de domaine. Ainsi, les commandes sont simplement des structures de données qui contiennent des données en lecture seule, sans aucun comportement. Le nom de la commande indique son rôle. Dans de nombreux langages, comme C#, les commandes sont représentées sous forme de classes, mais il ne s’agit pas de vraies classes au sens orienté objet.

Autre caractéristique des commandes : elles sont immuables, car l’usage veut qu’elles soient traitées directement par le modèle de domaine. Elles n’ont pas besoin de changer au cours de leur durée de vie prévue. Dans une classe C#, l’immuabilité implique d’éviter toute méthode setter ou autre méthode qui modifie l’état interne.

N’oubliez pas que si vous envisagez ou pensez que les commandes passent par un processus de sérialisation/désérialisation, les propriétés doivent avoir un accesseur Set privé et l' `[DataMember]` attribut (ou `[JsonProperty]` ). Dans le cas contraire, le désérialiseur ne pourra pas reconstruire l’objet à la destination avec les valeurs requises. Vous pouvez également utiliser des propriétés réellement en lecture seule si la classe a un constructeur avec des paramètres pour toutes les propriétés, avec la Convention d’affectation de noms la casse mixte habituelle et annoter le constructeur comme `[JsonConstructor]` . Toutefois, cette option requiert davantage de code.

Par exemple, la classe de commande pour la création d’une commande est probablement similaire en termes de données à la commande que vous souhaitez créer, mais vous n’avez probablement pas besoin des mêmes attributs. Par exemple, `CreateOrderCommand` n’a pas d’ID de commande, car la commande n’a pas encore été créée.

De nombreuses classes de commande peuvent être simples, car elles n’ont besoin que de quelques champs sur un état qui doit être modifié. C’est le cas si vous changez simplement l’état d’une commande de « en cours » en « payé » ou « expédié » à l’aide d’une commande semblable à la suivante :

```csharp
[DataContract]
public class UpdateOrderStatusCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    public string Status { get; private set; }

    [DataMember]
    public string OrderId { get; private set; }

    [DataMember]
    public string BuyerIdentityGuid { get; private set; }
}
```

Certains développeurs séparent leurs objets de demande d’interface utilisateur de leurs objets de transfert de données, mais il ne s’agit que d’une question de préférence. Cette séparation est fastidieuse et n’ajoute pas de valeur. Les objets ont presque exactement la même forme. Par exemple, dans eShopOnContainers, certaines commandes viennent directement du côté client.

### <a name="the-command-handler-class"></a>La classe du gestionnaire de commandes

Vous devez implémenter une classe de gestionnaire de commandes spécifique pour chaque commande. C’est ainsi que le modèle fonctionne, et c’est là que vous allez utiliser l’objet de commande, les objets de domaine et les objets de référentiel d’infrastructure. Le gestionnaire de commandes est en fait le cœur de la couche Application en termes de CQRS et DDD. Toutefois, toute la logique de domaine doit être contenue dans les classes de domaine (dans les racines d’agrégat (entités racine), les entités enfants ou les [services de domaine](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), mais pas dans le gestionnaire de commandes, qui est une classe de la couche application.

La classe du gestionnaire de commandes offre une base solide pour appliquer le principe de responsabilité unique mentionné dans une des sections précédentes.

Un gestionnaire de commandes reçoit une commande et obtient un résultat de l’agrégat qui est utilisé. Ce résultat doit être l’exécution correcte de la commande ou une exception. En cas d’exception, l’état du système ne doit pas changer.

Le gestionnaire de commandes suit généralement les étapes suivantes :

- Il reçoit l’objet de commande, comme un objet de transfert de données (de la part du [médiateur](https://en.wikipedia.org/wiki/Mediator_pattern) ou d’un autre objet d’infrastructure).

- Il vérifie que la commande est valide (si elle n’est pas validée par le médiateur).

- Il instancie l’instance racine de l’agrégat qui est la cible de la commande en cours.

- Il exécute la méthode sur l’instance racine de l’agrégat, pour obtenir les données nécessaires à partir de la commande.

- Il conserve le nouvel état de l’agrégat dans sa base de données correspondante. Cette dernière opération correspond à la transaction réelle.

En règle générale, un gestionnaire de commandes s’occupe d’un seul agrégat piloté par sa racine d’agrégat (entité racine). Si plusieurs agrégats doivent être concernés par la réception d’une commande unique, vous pouvez utiliser des événements de domaine pour propager des états ou des actions sur plusieurs agrégats.

L’important ici est que, quand une commande est en cours de traitement, toute la logique de domaine soit à l’intérieur du modèle de domaine (les agrégats), entièrement encapsulée et prête pour les tests unitaires. Le gestionnaire de commandes sert simplement de moyen d’obtenir le modèle de domaine auprès de la base de données et, pour finir, d’indiquer à la couche d’infrastructure (dépôts) de rendre les modifications persistantes quand le modèle est modifié. L’avantage de cette approche est que vous pouvez refactoriser la logique de domaine dans un modèle de domaine isolé, entièrement encapsulé, riche et comportemental sans modifier le code dans les couches Application ou d’infrastructure, qui forment le niveau de raccordement (gestionnaires de commandes, API web, dépôts, etc.).

Lorsque les gestionnaires de commandes deviennent complexes, avec trop de logique, un « code smell » peut se produire. Passez-les en revue et si vous trouvez la logique de domaine, refactorisez le code pour déplacer ce comportement de domaine vers les méthodes des objets de domaine (entité racine et enfant de l’agrégat).

En guise d’exemple de classe de gestionnaire de commandes, le code suivant montre la même `CreateOrderCommandHandler` classe que celle que vous avez vue au début de ce chapitre. Nous voulons ici mettre en exergue la méthode Handle et les opérations effectuées avec les objets/agrégats du modèle de domaine.

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

Il s’agit des étapes supplémentaires que doit suivre un gestionnaire de commandes :

- Utilisez les données de la commande pour utiliser les méthodes et le comportement de la racine d’agrégat.

- En interne dans les objets de domaine, déclenchez des événements de domaine pendant l’exécution de la transaction, en sachant que cette action est transparente du point de vue du gestionnaire de commandes.

- Si le résultat de l’opération d’agrégation aboutit et que la transaction est terminée, déclenchez des événements d’intégration. (Ces derniers peuvent également être déclenchés par des classes d’infrastructure comme les dépôts.)

#### <a name="additional-resources"></a>Ressources supplémentaires

- **Mark Seemann. Au niveau des limites, les applications ne sont pas orientées objet** \
  <https://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/>

- **Commandes et événements** \
  <https://cqrs.nu/Faq/commands-and-events>

- **What does a command handler do?** \
  <https://cqrs.nu/Faq/command-handlers>

- **Jimmy bogard. Modèles de commande de domaine : gestionnaires** \
  <https://jimmybogard.com/domain-command-patterns-handlers/>

- **Jimmy bogard. Modèles de commande de domaine – validation** \
  <https://jimmybogard.com/domain-command-patterns-validation/>

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a>Pipeline du processus de commande : comment déclencher un gestionnaire de commandes

La question suivante a trait à la manière d’appeler un gestionnaire de commandes. Vous pouvez l’appeler manuellement à partir de chaque contrôleur ASP.NET Core connexe. Toutefois, cette approche paraît trop couplée et n’est donc pas idéale.

Les deux autres options principales, qui sont recommandées, sont les suivantes :

- Par le biais d’un artefact de modèle Médiateur en mémoire.

- Avec une file d’attente de messages asynchrones, entre les contrôleurs et les gestionnaires.

### <a name="use-the-mediator-pattern-in-memory-in-the-command-pipeline"></a>Utiliser le modèle de médiateur (en mémoire) dans le pipeline de commandes

Comme le montre la figure 7-25, dans une approche CQRS, vous utilisez un médiateur intelligent, similaire à un bus en mémoire, suffisamment intelligent pour effectuer une redirection vers le gestionnaire de commandes approprié en fonction du type de commande ou d’objet de transfert de données reçu. Les flèches noires entre les composants représentent les dépendances entre les objets (dans de nombreux cas, injectées par injection de dépendances) avec leurs interactions associées.

![Diagramme montrant un flot de données plus détaillé entre le client et la base de données.](./media/microservice-application-layer-implementation-web-api/mediator-cqrs-microservice.png)

**Figure 7-25**. Utilisation du modèle Médiateur dans le processus dans un microservice CQRS unique

Le diagramme ci-dessus montre un zoom avant à partir de l’image 7-24 : le contrôleur ASP.NET Core envoie la commande au pipeline de commande de médiateur, afin qu’ils obtiennent le gestionnaire approprié.

L’utilisation du modèle Médiateur prend tout son sens dans les applications d’entreprise, où les demandes de traitement peuvent devenir compliquées. Vous avez besoin de pouvoir ajouter un nombre ouvert de problèmes transversaux comme la journalisation, les validations, l’audit et la sécurité. Dans ce cas, vous pouvez compter sur un pipeline de médiateur (consultez [Modèle Médiateur](https://en.wikipedia.org/wiki/Mediator_pattern)) pour fournir un moyen à ces comportements supplémentaires ou problèmes transversaux.

Un médiateur est un objet qui encapsule la « procédure » de ce processus : il coordonne l’exécution en fonction de l’État, de la façon dont un gestionnaire de commandes est appelé ou de la charge utile que vous fournissez au gestionnaire. Avec un composant médiateur, vous pouvez appliquer des problèmes transversaux de manière centralisée et transparente en appliquant des éléments décoratifs (ou [comportements de pipeline](https://github.com/jbogard/MediatR/wiki/Behaviors) depuis [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)). Pour plus d’informations, consultez le [modèle Élément décoratif](https://en.wikipedia.org/wiki/Decorator_pattern).

Les éléments décoratifs et les comportements sont similaires à la [programmation orientée aspect](https://en.wikipedia.org/wiki/Aspect-oriented_programming), uniquement appliquée à un pipeline de processus spécifique géré par le composant médiateur. Les aspects en programmation orientée aspect qui implémentent des problèmes transversaux sont appliqués selon les *tisseurs d’aspect* injectés au moment de la compilation ou en fonction de l’interception des appels d’objet. Les deux approches usuelles de la programmation orientée aspect sont parfois considérées comme « magiques », car il n’est pas facile de voir comment leur travail est effectué. Lorsque qu’il s’agit de traiter des problèmes ou bogues graves, la programmation orientée aspect peut rendre le débogage difficile. En revanche, ces éléments décoratifs/comportements sont explicites et uniquement appliqués dans le contexte du médiateur, donc le débogage est beaucoup plus prévisible et facile.

Par exemple, dans le microservice de passation de commandes eShopOnContainers, nous avons implémenté deux exemples de comportements, une classe [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) et une classe [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs). L’implémentation des comportements est expliquée dans la section suivante en illustrant la façon dont eShopOnContainers utilise les [comportements](https://github.com/jbogard/MediatR/wiki/Behaviors) [médiateurr 3](https://www.nuget.org/packages/MediatR/3.0.0) .

### <a name="use-message-queues-out-of-proc-in-the-commands-pipeline"></a>Utiliser des files d’attente de messages (out-of-proc) dans le pipeline de la commande

Un autre choix consiste à utiliser des messages asynchrones basés sur des services Broker ou des files d’attente de messages, comme le montre la figure 7-26. Vous pouvez aussi combiner cette option avec le composant médiateur juste avant le gestionnaire de commandes.

![Diagramme montrant le flux de données à l’aide d’une file d’attente de messages haute disponibilité.](./media/microservice-application-layer-implementation-web-api/add-ha-message-queue.png)

**Figure 7-26**. Utilisation de files d’attente de messages (communication hors processus et entre processus) avec des commandes CQRS

Le pipeline de commandes peut également être géré par une file d’attente à haute disponibilité pour délivrer les commandes au gestionnaire approprié. L’utilisation de files d’attente de messages pour accepter les commandes peut compliquer davantage le pipeline de votre commande, car vous devrez probablement fractionner le pipeline en deux processus connectés via la file d’attente de messages externe. Néanmoins, vous devez l’utiliser si vous avez besoin d’une meilleure scalabilité et de performances améliorées en fonction de la messagerie asynchrone. Considérez que, dans le cas de la figure 7-26, le contrôleur envoie simplement le message de commande dans la file d’attente, puis retourne. Ensuite, les gestionnaires de commandes traitent les messages à leur propre rythme. C’est l’énorme avantage des files d’attente : elles peuvent agir en tant que mémoire tampon quand le besoin de scalabilité est considérable, par exemple pour des stocks ou tout autre scénario impliquant un volume élevé de données d’entrée.

Toutefois, en raison de la nature asynchrone des files d’attente de messages, vous devez déterminer comment communiquer avec l’application cliente à propos de la réussite ou de l’échec du processus de la commande. En règle générale, vous ne devez jamais utiliser les commandes « déclencher et oublier ». Chaque application métier doit savoir si une commande a été traitée correctement, ou au moins validée et acceptée.

Par conséquent, la possibilité de répondre au client après la validation d’un message de commande qui a été envoyé à une file d’attente asynchrone ajoute de la complexité à votre système, par rapport à un processus de commande in-process qui retourne le résultat de l’opération après l’exécution de la transaction. L’utilisation de files d’attente peut vous obliger à retourner le résultat du processus de commande par le biais d’autres messages de résultat d’opération, ce qui nécessite des composants supplémentaires et une communication personnalisée dans votre système.

De plus, les commandes asynchrones sont des commandes unidirectionnelles, inutiles dans de nombreux cas, comme expliqué dans l’intéressant échange suivant entre Burtsev Alexey et Greg Young au cours d’une [conversation en ligne](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ) :

> \[Burtsev Alexey\] Je trouve beaucoup de code où les informaticiens utilisent une gestion de commandes asynchrone ou des messages de commande unidirectionnels sans aucune raison de le faire (ils n’effectuent pas une opération longue, ils n’exécutent pas du code asynchrone externe, ils ne franchissent même pas la limite de l’application pour utiliser un bus de messages). Pourquoi introduisent-ils cette complexité inutile ? En fait, je n’ai jamais vu un exemple de code CQRS avec des gestionnaires de commandes bloquants jusqu’à présent, même si cela fonctionnerait parfaitement dans la plupart des cas.
>
> \[Greg Young \] \[ ... \] une commande asynchrone n’existe pas ; il s’agit en fait d’un autre événement. Si je dois accepter ce que vous m’envoyez et déclencher un événement si je ne suis pas d’accord, il n’est plus nécessaire d’effectuer une opération, il ne s’agit \[ pas d’une commande \] . Mais vous qui me dites que quelque chose a été fait. La différence peut sembler légère dans un premier temps, mais ses implications sont nombreuses.

Les commandes asynchrones augmentent considérablement la complexité d’un système, car il n’existe aucun moyen simple d’indiquer des échecs. Ainsi, les commandes asynchrones ne sont pas recommandées si ce n’est quand il existe des besoins de mise à l’échelle ou dans des cas spéciaux de communication des microservices internes par le biais d’une messagerie. Le cas échéant, vous devez concevoir un système de création de rapports et de récupération distinct pour les échecs.

Dans la version initiale d’eShopOnContainers, nous avons décidé d’utiliser un traitement des commandes synchrone, qui démarre à partir de requêtes HTTP et qui est piloté par le modèle Médiateur. Ce traitement vous permet de retourner facilement la réussite ou l’échec du processus, comme dans l’implémentation [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs).

Dans tous les cas, cette décision doit être basée sur les besoins métier de votre application ou de votre microservice.

## <a name="implement-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a>Implémenter le pipeline du processus de commande avec un modèle de médiateur (MediatR)

À titre d’exemple d’implémentation, le présent guide propose d’utiliser le pipeline in-process basé sur le modèle Médiateur pour diriger l’ingestion des commandes et acheminer les commandes, dans la mémoire, vers les gestionnaires de commandes appropriés. Le guide propose également d’appliquer des [comportements](https://github.com/jbogard/MediatR/wiki/Behaviors) pour séparer les problèmes transversaux.

Pour l’implémentation dans .NET Core, il existe plusieurs bibliothèques open source disponibles qui implémentent le modèle Médiateur. La bibliothèque utilisée dans ce guide est la bibliothèque open source [MediatR](https://github.com/jbogard/MediatR) (créée par Jimmy Bogard), mais vous pouvez utiliser une autre approche. MediatR est une petite bibliothèque simple qui vous permet de traiter les messages en mémoire comme une commande, tout en appliquant des éléments décoratifs ou des comportements.

L’utilisation du modèle Médiateur vous aide à réduire le couplage et à isoler les problèmes du travail demandé, tout en vous connectant automatiquement au gestionnaire qui effectue ce travail (ici, les gestionnaires de commandes).

Jimmy Bogard a précisé une autre bonne raison d’utiliser le modèle Médiateur quand il a révisé ce guide :

> Je pense qu’il est intéressant de mentionner les tests ici : le modèle ouvre une fenêtre cohérente sur le comportement de votre système. Demande, réponse. Nous avons constaté que cet aspect est très utile pour créer des tests qui se comportent de manière cohérente.

Tout d’abord, examinons un exemple de contrôleur WebAPI dans lequel vous utilisez réellement l’objet médiateur. Si vous n’utilisez pas l’objet médiateur, vous devez injecter toutes les dépendances de ce contrôleur, comme un objet enregistreur d’événements et d’autres. Ainsi, le constructeur est assez complexe. En revanche, si vous utilisez l’objet médiateur, le constructeur de votre contrôleur peut être beaucoup plus simple, avec seulement quelques dépendances plutôt que de nombreuses dépendances si vous n’en avez qu’une par opération transversale, comme dans l’exemple suivant :

```csharp
public class MyMicroserviceController : Controller
{
    public MyMicroserviceController(IMediator mediator,
                                    IMyMicroserviceQueries microserviceQueries)
    {
        // ...
    }
}
```

Vous pouvez voir que le médiateur fournit un constructeur de contrôleur d’API web propre et léger. De plus, dans les méthodes du contrôleur, le code permettant d’envoyer une commande à l’objet médiateur occupe quasiment une seule ligne :

```csharp
[Route("new")]
[HttpPost]
public async Task<IActionResult> ExecuteBusinessOperation([FromBody]RunOpCommand
                                                               runOperationCommand)
{
    var commandResult = await _mediator.SendAsync(runOperationCommand);

    return commandResult ? (IActionResult)Ok() : (IActionResult)BadRequest();
}
```

### <a name="implement-idempotent-commands"></a>Implémenter des commandes idempotentes

Dans **eShopOnContainers**, un exemple plus avancé que le précédent envoie un objet CreateOrderCommand à partir du microservice Ordering. Toutefois, étant donné que le processus d’entreprise de commande est un peu plus complexe et, dans notre cas, il commence dans le microservice du panier, cette action consistant à soumettre l’objet CreateOrderCommand est effectuée à partir d’un gestionnaire d’événements d’intégration nommé [UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) au lieu d’un contrôleur WebAPI simple appelé à partir de l’application cliente, comme dans l’exemple plus simple précédent.

Néanmoins, l’action d’envoi de la commande à MediatR est assez similaire, comme le montre le code suivant.

```csharp
var createOrderCommand = new CreateOrderCommand(eventMsg.Basket.Items,
                                                eventMsg.UserId, eventMsg.City,
                                                eventMsg.Street, eventMsg.State,
                                                eventMsg.Country, eventMsg.ZipCode,
                                                eventMsg.CardNumber,
                                                eventMsg.CardHolderName,
                                                eventMsg.CardExpiration,
                                                eventMsg.CardSecurityNumber,
                                                eventMsg.CardTypeId);

var requestCreateOrder = new IdentifiedCommand<CreateOrderCommand,bool>(createOrderCommand,
                                                                        eventMsg.RequestId);
result = await _mediator.Send(requestCreateOrder);
```

Toutefois, ce cas est également un peu plus avancé, car nous implémentons également des commandes idempotent. Le processus CreateOrderCommand doit être idempotent, donc si le même message est dupliqué par le biais du réseau, pour une raison quelconque, comme de nouvelles tentatives, la même commande commerciale n’est traitée qu’une seule fois.

Ceci est implémenté en wrappant la commande métier (dans ce cas CreateOrderCommand) et en l’incorporant dans une IdentifiedCommand générique suivi par un ID de chaque message arrivant sur le réseau et devant être idempotent.

Dans le code ci-dessous, vous pouvez voir qu’IdentifiedCommand n’est rien d’autre qu’un objet de transfert de données avec un ID et l’objet commande métier inclus dans un wrapper.

```csharp
public class IdentifiedCommand<T, R> : IRequest<R>
    where T : IRequest<R>
{
    public T Command { get; }
    public Guid Id { get; }
    public IdentifiedCommand(T command, Guid id)
    {
        Command = command;
        Id = id;
    }
}
```

Ensuite, le CommandHandler de l’IdentifiedCommand nommé [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) vérifie en gros si l’ID qui arrive dans le message existe déjà dans une table. S’il existe déjà, cette commande ne sera pas traitée à nouveau et se comporte donc comme une commande idempotent. Ce code d’infrastructure est exécuté par l’appel de méthode `_requestManager.ExistAsync` ci-dessous.

```csharp
// IdentifiedCommandHandler.cs
public class IdentifiedCommandHandler<T, R> :
                                   IAsyncRequestHandler<IdentifiedCommand<T, R>, R>
                                   where T : IRequest<R>
{
    private readonly IMediator _mediator;
    private readonly IRequestManager _requestManager;

    public IdentifiedCommandHandler(IMediator mediator,
                                    IRequestManager requestManager)
    {
        _mediator = mediator;
        _requestManager = requestManager;
    }

    protected virtual R CreateResultForDuplicateRequest()
    {
        return default(R);
    }

    public async Task<R> Handle(IdentifiedCommand<T, R> message)
    {
        var alreadyExists = await _requestManager.ExistAsync(message.Id);
        if (alreadyExists)
        {
            return CreateResultForDuplicateRequest();
        }
        else
        {
            await _requestManager.CreateRequestForCommandAsync<T>(message.Id);

            // Send the embedded business command to mediator
            // so it runs its related CommandHandler
            var result = await _mediator.Send(message.Command);

            return result;
        }
    }
}
```

Étant donné que IdentifiedCommand agit comme l’enveloppe d’une commande métier, lorsque la commande métier doit être traitée parce qu’il ne s’agit pas d’un ID répété, elle prend cette commande métier interne et la soumet à nouveau au Médiateur, comme dans la dernière partie du code indiqué ci-dessus lors de `_mediator.Send(message.Command)` l’exécution, à partir du [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).

Ce faisant, le gestionnaire de commandes métier, dans ce cas [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs), qui exécute des transactions dans la base de données Ordering, est lié et exécuté, comme le montre le code suivant.

```csharp
// CreateOrderCommandHandler.cs
public class CreateOrderCommandHandler
                                   : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Add/Update the Buyer AggregateRoot
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

### <a name="register-the-types-used-by-mediatr"></a>Inscrire les types utilisés par MediatR

Pour que MediatR ait connaissance de vos classes de gestionnaires de commandes, vous devez inscrire les classes du médiateur et les classes des gestionnaires de commandes dans votre conteneur IoC. Par défaut, MediatR utilise Autofac en tant que conteneur IoC, mais vous pouvez également utiliser le conteneur IoC ASP.NET Core intégré ou tout autre conteneur pris en charge par MediatR.

Le code suivant montre comment enregistrer les types et les commandes du Médiateur lors de l’utilisation de modules Autofac.

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IAsyncRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(
                              typeof(CreateOrderCommand).GetTypeInfo().Assembly).
                                   AsClosedTypesOf(typeof(IAsyncRequestHandler<,>));
        // Other types registration
        //...
    }
}
```

C’est là qu’intervient le « Magic » avec médiateur.

Étant donné que chaque gestionnaire de commandes implémente l’interface `IAsyncRequestHandler<T>` générique, quand vous inscrivez les assemblys, le code inscrit auprès de `RegisteredAssemblyTypes` tous les types marqués comme `IAsyncRequestHandler` pendant l’association des `CommandHandlers` à leurs `Commands`, grâce à la relation indiquée au niveau de la classe `CommandHandler`, comme dans l’exemple suivant :

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

Voici le code qui met en relation les commandes avec les gestionnaires de commandes. Le gestionnaire n’est qu’une simple classe, mais il hérite de `RequestHandler<T>`, où T est le type de commande, et MediatR vérifie qu’il est appelé avec la bonne charge utile (la commande).

## <a name="apply-cross-cutting-concerns-when-processing-commands-with-the-behaviors-in-mediatr"></a>Appliquer des préoccupations transversales lors du traitement des commandes avec les comportements dans MediatR

Dernière chose : pouvoir appliquer des problèmes transversaux au pipeline médiateur. Vous pouvez également voir, à la fin du code du module d’inscription Autofac, comment s’inscrit un type de comportement, et plus particulièrement, une classe LoggingBehavior personnalisée et une classe ValidatorBehavior. Vous pouvez cependant aussi ajouter d’autres comportements personnalisés.

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IAsyncRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(
                              typeof(CreateOrderCommand).GetTypeInfo().Assembly).
                                   AsClosedTypesOf(typeof(IAsyncRequestHandler<,>));
        // Other types registration
        //...
        builder.RegisterGeneric(typeof(LoggingBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
        builder.RegisterGeneric(typeof(ValidatorBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
    }
}
```

Vous pouvez implémenter cette classe [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) comme le code suivant, qui enregistre des informations sur le gestionnaire de commandes en cours d’exécution et sur sa réussite ou son échec.

```csharp
public class LoggingBehavior<TRequest, TResponse>
         : IPipelineBehavior<TRequest, TResponse>
{
    private readonly ILogger<LoggingBehavior<TRequest, TResponse>> _logger;
    public LoggingBehavior(ILogger<LoggingBehavior<TRequest, TResponse>> logger) =>
                                                                  _logger = logger;

    public async Task<TResponse> Handle(TRequest request,
                                        RequestHandlerDelegate<TResponse> next)
    {
        _logger.LogInformation($"Handling {typeof(TRequest).Name}");
        var response = await next();
        _logger.LogInformation($"Handled {typeof(TResponse).Name}");
        return response;
    }
}
```

En implémentant simplement cette classe de comportement et en l’inscrivant dans le pipeline (dans le MediatorModule plus haut), toutes les commandes traitées via MediatR consignent des informations sur l’exécution.

Le microservice de passation de commandes eShopOnContainers applique aussi un deuxième comportement pour les validations de base, la classe [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) qui s’appuie sur la bibliothèque [FluentValidation](https://github.com/JeremySkinner/FluentValidation), comme le montre le code suivant :

```csharp
public class ValidatorBehavior<TRequest, TResponse>
         : IPipelineBehavior<TRequest, TResponse>
{
    private readonly IValidator<TRequest>[] _validators;
    public ValidatorBehavior(IValidator<TRequest>[] validators) =>
                                                         _validators = validators;

    public async Task<TResponse> Handle(TRequest request,
                                        RequestHandlerDelegate<TResponse> next)
    {
        var failures = _validators
            .Select(v => v.Validate(request))
            .SelectMany(result => result.Errors)
            .Where(error => error != null)
            .ToList();

        if (failures.Any())
        {
            throw new OrderingDomainException(
                $"Command Validation Errors for type {typeof(TRequest).Name}",
                        new ValidationException("Validation exception", failures));
        }

        var response = await next();
        return response;
    }
}
```

Le comportement ici lève une exception en cas d’échec de la validation, mais vous pouvez également retourner un objet de résultat, qui contient le résultat de la commande si celui-ci a réussi ou si les messages de validation le cas échéant. Ceci faciliterait probablement l’affichage des résultats de la validation à l’utilisateur.

Ensuite, en fonction de la bibliothèque [FluentValidation](https://github.com/JeremySkinner/FluentValidation) , nous avons créé une validation pour les données passées avec CreateOrderCommand, comme dans le code suivant :

```csharp
public class CreateOrderCommandValidator : AbstractValidator<CreateOrderCommand>
{
    public CreateOrderCommandValidator()
    {
        RuleFor(command => command.City).NotEmpty();
        RuleFor(command => command.Street).NotEmpty();
        RuleFor(command => command.State).NotEmpty();
        RuleFor(command => command.Country).NotEmpty();
        RuleFor(command => command.ZipCode).NotEmpty();
        RuleFor(command => command.CardNumber).NotEmpty().Length(12, 19);
        RuleFor(command => command.CardHolderName).NotEmpty();
        RuleFor(command => command.CardExpiration).NotEmpty().Must(BeValidExpirationDate).WithMessage("Please specify a valid card expiration date");
        RuleFor(command => command.CardSecurityNumber).NotEmpty().Length(3);
        RuleFor(command => command.CardTypeId).NotEmpty();
        RuleFor(command => command.OrderItems).Must(ContainOrderItems).WithMessage("No order items found");
    }

    private bool BeValidExpirationDate(DateTime dateTime)
    {
        return dateTime >= DateTime.UtcNow;
    }

    private bool ContainOrderItems(IEnumerable<OrderItemDTO> orderItems)
    {
        return orderItems.Any();
    }
}

```

Vous pouvez créer des validations supplémentaires. Il s’agit d’un moyen très propre et élégant d’implémenter vos validations de commande.

De la même façon, vous pouvez implémenter d’autres comportements pour d’autres aspects ou problèmes transversaux que vous voulez appliquer aux commandes lorsque vous les gérez.

#### <a name="additional-resources"></a>Ressources supplémentaires

##### <a name="the-mediator-pattern"></a>Le modèle Médiateur

- **Modèle médiateur** \
  [https://en.wikipedia.org/wiki/Mediator\_pattern](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a>Le modèle Élément décoratif

- **Modèle Decorator** \
  [https://en.wikipedia.org/wiki/Decorator\_pattern](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a>MediatR (Jimmy Bogard)

- **MediatR.** Dépôt GitHub. \
  <https://github.com/jbogard/MediatR>

- **CQRS avec médiateur et AutoMapper** \
  <https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/>

- **Put your controllers on a diet: POSTs and commands.** \
  <https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/>

- **Résoudre les problèmes de coupe croisée avec un pipeline médiateur** \
  <https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/>

- **CQRS et REST : correspondance parfaite** \
  <https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/>

- **Exemples de pipeline médiateur** \
  <https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/>

- **Contextes de test des découpages verticaux pour médiateur et ASP.NET Core** \
  <https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>

- **Extensions de médiateur pour l’injection de dépendances Microsoft publiées** \
  <https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/>

##### <a name="fluent-validation"></a>Validation fluide

- **Jeremy Skinner. FluentValidation.** Dépôt GitHub. \
  <https://github.com/JeremySkinner/FluentValidation>

> [!div class="step-by-step"]
> [Précédent](microservice-application-layer-web-api-design.md) 
>  [Suivant](../implement-resilient-applications/index.md)
