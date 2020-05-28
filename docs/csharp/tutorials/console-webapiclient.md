---
title: Crée un client REST à l’aide de .NET Core
description: Ce didacticiel vous présente un certain nombre de fonctionnalités de .NET Core et du langage C#.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 1d1d1bec8c6602e4fe34fa3ce243423290412736
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004853"
---
# <a name="rest-client"></a>Client REST

Ce didacticiel vous présente un certain nombre de fonctionnalités de .NET Core et du langage C#. Vous apprendrez à :

* Notions de base du CLI .NET Core.
* Une présentation des fonctionnalités du langage C#.
* Gestion des dépendances avec NuGet
* Communications HTTP
* Traitement des informations JSON
* Gestion de la configuration avec les attributs.

Vous allez générer une application qui émet des requêtes HTTP vers un service REST sur GitHub. Vous lirez des informations au format JSON et convertirez ce paquet JSON en objets C#. Enfin, vous verrez comment travailler avec les objets C#.

Ce didacticiel présente de nombreuses fonctionnalités. Nous allons les construire une par une.

Si vous préférez utiliser l’[exemple final](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) pour cette rubrique, vous pouvez le télécharger. Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Prérequis

Vous devez configurer votre ordinateur pour exécuter .NET core. Vous trouverez les instructions d’installation dans la page [téléchargements .net Core](https://dotnet.microsoft.com/download) . Vous pouvez exécuter cette application sur Windows, Linux, Mac OS ou dans un conteneur Docker.
Vous devez installer l’éditeur de code de votre choix. Les descriptions ci-dessous utilisent [Visual Studio code](https://code.visualstudio.com/), qui est un éditeur de plateformes Open source et multiplateforme. Cependant, vous pouvez utiliser les outils avec lesquels vous êtes le plus à l’aise.

## <a name="create-the-application"></a>Création de l’application

La première étape consiste à créer une nouvelle application. Ouvrez une invite de commandes et créez un nouveau répertoire pour votre application. Réglez-le comme répertoire actuel. Entrez la commande suivante dans une fenêtre de console :

```dotnetcli
dotnet new console --name WebAPIClient
```

Elle crée les fichiers de démarrage d’une application « Hello World » de base. Le nom du projet est « WebAPIClient ». Comme il s’agit d’un nouveau projet, aucune des dépendances n’est en place. La première exécution télécharge l’infrastructure .NET Core, installe un certificat de développement et exécute le gestionnaire de package NuGet pour restaurer les dépendances manquantes.

Avant de commencer à apporter des modifications, tapez `dotnet run` ([voir la remarque](#dotnet-restore-note)) à l’invite de commandes pour exécuter votre application. `dotnet run` effectue automatiquement `dotnet restore` s’il manque des dépendances dans votre environnement. Il effectue également `dotnet build` si votre application doit être regénérée.
Après la configuration initiale, vous devez uniquement exécuter `dotnet restore` ou `dotnet build` quand cela est pertinent pour votre projet.

## <a name="adding-new-dependencies"></a>Ajout de nouvelles dépendances

L’un des objectifs de conception clés de .NET Core consiste à réduire la taille de l’installation .NET. Si une application a besoin de bibliothèques supplémentaires pour certaines de ses fonctionnalités, vous ajoutez ces dépendances dans votre fichier projet (\*.csproj) en C#. Pour notre exemple, vous devez ajouter le `System.Runtime.Serialization.Json` package, afin que votre application puisse traiter les réponses JSON.

Vous aurez besoin du `System.Runtime.Serialization.Json` package pour cette application. Ajoutez-le à votre projet en exécutant la commande [CLI .net](../../core/tools/dotnet-add-package.md) suivante :

```dotnetcli
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a>Effectuer des requêtes web

Vous êtes maintenant prêt à commencer la récupération des données à partir du web. Dans cette application, vous obtiendrez des informations à partir de [l’API GitHub](https://developer.github.com/v3/). Nous allons lire des informations sur les projets couverts par la [.NET Foundation](https://www.dotnetfoundation.org/). Vous allez commencer par créer la demande à l’API GitHub pour récupérer des informations sur les projets. Vous allez utiliser le point de terminaison <https://api.github.com/orgs/dotnet/repos>. Vous souhaitez récupérer toutes les informations sur ces projets, vous allez donc utiliser une requête HTTP GET.
Votre navigateur utilise également les requêtes HTTP GET, vous pouvez donc coller cette URL dans votre navigateur pour voir les informations que vous recevez et traitez.

Vous utilisez la classe <xref:System.Net.Http.HttpClient> pour effectuer des requêtes web. Comme toutes les API .NET modernes, <xref:System.Net.Http.HttpClient> prend en charge uniquement les méthodes async pour ses API les plus anciennes.
Commencez par créer une méthode async. Vous allez effectuer l’implémentation lors de la création des fonctionnalités de l’application. Commencez en ouvrant le fichier `program.cs` dans votre répertoire de projet et l’ajout de la méthode suivante à la classe `Program` :

```csharp
private static async Task ProcessRepositories()
{
}
```

Vous devez ajouter une `using` directive en haut de votre `Main` méthode afin que le compilateur C# reconnaisse le <xref:System.Threading.Tasks.Task> type :

```csharp
using System.Threading.Tasks;
```

Si vous générez votre projet à ce stade, vous obtiendrez un avertissement généré pour cette méthode, car elle ne contient aucun opérateur `await` et s’exécute de façon synchrone. Ignorez-le pour le moment. vous ajouterez des opérateurs `await` lorsque vous remplirez la méthode.

Ensuite, mettez à jour la `Main` méthode pour appeler la `ProcessRepositories` méthode. La `ProcessRepositories` méthode retourne une tâche et vous ne devez pas quitter le programme avant que cette tâche se termine. Par conséquent, vous devez modifier la signature de `Main` . Ajoutez le `async` modificateur, puis remplacez le type de retour par `Task` . Ensuite, dans le corps de la méthode, ajoutez un appel à `ProcessRepositories` . Ajoutez le `await` mot clé à cet appel de méthode :

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

À présent, vous disposez d’un programme qui ne fait rien, mais le fait de façon asynchrone. Nous allons l’améliorer.

Tout d’abord, vous avez besoin d’un objet pouvant récupérer des données à partir du web ; pour ce faire, vous pouvez utiliser <xref:System.Net.Http.HttpClient>. Cet objet gère la demande et les réponses. Instanciez une instance unique de ce type dans la `Program` classe à l’intérieur du fichier *Program.cs* .

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static async Task Main(string[] args)
        {
            //...
        }
    }
}
```

Revenons à la méthode `ProcessRepositories` et créons sa première version :

```csharp
private static async Task ProcessRepositories()
{
    client.DefaultRequestHeaders.Accept.Clear();
    client.DefaultRequestHeaders.Accept.Add(
        new MediaTypeWithQualityHeaderValue("application/vnd.github.v3+json"));
    client.DefaultRequestHeaders.Add("User-Agent", ".NET Foundation Repository Reporter");

    var stringTask = client.GetStringAsync("https://api.github.com/orgs/dotnet/repos");

    var msg = await stringTask;
    Console.Write(msg);
}
```

Pour compiler, vous devez également ajouter deux nouvelles `using` directives en haut du fichier :

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

Cette première version effectue une requête web pour lire la liste de tous les dépôts de l’organisation dotnet foundation. (L’ID GitHub de la .NET Foundation est 'dotnet'). Les premières lignes configurent <xref:System.Net.Http.HttpClient> pour cette requête. Tout d’abord, il est configuré pour accepter les réponses JSON de GitHub.
Ce format est simplement du JSON. La ligne suivante ajoute un en-tête d’agent utilisateur à toutes les requêtes à partir de cet objet. Ces deux en-têtes sont vérifiés par le code du serveur GitHub et sont nécessaires pour récupérer des informations à partir de GitHub.

Une fois que vous avez configuré le <xref:System.Net.Http.HttpClient>, effectuez une requête web et récupérez la réponse. Dans cette première version, vous utilisez la méthode pratique <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType>. Cette méthode démarre une tâche qui effectue la requête web, et, lorsque la demande est renvoyée, lit le flux de réponse puis extrait le contenu à partir du flux. Le corps de la réponse est renvoyé en tant que <xref:System.String>. La chaîne est disponible lorsque la tâche est terminée.

Les deux dernières lignes de cette méthode attendent cette tâche et impriment la réponse dans la console.
Générez l'application et exécutez-la. L’avertissement de génération a disparu maintenant, car `ProcessRepositories` contient maintenant un opérateur `await`. Vous verrez long affichage de texte au format JSON.

## <a name="processing-the-json-result"></a>Traitement du résultat JSON

À ce stade, vous avez écrit le code pour récupérer une réponse à partir d’un serveur web et afficher le texte contenu dans cette réponse. Ensuite, nous allons convertir cette réponse JSON en objets C#.

La <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> classe sérialise les objets au format JSON et désérialise JSON en objets. Commencez par définir une classe pour représenter l' `repo` objet JSON retourné à partir de l’API GitHub :

```csharp
using System;

namespace WebAPIClient
{
    public class Repository
    {
        public string name { get; set; }
    }
}
```

Placez le code ci-dessus dans un fichier nommé « repo.cs ». Cette version de la classe représente le chemin d’accès le plus simple pour traiter les données JSON. Le nom de classe et le nom du membre correspondent aux noms utilisés dans le paquet JSON, au lieu des conventions C# suivantes. Vous allez corriger cela en fournissant des attributs de configuration ultérieurement. Cette classe décrit une autre fonctionnalité importante de la sérialisation et de désérialisation JSON : tous les champs dans le paquet JSON font partie de cette classe.
Le sérialiseur JSON ignore les informations qui ne sont pas incluses dans le type de classe utilisé.
Cette fonctionnalité facilite la création de types qui fonctionnent avec uniquement un sous-ensemble des champs dans le paquet JSON.

Maintenant que vous avez créé le type, nous allons le désérialiser.

Ensuite, vous utiliserez le sérialiseur pour convertir le JSON en objets C#. Remplacez l’appel à <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> dans votre `ProcessRepositories` méthode par les lignes suivantes :

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
```

Vous utilisez de nouveaux espaces de noms. vous devez donc les ajouter en haut du fichier :

```csharp
using System.Collections.Generic;
using System.Text.Json;
```

Notez que vous utilisez maintenant <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> au lieu de <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>. Le sérialiseur utilise un flux plutôt qu’une chaîne comme source. Nous allons expliquer quelques-unes des fonctionnalités du langage C# qui sont utilisées dans la deuxième ligne de l’extrait de code précédent. Le premier argument de <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> est une `await` expression. (Les deux autres paramètres sont facultatifs et sont omis dans l’extrait de code.) Les expressions await peuvent apparaître presque n’importe où dans votre code, même si vous ne les avez vu que dans le cadre d’une instruction d’assignation. La `Deserialize` méthode est *générique*, ce qui signifie que vous devez fournir des arguments de type pour les types d’objets qui doivent être créés à partir du texte JSON. Dans cet exemple, vous désérialisez vers un `List<Repository>` , qui est un autre objet générique, le <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> . La `List<>` classe stocke une collection d’objets. L’argument de type déclare le type des objets stockés dans le `List<>` . Le texte JSON représente une collection d’objets référentiel, donc l’argument de type est `Repository` .

Nous en avons presque terminé avec cette section. Maintenant que vous avez converti le JSON en objets C#, nous allons afficher le nom de chaque dépôt. Remplacez les lignes :

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

avec les éléments suivants :

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

Compilez et exécutez l'application. Cela affichera les noms des espaces de stockage qui font partie de la .NET Foundation.

## <a name="controlling-serialization"></a>Contrôle de la sérialisation

Avant d’ajouter d’autres fonctionnalités, nous allons traiter la propriété à l' `name` aide de l' `[JsonPropertyName]` attribut. Apportez les modifications suivantes à la déclaration du champ `name` dans repo.cs :

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

Pour utiliser `[JsonPropertyName]` l’attribut, vous devez ajouter l' <xref:System.Text.Json.Serialization> espace de noms aux `using` directives :

```csharp
using System.Text.Json.Serialization;
```

Cette modification signifie que vous devez modifier le code qui écrit le nom de chaque dépôt dans program.cs :

```csharp
Console.WriteLine(repo.Name);
```

Exécutez `dotnet run` pour vérifier que les mappages sont corrects. Vous devriez voir la même sortie que précédemment.

Nous allons apporter une modification de plus avant d’ajouter de nouvelles fonctionnalités. La méthode `ProcessRepositories` peut faire le travail de façon asynchrone et renvoyer une collection des espaces de stockage. Nous allons renvoyer `List<Repository>` à partir de cette méthode et déplacer le code qui écrit les informations dans la méthode `Main`.

Modifiez la signature de `ProcessRepositories` pour retourner une tâche dont le résultat est une liste d’objets `Repository` :

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

Ensuite, retournez simplement les dépôts après le traitement de la réponse JSON :

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

Le compilateur génère l’objet `Task<T>` pour la valeur de retour, car vous avez marqué cette méthode comme `async`.
Ensuite, nous allons modifier la méthode `Main` afin qu’elle capture les résultats et écrive le nom de chaque dépôt dans la console. Votre méthode `Main` se présente maintenant comme suit :

```csharp
public static async Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a>Lire plus d'informations

Terminons par le traitement d’un certain nombre de propriétés dans le paquet JSON envoyé à partir de l’API GitHub. Vous ne voudrez pas récupérer tous les éléments, mais ajouter quelques propriétés vous permettra de découvrir d’autres fonctionnalités du langage C#.

Commençons par ajouter quelques autres types simples à la définition de classe `Repository`. Ajoutez ces propriétés à cette classe :

```csharp
[JsonPropertyName("description")]
public string Description { get; set; }

[JsonPropertyName("html_url")]
public Uri GitHubHomeUrl { get; set; }

[JsonPropertyName("homepage")]
public Uri Homepage { get; set; }

[JsonPropertyName("watchers")]
public int Watchers { get; set; }
```

Ces propriétés ont intégré des conversions intégrées du type chaîne (c’est ce que contiennent les paquets JSON) vers le type cible. Le type <xref:System.Uri> peut être nouveau pour vous. Il représente un URI, ou dans ce cas, une URL. Dans le cas des types `Uri` et `int`, si le paquet JSON contient des données qui ne sont pas convertibles dans le type cible, l’action de sérialisation lèvera une exception.

Une fois que vous avez ajouté cela, mettez à jour la méthode `Main` pour afficher ces éléments :

```csharp
foreach (var repo in repositories)
{
    Console.WriteLine(repo.Name);
    Console.WriteLine(repo.Description);
    Console.WriteLine(repo.GitHubHomeUrl);
    Console.WriteLine(repo.Homepage);
    Console.WriteLine(repo.Watchers);
    Console.WriteLine();
}
```

Dans la dernière étape, nous allons ajouter les informations de la dernière opération Push. Ces informations sont formatées de cette façon dans la réponse JSON :

```json
2016-02-08T21:27:00Z
```

Ce format est au format de temps universel coordonné (UTC). vous obtiendrez donc une <xref:System.DateTime> valeur dont la <xref:System.DateTime.Kind%2A> propriété est <xref:System.DateTimeKind.Utc> . Si vous préférez une date représentée dans votre fuseau horaire, vous devez écrire une méthode de conversion personnalisée. Tout d’abord, définissez une `public` propriété qui contiendra la représentation UTC de la date et de l’heure dans votre `Repository` classe et une `LastPush` `readonly` propriété qui retourne la date convertie en heure locale :

```csharp
[JsonPropertyName("pushed_at")]
public DateTime LastPushUtc { get; set; }

public DateTime LastPush => LastPushUtc.ToLocalTime();
```

Passons en revue les nouvelles constructions que nous venons de définir. La `LastPush` propriété est définie à l’aide d’un *membre à expression nulle* pour l' `get` accesseur. Il n'existe aucun accesseur `set`. L’omission de l' `set` accesseur est la façon dont vous définissez une propriété *en lecture seule* en C#. (Oui, vous pouvez créer des propriétés *en écriture seule* en C#, mais leur intérêt est limité.)

Enfin, ajoutez une dernière instruction de sortie dans la console et vous êtes prêt à générer et exécuter de nouveau cette application :

```csharp
Console.WriteLine(repo.LastPush);
```

Votre version doit maintenant correspondre à l’[exemple terminé](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).

## <a name="conclusion"></a>Conclusion

Ce didacticiel vous a montré comment effectuer des demandes web, analyser le résultat et afficher les propriétés de ces résultats. Vous avez également ajouté de nouveaux packages en tant que dépendances dans votre projet. Vous avez vu certaines des fonctionnalités du langage C# qui prennent en charge des techniques orientées objet.

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
