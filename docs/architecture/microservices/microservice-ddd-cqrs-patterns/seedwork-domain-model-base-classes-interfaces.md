---
title: Seedwork (interfaces et classes de base réutilisables pour votre modèle de domaine)
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Utiliser le concept de seedwork comme point de départ pour démarrer l’implémentation d’un modèle de domaine orienté DDD.
ms.date: 10/08/2018
ms.openlocfilehash: ab0aadc28dbd1175c75b04dadca29b7b0947f29b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116570"
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a><span data-ttu-id="836b5-103">Seedwork (interfaces et classes de base réutilisables pour votre modèle de domaine)</span><span class="sxs-lookup"><span data-stu-id="836b5-103">Seedwork (reusable base classes and interfaces for your domain model)</span></span>

<span data-ttu-id="836b5-104">Le dossier solution contient un dossier *SeedWork*.</span><span class="sxs-lookup"><span data-stu-id="836b5-104">The solution folder contains a *SeedWork* folder.</span></span> <span data-ttu-id="836b5-105">Ce dossier contient des classes de base personnalisées que vous pouvez utiliser comme base pour les entités et les objets de valeur de votre domaine.</span><span class="sxs-lookup"><span data-stu-id="836b5-105">This folder contains custom base classes that you can use as a base for your domain entities and value objects.</span></span> <span data-ttu-id="836b5-106">Utilisez ces classes de base afin de ne pas avoir de code redondant dans la classe d’objets de chaque domaine.</span><span class="sxs-lookup"><span data-stu-id="836b5-106">Use these base classes so you don't have redundant code in each domain’s object class.</span></span> <span data-ttu-id="836b5-107">Le dossier de ces types de classes s’appelle *SeedWork* et non pas *Framework*.</span><span class="sxs-lookup"><span data-stu-id="836b5-107">The folder for these types of classes is called *SeedWork* and not something like *Framework*.</span></span> <span data-ttu-id="836b5-108">C’est ce qu’on appelle *SeedWork* parce que le dossier ne contient qu’un petit sous-ensemble de classes réutilisables qui ne peuvent pas vraiment être considérés comme un cadre.</span><span class="sxs-lookup"><span data-stu-id="836b5-108">It's called *SeedWork* because the folder contains just a small subset of reusable classes that cannot really be considered a framework.</span></span> <span data-ttu-id="836b5-109">*Seedwork* est un terme introduit par [Michael Feathers](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) que [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) a rendu populaire, mais vous pouvez également donner à ce dossier le nom Common, SharedKernel ou un autre nom similaire.</span><span class="sxs-lookup"><span data-stu-id="836b5-109">*Seedwork* is a term introduced by [Michael Feathers](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) and popularized by [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) but you could also name that folder Common, SharedKernel, or similar.</span></span>

<span data-ttu-id="836b5-110">La figure 7-12 montre les classes qui constituent le seedwork du modèle de domaine dans le microservice Ordering.</span><span class="sxs-lookup"><span data-stu-id="836b5-110">Figure 7-12 shows the classes that form the seedwork of the domain model in the ordering microservice.</span></span> <span data-ttu-id="836b5-111">Il comporte quelques classes de base personnalisées comme Entity, ValueObject et Enumeration, ainsi que quelques interfaces.</span><span class="sxs-lookup"><span data-stu-id="836b5-111">It has a few custom base classes like Entity, ValueObject, and Enumeration, plus a few interfaces.</span></span> <span data-ttu-id="836b5-112">Ces interfaces (IRepository et IUnitOfWork) informent la couche d’infrastructure sur ce qui doit être implémenté.</span><span class="sxs-lookup"><span data-stu-id="836b5-112">These interfaces (IRepository and IUnitOfWork) inform the infrastructure layer about what needs to be implemented.</span></span> <span data-ttu-id="836b5-113">Elles sont également utilisées par injection de dépendances à partir de la couche Application.</span><span class="sxs-lookup"><span data-stu-id="836b5-113">Those interfaces are also used through Dependency Injection from the application layer.</span></span>

:::image type="complex" source="./media/seedwork-domain-model-base-classes-interfaces/vs-solution-seedwork-classes.png" alt-text="Capture d’écran des classes contenues dans le dossier SeedWork.":::
<span data-ttu-id="836b5-115">Le contenu détaillé du dossier SeedWork, contenant des classes de base et des interfaces : Entity.cs, Enumeration.cs, IAggregateRoot.cs, IRepository.cs, IUnitOfWork.cs et ValueObject.cs.</span><span class="sxs-lookup"><span data-stu-id="836b5-115">The detailed contents of the SeedWork folder, containing base classes and interfaces: Entity.cs, Enumeration.cs, IAggregateRoot.cs, IRepository.cs, IUnitOfWork.cs, and ValueObject.cs.</span></span>
:::image-end:::

<span data-ttu-id="836b5-116">**Figure 7-12**.</span><span class="sxs-lookup"><span data-stu-id="836b5-116">**Figure 7-12**.</span></span> <span data-ttu-id="836b5-117">Exemple d’ensemble de classes de base et d’interfaces « seedwork » de modèle de domaine</span><span class="sxs-lookup"><span data-stu-id="836b5-117">A sample set of domain model “seedwork" base classes and interfaces</span></span>

<span data-ttu-id="836b5-118">Il s’agit du type de réutilisation par copier- coller que de nombreux développeurs partagent entre les projets, et non d’un framework formel.</span><span class="sxs-lookup"><span data-stu-id="836b5-118">This is the type of copy and paste reuse that many developers share between projects, not a formal framework.</span></span> <span data-ttu-id="836b5-119">Vous pouvez avoir des seedworks dans n’importe quelle couche ou bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="836b5-119">You can have seedworks in any layer or library.</span></span> <span data-ttu-id="836b5-120">Cependant, si l’ensemble des classes et des interfaces devient assez grand, vous voudrez peut-être créer une bibliothèque de classe unique.</span><span class="sxs-lookup"><span data-stu-id="836b5-120">However, if the set of classes and interfaces gets large enough, you might want to create a single class library.</span></span>

## <a name="the-custom-entity-base-class"></a><span data-ttu-id="836b5-121">Classe de base Entity personnalisée</span><span class="sxs-lookup"><span data-stu-id="836b5-121">The custom Entity base class</span></span>

<span data-ttu-id="836b5-122">Le code suivant est un exemple de classe de base Entity dans lequel vous pouvez placer du code utilisable de la même façon par une entité de domaine, comme l’ID d’entité, les [opérateurs d’égalité](../../../csharp/language-reference/operators/equality-operators.md), une liste d’événements de domaine par entité, etc.</span><span class="sxs-lookup"><span data-stu-id="836b5-122">The following code is an example of an Entity base class where you can place code that can be used the same way by any domain entity, such as the entity ID, [equality operators](../../../csharp/language-reference/operators/equality-operators.md), a domain event list per entity, etc.</span></span>

```csharp
// COMPATIBLE WITH ENTITY FRAMEWORK CORE (1.1 and later)
public abstract class Entity
{
    int? _requestedHashCode;
    int _Id;
    private List<INotification> _domainEvents;
    public virtual int Id
    {
        get
        {
            return _Id;
        }
        protected set
        {
            _Id = value;
        }
    }

    public List<INotification> DomainEvents => _domainEvents;
    public void AddDomainEvent(INotification eventItem)
    {
        _domainEvents = _domainEvents ?? new List<INotification>();
        _domainEvents.Add(eventItem);
    }
    public void RemoveDomainEvent(INotification eventItem)
    {
        if (_domainEvents is null) return;
        _domainEvents.Remove(eventItem);
    }

    public bool IsTransient()
    {
        return this.Id == default(Int32);
    }

    public override bool Equals(object obj)
    {
        if (obj == null || !(obj is Entity))
            return false;
        if (Object.ReferenceEquals(this, obj))
            return true;
        if (this.GetType() != obj.GetType())
            return false;
        Entity item = (Entity)obj;
        if (item.IsTransient() || this.IsTransient())
            return false;
        else
            return item.Id == this.Id;
    }

    public override int GetHashCode()
    {
        if (!IsTransient())
        {
            if (!_requestedHashCode.HasValue)
                _requestedHashCode = this.Id.GetHashCode() ^ 31;
            // XOR for random distribution. See:
            // https://docs.microsoft.com/archive/blogs/ericlippert/guidelines-and-rules-for-gethashcode
            return _requestedHashCode.Value;
        }
        else
            return base.GetHashCode();
    }
    public static bool operator ==(Entity left, Entity right)
    {
        if (Object.Equals(left, null))
            return (Object.Equals(right, null));
        else
            return left.Equals(right);
    }
    public static bool operator !=(Entity left, Entity right)
    {
        return !(left == right);
    }
}
```

<span data-ttu-id="836b5-123">Le code précédent qui utilise une liste d’événements de domaine par entité est expliqué dans les sections suivantes dédiées aux événements de domaine.</span><span class="sxs-lookup"><span data-stu-id="836b5-123">The previous code using a domain event list per entity will be explained in the next sections when focusing on domain events.</span></span>

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a><span data-ttu-id="836b5-124">Contrats (interfaces) de dépôt dans la couche du modèle de domaine</span><span class="sxs-lookup"><span data-stu-id="836b5-124">Repository contracts (interfaces) in the domain model layer</span></span>

<span data-ttu-id="836b5-125">Les contrats de dépôt sont simplement des interfaces .NET qui expriment les spécifications contractuelles des dépôts à utiliser pour chaque agrégat.</span><span class="sxs-lookup"><span data-stu-id="836b5-125">Repository contracts are simply .NET interfaces that express the contract requirements of the repositories to be used for each aggregate.</span></span>

<span data-ttu-id="836b5-126">Les référentiels eux-mêmes, avec du code EF Core ou avec d’autres dépendances et d’autre code d’infrastructure (LinQ, SQL, etc.), ne doivent pas être implémentés au sein du modèle de domaine : ils doivent implémenter seulement les interfaces que vous définissez dans le modèle de domaine.</span><span class="sxs-lookup"><span data-stu-id="836b5-126">The repositories themselves, with EF Core code or any other infrastructure dependencies and code (Linq, SQL, etc.), must not be implemented within the domain model; the repositories should only implement the interfaces you define in the domain model.</span></span>

<span data-ttu-id="836b5-127">Le modèle lié à cette pratique (placer les interfaces de dépôt dans la couche du modèle de domaine) est le modèle Interface séparée.</span><span class="sxs-lookup"><span data-stu-id="836b5-127">A pattern related to this practice (placing the repository interfaces in the domain model layer) is the Separated Interface pattern.</span></span> <span data-ttu-id="836b5-128">Comme l’[explique](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) Martin Fowler, « utilisez une interface séparée pour définir une interface dans un premier paquet mais l’implémenter dans un autre.</span><span class="sxs-lookup"><span data-stu-id="836b5-128">As [explained](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) by Martin Fowler, “Use Separated Interface to define an interface in one package but implement it in another.</span></span> <span data-ttu-id="836b5-129">De cette manière, un client qui a besoin de la dépendance vis-à-vis de l’interface peut ne pas en connaître du tout l’implémentation ».</span><span class="sxs-lookup"><span data-stu-id="836b5-129">This way a client that needs the dependency to the interface can be completely unaware of the implementation.”</span></span>

<span data-ttu-id="836b5-130">Avec le modèle Interface séparée, la couche Application (dans ce cas, le projet d’API web pour le microservice) comporte une dépendance vis-à-vis des spécifications définies dans le modèle de domaine, mais pas une dépendance directe vis-à-vis de la couche d’infrastructure/de persistance.</span><span class="sxs-lookup"><span data-stu-id="836b5-130">Following the Separated Interface pattern enables the application layer (in this case, the Web API project for the microservice) to have a dependency on the requirements defined in the domain model, but not a direct dependency to the infrastructure/persistence layer.</span></span> <span data-ttu-id="836b5-131">De plus, vous pouvez utiliser l’injection de dépendances pour isoler l’implémentation, qui est implémentée dans la couche d’infrastructure/de persistance à l’aide de dépôts.</span><span class="sxs-lookup"><span data-stu-id="836b5-131">In addition, you can use Dependency Injection to isolate the implementation, which is implemented in the infrastructure/ persistence layer using repositories.</span></span>

<span data-ttu-id="836b5-132">L’exemple suivant avec l’interface IOrderRepository définit les opérations que la classe OrderRepository a besoin d’implémenter au niveau de la couche d’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="836b5-132">For example, the following example with the IOrderRepository interface defines what operations the OrderRepository class will need to implement at the infrastructure layer.</span></span> <span data-ttu-id="836b5-133">Dans l’implémentation actuelle de l’application, le code doit simplement ajouter ou mettre à jour des commandes dans la base de données, étant donné que les requêtes sont fractionnées selon l’approche CQRS simplifiée.</span><span class="sxs-lookup"><span data-stu-id="836b5-133">In the current implementation of the application, the code just needs to add or update orders to the database, since queries are split following the simplified CQRS approach.</span></span>

```csharp
// Defined at IOrderRepository.cs
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);

    void Update(Order order);

    Task<Order> GetAsync(int orderId);
}

// Defined at IRepository.cs (Part of the Domain Seedwork)
public interface IRepository<T> where T : IAggregateRoot
{
    IUnitOfWork UnitOfWork { get; }
}
```

## <a name="additional-resources"></a><span data-ttu-id="836b5-134">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="836b5-134">Additional resources</span></span>

- <span data-ttu-id="836b5-135">**Martin Fowler. Interface séparée.**</span><span class="sxs-lookup"><span data-stu-id="836b5-135">**Martin Fowler. Separated Interface.**</span></span> \
  <https://www.martinfowler.com/eaaCatalog/separatedInterface.html>

>[!div class="step-by-step"]
><span data-ttu-id="836b5-136">[Suivant précédent](net-core-microservice-domain-model.md)
>[Next](implement-value-objects.md)</span><span class="sxs-lookup"><span data-stu-id="836b5-136">[Previous](net-core-microservice-domain-model.md)
[Next](implement-value-objects.md)</span></span>
