---
title: Vue d’ensemble de LINQ-.NET
description: Language-Integrated query (LINQ) fournit des fonctions d’interrogation au niveau du langage et une API de fonction d’ordre supérieur pour C# et Visual Basic, qui vous permettent d’écrire du code déclaratif expressif.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
dev_langs:
- csharp
- vb
ms.openlocfilehash: ed78082c97511a8dbcc48d413a75a46c9da906a9
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825830"
---
# <a name="linq-overview"></a><span data-ttu-id="0fc0c-103">Vue d’ensemble de LINQ</span><span class="sxs-lookup"><span data-stu-id="0fc0c-103">LINQ overview</span></span>

<span data-ttu-id="0fc0c-104">Language-Integrated query (LINQ) fournit des fonctions d’interrogation au niveau du langage et une API de [fonction d’ordre supérieur](https://en.wikipedia.org/wiki/Higher-order_function) pour C# et Visual Basic, qui vous permettent d’écrire du code déclaratif expressif.</span><span class="sxs-lookup"><span data-stu-id="0fc0c-104">Language-Integrated Query (LINQ) provides language-level querying capabilities, and a [higher-order function](https://en.wikipedia.org/wiki/Higher-order_function) API to C# and Visual Basic, that enable you to write expressive declarative code.</span></span>

## <a name="language-level-query-syntax"></a><span data-ttu-id="0fc0c-105">Syntaxe de requête au niveau du langage</span><span class="sxs-lookup"><span data-stu-id="0fc0c-105">Language-level query syntax</span></span>

<span data-ttu-id="0fc0c-106">Voici la syntaxe de requête au niveau du langage :</span><span class="sxs-lookup"><span data-stu-id="0fc0c-106">This is the language-level query syntax:</span></span>

```csharp
var linqExperts = from p in programmers
                  where p.IsNewToLINQ
                  select new LINQExpert(p);
```

```vb
Dim linqExperts = From p in programmers
                  Where p.IsNewToLINQ
                  Select New LINQExpert(p)
```

<span data-ttu-id="0fc0c-107">Voici le même exemple d’utilisation de l' `IEnumerable<T>` API :</span><span class="sxs-lookup"><span data-stu-id="0fc0c-107">This is the same example using the `IEnumerable<T>` API:</span></span>

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

```vb
Dim linqExperts = programmers.Where(Function(p) p.IsNewToLINQ).
                             Select(Function(p) New LINQExpert(p))
```

## <a name="linq-is-expressive"></a><span data-ttu-id="0fc0c-108">LINQ est expressif</span><span class="sxs-lookup"><span data-stu-id="0fc0c-108">LINQ is expressive</span></span>

<span data-ttu-id="0fc0c-109">Imaginez que vous avez une liste d’animaux domestiques, mais que vous voulez la convertir en dictionnaire dans lequel vous pouvez accéder à un animal directement par sa valeur `RFID`.</span><span class="sxs-lookup"><span data-stu-id="0fc0c-109">Imagine you have a list of pets, but want to convert it into a dictionary where you can access a pet directly by its `RFID` value.</span></span>

<span data-ttu-id="0fc0c-110">Il s’agit du code impératif traditionnel :</span><span class="sxs-lookup"><span data-stu-id="0fc0c-110">This is traditional imperative code:</span></span>

```csharp
var petLookup = new Dictionary<int, Pet>();

foreach (var pet in pets)
{
    petLookup.Add(pet.RFID, pet);
}
```

```vb
Dim petLookup = New Dictionary(Of Integer, Pet)()

For Each pet in pets
    petLookup.Add(pet.RFID, pet)
Next
```

<span data-ttu-id="0fc0c-111">L’objectif derrière le code n’est pas de créer un nouveau `Dictionary<int, Pet>` et de l’ajouter à l’aide d’une boucle. il consiste à convertir une liste existante en dictionnaire !</span><span class="sxs-lookup"><span data-stu-id="0fc0c-111">The intention behind the code isn't to create a new `Dictionary<int, Pet>` and add to it via a loop, it's to convert an existing list into a dictionary!</span></span> <span data-ttu-id="0fc0c-112">LINQ conserve l’intention, contrairement au code impératif.</span><span class="sxs-lookup"><span data-stu-id="0fc0c-112">LINQ preserves the intention whereas the imperative code doesn't.</span></span>

<span data-ttu-id="0fc0c-113">Il s’agit de l’expression LINQ équivalente :</span><span class="sxs-lookup"><span data-stu-id="0fc0c-113">This is the equivalent LINQ expression:</span></span>

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

```vb
Dim petLookup = pets.ToDictionary(Function(pet) pet.RFID)
```

<span data-ttu-id="0fc0c-114">Le code qui utilise LINQ est utile, car il égalise le terrain entre l’intention et le code dans un contexte de programmation.</span><span class="sxs-lookup"><span data-stu-id="0fc0c-114">The code using LINQ is valuable because it evens the playing field between intent and code when reasoning as a programmer.</span></span> <span data-ttu-id="0fc0c-115">Un autre bonus est la concision du code.</span><span class="sxs-lookup"><span data-stu-id="0fc0c-115">Another bonus is code brevity.</span></span> <span data-ttu-id="0fc0c-116">Imaginez que vous pouvez réduire d’un tiers les grandes parties d’un code Base comme illustré ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="0fc0c-116">Imagine reducing large portions of a codebase by 1/3 as done above.</span></span> <span data-ttu-id="0fc0c-117">Bonne affaire, n’est-ce pas ?</span><span class="sxs-lookup"><span data-stu-id="0fc0c-117">Sweet deal, right?</span></span>

## <a name="linq-providers-simplify-data-access"></a><span data-ttu-id="0fc0c-118">Les fournisseurs LINQ simplifient l’accès aux données</span><span class="sxs-lookup"><span data-stu-id="0fc0c-118">LINQ providers simplify data access</span></span>

<span data-ttu-id="0fc0c-119">Pour un grand nombre de logiciels en nature, tout tourne autour du traitement des données provenant d’une source (bases de données, JSON, XML, etc.).</span><span class="sxs-lookup"><span data-stu-id="0fc0c-119">For a significant chunk of software out in the wild, everything revolves around dealing with data from some source (Databases, JSON, XML, and so on).</span></span> <span data-ttu-id="0fc0c-120">Cela implique souvent d’apprendre une nouvelle API par source de données, ce qui peut s’avérer fastidieux.</span><span class="sxs-lookup"><span data-stu-id="0fc0c-120">Often this involves learning a new API for each data source, which can be annoying.</span></span> <span data-ttu-id="0fc0c-121">LINQ simplifie cela en faisant abstraction des éléments communs de l’accès aux données dans une syntaxe de requête qui se présente de la même façon, quelle que soit la source de données que vous choisissez.</span><span class="sxs-lookup"><span data-stu-id="0fc0c-121">LINQ simplifies this by abstracting common elements of data access into a query syntax that looks the same no matter which data source you pick.</span></span>

<span data-ttu-id="0fc0c-122">Cela recherche tous les éléments XML avec une valeur d’attribut spécifique :</span><span class="sxs-lookup"><span data-stu-id="0fc0c-122">This finds all XML elements with a specific attribute value:</span></span>

```csharp
public static IEnumerable<XElement> FindAllElementsWithAttribute(XElement documentRoot, string elementName,
                                           string attributeName, string value)
{
    return from el in documentRoot.Elements(elementName)
           where (string)el.Element(attributeName) == value
           select el;
}
```

```vb
Public Shared Function FindAllElementsWithAttribute(documentRoot As XElement, elementName As String,
                                           attributeName As String, value As String) As IEnumerable(Of XElement)
    Return From el In documentRoot.Elements(elementName)
           Where el.Element(attributeName).ToString() = value
           Select el
End Function
```

<span data-ttu-id="0fc0c-123">L’écriture de code pour parcourir manuellement le document XML pour effectuer cette tâche serait beaucoup plus complexe.</span><span class="sxs-lookup"><span data-stu-id="0fc0c-123">Writing code to manually traverse the XML document to do this task would be far more challenging.</span></span>

<span data-ttu-id="0fc0c-124">L’interaction avec XML n’est pas la seule chose que vous pouvez faire avec les fournisseurs LINQ.</span><span class="sxs-lookup"><span data-stu-id="0fc0c-124">Interacting with XML isn't the only thing you can do with LINQ Providers.</span></span> <span data-ttu-id="0fc0c-125">[LINQ to SQL](../../framework/data/adonet/sql/linq/index.md) est un mappeur ORM (Object-Relational Mapper) de base de données MSSQL relativement minimaliste.</span><span class="sxs-lookup"><span data-stu-id="0fc0c-125">[Linq to SQL](../../framework/data/adonet/sql/linq/index.md) is a fairly bare-bones Object-Relational Mapper (ORM) for an MSSQL Server Database.</span></span> <span data-ttu-id="0fc0c-126">La bibliothèque [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) fournit un balayage efficace du document JSON via LINQ.</span><span class="sxs-lookup"><span data-stu-id="0fc0c-126">The [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) library provides efficient JSON Document traversal via LINQ.</span></span> <span data-ttu-id="0fc0c-127">En outre, si aucune bibliothèque ne fait ce dont vous avez besoin, vous pouvez également [écrire votre propre fournisseur LINQ](/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))!</span><span class="sxs-lookup"><span data-stu-id="0fc0c-127">Furthermore, if there isn't a library that does what you need, you can also [write your own LINQ Provider](/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))!</span></span>

## <a name="reasons-to-use-the-query-syntax"></a><span data-ttu-id="0fc0c-128">Raisons d’utiliser la syntaxe de requête</span><span class="sxs-lookup"><span data-stu-id="0fc0c-128">Reasons to use the query syntax</span></span>

<span data-ttu-id="0fc0c-129">Pourquoi utiliser la syntaxe de requête ?</span><span class="sxs-lookup"><span data-stu-id="0fc0c-129">Why use query syntax?</span></span> <span data-ttu-id="0fc0c-130">Il s’agit d’une question qui se pose souvent.</span><span class="sxs-lookup"><span data-stu-id="0fc0c-130">This is a question that often comes up.</span></span> <span data-ttu-id="0fc0c-131">Après tout, le code suivant :</span><span class="sxs-lookup"><span data-stu-id="0fc0c-131">After all, the following code:</span></span>

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

```vb
Dim filteredItems = myItems.Where(Function(item) item.Foo)
```

<span data-ttu-id="0fc0c-132">est beaucoup plus concis que ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="0fc0c-132">is a lot more concise than this:</span></span>

```csharp
var filteredItems = from item in myItems
                    where item.Foo
                    select item;
```

```vb
Dim filteredItems = From item In myItems
                    Where item.Foo
                    Select item
```

<span data-ttu-id="0fc0c-133">La syntaxe d’API n’est-elle pas seulement un moyen plus concis d’effectuer la syntaxe de requête ?</span><span class="sxs-lookup"><span data-stu-id="0fc0c-133">Isn't the API syntax just a more concise way to do the query syntax?</span></span>

<span data-ttu-id="0fc0c-134">Non.</span><span class="sxs-lookup"><span data-stu-id="0fc0c-134">No.</span></span> <span data-ttu-id="0fc0c-135">La syntaxe de requête permet d’utiliser la clause **let**, ce qui vous permet d’introduire et de lier une variable dans la portée de l’expression, en l’utilisant dans les parties suivantes de l’expression.</span><span class="sxs-lookup"><span data-stu-id="0fc0c-135">The query syntax allows for the use of the **let** clause, which allows you to introduce and bind a variable within the scope of the expression, using it in subsequent pieces of the expression.</span></span> <span data-ttu-id="0fc0c-136">Il est possible de reproduire le même code avec la syntaxe d’API uniquement, mais cela entraînera très probablement du code difficile à lire.</span><span class="sxs-lookup"><span data-stu-id="0fc0c-136">Reproducing the same code with only the API syntax can be done, but will most likely lead to code that's hard to read.</span></span>

<span data-ttu-id="0fc0c-137">Ce qui nous amène à la question suivante : **devez-vous vous contenter d’utiliser la syntaxe de requête ?**</span><span class="sxs-lookup"><span data-stu-id="0fc0c-137">So this begs the question, **should you just use the query syntax?**</span></span>

<span data-ttu-id="0fc0c-138">La réponse à cette question est **Oui** dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="0fc0c-138">The answer to this question is **yes** if:</span></span>

- <span data-ttu-id="0fc0c-139">Votre code base existant utilise déjà la syntaxe de requête.</span><span class="sxs-lookup"><span data-stu-id="0fc0c-139">Your existing codebase already uses the query syntax.</span></span>
- <span data-ttu-id="0fc0c-140">Vous devez étendre les variables dans vos requêtes en raison de la complexité.</span><span class="sxs-lookup"><span data-stu-id="0fc0c-140">You need to scope variables within your queries because of complexity.</span></span>
- <span data-ttu-id="0fc0c-141">Vous préférez la syntaxe de requête et celle-ci ne gêne pas votre code base.</span><span class="sxs-lookup"><span data-stu-id="0fc0c-141">You prefer the query syntax and it won't distract from your codebase.</span></span>

<span data-ttu-id="0fc0c-142">La réponse à cette question est **non**, si...</span><span class="sxs-lookup"><span data-stu-id="0fc0c-142">The answer to this question is **no** if...</span></span>

- <span data-ttu-id="0fc0c-143">Votre code Base utilise déjà la syntaxe d’API</span><span class="sxs-lookup"><span data-stu-id="0fc0c-143">Your existing codebase already uses the API syntax</span></span>
- <span data-ttu-id="0fc0c-144">Vous n’avez pas besoin de définir l’étendue des variables dans vos requêtes</span><span class="sxs-lookup"><span data-stu-id="0fc0c-144">You have no need to scope variables within your queries</span></span>
- <span data-ttu-id="0fc0c-145">Vous préférez la syntaxe d’API et cela ne gêne pas votre code base</span><span class="sxs-lookup"><span data-stu-id="0fc0c-145">You prefer the API syntax and it won't distract from your codebase</span></span>

## <a name="essential-linq"></a><span data-ttu-id="0fc0c-146">LINQ essentiel</span><span class="sxs-lookup"><span data-stu-id="0fc0c-146">Essential LINQ</span></span>

<span data-ttu-id="0fc0c-147">Pour obtenir la liste complète des exemples LINQ, consultez [101 LINQ Samples](/samples/dotnet/try-samples/101-linq-samples/) (101 exemples LINQ).</span><span class="sxs-lookup"><span data-stu-id="0fc0c-147">For a truly comprehensive list of LINQ samples, visit [101 LINQ Samples](/samples/dotnet/try-samples/101-linq-samples/).</span></span>

<span data-ttu-id="0fc0c-148">Les exemples suivants sont une démonstration rapide de quelques-uns des éléments essentiels de LINQ.</span><span class="sxs-lookup"><span data-stu-id="0fc0c-148">The following examples are a quick demonstration of some of the essential pieces of LINQ.</span></span> <span data-ttu-id="0fc0c-149">Cette approche n’est pas exhaustive, car LINQ fournit plus de fonctionnalités que ce qui est présenté ici.</span><span class="sxs-lookup"><span data-stu-id="0fc0c-149">This is in no way comprehensive, as LINQ provides more functionality than what is showcased here.</span></span>

### <a name="the-bread-and-butter---where-select-and-aggregate"></a><span data-ttu-id="0fc0c-150">Le pain et le beurre- `Where` , `Select` et `Aggregate`</span><span class="sxs-lookup"><span data-stu-id="0fc0c-150">The bread and butter - `Where`, `Select`, and `Aggregate`</span></span>

```csharp
// Filtering a list.
var germanShepherds = dogs.Where(dog => dog.Breed == DogBreed.GermanShepherd);

// Using the query syntax.
var queryGermanShepherds = from dog in dogs
                          where dog.Breed == DogBreed.GermanShepherd
                          select dog;

// Mapping a list from type A to type B.
var cats = dogs.Select(dog => dog.TurnIntoACat());

// Using the query syntax.
var queryCats = from dog in dogs
                select dog.TurnIntoACat();

// Summing the lengths of a set of strings.
int seed = 0;
int sumOfStrings = strings.Aggregate(seed, (s1, s2) => s1.Length + s2.Length);
```

```vb
' Filtering a list.
Dim germanShepherds = dogs.Where(Function(dog) dog.Breed = DogBreed.GermanShepherd)

' Using the query syntax.
Dim queryGermanShepherds = From dog In dogs
                          Where dog.Breed = DogBreed.GermanShepherd
                          Select dog

' Mapping a list from type A to type B.
Dim cats = dogs.Select(Function(dog) dog.TurnIntoACat())

' Using the query syntax.
Dim queryCats = From dog In dogs
                Select dog.TurnIntoACat()

' Summing the lengths of a set of strings.
Dim seed As Integer = 0
Dim sumOfStrings As Integer = strings.Aggregate(seed, Function(s1, s2) s1.Length + s2.Length)
```

### <a name="flattening-a-list-of-lists"></a><span data-ttu-id="0fc0c-151">Aplatissement d’une liste de listes</span><span class="sxs-lookup"><span data-stu-id="0fc0c-151">Flattening a list of lists</span></span>

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

```vb
' Transforms the list of kennels into a list of all their dogs.
Dim allDogsFromKennels = kennels.SelectMany(Function(kennel) kennel.Dogs)
```

### <a name="union-between-two-sets-with-custom-comparator"></a><span data-ttu-id="0fc0c-152">Union entre deux ensembles (avec un comparateur personnalisé)</span><span class="sxs-lookup"><span data-stu-id="0fc0c-152">Union between two sets (with custom comparator)</span></span>

```csharp
public class DogHairLengthComparer : IEqualityComparer<Dog>
{
    public bool Equals(Dog a, Dog b)
    {
        if (a == null && b == null)
        {
            return true;
        }
        else if ((a == null && b != null) ||
                 (a != null && b == null))
        {
            return false;
        }
        else
        {
            return a.HairLengthType == b.HairLengthType;
        }
    }

    public int GetHashCode(Dog d)
    {
        // Default hashcode is enough here, as these are simple objects.
        return d.GetHashCode();
    }
}
...

// Gets all the short-haired dogs between two different kennels.
var allShortHairedDogs = kennel1.Dogs.Union(kennel2.Dogs, new DogHairLengthComparer());

```

```vb
Public Class DogHairLengthComparer
  Inherits IEqualityComparer(Of Dog)

  Public Function Equals(a As Dog,b As Dog) As Boolean
      If a Is Nothing AndAlso b Is Nothing Then
          Return True
      ElseIf (a Is Nothing AndAlso b IsNot Nothing) OrElse (a IsNot Nothing AndAlso b Is Nothing) Then
          Return False
      Else
          Return a.HairLengthType = b.HairLengthType
      End If
  End Function

  Public Function GetHashCode(d As Dog) As Integer
      ' Default hashcode is enough here, as these are simple objects.
      Return d.GetHashCode()
  End Function
End Class

...

' Gets all the short-haired dogs between two different kennels.
Dim allShortHairedDogs = kennel1.Dogs.Union(kennel2.Dogs, New DogHairLengthComparer())
```

### <a name="intersection-between-two-sets"></a><span data-ttu-id="0fc0c-153">Intersection entre deux jeux</span><span class="sxs-lookup"><span data-stu-id="0fc0c-153">Intersection between two sets</span></span>

```csharp
// Gets the volunteers who spend share time with two humane societies.
var volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     new VolunteerTimeComparer());
```

```vb
' Gets the volunteers who spend share time with two humane societies.
Dim volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     New VolunteerTimeComparer())
```

### <a name="ordering"></a><span data-ttu-id="0fc0c-154">Classement</span><span class="sxs-lookup"><span data-stu-id="0fc0c-154">Ordering</span></span>

```csharp
// Get driving directions, ordering by if it's toll-free before estimated driving time.
var results = DirectionsProcessor.GetDirections(start, end)
              .OrderBy(direction => direction.HasNoTolls)
              .ThenBy(direction => direction.EstimatedTime);
```

```vb
' Get driving directions, ordering by if it's toll-free before estimated driving time.
Dim results = DirectionsProcessor.GetDirections(start, end).
                OrderBy(Function(direction) direction.HasNoTolls).
                ThenBy(Function(direction) direction.EstimatedTime)
```

### <a name="equality-of-instance-properties"></a><span data-ttu-id="0fc0c-155">Égalité des propriétés de l’instance</span><span class="sxs-lookup"><span data-stu-id="0fc0c-155">Equality of instance properties</span></span>

<span data-ttu-id="0fc0c-156">Enfin, un exemple plus avancé : déterminer si les valeurs des propriétés de deux instances du même type sont égales (emprunté à [ce billet StackOverflow](https://stackoverflow.com/a/844855) et modifié) :</span><span class="sxs-lookup"><span data-stu-id="0fc0c-156">Finally, a more advanced sample: determining if the values of the properties of two instances of the same type are equal (Borrowed and modified from [this StackOverflow post](https://stackoverflow.com/a/844855)):</span></span>

```csharp
public static bool PublicInstancePropertiesEqual<T>(this T self, T to, params string[] ignore) where T : class
{
    if (self == null || to == null)
    {
        return self == to;
    }

    // Selects the properties which have unequal values into a sequence of those properties.
    var unequalProperties = from property in typeof(T).GetProperties(BindingFlags.Public | BindingFlags.Instance)
                            where !ignore.Contains(property.Name)
                            let selfValue = property.GetValue(self, null)
                            let toValue = property.GetValue(to, null)
                            where !Equals(selfValue, toValue)
                            select property;
    return !unequalProperties.Any();
}
```

```vb
<System.Runtime.CompilerServices.Extension()>
Public Function PublicInstancePropertiesEqual(Of T As Class)(self As T, [to] As T, ParamArray ignore As String()) As Boolean
    If self Is Nothing OrElse [to] Is Nothing Then
        Return self Is [to]
    End If

    ' Selects the properties which have unequal values into a sequence of those properties.
    Dim unequalProperties = From [property] In GetType(T).GetProperties(BindingFlags.Public Or BindingFlags.Instance)
                            Where Not ignore.Contains([property].Name)
                            Let selfValue = [property].GetValue(self, Nothing)
                            Let toValue = [property].GetValue([to], Nothing)
                            Where Not Equals(selfValue, toValue) Select [property]
    Return Not unequalProperties.Any()
End Function
```

## <a name="plinq"></a><span data-ttu-id="0fc0c-157">PLINQ</span><span class="sxs-lookup"><span data-stu-id="0fc0c-157">PLINQ</span></span>

<span data-ttu-id="0fc0c-158">PLINQ, ou Parallel LINQ, est un moteur d’exécution parallèle pour les expressions LINQ.</span><span class="sxs-lookup"><span data-stu-id="0fc0c-158">PLINQ, or Parallel LINQ, is a parallel execution engine for LINQ expressions.</span></span> <span data-ttu-id="0fc0c-159">En d’autres termes, une expression régulière LINQ peut être parallélisée de manière simple sur n’importe quel nombre de threads.</span><span class="sxs-lookup"><span data-stu-id="0fc0c-159">In other words, a regular LINQ expression can be trivially parallelized across any number of threads.</span></span> <span data-ttu-id="0fc0c-160">Cela s’effectue par un appel à `AsParallel()` avant l’expression.</span><span class="sxs-lookup"><span data-stu-id="0fc0c-160">This is accomplished via a call to `AsParallel()` preceding the expression.</span></span>

<span data-ttu-id="0fc0c-161">Tenez compte des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="0fc0c-161">Consider the following:</span></span>

```csharp
public static string GetAllFacebookUserLikesMessage(IEnumerable<FacebookUser> facebookUsers)
{
    var seed = default(UInt64);

    Func<UInt64, UInt64, UInt64> threadAccumulator = (t1, t2) => t1 + t2;
    Func<UInt64, UInt64, UInt64> threadResultAccumulator = (t1, t2) => t1 + t2;
    Func<Uint64, string> resultSelector = total => $"Facebook has {total} likes!";

    return facebookUsers.AsParallel()
                        .Aggregate(seed, threadAccumulator, threadResultAccumulator, resultSelector);
}
```

```vb
Public Shared GetAllFacebookUserLikesMessage(facebookUsers As IEnumerable(Of FacebookUser)) As String
{
    Dim seed As UInt64 = 0

    Dim threadAccumulator As Func(Of UInt64, UInt64, UInt64) = Function(t1, t2) t1 + t2
    Dim threadResultAccumulator As Func(Of UInt64, UInt64, UInt64) = Function(t1, t2) t1 + t2
    Dim resultSelector As Func(Of Uint64, string) = Function(total) $"Facebook has {total} likes!"

    Return facebookUsers.AsParallel().
                        Aggregate(seed, threadAccumulator, threadResultAccumulator, resultSelector)
}
```

<span data-ttu-id="0fc0c-162">Ce code partitionne `facebookUsers` entre les threads système si nécessaire, additionne le nombre total de mentions J’aime sur chaque thread en parallèle, additionne les résultats calculés par chaque thread et projette ce résultat dans une chaîne très pratique.</span><span class="sxs-lookup"><span data-stu-id="0fc0c-162">This code will partition `facebookUsers` across system threads as necessary, sum up the total likes on each thread in parallel, sum the results computed by each thread, and project that result into a nice string.</span></span>

<span data-ttu-id="0fc0c-163">Sous forme de diagramme :</span><span class="sxs-lookup"><span data-stu-id="0fc0c-163">In diagram form:</span></span>

![Diagramme PLINQ](media/index/plinq-diagram.png)

<span data-ttu-id="0fc0c-165">Les tâches parallèles liées à l’UC qui peuvent être facilement exprimées via LINQ (en d’autres termes, sont des fonctions pures et n’ont pas d’effets secondaires) sont un bon candidat pour PLINQ.</span><span class="sxs-lookup"><span data-stu-id="0fc0c-165">Parallelizable CPU-bound jobs that can be easily expressed via LINQ (in other words, are pure functions and have no side effects) are a great candidate for PLINQ.</span></span> <span data-ttu-id="0fc0c-166">Pour les tâches _qui ont_ un effet secondaire, envisagez d’utiliser la [bibliothèque parallèle de tâches](../parallel-programming/task-parallel-library-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="0fc0c-166">For jobs that _do_ have a side effect, consider using the [Task Parallel Library](../parallel-programming/task-parallel-library-tpl.md).</span></span>

## <a name="more-resources"></a><span data-ttu-id="0fc0c-167">Plus de ressources</span><span class="sxs-lookup"><span data-stu-id="0fc0c-167">More resources</span></span>

* [<span data-ttu-id="0fc0c-168">101 exemples LINQ</span><span class="sxs-lookup"><span data-stu-id="0fc0c-168">101 LINQ Samples</span></span>](/samples/dotnet/try-samples/101-linq-samples/)
* <span data-ttu-id="0fc0c-169">[LINQPad](https://www.linqpad.net/), environnement de laboratoire et moteur d’interrogation de base de données pour C#/F #/Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0fc0c-169">[Linqpad](https://www.linqpad.net/), a playground environment and Database querying engine for C#/F#/Visual Basic</span></span>
* <span data-ttu-id="0fc0c-170">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), livre électronique pour apprendre comment LINQ-to-objects est implémenté</span><span class="sxs-lookup"><span data-stu-id="0fc0c-170">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), an e-book for learning how LINQ-to-objects is implemented</span></span>
