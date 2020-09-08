---
title: Vue d’ensemble de LINQ-.NET
description: LINQ (Language-Integrated Query) fournit des fonctions d’interrogation au niveau du langage et une API de fonction d’ordre supérieur pour C# et Visual Basic, qui vous permettent d’écrire du code déclaratif expressif.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.openlocfilehash: 2e8abef547d8cc06d80b8cbf865ec984eb91d330
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552417"
---
# <a name="linq-overview"></a>Vue d’ensemble de LINQ

LINQ (Language-Integrated Query) fournit des fonctions d’interrogation au niveau du langage et une API de [fonction d’ordre supérieur](https://en.wikipedia.org/wiki/Higher-order_function) pour C# et Visual Basic, qui vous permettent d’écrire du code déclaratif expressif.

## <a name="language-level-query-syntax"></a>Syntaxe de requête au niveau du langage

Voici la syntaxe de requête au niveau du langage :

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

Voici le même exemple d’utilisation de l' `IEnumerable<T>` API :

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

```vb
Dim linqExperts = programmers.Where(Function(p) p.IsNewToLINQ).
                             Select(Function(p) New LINQExpert(p))
```

## <a name="linq-is-expressive"></a>LINQ est expressif

Imaginez que vous avez une liste d’animaux domestiques, mais que vous voulez la convertir en dictionnaire dans lequel vous pouvez accéder à un animal directement par sa valeur `RFID`.

Il s’agit du code impératif traditionnel :

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

L’objectif derrière le code n’est pas de créer un nouveau `Dictionary<int, Pet>` et de l’ajouter à l’aide d’une boucle. il consiste à convertir une liste existante en dictionnaire ! LINQ conserve l’intention, contrairement au code impératif.

Il s’agit de l’expression LINQ équivalente :

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

```vb
Dim petLookup = pets.ToDictionary(Function(pet) pet.RFID)
```

Le code qui utilise LINQ est utile, car il égalise le terrain entre l’intention et le code dans un contexte de programmation. Un autre bonus est la concision du code. Imaginez que vous pouvez réduire d’un tiers les grandes parties d’un code Base comme illustré ci-dessus. Bonne affaire, n’est-ce pas ?

## <a name="linq-providers-simplify-data-access"></a>Les fournisseurs LINQ simplifient l’accès aux données

Pour un grand nombre de logiciels en nature, tout tourne autour du traitement des données provenant d’une source (bases de données, JSON, XML, etc.). Cela implique souvent d’apprendre une nouvelle API par source de données, ce qui peut s’avérer fastidieux. LINQ simplifie cela en faisant abstraction des éléments communs de l’accès aux données dans une syntaxe de requête qui se présente de la même façon, quelle que soit la source de données que vous choisissez.

Cela recherche tous les éléments XML avec une valeur d’attribut spécifique :

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

L’écriture de code pour parcourir manuellement le document XML pour effectuer cette tâche serait beaucoup plus complexe.

L’interaction avec XML n’est pas la seule chose que vous pouvez faire avec les fournisseurs LINQ. [LINQ to SQL](../../framework/data/adonet/sql/linq/index.md) est un mappeur ORM (Object-Relational Mapper) de base de données MSSQL relativement minimaliste. La bibliothèque [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) fournit un balayage efficace du document JSON via LINQ. En outre, si aucune bibliothèque ne fait ce dont vous avez besoin, vous pouvez également [écrire votre propre fournisseur LINQ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))!

## <a name="reasons-to-use-the-query-syntax"></a>Raisons d’utiliser la syntaxe de requête

Pourquoi utiliser la syntaxe de requête ? Il s’agit d’une question qui se pose souvent. Après tout, le code suivant :

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

```vb
Dim filteredItems = myItems.Where(Function(item) item.Foo)
```

est beaucoup plus concis que ce qui suit :

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

La syntaxe d’API n’est-elle pas seulement un moyen plus concis d’effectuer la syntaxe de requête ?

Non. La syntaxe de requête permet d’utiliser la clause **let**, ce qui vous permet d’introduire et de lier une variable dans la portée de l’expression, en l’utilisant dans les parties suivantes de l’expression. Il est possible de reproduire le même code avec la syntaxe d’API uniquement, mais cela entraînera très probablement du code difficile à lire.

Ce qui nous amène à la question suivante : **devez-vous vous contenter d’utiliser la syntaxe de requête ?**

La réponse à cette question est **Oui** dans les cas suivants :

- Votre code base existant utilise déjà la syntaxe de requête.
- Vous devez étendre les variables dans vos requêtes en raison de la complexité.
- Vous préférez la syntaxe de requête et celle-ci ne gêne pas votre code base.

La réponse à cette question est **non**, si...

- Votre code Base utilise déjà la syntaxe d’API
- Vous n’avez pas besoin de définir l’étendue des variables dans vos requêtes
- Vous préférez la syntaxe d’API et cela ne gêne pas votre code base

## <a name="essential-linq"></a>LINQ essentiel

Pour obtenir la liste complète des exemples LINQ, consultez [101 LINQ Samples](https://docs.microsoft.com/samples/dotnet/try-samples/101-linq-samples/) (101 exemples LINQ).

Les exemples suivants sont une démonstration rapide de quelques-uns des éléments essentiels de LINQ. Cette approche n’est pas exhaustive, car LINQ fournit plus de fonctionnalités que ce qui est présenté ici.

### <a name="the-bread-and-butter---where-select-and-aggregate"></a>Le pain et le beurre- `Where` , `Select` et `Aggregate`

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

### <a name="flattening-a-list-of-lists"></a>Aplatissement d’une liste de listes

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

```vb
' Transforms the list of kennels into a list of all their dogs.
Dim allDogsFromKennels = kennels.SelectMany(Function(kennel) kennel.Dogs)
```

### <a name="union-between-two-sets-with-custom-comparator"></a>Union entre deux ensembles (avec un comparateur personnalisé)

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

### <a name="intersection-between-two-sets"></a>Intersection entre deux jeux

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

### <a name="ordering"></a>Classement

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

### <a name="equality-of-instance-properties"></a>Égalité des propriétés de l’instance

Enfin, un exemple plus avancé : déterminer si les valeurs des propriétés de deux instances du même type sont égales (emprunté à [ce billet StackOverflow](https://stackoverflow.com/a/844855) et modifié) :

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

## <a name="plinq"></a>PLINQ

PLINQ, ou Parallel LINQ, est un moteur d’exécution parallèle pour les expressions LINQ. En d’autres termes, une expression régulière LINQ peut être parallélisée de manière simple sur n’importe quel nombre de threads. Cela s’effectue par un appel à `AsParallel()` avant l’expression.

Tenez compte des éléments suivants :

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

Ce code partitionne `facebookUsers` entre les threads système si nécessaire, additionne le nombre total de mentions J’aime sur chaque thread en parallèle, additionne les résultats calculés par chaque thread et projette ce résultat dans une chaîne très pratique.

Sous forme de diagramme :

![Diagramme PLINQ](media/index/plinq-diagram.png)

Les tâches parallèles liées à l’UC qui peuvent être facilement exprimées via LINQ (en d’autres termes, sont des fonctions pures et n’ont pas d’effets secondaires) sont un bon candidat pour PLINQ. Pour les tâches _qui ont_ un effet secondaire, envisagez d’utiliser la [bibliothèque parallèle de tâches](../parallel-programming/task-parallel-library-tpl.md).

## <a name="more-resources"></a>Plus de ressources

* [101 exemples LINQ](https://docs.microsoft.com/samples/dotnet/try-samples/101-linq-samples/)
* [LINQPad](https://www.linqpad.net/), environnement de laboratoire et moteur d’interrogation de base de données pour C#/F #/Visual Basic
* [EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), livre électronique pour apprendre comment LINQ-to-objects est implémenté
