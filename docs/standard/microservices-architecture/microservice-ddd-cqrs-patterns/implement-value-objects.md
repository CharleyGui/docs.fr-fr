---
title: Implémentation d’objets de valeur
description: Architecture de microservices .NET pour les applications .NET conteneurisées | Découvrez les explications détaillées et les options disponibles pour implémenter des objets de valeur à l’aide des nouvelles fonctionnalités d’Entity Framework.
ms.date: 10/08/2018
ms.openlocfilehash: 850d571ffb92f2d200e24430a9611fb13b64e635
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644297"
---
# <a name="implement-value-objects"></a>Implémenter des objets de valeur

Comme indiqué dans les sections précédentes sur les entités et les agrégats, l’identité est fondamentale pour les entités. Toutefois, un système comprend de nombreux objets et éléments de données qui ne nécessitent aucune identité et aucun suivi d’identité. C’est le cas notamment des objets de valeur.

Un objet de valeur peut faire référence à d’autres entités. Par exemple, dans une application qui génère un itinéraire entre un point A et un point B, cet itinéraire est un objet de valeur. Il s’agit d’un instantané de points sur un itinéraire spécifique, mais cet itinéraire suggéré n’a pas d’identité, même s’il peut faire référence en interne à des entités comme City, Road, etc.

La figure 7-13 illustre l’objet de valeur Address dans l’agrégat Order.

![Objet de valeur Address dans l’agrégat Order.](./media/image14.png)

**Figure 7-13**. Objet de valeur Address dans l’agrégat Order

Comme le montre la figure 7-13, une entité est généralement composée de plusieurs attributs. Par exemple, l’entité `Order` peut être modélisée comme entité avec une identité et composée en interne d’un ensemble d’attributs comme OrderId, OrderDate, OrderItems, etc. Mais l’adresse, qui est simplement une valeur complexe comprenant un pays, une rue, une ville, etc. et qui n’a pas d’identité dans ce domaine, doit être modélisée et traitée comme objet de valeur.

## <a name="important-characteristics-of-value-objects"></a>Caractéristiques importantes des objets de valeur

Voici les deux principales caractéristiques des objets de valeur :

- Ils n’ont pas d’identité.

- Ils sont immuables.

Nous avons déjà évoqué la première caractéristique. L’immuabilité est une exigence importante. Une fois l’objet de valeur créé, ses valeurs doivent être immuables. Vous devez donc fournir les valeurs demandées au moment de la construction de l’objet, mais vous devez interdire tout changement de ces valeurs pendant la durée de vie de l’objet.

De par la nature immuable des objets de valeur, vous pouvez recourir à certains stratagèmes pour améliorer les performances. Cela vaut particulièrement pour les systèmes comprenant des milliers d’instances d’objet de valeur, bon nombre d’entre elles ayant les mêmes valeurs. Du fait que ces objets sont immuables, vous pouvez les réutiliser. Il sont aussi interchangeables puisque leurs valeurs sont identiques et qu’ils n’ont pas d’identité. C’est ce type d’optimisation qui fait parfois la différence entre un logiciel qui fonctionne lentement et un autre qui offre de bonnes performances. Bien entendu, tous ces cas dépendent de l’environnement de l’application et du contexte de déploiement.

## <a name="value-object-implementation-in-c"></a>Implémentation d’objets de valeur en C\#

En termes d’implémentation, vous pouvez avoir une classe de base d’objet de valeur comprenant des méthodes utilitaires simples, par exemple une méthode d’égalité basée sur la comparaison de tous les attributs (puisqu’un objet de valeur ne doit pas être basé sur l’identité), et d’autres caractéristiques fondamentales. L’exemple suivant montre une classe de base d’objet de valeur utilisée dans le microservice de commande d’eShopOnContainers.

```csharp
public abstract class ValueObject
{
    protected static bool EqualOperator(ValueObject left, ValueObject right)
    {
        if (ReferenceEquals(left, null) ^ ReferenceEquals(right, null))
        {
            return false;
        }
        return ReferenceEquals(left, null) || left.Equals(right);
    }

    protected static bool NotEqualOperator(ValueObject left, ValueObject right)
    {
        return !(EqualOperator(left, right));
    }

    protected abstract IEnumerable<object> GetAtomicValues();

    public override bool Equals(object obj)
    {
        if (obj == null || obj.GetType() != GetType())
        {
            return false;
        }

        ValueObject other = (ValueObject)obj;
        IEnumerator<object> thisValues = GetAtomicValues().GetEnumerator();
        IEnumerator<object> otherValues = other.GetAtomicValues().GetEnumerator();
        while (thisValues.MoveNext() && otherValues.MoveNext())
        {
            if (ReferenceEquals(thisValues.Current, null) ^
                ReferenceEquals(otherValues.Current, null))
            {
                return false;
            }

            if (thisValues.Current != null &&
                !thisValues.Current.Equals(otherValues.Current))
            {
                return false;
            }
        }
        return !thisValues.MoveNext() && !otherValues.MoveNext();
    }

    public override int GetHashCode()
    {
        return GetAtomicValues()
         .Select(x => x != null ? x.GetHashCode() : 0)
         .Aggregate((x, y) => x ^ y);
    }
    // Other utility methods
}
```

Vous pouvez utiliser cette classe quand vous implémentez votre objet de valeur réel, comme avec l’objet de valeur Address dans l’exemple suivant :

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }

    private Address() { }

    public Address(string street, string city, string state, string country, string zipcode)
    {
        Street = street;
        City = city;
        State = state;
        Country = country;
        ZipCode = zipcode;
    }

    protected override IEnumerable<object> GetAtomicValues()
    {
        // Using a yield return statement to return each element one at a time
        yield return Street;
        yield return City;
        yield return State;
        yield return Country;
        yield return ZipCode;
    }
}
```

Comme vous pouvez le voir, cette implémentation de l’objet de valeur Address n’a pas d’identité, et donc pas de champ ID, ni dans la classe Address ni dans la classe ValueObject.

L’absence de champ ID dans une classe utilisée par Entity Framework n’était pas possible avant EF Core 2.0. Il est maintenant beaucoup plus simple d’implémenter correctement des objets de valeur sans ID. C’est précisément ce que nous allons expliquer dans la section suivante.

On pourrait penser que, comme ils sont immuables, les objets de valeur doivent être en lecture seule (avec des propriétés get-only). C’est exact. Toutefois, ils sont généralement sérialisés et désérialisés dans les files d’attente ; or, s’ils sont en lecture seule, le désérialiseur arrête l’affectation de valeurs. Pour des raisons pratiques, nous allons simplement les laisser définis comme privés, ce qui constitue un niveau de lecture seule suffisant.

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20"></a>Comment rendre des objets de valeur persistants dans la base de données avec EF Core 2.0

Vous venez de voir comment définir un objet de valeur dans votre modèle de domaine. Mais comment faire pour le rendre persistant dans la base de données au moyen d’Entity Framework (EF) Core, qui cible généralement les entités avec l’identité ?

### <a name="background-and-older-approaches-using-ef-core-11"></a>Informations générales et anciennes approches avec EF Core 1.1

À titre d’information, EF Core 1.0 ou 1.1 présente des limitations, en ce sens qu’il n’est pas possible de recourir aux [types complexes](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) définis dans EF 6.x dans le .NET Framework traditionnel. Si vous utilisez EF Core 1.0 ou 1.1, vous devez donc stocker votre objet de valeur sous la forme d’une entité EF avec un champ ID. Ensuite, pour qu’il ressemble plus à un objet de valeur sans identité, vous pouvez masquer son ID pour indiquer clairement que l’identité d’un objet de valeur n’est pas importante dans le modèle de domaine. Vous pouvez masquer cet ID en l’utilisant comme [propriété cachée](https://docs.microsoft.com/ef/core/modeling/shadow-properties ). Cette configuration consistant à masquer l’ID dans le modèle étant configurée dans le niveau d’infrastructure EF, elle est en quelque sorte transparente pour votre modèle de domaine.

Dans la version initiale d’eShopOnContainers (.NET Core 1.1), l’ID masqué exigé par l’infrastructure EF Core est implémenté de la manière suivante dans le niveau DbContext, à l’aide de l’API Fluent au niveau du projet d’infrastructure. L’ID est donc masqué du point de vue du modèle de domaine, mais il est toujours présent dans l’infrastructure.

```csharp
// Old approach with EF Core 1.1
// Fluent API within the OrderingContext:DbContext in the Infrastructure project
void ConfigureAddress(EntityTypeBuilder<Address> addressConfiguration)
{
    addressConfiguration.ToTable("address", DEFAULT_SCHEMA);

    addressConfiguration.Property<int>("Id")  // Id is a shadow property
        .IsRequired();
    addressConfiguration.HasKey("Id");   // Id is a shadow property
}
```

Toutefois, la persistance de cet objet de valeur dans la base de données s’apparente à une entité normale dans une autre table.

EF Core 2.0 offre de nouveaux moyens plus efficaces de rendre les objets de valeur persistants.

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20"></a>Rendre les objets de valeur persistants en tant que types d’entité détenus dans EF Core 2.0

Même si des écarts existent entre le modèle d’objet de valeur canonique dans DDD et le type d’entité détenu dans EF Core, il s’agit actuellement de la meilleure façon de rendre les objets de valeur persistants avec EF Core 2.0. Les limitations sont présentées à la fin de cette section.

La fonctionnalité des types d’entité détenus est proposée dans EF Core depuis la version 2.0.

Un type d’entité détenu vous permet de mapper les types dont l’identité n’est pas explicitement définie dans le modèle de domaine et qui sont utilisés en tant que propriétés, par exemple un objet de valeur, dans l’une de vos entités. Un type d’entité détenu partage le même type CLR avec un autre type d’entité (comme une classe standard). L’entité contenant la navigation de définition est l’entité du propriétaire. Quand le propriétaire fait l’objet d’une interrogation, les types détenus sont inclus par défaut.

Un simple coup d’œil au modèle de domaine suffit pour constater qu’un type détenu n’a apparemment pas d’identité. Les types détenus ont toutefois une identité, mais la propriété de navigation du propriétaire fait partie de cette identité.

L’identité des instances de types détenus ne leur appartient pas entièrement. Elle est formée de trois composants :

- l’identité du propriétaire ;

- la propriété de navigation pointant vers les types ;

- dans le cas de collections de types détenus, un composant indépendant (non pris en charge dans EF Core 2.0 ; prise en charge prévue dans la version 2.2).

Par exemple, dans le modèle de domaine Ordering d’eShopOnContainers, dans le cadre de l’entité Order, l’objet de valeur Address est implémenté comme type d’entité détenu au sein de l’entité du propriétaire, qui est l’entité Order. Address est un type dont la propriété d’identité n’est pas définie dans le modèle de domaine. Il est utilisé comme propriété du type Order pour spécifier l’adresse d’expédition d’une commande particulière.

Par convention, une clé primaire cachée est créée pour le type détenu et est mappée à la même table que le propriétaire à l’aide du fractionnement de table. Cela permet d’utiliser des types détenus à l’image des types complexes dans EF6 dans le .NET Framework traditionnel.

Il est important de noter que les types détenus ne sont jamais découverts par convention dans EF Core. Vous devez donc les déclarer explicitement.

Dans eShopOnContainers, au niveau d’OrderingContext.cs, dans la méthode OnModelCreating(), plusieurs configurations d’infrastructure sont appliquées. L’une d’entre elles est liée à l’entité Order.

```csharp
// Part of the OrderingContext.cs class at the Ordering.Infrastructure project
//
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    modelBuilder.ApplyConfiguration(new ClientRequestEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new PaymentMethodEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new OrderItemEntityTypeConfiguration());
    //...Additional type configurations
}
```

Dans le code suivant, l’infrastructure de persistance est définie pour l’entité Order :

```csharp
// Part of the OrderEntityTypeConfiguration.cs class
//
public void Configure(EntityTypeBuilder<Order> orderConfiguration)
{
    orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);
    orderConfiguration.HasKey(o => o.Id);
    orderConfiguration.Ignore(b => b.DomainEvents);
    orderConfiguration.Property(o => o.Id)
        .ForSqlServerUseSequenceHiLo("orderseq", OrderingContext.DEFAULT_SCHEMA);

    //Address value object persisted as owned entity in EF Core 2.0
    orderConfiguration.OwnsOne(o => o.Address);

    orderConfiguration.Property<DateTime>("OrderDate").IsRequired();

    //...Additional validations, constraints and code...
    //...
}
```

Dans le code précédent, la méthode `orderConfiguration.OwnsOne(o => o.Address)` spécifie que la propriété `Address` est une entité détenue de type `Order`.

Par défaut, les conventions EF Core nomment les colonnes de base de données pour les propriétés du type d’entité détenu comme suit : `EntityProperty_OwnedEntityProperty`. Les propriétés internes liées à `Address` apparaissent donc dans la table `Orders` avec les noms `Address_Street`, `Address_City` (et ainsi de suite pour `State`, `Country` et `ZipCode`).

Vous pouvez ajouter la méthode fluent `Property().HasColumnName()` pour renommer ces colonnes. Si `Address` est une propriété publique, les mappages ressemblent aux suivants :

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

Il est possible de chaîner la méthode `OwnsOne` dans un mappage fluent. Dans l’exemple hypothétique suivant, `OrderDetails` détient `BillingAddress` et `ShippingAddress`, qui sont tous deux des types `Address`. `OrderDetails` est alors détenu par le type `Order`.

```csharp
orderConfiguration.OwnsOne(p => p.OrderDetails, cb =>
    {
        cb.OwnsOne(c => c.BillingAddress);
        cb.OwnsOne(c => c.ShippingAddress);
    });
//...
//...
public class Order
{
    public int Id { get; set; }
    public OrderDetails OrderDetails { get; set; }
}

public class OrderDetails
{
    public Address BillingAddress { get; set; }
    public Address ShippingAddress { get; set; }
}

public class Address
{
    public string Street { get; set; }
    public string City { get; set; }
}
```

### <a name="additional-details-on-owned-entity-types"></a>Détails supplémentaires sur les types d’entité détenus

- Les types détenus sont définis quand vous configurez une propriété de navigation en type particulier à l’aide de l’API fluent OwnsOne.

- La définition d’un type détenu dans notre modèle de métadonnées est un composite du type du propriétaire, de la propriété de navigation et du type CLR du type détenu.

- L’identité (clé) d’une instance de type détenu dans notre pile est un composite de l’identité du type du propriétaire et de la définition du type détenu.

#### <a name="owned-entities-capabilities"></a>Fonctionnalités des entités détenues :

- Les types détenus peuvent référencer d’autres entités, qu’elles soient détenues (types détenus imbriqués) ou non (propriétés de navigation de référence régulières à d’autres entités).

- Vous pouvez mapper le même type CLR en tant que types détenus différents dans la même entité du propriétaire par le biais de propriétés de navigation distinctes.

- Le fractionnement de table est configuré par convention, mais vous pouvez le refuser en mappant le type détenu à une autre table à l’aide de ToTable.

- Un chargement hâtif est effectué automatiquement sur les types détenus. Il est donc inutile d’appeler Include() sur la requête.

- Cela peut être configuré avec l’attribut \[Owned\] dans EF Core 2.1

#### <a name="owned-entities-limitations"></a>Limitations des entités détenues :

- Vous ne pouvez pas créer un DbSet\<T\> d’un type détenu (par conception).

- Vous ne pouvez pas appeler ModelBuilder.Entity\<T\>() sur des types détenus (actuellement par conception).

- Il n’y a pas de collections de types détenus dans EF Core 2.1 et versions antérieures, mais leur prise en charge est prévue dans la version 2.2.

- Les types détenus facultatifs (acceptant une valeur Null) qui sont mappés avec le propriétaire dans la même table (à l’aide du fractionnement de table) ne sont pas pris en charge. Cela est dû au fait que le mappage est effectué pour chaque propriété, et nous n’avons pas de sentinelle séparée pour traiter globalement la valeur complexe Null.

- Le mappage d’héritage pour les types détenus n’est pas pris en charge, mais vous pouvez normalement mapper deux types feuilles des mêmes hiérarchies d’héritage en tant que types détenus différents. EF Core ne réalise pas qu’ils font partie de la même hiérarchie.

#### <a name="main-differences-with-ef6s-complex-types"></a>Principales différences avec les types complexes d’EF6

- Le fractionnement de table est facultatif, c’est-à-dire que les types peuvent éventuellement être mappés à une table distincte tout en restant des types détenus.

- Ils peuvent référencer d’autres entités (et donc constituer la partie dépendante des relations à d’autres types non détenus).

## <a name="additional-resources"></a>Ressources supplémentaires

- **Martin Fowler. Modèle ValueObject** \
  <https://martinfowler.com/bliki/ValueObject.html>

- **Eric Evans. Domain-Driven Design : Tackling Complexity in the Heart of Software.** (Livre incluant une discussion sur les objets de valeur) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- **Vaughn Vernon. Implementing Domain-Driven Design.** (Livre incluant une discussion sur les objets de valeur) \
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- **Propriétés cachées** \
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- **Types complexes et/ou objets de valeur**. Discussion dans le dépôt GitHub EF Core (onglet des problèmes) \
  <https://github.com/aspnet/EntityFramework/issues/246>

- **ValueObject.cs.** Classe d’objet de valeur de base dans eShopOnContainers. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs>

- **Classe d’adresses.** Exemple de classe d’objet de valeur dans eShopOnContainers. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs>

> [!div class="step-by-step"]
> [Précédent](seedwork-domain-model-base-classes-interfaces.md)
> [Suivant](enumeration-classes-over-enum-types.md)
