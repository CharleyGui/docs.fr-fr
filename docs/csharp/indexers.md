---
title: Indexeurs
description: Découvrez les indexeurs C# et la façon d’implémenter des propriétés indexées, qui sont des propriétés référencées à l’aide d’un ou plusieurs arguments.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 0e9496da-e766-45a9-b92b-91820d4a350e
ms.openlocfilehash: 1369740404c500d8b44b4706959bf4640c26aa2d
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656109"
---
# <a name="indexers"></a>Indexeurs

Les *indexeurs* sont similaires aux propriétés. Les indexeurs sont souvent construits à l’aide des mêmes fonctionnalités de langage que les [propriétés](properties.md). Il permettent l’utilisation de propriétés *indexées*, qui sont référencées à l’aide d’un ou plusieurs arguments. Ces arguments fournissent un index dans une collection de valeurs.

## <a name="indexer-syntax"></a>Syntaxe de l’indexeur

Vous pouvez accéder à un indexeur avec un nom de variable et des crochets. Vous devez placer les arguments de l’indexeur entre crochets :

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

Déclarez les indexeurs en utilisant le mot clé `this` comme nom de propriété et en déclarant les arguments entre crochets. Cette déclaration correspond à l’utilisation abordée dans le paragraphe précédent :

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

Dans ce premier exemple, vous pouvez voir la relation entre la syntaxe des propriétés et celle des indexeurs. Cette analogie s’applique à la plupart des règles de syntaxe des indexeurs. Les indexeurs peuvent avoir n’importe quel modificateur d’accès valide (public, protected internal, protected, internal, private ou private protected). Ils peuvent être sealed, virtual ou abstract. Comme pour les propriétés, vous pouvez spécifier des modificateurs d’accès différents pour les accesseurs get et set d’un indexeur.
Vous pouvez également spécifier des indexeurs en lecture seule (en omettant l’accesseur set) ou des indexeurs en écriture seule (en omettant l’accesseur get).

Vous pouvez appliquer aux indexeurs quasiment tout ce que vous avez appris de l’utilisation des propriétés. La seule exception à cette règle sont les *propriétés implémentées automatiquement*. Le compilateur ne peut pas toujours générer le stockage adapté à l’indexeur.

C’est la présence d’arguments référençant un élément dans un ensemble d’éléments qui distingue les indexeurs des propriétés. Vous pouvez définir plusieurs indexeurs sur un type, tant que chaque indexeur a sa propre liste d’arguments. Nous allons explorer différents scénarios où vous pourrez utiliser un ou plusieurs indexeurs dans une définition de classe.

## <a name="scenarios"></a>Scénarios

Vous définissez des *indexeurs* dans votre type quand son API modélise une collection dans laquelle vous définissez des arguments. Vos indexeurs peuvent ou non être mappés directement aux types de collection qui font partie du framework .NET Core. Votre type peut avoir d’autres responsabilités en plus de la modélisation d’une collection.
Les indexeurs vous permettent de fournir l’API qui correspond à l’abstraction de votre type sans exposer les détails internes concernant le stockage ou le calcul des valeurs de cette abstraction.

Examinons quelques-uns des scénarios courants d’utilisation des *indexeurs*. Vous pouvez accéder au [dossier d’exemples d’indexeurs](https://github.com/dotnet/samples/tree/master/csharp/indexers). Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../samples-and-tutorials/index.md#view-and-download-samples).

### <a name="arrays-and-vectors"></a>Tableaux et vecteurs

L’un des scénarios de création d’indexeur les plus courants est lorsque votre type modélise un tableau ou un vecteur. Vous pouvez créer un indexeur pour modéliser une liste de données triées.

L’avantage de créer votre propre indexeur est que vous pouvez définir le stockage de cette collection en fonction de vos besoins. Imaginez un scénario où votre type modélise des données d’historique qui sont trop volumineuses pour être chargées en une seule fois dans la mémoire. Vous devez charger et décharger des sections de la collection selon leur utilisation. L’exemple suivant modélise ce comportement. Il signale le nombre de points de données. Il crée à la demande des pages contenant des sections de données. Il supprime des pages de la mémoire afin de libérer de l’espace pour les pages qui ont fait l’objet de demandes récentes.

```csharp
public class DataSamples
{
    private class Page
    {
        private readonly List<Measurements> pageData = new List<Measurements>();
        private readonly int startingIndex;
        private readonly int length;
        private bool dirty;
        private DateTime lastAccess;

        public Page(int startingIndex, int length)
        {
            this.startingIndex = startingIndex;
            this.length = length;
            lastAccess = DateTime.Now;

            // This stays as random stuff:
            var generator = new Random();
            for(int i=0; i < length; i++)
            {
                var m = new Measurements
                {
                    HiTemp = generator.Next(50, 95),
                    LoTemp = generator.Next(12, 49),
                    AirPressure = 28.0 + generator.NextDouble() * 4
                };
                pageData.Add(m);
            }
        }
        public bool HasItem(int index) =>
            ((index >= startingIndex) &&
            (index < startingIndex + length));

        public Measurements this[int index]
        {
            get
            {
                lastAccess = DateTime.Now;
                return pageData[index - startingIndex];
            }
            set
            {
                pageData[index - startingIndex] = value;
                dirty = true;
                lastAccess = DateTime.Now;
            }
        }

        public bool Dirty => dirty;
        public DateTime LastAccess => lastAccess;
    }

    private readonly int totalSize;
    private readonly List<Page> pagesInMemory = new List<Page>();

    public DataSamples(int totalSize)
    {
        this.totalSize = totalSize;
    }

    public Measurements this[int index]
    {
        get
        {
            if (index < 0)
                throw new IndexOutOfRangeException("Cannot index less than 0");
            if (index >= totalSize)
                throw new IndexOutOfRangeException("Cannot index past the end of storage");

            var page = updateCachedPagesForAccess(index);
            return page[index];
        }
        set
        {
            if (index < 0)
                throw new IndexOutOfRangeException("Cannot index less than 0");
            if (index >= totalSize)
                throw new IndexOutOfRangeException("Cannot index past the end of storage");
            var page = updateCachedPagesForAccess(index);

            page[index] = value;
        }
    }

    private Page updateCachedPagesForAccess(int index)
    {
        foreach (var p in pagesInMemory)
        {
            if (p.HasItem(index))
            {
                return p;
            }
        }
        var startingIndex = (index / 1000) * 1000;
        var newPage = new Page(startingIndex, 1000);
        addPageToCache(newPage);
        return newPage;
    }

    private void addPageToCache(Page p)
    {
        if (pagesInMemory.Count > 4)
        {
            // remove oldest non-dirty page:
            var oldest = pagesInMemory
                .Where(page => !page.Dirty)
                .OrderBy(page => page.LastAccess)
                .FirstOrDefault();
            // Note that this may keep more than 5 pages in memory
            // if too much is dirty
            if (oldest != null)
                pagesInMemory.Remove(oldest);
        }
        pagesInMemory.Add(p);
    }
}
```

Vous pouvez suivre cet idiome de conception afin de modéliser toute sorte de collection pour laquelle il existe de bonnes raisons de ne pas charger l’intégralité des données en mémoire. Notez que la classe `Page` est une classe privée imbriquée qui ne fait pas partie de l’interface publique. Ces détails sont masqués pour tous les utilisateurs de cette classe.

### <a name="dictionaries"></a>Dictionnaires

Un autre scénario courant est lorsque vous avez besoin de modéliser un dictionnaire ou un mappage. Dans ce cas, votre type stocke des valeurs en fonction des clés, généralement des clés de texte. Cet exemple crée un dictionnaire qui mappe les arguments de ligne de commande à des [expressions lambda](delegates-overview.md) qui gèrent ces options. L’exemple suivant montre deux classes : une classe `ArgsActions` qui mappe une option de ligne de commande à un délégué `Action`, et un `ArgsProcessor` qui utilise `ArgsActions` pour exécuter chaque `Action` quand il rencontre cette option.

```csharp
public class ArgsProcessor
{
    private readonly ArgsActions actions;

    public ArgsProcessor(ArgsActions actions)
    {
        this.actions = actions;
    }

    public void Process(string[] args)
    {
        foreach(var arg in args)
        {
            actions[arg]?.Invoke();
        }
    }

}
public class ArgsActions
{
    readonly private Dictionary<string, Action> argsActions = new Dictionary<string, Action>();

    public Action this[string s]
    {
        get
        {
            Action action;
            Action defaultAction = () => {} ;
            return argsActions.TryGetValue(s, out action) ? action : defaultAction;
        }
    }

    public void SetOption(string s, Action a)
    {
        argsActions[s] = a;
    }
}
```

Dans cet exemple, la collection `ArgsAction` correspond étroitement à la collection sous-jacente.
`get` détermine si une option donnée a été configurée. Si c’est le cas, il retourne le `Action` associé à cette option. Sinon, il retourne un `Action` qui n’a aucun effet. L’accesseur public n’inclut pas d’accesseur `set`, mais il comprend la conception qui utilise une méthode publique pour définir des options.

### <a name="multi-dimensional-maps"></a>Mappages multidimensionnels

Vous pouvez créer des indexeurs qui utilisent plusieurs arguments. En outre, ces arguments ne sont pas contraints à être du même type. Examinons ces deux exemples.

Le premier exemple montre une classe qui génère des valeurs pour un ensemble de Mandelbrot. Pour plus d’informations sur les mathématiques impliquées par cet ensemble, lisez [cet article](https://en.wikipedia.org/wiki/Mandelbrot_set).
L’indexeur utilise deux doubles pour définir un point dans le plan X, Y.
L’accesseur get calcule le nombre d’itérations jusqu’à un point déterminé pour ne pas se trouver dans l’ensemble. Si le nombre maximal d’itérations est atteint, le point se trouve dans l’ensemble, et la valeur maxIterations de la classe est retournée. Les images générées par ordinateur popularisées par l’ensemble de Mandelbrot définissent des couleurs pour le nombre d’itérations qui sont nécessaires pour déterminer qu’un point se trouve en dehors de l’ensemble.

```csharp
public class Mandelbrot
{
    readonly private int maxIterations;

    public Mandelbrot(int maxIterations)
    {
        this.maxIterations = maxIterations;
    }

    public int this [double x, double y]
    {
        get
        {
            var iterations = 0;
            var x0 = x;
            var y0 = y;

            while ((x*x + y * y < 4) &&
                (iterations < maxIterations))
            {
                var newX = x * x - y * y + x0;
                y = 2 * x * y + y0;
                x = newX;
                iterations++;
            }
            return iterations;
        }
    }
}
```

L’ensemble de Mandelbrot définit des valeurs à chaque coordonnée (x, y) pour des valeurs de nombres réels.
Cela définit un dictionnaire qui peut contenir un nombre infini de valeurs. Par conséquent, aucun stockage n’est nécessaire. Cette classe calcule la valeur de chaque point lorsque le code appelle l’accesseur `get`. Aucun stockage sous-jacent n’est utilisé.

Examinons une dernière utilisation d’indexeur, dans laquelle l’indexeur accepte plusieurs arguments de types différents. Prenons un programme qui gère des données d’historique des températures. Cet indexeur utilise une ville et une date pour définir ou obtenir les températures minimales et maximales de la ville en question :

```csharp
using DateMeasurements =
    System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements =
    System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;

public class HistoricalWeatherData
{
    readonly CityDataMeasurements storage = new CityDataMeasurements();

    public Measurements this[string city, DateTime date]
    {
        get
        {
            var cityData = default(DateMeasurements);

            if (!storage.TryGetValue(city, out cityData))
                throw new ArgumentOutOfRangeException(nameof(city), "City not found");

            // strip out any time portion:
            var index = date.Date;
            var measure = default(Measurements);
            if (cityData.TryGetValue(index, out measure))
                return measure;
            throw new ArgumentOutOfRangeException(nameof(date), "Date not found");
        }
        set
        {
            var cityData = default(DateMeasurements);

            if (!storage.TryGetValue(city, out cityData))
            {
                cityData = new DateMeasurements();
                storage.Add(city, cityData);
            }

            // Strip out any time portion:
            var index = date.Date;
            cityData[index] = value;
        }
    }
}
```

Cet exemple crée un indexeur qui mappe des données météorologiques sur deux arguments différents : une ville (représentée par un `string`) et une date (représentée par un `DateTime`). Le stockage interne utilise deux classes `Dictionary` pour représenter le dictionnaire à deux dimensions. L’API publique ne représente plus le stockage sous-jacent. Les fonctionnalités de langage des indexeurs vous permettent de créer une interface publique qui représente votre abstraction, même si le stockage sous-jacent doit utiliser des types de collections de base différents.

Ce code comprend deux sections avec lesquelles vous pouvez ne pas être familier. Ces deux `using` directives :

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

créent un *alias* pour un type générique construit. Ces instructions permettent au code d’utiliser plus tard les noms plus descriptifs que sont `DateMeasurements` et `CityDateMeasurements`, au lieu de la construction générique de `Dictionary<DateTime, Measurements>` et `Dictionary<string, Dictionary<DateTime, Measurements> >`.
Cette construction nécessite l’utilisation de noms de types qualifiés complets à droite du signe `=`.

La deuxième technique consiste à supprimer les sections de date et heure de tous les objets `DateTime` utilisés pour indexer des collections. .NET n’inclut pas de type Date uniquement.
Les développeurs utilisent le type `DateTime`, mais utilisent la propriété `Date` pour s’assurer qu’il n’existe pas d’objets `DateTime` égaux pour ce jour-là.

## <a name="summing-up"></a>Récapitulatif

Vous devez créer des indexeurs chaque fois que vous avez un élément de type propriété dans votre classe, où cette propriété ne représente pas une valeur unique, mais une collection de valeurs dans laquelle chaque élément est identifié par un ensemble d’arguments. Ces arguments peuvent identifier quel élément de la collection doit être référencé.
Les indexeurs étendent le concept de [Propriétés](properties.md), où un membre est traité comme un élément de données provenant de l’extérieur de la classe, mais comme une méthode à l’intérieur. Les indexeurs autorisent les arguments à rechercher un élément d’une propriété qui représente un ensemble d’éléments.
