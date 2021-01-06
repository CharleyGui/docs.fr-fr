---
title: Crée un client REST à l’aide de .NET Core
description: Ce didacticiel vous présente un certain nombre de fonctionnalités de .NET Core et du langage C#.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: b537108bd77b3ed2248ca9e459044e09fa854ba9
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97899650"
---
# <a name="rest-client"></a><span data-ttu-id="3886a-103">Client REST</span><span class="sxs-lookup"><span data-stu-id="3886a-103">REST client</span></span>

<span data-ttu-id="3886a-104">Ce didacticiel vous présente un certain nombre de fonctionnalités de .NET Core et du langage C#.</span><span class="sxs-lookup"><span data-stu-id="3886a-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="3886a-105">Vous apprendrez à :</span><span class="sxs-lookup"><span data-stu-id="3886a-105">You’ll learn:</span></span>

* <span data-ttu-id="3886a-106">Notions de base du CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3886a-106">The basics of the .NET Core CLI.</span></span>
* <span data-ttu-id="3886a-107">Une présentation des fonctionnalités du langage C#.</span><span class="sxs-lookup"><span data-stu-id="3886a-107">An overview of C# Language features.</span></span>
* <span data-ttu-id="3886a-108">Gestion des dépendances avec NuGet</span><span class="sxs-lookup"><span data-stu-id="3886a-108">Managing dependencies with NuGet</span></span>
* <span data-ttu-id="3886a-109">Communications HTTP</span><span class="sxs-lookup"><span data-stu-id="3886a-109">HTTP Communications</span></span>
* <span data-ttu-id="3886a-110">Traitement des informations JSON</span><span class="sxs-lookup"><span data-stu-id="3886a-110">Processing JSON information</span></span>
* <span data-ttu-id="3886a-111">Gestion de la configuration avec les attributs.</span><span class="sxs-lookup"><span data-stu-id="3886a-111">Managing configuration with Attributes.</span></span>

<span data-ttu-id="3886a-112">Vous allez générer une application qui émet des requêtes HTTP vers un service REST sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="3886a-112">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="3886a-113">Vous lirez des informations au format JSON et convertirez ce paquet JSON en objets C#.</span><span class="sxs-lookup"><span data-stu-id="3886a-113">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="3886a-114">Enfin, vous verrez comment travailler avec les objets C#.</span><span class="sxs-lookup"><span data-stu-id="3886a-114">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="3886a-115">Ce didacticiel présente de nombreuses fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="3886a-115">There are many features in this tutorial.</span></span> <span data-ttu-id="3886a-116">Nous allons les construire une par une.</span><span class="sxs-lookup"><span data-stu-id="3886a-116">Let’s build them one by one.</span></span>

<span data-ttu-id="3886a-117">Si vous préférez utiliser l’[exemple final](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) pour cette rubrique, vous pouvez le télécharger.</span><span class="sxs-lookup"><span data-stu-id="3886a-117">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="3886a-118">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#view-and-download-samples).</span><span class="sxs-lookup"><span data-stu-id="3886a-118">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3886a-119">Prérequis</span><span class="sxs-lookup"><span data-stu-id="3886a-119">Prerequisites</span></span>

<span data-ttu-id="3886a-120">Vous devez configurer votre ordinateur pour exécuter .NET core.</span><span class="sxs-lookup"><span data-stu-id="3886a-120">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="3886a-121">Consultez les instructions d’installation à la page [Téléchargements .NET Core](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="3886a-121">You can find the installation instructions on the [.NET Core Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="3886a-122">Vous pouvez exécuter cette application sur Windows, Linux, Mac OS ou dans un conteneur Docker.</span><span class="sxs-lookup"><span data-stu-id="3886a-122">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="3886a-123">Vous devez installer l’éditeur de code de votre choix.</span><span class="sxs-lookup"><span data-stu-id="3886a-123">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="3886a-124">Les descriptions ci-dessous utilisent [Visual Studio Code](https://code.visualstudio.com/), qui est un éditeur multiplateforme open source.</span><span class="sxs-lookup"><span data-stu-id="3886a-124">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="3886a-125">Cependant, vous pouvez utiliser les outils avec lesquels vous êtes le plus à l’aise.</span><span class="sxs-lookup"><span data-stu-id="3886a-125">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="3886a-126">Création de l’application</span><span class="sxs-lookup"><span data-stu-id="3886a-126">Create the Application</span></span>

<span data-ttu-id="3886a-127">La première étape consiste à créer une nouvelle application.</span><span class="sxs-lookup"><span data-stu-id="3886a-127">The first step is to create a new application.</span></span> <span data-ttu-id="3886a-128">Ouvrez une invite de commandes et créez un nouveau répertoire pour votre application.</span><span class="sxs-lookup"><span data-stu-id="3886a-128">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="3886a-129">Réglez-le comme répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="3886a-129">Make that the current directory.</span></span> <span data-ttu-id="3886a-130">Entrez la commande suivante dans la fenêtre de console :</span><span class="sxs-lookup"><span data-stu-id="3886a-130">Enter the following command in a console window:</span></span>

```dotnetcli
dotnet new console --name WebAPIClient
```

<span data-ttu-id="3886a-131">Elle crée les fichiers de démarrage d’une application « Hello World » de base.</span><span class="sxs-lookup"><span data-stu-id="3886a-131">This creates the starter files for a basic "Hello World" application.</span></span> <span data-ttu-id="3886a-132">Le nom du projet est « WebAPIClient ».</span><span class="sxs-lookup"><span data-stu-id="3886a-132">The project name is "WebAPIClient".</span></span> <span data-ttu-id="3886a-133">Comme il s’agit d’un nouveau projet, aucune des dépendances n’est en place.</span><span class="sxs-lookup"><span data-stu-id="3886a-133">As this is a new project, none of the dependencies are in place.</span></span> <span data-ttu-id="3886a-134">La première exécution télécharge l’infrastructure .NET Core, installe un certificat de développement et exécute le gestionnaire de package NuGet pour restaurer les dépendances manquantes.</span><span class="sxs-lookup"><span data-stu-id="3886a-134">The first run will download the .NET Core framework, install a development certificate, and run the NuGet package manager to restore missing dependencies.</span></span>

<span data-ttu-id="3886a-135">Avant de commencer à apporter des modifications, `cd` dans le répertoire « WebAPIClient » et tapez `dotnet run` ([Voir la remarque](#dotnet-restore-note)) à l’invite de commandes pour exécuter votre application.</span><span class="sxs-lookup"><span data-stu-id="3886a-135">Before you start making modifications, `cd` into the "WebAPIClient" directory and type `dotnet run` ([see note](#dotnet-restore-note)) at the command prompt to run your application.</span></span> <span data-ttu-id="3886a-136">`dotnet run` effectue automatiquement `dotnet restore` s’il manque des dépendances dans votre environnement.</span><span class="sxs-lookup"><span data-stu-id="3886a-136">`dotnet run` automatically performs `dotnet restore` if your environment is missing dependencies.</span></span> <span data-ttu-id="3886a-137">Il effectue également `dotnet build` si votre application doit être regénérée.</span><span class="sxs-lookup"><span data-stu-id="3886a-137">It also performs `dotnet build` if your application needs to be rebuilt.</span></span>
<span data-ttu-id="3886a-138">Après la configuration initiale, vous devez uniquement exécuter `dotnet restore` ou `dotnet build` quand cela est pertinent pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="3886a-138">After your initial setup, you will only need to run `dotnet restore` or `dotnet build` when it makes sense for your project.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="3886a-139">Ajout de nouvelles dépendances</span><span class="sxs-lookup"><span data-stu-id="3886a-139">Adding New Dependencies</span></span>

<span data-ttu-id="3886a-140">L’un des objectifs de conception clés de .NET Core consiste à réduire la taille de l’installation .NET.</span><span class="sxs-lookup"><span data-stu-id="3886a-140">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="3886a-141">Si une application a besoin de bibliothèques supplémentaires pour certaines de ses fonctionnalités, vous ajoutez ces dépendances dans votre fichier projet (\*.csproj) en C#.</span><span class="sxs-lookup"><span data-stu-id="3886a-141">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="3886a-142">Pour notre exemple, vous devez ajouter le `System.Runtime.Serialization.Json` package, afin que votre application puisse traiter les réponses JSON.</span><span class="sxs-lookup"><span data-stu-id="3886a-142">For our example, you'll need to add the `System.Runtime.Serialization.Json` package, so your application can process JSON responses.</span></span>

<span data-ttu-id="3886a-143">Vous aurez besoin du `System.Runtime.Serialization.Json` package pour cette application.</span><span class="sxs-lookup"><span data-stu-id="3886a-143">You'll need the `System.Runtime.Serialization.Json` package for this application.</span></span> <span data-ttu-id="3886a-144">Ajoutez-le à votre projet en exécutant la commande [CLI .net](../../core/tools/dotnet-add-package.md) suivante :</span><span class="sxs-lookup"><span data-stu-id="3886a-144">Add it to your project by running the following [.NET CLI](../../core/tools/dotnet-add-package.md) command:</span></span>

```dotnetcli
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a><span data-ttu-id="3886a-145">Effectuer des requêtes web</span><span class="sxs-lookup"><span data-stu-id="3886a-145">Making Web Requests</span></span>

<span data-ttu-id="3886a-146">Vous êtes maintenant prêt à commencer la récupération des données à partir du web.</span><span class="sxs-lookup"><span data-stu-id="3886a-146">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="3886a-147">Dans cette application, vous obtiendrez des informations à partir de [l’API GitHub](https://developer.github.com/v3/).</span><span class="sxs-lookup"><span data-stu-id="3886a-147">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="3886a-148">Nous allons lire des informations sur les projets couverts par la [.NET Foundation](https://www.dotnetfoundation.org/).</span><span class="sxs-lookup"><span data-stu-id="3886a-148">Let's read information about the projects under the [.NET Foundation](https://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="3886a-149">Vous allez commencer par créer la demande à l’API GitHub pour récupérer des informations sur les projets.</span><span class="sxs-lookup"><span data-stu-id="3886a-149">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="3886a-150">Vous allez utiliser le point de terminaison <https://api.github.com/orgs/dotnet/repos>.</span><span class="sxs-lookup"><span data-stu-id="3886a-150">The endpoint you'll use is: <https://api.github.com/orgs/dotnet/repos>.</span></span> <span data-ttu-id="3886a-151">Vous souhaitez récupérer toutes les informations sur ces projets, vous allez donc utiliser une requête HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="3886a-151">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="3886a-152">Votre navigateur utilise également les requêtes HTTP GET, vous pouvez donc coller cette URL dans votre navigateur pour voir les informations que vous recevez et traitez.</span><span class="sxs-lookup"><span data-stu-id="3886a-152">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="3886a-153">Vous utilisez la classe <xref:System.Net.Http.HttpClient> pour effectuer des requêtes web.</span><span class="sxs-lookup"><span data-stu-id="3886a-153">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="3886a-154">Comme toutes les API .NET modernes, <xref:System.Net.Http.HttpClient> prend en charge uniquement les méthodes async pour ses API les plus anciennes.</span><span class="sxs-lookup"><span data-stu-id="3886a-154">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="3886a-155">Commencez par créer une méthode async.</span><span class="sxs-lookup"><span data-stu-id="3886a-155">Start by making an async method.</span></span> <span data-ttu-id="3886a-156">Vous allez effectuer l’implémentation lors de la création des fonctionnalités de l’application.</span><span class="sxs-lookup"><span data-stu-id="3886a-156">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="3886a-157">Commencez en ouvrant le fichier `program.cs` dans votre répertoire de projet et l’ajout de la méthode suivante à la classe `Program` :</span><span class="sxs-lookup"><span data-stu-id="3886a-157">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
}
```

<span data-ttu-id="3886a-158">Vous devez ajouter une `using` directive en haut de votre `Main` méthode afin que le compilateur C# reconnaisse le <xref:System.Threading.Tasks.Task> type :</span><span class="sxs-lookup"><span data-stu-id="3886a-158">You'll need to add a `using` directive at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="3886a-159">Si vous générez votre projet à ce stade, vous obtiendrez un avertissement généré pour cette méthode, car elle ne contient aucun opérateur `await` et s’exécute de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="3886a-159">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="3886a-160">Ignorez-le pour le moment. vous ajouterez des opérateurs `await` lorsque vous remplirez la méthode.</span><span class="sxs-lookup"><span data-stu-id="3886a-160">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="3886a-161">Ensuite, mettez à jour la `Main` méthode pour appeler la `ProcessRepositories` méthode.</span><span class="sxs-lookup"><span data-stu-id="3886a-161">Next, update the `Main` method to call the `ProcessRepositories` method.</span></span> <span data-ttu-id="3886a-162">La `ProcessRepositories` méthode retourne une tâche et vous ne devez pas quitter le programme avant que cette tâche se termine.</span><span class="sxs-lookup"><span data-stu-id="3886a-162">The `ProcessRepositories` method returns a task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="3886a-163">Par conséquent, vous devez modifier la signature de `Main` .</span><span class="sxs-lookup"><span data-stu-id="3886a-163">Therefore, you must change the signature of `Main`.</span></span> <span data-ttu-id="3886a-164">Ajoutez le `async` modificateur, puis remplacez le type de retour par `Task` .</span><span class="sxs-lookup"><span data-stu-id="3886a-164">Add the `async` modifier, and change the return type to `Task`.</span></span> <span data-ttu-id="3886a-165">Ensuite, dans le corps de la méthode, ajoutez un appel à `ProcessRepositories` .</span><span class="sxs-lookup"><span data-stu-id="3886a-165">Then, in the body of the method, add a call to `ProcessRepositories`.</span></span> <span data-ttu-id="3886a-166">Ajoutez le `await` mot clé à cet appel de méthode :</span><span class="sxs-lookup"><span data-stu-id="3886a-166">Add the `await` keyword to that method call:</span></span>

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

<span data-ttu-id="3886a-167">À présent, vous disposez d’un programme qui ne fait rien, mais le fait de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="3886a-167">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="3886a-168">Nous allons l’améliorer.</span><span class="sxs-lookup"><span data-stu-id="3886a-168">Let's improve it.</span></span>

<span data-ttu-id="3886a-169">Tout d’abord, vous avez besoin d’un objet pouvant récupérer des données à partir du web ; pour ce faire, vous pouvez utiliser <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="3886a-169">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="3886a-170">Cet objet gère la demande et les réponses.</span><span class="sxs-lookup"><span data-stu-id="3886a-170">This object handles the request and the responses.</span></span> <span data-ttu-id="3886a-171">Instanciez une instance unique de ce type dans la `Program` classe à l’intérieur du fichier *Program.cs* .</span><span class="sxs-lookup"><span data-stu-id="3886a-171">Instantiate a single instance of that type in the `Program` class inside the *Program.cs* file.</span></span>

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

<span data-ttu-id="3886a-172">Revenons à la méthode `ProcessRepositories` et créons sa première version :</span><span class="sxs-lookup"><span data-stu-id="3886a-172">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="3886a-173">Pour compiler, vous devez également ajouter deux nouvelles `using` directives en haut du fichier :</span><span class="sxs-lookup"><span data-stu-id="3886a-173">You'll need to also add two new `using` directives at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="3886a-174">Cette première version effectue une requête web pour lire la liste de tous les dépôts de l’organisation dotnet foundation.</span><span class="sxs-lookup"><span data-stu-id="3886a-174">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="3886a-175">(L’ID GitHub de la .NET Foundation est 'dotnet').</span><span class="sxs-lookup"><span data-stu-id="3886a-175">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="3886a-176">Les premières lignes configurent <xref:System.Net.Http.HttpClient> pour cette requête.</span><span class="sxs-lookup"><span data-stu-id="3886a-176">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="3886a-177">Tout d’abord, il est configuré pour accepter les réponses JSON de GitHub.</span><span class="sxs-lookup"><span data-stu-id="3886a-177">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="3886a-178">Ce format est simplement du JSON.</span><span class="sxs-lookup"><span data-stu-id="3886a-178">This format is simply JSON.</span></span> <span data-ttu-id="3886a-179">La ligne suivante ajoute un en-tête d’agent utilisateur à toutes les requêtes à partir de cet objet.</span><span class="sxs-lookup"><span data-stu-id="3886a-179">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="3886a-180">Ces deux en-têtes sont vérifiés par le code du serveur GitHub et sont nécessaires pour récupérer des informations à partir de GitHub.</span><span class="sxs-lookup"><span data-stu-id="3886a-180">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="3886a-181">Une fois que vous avez configuré le <xref:System.Net.Http.HttpClient>, effectuez une requête web et récupérez la réponse.</span><span class="sxs-lookup"><span data-stu-id="3886a-181">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="3886a-182">Dans cette première version, vous utilisez la méthode pratique <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3886a-182">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="3886a-183">Cette méthode démarre une tâche qui effectue la requête web, et, lorsque la demande est renvoyée, lit le flux de réponse puis extrait le contenu à partir du flux.</span><span class="sxs-lookup"><span data-stu-id="3886a-183">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="3886a-184">Le corps de la réponse est renvoyé en tant que <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3886a-184">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="3886a-185">La chaîne est disponible lorsque la tâche est terminée.</span><span class="sxs-lookup"><span data-stu-id="3886a-185">The string is available when the task completes.</span></span>

<span data-ttu-id="3886a-186">Les deux dernières lignes de cette méthode attendent cette tâche et impriment la réponse dans la console.</span><span class="sxs-lookup"><span data-stu-id="3886a-186">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="3886a-187">Générez l'application et exécutez-la.</span><span class="sxs-lookup"><span data-stu-id="3886a-187">Build the app, and run it.</span></span> <span data-ttu-id="3886a-188">L’avertissement de génération a disparu maintenant, car `ProcessRepositories` contient maintenant un opérateur `await`.</span><span class="sxs-lookup"><span data-stu-id="3886a-188">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="3886a-189">Vous verrez long affichage de texte au format JSON.</span><span class="sxs-lookup"><span data-stu-id="3886a-189">You'll see a long display of JSON formatted text.</span></span>

## <a name="processing-the-json-result"></a><span data-ttu-id="3886a-190">Traitement du résultat JSON</span><span class="sxs-lookup"><span data-stu-id="3886a-190">Processing the JSON Result</span></span>

<span data-ttu-id="3886a-191">À ce stade, vous avez écrit le code pour récupérer une réponse à partir d’un serveur web et afficher le texte contenu dans cette réponse.</span><span class="sxs-lookup"><span data-stu-id="3886a-191">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="3886a-192">Ensuite, nous allons convertir cette réponse JSON en objets C#.</span><span class="sxs-lookup"><span data-stu-id="3886a-192">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="3886a-193">La <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> classe sérialise les objets au format JSON et désérialise JSON en objets.</span><span class="sxs-lookup"><span data-stu-id="3886a-193">The <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> class serializes objects to JSON and deserializes JSON into objects.</span></span> <span data-ttu-id="3886a-194">Commencez par définir une classe pour représenter l' `repo` objet JSON retourné à partir de l’API GitHub :</span><span class="sxs-lookup"><span data-stu-id="3886a-194">Start by defining a class to represent the `repo` JSON object returned from the GitHub API:</span></span>

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

<span data-ttu-id="3886a-195">Placez le code ci-dessus dans un fichier nommé « repo.cs ».</span><span class="sxs-lookup"><span data-stu-id="3886a-195">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="3886a-196">Cette version de la classe représente le chemin d’accès le plus simple pour traiter les données JSON.</span><span class="sxs-lookup"><span data-stu-id="3886a-196">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="3886a-197">Le nom de classe et le nom du membre correspondent aux noms utilisés dans le paquet JSON, au lieu des conventions C# suivantes.</span><span class="sxs-lookup"><span data-stu-id="3886a-197">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="3886a-198">Vous allez corriger cela en fournissant des attributs de configuration ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="3886a-198">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="3886a-199">Cette classe décrit une autre fonctionnalité importante de la sérialisation et de désérialisation JSON : tous les champs dans le paquet JSON font partie de cette classe.</span><span class="sxs-lookup"><span data-stu-id="3886a-199">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="3886a-200">Le sérialiseur JSON ignore les informations qui ne sont pas incluses dans le type de classe utilisé.</span><span class="sxs-lookup"><span data-stu-id="3886a-200">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="3886a-201">Cette fonctionnalité facilite la création de types qui fonctionnent avec uniquement un sous-ensemble des champs dans le paquet JSON.</span><span class="sxs-lookup"><span data-stu-id="3886a-201">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="3886a-202">Maintenant que vous avez créé le type, nous allons le désérialiser.</span><span class="sxs-lookup"><span data-stu-id="3886a-202">Now that you've created the type, let's deserialize it.</span></span>

<span data-ttu-id="3886a-203">Ensuite, vous utiliserez le sérialiseur pour convertir le JSON en objets C#.</span><span class="sxs-lookup"><span data-stu-id="3886a-203">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="3886a-204">Remplacez l’appel à <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> dans votre `ProcessRepositories` méthode par les lignes suivantes :</span><span class="sxs-lookup"><span data-stu-id="3886a-204">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
```

<span data-ttu-id="3886a-205">Vous utilisez de nouveaux espaces de noms. vous devez donc les ajouter en haut du fichier :</span><span class="sxs-lookup"><span data-stu-id="3886a-205">You're using new namespaces, so you'll need to add it at the top of the file as well:</span></span>

```csharp
using System.Collections.Generic;
using System.Text.Json;
```

<span data-ttu-id="3886a-206">Notez que vous utilisez maintenant <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> au lieu de <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="3886a-206">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="3886a-207">Le sérialiseur utilise un flux plutôt qu’une chaîne comme source.</span><span class="sxs-lookup"><span data-stu-id="3886a-207">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="3886a-208">Nous allons expliquer quelques-unes des fonctionnalités du langage C# qui sont utilisées dans la deuxième ligne de l’extrait de code précédent.</span><span class="sxs-lookup"><span data-stu-id="3886a-208">Let's explain a couple features of the C# language that are being used in the second line of the preceding code snippet.</span></span> <span data-ttu-id="3886a-209">Le premier argument de <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> est une `await` expression.</span><span class="sxs-lookup"><span data-stu-id="3886a-209">The first argument to <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> is an `await` expression.</span></span> <span data-ttu-id="3886a-210">(Les deux autres paramètres sont facultatifs et sont omis dans l’extrait de code.) Les expressions await peuvent apparaître presque n’importe où dans votre code, même si vous ne les avez vu que dans le cadre d’une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="3886a-210">(The other two parameters are optional and are omitted in the code snippet.) Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span> <span data-ttu-id="3886a-211">La `Deserialize` méthode est *générique*, ce qui signifie que vous devez fournir des arguments de type pour les types d’objets qui doivent être créés à partir du texte JSON.</span><span class="sxs-lookup"><span data-stu-id="3886a-211">The `Deserialize` method is *generic*, which means you must supply type arguments for what kind of objects should be created from the JSON text.</span></span> <span data-ttu-id="3886a-212">Dans cet exemple, vous désérialisez vers un `List<Repository>` , qui est un autre objet générique, le <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3886a-212">In this example, you're deserializing to a `List<Repository>`, which is another generic object, the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3886a-213">La `List<>` classe stocke une collection d’objets.</span><span class="sxs-lookup"><span data-stu-id="3886a-213">The `List<>` class stores a collection of objects.</span></span> <span data-ttu-id="3886a-214">L’argument de type déclare le type des objets stockés dans le `List<>` .</span><span class="sxs-lookup"><span data-stu-id="3886a-214">The type argument declares the type of objects stored in the `List<>`.</span></span> <span data-ttu-id="3886a-215">Le texte JSON représente une collection d’objets référentiel, donc l’argument de type est `Repository` .</span><span class="sxs-lookup"><span data-stu-id="3886a-215">The JSON text represents a collection of repo objects, so the type argument is `Repository`.</span></span>

<span data-ttu-id="3886a-216">Nous en avons presque terminé avec cette section.</span><span class="sxs-lookup"><span data-stu-id="3886a-216">You're almost done with this section.</span></span> <span data-ttu-id="3886a-217">Maintenant que vous avez converti le JSON en objets C#, nous allons afficher le nom de chaque dépôt.</span><span class="sxs-lookup"><span data-stu-id="3886a-217">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="3886a-218">Remplacez les lignes :</span><span class="sxs-lookup"><span data-stu-id="3886a-218">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="3886a-219">avec les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="3886a-219">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="3886a-220">Compilez et exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="3886a-220">Compile and run the application.</span></span> <span data-ttu-id="3886a-221">Cela affichera les noms des espaces de stockage qui font partie de la .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="3886a-221">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="3886a-222">Contrôle de la sérialisation</span><span class="sxs-lookup"><span data-stu-id="3886a-222">Controlling Serialization</span></span>

<span data-ttu-id="3886a-223">Avant d’ajouter d’autres fonctionnalités, nous allons traiter la propriété à l' `name` aide de l' `[JsonPropertyName]` attribut.</span><span class="sxs-lookup"><span data-stu-id="3886a-223">Before you add more features, let's address the `name` property by using the `[JsonPropertyName]` attribute.</span></span> <span data-ttu-id="3886a-224">Apportez les modifications suivantes à la déclaration du champ `name` dans repo.cs :</span><span class="sxs-lookup"><span data-stu-id="3886a-224">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

<span data-ttu-id="3886a-225">Pour utiliser `[JsonPropertyName]` l’attribut, vous devez ajouter l' <xref:System.Text.Json.Serialization> espace de noms aux `using` directives :</span><span class="sxs-lookup"><span data-stu-id="3886a-225">To use `[JsonPropertyName]` attribute, you will need to add the <xref:System.Text.Json.Serialization> namespace to the `using` directives:</span></span>

```csharp
using System.Text.Json.Serialization;
```

<span data-ttu-id="3886a-226">Cette modification signifie que vous devez modifier le code qui écrit le nom de chaque dépôt dans program.cs :</span><span class="sxs-lookup"><span data-stu-id="3886a-226">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="3886a-227">Exécutez `dotnet run` pour vérifier que les mappages sont corrects.</span><span class="sxs-lookup"><span data-stu-id="3886a-227">Execute `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="3886a-228">Vous devriez voir la même sortie que précédemment.</span><span class="sxs-lookup"><span data-stu-id="3886a-228">You should see the same output as before.</span></span>

<span data-ttu-id="3886a-229">Nous allons apporter une modification de plus avant d’ajouter de nouvelles fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="3886a-229">Let's make one more change before adding new features.</span></span> <span data-ttu-id="3886a-230">La méthode `ProcessRepositories` peut faire le travail de façon asynchrone et renvoyer une collection des espaces de stockage.</span><span class="sxs-lookup"><span data-stu-id="3886a-230">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="3886a-231">Nous allons renvoyer `List<Repository>` à partir de cette méthode et déplacer le code qui écrit les informations dans la méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="3886a-231">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="3886a-232">Modifiez la signature de `ProcessRepositories` pour retourner une tâche dont le résultat est une liste d’objets `Repository` :</span><span class="sxs-lookup"><span data-stu-id="3886a-232">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="3886a-233">Ensuite, retournez simplement les dépôts après le traitement de la réponse JSON :</span><span class="sxs-lookup"><span data-stu-id="3886a-233">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

<span data-ttu-id="3886a-234">Le compilateur génère l’objet `Task<T>` pour la valeur de retour, car vous avez marqué cette méthode comme `async`.</span><span class="sxs-lookup"><span data-stu-id="3886a-234">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="3886a-235">Ensuite, nous allons modifier la méthode `Main` afin qu’elle capture les résultats et écrive le nom de chaque dépôt dans la console.</span><span class="sxs-lookup"><span data-stu-id="3886a-235">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="3886a-236">Votre méthode `Main` se présente maintenant comme suit :</span><span class="sxs-lookup"><span data-stu-id="3886a-236">Your `Main` method now looks like this:</span></span>

```csharp
public static async Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a><span data-ttu-id="3886a-237">Lire plus d'informations</span><span class="sxs-lookup"><span data-stu-id="3886a-237">Reading More Information</span></span>

<span data-ttu-id="3886a-238">Terminons par le traitement d’un certain nombre de propriétés dans le paquet JSON envoyé à partir de l’API GitHub.</span><span class="sxs-lookup"><span data-stu-id="3886a-238">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="3886a-239">Vous ne voudrez pas récupérer tous les éléments, mais ajouter quelques propriétés vous permettra de découvrir d’autres fonctionnalités du langage C#.</span><span class="sxs-lookup"><span data-stu-id="3886a-239">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="3886a-240">Commençons par ajouter quelques autres types simples à la définition de classe `Repository`.</span><span class="sxs-lookup"><span data-stu-id="3886a-240">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="3886a-241">Ajoutez ces propriétés à cette classe :</span><span class="sxs-lookup"><span data-stu-id="3886a-241">Add these properties to that class:</span></span>

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

<span data-ttu-id="3886a-242">Ces propriétés ont intégré des conversions intégrées du type chaîne (c’est ce que contiennent les paquets JSON) vers le type cible.</span><span class="sxs-lookup"><span data-stu-id="3886a-242">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="3886a-243">Le type <xref:System.Uri> peut être nouveau pour vous.</span><span class="sxs-lookup"><span data-stu-id="3886a-243">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="3886a-244">Il représente un URI, ou dans ce cas, une URL.</span><span class="sxs-lookup"><span data-stu-id="3886a-244">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="3886a-245">Dans le cas des types `Uri` et `int`, si le paquet JSON contient des données qui ne sont pas convertibles dans le type cible, l’action de sérialisation lèvera une exception.</span><span class="sxs-lookup"><span data-stu-id="3886a-245">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="3886a-246">Une fois que vous avez ajouté cela, mettez à jour la méthode `Main` pour afficher ces éléments :</span><span class="sxs-lookup"><span data-stu-id="3886a-246">Once you've added these, update the `Main` method to display those elements:</span></span>

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

<span data-ttu-id="3886a-247">Dans la dernière étape, nous allons ajouter les informations de la dernière opération Push.</span><span class="sxs-lookup"><span data-stu-id="3886a-247">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="3886a-248">Ces informations sont formatées de cette façon dans la réponse JSON :</span><span class="sxs-lookup"><span data-stu-id="3886a-248">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="3886a-249">Ce format est au format de temps universel coordonné (UTC). vous obtiendrez donc une <xref:System.DateTime> valeur dont la <xref:System.DateTime.Kind%2A> propriété est <xref:System.DateTimeKind.Utc> .</span><span class="sxs-lookup"><span data-stu-id="3886a-249">That format is in Coordinated Universal Time (UTC) so you'll get a <xref:System.DateTime> value whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Utc>.</span></span> <span data-ttu-id="3886a-250">Si vous préférez une date représentée dans votre fuseau horaire, vous devez écrire une méthode de conversion personnalisée.</span><span class="sxs-lookup"><span data-stu-id="3886a-250">If you prefer a date represented in your time zone, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="3886a-251">Tout d’abord, définissez une `public` propriété qui contiendra la représentation UTC de la date et de l’heure dans votre `Repository` classe et une `LastPush` `readonly` propriété qui retourne la date convertie en heure locale :</span><span class="sxs-lookup"><span data-stu-id="3886a-251">First, define a `public` property that will hold the UTC representation of the date and time in your `Repository` class and a `LastPush` `readonly` property that returns the date converted to local time:</span></span>

```csharp
[JsonPropertyName("pushed_at")]
public DateTime LastPushUtc { get; set; }

public DateTime LastPush => LastPushUtc.ToLocalTime();
```

<span data-ttu-id="3886a-252">Passons en revue les nouvelles constructions que nous venons de définir.</span><span class="sxs-lookup"><span data-stu-id="3886a-252">Let's go over the new constructs we just defined.</span></span> <span data-ttu-id="3886a-253">La `LastPush` propriété est définie à l’aide d’un *membre à expression nulle* pour l' `get` accesseur.</span><span class="sxs-lookup"><span data-stu-id="3886a-253">The `LastPush` property is defined using an *expression-bodied member* for the `get` accessor.</span></span> <span data-ttu-id="3886a-254">Il n'existe aucun accesseur `set`.</span><span class="sxs-lookup"><span data-stu-id="3886a-254">There is no `set` accessor.</span></span> <span data-ttu-id="3886a-255">L’omission de l' `set` accesseur est la façon dont vous définissez une propriété *en lecture seule* en C#.</span><span class="sxs-lookup"><span data-stu-id="3886a-255">Omitting the `set` accessor is how you define a *read-only* property in C#.</span></span> <span data-ttu-id="3886a-256">(Oui, vous pouvez créer des propriétés *en écriture seule* en C#, mais leur intérêt est limité.)</span><span class="sxs-lookup"><span data-stu-id="3886a-256">(Yes, you can create *write-only* properties in C#, but their value is limited.)</span></span>

<span data-ttu-id="3886a-257">Enfin, ajoutez une dernière instruction de sortie dans la console et vous êtes prêt à générer et exécuter de nouveau cette application :</span><span class="sxs-lookup"><span data-stu-id="3886a-257">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="3886a-258">Votre version doit maintenant correspondre à l’[exemple terminé](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="3886a-258">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>

## <a name="conclusion"></a><span data-ttu-id="3886a-259">Conclusion</span><span class="sxs-lookup"><span data-stu-id="3886a-259">Conclusion</span></span>

<span data-ttu-id="3886a-260">Ce didacticiel vous a montré comment effectuer des demandes web, analyser le résultat et afficher les propriétés de ces résultats.</span><span class="sxs-lookup"><span data-stu-id="3886a-260">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="3886a-261">Vous avez également ajouté de nouveaux packages en tant que dépendances dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="3886a-261">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="3886a-262">Vous avez vu certaines des fonctionnalités du langage C# qui prennent en charge des techniques orientées objet.</span><span class="sxs-lookup"><span data-stu-id="3886a-262">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
