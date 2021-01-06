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
# <a name="use-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="74f0d-103">Utiliser des classes d’énumération à la place de types enum</span><span class="sxs-lookup"><span data-stu-id="74f0d-103">Use enumeration classes instead of enum types</span></span>

<span data-ttu-id="74f0d-104">Les [énumérations](../../../csharp/language-reference/builtin-types/enum.md) (ou *types enum* en abrégé) constituent un wrapper de langage simple autour d’un type intégral.</span><span class="sxs-lookup"><span data-stu-id="74f0d-104">[Enumerations](../../../csharp/language-reference/builtin-types/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="74f0d-105">Vous souhaiterez peut-être limiter leur utilisation au stockage d’une valeur d’un ensemble fermé de valeurs.</span><span class="sxs-lookup"><span data-stu-id="74f0d-105">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="74f0d-106">La classification basée sur les tailles (petite, moyenne, grande) est un bon exemple.</span><span class="sxs-lookup"><span data-stu-id="74f0d-106">Classification based on sizes (small, medium, large) is a good example.</span></span> <span data-ttu-id="74f0d-107">L’utilisation d’enums pour le flux de contrôle ou d’abstractions plus puissantes peut être un [code smell](https://deviq.com/antipatterns/code-smells).</span><span class="sxs-lookup"><span data-stu-id="74f0d-107">Using enums for control flow or more robust abstractions can be a [code smell](https://deviq.com/antipatterns/code-smells).</span></span> <span data-ttu-id="74f0d-108">Ce type d’utilisation a pour effet de fragiliser le code avec de nombreuses instructions de flux de contrôle qui vérifient les valeurs de l’enum.</span><span class="sxs-lookup"><span data-stu-id="74f0d-108">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="74f0d-109">À la place, vous pouvez créer des classes d’énumération qui activent toutes les fonctionnalités avancées d’un langage orienté objet.</span><span class="sxs-lookup"><span data-stu-id="74f0d-109">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="74f0d-110">Toutefois, ce n’est pas un sujet très important et, dans de nombreux cas, vous pouvez toujours simplifier en utilisant des [types enum](../../../csharp/language-reference/builtin-types/enum.md) standard, si vous préférez.</span><span class="sxs-lookup"><span data-stu-id="74f0d-110">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../csharp/language-reference/builtin-types/enum.md) if that's your preference.</span></span> <span data-ttu-id="74f0d-111">L’utilisation de classes d’énumération est plus liée aux concepts liés à l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="74f0d-111">The use of enumeration classes is more related to business-related concepts.</span></span>

## <a name="implement-an-enumeration-base-class"></a><span data-ttu-id="74f0d-112">Implémenter une classe d’énumération de base</span><span class="sxs-lookup"><span data-stu-id="74f0d-112">Implement an Enumeration base class</span></span>

<span data-ttu-id="74f0d-113">Le microservice Ordering (Commandes) dans eShopOnContainers fournit un exemple d’implémentation de classe d’énumération de base, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="74f0d-113">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

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

<span data-ttu-id="74f0d-114">Vous pouvez utiliser cette classe comme type dans n’importe quel objet entité ou valeur, comme pour la classe `CardType` : `Enumeration` suivante :</span><span class="sxs-lookup"><span data-stu-id="74f0d-114">You can use this class as a type in any entity or value object, as for the following `CardType` : `Enumeration` class:</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="74f0d-115">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="74f0d-115">Additional resources</span></span>

- <span data-ttu-id="74f0d-116">**Jimmy bogard. Classes d’énumération** </span><span class="sxs-lookup"><span data-stu-id="74f0d-116">**Jimmy Bogard. Enumeration classes** </span></span>\
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- <span data-ttu-id="74f0d-117">**Steve Smith. Énumérer les alternatives en C #** </span><span class="sxs-lookup"><span data-stu-id="74f0d-117">**Steve Smith. Enum Alternatives in C#** </span></span>\
  <https://ardalis.com/enum-alternatives-in-c>

- <span data-ttu-id="74f0d-118">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="74f0d-118">**Enumeration.cs.**</span></span> <span data-ttu-id="74f0d-119">Classe d’énumération de base dans eShopOnContainers </span><span class="sxs-lookup"><span data-stu-id="74f0d-119">Base Enumeration class in eShopOnContainers </span></span>\
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- <span data-ttu-id="74f0d-120">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="74f0d-120">**CardType.cs**.</span></span> <span data-ttu-id="74f0d-121">Exemple de classe d’énumération dans eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="74f0d-121">Sample Enumeration class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>

- <span data-ttu-id="74f0d-122">**SmartEnum**.</span><span class="sxs-lookup"><span data-stu-id="74f0d-122">**SmartEnum**.</span></span> <span data-ttu-id="74f0d-123">Ardalis - Cours pour apprendre à créer des enums fortement typés plus intelligents dans .NET.</span><span class="sxs-lookup"><span data-stu-id="74f0d-123">Ardalis - Classes to help produce strongly typed smarter enums in .NET.</span></span> \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
><span data-ttu-id="74f0d-124">[Précédent](implement-value-objects.md) 
> [Suivant](domain-model-layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="74f0d-124">[Previous](implement-value-objects.md)
[Next](domain-model-layer-validations.md)</span></span>
