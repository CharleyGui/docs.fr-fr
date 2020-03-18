---
title: Fonctions Azure - Applications sans serveur
description: Les fonctions Azure fournissent des capacités sans serveur sur plusieurs langues (C, JavaScript, Java) et des plates-formes pour fournir un code instantané axé sur les événements.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 8764e6a33f3fdd53e60fa767d0fb584a9c07de7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401612"
---
# <a name="azure-functions"></a><span data-ttu-id="1723c-103">Azure Functions</span><span class="sxs-lookup"><span data-stu-id="1723c-103">Azure Functions</span></span>

<span data-ttu-id="1723c-104">Les fonctions Azure offrent une expérience de calcul sans serveur.</span><span class="sxs-lookup"><span data-stu-id="1723c-104">Azure functions provide a serverless compute experience.</span></span> <span data-ttu-id="1723c-105">Une fonction est invoquée par un *déclencheur* (comme l’accès à un point de terminaison HTTP ou à une minuterie) et exécute un bloc de code ou de logique métier.</span><span class="sxs-lookup"><span data-stu-id="1723c-105">A function is invoked by a *trigger* (such as access to an HTTP endpoint or a timer) and executes a block of code or business logic.</span></span> <span data-ttu-id="1723c-106">Les fonctions prennent également en charge des *liaisons* spécialisées qui se connectent à des ressources comme le stockage et les files d’attente.</span><span class="sxs-lookup"><span data-stu-id="1723c-106">Functions also support specialized *bindings* that connect to resources like storage and queues.</span></span>

![Logo azure fonctions](./media/azure-functions-logo.png)

<span data-ttu-id="1723c-108">Il existe deux versions du cadre Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="1723c-108">There are two versions of the Azure Functions framework.</span></span> <span data-ttu-id="1723c-109">La version héritée prend en charge le cadre .NET complet et le nouveau runtime prend en charge les applications cross-platform .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1723c-109">The legacy version supports the full .NET Framework and the new runtime supports cross-platform .NET Core applications.</span></span> <span data-ttu-id="1723c-110">D’autres langues en dehors de C’telles que JavaScript, F' et Java sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="1723c-110">Additional languages besides C# such as JavaScript, F#, and Java are supported.</span></span> <span data-ttu-id="1723c-111">Les fonctions créées dans le portail fournissent une syntaxe scriptive riche.</span><span class="sxs-lookup"><span data-stu-id="1723c-111">Functions created in the portal provide a rich scripting syntax.</span></span> <span data-ttu-id="1723c-112">Les fonctions créées en tant que projets autonomes peuvent être déployées avec un soutien et des capacités de plate-forme complets.</span><span class="sxs-lookup"><span data-stu-id="1723c-112">Functions created as standalone projects can be deployed with full platform support and capabilities.</span></span>

<span data-ttu-id="1723c-113">Pour plus d’informations, voir [la documentation Azure Functions](https://docs.microsoft.com/azure/azure-functions).</span><span class="sxs-lookup"><span data-stu-id="1723c-113">For more information, see [Azure Functions documentation](https://docs.microsoft.com/azure/azure-functions).</span></span>

## <a name="functions-v1-vs-v2"></a><span data-ttu-id="1723c-114">Fonctions v1 vs v2</span><span class="sxs-lookup"><span data-stu-id="1723c-114">Functions v1 vs. v2</span></span>

<span data-ttu-id="1723c-115">Il existe deux versions de l’heure d’exécution Azure Functions : 1.x et 2.x.</span><span class="sxs-lookup"><span data-stu-id="1723c-115">There are two versions of the Azure Functions runtime: 1.x and 2.x.</span></span> <span data-ttu-id="1723c-116">La version 1.x est généralement disponible (GA).</span><span class="sxs-lookup"><span data-stu-id="1723c-116">Version 1.x is generally available (GA).</span></span> <span data-ttu-id="1723c-117">Il prend en charge le développement .NET à partir du portail ou des machines Windows et utilise le cadre .NET.</span><span class="sxs-lookup"><span data-stu-id="1723c-117">It supports .NET development from the portal or Windows machines and uses the .NET Framework.</span></span> <span data-ttu-id="1723c-118">1.x prend en charge C, JavaScript et F, avec un support expérimental pour Python, PHP, TypeScript, Batch, Bash et PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1723c-118">1.x supports C#, JavaScript, and F#, with experimental support for Python, PHP, TypeScript, Batch, Bash, and PowerShell.</span></span>

<span data-ttu-id="1723c-119">[Version 2.x est également généralement disponible dès maintenant](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/).</span><span class="sxs-lookup"><span data-stu-id="1723c-119">[Version 2.x is also generally available now](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/).</span></span> <span data-ttu-id="1723c-120">Il tire parti de .NET Core et prend en charge le développement multiplateforme sur les machines Windows, macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="1723c-120">It leverages .NET Core and supports cross-platform development on Windows, macOS, and Linux machines.</span></span> <span data-ttu-id="1723c-121">2.x ajoute un support de première classe pour Java, mais ne prend pas encore directement en charge l’une des langues expérimentales.</span><span class="sxs-lookup"><span data-stu-id="1723c-121">2.x adds first-class support for Java but doesn't yet directly support any of the experimental languages.</span></span> <span data-ttu-id="1723c-122">La version 2.x utilise un nouveau modèle d’extéabilité contraignante qui permet des extensions tierces à la plate-forme, une version indépendante des fixations et un environnement d’exécution plus rationalisé.</span><span class="sxs-lookup"><span data-stu-id="1723c-122">Version 2.x uses a new binding extensibility model that enables third-party extensions to the platform, independent versioning of bindings, and a more streamlined execution environment.</span></span>

> <span data-ttu-id="1723c-123">**Il ya un problème connu dans 1.x avec [le soutien réorienté contraignant](https://github.com/Azure/azure-functions-host/issues/992).**</span><span class="sxs-lookup"><span data-stu-id="1723c-123">**There is a known issue in 1.x with [binding redirect support](https://github.com/Azure/azure-functions-host/issues/992).**</span></span> <span data-ttu-id="1723c-124">La question est spécifique au développement .NET.</span><span class="sxs-lookup"><span data-stu-id="1723c-124">The issue is specific to .NET development.</span></span> <span data-ttu-id="1723c-125">Les projets ayant des dépendances sur les bibliothèques qui sont une version différente des bibliothèques incluses dans le temps d’exécution sont touchés.</span><span class="sxs-lookup"><span data-stu-id="1723c-125">Projects with dependencies on libraries that are a different version from the libraries included in the runtime are impacted.</span></span> <span data-ttu-id="1723c-126">L’équipe des fonctions s’est engagée à faire des progrès concrets sur le problème.</span><span class="sxs-lookup"><span data-stu-id="1723c-126">The functions team has committed to making concrete progress on the problem.</span></span> <span data-ttu-id="1723c-127">L’équipe abordera les redirections de liaison en 2.x avant qu’elle n’entre dans la disponibilité générale.</span><span class="sxs-lookup"><span data-stu-id="1723c-127">The team will address binding redirects in 2.x before it goes into general availability.</span></span> <span data-ttu-id="1723c-128">La déclaration officielle de l’équipe avec des correctifs suggérés et des solutions de contournement est disponible ici: [résolution de l’Assemblée dans azure Fonctions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).</span><span class="sxs-lookup"><span data-stu-id="1723c-128">The official team statement with suggested fixes and workarounds is available here: [Assembly resolution in Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).</span></span>

<span data-ttu-id="1723c-129">Pour plus d’informations, voir [Comparez 1.x et 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).</span><span class="sxs-lookup"><span data-stu-id="1723c-129">For more information, see [Compare 1.x and 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).</span></span>

## <a name="programming-language-support"></a><span data-ttu-id="1723c-130">Soutien linguistique de programmation</span><span class="sxs-lookup"><span data-stu-id="1723c-130">Programming language support</span></span>

<span data-ttu-id="1723c-131">Les langues suivantes sont prises en charge soit en disponibilité générale (GA), en avant-première, soit expérimentale.</span><span class="sxs-lookup"><span data-stu-id="1723c-131">The following languages are supported either in general availability (GA), preview, or experimental.</span></span>

|<span data-ttu-id="1723c-132">Langage</span><span class="sxs-lookup"><span data-stu-id="1723c-132">Language</span></span>      |<span data-ttu-id="1723c-133">1.x</span><span class="sxs-lookup"><span data-stu-id="1723c-133">1.x</span></span>         |<span data-ttu-id="1723c-134">2.x</span><span class="sxs-lookup"><span data-stu-id="1723c-134">2.x</span></span>      |
|--------------|------------|---------|
|<span data-ttu-id="1723c-135">**C #**</span><span class="sxs-lookup"><span data-stu-id="1723c-135">**C#**</span></span>        |<span data-ttu-id="1723c-136">GA</span><span class="sxs-lookup"><span data-stu-id="1723c-136">GA</span></span>          |<span data-ttu-id="1723c-137">PRÉVERSION</span><span class="sxs-lookup"><span data-stu-id="1723c-137">Preview</span></span>  |
|<span data-ttu-id="1723c-138">**Javascript**</span><span class="sxs-lookup"><span data-stu-id="1723c-138">**JavaScript**</span></span>|<span data-ttu-id="1723c-139">GA</span><span class="sxs-lookup"><span data-stu-id="1723c-139">GA</span></span>          |<span data-ttu-id="1723c-140">PRÉVERSION</span><span class="sxs-lookup"><span data-stu-id="1723c-140">Preview</span></span>  |
|<span data-ttu-id="1723c-141">**F #**</span><span class="sxs-lookup"><span data-stu-id="1723c-141">**F#**</span></span>        |<span data-ttu-id="1723c-142">GA</span><span class="sxs-lookup"><span data-stu-id="1723c-142">GA</span></span>          |         |
|<span data-ttu-id="1723c-143">**Java**</span><span class="sxs-lookup"><span data-stu-id="1723c-143">**Java**</span></span>      |            |<span data-ttu-id="1723c-144">PRÉVERSION</span><span class="sxs-lookup"><span data-stu-id="1723c-144">Preview</span></span>  |
|<span data-ttu-id="1723c-145">**Python**</span><span class="sxs-lookup"><span data-stu-id="1723c-145">**Python**</span></span>    |<span data-ttu-id="1723c-146">Expérimental</span><span class="sxs-lookup"><span data-stu-id="1723c-146">Experimental</span></span>|         |
|<span data-ttu-id="1723c-147">**Php**</span><span class="sxs-lookup"><span data-stu-id="1723c-147">**PHP**</span></span>       |<span data-ttu-id="1723c-148">Expérimental</span><span class="sxs-lookup"><span data-stu-id="1723c-148">Experimental</span></span>|         |
|<span data-ttu-id="1723c-149">**TypeScript**</span><span class="sxs-lookup"><span data-stu-id="1723c-149">**TypeScript**</span></span>|<span data-ttu-id="1723c-150">Expérimental</span><span class="sxs-lookup"><span data-stu-id="1723c-150">Experimental</span></span>|         |
|<span data-ttu-id="1723c-151">**Lot**</span><span class="sxs-lookup"><span data-stu-id="1723c-151">**Batch**</span></span>     |<span data-ttu-id="1723c-152">Expérimental</span><span class="sxs-lookup"><span data-stu-id="1723c-152">Experimental</span></span>|         |
|<span data-ttu-id="1723c-153">**Bash**</span><span class="sxs-lookup"><span data-stu-id="1723c-153">**Bash**</span></span>      |<span data-ttu-id="1723c-154">Expérimental</span><span class="sxs-lookup"><span data-stu-id="1723c-154">Experimental</span></span>|         |
|<span data-ttu-id="1723c-155">**PowerShell**</span><span class="sxs-lookup"><span data-stu-id="1723c-155">**PowerShell**</span></span>|<span data-ttu-id="1723c-156">Expérimental</span><span class="sxs-lookup"><span data-stu-id="1723c-156">Experimental</span></span>|         |

<span data-ttu-id="1723c-157">Pour en savoir plus, consultez [Langages pris en charge](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span><span class="sxs-lookup"><span data-stu-id="1723c-157">For more information, see [Supported languages](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span></span>

## <a name="app-service-plans"></a><span data-ttu-id="1723c-158">Plans de service App</span><span class="sxs-lookup"><span data-stu-id="1723c-158">App service plans</span></span>

<span data-ttu-id="1723c-159">Les fonctions sont soutenues par un *plan de service d’application*.</span><span class="sxs-lookup"><span data-stu-id="1723c-159">Functions are backed by an *app service plan*.</span></span> <span data-ttu-id="1723c-160">Le plan définit les ressources utilisées par l’application fonctions.</span><span class="sxs-lookup"><span data-stu-id="1723c-160">The plan defines the resources used by the functions app.</span></span> <span data-ttu-id="1723c-161">Vous pouvez affecter des plans à une région, déterminer la taille et le nombre de machines virtuelles qui seront utilisées, et choisir un niveau de tarification.</span><span class="sxs-lookup"><span data-stu-id="1723c-161">You can assign plans to a region, determine the size and number of virtual machines that will be used, and pick a pricing tier.</span></span> <span data-ttu-id="1723c-162">Pour une véritable approche sans serveur, les applications de fonction peuvent utiliser le plan **de consommation.**</span><span class="sxs-lookup"><span data-stu-id="1723c-162">For a true serverless approach, function apps may use the **consumption** plan.</span></span> <span data-ttu-id="1723c-163">Le plan de consommation permettra d’échelle de l’arrière automatiquement en fonction de la charge.</span><span class="sxs-lookup"><span data-stu-id="1723c-163">The consumption plan will scale the back end automatically based on load.</span></span>

<span data-ttu-id="1723c-164">Pour plus d’informations, consultez [les plans de service App](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span><span class="sxs-lookup"><span data-stu-id="1723c-164">For more information, see [App service plans](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

## <a name="create-your-first-function"></a><span data-ttu-id="1723c-165">Créer votre première fonction</span><span class="sxs-lookup"><span data-stu-id="1723c-165">Create your first function</span></span>

<span data-ttu-id="1723c-166">Il existe trois façons courantes de créer des applications de fonction.</span><span class="sxs-lookup"><span data-stu-id="1723c-166">There are three common ways you can create function apps.</span></span>

- <span data-ttu-id="1723c-167">Fonctions de script dans le portail.</span><span class="sxs-lookup"><span data-stu-id="1723c-167">Script functions in the portal.</span></span>
- <span data-ttu-id="1723c-168">Créez les ressources nécessaires à l’aide du CLI Azure.</span><span class="sxs-lookup"><span data-stu-id="1723c-168">Create the necessary resources using the Azure CLI.</span></span>
- <span data-ttu-id="1723c-169">Construisez des fonctions localement à l’aide de votre IDE préféré et publiez-les sur Azure.</span><span class="sxs-lookup"><span data-stu-id="1723c-169">Build functions locally using your favorite IDE and publish them to Azure.</span></span>

<span data-ttu-id="1723c-170">Pour plus d’informations sur la création d’une fonction scénarisée dans le portail, voir [Créer votre première fonction dans le portail Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span><span class="sxs-lookup"><span data-stu-id="1723c-170">For more information on creating a scripted function in the portal, see [Create your first function in the Azure portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span></span>

<span data-ttu-id="1723c-171">Pour construire à partir du CLI Azure, voir [Créer votre première fonction à l’aide de l’Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span><span class="sxs-lookup"><span data-stu-id="1723c-171">To build from the Azure CLI, see [Create your first function using the Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span></span>

<span data-ttu-id="1723c-172">Pour créer une fonction à partir de Visual Studio, voir [Créer votre première fonction en utilisant Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="1723c-172">To create a function from Visual Studio, see [Create your first function using Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span></span>

## <a name="understand-triggers-and-bindings"></a><span data-ttu-id="1723c-173">Comprendre les déclencheurs et les fixations</span><span class="sxs-lookup"><span data-stu-id="1723c-173">Understand triggers and bindings</span></span>

<span data-ttu-id="1723c-174">Les fonctions sont invoquées par un *déclencheur* et peuvent en avoir exactement une.</span><span class="sxs-lookup"><span data-stu-id="1723c-174">Functions are invoked by a *trigger* and can have exactly one.</span></span> <span data-ttu-id="1723c-175">En plus d’invoquer la fonction, certains déclencheurs servent également de fixations.</span><span class="sxs-lookup"><span data-stu-id="1723c-175">In addition to invoking the function, certain triggers also serve as bindings.</span></span> <span data-ttu-id="1723c-176">Vous pouvez également définir plusieurs liaisons en plus de la gâchette.</span><span class="sxs-lookup"><span data-stu-id="1723c-176">You may also define multiple bindings in addition to the trigger.</span></span> <span data-ttu-id="1723c-177">*Les liaisons* fournissent un moyen déclaratif de connecter les données à votre code.</span><span class="sxs-lookup"><span data-stu-id="1723c-177">*Bindings* provide a declarative way to connect data to your code.</span></span> <span data-ttu-id="1723c-178">Ils peuvent être transmis (entrée) ou recevoir des données (sortie).</span><span class="sxs-lookup"><span data-stu-id="1723c-178">They can be passed in (input) or receive data (output).</span></span> <span data-ttu-id="1723c-179">Les déclencheurs et les fixations facilitent le travail des fonctions.</span><span class="sxs-lookup"><span data-stu-id="1723c-179">Triggers and bindings make functions easy to work with.</span></span> <span data-ttu-id="1723c-180">Les liaisons suppriment les frais généraux de la création manuelle de bases de données ou de connexions système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="1723c-180">Bindings remove the overhead of manually creating database or file system connections.</span></span> <span data-ttu-id="1723c-181">Toutes les informations nécessaires pour les liaisons sont contenues dans un fichier *functions.json* spécial pour les scripts ou déclaré avec des attributs dans le code.</span><span class="sxs-lookup"><span data-stu-id="1723c-181">All of the information needed for the bindings is contained in a special *functions.json* file for scripts or declared with attributes in code.</span></span>

<span data-ttu-id="1723c-182">Voici quelques déclencheurs courants :</span><span class="sxs-lookup"><span data-stu-id="1723c-182">Some common triggers include:</span></span>

- <span data-ttu-id="1723c-183">Stockage Blob : invoquez votre fonction lorsqu’un fichier ou un dossier est téléchargé ou modifié dans le stockage.</span><span class="sxs-lookup"><span data-stu-id="1723c-183">Blob Storage: invoke your function when a file or folder is uploaded or changed in storage.</span></span>
- <span data-ttu-id="1723c-184">HTTP : invoquez votre fonction comme une API REST.</span><span class="sxs-lookup"><span data-stu-id="1723c-184">HTTP: invoke your function like a REST API.</span></span>
- <span data-ttu-id="1723c-185">File d’attente : invoquez votre fonction lorsque des éléments existent dans une file d’attente.</span><span class="sxs-lookup"><span data-stu-id="1723c-185">Queue: invoke your function when items exist in a queue.</span></span>
- <span data-ttu-id="1723c-186">Minuterie : invoquez votre fonction sur une cadence régulière.</span><span class="sxs-lookup"><span data-stu-id="1723c-186">Timer: invoke your function on a regular cadence.</span></span>

<span data-ttu-id="1723c-187">Voici quelques exemples de liaisons :</span><span class="sxs-lookup"><span data-stu-id="1723c-187">Examples of bindings include:</span></span>

- <span data-ttu-id="1723c-188">CosmosDB : connectez-vous facilement à la base de données pour charger ou enregistrer des fichiers.</span><span class="sxs-lookup"><span data-stu-id="1723c-188">CosmosDB: easily connect to the database to load or save files.</span></span>
- <span data-ttu-id="1723c-189">Stockage de table : travaillez avec le stockage de clé/valeur à partir de votre application de fonction.</span><span class="sxs-lookup"><span data-stu-id="1723c-189">Table Storage: work with key/value storage from your function app.</span></span>
- <span data-ttu-id="1723c-190">Stockage de file d’attente : récupérez facilement des articles d’une file d’attente ou placez de nouveaux éléments dans la file d’attente.</span><span class="sxs-lookup"><span data-stu-id="1723c-190">Queue Storage: easily retrieve items from a queue, or place new items on the queue.</span></span>

<span data-ttu-id="1723c-191">L’exemple suivant *functions.json* fichier définit un déclencheur et une liaison:</span><span class="sxs-lookup"><span data-stu-id="1723c-191">The following example *functions.json* file defines a trigger and a binding:</span></span>

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

<span data-ttu-id="1723c-192">Dans cet exemple, la fonction est déclenchée par `images` un changement de stockage blob dans le conteneur.</span><span class="sxs-lookup"><span data-stu-id="1723c-192">In this example, the function is triggered by a change to blob storage in the `images` container.</span></span> <span data-ttu-id="1723c-193">Les informations pour le fichier sont transmises, de sorte que le déclencheur agit également comme une liaison.</span><span class="sxs-lookup"><span data-stu-id="1723c-193">The information for the file is passed in, so the trigger also acts as a binding.</span></span> <span data-ttu-id="1723c-194">Une autre liaison existe pour mettre `images`l’information sur une file d’attente nommée .</span><span class="sxs-lookup"><span data-stu-id="1723c-194">Another binding exists to put information onto a queue named `images`.</span></span>

<span data-ttu-id="1723c-195">Voici le script C pour la fonction:</span><span class="sxs-lookup"><span data-stu-id="1723c-195">Here is the C# script for the function:</span></span>

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

<span data-ttu-id="1723c-196">L’exemple est une fonction simple qui prend le nom du fichier qui a été modifié ou téléchargé sur le stockage blob, et le place sur une file d’attente pour le traitement ultérieur.</span><span class="sxs-lookup"><span data-stu-id="1723c-196">The example is a simple function that takes the name of the file that was modified or uploaded to blob storage, and places it on a queue for later processing.</span></span>

<span data-ttu-id="1723c-197">Pour une liste complète des déclencheurs et des fixations, voir [les déclencheurs et les concepts de fixations Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span><span class="sxs-lookup"><span data-stu-id="1723c-197">For a full list of triggers and bindings, see [Azure Functions triggers and bindings concepts](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span></span>

## <a name="proxies"></a><span data-ttu-id="1723c-198">Proxies</span><span class="sxs-lookup"><span data-stu-id="1723c-198">Proxies</span></span>

<span data-ttu-id="1723c-199">Les procurations fournissent des fonctionnalités de redirection pour votre application.</span><span class="sxs-lookup"><span data-stu-id="1723c-199">Proxies provide redirect functionality for your application.</span></span> <span data-ttu-id="1723c-200">Les procurations exposent un point de terminaison et cartographient ce point de terminaison vers une autre ressource.</span><span class="sxs-lookup"><span data-stu-id="1723c-200">Proxies expose an endpoint and map that endpoint to another resource.</span></span> <span data-ttu-id="1723c-201">Avec des procurations, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="1723c-201">With proxies, you can:</span></span>

- <span data-ttu-id="1723c-202">Réorienter une demande entrante à un autre critère d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="1723c-202">Reroute an incoming request to another endpoint.</span></span>
- <span data-ttu-id="1723c-203">Modifier la demande entrante avant qu’elle ne soit transmise.</span><span class="sxs-lookup"><span data-stu-id="1723c-203">Modify the incoming request before it's passed along.</span></span>
- <span data-ttu-id="1723c-204">Modifier ou fournir une réponse.</span><span class="sxs-lookup"><span data-stu-id="1723c-204">Modify or provide a response.</span></span>

<span data-ttu-id="1723c-205">Les procurations sont utilisées pour des scénarios tels que :</span><span class="sxs-lookup"><span data-stu-id="1723c-205">Proxies are used for scenarios such as:</span></span>

- <span data-ttu-id="1723c-206">Simplifier, raccourcir ou modifier l’URL.</span><span class="sxs-lookup"><span data-stu-id="1723c-206">Simplifying, shortening, or changing the URL.</span></span>
- <span data-ttu-id="1723c-207">Fournir un préfixe API cohérent à plusieurs services back-end.</span><span class="sxs-lookup"><span data-stu-id="1723c-207">Providing a consistent API prefix to multiple back-end services.</span></span>
- <span data-ttu-id="1723c-208">Se moquer d’une réponse à un point de terminaison en cours d’élaboration.</span><span class="sxs-lookup"><span data-stu-id="1723c-208">Mocking a response to an endpoint being developed.</span></span>
- <span data-ttu-id="1723c-209">Fournir une réponse statique à un critère d’évaluation bien connu.</span><span class="sxs-lookup"><span data-stu-id="1723c-209">Providing a static response to a well-known endpoint.</span></span>
- <span data-ttu-id="1723c-210">Maintenir un point de terminaison API cohérent pendant que l’extrémité arrière est déplacée ou migrée.</span><span class="sxs-lookup"><span data-stu-id="1723c-210">Keeping an API endpoint consistent while the back end is moved or migrated.</span></span>

<span data-ttu-id="1723c-211">Les procurations sont stockées sous forme de définitions JSON.</span><span class="sxs-lookup"><span data-stu-id="1723c-211">Proxies are stored as JSON definitions.</span></span> <span data-ttu-id="1723c-212">Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="1723c-212">Here is an example:</span></span>

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

<span data-ttu-id="1723c-213">Le `Domain Redirect` proxy prend un itinéraire raccourci et le cartographie à la ressource de fonction plus longue.</span><span class="sxs-lookup"><span data-stu-id="1723c-213">The `Domain Redirect` proxy takes a shortened route and maps it to the longer function resource.</span></span> <span data-ttu-id="1723c-214">La transformation ressemble à:</span><span class="sxs-lookup"><span data-stu-id="1723c-214">The transformation looks like:</span></span>

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

<span data-ttu-id="1723c-215">Le `Root` proxy prend tout ce`https://--shorturl--/`qui est envoyé à l’URL racine ( ) et la redirige vers le site de documentation.</span><span class="sxs-lookup"><span data-stu-id="1723c-215">The `Root` proxy takes anything sent to the root URL (`https://--shorturl--/`) and redirects it to the documentation site.</span></span>

<span data-ttu-id="1723c-216">Un exemple d’utilisation de procurations est montré dans la vidéo [Azure: Apportez votre application au cloud avec des fonctions Azure sans serveur](https://channel9.msdn.com/events/Connect/2017/E102).</span><span class="sxs-lookup"><span data-stu-id="1723c-216">An example of using proxies is shown in the video [Azure: Bring your app to the cloud with serverless Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102).</span></span> <span data-ttu-id="1723c-217">En temps réel, une application ASP.NET Core fonctionnant sur SQL Server local est migrée vers le Cloud Azure.</span><span class="sxs-lookup"><span data-stu-id="1723c-217">In real time, an ASP.NET Core application running on local SQL Server is migrated to the Azure Cloud.</span></span> <span data-ttu-id="1723c-218">Les procurations sont utilisées pour aider à refactorer un projet traditionnel d’API Web pour utiliser des fonctions.</span><span class="sxs-lookup"><span data-stu-id="1723c-218">Proxies are used to help refactor a traditional Web API project to use functions.</span></span>

<span data-ttu-id="1723c-219">Pour plus d’informations sur Proxies, voir [Work with Azure Functions Proxies](https://docs.microsoft.com/azure/azure-functions/functions-proxies).</span><span class="sxs-lookup"><span data-stu-id="1723c-219">For more information about Proxies, see [Work with Azure Functions Proxies](https://docs.microsoft.com/azure/azure-functions/functions-proxies).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1723c-220">[Suivant précédent](azure-serverless-platform.md)
>[Next](application-insights.md)</span><span class="sxs-lookup"><span data-stu-id="1723c-220">[Previous](azure-serverless-platform.md)
[Next](application-insights.md)</span></span>
