---
title: Seedwork (interfaces et classes de base réutilisables pour votre modèle de domaine)
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Utiliser le concept de seedwork comme point de départ pour démarrer l’implémentation d’un modèle de domaine orienté DDD.
ms.date: 10/08/2018
ms.openlocfilehash: 545be2723ba468a5fd65f81978799328234ca113
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988308"
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a>Seedwork (interfaces et classes de base réutilisables pour votre modèle de domaine)

Le dossier solution contient un dossier *SeedWork*. Ce dossier contient des classes de base personnalisées que vous pouvez utiliser comme base pour les entités et les objets de valeur de votre domaine. Utilisez ces classes de base afin de ne pas avoir de code redondant dans la classe d’objets de chaque domaine. Le dossier de ces types de classes s’appelle *SeedWork* et non pas *Framework*. C’est ce qu’on appelle *SeedWork* parce que le dossier ne contient qu’un petit sous-ensemble de classes réutilisables qui ne peuvent pas vraiment être considérés comme un cadre. *Seedwork* est un terme introduit par [Michael Feathers](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) que [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) a rendu populaire, mais vous pouvez également donner à ce dossier le nom Common, SharedKernel ou un autre nom similaire.

La figure 7-12 montre les classes qui constituent le seedwork du modèle de domaine dans le microservice Ordering. Il comporte quelques classes de base personnalisées comme Entity, ValueObject et Enumeration, ainsi que quelques interfaces. Ces interfaces (IRepository et IUnitOfWork) informent la couche d’infrastructure sur ce qui doit être implémenté. Elles sont également utilisées par injection de dépendances à partir de la couche Application.

:::image type="complex" source="./media/seedwork-domain-model-base-classes-interfaces/vs-solution-seedwork-classes.png" alt-text="Capture d’écran des classes contenues dans le dossier SeedWork.":::
Le contenu détaillé du dossier SeedWork, contenant des classes de base et des interfaces : Entity.cs, Enumeration.cs, IAggregateRoot.cs, IRepository.cs, IUnitOfWork.cs et ValueObject.cs.
:::image-end:::

**Figure 7-12**. Un ensemble d’échantillons de modèles de domaine "seedwork" classes de base et des interfaces

Il s’agit du type de réutilisation par copier- coller que de nombreux développeurs partagent entre les projets, et non d’un framework formel. Vous pouvez avoir des seedworks dans n’importe quelle couche ou bibliothèque. Cependant, si l’ensemble des classes et des interfaces devient assez grand, vous voudrez peut-être créer une bibliothèque de classe unique.

## <a name="the-custom-entity-base-class"></a>Classe de base Entity personnalisée

Le code suivant est un exemple de classe de base Entity dans lequel vous pouvez placer du code utilisable de la même façon par une entité de domaine, comme l’ID d’entité, les [opérateurs d’égalité](../../../csharp/language-reference/operators/equality-operators.md), une liste d’événements de domaine par entité, etc.

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

Le code précédent qui utilise une liste d’événements de domaine par entité est expliqué dans les sections suivantes dédiées aux événements de domaine.

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a>Contrats (interfaces) de dépôt dans la couche du modèle de domaine

Les contrats de dépôt sont simplement des interfaces .NET qui expriment les spécifications contractuelles des dépôts à utiliser pour chaque agrégat.

Les référentiels eux-mêmes, avec du code EF Core ou avec d’autres dépendances et d’autre code d’infrastructure (LinQ, SQL, etc.), ne doivent pas être implémentés au sein du modèle de domaine : ils doivent implémenter seulement les interfaces que vous définissez dans le modèle de domaine.

Le modèle lié à cette pratique (placer les interfaces de dépôt dans la couche du modèle de domaine) est le modèle Interface séparée. Comme [l’explique](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) Martin Fowler, « Utilisez l’interface séparée pour définir une interface dans un paquet, mais implémentez-la dans un autre. De cette façon, un client qui a besoin de la dépendance à l’interface peut être complètement inconscient de la mise en œuvre.

Avec le modèle Interface séparée, la couche Application (dans ce cas, le projet d’API web pour le microservice) comporte une dépendance vis-à-vis des spécifications définies dans le modèle de domaine, mais pas une dépendance directe vis-à-vis de la couche d’infrastructure/de persistance. De plus, vous pouvez utiliser l’injection de dépendances pour isoler l’implémentation, qui est implémentée dans la couche d’infrastructure/de persistance à l’aide de dépôts.

L’exemple suivant avec l’interface IOrderRepository définit les opérations que la classe OrderRepository a besoin d’implémenter au niveau de la couche d’infrastructure. Dans l’implémentation actuelle de l’application, le code doit simplement ajouter ou mettre à jour des commandes dans la base de données, étant donné que les requêtes sont fractionnées selon l’approche CQRS simplifiée.

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

## <a name="additional-resources"></a>Ressources supplémentaires

- **Martin Fowler. Interface séparée.** \
  <https://www.martinfowler.com/eaaCatalog/separatedInterface.html>

>[!div class="step-by-step"]
>[Suivant précédent](net-core-microservice-domain-model.md)
>[Next](implement-value-objects.md)
