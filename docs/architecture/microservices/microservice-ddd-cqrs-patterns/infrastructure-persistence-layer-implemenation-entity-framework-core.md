---
title: Implémentation de la couche de persistance de l’infrastructure avec Entity Framework Core
description: .NET Microservices Architecture for Containerized .NET Applications (fr) Explorez les détails de la mise en œuvre de la couche de persistance de l’infrastructure, à l’aide de Entity Framework Core.
ms.date: 01/30/2020
ms.openlocfilehash: 7ab3be0d6a5affda478f7ec8f6c356571e304759
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805480"
---
# <a name="implement-the-infrastructure-persistence-layer-with-entity-framework-core"></a>Implémenter la couche de persistance de l’infrastructure avec Entity Framework Core

Quand vous utilisez des bases de données relationnelles telles que SQL Server, Oracle ou PostgreSQL, une approche recommandée consiste à implémenter la couche de persistance en fonction d’Entity Framework (EF). EF prend en charge LINQ et fournit des objets fortement typés pour votre modèle, ainsi qu’une persistance simplifiée dans votre base de données.

Entity Framework présente un long historique dans le cadre du .NET Framework. Quand vous utilisez .NET Core, vous devez également utiliser Entity Framework Core, qui s’exécute sur Windows ou Linux de la même façon que .NET Core. EF Core est une réécriture complète du cadre d’entité qui est mise en œuvre avec une empreinte beaucoup plus petite et des améliorations importantes de la performance.

## <a name="introduction-to-entity-framework-core"></a>Introduction à Entity Framework Core

Entity Framework (EF) Core est une version légère, extensible et multiplateforme de la technologie d’accès aux données Entity Framework populaire. Elle a été introduite avec .NET Core au milieu de l’année 2016.

Dans la mesure où une introduction à EF Core est déjà disponible dans la documentation Microsoft, nous indiquons simplement ici les liens vers ces informations.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Base du cadre de l’entité** \
  [https://docs.microsoft.com/ef/core/](/ef/core/)

- **Commencer avec ASP.NET Core et Entity Framework Core à l’aide de Visual Studio** \
  [https://docs.microsoft.com/aspnet/core/data/ef-mvc/](/aspnet/core/data/ef-mvc/)

- **Classe DbContext** \
  [https://docs.microsoft.com/dotnet/api/microsoft.entityframeworkcore.dbcontext](xref:Microsoft.EntityFrameworkCore.DbContext)

- **Comparez EF Core & EF6.x** \
  [https://docs.microsoft.com/ef/efcore-and-ef6/index](/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a>Infrastructure dans Entity Framework Core à partir d’une perspective DDD

D’un point de vue DDD, une fonctionnalité importante d’EF est la possibilité d’utiliser les entités de domaine OCT, également désignées dans la terminologie EF sous le nom *d’entités Code First * OCT. Si vous utilisez des entités de domaine OCT, vos classes de modèle de domaine ignorent la persistance, selon les principes [d’ignorance de la persistance](https://deviq.com/persistence-ignorance/) et [d’ignorance de l’infrastructure](https://ayende.com/blog/3137/infrastructure-ignorance).

Selon les modèles DDD, vous devez encapsuler le comportement et les règles du domaine au sein de la classe d’entité pour qu’elle puisse contrôler les règles, les validations et les invariants lors de l’accès à toute collection. Par conséquent, il est déconseillé dans DDD d’autoriser un accès public à des collections d’objets de valeur ou d’entités enfants. Au lieu de cela, vous pouvez exposer des méthodes qui contrôlent comment et quand vos champs et collections de propriétés peuvent être mis à jour, ainsi que le comportement et les actions qui doivent se produire à ce moment-là.

Depuis EF Core 1.1, pour répondre à ces exigences DDD, vous pouvez avoir des champs tout simples dans vos entités au lieu de propriétés publiques. Si vous ne souhaitez pas qu’un champ d’entité soit accessible en externe, il vous suffit de créer l’attribut ou le champ au lieu d’une propriété. Vous pouvez également utiliser des méthodes setter de propriétés privées.

De la même façon, vous pouvez maintenant accéder en lecture seule aux collections à l’aide d’une propriété publique typée comme `IReadOnlyCollection<T>`, qui est associée à un membre de champ privé pour la collection (tel qu’un `List<T>`) dans votre entité qui s’appuie sur EF pour la persistance. Les versions précédentes d’Entity Framework exigeaient que les propriétés de collection prennent en charge `ICollection<T>`, ce qui signifiait que tout développeur utilisant la classe d’entité parente pouvait ajouter ou supprimer des éléments via ses collections de propriétés. Cette possibilité s’oppose aux modèles recommandés dans DDD.

Vous pouvez utiliser une collection privée tout en exposant un objet `IReadOnlyCollection<T>` en lecture seule, comme illustré dans l’exemple de code suivant :

```csharp
public class Order : Entity
{
    // Using private fields, allowed since EF Core 1.1
    private DateTime _orderDate;
    // Other fields ...

    private readonly List<OrderItem> _orderItems;
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;

    protected Order() { }

    public Order(int buyerId, int paymentMethodId, Address address)
    {
        // Initializations ...
    }

    public void AddOrderItem(int productId, string productName,
                             decimal unitPrice, decimal discount,
                             string pictureUrl, int units = 1)
    {
        // Validation logic...

        var orderItem = new OrderItem(productId, productName,
                                      unitPrice, discount,
                                      pictureUrl, units);
        _orderItems.Add(orderItem);
    }
}
```

La `OrderItems` propriété ne peut être consultée `IReadOnlyCollection<OrderItem>`que comme lu-seulement en utilisant . Ce type est en lecture seule et donc protégé contre les mises à jour externes standard.

EF Core offre un moyen de mapper le modèle de domaine à la base de données physique sans « contaminer » le modèle de domaine. Il s’agit de code .NET purement OCT, étant donné que l’action de mappage est implémentée dans la couche de persistance. Dans cette action de mappage, vous devez configurer le mappage de champs à base de données. Dans l’exemple suivant de la méthode `OnModelCreating` de `OrderingContext` et de la classe `OrderEntityTypeConfiguration`, l’appel à `SetPropertyAccessMode` indique à EF Core d’accéder à la propriété `OrderItems` via son champ.

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities' configuration ...
}

// At OrderEntityTypeConfiguration.cs from eShopOnContainers
class OrderEntityTypeConfiguration : IEntityTypeConfiguration<Order>
{
    public void Configure(EntityTypeBuilder<Order> orderConfiguration)
    {
        orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);
        // Other configuration

        var navigation =
              orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));

        //EF access the OrderItem collection property through its backing field
        navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

        // Other configuration
    }
}
```

Lorsque vous utilisez des champs `OrderItem` au lieu de propriétés, l’entité est persistée comme si elle avait une `List<OrderItem>` propriété. Cependant, elle expose un seul accesseur, la méthode `AddOrderItem`, pour ajouter de nouveaux articles à la commande. Par conséquent, le comportement et les données sont reliés et seront cohérents dans n’importe quel code d’application qui utilise le modèle de domaine.

## <a name="implement-custom-repositories-with-entity-framework-core"></a>Implémenter des référentiels personnalisés avec Entity Framework Core

Au niveau de l’implémentation, un dépôt est simplement une classe avec un code de persistance de données coordonné par une unité de travail (DBContext dans EF Core) quand vous effectuez des mises à jour, comme indiqué dans la classe suivante :

```csharp
// using statements...
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class BuyerRepository : IBuyerRepository
    {
        private readonly OrderingContext _context;
        public IUnitOfWork UnitOfWork
        {
            get
            {
                return _context;
            }
        }

        public BuyerRepository(OrderingContext context)
        {
            _context = context ?? throw new ArgumentNullException(nameof(context));
        }

        public Buyer Add(Buyer buyer)
        {
            return _context.Buyers.Add(buyer).Entity;
        }

        public async Task<Buyer> FindAsync(string buyerIdentityGuid)
        {
            var buyer = await _context.Buyers
                .Include(b => b.Payments)
                .Where(b => b.FullName == buyerIdentityGuid)
                .SingleOrDefaultAsync();

            return buyer;
        }
    }
}
```

L’interface `IBuyerRepository` provient de la couche du modèle de domaine comme un contrat. Toutefois, l’implémentation du dépôt est effectuée au niveau de la couche de persistance et de la couche d’infrastructure.

DBContext EF passe par le constructeur via une injection de dépendances. Elle est partagée entre plusieurs référentiels dans la même étendue de requête HTTP grâce à sa durée de vie par défaut (`ServiceLifetime.Scoped`) dans le conteneur IoC (qui peut également être explicitement défini avec `services.AddDbContext<>`).

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a>Méthodes à implémenter dans un dépôt (mises à jour ou transactions et requêtes)

Dans chaque classe de dépôt, vous devez placer les méthodes de persistance qui mettent à jour l’état des entités contenues par son agrégat associé. Gardez à l’esprit qu’il existe une relation un-à-un entre un agrégat et son dépôt associé. Tenez compte du fait qu’un objet d’entité racine d’agrégat peut avoir des entités enfants incorporées dans son graphe EF. Par exemple, un acheteur peut avoir plusieurs modes de paiement en tant qu’entités enfants associées.

Étant donné que l’approche pour le microservice de commandes dans eShopOnContainers repose également sur CQS/CQRS, la plupart des requêtes ne sont pas implémentées dans les dépôts personnalisés. Les développeurs ont la possibilité de créer les requêtes et les jointures dont ils ont besoin pour la couche de présentation sans les restrictions imposées par les agrégats, les dépôts personnalisés par agrégat et DDD en général. La plupart des dépôts personnalisés suggérés par ce guide ont plusieurs méthodes de mise à jour ou transactionnelles, mais uniquement les méthodes de requête nécessaires pour obtenir les données à mettre à jour. Par exemple, le dépôt BuyerRepository implémente une méthode FindAsync, car l’application doit savoir si un acheteur donné existe avant d’en créer un nouveau lié à la commande.

Toutefois, les méthodes de requête réelles pour obtenir des données à envoyer à la couche de présentation ou aux applications clientes sont implémentées, comme indiqué, dans les requêtes CQRS basées sur des requêtes flexibles à l’aide de Dapper.

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a>Comparaison entre l’utilisation d’un dépôt personnalisé et l’utilisation directe de DbContext EF

La classe DbContext de l’Entité-Cadre est basée sur les modèles de l’Unité de travail et de dépôt et peut être utilisée directement à partir de votre code, par exemple à partir d’un contrôleur ASP.NET Core MVC. Les modèles de l’Unité de travail et de dépôt donnent au code le plus simple, comme dans le microservice de catalogue CRUD dans eShopOnContainers. Quand vous voulez le code le plus simple possible, vous pouvez utiliser directement la classe DbContext, comme de nombreux développeurs.

Toutefois, l’implémentation de dépôts personnalisés présente plusieurs avantages lors de l’implémentation de microservices ou d’applications plus complexes. Les modèles de l’Unité de travail et de dépôt sont destinés à encapsuler la couche de persistance de l’infrastructure afin qu’elle soit découplée des couches d’application et de modèle de domaine. L’implémentation de ces modèles peut faciliter l’utilisation de dépôts fictifs simulant l’accès à la base de données.

Dans la figure 7-18, vous pouvez voir les différences entre ne pas utiliser de dépôts (directement à l’aide du texte EF DbContext) à l’aide de dépôts, ce qui facilite la moquerie de ces dépôts.

![Diagramme montrant les composants et le flux de données dans les deux dépôts.](./media/infrastructure-persistence-layer-implemenation-entity-framework-core/custom-repo-versus-db-context.png)

**Figure 7-18**. Utilisation de dépôts personnalisés par rapport à un simple DbContext

La figure 7-18 montre que l’utilisation d’un référentiel personnalisé ajoute une couche d’abstraction qui peut être utilisée pour faciliter les tests en se moquant du référentiel. Il existe plusieurs alternatives lors de la simulation. Vous pouvez simuler uniquement les dépôts ou l’intégralité d’une unité de travail. Généralement, la simulation des dépôts uniquement est suffisante, et la tâche complexe d’abstraction et de simulation de l’intégralité d’une unité de travail n’est pas nécessaire.

Plus tard, quand nous nous concentrerons sur la couche d’application, vous verrez comment fonctionne l’injection de dépendances dans ASP.NET Core et comment elle est implémentée lors de l’utilisation de dépôts.

En bref, les dépôts personnalisés vous permettent de tester plus facilement le code avec des tests unitaires qui ne sont pas affectés par l’état de la couche Données. Si vous exécutez des tests qui accèdent également à la base de données réelle via Entity Framework, il ne s’agit pas de tests unitaires, mais de tests d’intégration qui sont beaucoup plus lents.

Si vous utilisez DbContext directement, vous devez le simuler ou exécuter des tests unitaires en utilisant une instance de SQL Server en mémoire avec des données prévisibles pour les tests unitaires. Mais la simulation de DbContext ou le contrôle des données fictives nécessite plus de travail que la simulation au niveau du référentiel. Bien entendu, vous pouvez toujours tester les contrôleurs MVC.

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a>Durée de vie des instances DbContext EF et IUnitOfWork dans votre conteneur IoC

L’objet `DbContext` (exposé comme objet `IUnitOfWork`) doit être partagé entre plusieurs référentiels au sein de la même étendue de requête HTTP. Par exemple, cela est vrai quand l’opération en cours d’exécution doit gérer plusieurs agrégats ou simplement parce que vous utilisez plusieurs instances de dépôt. Il est également important de mentionner que l’interface `IUnitOfWork` fait partie de votre couche de domaine, et qu’elle n’est pas un type EF Core.

Pour cela, l’instance de l’objet `DbContext` doit avoir sa durée de vie de service définie sur ServiceLifetime.Scoped. Il s’agit de la durée de vie par défaut lors de l’inscription d’un `DbContext` auprès de `services.AddDbContext` dans votre conteneur IoC à partir de la méthode ConfigureServices du fichier `Startup.cs` dans votre projet d’API web ASP.NET Core. Le code suivant illustre ce comportement :

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddMvc(options =>
    {
        options.Filters.Add(typeof(HttpGlobalExceptionFilter));
    }).AddControllersAsServices();

    services.AddEntityFrameworkSqlServer()
      .AddDbContext<OrderingContext>(options =>
      {
          options.UseSqlServer(Configuration["ConnectionString"],
                               sqlOptions => sqlOptions.MigrationsAssembly(typeof(Startup).GetTypeInfo().
                                                                                    Assembly.GetName().Name));
      },
      ServiceLifetime.Scoped // Note that Scoped is the default choice
                             // in AddDbContext. It is shown here only for
                             // pedagogic purposes.
      );
}
```

Le mode d’instanciation de DbContext ne doit pas être configuré comme ServiceLifetime.Transient ni ServiceLifetime.Singleton.

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a>Durée de vie de l’instance de dépôt dans votre conteneur IoC

De la même manière, la durée de vie du référentiel doit généralement être définie comme portée (InstancePerLifetimeScope dans Autofac). Cela peut également être temporaire (InstancePerDependency dans Autofac), mais votre service sera plus efficace en ce qui concerne la mémoire lors de l’utilisation de la durée de vie délimitée.

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

L’utilisation de la durée de vie du singleton pour le référentiel pourrait vous causer de graves problèmes de concurrence lorsque votre DbContext est configuré à la durée de vie (InstancePerLifetimeScope) (les durées de vie par défaut pour un DBContext).

### <a name="additional-resources"></a>Ressources supplémentaires

- **Mise en œuvre du dépôt et de l’unité des modèles de travail dans une application MVC ASP.NET** \
  <https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

- **Jonathan Allen. Stratégies de mise en œuvre pour le modèle de dépôt avec cadre d’entité, Dapper, et chaîne** \
  <https://www.infoq.com/articles/repository-implementation-strategies>

- **Cesar de la Torre. Comparaison ASP.NET durée de vie du service de conteneurs Core IoC avec les portées d’instance de conteneurs Autofac IoC** \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="table-mapping"></a>Mappage de table

Le mappage de tables identifie les données de table à interroger et enregistrer dans la base de données. Précédemment, vous avez vu comment les entités de domaine (par exemple, un produit ou domaine de commande) pouvaient servir à générer un schéma de base de données associé. EF est en grande partie conçu autour du concept de *conventions*. Les conventions abordent des questions telles que « Quel sera le nom d’une table? » ou « Quelle propriété est la clé principale? » Les conventions sont généralement basées sur des noms conventionnels. Par exemple, il est typique pour la clé `Id`principale d’être une propriété qui se termine par .

Par convention, chaque entité est configurée pour être mappée à une table avec le même nom que la propriété `DbSet<TEntity>` qui expose l’entité sur le contexte dérivé. Si aucune valeur de `DbSet<TEntity>` n’est fournie pour l’entité donnée, le nom de classe est utilisé.

### <a name="data-annotations-versus-fluent-api"></a>Annotations de données et API Fluent

Il existe de nombreuses conventions EF Core supplémentaires et la plupart d’entre elles peuvent être modifiées à l’aide des annotations de données ou de l’API Fluent, implémentée dans la méthode OnModelCreating.

Les annotations de données doivent être utilisées sur les classes de modèle d’entité, ce qui représente un moyen plus intrusif du point de vue DDD. En effet, vous contaminez votre modèle avec des annotations de données liées à la base de données de l’infrastructure. En revanche, l’API Fluent représente un moyen pratique de modifier la plupart des conventions et des mappages dans la couche d’infrastructure de persistance de données ; le modèle d’entité est donc propre et découplé de l’infrastructure de persistance.

### <a name="fluent-api-and-the-onmodelcreating-method"></a>API Fluent et la méthode OnModelCreating

Comme mentionné, afin de modifier les conventions et les mappages, vous pouvez utiliser la méthode OnModelCreating dans la classe DbContext.

Le microservice de commandes dans eShopOnContainers implémente une configuration et un mappage explicites, si nécessaire, comme indiqué dans le code suivant.

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities' configuration ...
}

// At OrderEntityTypeConfiguration.cs from eShopOnContainers
class OrderEntityTypeConfiguration : IEntityTypeConfiguration<Order>
{
    public void Configure(EntityTypeBuilder<Order> orderConfiguration)
    {
        orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);

        orderConfiguration.HasKey(o => o.Id);

        orderConfiguration.Ignore(b => b.DomainEvents);

        orderConfiguration.Property(o => o.Id)
            .UseHiLo("orderseq", OrderingContext.DEFAULT_SCHEMA);

        //Address value object persisted as owned entity type supported since EF Core 2.0
        orderConfiguration
            .OwnsOne(o => o.Address, a =>
            {
                a.WithOwner();
            });

        orderConfiguration
            .Property<int?>("_buyerId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("BuyerId")
            .IsRequired(false);

        orderConfiguration
            .Property<DateTime>("_orderDate")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("OrderDate")
            .IsRequired();

        orderConfiguration
            .Property<int>("_orderStatusId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("OrderStatusId")
            .IsRequired();

        orderConfiguration
            .Property<int?>("_paymentMethodId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("PaymentMethodId")
            .IsRequired(false);

        orderConfiguration.Property<string>("Description").IsRequired(false);

        var navigation = orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));

        // DDD Patterns comment:
        //Set as field (New since EF 1.1) to access the OrderItem collection property through its field
        navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

        orderConfiguration.HasOne<PaymentMethod>()
            .WithMany()
            .HasForeignKey("_paymentMethodId")
            .IsRequired(false)
            .OnDelete(DeleteBehavior.Restrict);

        orderConfiguration.HasOne<Buyer>()
            .WithMany()
            .IsRequired(false)
            .HasForeignKey("_buyerId");

        orderConfiguration.HasOne(o => o.OrderStatus)
            .WithMany()
            .HasForeignKey("_orderStatusId");
    }
}
```

Vous pouvez définir toutes les cartes fluentes de l’API dans la même `OnModelCreating` méthode, mais il est conseillé de partitionner ce code et d’avoir plusieurs classes de configuration, une par entité, comme indiqué dans l’exemple. Surtout pour les grands modèles, il est conseillé d’avoir des classes de configuration séparées pour configurer différents types d’entités.

Le code dans l’exemple montre quelques déclarations et mappages explicites. Toutefois, les conventions EF Core effectuant un grand nombre de ces mappages automatiquement, le code réel nécessaire dans votre cas peut être moindre.

### <a name="the-hilo-algorithm-in-ef-core"></a>Algorithme Hi/Lo dans EF Core

Un aspect intéressant du code dans l’exemple précédent est qu’il utilise [l’algorithme Hi/Lo](https://vladmihalcea.com/the-hilo-algorithm/) comme stratégie de génération de clés.

L’algorithme Hi/Lo est pratique quand vous avez besoin de clés uniques avant de valider des modifications. En résumé, l’algorithme Hi/Lo affecte des identificateurs uniques aux lignes de table sans dépendre du stockage immédiat de la ligne dans la base de données. Cela vous permet de commencer à utiliser les identificateurs dès à présent, comme c’est le cas avec les ID de base de données séquentiels standard.

L’algorithme Hi/Lo décrit un mécanisme permettant d’obtenir un lot d’ID uniques à partir d’une séquence de base de données associée. L’utilisation de ces ID est sûre, car la base de données garantit l’unicité : il n’y a donc pas de risques de collision entre les utilisateurs. Cet algorithme est intéressant pour les raisons suivantes :

- Il n’interrompt pas le modèle d’unité de travail.

- Il obtient les ID de séquence par lots, de façon réduire les allers-retours avec la base de données.

- Il génère un identificateur contrôlable de visu, contrairement aux techniques qui utilisent des GUID.

EF Core prend en `UseHiLo` charge [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) avec la méthode, comme le montre l’exemple précédent.

### <a name="map-fields-instead-of-properties"></a>Mapper des champs au lieu de propriétés

Avec cette fonctionnalité, disponible depuis EF Core 1.1, vous pouvez directement mapper les colonnes aux champs. Il est possible de ne pas utiliser de propriétés dans la classe d’entité et uniquement pour mapper les colonnes d’une table aux champs. Cette fonctionnalité est couramment utilisée dans le cadre des champs privés pour n’importe quel état interne qui ne doit pas être accessible depuis l’extérieur de l’entité.

Pour ce faire, utilisez des champs uniques, mais également des collections, comme un champ `List<>`. Ce point a été mentionné précédemment quand nous avons abordé la modélisation des classes de modèle de domaine, mais vous pouvez voir ici comment ce mappage est effectué avec la configuration `PropertyAccessMode.Field` mise en surbrillance dans le code précédent.

### <a name="use-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a>Utiliser des propriétés fantômes dans EF Core, masquées au niveau de l’infrastructure

Les propriétés cachées dans EF Core sont des propriétés qui n’existent pas dans votre modèle de classe d’entité. Les valeurs et les états de ces propriétés sont conservés uniquement dans la classe [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) au niveau de l’infrastructure.

## <a name="implement-the-query-specification-pattern"></a>Implémenter le modèle de spécification de requête

Comme introduit précédemment dans la section relative à la conception, le modèle de spécification de requête est un modèle DDD (Domain-Driven Design) conçu comme l’endroit où vous pouvez placer la définition d’une requête avec une logique facultative de pagination et de tri.

Le modèle de spécification de requête définit une requête dans un objet. Par exemple, pour encapsuler une requête paginée qui recherche certains produits, vous pouvez créer une spécification PagedProduct qui accepte les paramètres d’entrée nécessaires (pageNumber, pageSize, filtre, etc.). Ensuite, au sein d’une méthode du référentiel (généralement une surcharge de List()), elle peut accepter une IQuerySpecification et exécuter la requête attendue en fonction de cette spécification.

Le code suivant issu d’[eShopOnweb](https://github.com/dotnet-architecture/eShopOnWeb) est un exemple d’interface Spécification générique.

```csharp
// GENERIC SPECIFICATION INTERFACE
// https://github.com/dotnet-architecture/eShopOnWeb

public interface ISpecification<T>
{
    Expression<Func<T, bool>> Criteria { get; }
    List<Expression<Func<T, object>>> Includes { get; }
    List<string> IncludeStrings { get; }
}
```

Ensuite, l’implémentation d’une classe de base de spécification générique s’affiche comme suit.

```csharp
// GENERIC SPECIFICATION IMPLEMENTATION (BASE CLASS)
// https://github.com/dotnet-architecture/eShopOnWeb

public abstract class BaseSpecification<T> : ISpecification<T>
{
    public BaseSpecification(Expression<Func<T, bool>> criteria)
    {
        Criteria = criteria;
    }
    public Expression<Func<T, bool>> Criteria { get; }

    public List<Expression<Func<T, object>>> Includes { get; } =
                                           new List<Expression<Func<T, object>>>();

    public List<string> IncludeStrings { get; } = new List<string>();

    protected virtual void AddInclude(Expression<Func<T, object>> includeExpression)
    {
        Includes.Add(includeExpression);
    }

    // string-based includes allow for including children of children
    // e.g. Basket.Items.Product
    protected virtual void AddInclude(string includeString)
    {
        IncludeStrings.Add(includeString);
    }
}
```

Les spécifications suivantes chargent une entité de panier unique étant donné l’ID du panier ou l’id de l’acheteur à qui appartient le panier. Il [chargera avec empressement](/ef/core/querying/related-data) la collection du `Items` panier.

```csharp
// SAMPLE QUERY SPECIFICATION IMPLEMENTATION

public class BasketWithItemsSpecification : BaseSpecification<Basket>
{
    public BasketWithItemsSpecification(int basketId)
        : base(b => b.Id == basketId)
    {
        AddInclude(b => b.Items);
    }

    public BasketWithItemsSpecification(string buyerId)
        : base(b => b.BuyerId == buyerId)
    {
        AddInclude(b => b.Items);
    }
}
```

Enfin, vous pouvez voir ci-dessous comment un dépôt EF générique peut utiliser ce type de spécification pour filtrer et charger hâtivement des données liées à un type d’entité T donné.

```csharp
// GENERIC EF REPOSITORY WITH SPECIFICATION
// https://github.com/dotnet-architecture/eShopOnWeb

public IEnumerable<T> List(ISpecification<T> spec)
{
    // fetch a Queryable that includes all expression-based includes
    var queryableResultWithIncludes = spec.Includes
        .Aggregate(_dbContext.Set<T>().AsQueryable(),
            (current, include) => current.Include(include));

    // modify the IQueryable to include any string-based include statements
    var secondaryResult = spec.IncludeStrings
        .Aggregate(queryableResultWithIncludes,
            (current, include) => current.Include(include));

    // return the result of the query using the specification's criteria expression
    return secondaryResult
                    .Where(spec.Criteria)
                    .AsEnumerable();
}
```

En plus de l’encapsulation de la logique de filtrage, la spécification peut spécifier la forme des données à retourner, dont les propriétés à remplir.

Bien que nous ne `IQueryable` recommandons pas de revenir d’un référentiel, il est parfaitement bien de les utiliser dans le référentiel pour construire un ensemble de résultats. Vous pouvez voir cette approche utilisée dans la `IQueryable` méthode Liste ci-dessus, qui utilise des expressions intermédiaires pour constituer la liste des inclus de la requête avant d’exécuter la requête avec les critères de spécification sur la dernière ligne.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Cartographie de table** \
  [https://docs.microsoft.com/ef/core/modeling/relational/tables](/ef/core/modeling/relational/tables)

- **Utilisez HiLo pour générer des clés avec Entity Framework Core** \
  <https://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/>

- **Champs de soutien** \
  [https://docs.microsoft.com/ef/core/modeling/backing-field](/ef/core/modeling/backing-field)

- **Steve Smith. Collections encapsulées dans le noyau cadre d’entité** \
  <https://ardalis.com/encapsulated-collections-in-entity-framework-core>

- **Propriétés d’ombre** \
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- **Le modèle de spécification** \
  <https://deviq.com/specification-pattern/>

> [!div class="step-by-step"]
> [Suivant précédent](infrastructure-persistence-layer-design.md)
> [Next](nosql-database-persistence-infrastructure.md)
