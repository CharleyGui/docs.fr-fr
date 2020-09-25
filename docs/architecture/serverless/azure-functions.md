---
title: Applications sans serveur Azure Functions
description: Azure Functions offre des fonctionnalités sans serveur dans plusieurs langues (C#, JavaScript, Java) et des plateformes pour fournir un code de mise à l’échelle instantanée piloté par les événements.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/06/2020
ms.openlocfilehash: 7625b2a0dafb90dc1bf2fb7fe680d53b20764c09
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171804"
---
# <a name="azure-functions"></a><span data-ttu-id="8fbfc-103">Azure Functions</span><span class="sxs-lookup"><span data-stu-id="8fbfc-103">Azure Functions</span></span>

<span data-ttu-id="8fbfc-104">Azure Functions offre une expérience de calcul sans serveur.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-104">Azure functions provide a serverless compute experience.</span></span> <span data-ttu-id="8fbfc-105">Une fonction est appelée par un *déclencheur* (comme l’accès à un point de terminaison http ou une minuterie) et exécute un bloc de code ou une logique métier.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-105">A function is invoked by a *trigger* (such as access to an HTTP endpoint or a timer) and executes a block of code or business logic.</span></span> <span data-ttu-id="8fbfc-106">Les fonctions prennent également en charge des *liaisons* spécialisées qui se connectent à des ressources telles que le stockage et les files d’attente.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-106">Functions also support specialized *bindings* that connect to resources like storage and queues.</span></span>

![Logo Azure Functions](./media/azure-functions-logo.png)

<span data-ttu-id="8fbfc-108">La version de Runtime actuelle 3,0 prend en charge les applications .NET Core 3,1 multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-108">The current runtime version 3.0 supports cross-platform .NET Core 3.1 applications.</span></span> <span data-ttu-id="8fbfc-109">Des langages supplémentaires en plus de C#, tels que JavaScript, F # et Java, sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-109">Additional languages besides C# such as JavaScript, F#, and Java are supported.</span></span> <span data-ttu-id="8fbfc-110">Les fonctions créées dans le portail fournissent une syntaxe de script riche.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-110">Functions created in the portal provide a rich scripting syntax.</span></span> <span data-ttu-id="8fbfc-111">Les fonctions créées en tant que projets autonomes peuvent être déployées avec une prise en charge complète des plateformes et des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-111">Functions created as standalone projects can be deployed with full platform support and capabilities.</span></span>

<span data-ttu-id="8fbfc-112">Pour plus d’informations, consultez [la documentation Azure Functions](/azure/azure-functions).</span><span class="sxs-lookup"><span data-stu-id="8fbfc-112">For more information, see [Azure Functions documentation](/azure/azure-functions).</span></span>

## <a name="programming-language-support"></a><span data-ttu-id="8fbfc-113">Prise en charge des langages de programmation</span><span class="sxs-lookup"><span data-stu-id="8fbfc-113">Programming language support</span></span>

<span data-ttu-id="8fbfc-114">Les langues suivantes sont toutes prises en charge dans la disponibilité générale (GA).</span><span class="sxs-lookup"><span data-stu-id="8fbfc-114">The following languages are all supported in general availability (GA).</span></span>

|<span data-ttu-id="8fbfc-115">Langage</span><span class="sxs-lookup"><span data-stu-id="8fbfc-115">Language</span></span>      |<span data-ttu-id="8fbfc-116">Runtimes pris en charge</span><span class="sxs-lookup"><span data-stu-id="8fbfc-116">Supported runtimes</span></span>|
|--------------|------------------|
|<span data-ttu-id="8fbfc-117">**C#**</span><span class="sxs-lookup"><span data-stu-id="8fbfc-117">**C#**</span></span>        |<span data-ttu-id="8fbfc-118">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="8fbfc-118">.NET Core 3.1</span></span>     |
|<span data-ttu-id="8fbfc-119">**JavaScript**</span><span class="sxs-lookup"><span data-stu-id="8fbfc-119">**JavaScript**</span></span>|<span data-ttu-id="8fbfc-120">Nœud 10 & 12</span><span class="sxs-lookup"><span data-stu-id="8fbfc-120">Node 10 & 12</span></span>      |
|<span data-ttu-id="8fbfc-121">**F#**</span><span class="sxs-lookup"><span data-stu-id="8fbfc-121">**F#**</span></span>        |<span data-ttu-id="8fbfc-122">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="8fbfc-122">.NET Core 3.1</span></span>     |
|<span data-ttu-id="8fbfc-123">**Java**</span><span class="sxs-lookup"><span data-stu-id="8fbfc-123">**Java**</span></span>      |<span data-ttu-id="8fbfc-124">Java 8</span><span class="sxs-lookup"><span data-stu-id="8fbfc-124">Java 8</span></span>            |
|<span data-ttu-id="8fbfc-125">**Python**</span><span class="sxs-lookup"><span data-stu-id="8fbfc-125">**Python**</span></span>    |<span data-ttu-id="8fbfc-126">Python 3,6, 3,7, & 3,8</span><span class="sxs-lookup"><span data-stu-id="8fbfc-126">Python 3.6, 3.7, & 3.8</span></span>|
|<span data-ttu-id="8fbfc-127">**TypeScript**</span><span class="sxs-lookup"><span data-stu-id="8fbfc-127">**TypeScript**</span></span>|<span data-ttu-id="8fbfc-128">Nœud 10 & 12 (via JavaScript)</span><span class="sxs-lookup"><span data-stu-id="8fbfc-128">Node 10 & 12 (via JavaScript)</span></span>|
|<span data-ttu-id="8fbfc-129">**PowerShell**</span><span class="sxs-lookup"><span data-stu-id="8fbfc-129">**PowerShell**</span></span>|<span data-ttu-id="8fbfc-130">PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="8fbfc-130">PowerShell Core 6</span></span>|

<span data-ttu-id="8fbfc-131">Pour en savoir plus, consultez [Langages pris en charge](/azure/azure-functions/supported-languages).</span><span class="sxs-lookup"><span data-stu-id="8fbfc-131">For more information, see [Supported languages](/azure/azure-functions/supported-languages).</span></span>

## <a name="app-service-plans"></a><span data-ttu-id="8fbfc-132">Plans App service</span><span class="sxs-lookup"><span data-stu-id="8fbfc-132">App service plans</span></span>

<span data-ttu-id="8fbfc-133">Les fonctions sont associées à un *plan App service*.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-133">Functions are backed by an *app service plan*.</span></span> <span data-ttu-id="8fbfc-134">Le plan définit les ressources utilisées par l’application functions.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-134">The plan defines the resources used by the functions app.</span></span> <span data-ttu-id="8fbfc-135">Vous pouvez affecter des plans à une région, déterminer la taille et le nombre d’ordinateurs virtuels qui seront utilisés, et choisir un niveau tarifaire.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-135">You can assign plans to a region, determine the size and number of virtual machines that will be used, and pick a pricing tier.</span></span> <span data-ttu-id="8fbfc-136">Pour une véritable approche sans serveur, les applications de fonction peuvent utiliser le plan de **consommation** .</span><span class="sxs-lookup"><span data-stu-id="8fbfc-136">For a true serverless approach, function apps may use the **consumption** plan.</span></span> <span data-ttu-id="8fbfc-137">Le plan de consommation met automatiquement à l’échelle le back end en fonction de la charge.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-137">The consumption plan will scale the back end automatically based on load.</span></span>

<span data-ttu-id="8fbfc-138">Le [plan Premium](/azure/azure-functions/functions-premium-plan)est une autre option d’hébergement pour les applications de fonction.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-138">Another hosting option for function apps is the [Premium plan](/azure/azure-functions/functions-premium-plan).</span></span> <span data-ttu-id="8fbfc-139">Ce plan fournit une instance « Always on » pour éviter le démarrage à froid, prend en charge des fonctionnalités avancées telles que la connectivité de réseau virtuel et s’exécute sur du matériel Premium.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-139">This plan provides an "always on" instance to avoid cold start, supports advanced features like VNet connectivity, and runs on premium hardware.</span></span>

<span data-ttu-id="8fbfc-140">Pour plus d’informations, consultez [plans App service](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span><span class="sxs-lookup"><span data-stu-id="8fbfc-140">For more information, see [App service plans](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

## <a name="create-your-first-function"></a><span data-ttu-id="8fbfc-141">Créer votre première fonction</span><span class="sxs-lookup"><span data-stu-id="8fbfc-141">Create your first function</span></span>

<span data-ttu-id="8fbfc-142">Il existe trois méthodes courantes pour créer des applications de fonction.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-142">There are three common ways you can create function apps.</span></span>

- <span data-ttu-id="8fbfc-143">Fonctions de script dans le portail.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-143">Script functions in the portal.</span></span>
- <span data-ttu-id="8fbfc-144">Créez les ressources nécessaires à l’aide de l’Azure CLI.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-144">Create the necessary resources using the Azure CLI.</span></span>
- <span data-ttu-id="8fbfc-145">Créez des fonctions localement à l’aide de votre IDE favori et publiez-les sur Azure.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-145">Build functions locally using your favorite IDE and publish them to Azure.</span></span>

<span data-ttu-id="8fbfc-146">Pour plus d’informations sur la création d’une fonction de script dans le portail, consultez [créer votre première fonction dans la portail Azure](/azure/azure-functions/functions-create-first-azure-function).</span><span class="sxs-lookup"><span data-stu-id="8fbfc-146">For more information on creating a scripted function in the portal, see [Create your first function in the Azure portal](/azure/azure-functions/functions-create-first-azure-function).</span></span>

<span data-ttu-id="8fbfc-147">Pour générer à partir de la Azure CLI, consultez [créer votre première fonction à l’aide de l’Azure CLI](/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span><span class="sxs-lookup"><span data-stu-id="8fbfc-147">To build from the Azure CLI, see [Create your first function using the Azure CLI](/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span></span>

<span data-ttu-id="8fbfc-148">Pour créer une fonction à partir de Visual Studio, consultez [créer votre première fonction à l’aide de Visual Studio](/azure/azure-functions/functions-create-your-first-function-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="8fbfc-148">To create a function from Visual Studio, see [Create your first function using Visual Studio](/azure/azure-functions/functions-create-your-first-function-visual-studio).</span></span>

## <a name="understand-triggers-and-bindings"></a><span data-ttu-id="8fbfc-149">Comprendre les déclencheurs et les liaisons</span><span class="sxs-lookup"><span data-stu-id="8fbfc-149">Understand triggers and bindings</span></span>

<span data-ttu-id="8fbfc-150">Les fonctions sont appelées par un *déclencheur* et ne peuvent en avoir qu’une seule.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-150">Functions are invoked by a *trigger* and can have exactly one.</span></span> <span data-ttu-id="8fbfc-151">Outre l’appel de la fonction, certains déclencheurs servent également de liaisons.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-151">In addition to invoking the function, certain triggers also serve as bindings.</span></span> <span data-ttu-id="8fbfc-152">Vous pouvez également définir plusieurs liaisons en plus du déclencheur.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-152">You may also define multiple bindings in addition to the trigger.</span></span> <span data-ttu-id="8fbfc-153">Les *liaisons* offrent un moyen déclaratif de connecter des données à votre code.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-153">*Bindings* provide a declarative way to connect data to your code.</span></span> <span data-ttu-id="8fbfc-154">Ils peuvent être transmis (entrée) ou recevoir des données (sortie).</span><span class="sxs-lookup"><span data-stu-id="8fbfc-154">They can be passed in (input) or receive data (output).</span></span> <span data-ttu-id="8fbfc-155">Les déclencheurs et les liaisons rendent les fonctions faciles à utiliser.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-155">Triggers and bindings make functions easy to work with.</span></span> <span data-ttu-id="8fbfc-156">Les liaisons suppriment la surcharge liée à la création manuelle de connexions de base de données ou de système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-156">Bindings remove the overhead of manually creating database or file system connections.</span></span> <span data-ttu-id="8fbfc-157">Toutes les informations nécessaires pour les liaisons sont contenues dans unfunctions.jsspécial \* sur\* le fichier pour les scripts ou déclarés avec des attributs dans le code.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-157">All of the information needed for the bindings is contained in a special *functions.json* file for scripts or declared with attributes in code.</span></span>

<span data-ttu-id="8fbfc-158">Parmi les déclencheurs les plus courants, citons :</span><span class="sxs-lookup"><span data-stu-id="8fbfc-158">Some common triggers include:</span></span>

- <span data-ttu-id="8fbfc-159">Stockage d’objets BLOB : appelez votre fonction lorsqu’un fichier ou un dossier est téléchargé ou modifié dans le stockage.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-159">Blob Storage: invoke your function when a file or folder is uploaded or changed in storage.</span></span>
- <span data-ttu-id="8fbfc-160">HTTP : appelez votre fonction comme une API REST.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-160">HTTP: invoke your function like a REST API.</span></span>
- <span data-ttu-id="8fbfc-161">Queue : appelez votre fonction lorsque des éléments existent dans une file d’attente.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-161">Queue: invoke your function when items exist in a queue.</span></span>
- <span data-ttu-id="8fbfc-162">Timer : appelez votre fonction sur une cadence régulière.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-162">Timer: invoke your function on a regular cadence.</span></span>

<span data-ttu-id="8fbfc-163">Voici quelques exemples de liaisons :</span><span class="sxs-lookup"><span data-stu-id="8fbfc-163">Examples of bindings include:</span></span>

- <span data-ttu-id="8fbfc-164">CosmosDB : Connectez-vous facilement à la base de données pour charger ou enregistrer des fichiers.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-164">CosmosDB: easily connect to the database to load or save files.</span></span>
- <span data-ttu-id="8fbfc-165">Stockage table : travaillez avec le stockage clé/valeur à partir de votre application de fonction.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-165">Table Storage: work with key/value storage from your function app.</span></span>
- <span data-ttu-id="8fbfc-166">Stockage file d’attente : récupérer facilement des éléments d’une file d’attente ou placer de nouveaux éléments dans la file d’attente.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-166">Queue Storage: easily retrieve items from a queue, or place new items on the queue.</span></span>

<span data-ttu-id="8fbfc-167">L’exemple suivant *functions.jssur* le fichier définit un déclencheur et une liaison :</span><span class="sxs-lookup"><span data-stu-id="8fbfc-167">The following example *functions.json* file defines a trigger and a binding:</span></span>

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

<span data-ttu-id="8fbfc-168">Dans cet exemple, la fonction est déclenchée par une modification du stockage d’objets BLOB dans le `images` conteneur.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-168">In this example, the function is triggered by a change to blob storage in the `images` container.</span></span> <span data-ttu-id="8fbfc-169">Les informations relatives au fichier étant transmises, le déclencheur joue également le rôle de liaison.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-169">The information for the file is passed in, so the trigger also acts as a binding.</span></span> <span data-ttu-id="8fbfc-170">Il existe une autre liaison pour placer des informations dans une file d’attente nommée `images` .</span><span class="sxs-lookup"><span data-stu-id="8fbfc-170">Another binding exists to put information onto a queue named `images`.</span></span>

<span data-ttu-id="8fbfc-171">Voici le script C# pour la fonction :</span><span class="sxs-lookup"><span data-stu-id="8fbfc-171">Here is the C# script for the function:</span></span>

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

<span data-ttu-id="8fbfc-172">L’exemple est une fonction simple qui prend le nom du fichier qui a été modifié ou téléchargé dans le stockage d’objets BLOB, et la place dans une file d’attente pour un traitement ultérieur.</span><span class="sxs-lookup"><span data-stu-id="8fbfc-172">The example is a simple function that takes the name of the file that was modified or uploaded to blob storage, and places it on a queue for later processing.</span></span>

<span data-ttu-id="8fbfc-173">Pour obtenir la liste complète des déclencheurs et des liaisons, consultez [Azure Functions les concepts de déclencheurs et de liaisons](/azure/azure-functions/functions-triggers-bindings).</span><span class="sxs-lookup"><span data-stu-id="8fbfc-173">For a full list of triggers and bindings, see [Azure Functions triggers and bindings concepts](/azure/azure-functions/functions-triggers-bindings).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8fbfc-174">[Précédent](azure-serverless-platform.md) 
> [Suivant](application-insights.md)</span><span class="sxs-lookup"><span data-stu-id="8fbfc-174">[Previous](azure-serverless-platform.md)
[Next](application-insights.md)</span></span>
