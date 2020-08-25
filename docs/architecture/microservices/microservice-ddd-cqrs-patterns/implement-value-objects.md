---
title: Implémentation d’objets de valeur
description: Architecture de microservices .NET pour les applications .NET conteneurisées | Découvrez les explications détaillées et les options disponibles pour implémenter des objets de valeur à l’aide des nouvelles fonctionnalités d’Entity Framework.
ms.date: 08/21/2020
ms.openlocfilehash: 02eed7baaa364c62aa2df599f1d8b0e700dd215f
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811117"
---
# <a name="implement-value-objects"></a><span data-ttu-id="6ac05-103">Implémenter des objets de valeur</span><span class="sxs-lookup"><span data-stu-id="6ac05-103">Implement value objects</span></span>

<span data-ttu-id="6ac05-104">Comme indiqué dans les sections précédentes sur les entités et les agrégats, l’identité est fondamentale pour les entités.</span><span class="sxs-lookup"><span data-stu-id="6ac05-104">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="6ac05-105">Toutefois, un système comprend de nombreux objets et éléments de données qui ne nécessitent aucune identité et aucun suivi d’identité. C’est le cas notamment des objets de valeur.</span><span class="sxs-lookup"><span data-stu-id="6ac05-105">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="6ac05-106">Un objet de valeur peut faire référence à d’autres entités.</span><span class="sxs-lookup"><span data-stu-id="6ac05-106">A value object can reference other entities.</span></span> <span data-ttu-id="6ac05-107">Par exemple, dans une application qui génère un itinéraire entre un point A et un point B, cet itinéraire est un objet de valeur.</span><span class="sxs-lookup"><span data-stu-id="6ac05-107">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="6ac05-108">Il s’agit d’un instantané de points sur un itinéraire spécifique, mais cet itinéraire suggéré n’a pas d’identité, même s’il peut faire référence en interne à des entités comme City, Road, etc.</span><span class="sxs-lookup"><span data-stu-id="6ac05-108">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="6ac05-109">La figure 7-13 illustre l’objet de valeur Address dans l’agrégat Order.</span><span class="sxs-lookup"><span data-stu-id="6ac05-109">Figure 7-13 shows the Address value object within the Order aggregate.</span></span>

![Diagramme montrant l’objet Address value-à l’intérieur de l’agrégat Order.](./media/implement-value-objects/value-object-within-aggregate.png)

<span data-ttu-id="6ac05-111">**Figure 7-13**.</span><span class="sxs-lookup"><span data-stu-id="6ac05-111">**Figure 7-13**.</span></span> <span data-ttu-id="6ac05-112">Objet de valeur Address dans l’agrégat Order</span><span class="sxs-lookup"><span data-stu-id="6ac05-112">Address value object within the Order aggregate</span></span>

<span data-ttu-id="6ac05-113">Comme le montre la figure 7-13, une entité est généralement composée de plusieurs attributs.</span><span class="sxs-lookup"><span data-stu-id="6ac05-113">As shown in Figure 7-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="6ac05-114">Par exemple, l' `Order` entité peut être modélisée en tant qu’entité avec une identité et composée en interne d’un ensemble d’attributs tels que OrderID, OrderDate, OrderItems, etc. Toutefois, l’adresse, qui est simplement une valeur complexe composée d’un pays/d’une région, d’une rue, d’une ville, etc. et qui n’a pas d’identité dans ce domaine, doit être modélisée et traitée comme un objet de valeur.</span><span class="sxs-lookup"><span data-stu-id="6ac05-114">For example, the `Order` entity can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex-value composed of country/region, street, city, etc. and has no identity in this domain, must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="6ac05-115">Caractéristiques importantes des objets de valeur</span><span class="sxs-lookup"><span data-stu-id="6ac05-115">Important characteristics of value objects</span></span>

<span data-ttu-id="6ac05-116">Voici les deux principales caractéristiques des objets de valeur :</span><span class="sxs-lookup"><span data-stu-id="6ac05-116">There are two main characteristics for value objects:</span></span>

- <span data-ttu-id="6ac05-117">Ils n’ont pas d’identité.</span><span class="sxs-lookup"><span data-stu-id="6ac05-117">They have no identity.</span></span>

- <span data-ttu-id="6ac05-118">Ils sont immuables.</span><span class="sxs-lookup"><span data-stu-id="6ac05-118">They are immutable.</span></span>

<span data-ttu-id="6ac05-119">Nous avons déjà évoqué la première caractéristique.</span><span class="sxs-lookup"><span data-stu-id="6ac05-119">The first characteristic was already discussed.</span></span> <span data-ttu-id="6ac05-120">L’immuabilité est une exigence importante.</span><span class="sxs-lookup"><span data-stu-id="6ac05-120">Immutability is an important requirement.</span></span> <span data-ttu-id="6ac05-121">Une fois l’objet de valeur créé, ses valeurs doivent être immuables.</span><span class="sxs-lookup"><span data-stu-id="6ac05-121">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="6ac05-122">Par conséquent, lorsque l’objet est construit, vous devez fournir les valeurs requises, mais vous ne devez pas les autoriser à changer au cours de la durée de vie de l’objet.</span><span class="sxs-lookup"><span data-stu-id="6ac05-122">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object's lifetime.</span></span>

<span data-ttu-id="6ac05-123">De par la nature immuable des objets de valeur, vous pouvez recourir à certains stratagèmes pour améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="6ac05-123">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="6ac05-124">Cela vaut particulièrement pour les systèmes comprenant des milliers d’instances d’objet de valeur, bon nombre d’entre elles ayant les mêmes valeurs.</span><span class="sxs-lookup"><span data-stu-id="6ac05-124">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="6ac05-125">Du fait que ces objets sont immuables, vous pouvez les réutiliser. Il sont aussi interchangeables puisque leurs valeurs sont identiques et qu’ils n’ont pas d’identité.</span><span class="sxs-lookup"><span data-stu-id="6ac05-125">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="6ac05-126">C’est ce type d’optimisation qui fait parfois la différence entre un logiciel qui fonctionne lentement et un autre qui offre de bonnes performances.</span><span class="sxs-lookup"><span data-stu-id="6ac05-126">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="6ac05-127">Bien entendu, tous ces cas dépendent de l’environnement de l’application et du contexte de déploiement.</span><span class="sxs-lookup"><span data-stu-id="6ac05-127">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="6ac05-128">Implémentation d’objets de valeur en C\#</span><span class="sxs-lookup"><span data-stu-id="6ac05-128">Value object implementation in C\#</span></span>

<span data-ttu-id="6ac05-129">En termes d’implémentation, vous pouvez avoir une classe de base d’objet de valeur qui a des méthodes utilitaires de base comme l’égalité en fonction de la comparaison entre tous les attributs (puisqu’un objet de valeur ne doit pas être basé sur l’identité) et d’autres caractéristiques fondamentales.</span><span class="sxs-lookup"><span data-stu-id="6ac05-129">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on the comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="6ac05-130">L’exemple suivant montre une classe de base d’objet de valeur utilisée dans le microservice de commande d’eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="6ac05-130">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

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

    protected abstract IEnumerable<object> GetEqualityComponents();

    public override bool Equals(object obj)
    {
        if (obj == null || obj.GetType() != GetType())
        {
            return false;
        }

        var other = (ValueObject)obj;

        return this.GetEqualityComponents().SequenceEqual(other.GetEqualityComponents());
    }

    public override int GetHashCode()
    {
        return GetEqualityComponents()
            .Select(x => x != null ? x.GetHashCode() : 0)
            .Aggregate((x, y) => x ^ y);
    }
    // Other utility methods
}
```

<span data-ttu-id="6ac05-131">Vous pouvez utiliser cette classe quand vous implémentez votre objet de valeur réel, comme avec l’objet de valeur Address dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="6ac05-131">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }

    public Address() { }

    public Address(string street, string city, string state, string country, string zipcode)
    {
        Street = street;
        City = city;
        State = state;
        Country = country;
        ZipCode = zipcode;
    }

    protected override IEnumerable<object> GetEqualityComponents()
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

<span data-ttu-id="6ac05-132">Comme vous pouvez le voir, cette implémentation de l’objet de valeur Address n’a pas d’identité, et donc pas de champ ID, ni dans la classe Address ni dans la classe ValueObject.</span><span class="sxs-lookup"><span data-stu-id="6ac05-132">You can see how this value object implementation of Address has no identity and therefore, no ID field, neither at the Address class not even at the ValueObject class.</span></span>

<span data-ttu-id="6ac05-133">Il n’est pas possible d’avoir un champ d’ID dans une classe à utiliser par Entity Framework (EF) tant que EF Core 2,0, ce qui permet d’implémenter de meilleurs objets de valeur sans ID.</span><span class="sxs-lookup"><span data-stu-id="6ac05-133">Having no ID field in a class to be used by Entity Framework (EF) was not possible until EF Core 2.0, which greatly helps to implement better value objects with no ID.</span></span> <span data-ttu-id="6ac05-134">C’est précisément ce que nous allons expliquer dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="6ac05-134">That is precisely the explanation of the next section.</span></span>

<span data-ttu-id="6ac05-135">Il peut être allégué que les objets de valeur, qui sont immuables, doivent être en lecture seule (autrement dit, ont des propriétés d’accès en lecture seule) et cela est effectivement vrai.</span><span class="sxs-lookup"><span data-stu-id="6ac05-135">It could be argued that value objects, being immutable, should be read-only (that is, have get-only properties), and that's indeed true.</span></span> <span data-ttu-id="6ac05-136">Toutefois, les objets de valeur sont généralement sérialisés et désérialisés pour traverser les files d’attente de messages, et en lecture seule empêche le désérialiseur d’assigner des valeurs, vous ne pouvez donc pas les conserver comme `private set` , ce qui est suffisamment en lecture seule pour être pratique.</span><span class="sxs-lookup"><span data-stu-id="6ac05-136">However, value objects are usually serialized and deserialized to go through message queues, and being read-only stops the deserializer from assigning values, so you just leave them as `private set`, which is read-only enough to be practical.</span></span>

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20-and-later"></a><span data-ttu-id="6ac05-137">Comment conserver des objets de valeur dans la base de données avec EF Core 2,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="6ac05-137">How to persist value objects in the database with EF Core 2.0 and later</span></span>

<span data-ttu-id="6ac05-138">Vous venez de voir comment définir un objet de valeur dans votre modèle de domaine.</span><span class="sxs-lookup"><span data-stu-id="6ac05-138">You just saw how to define a value object in your domain model.</span></span> <span data-ttu-id="6ac05-139">Mais comment pouvez-vous réellement la conserver dans la base de données à l’aide de Entity Framework Core, car elle cible généralement les entités avec l’identité ?</span><span class="sxs-lookup"><span data-stu-id="6ac05-139">But how can you actually persist it into the database using Entity Framework Core since it usually targets entities with identity?</span></span>

### <a name="background-and-older-approaches-using-ef-core-11"></a><span data-ttu-id="6ac05-140">Informations générales et anciennes approches avec EF Core 1.1</span><span class="sxs-lookup"><span data-stu-id="6ac05-140">Background and older approaches using EF Core 1.1</span></span>

<span data-ttu-id="6ac05-141">En arrière-plan, une limitation lors de l’utilisation de EF Core 1,0 et 1,1 était que vous ne pouviez pas utiliser de [types complexes](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) tels que définis dans EF 6. x dans le .NET Framework traditionnel.</span><span class="sxs-lookup"><span data-stu-id="6ac05-141">As background, a limitation when using EF Core 1.0 and 1.1 was that you could not use [complex types](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) as defined in EF 6.x in the traditional .NET Framework.</span></span> <span data-ttu-id="6ac05-142">Si vous utilisez EF Core 1.0 ou 1.1, vous devez donc stocker votre objet de valeur sous la forme d’une entité EF avec un champ ID.</span><span class="sxs-lookup"><span data-stu-id="6ac05-142">Therefore, if using EF Core 1.0 or 1.1, you needed to store your value object as an EF entity with an ID field.</span></span> <span data-ttu-id="6ac05-143">Ensuite, pour qu’il ressemble plus à un objet de valeur sans identité, vous pouvez masquer son ID pour indiquer clairement que l’identité d’un objet de valeur n’est pas importante dans le modèle de domaine.</span><span class="sxs-lookup"><span data-stu-id="6ac05-143">Then, so it looked more like a value object with no identity, you could hide its ID so you make clear that the identity of a value object is not important in the domain model.</span></span> <span data-ttu-id="6ac05-144">Vous pouvez masquer cet ID en l’utilisant comme [propriété cachée](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span><span class="sxs-lookup"><span data-stu-id="6ac05-144">You could hide that ID by using the ID as a [shadow property](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span></span> <span data-ttu-id="6ac05-145">Cette configuration consistant à masquer l’ID dans le modèle étant configurée dans le niveau d’infrastructure EF, elle est en quelque sorte transparente pour votre modèle de domaine.</span><span class="sxs-lookup"><span data-stu-id="6ac05-145">Since that configuration for hiding the ID in the model is set up in the EF infrastructure level, it would be kind of transparent for your domain model.</span></span>

<span data-ttu-id="6ac05-146">Dans la version initiale d’eShopOnContainers (.NET Core 1.1), l’ID masqué exigé par l’infrastructure EF Core est implémenté de la manière suivante dans le niveau DbContext, à l’aide de l’API Fluent au niveau du projet d’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="6ac05-146">In the initial version of eShopOnContainers (.NET Core 1.1), the hidden ID needed by EF Core infrastructure was implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span> <span data-ttu-id="6ac05-147">L’ID est donc masqué du point de vue du modèle de domaine, mais il est toujours présent dans l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="6ac05-147">Therefore, the ID was hidden from the domain model point of view, but still present in the infrastructure.</span></span>

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

<span data-ttu-id="6ac05-148">Toutefois, la persistance de cet objet de valeur dans la base de données s’apparente à une entité normale dans une autre table.</span><span class="sxs-lookup"><span data-stu-id="6ac05-148">However, the persistence of that value object into the database was performed like a regular entity in a different table.</span></span>

<span data-ttu-id="6ac05-149">Avec EF Core 2,0 et versions ultérieures, il existe de nouvelles méthodes et de meilleures façons de conserver les objets de valeur.</span><span class="sxs-lookup"><span data-stu-id="6ac05-149">With EF Core 2.0 and later, there are new and better ways to persist value objects.</span></span>

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20-and-later"></a><span data-ttu-id="6ac05-150">Conserver les objets de valeur en tant que types d’entité détenus dans EF Core 2,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="6ac05-150">Persist value objects as owned entity types in EF Core 2.0 and later</span></span>

<span data-ttu-id="6ac05-151">Même avec certains écarts entre le modèle d’objet de valeur canonique dans DDD et le type d’entité détenu dans EF Core, il s’agit actuellement de la meilleure façon de rendre les objets de valeur persistants avec EF Core 2,0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="6ac05-151">Even with some gaps between the canonical value object pattern in DDD and the owned entity type in EF Core, it's currently the best way to persist value objects with EF Core 2.0 and later.</span></span> <span data-ttu-id="6ac05-152">Les limitations sont présentées à la fin de cette section.</span><span class="sxs-lookup"><span data-stu-id="6ac05-152">You can see limitations at the end of this section.</span></span>

<span data-ttu-id="6ac05-153">La fonctionnalité des types d’entité détenus est proposée dans EF Core depuis la version 2.0.</span><span class="sxs-lookup"><span data-stu-id="6ac05-153">The owned entity type feature was added to EF Core since version 2.0.</span></span>

<span data-ttu-id="6ac05-154">Un type d’entité détenu vous permet de mapper les types dont l’identité n’est pas explicitement définie dans le modèle de domaine et qui sont utilisés en tant que propriétés, par exemple un objet de valeur, dans l’une de vos entités.</span><span class="sxs-lookup"><span data-stu-id="6ac05-154">An owned entity type allows you to map types that do not have their own identity explicitly defined in the domain model and are used as properties, such as a value object, within any of your entities.</span></span> <span data-ttu-id="6ac05-155">Un type d’entité détenu partage le même type CLR avec un autre type d’entité (autrement dit, il s’agit simplement d’une classe normale).</span><span class="sxs-lookup"><span data-stu-id="6ac05-155">An owned entity type shares the same CLR type with another entity type (that is, it's just a regular class).</span></span> <span data-ttu-id="6ac05-156">L’entité contenant la navigation de définition est l’entité du propriétaire.</span><span class="sxs-lookup"><span data-stu-id="6ac05-156">The entity containing the defining navigation is the owner entity.</span></span> <span data-ttu-id="6ac05-157">Quand le propriétaire fait l’objet d’une interrogation, les types détenus sont inclus par défaut.</span><span class="sxs-lookup"><span data-stu-id="6ac05-157">When querying the owner, the owned types are included by default.</span></span>

<span data-ttu-id="6ac05-158">En examinant simplement le modèle de domaine, un type détenu semble ne pas avoir d’identité.</span><span class="sxs-lookup"><span data-stu-id="6ac05-158">Just by looking at the domain model, an owned type looks like it doesn't have any identity.</span></span> <span data-ttu-id="6ac05-159">Toutefois, en coulisses, les types détenus ont l’identité, mais la propriété de navigation propriétaire fait partie de cette identité.</span><span class="sxs-lookup"><span data-stu-id="6ac05-159">However, under the covers, owned types do have the identity, but the owner navigation property is part of this identity.</span></span>

<span data-ttu-id="6ac05-160">L’identité des instances de types détenus ne leur appartient pas entièrement.</span><span class="sxs-lookup"><span data-stu-id="6ac05-160">The identity of instances of owned types is not completely their own.</span></span> <span data-ttu-id="6ac05-161">Elle est formée de trois composants :</span><span class="sxs-lookup"><span data-stu-id="6ac05-161">It consists of three components:</span></span>

- <span data-ttu-id="6ac05-162">l’identité du propriétaire ;</span><span class="sxs-lookup"><span data-stu-id="6ac05-162">The identity of the owner</span></span>

- <span data-ttu-id="6ac05-163">la propriété de navigation pointant vers les types ;</span><span class="sxs-lookup"><span data-stu-id="6ac05-163">The navigation property pointing to them</span></span>

- <span data-ttu-id="6ac05-164">Dans le cas des collections de types détenus, un composant indépendant (pris en charge dans EF Core 2,2 et versions ultérieures).</span><span class="sxs-lookup"><span data-stu-id="6ac05-164">In the case of collections of owned types, an independent component (supported in EF Core 2.2 and later).</span></span>

<span data-ttu-id="6ac05-165">Par exemple, dans le modèle de domaine Ordering d’eShopOnContainers, dans le cadre de l’entité Order, l’objet de valeur Address est implémenté comme type d’entité détenu au sein de l’entité du propriétaire, qui est l’entité Order.</span><span class="sxs-lookup"><span data-stu-id="6ac05-165">For example, in the Ordering domain model at eShopOnContainers, as part of the Order entity, the Address value object is implemented as an owned entity type within the owner entity, which is the Order entity.</span></span> <span data-ttu-id="6ac05-166">`Address` est un type sans propriété d’identité définie dans le modèle de domaine.</span><span class="sxs-lookup"><span data-stu-id="6ac05-166">`Address` is a type with no identity property defined in the domain model.</span></span> <span data-ttu-id="6ac05-167">Il est utilisé comme propriété du type Order pour spécifier l’adresse d’expédition d’une commande particulière.</span><span class="sxs-lookup"><span data-stu-id="6ac05-167">It is used as a property of the Order type to specify the shipping address for a particular order.</span></span>

<span data-ttu-id="6ac05-168">Par convention, une clé primaire cachée est créée pour le type détenu et est mappée à la même table que le propriétaire à l’aide du fractionnement de table.</span><span class="sxs-lookup"><span data-stu-id="6ac05-168">By convention, a shadow primary key is created for the owned type and it will be mapped to the same table as the owner by using table splitting.</span></span> <span data-ttu-id="6ac05-169">Cela permet d’utiliser des types détenus à l’image des types complexes dans EF6 dans le .NET Framework traditionnel.</span><span class="sxs-lookup"><span data-stu-id="6ac05-169">This allows to use owned types similarly to how complex types are used in EF6 in the traditional .NET Framework.</span></span>

<span data-ttu-id="6ac05-170">Il est important de noter que les types détenus ne sont jamais découverts par convention dans EF Core. Vous devez donc les déclarer explicitement.</span><span class="sxs-lookup"><span data-stu-id="6ac05-170">It is important to note that owned types are never discovered by convention in EF Core, so you have to declare them explicitly.</span></span>

<span data-ttu-id="6ac05-171">Dans eShopOnContainers, dans le fichier OrderingContext.cs, dans la `OnModelCreating()` méthode, plusieurs configurations d’infrastructure sont appliquées.</span><span class="sxs-lookup"><span data-stu-id="6ac05-171">In eShopOnContainers, in the OrderingContext.cs file, within the `OnModelCreating()` method, multiple infrastructure configurations are applied.</span></span> <span data-ttu-id="6ac05-172">L’une d’entre elles est liée à l’entité Order.</span><span class="sxs-lookup"><span data-stu-id="6ac05-172">One of them is related to the Order entity.</span></span>

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

<span data-ttu-id="6ac05-173">Dans le code suivant, l’infrastructure de persistance est définie pour l’entité Order :</span><span class="sxs-lookup"><span data-stu-id="6ac05-173">In the following code, the persistence infrastructure is defined for the Order entity:</span></span>

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

<span data-ttu-id="6ac05-174">Dans le code précédent, la méthode `orderConfiguration.OwnsOne(o => o.Address)` spécifie que la propriété `Address` est une entité détenue de type `Order`.</span><span class="sxs-lookup"><span data-stu-id="6ac05-174">In the previous code, the `orderConfiguration.OwnsOne(o => o.Address)` method specifies that the `Address` property is an owned entity of the `Order` type.</span></span>

<span data-ttu-id="6ac05-175">Par défaut, les conventions EF Core nomment les colonnes de base de données pour les propriétés du type d’entité détenu comme suit : `EntityProperty_OwnedEntityProperty`.</span><span class="sxs-lookup"><span data-stu-id="6ac05-175">By default, EF Core conventions name the database columns for the properties of the owned entity type as `EntityProperty_OwnedEntityProperty`.</span></span> <span data-ttu-id="6ac05-176">Par conséquent, les propriétés internes de `Address` s’affichent dans la `Orders` table avec les noms `Address_Street` , `Address_City` (et ainsi de suite pour `State` , `Country` et `ZipCode` ).</span><span class="sxs-lookup"><span data-stu-id="6ac05-176">Therefore, the internal properties of `Address` will appear in the `Orders` table with the names `Address_Street`, `Address_City` (and so on for `State`, `Country`, and `ZipCode`).</span></span>

<span data-ttu-id="6ac05-177">Vous pouvez ajouter la méthode fluent `Property().HasColumnName()` pour renommer ces colonnes.</span><span class="sxs-lookup"><span data-stu-id="6ac05-177">You can append the `Property().HasColumnName()` fluent method to rename those columns.</span></span> <span data-ttu-id="6ac05-178">Si `Address` est une propriété publique, les mappages ressemblent aux suivants :</span><span class="sxs-lookup"><span data-stu-id="6ac05-178">In the case where `Address` is a public property, the mappings would be like the following:</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

<span data-ttu-id="6ac05-179">Il est possible de chaîner la `OwnsOne` méthode dans un mappage Fluent.</span><span class="sxs-lookup"><span data-stu-id="6ac05-179">It's possible to chain the `OwnsOne` method in a fluent mapping.</span></span> <span data-ttu-id="6ac05-180">Dans l’exemple hypothétique suivant, `OrderDetails` détient `BillingAddress` et `ShippingAddress`, qui sont tous deux des types `Address`.</span><span class="sxs-lookup"><span data-stu-id="6ac05-180">In the following hypothetical example, `OrderDetails` owns `BillingAddress` and `ShippingAddress`, which are both `Address` types.</span></span> <span data-ttu-id="6ac05-181">`OrderDetails` est alors détenu par le type `Order`.</span><span class="sxs-lookup"><span data-stu-id="6ac05-181">Then `OrderDetails` is owned by the `Order` type.</span></span>

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

### <a name="additional-details-on-owned-entity-types"></a><span data-ttu-id="6ac05-182">Détails supplémentaires sur les types d’entité détenus</span><span class="sxs-lookup"><span data-stu-id="6ac05-182">Additional details on owned entity types</span></span>

- <span data-ttu-id="6ac05-183">Les types détenus sont définis quand vous configurez une propriété de navigation en type particulier à l’aide de l’API fluent OwnsOne.</span><span class="sxs-lookup"><span data-stu-id="6ac05-183">Owned types are defined when you configure a navigation property to a particular type using the OwnsOne fluent API.</span></span>

- <span data-ttu-id="6ac05-184">La définition d’un type détenu dans notre modèle de métadonnées est un composite du type du propriétaire, de la propriété de navigation et du type CLR du type détenu.</span><span class="sxs-lookup"><span data-stu-id="6ac05-184">The definition of an owned type in our metadata model is a composite of: the owner type, the navigation property, and the CLR type of the owned type.</span></span>

- <span data-ttu-id="6ac05-185">L’identité (clé) d’une instance de type détenu dans notre pile est un composite de l’identité du type du propriétaire et de la définition du type détenu.</span><span class="sxs-lookup"><span data-stu-id="6ac05-185">The identity (key) of an owned type instance in our stack is a composite of the identity of the owner type and the definition of the owned type.</span></span>

#### <a name="owned-entities-capabilities"></a><span data-ttu-id="6ac05-186">Fonctionnalités des entités détenues</span><span class="sxs-lookup"><span data-stu-id="6ac05-186">Owned entities capabilities</span></span>

- <span data-ttu-id="6ac05-187">Les types détenus peuvent référencer d’autres entités, qu’elles soient détenues (types détenus imbriqués) ou non (propriétés de navigation de référence régulières à d’autres entités).</span><span class="sxs-lookup"><span data-stu-id="6ac05-187">Owned types can reference other entities, either owned (nested owned types) or non-owned (regular reference navigation properties to other entities).</span></span>

- <span data-ttu-id="6ac05-188">Vous pouvez mapper le même type CLR en tant que types détenus différents dans la même entité du propriétaire par le biais de propriétés de navigation distinctes.</span><span class="sxs-lookup"><span data-stu-id="6ac05-188">You can map the same CLR type as different owned types in the same owner entity through separate navigation properties.</span></span>

- <span data-ttu-id="6ac05-189">Le fractionnement de table est configuré par Convention, mais vous pouvez le désactiver en mappant le type détenu à une autre table à l’aide de ToTable.</span><span class="sxs-lookup"><span data-stu-id="6ac05-189">Table splitting is set up by convention, but you can opt out by mapping the owned type to a different table using ToTable.</span></span>

- <span data-ttu-id="6ac05-190">Le chargement hâtif est effectué automatiquement sur les types détenus, autrement dit, il n’est pas nécessaire d’appeler `.Include()` la requête.</span><span class="sxs-lookup"><span data-stu-id="6ac05-190">Eager loading is performed automatically on owned types, that is, there's no need to call `.Include()` on the query.</span></span>

- <span data-ttu-id="6ac05-191">Peut être configuré avec `[Owned]` l’attribut à l’aide de EF Core 2,1 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="6ac05-191">Can be configured with attribute `[Owned]`, using EF Core 2.1 and later.</span></span>

- <span data-ttu-id="6ac05-192">Peut gérer des collections de types détenus (à l’aide de la version 2,2 et versions ultérieures).</span><span class="sxs-lookup"><span data-stu-id="6ac05-192">Can handle collections of owned types (using version 2.2 and later).</span></span>

#### <a name="owned-entities-limitations"></a><span data-ttu-id="6ac05-193">Limitations des entités détenues</span><span class="sxs-lookup"><span data-stu-id="6ac05-193">Owned entities limitations</span></span>

- <span data-ttu-id="6ac05-194">Vous ne pouvez pas créer un `DbSet<T>` d’un type détenu (par conception).</span><span class="sxs-lookup"><span data-stu-id="6ac05-194">You can't create a `DbSet<T>` of an owned type (by design).</span></span>

- <span data-ttu-id="6ac05-195">Vous ne pouvez pas appeler `ModelBuilder.Entity<T>()` sur des types détenus (actuellement par conception).</span><span class="sxs-lookup"><span data-stu-id="6ac05-195">You can't call `ModelBuilder.Entity<T>()` on owned types (currently by design).</span></span>

- <span data-ttu-id="6ac05-196">Aucune prise en charge des types facultatifs (autrement dit, Nullable) qui sont mappés avec le propriétaire dans la même table (autrement dit, en utilisant le fractionnement de table).</span><span class="sxs-lookup"><span data-stu-id="6ac05-196">No support for optional (that is, nullable) owned types that are mapped with the owner in the same table (that is, using table splitting).</span></span> <span data-ttu-id="6ac05-197">Cela est dû au fait que le mappage est effectué pour chaque propriété, il n’existe pas de sentinelle distincte pour la valeur complexe null dans son ensemble.</span><span class="sxs-lookup"><span data-stu-id="6ac05-197">This is because mapping is done for each property, there is no  separate sentinel for the null complex value as a whole.</span></span>

- <span data-ttu-id="6ac05-198">Aucune prise en charge du mappage d’héritage pour les types détenus, mais vous devez être en mesure de mapper deux types feuille des mêmes hiérarchies d’héritage en tant que types détenus différents.</span><span class="sxs-lookup"><span data-stu-id="6ac05-198">No inheritance-mapping support for owned types, but you should be able to map two leaf types of the same inheritance hierarchies as different owned types.</span></span> <span data-ttu-id="6ac05-199">EF Core ne réalise pas qu’ils font partie de la même hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="6ac05-199">EF Core will not reason about the fact that they are part of the same hierarchy.</span></span>

#### <a name="main-differences-with-ef6s-complex-types"></a><span data-ttu-id="6ac05-200">Principales différences avec les types complexes d’EF6</span><span class="sxs-lookup"><span data-stu-id="6ac05-200">Main differences with EF6's complex types</span></span>

- <span data-ttu-id="6ac05-201">Le fractionnement de table est facultatif, autrement dit, ils peuvent éventuellement être mappés à une table distincte et sont toujours des types détenus.</span><span class="sxs-lookup"><span data-stu-id="6ac05-201">Table splitting is optional, that is, they can optionally be mapped to a separate table and still be owned types.</span></span>

- <span data-ttu-id="6ac05-202">Ils peuvent référencer d’autres entités (autrement dit, ils peuvent agir comme côté dépendant sur des relations avec d’autres types non détenus).</span><span class="sxs-lookup"><span data-stu-id="6ac05-202">They can reference other entities (that is, they can act as the dependent side on relationships to other non-owned types).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="6ac05-203">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="6ac05-203">Additional resources</span></span>

- <span data-ttu-id="6ac05-204">**Martin Fowler. Modèle ValueObject** </span><span class="sxs-lookup"><span data-stu-id="6ac05-204">**Martin Fowler. ValueObject pattern** </span></span>\
  <https://martinfowler.com/bliki/ValueObject.html>

- <span data-ttu-id="6ac05-205">**Eric Evans. Conception pilotée par domaine : la complexité du logiciel est plus complexe.**</span><span class="sxs-lookup"><span data-stu-id="6ac05-205">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="6ac05-206">(Livre incluant une discussion sur les objets de valeur) </span><span class="sxs-lookup"><span data-stu-id="6ac05-206">(Book; includes a discussion of value objects) </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- <span data-ttu-id="6ac05-207">**Vaughn Vernon. Implémentation de la conception pilotée par le domaine.**</span><span class="sxs-lookup"><span data-stu-id="6ac05-207">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="6ac05-208">(Livre incluant une discussion sur les objets de valeur) </span><span class="sxs-lookup"><span data-stu-id="6ac05-208">(Book; includes a discussion of value objects) </span></span>\
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- <span data-ttu-id="6ac05-209">**Types d’entité détenus** </span><span class="sxs-lookup"><span data-stu-id="6ac05-209">**Owned Entity Types** </span></span>\
  <https://docs.microsoft.com/ef/core/modeling/owned-entities>

- <span data-ttu-id="6ac05-210">**Propriétés Shadow** </span><span class="sxs-lookup"><span data-stu-id="6ac05-210">**Shadow Properties** </span></span>\
  <https://docs.microsoft.com/ef/core/modeling/shadow-properties>

- <span data-ttu-id="6ac05-211">**Types complexes et/ou objets de valeur**.</span><span class="sxs-lookup"><span data-stu-id="6ac05-211">**Complex types and/or value objects**.</span></span> <span data-ttu-id="6ac05-212">Discussion dans le dépôt GitHub EF Core (onglet des problèmes) </span><span class="sxs-lookup"><span data-stu-id="6ac05-212">Discussion in the EF Core GitHub repo (Issues tab) </span></span>\
  <https://github.com/dotnet/efcore/issues/246>

- <span data-ttu-id="6ac05-213">**ValueObject.cs.**</span><span class="sxs-lookup"><span data-stu-id="6ac05-213">**ValueObject.cs.**</span></span> <span data-ttu-id="6ac05-214">Classe d’objet de valeur de base dans eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="6ac05-214">Base value object class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs>

- <span data-ttu-id="6ac05-215">**Classe d’adresses.**</span><span class="sxs-lookup"><span data-stu-id="6ac05-215">**Address class.**</span></span> <span data-ttu-id="6ac05-216">Exemple de classe d’objet de valeur dans eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="6ac05-216">Sample value object class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs>

> [!div class="step-by-step"]
> <span data-ttu-id="6ac05-217">[Précédent](seedwork-domain-model-base-classes-interfaces.md) 
>  [Suivant](enumeration-classes-over-enum-types.md)</span><span class="sxs-lookup"><span data-stu-id="6ac05-217">[Previous](seedwork-domain-model-base-classes-interfaces.md)
[Next](enumeration-classes-over-enum-types.md)</span></span>
