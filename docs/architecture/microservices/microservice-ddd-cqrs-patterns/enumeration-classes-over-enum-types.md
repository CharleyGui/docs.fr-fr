---
title: Utilisation de classes d’énumération plutôt que de types enum
description: Architecture de microservices .NET pour les applications .NET conteneurisées | Découvrez comment utiliser des classes d’énumération pour contourner certaines limitations des types enum.
ms.date: 10/08/2018
ms.openlocfilehash: 6752adb28b1bd0982c66fa2d021b04b999447c6e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337678"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="763d2-103">Utiliser des classes d’énumération à la place de types enum</span><span class="sxs-lookup"><span data-stu-id="763d2-103">Use enumeration classes instead of enum types</span></span>

<span data-ttu-id="763d2-104">Les [énumérations](../../../csharp/language-reference/builtin-types/enum.md) (ou *types enum* en abrégé) constituent un wrapper de langage simple autour d’un type intégral.</span><span class="sxs-lookup"><span data-stu-id="763d2-104">[Enumerations](../../../csharp/language-reference/builtin-types/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="763d2-105">Vous souhaiterez peut-être limiter leur utilisation au stockage d’une valeur d’un ensemble fermé de valeurs.</span><span class="sxs-lookup"><span data-stu-id="763d2-105">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="763d2-106">La classification basée sur les tailles (petite, moyenne, grande) est un bon exemple.</span><span class="sxs-lookup"><span data-stu-id="763d2-106">Classification based on sizes (small, medium, large) is a good example.</span></span> <span data-ttu-id="763d2-107">L’utilisation d’enums pour le flux de contrôle ou d’abstractions plus puissantes peut être un [code smell](https://deviq.com/code-smells/).</span><span class="sxs-lookup"><span data-stu-id="763d2-107">Using enums for control flow or more robust abstractions can be a [code smell](https://deviq.com/code-smells/).</span></span> <span data-ttu-id="763d2-108">Ce type d’utilisation a pour effet de fragiliser le code avec de nombreuses instructions de flux de contrôle qui vérifient les valeurs de l’enum.</span><span class="sxs-lookup"><span data-stu-id="763d2-108">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="763d2-109">À la place, vous pouvez créer des classes d’énumération qui activent toutes les fonctionnalités avancées d’un langage orienté objet.</span><span class="sxs-lookup"><span data-stu-id="763d2-109">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="763d2-110">Toutefois, ce n’est pas un sujet très important et, dans de nombreux cas, vous pouvez toujours simplifier en utilisant des [types enum](../../../csharp/language-reference/builtin-types/enum.md) standard, si vous préférez.</span><span class="sxs-lookup"><span data-stu-id="763d2-110">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../csharp/language-reference/builtin-types/enum.md) if that's your preference.</span></span> <span data-ttu-id="763d2-111">En fait, l’utilisation des classes d’énumération est davantage liée à des concepts métier.</span><span class="sxs-lookup"><span data-stu-id="763d2-111">Anyway, the use of enumeration classes is more related to business-related concepts.</span></span>

## <a name="implement-an-enumeration-base-class"></a><span data-ttu-id="763d2-112">Implémenter une classe d’énumération de base</span><span class="sxs-lookup"><span data-stu-id="763d2-112">Implement an Enumeration base class</span></span>

<span data-ttu-id="763d2-113">Le microservice Ordering (Commandes) dans eShopOnContainers fournit un exemple d’implémentation de classe d’énumération de base, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="763d2-113">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; private set; }

    public int Id { get; private set; }

    protected Enumeration(int id, string name)
    {
        Id = id;
        Name = name;
    }

    public override string ToString() => Name;

    public static IEnumerable<T> GetAll<T>() where T : Enumeration
    {
        var fields = typeof(T).GetFields(BindingFlags.Public |
                                         BindingFlags.Static |
                                         BindingFlags.DeclaredOnly);

        return fields.Select(f => f.GetValue(null)).Cast<T>();
    }

    public override bool Equals(object obj)
    {
        var otherValue = obj as Enumeration;

        if (otherValue == null)
            return false;

        var typeMatches = GetType().Equals(obj.GetType());
        var valueMatches = Id.Equals(otherValue.Id);

        return typeMatches && valueMatches;
    }

    public int CompareTo(object other) => Id.CompareTo(((Enumeration)other).Id);

    // Other utility methods ...
}
```

<span data-ttu-id="763d2-114">Vous pouvez utiliser cette classe comme type dans n’importe quel objet entité ou valeur, comme pour la classe `CardType` : `Enumeration` suivante :</span><span class="sxs-lookup"><span data-stu-id="763d2-114">You can use this class as a type in any entity or value object, as for the following `CardType` : `Enumeration` class:</span></span>

```csharp
public class CardType : Enumeration
{
    public static CardType Amex = new CardType(1, "Amex");
    public static CardType Visa = new CardType(2, "Visa");
    public static CardType MasterCard = new CardType(3, "MasterCard");

    public CardType(int id, string name)
        : base(id, name)
    {
    }
}
```

## <a name="additional-resources"></a><span data-ttu-id="763d2-115">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="763d2-115">Additional resources</span></span>

- <span data-ttu-id="763d2-116">**Enum’s are evil—update** </span><span class="sxs-lookup"><span data-stu-id="763d2-116">**Enum’s are evil—update** </span></span>\
  <https://www.planetgeek.ch/2009/07/01/enums-are-evil/>

- <span data-ttu-id="763d2-117">**Daniel dur. Comment les énumérations sont réparties sur les maladies, et comment les y remédier** </span><span class="sxs-lookup"><span data-stu-id="763d2-117">**Daniel Hardman. How Enums Spread Disease — And How To Cure It** </span></span>\
  <https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/>

- <span data-ttu-id="763d2-118">**Jimmy bogard. Classes d’énumération** </span><span class="sxs-lookup"><span data-stu-id="763d2-118">**Jimmy Bogard. Enumeration classes** </span></span>\
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- <span data-ttu-id="763d2-119">**Steve Smith. Énumérer les C# alternatives dans** </span><span class="sxs-lookup"><span data-stu-id="763d2-119">**Steve Smith. Enum Alternatives in C#** </span></span>\
  <https://ardalis.com/enum-alternatives-in-c>

- <span data-ttu-id="763d2-120">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="763d2-120">**Enumeration.cs.**</span></span> <span data-ttu-id="763d2-121">Classe d’énumération de base dans eShopOnContainers </span><span class="sxs-lookup"><span data-stu-id="763d2-121">Base Enumeration class in eShopOnContainers </span></span>\
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- <span data-ttu-id="763d2-122">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="763d2-122">**CardType.cs**.</span></span> <span data-ttu-id="763d2-123">Exemple de classe d’énumération dans eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="763d2-123">Sample Enumeration class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>

- <span data-ttu-id="763d2-124">**SmartEnum**.</span><span class="sxs-lookup"><span data-stu-id="763d2-124">**SmartEnum**.</span></span> <span data-ttu-id="763d2-125">Ardalis - Cours pour apprendre à créer des enums fortement typés plus intelligents dans .NET.</span><span class="sxs-lookup"><span data-stu-id="763d2-125">Ardalis - Classes to help produce strongly typed smarter enums in .NET.</span></span> \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
><span data-ttu-id="763d2-126">[Précédent](implement-value-objects.md)
>[Suivant](domain-model-layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="763d2-126">[Previous](implement-value-objects.md)
[Next](domain-model-layer-validations.md)</span></span>
