---
title: Applications sans serveur Azure Functions
description: Azure Functions offre des fonctionnalités sans serveur dans plusieursC#langues (, JavaScript, Java) et des plateformes pour fournir un code de mise à l’échelle instantanée piloté par les événements.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 8764e6a33f3fdd53e60fa767d0fb584a9c07de7e
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920967"
---
# <a name="azure-functions"></a><span data-ttu-id="9f485-103">Azure Functions</span><span class="sxs-lookup"><span data-stu-id="9f485-103">Azure Functions</span></span>

<span data-ttu-id="9f485-104">Azure Functions offre une expérience de calcul sans serveur.</span><span class="sxs-lookup"><span data-stu-id="9f485-104">Azure functions provide a serverless compute experience.</span></span> <span data-ttu-id="9f485-105">Une fonction est appelée par un *déclencheur* (comme l’accès à un point de terminaison http ou une minuterie) et exécute un bloc de code ou une logique métier.</span><span class="sxs-lookup"><span data-stu-id="9f485-105">A function is invoked by a *trigger* (such as access to an HTTP endpoint or a timer) and executes a block of code or business logic.</span></span> <span data-ttu-id="9f485-106">Les fonctions prennent également en charge des *liaisons* spécialisées qui se connectent à des ressources telles que le stockage et les files d’attente.</span><span class="sxs-lookup"><span data-stu-id="9f485-106">Functions also support specialized *bindings* that connect to resources like storage and queues.</span></span>

![Logo Azure Functions](./media/azure-functions-logo.png)

<span data-ttu-id="9f485-108">Il existe deux versions de l’infrastructure Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="9f485-108">There are two versions of the Azure Functions framework.</span></span> <span data-ttu-id="9f485-109">La version héritée prend en charge la .NET Framework complète et le nouveau Runtime prend en charge les applications .NET Core multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="9f485-109">The legacy version supports the full .NET Framework and the new runtime supports cross-platform .NET Core applications.</span></span> <span data-ttu-id="9f485-110">Des langages C# supplémentaires, tels que F#JavaScript, et Java, sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="9f485-110">Additional languages besides C# such as JavaScript, F#, and Java are supported.</span></span> <span data-ttu-id="9f485-111">Les fonctions créées dans le portail fournissent une syntaxe de script riche.</span><span class="sxs-lookup"><span data-stu-id="9f485-111">Functions created in the portal provide a rich scripting syntax.</span></span> <span data-ttu-id="9f485-112">Les fonctions créées en tant que projets autonomes peuvent être déployées avec une prise en charge complète des plateformes et des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="9f485-112">Functions created as standalone projects can be deployed with full platform support and capabilities.</span></span>

<span data-ttu-id="9f485-113">Pour plus d’informations, consultez [la documentation Azure Functions](https://docs.microsoft.com/azure/azure-functions).</span><span class="sxs-lookup"><span data-stu-id="9f485-113">For more information, see [Azure Functions documentation](https://docs.microsoft.com/azure/azure-functions).</span></span>

## <a name="functions-v1-vs-v2"></a><span data-ttu-id="9f485-114">Fonctions v1 et v2</span><span class="sxs-lookup"><span data-stu-id="9f485-114">Functions v1 vs. v2</span></span>

<span data-ttu-id="9f485-115">Il existe deux versions du Azure Functions Runtime : 1. x et 2. x.</span><span class="sxs-lookup"><span data-stu-id="9f485-115">There are two versions of the Azure Functions runtime: 1.x and 2.x.</span></span> <span data-ttu-id="9f485-116">La version 1. x est généralement disponible (GA).</span><span class="sxs-lookup"><span data-stu-id="9f485-116">Version 1.x is generally available (GA).</span></span> <span data-ttu-id="9f485-117">Il prend en charge le développement .NET à partir du portail ou des ordinateurs Windows et utilise le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9f485-117">It supports .NET development from the portal or Windows machines and uses the .NET Framework.</span></span> <span data-ttu-id="9f485-118">1. x prend C#en charge, JavaScript F#et, avec prise en charge expérimentale de Python, php, machine à écrire, batch, bash et PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9f485-118">1.x supports C#, JavaScript, and F#, with experimental support for Python, PHP, TypeScript, Batch, Bash, and PowerShell.</span></span>

<span data-ttu-id="9f485-119">La [version 2. x est également mis à la disposition générale dès maintenant](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/).</span><span class="sxs-lookup"><span data-stu-id="9f485-119">[Version 2.x is also generally available now](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/).</span></span> <span data-ttu-id="9f485-120">Il s’appuie sur .NET Core et prend en charge le développement multiplateforme sur des ordinateurs Windows, macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="9f485-120">It leverages .NET Core and supports cross-platform development on Windows, macOS, and Linux machines.</span></span> <span data-ttu-id="9f485-121">2. x ajoute une prise en charge de première classe pour Java, mais ne prend pas encore en charge directement les langages expérimentaux.</span><span class="sxs-lookup"><span data-stu-id="9f485-121">2.x adds first-class support for Java but doesn't yet directly support any of the experimental languages.</span></span> <span data-ttu-id="9f485-122">La version 2. x utilise un nouveau modèle d’extensibilité de liaison qui active des extensions tierces à la plateforme, un contrôle de version indépendant des liaisons et un environnement d’exécution plus rationalisé.</span><span class="sxs-lookup"><span data-stu-id="9f485-122">Version 2.x uses a new binding extensibility model that enables third-party extensions to the platform, independent versioning of bindings, and a more streamlined execution environment.</span></span>

> <span data-ttu-id="9f485-123">**Il existe un problème connu dans 1. x avec [la prise en charge de la redirection de liaison](https://github.com/Azure/azure-functions-host/issues/992).**</span><span class="sxs-lookup"><span data-stu-id="9f485-123">**There is a known issue in 1.x with [binding redirect support](https://github.com/Azure/azure-functions-host/issues/992).**</span></span> <span data-ttu-id="9f485-124">Le problème est spécifique au développement .NET.</span><span class="sxs-lookup"><span data-stu-id="9f485-124">The issue is specific to .NET development.</span></span> <span data-ttu-id="9f485-125">Les projets avec des dépendances sur des bibliothèques qui sont une version différente des bibliothèques incluses dans le runtime sont affectés.</span><span class="sxs-lookup"><span data-stu-id="9f485-125">Projects with dependencies on libraries that are a different version from the libraries included in the runtime are impacted.</span></span> <span data-ttu-id="9f485-126">L’équipe Functions s’est engagée à créer une progression concrète sur le problème.</span><span class="sxs-lookup"><span data-stu-id="9f485-126">The functions team has committed to making concrete progress on the problem.</span></span> <span data-ttu-id="9f485-127">L’équipe traitera les redirections de liaison dans 2. x avant de passer à la mise à la disposition générale.</span><span class="sxs-lookup"><span data-stu-id="9f485-127">The team will address binding redirects in 2.x before it goes into general availability.</span></span> <span data-ttu-id="9f485-128">La déclaration officielle de l’équipe avec des correctifs suggérés et des solutions de contournement est disponible ici : [résolution de l’assembly dans Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).</span><span class="sxs-lookup"><span data-stu-id="9f485-128">The official team statement with suggested fixes and workarounds is available here: [Assembly resolution in Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).</span></span>

<span data-ttu-id="9f485-129">Pour plus d’informations, consultez [comparer 1. x et 2. x](https://docs.microsoft.com/azure/azure-functions/functions-versions).</span><span class="sxs-lookup"><span data-stu-id="9f485-129">For more information, see [Compare 1.x and 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).</span></span>

## <a name="programming-language-support"></a><span data-ttu-id="9f485-130">Prise en charge des langages de programmation</span><span class="sxs-lookup"><span data-stu-id="9f485-130">Programming language support</span></span>

<span data-ttu-id="9f485-131">Les langues suivantes sont prises en charge dans General Availability (GA), preview ou expérimental.</span><span class="sxs-lookup"><span data-stu-id="9f485-131">The following languages are supported either in general availability (GA), preview, or experimental.</span></span>

|<span data-ttu-id="9f485-132">Language</span><span class="sxs-lookup"><span data-stu-id="9f485-132">Language</span></span>      |<span data-ttu-id="9f485-133">1.x</span><span class="sxs-lookup"><span data-stu-id="9f485-133">1.x</span></span>         |<span data-ttu-id="9f485-134">2.x</span><span class="sxs-lookup"><span data-stu-id="9f485-134">2.x</span></span>      |
|--------------|------------|---------|
|<span data-ttu-id="9f485-135">**C#**</span><span class="sxs-lookup"><span data-stu-id="9f485-135">**C#**</span></span>        |<span data-ttu-id="9f485-136">DISPONIBLE</span><span class="sxs-lookup"><span data-stu-id="9f485-136">GA</span></span>          |<span data-ttu-id="9f485-137">Aperçu</span><span class="sxs-lookup"><span data-stu-id="9f485-137">Preview</span></span>  |
|<span data-ttu-id="9f485-138">**JavaScript**</span><span class="sxs-lookup"><span data-stu-id="9f485-138">**JavaScript**</span></span>|<span data-ttu-id="9f485-139">DISPONIBLE</span><span class="sxs-lookup"><span data-stu-id="9f485-139">GA</span></span>          |<span data-ttu-id="9f485-140">Aperçu</span><span class="sxs-lookup"><span data-stu-id="9f485-140">Preview</span></span>  |
|<span data-ttu-id="9f485-141">**F#**</span><span class="sxs-lookup"><span data-stu-id="9f485-141">**F#**</span></span>        |<span data-ttu-id="9f485-142">DISPONIBLE</span><span class="sxs-lookup"><span data-stu-id="9f485-142">GA</span></span>          |         |
|<span data-ttu-id="9f485-143">**Java**</span><span class="sxs-lookup"><span data-stu-id="9f485-143">**Java**</span></span>      |            |<span data-ttu-id="9f485-144">Aperçu</span><span class="sxs-lookup"><span data-stu-id="9f485-144">Preview</span></span>  |
|<span data-ttu-id="9f485-145">**Python**</span><span class="sxs-lookup"><span data-stu-id="9f485-145">**Python**</span></span>    |<span data-ttu-id="9f485-146">Expérimental</span><span class="sxs-lookup"><span data-stu-id="9f485-146">Experimental</span></span>|         |
|<span data-ttu-id="9f485-147">**PHP**</span><span class="sxs-lookup"><span data-stu-id="9f485-147">**PHP**</span></span>       |<span data-ttu-id="9f485-148">Expérimental</span><span class="sxs-lookup"><span data-stu-id="9f485-148">Experimental</span></span>|         |
|<span data-ttu-id="9f485-149">**TypeScript**</span><span class="sxs-lookup"><span data-stu-id="9f485-149">**TypeScript**</span></span>|<span data-ttu-id="9f485-150">Expérimental</span><span class="sxs-lookup"><span data-stu-id="9f485-150">Experimental</span></span>|         |
|<span data-ttu-id="9f485-151">**Batch**</span><span class="sxs-lookup"><span data-stu-id="9f485-151">**Batch**</span></span>     |<span data-ttu-id="9f485-152">Expérimental</span><span class="sxs-lookup"><span data-stu-id="9f485-152">Experimental</span></span>|         |
|<span data-ttu-id="9f485-153">**Anniversaire**</span><span class="sxs-lookup"><span data-stu-id="9f485-153">**Bash**</span></span>      |<span data-ttu-id="9f485-154">Expérimental</span><span class="sxs-lookup"><span data-stu-id="9f485-154">Experimental</span></span>|         |
|<span data-ttu-id="9f485-155">**PowerShell**</span><span class="sxs-lookup"><span data-stu-id="9f485-155">**PowerShell**</span></span>|<span data-ttu-id="9f485-156">Expérimental</span><span class="sxs-lookup"><span data-stu-id="9f485-156">Experimental</span></span>|         |

<span data-ttu-id="9f485-157">Pour plus d’informations, consultez [langues prises en charge](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span><span class="sxs-lookup"><span data-stu-id="9f485-157">For more information, see [Supported languages](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span></span>

## <a name="app-service-plans"></a><span data-ttu-id="9f485-158">Plans App service</span><span class="sxs-lookup"><span data-stu-id="9f485-158">App service plans</span></span>

<span data-ttu-id="9f485-159">Les fonctions sont associées à un *plan App service*.</span><span class="sxs-lookup"><span data-stu-id="9f485-159">Functions are backed by an *app service plan*.</span></span> <span data-ttu-id="9f485-160">Le plan définit les ressources utilisées par l’application functions.</span><span class="sxs-lookup"><span data-stu-id="9f485-160">The plan defines the resources used by the functions app.</span></span> <span data-ttu-id="9f485-161">Vous pouvez affecter des plans à une région, déterminer la taille et le nombre d’ordinateurs virtuels qui seront utilisés, et choisir un niveau tarifaire.</span><span class="sxs-lookup"><span data-stu-id="9f485-161">You can assign plans to a region, determine the size and number of virtual machines that will be used, and pick a pricing tier.</span></span> <span data-ttu-id="9f485-162">Pour une véritable approche sans serveur, les applications de fonction peuvent utiliser le plan de **consommation** .</span><span class="sxs-lookup"><span data-stu-id="9f485-162">For a true serverless approach, function apps may use the **consumption** plan.</span></span> <span data-ttu-id="9f485-163">Le plan de consommation met automatiquement à l’échelle le back end en fonction de la charge.</span><span class="sxs-lookup"><span data-stu-id="9f485-163">The consumption plan will scale the back end automatically based on load.</span></span>

<span data-ttu-id="9f485-164">Pour plus d’informations, consultez [plans App service](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span><span class="sxs-lookup"><span data-stu-id="9f485-164">For more information, see [App service plans](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

## <a name="create-your-first-function"></a><span data-ttu-id="9f485-165">Créer votre première fonction</span><span class="sxs-lookup"><span data-stu-id="9f485-165">Create your first function</span></span>

<span data-ttu-id="9f485-166">Il existe trois méthodes courantes pour créer des applications de fonction.</span><span class="sxs-lookup"><span data-stu-id="9f485-166">There are three common ways you can create function apps.</span></span>

- <span data-ttu-id="9f485-167">Fonctions de script dans le portail.</span><span class="sxs-lookup"><span data-stu-id="9f485-167">Script functions in the portal.</span></span>
- <span data-ttu-id="9f485-168">Créez les ressources nécessaires à l’aide de l’Azure CLI.</span><span class="sxs-lookup"><span data-stu-id="9f485-168">Create the necessary resources using the Azure CLI.</span></span>
- <span data-ttu-id="9f485-169">Créez des fonctions localement à l’aide de votre IDE favori et publiez-les sur Azure.</span><span class="sxs-lookup"><span data-stu-id="9f485-169">Build functions locally using your favorite IDE and publish them to Azure.</span></span>

<span data-ttu-id="9f485-170">Pour plus d’informations sur la création d’une fonction de script dans le portail, consultez [créer votre première fonction dans la portail Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span><span class="sxs-lookup"><span data-stu-id="9f485-170">For more information on creating a scripted function in the portal, see [Create your first function in the Azure portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span></span>

<span data-ttu-id="9f485-171">Pour générer à partir de la Azure CLI, consultez [créer votre première fonction à l’aide de l’Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span><span class="sxs-lookup"><span data-stu-id="9f485-171">To build from the Azure CLI, see [Create your first function using the Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span></span>

<span data-ttu-id="9f485-172">Pour créer une fonction à partir de Visual Studio, consultez [créer votre première fonction à l’aide de Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="9f485-172">To create a function from Visual Studio, see [Create your first function using Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span></span>

## <a name="understand-triggers-and-bindings"></a><span data-ttu-id="9f485-173">Comprendre les déclencheurs et les liaisons</span><span class="sxs-lookup"><span data-stu-id="9f485-173">Understand triggers and bindings</span></span>

<span data-ttu-id="9f485-174">Les fonctions sont appelées par un *déclencheur* et ne peuvent en avoir qu’une seule.</span><span class="sxs-lookup"><span data-stu-id="9f485-174">Functions are invoked by a *trigger* and can have exactly one.</span></span> <span data-ttu-id="9f485-175">Outre l’appel de la fonction, certains déclencheurs servent également de liaisons.</span><span class="sxs-lookup"><span data-stu-id="9f485-175">In addition to invoking the function, certain triggers also serve as bindings.</span></span> <span data-ttu-id="9f485-176">Vous pouvez également définir plusieurs liaisons en plus du déclencheur.</span><span class="sxs-lookup"><span data-stu-id="9f485-176">You may also define multiple bindings in addition to the trigger.</span></span> <span data-ttu-id="9f485-177">Les *liaisons* offrent un moyen déclaratif de connecter des données à votre code.</span><span class="sxs-lookup"><span data-stu-id="9f485-177">*Bindings* provide a declarative way to connect data to your code.</span></span> <span data-ttu-id="9f485-178">Ils peuvent être transmis (entrée) ou recevoir des données (sortie).</span><span class="sxs-lookup"><span data-stu-id="9f485-178">They can be passed in (input) or receive data (output).</span></span> <span data-ttu-id="9f485-179">Les déclencheurs et les liaisons rendent les fonctions faciles à utiliser.</span><span class="sxs-lookup"><span data-stu-id="9f485-179">Triggers and bindings make functions easy to work with.</span></span> <span data-ttu-id="9f485-180">Les liaisons suppriment la surcharge liée à la création manuelle de connexions de base de données ou de système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="9f485-180">Bindings remove the overhead of manually creating database or file system connections.</span></span> <span data-ttu-id="9f485-181">Toutes les informations nécessaires pour les liaisons sont contenues dans un fichier *functions. JSON* spécial pour les scripts ou déclarés avec des attributs dans le code.</span><span class="sxs-lookup"><span data-stu-id="9f485-181">All of the information needed for the bindings is contained in a special *functions.json* file for scripts or declared with attributes in code.</span></span>

<span data-ttu-id="9f485-182">Parmi les déclencheurs les plus courants, citons :</span><span class="sxs-lookup"><span data-stu-id="9f485-182">Some common triggers include:</span></span>

- <span data-ttu-id="9f485-183">Stockage d’objets BLOB : appelez votre fonction lorsqu’un fichier ou un dossier est téléchargé ou modifié dans le stockage.</span><span class="sxs-lookup"><span data-stu-id="9f485-183">Blob Storage: invoke your function when a file or folder is uploaded or changed in storage.</span></span>
- <span data-ttu-id="9f485-184">HTTP : appelez votre fonction comme une API REST.</span><span class="sxs-lookup"><span data-stu-id="9f485-184">HTTP: invoke your function like a REST API.</span></span>
- <span data-ttu-id="9f485-185">Queue : appelez votre fonction lorsque des éléments existent dans une file d’attente.</span><span class="sxs-lookup"><span data-stu-id="9f485-185">Queue: invoke your function when items exist in a queue.</span></span>
- <span data-ttu-id="9f485-186">Timer : appelez votre fonction sur une cadence régulière.</span><span class="sxs-lookup"><span data-stu-id="9f485-186">Timer: invoke your function on a regular cadence.</span></span>

<span data-ttu-id="9f485-187">Voici quelques exemples de liaisons :</span><span class="sxs-lookup"><span data-stu-id="9f485-187">Examples of bindings include:</span></span>

- <span data-ttu-id="9f485-188">CosmosDB : Connectez-vous facilement à la base de données pour charger ou enregistrer des fichiers.</span><span class="sxs-lookup"><span data-stu-id="9f485-188">CosmosDB: easily connect to the database to load or save files.</span></span>
- <span data-ttu-id="9f485-189">Stockage table : travaillez avec le stockage clé/valeur à partir de votre application de fonction.</span><span class="sxs-lookup"><span data-stu-id="9f485-189">Table Storage: work with key/value storage from your function app.</span></span>
- <span data-ttu-id="9f485-190">Stockage file d’attente : récupérer facilement des éléments d’une file d’attente ou placer de nouveaux éléments dans la file d’attente.</span><span class="sxs-lookup"><span data-stu-id="9f485-190">Queue Storage: easily retrieve items from a queue, or place new items on the queue.</span></span>

<span data-ttu-id="9f485-191">L’exemple de fichier *functions. JSON* suivant définit un déclencheur et une liaison :</span><span class="sxs-lookup"><span data-stu-id="9f485-191">The following example *functions.json* file defines a trigger and a binding:</span></span>

```json
{
  "bindings": [
    {
      "name": "myBlob",
      "type": "blobTrigger",
      "direction": "in",
      "path": "images/{name}",
      "connection": "AzureWebJobsStorage"
    },
    {
      "name": "$return",
      "type": "queue",
      "direction": "out",
      "queueName": "images",
      "connection": "AzureWebJobsStorage"
    }
  ],
  "disabled": false
}
```

<span data-ttu-id="9f485-192">Dans cet exemple, la fonction est déclenchée par une modification du stockage d’objets BLOB dans le conteneur `images`.</span><span class="sxs-lookup"><span data-stu-id="9f485-192">In this example, the function is triggered by a change to blob storage in the `images` container.</span></span> <span data-ttu-id="9f485-193">Les informations relatives au fichier étant transmises, le déclencheur joue également le rôle de liaison.</span><span class="sxs-lookup"><span data-stu-id="9f485-193">The information for the file is passed in, so the trigger also acts as a binding.</span></span> <span data-ttu-id="9f485-194">Il existe une autre liaison pour placer des informations dans une file d’attente nommée `images`.</span><span class="sxs-lookup"><span data-stu-id="9f485-194">Another binding exists to put information onto a queue named `images`.</span></span>

<span data-ttu-id="9f485-195">Voici le C# script de la fonction :</span><span class="sxs-lookup"><span data-stu-id="9f485-195">Here is the C# script for the function:</span></span>

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

<span data-ttu-id="9f485-196">L’exemple est une fonction simple qui prend le nom du fichier qui a été modifié ou téléchargé dans le stockage d’objets BLOB, et la place dans une file d’attente pour un traitement ultérieur.</span><span class="sxs-lookup"><span data-stu-id="9f485-196">The example is a simple function that takes the name of the file that was modified or uploaded to blob storage, and places it on a queue for later processing.</span></span>

<span data-ttu-id="9f485-197">Pour obtenir la liste complète des déclencheurs et des liaisons, consultez [Azure Functions les concepts de déclencheurs et de liaisons](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span><span class="sxs-lookup"><span data-stu-id="9f485-197">For a full list of triggers and bindings, see [Azure Functions triggers and bindings concepts](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span></span>

## <a name="proxies"></a><span data-ttu-id="9f485-198">Serveurs proxy</span><span class="sxs-lookup"><span data-stu-id="9f485-198">Proxies</span></span>

<span data-ttu-id="9f485-199">Les proxies fournissent des fonctionnalités de redirection pour votre application.</span><span class="sxs-lookup"><span data-stu-id="9f485-199">Proxies provide redirect functionality for your application.</span></span> <span data-ttu-id="9f485-200">Les proxies exposent un point de terminaison et mappent ce point de terminaison à une autre ressource.</span><span class="sxs-lookup"><span data-stu-id="9f485-200">Proxies expose an endpoint and map that endpoint to another resource.</span></span> <span data-ttu-id="9f485-201">Avec les proxies, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="9f485-201">With proxies, you can:</span></span>

- <span data-ttu-id="9f485-202">Rediriger une demande entrante vers un autre point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="9f485-202">Reroute an incoming request to another endpoint.</span></span>
- <span data-ttu-id="9f485-203">Modifiez la requête entrante avant de la transmettre.</span><span class="sxs-lookup"><span data-stu-id="9f485-203">Modify the incoming request before it's passed along.</span></span>
- <span data-ttu-id="9f485-204">Modifiez ou fournissez une réponse.</span><span class="sxs-lookup"><span data-stu-id="9f485-204">Modify or provide a response.</span></span>

<span data-ttu-id="9f485-205">Les proxies sont utilisés dans des scénarios tels que :</span><span class="sxs-lookup"><span data-stu-id="9f485-205">Proxies are used for scenarios such as:</span></span>

- <span data-ttu-id="9f485-206">Simplification, raccourcissement ou modification de l’URL.</span><span class="sxs-lookup"><span data-stu-id="9f485-206">Simplifying, shortening, or changing the URL.</span></span>
- <span data-ttu-id="9f485-207">Fournir un préfixe d’API cohérent à plusieurs services principaux.</span><span class="sxs-lookup"><span data-stu-id="9f485-207">Providing a consistent API prefix to multiple back-end services.</span></span>
- <span data-ttu-id="9f485-208">Simulation d’une réponse à un point de terminaison en cours de développement.</span><span class="sxs-lookup"><span data-stu-id="9f485-208">Mocking a response to an endpoint being developed.</span></span>
- <span data-ttu-id="9f485-209">Fournir une réponse statique à un point de terminaison connu.</span><span class="sxs-lookup"><span data-stu-id="9f485-209">Providing a static response to a well-known endpoint.</span></span>
- <span data-ttu-id="9f485-210">Maintien de la cohérence d’un point de terminaison d’API pendant le déplacement ou la migration du back end.</span><span class="sxs-lookup"><span data-stu-id="9f485-210">Keeping an API endpoint consistent while the back end is moved or migrated.</span></span>

<span data-ttu-id="9f485-211">Les proxies sont stockés sous forme de définitions JSON.</span><span class="sxs-lookup"><span data-stu-id="9f485-211">Proxies are stored as JSON definitions.</span></span> <span data-ttu-id="9f485-212">Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="9f485-212">Here is an example:</span></span>

```json
{
  "$schema": "http://json.schemastore.org/proxies",
  "proxies": {
    "Domain Redirect": {
      "matchCondition": {
        "route": "/{shortUrl}"
      },
      "backendUri": "http://%WEBSITE_HOSTNAME%/api/UrlRedirect/{shortUrl}"
    },
    "Root": {
      "matchCondition": {
        "route": "/"
      },
      "responseOverrides": {
        "response.statusCode": "301",
        "response.statusReason": "Moved Permanently",
        "response.headers.location": "https://docs.microsoft.com/"
      }
    }
  }
}
```

<span data-ttu-id="9f485-213">Le proxy `Domain Redirect` prend un itinéraire abrégé et le mappe à la ressource de fonction plus longue.</span><span class="sxs-lookup"><span data-stu-id="9f485-213">The `Domain Redirect` proxy takes a shortened route and maps it to the longer function resource.</span></span> <span data-ttu-id="9f485-214">La transformation ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="9f485-214">The transformation looks like:</span></span>

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

<span data-ttu-id="9f485-215">Le proxy `Root` prend tout ce qui est envoyé à l’URL racine (`https://--shorturl--/`) et le redirige vers le site de documentation.</span><span class="sxs-lookup"><span data-stu-id="9f485-215">The `Root` proxy takes anything sent to the root URL (`https://--shorturl--/`) and redirects it to the documentation site.</span></span>

<span data-ttu-id="9f485-216">Un exemple d’utilisation de proxys est présenté dans la vidéo [Azure : mettez votre application dans le Cloud avec des Azure Functions sans serveur](https://channel9.msdn.com/events/Connect/2017/E102).</span><span class="sxs-lookup"><span data-stu-id="9f485-216">An example of using proxies is shown in the video [Azure: Bring your app to the cloud with serverless Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102).</span></span> <span data-ttu-id="9f485-217">En temps réel, une application ASP.NET Core s’exécutant sur SQL Server local est migrée vers le Cloud Azure.</span><span class="sxs-lookup"><span data-stu-id="9f485-217">In real time, an ASP.NET Core application running on local SQL Server is migrated to the Azure Cloud.</span></span> <span data-ttu-id="9f485-218">Les proxies sont utilisés pour aider à refactoriser un projet d’API Web traditionnel afin d’utiliser des fonctions.</span><span class="sxs-lookup"><span data-stu-id="9f485-218">Proxies are used to help refactor a traditional Web API project to use functions.</span></span>

<span data-ttu-id="9f485-219">Pour plus d’informations sur les proxies, consultez [utiliser Azure Functions proxies](https://docs.microsoft.com/azure/azure-functions/functions-proxies).</span><span class="sxs-lookup"><span data-stu-id="9f485-219">For more information about Proxies, see [Work with Azure Functions Proxies](https://docs.microsoft.com/azure/azure-functions/functions-proxies).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9f485-220">[Précédent](azure-serverless-platform.md)
>[Suivant](application-insights.md)</span><span class="sxs-lookup"><span data-stu-id="9f485-220">[Previous](azure-serverless-platform.md)
[Next](application-insights.md)</span></span>
