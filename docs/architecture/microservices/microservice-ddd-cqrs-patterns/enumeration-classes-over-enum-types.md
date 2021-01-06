---
title: Utilisation de classes d’énumération plutôt que de types enum
description: Architecture de microservices .NET pour les applications .NET conteneurisées | Découvrez comment utiliser des classes d’énumération pour contourner certaines limitations des types enum.
ms.date: 11/25/2020
ms.openlocfilehash: a45347d7cc9c3fc6378198ca1c44ba6fecfd54f5
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97899526"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a>Utiliser des classes d’énumération à la place de types enum

Les [énumérations](../../../csharp/language-reference/builtin-types/enum.md) (ou *types enum* en abrégé) constituent un wrapper de langage simple autour d’un type intégral. Vous souhaiterez peut-être limiter leur utilisation au stockage d’une valeur d’un ensemble fermé de valeurs. La classification basée sur les tailles (petite, moyenne, grande) est un bon exemple. L’utilisation d’enums pour le flux de contrôle ou d’abstractions plus puissantes peut être un [code smell](https://deviq.com/antipatterns/code-smells). Ce type d’utilisation a pour effet de fragiliser le code avec de nombreuses instructions de flux de contrôle qui vérifient les valeurs de l’enum.

À la place, vous pouvez créer des classes d’énumération qui activent toutes les fonctionnalités avancées d’un langage orienté objet.

Toutefois, ce n’est pas un sujet très important et, dans de nombreux cas, vous pouvez toujours simplifier en utilisant des [types enum](../../../csharp/language-reference/builtin-types/enum.md) standard, si vous préférez. L’utilisation de classes d’énumération est plus liée aux concepts liés à l’entreprise.

## <a name="implement-an-enumeration-base-class"></a>Implémenter une classe d’énumération de base

Le microservice Ordering (Commandes) dans eShopOnContainers fournit un exemple d’implémentation de classe d’énumération de base, comme illustré dans l’exemple suivant :

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; private set; }

    public int Id { get; private set; }

    protected Enumeration(int id, string name) => (Id, Name) = (id, name);

    public override string ToString() => Name;

    public static IEnumerable<T> GetAll<T>() where T : Enumeration =>
        typeof(T).GetFields(BindingFlags.Public |
                            BindingFlags.Static |
                            BindingFlags.DeclaredOnly)
                 .Select(f => f.GetValue(null))
                 .Cast<T>();

    public override bool Equals(object obj)
    {
        if (obj is not Enumeration otherValue)
        {
            return false;
        }

        var typeMatches = GetType().Equals(obj.GetType());
        var valueMatches = Id.Equals(otherValue.Id);

        return typeMatches && valueMatches;
    }

    public int CompareTo(object other) => Id.CompareTo(((Enumeration)other).Id);

    // Other utility methods ...
}
```

Vous pouvez utiliser cette classe comme type dans n’importe quel objet entité ou valeur, comme pour la classe `CardType` : `Enumeration` suivante :

```csharp
public class CardType
    : Enumeration
{
    public static CardType Amex = new CardType(1, nameof(Amex));
    public static CardType Visa = new CardType(2, nameof(Visa));
    public static CardType MasterCard = new CardType(3, nameof(MasterCard));

    public CardType(int id, string name)
        : base(id, name)
    {
    }
}
```

## <a name="additional-resources"></a>Ressources supplémentaires

- **Jimmy bogard. Classes d’énumération** \
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- **Steve Smith. Énumérer les alternatives en C #** \
  <https://ardalis.com/enum-alternatives-in-c>

- **Enumeration.cs.** Classe d’énumération de base dans eShopOnContainers \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- **CardType.cs**. Exemple de classe d’énumération dans eShopOnContainers. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>

- **SmartEnum**. Ardalis - Cours pour apprendre à créer des enums fortement typés plus intelligents dans .NET. \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
>[Précédent](implement-value-objects.md) 
> [Suivant](domain-model-layer-validations.md)
