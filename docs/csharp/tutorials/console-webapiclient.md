---
title: Crée un client REST à l’aide de .NET Core
description: Ce didacticiel vous présente un certain nombre de fonctionnalités de .NET Core et du langage C#.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 5796df2d2fd8c4d9aaca783d720448c90858c067
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156855"
---
# <a name="rest-client"></a>Client REST

Ce didacticiel vous présente un certain nombre de fonctionnalités de .NET Core et du langage C#. Vous apprendrez à :

* Les bases de l’ICIC .NET Core.
* Une présentation des fonctionnalités du langage C#.
* Gestion des dépendances avec NuGet
* Communications HTTP
* Traitement des informations JSON
* Gestion de la configuration avec les attributs.

Vous allez générer une application qui émet des requêtes HTTP vers un service REST sur GitHub. Vous lirez des informations au format JSON et convertirez ce paquet JSON en objets C#. Enfin, vous verrez comment travailler avec les objets C#.

Il ya beaucoup de fonctionnalités dans ce tutoriel. Nous allons les construire une par une.

Si vous préférez utiliser l’[exemple final](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) pour cette rubrique, vous pouvez le télécharger. Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Conditions préalables requises

Vous devez configurer votre ordinateur pour exécuter .NET core. Vous pouvez trouver les instructions d’installation sur la page [.NET Core Downloads.](https://dotnet.microsoft.com/download) Vous pouvez exécuter cette application sur Windows, Linux, Mac OS ou dans un conteneur Docker.
Vous devez installer l’éditeur de code de votre choix. Les descriptions ci-dessous utilisent [Visual Studio Code](https://code.visualstudio.com/), qui est une open source, éditeur de plate-forme croisée. Cependant, vous pouvez utiliser les outils avec lesquels vous êtes le plus à l’aise.

## <a name="create-the-application"></a>Création de l’application

La première étape consiste à créer une nouvelle application. Ouvrez une invite de commandes et créez un nouveau répertoire pour votre application. Réglez-le comme répertoire actuel. Entrez la commande suivante dans une fenêtre de console :

```dotnetcli
dotnet new console --name WebApiClient
```

Elle crée les fichiers de démarrage d’une application « Hello World » de base. Le nom du projet est "WebApiClient". Comme il s’agit d’un nouveau projet, aucune des dépendances n’est en place. La première exécution téléchargera le cadre .NET Core, installera un certificat de développement et exécutera le gestionnaire de paquets NuGet pour restaurer les dépendances manquantes.

Avant de commencer à apporter des modifications, tapez `dotnet run` ([voir la remarque](#dotnet-restore-note)) à l’invite de commandes pour exécuter votre application. `dotnet run` effectue automatiquement `dotnet restore` s’il manque des dépendances dans votre environnement. Il effectue également `dotnet build` si votre application doit être regénérée.
Après la configuration initiale, vous devez uniquement exécuter `dotnet restore` ou `dotnet build` quand cela est pertinent pour votre projet.

## <a name="adding-new-dependencies"></a>Ajout de nouvelles dépendances

L’un des objectifs de conception clés de .NET Core consiste à réduire la taille de l’installation .NET. Si une application a besoin de bibliothèques supplémentaires pour certaines de ses fonctionnalités, vous ajoutez ces dépendances dans votre fichier projet (\*.csproj) en C#. Pour notre exemple, vous devrez `System.Runtime.Serialization.Json` ajouter le paquet, afin que votre demande puisse traiter les réponses JSON.

Vous aurez besoin `System.Runtime.Serialization.Json` du paquet pour cette application. Ajoutez-le à votre projet en exécutant la commande [CLI .NET](../../core/tools/dotnet-add-package.md) suivante :

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

Vous devrez ajouter une `using` directive en haut `Main` de votre méthode afin que <xref:System.Threading.Tasks.Task> le compilateur Cmd reconnaisse le type :

```csharp
using System.Threading.Tasks;
```

Si vous générez votre projet à ce stade, vous obtiendrez un avertissement généré pour cette méthode, car elle ne contient aucun opérateur `await` et s’exécute de façon synchrone. Ignorez-le pour le moment. vous ajouterez des opérateurs `await` lorsque vous remplirez la méthode.

Ensuite, renommez l’espace de noms défini dans l’instruction `namespace` de sa valeur par défaut de `ConsoleApp` en `WebAPIClient`. Plus tard, nous allons définir une classe `repo` dans cet espace de noms.

Ensuite, mettez à jour la méthode `Main` pour appeler cette méthode. La `ProcessRepositories` méthode renvoie une tâche, et vous ne devriez pas quitter le programme avant que cette tâche se termine. Par conséquent, vous devez `Main`changer la signature de . Ajouter `async` le modificateur et modifier `Task`le type de retour à . Puis, dans le corps de la `ProcessRepositories`méthode, ajouter un appel à . Ajoutez `await` le mot clé à cet appel de méthode :

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

À présent, vous disposez d’un programme qui ne fait rien, mais le fait de façon asynchrone. Nous allons l’améliorer.

Tout d’abord, vous avez besoin d’un objet pouvant récupérer des données à partir du web ; pour ce faire, vous pouvez utiliser <xref:System.Net.Http.HttpClient>. Cet objet gère la demande et les réponses. Instantané d’une seule instance de `Program` ce type dans la classe à l’intérieur du fichier *Program.cs.*

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

Vous devrez également ajouter deux `using` nouvelles directives en haut du fichier pour que cela compile :

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

La <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> classe sérialis des objets à JSON et désélise JSON en objets. Commencez par définir une `repo` classe pour représenter l’objet JSON retourné de l’API GitHub :

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

Ensuite, vous utiliserez le sérialiseur pour convertir le JSON en objets C#. Remplacez <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> l’appel `ProcessRepositories` dans votre méthode par les trois lignes suivantes :

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
```

Vous utilisez un nouvel espace de nom, donc vous aurez besoin de l’ajouter en haut du fichier ainsi:

```csharp
using System.Text.Json;
```

Notez que vous utilisez maintenant <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> au lieu de <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>. Le sérialiseur utilise un flux plutôt qu’une chaîne comme source. Expliquons quelques caractéristiques de la langue C qui sont utilisées dans la deuxième ligne de l’extrait de code précédent. Le premier <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> argument `await` à être une expression. (Les deux autres paramètres sont facultatifs et sont omis dans l’extrait de code.) Les expressions en attente peuvent apparaître presque n’importe où dans votre code, même si jusqu’à présent, vous ne les avez vues que dans le cadre d’une déclaration d’affectation. La `Deserialize` méthode est *générique,* ce qui signifie que vous devez fournir des arguments de type pour quel type d’objets doivent être créés à partir du texte JSON. Dans cet exemple, vous déséialisez à un `List<Repository>`, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>qui est un autre objet générique, le . La `List<>` classe stocke une collection d’objets. L’argument type déclare le type `List<>`d’objets stockés dans le . Le texte JSON représente une collection d’objets `Repository`de pension, de sorte que l’argument de type est .

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

Avant d’ajouter plus de fonctionnalités, adressons-nous à la `name` propriété en utilisant l’attribut. `[JsonPropertyName]` Apportez les modifications suivantes à la déclaration du champ `name` dans repo.cs :

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

Pour `[JsonPropertyName]` utiliser l’attribut, vous <xref:System.Text.Json.Serialization> devrez ajouter `using` l’espace nom aux directives :

```csharp
using System.Text.Json.Serialization;
```

Cette modification signifie que vous devez modifier le code qui écrit le nom de chaque dépôt dans program.cs :

```csharp
Console.WriteLine(repo.Name);
```

Exécutez-vous `dotnet run` pour vous assurer que vous avez les cartes correctes. Vous devriez voir la même sortie que précédemment.

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

Ce format ne suit pas les formats .NET <xref:System.DateTime> standard. Par conséquent, vous devez écrire une méthode de conversion personnalisée. En outre, vous ne souhaiterez probablement pas que la chaîne brute soit exposée aux utilisateurs de la classe `Repository`. Les attributs permettent aussi de contrôler cela. Tout d’abord, `public` définissez une propriété qui tiendra `Repository` la représentation `LastPush` des chaînes de la date et de l’heure de votre classe et une `readonly` propriété qui renvoie une chaîne formatée qui représente la date retournée :

```csharp
[JsonPropertyName("pushed_at")]
public string JsonDate { get; set; }

public DateTime LastPush =>
    DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
```

Passons en avant les nouvelles constructions que nous venons de définir. La `LastPush` propriété est définie à l’aide `get` d’un membre à corps *d’expression* pour l’accesseur. Il n'existe aucun accesseur `set`. L’omission `set` de l’accesseur est la façon dont vous définissez une propriété *de lecture seulement* dans C. (Oui, vous pouvez créer des propriétés *d’écriture uniquement* dans le C, mais leur valeur est limitée.) La <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> méthode analyse une chaîne <xref:System.DateTime> et crée un objet à l’aide d’un `CultureInfo` format de date fourni, et ajoute des métadonnées supplémentaires à l’utilisation d’un `DateTime` objet. Si l’opération d’analyse échoue, l’accesseur de propriété lève une exception.

Pour <xref:System.Globalization.CultureInfo.InvariantCulture>utiliser, vous devrez <xref:System.Globalization> ajouter l’espace nom aux `using` directives dans `repo.cs`:

```csharp
using System.Globalization;
```

Enfin, ajoutez une dernière instruction de sortie dans la console et vous êtes prêt à générer et exécuter de nouveau cette application :

```csharp
Console.WriteLine(repo.LastPush);
```

Votre version doit maintenant correspondre à l’[exemple terminé](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).

## <a name="conclusion"></a>Conclusion

Ce didacticiel vous a montré comment effectuer des demandes web, analyser le résultat et afficher les propriétés de ces résultats. Vous avez également ajouté de nouveaux packages en tant que dépendances dans votre projet. Vous avez vu certaines des fonctionnalités du langage C# qui prennent en charge des techniques orientées objet.

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
