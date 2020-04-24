---
title: Exemples de scénarios d’entreprise et de cas d’utilisation pour les applications sans serveur
description: Découvrez sans serveur une approche pratique en accédant à des exemples qui vont du traitement de l’image à la prise en charge mobile et aux pipelines ETL.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/17/2020
ms.openlocfilehash: 5c2ee70b86fbc9a54d2a532eaa3d7509f23825df
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135657"
---
# <a name="serverless-business-scenarios-and-use-cases"></a><span data-ttu-id="96cae-103">Scénarios métier et cas d’usage serverless</span><span class="sxs-lookup"><span data-stu-id="96cae-103">Serverless business scenarios and use cases</span></span>

<span data-ttu-id="96cae-104">Il existe de nombreux scénarios et scénarios d’utilisation pour les applications sans serveur.</span><span class="sxs-lookup"><span data-stu-id="96cae-104">There are many use cases and scenarios for serverless applications.</span></span> <span data-ttu-id="96cae-105">Ce chapitre contient des exemples qui illustrent les différents scénarios.</span><span class="sxs-lookup"><span data-stu-id="96cae-105">This chapter includes samples that illustrate the different scenarios.</span></span> <span data-ttu-id="96cae-106">Les scénarios incluent des liens vers la documentation connexe et les référentiels de code source publics.</span><span class="sxs-lookup"><span data-stu-id="96cae-106">The scenarios include links to related documentation and public source code repositories.</span></span> <span data-ttu-id="96cae-107">Les exemples de ce chapitre vous permettent de commencer à créer et à mettre en œuvre des solutions sans serveur.</span><span class="sxs-lookup"><span data-stu-id="96cae-107">The samples in this chapter enable you to get started on your own building and implementing serverless solutions.</span></span>

## <a name="big-data-processing"></a><span data-ttu-id="96cae-108">Traitement du Big Data</span><span class="sxs-lookup"><span data-stu-id="96cae-108">Big data processing</span></span>

![Diagramme de mappage/réduction](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/media/mapreducearchitecture.png)

<span data-ttu-id="96cae-110">Cet exemple utilise sans serveur pour effectuer une opération de mappage/réduction sur un jeu de Big Data.</span><span class="sxs-lookup"><span data-stu-id="96cae-110">This example uses serverless to do a map/reduce operation on a big data set.</span></span> <span data-ttu-id="96cae-111">Il détermine la vitesse moyenne des voyages de taxis jaunes de New York par jour en 2017.</span><span class="sxs-lookup"><span data-stu-id="96cae-111">It determines the average speed of New York Yellow taxi trips per day in 2017.</span></span>

[<span data-ttu-id="96cae-112">Traitement des données Big Data : MapReduce sans serveur sur Azure</span><span class="sxs-lookup"><span data-stu-id="96cae-112">Big Data Processing: Serverless MapReduce on Azure</span></span>](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/)

## <a name="create-serverless-applications-hands-on-lab"></a><span data-ttu-id="96cae-113">Créer des applications sans serveur : laboratoire pratique</span><span class="sxs-lookup"><span data-stu-id="96cae-113">Create serverless applications: hands-on lab</span></span>

<span data-ttu-id="96cae-114">Découvrez comment utiliser les fonctions pour exécuter une logique côté serveur et créer des architectures sans serveur.</span><span class="sxs-lookup"><span data-stu-id="96cae-114">Learn how to use functions to execute server-side logic and build serverless architectures.</span></span>

- <span data-ttu-id="96cae-115">Choix du meilleur service Azure pour votre entreprise</span><span class="sxs-lookup"><span data-stu-id="96cae-115">Choosing the best Azure service for your business</span></span>
- <span data-ttu-id="96cae-116">Création d’Azure Functions</span><span class="sxs-lookup"><span data-stu-id="96cae-116">Creating Azure Functions</span></span>
- <span data-ttu-id="96cae-117">Utilisation de déclencheurs</span><span class="sxs-lookup"><span data-stu-id="96cae-117">Using triggers</span></span>
- <span data-ttu-id="96cae-118">Chaînage des fonctions</span><span class="sxs-lookup"><span data-stu-id="96cae-118">Chaining functions</span></span>
- <span data-ttu-id="96cae-119">Flux de travail de longue durée</span><span class="sxs-lookup"><span data-stu-id="96cae-119">Long-running workflows</span></span>
- <span data-ttu-id="96cae-120">Surveillance</span><span class="sxs-lookup"><span data-stu-id="96cae-120">Monitoring</span></span>
- <span data-ttu-id="96cae-121">Développement, test et déploiement</span><span class="sxs-lookup"><span data-stu-id="96cae-121">Development, testing, and deployment</span></span>

[<span data-ttu-id="96cae-122">Créer des applications sans serveur</span><span class="sxs-lookup"><span data-stu-id="96cae-122">Create serverless applications</span></span>](https://docs.microsoft.com/learn/paths/create-serverless-applications/)

## <a name="customer-reviews"></a><span data-ttu-id="96cae-123">Révisions client</span><span class="sxs-lookup"><span data-stu-id="96cae-123">Customer reviews</span></span>

<span data-ttu-id="96cae-124">Cet exemple illustre les nouveaux outils de Azure Functions pour les bibliothèques de classes C# dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="96cae-124">This sample showcases the new Azure Functions tooling for C# Class Libraries in Visual Studio.</span></span> <span data-ttu-id="96cae-125">Créez un site Web où les clients envoient des avis de produits stockés dans les objets BLOB de stockage Azure et CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="96cae-125">Create a website where customers submit product reviews that are stored in Azure storage blobs and CosmosDB.</span></span> <span data-ttu-id="96cae-126">Ajoutez une fonction Azure pour effectuer une modération automatique des évaluations des clients à l’aide d’Azure Cognitive Services.</span><span class="sxs-lookup"><span data-stu-id="96cae-126">Add an Azure Function to perform automated moderation of the customer reviews using Azure Cognitive Services.</span></span> <span data-ttu-id="96cae-127">Utilisez une file d’attente de stockage Azure pour découpler le site Web de la fonction.</span><span class="sxs-lookup"><span data-stu-id="96cae-127">Use an Azure storage queue to decouple the website from the function.</span></span>

[<span data-ttu-id="96cae-128">Application de révisions du client avec Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="96cae-128">Customer Reviews App with Cognitive Services</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-customer-reviews/customer-reviews-cognitive-services/)

## <a name="docker-linux-image-support"></a><span data-ttu-id="96cae-129">Prise en charge des images Linux de l’arrimeur</span><span class="sxs-lookup"><span data-stu-id="96cae-129">Docker Linux image support</span></span>

<span data-ttu-id="96cae-130">Cet exemple montre comment créer un `Dockerfile` pour générer et exécuter des Azure Functions sur un conteneur d’ancrage Linux.</span><span class="sxs-lookup"><span data-stu-id="96cae-130">This sample demonstrates how to create a `Dockerfile` to build and run Azure Functions on a Linux Docker container.</span></span>

[<span data-ttu-id="96cae-131">Azure Functions sur Linux</span><span class="sxs-lookup"><span data-stu-id="96cae-131">Azure Functions on Linux</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-linux-custom-image/azure-functions-on-linux-custom-image-tutorial-sample-project/)

## <a name="file-processing-and-validation"></a><span data-ttu-id="96cae-132">Traitement et validation des fichiers</span><span class="sxs-lookup"><span data-stu-id="96cae-132">File processing and validation</span></span>

<span data-ttu-id="96cae-133">Cet exemple analyse un ensemble de fichiers CSV provenant de clients hypothétiques.</span><span class="sxs-lookup"><span data-stu-id="96cae-133">This example parses a set of CSV files from hypothetical customers.</span></span> <span data-ttu-id="96cae-134">Il garantit que tous les fichiers requis pour un client « batch » sont prêts, puis valide la structure de chaque fichier.</span><span class="sxs-lookup"><span data-stu-id="96cae-134">It ensures that all files required for a customer "batch" are ready, then validates the structure of each file.</span></span> <span data-ttu-id="96cae-135">Différentes solutions sont présentées à l’aide de Azure Functions, Logic Apps et Durable Functions.</span><span class="sxs-lookup"><span data-stu-id="96cae-135">Different solutions are presented using Azure Functions, Logic Apps, and Durable Functions.</span></span>

[<span data-ttu-id="96cae-136">Traitement des fichiers et validation à l’aide de Azure Functions, Logic Apps et Durable Functions</span><span class="sxs-lookup"><span data-stu-id="96cae-136">File processing and validation using Azure Functions, Logic Apps, and Durable Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/serverless-file-validation/file-processing-and-validation-using-azure-functions-logic-apps-and-durable-functions/)

## <a name="game-data-visualization"></a><span data-ttu-id="96cae-137">Visualisation des données du jeu</span><span class="sxs-lookup"><span data-stu-id="96cae-137">Game data visualization</span></span>

![Télémétrie de jeu](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/media/points.png)

<span data-ttu-id="96cae-139">Exemple de la façon dont un développeur peut implémenter une solution de visualisation des données dans l’éditeur pour son jeu.</span><span class="sxs-lookup"><span data-stu-id="96cae-139">An example of how a developer could implement an in-editor data visualization solution for their game.</span></span> <span data-ttu-id="96cae-140">En fait, un plug-in de moteur 4 non réel et un plug-in Unity ont été développés à l’aide de cet exemple comme backend.</span><span class="sxs-lookup"><span data-stu-id="96cae-140">In fact, an Unreal Engine 4 Plugin and Unity Plugin were developed using this sample as its backend.</span></span> <span data-ttu-id="96cae-141">Le composant de service est indépendant du moteur de jeu.</span><span class="sxs-lookup"><span data-stu-id="96cae-141">The service component is game engine agnostic.</span></span>

[<span data-ttu-id="96cae-142">Visualisation de la télémétrie du jeu dans l’éditeur</span><span class="sxs-lookup"><span data-stu-id="96cae-142">In-editor game telemetry visualization</span></span>](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/)

## <a name="graphql"></a><span data-ttu-id="96cae-143">GraphQL</span><span class="sxs-lookup"><span data-stu-id="96cae-143">GraphQL</span></span>

<span data-ttu-id="96cae-144">Créer une fonction sans serveur qui expose une API GraphQL.</span><span class="sxs-lookup"><span data-stu-id="96cae-144">Create a serverless function that exposes a GraphQL API.</span></span>

[<span data-ttu-id="96cae-145">Fonctions sans serveur pour GraphQL</span><span class="sxs-lookup"><span data-stu-id="96cae-145">Serverless functions for GraphQL</span></span>](https://github.com/softchris/graphql-workshop-dotnet/blob/master/docs/workshop/4.md)

## <a name="internet-of-things-iot-reliable-edge-relay"></a><span data-ttu-id="96cae-146">Relais de périphérie Reliable Internet des objets (IoT)</span><span class="sxs-lookup"><span data-stu-id="96cae-146">Internet of Things (IoT) reliable edge relay</span></span>

![Architecture IoT](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/media/architecture.png)

<span data-ttu-id="96cae-148">Cet exemple implémente un nouveau protocole de communication pour activer la communication en amont fiable à partir des appareils IoT.</span><span class="sxs-lookup"><span data-stu-id="96cae-148">This sample implements a new communication protocol to enable reliable upstream communication from IoT devices.</span></span> <span data-ttu-id="96cae-149">Il automatise la détection et le renvoi des écarts de données.</span><span class="sxs-lookup"><span data-stu-id="96cae-149">It automates data gap detection and backfill.</span></span>

[<span data-ttu-id="96cae-150">Relais de périphérie Reliable IoT</span><span class="sxs-lookup"><span data-stu-id="96cae-150">IoT Reliable Edge Relay</span></span>](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/)

## <a name="microservices-reference-architecture"></a><span data-ttu-id="96cae-151">Architecture de référence des microservices</span><span class="sxs-lookup"><span data-stu-id="96cae-151">Microservices reference architecture</span></span>

![Architecture de référence](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/media/macro-architecture.png)

<span data-ttu-id="96cae-153">Architecture de référence qui vous guide tout au long du processus de prise de décision impliqué dans la conception, le développement et la diffusion de l’application RideShare by Relecloud (une société fictive).</span><span class="sxs-lookup"><span data-stu-id="96cae-153">A reference architecture that walks you through the decision-making process involved in designing, developing, and delivering the Rideshare by Relecloud application (a fictitious company).</span></span> <span data-ttu-id="96cae-154">Il comprend des instructions pratiques pour la configuration et le déploiement de tous les composants de l’architecture.</span><span class="sxs-lookup"><span data-stu-id="96cae-154">It includes hands-on instructions for configuring and deploying all of the architecture's components.</span></span>

[<span data-ttu-id="96cae-155">Architecture de référence des microservices sans serveur</span><span class="sxs-lookup"><span data-stu-id="96cae-155">Serverless Microservices reference architecture</span></span>](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/)

## <a name="migrate-console-apps-to-serverless"></a><span data-ttu-id="96cae-156">Migrer des applications console vers sans serveur</span><span class="sxs-lookup"><span data-stu-id="96cae-156">Migrate console apps to serverless</span></span>

<span data-ttu-id="96cae-157">Cet exemple est une fonction générique (`.csx` fichier) qui peut être utilisée pour convertir n’importe quelle application console en service Web HTTP dans Azure functions.</span><span class="sxs-lookup"><span data-stu-id="96cae-157">This sample is a generic function (`.csx` file) that can be used to convert any console application to an HTTP web service in Azure Functions.</span></span> <span data-ttu-id="96cae-158">Il vous suffit de modifier un fichier de configuration et de spécifier les paramètres d’entrée qui seront passés comme arguments à `.exe`l'.</span><span class="sxs-lookup"><span data-stu-id="96cae-158">All you have to do is edit a configuration file and specify what input parameters will be passed as arguments to the `.exe`.</span></span>

[<span data-ttu-id="96cae-159">Exécuter des applications de console sur Azure Functions</span><span class="sxs-lookup"><span data-stu-id="96cae-159">Run Console Apps on Azure Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-dotnet-migrating-console-apps/run-console-apps-on-azure-functions/)

## <a name="serverless-for-mobile"></a><span data-ttu-id="96cae-160">Sans serveur pour les appareils mobiles</span><span class="sxs-lookup"><span data-stu-id="96cae-160">Serverless for mobile</span></span>

<span data-ttu-id="96cae-161">Les Azure Functions sont faciles à implémenter et à gérer, et accessibles via HTTP.</span><span class="sxs-lookup"><span data-stu-id="96cae-161">Azure Functions are easy to implement and maintain, and accessible through HTTP.</span></span> <span data-ttu-id="96cae-162">Ils constituent un excellent moyen d’implémenter une API pour une application mobile.</span><span class="sxs-lookup"><span data-stu-id="96cae-162">They are a great way to implement an API for a mobile application.</span></span> <span data-ttu-id="96cae-163">Microsoft propose de superbes outils multiplateformes pour iOS, Android et Windows avec Xamarin.</span><span class="sxs-lookup"><span data-stu-id="96cae-163">Microsoft offers great cross-platform tools for iOS, Android, and Windows with Xamarin.</span></span> <span data-ttu-id="96cae-164">En tant que tel, Xamarin et Azure Functions fonctionnent bien ensemble.</span><span class="sxs-lookup"><span data-stu-id="96cae-164">As such, Xamarin and Azure Functions are working great together.</span></span> <span data-ttu-id="96cae-165">Cet article montre comment implémenter une fonction Azure dans le portail Web Azure ou dans Visual Studio au début, et comment créer un client multiplateforme avec Xamarin. Forms, qui s’exécute sur Android, iOS et Windows.</span><span class="sxs-lookup"><span data-stu-id="96cae-165">This article shows how to implement an Azure Function in the Azure Web Portal or in Visual Studio at first, and build a cross-platform client with Xamarin.Forms, running on Android, iOS, and Windows.</span></span>

[<span data-ttu-id="96cae-166">Implémentation d’une fonction Azure simple avec un client Xamarin. Forms</span><span class="sxs-lookup"><span data-stu-id="96cae-166">Implementing a simple Azure Function with a Xamarin.Forms client</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)

## <a name="serverless-messaging"></a><span data-ttu-id="96cae-167">Messagerie sans serveur</span><span class="sxs-lookup"><span data-stu-id="96cae-167">Serverless messaging</span></span>

<span data-ttu-id="96cae-168">Cet exemple montre comment utiliser Durable Functions modèle de ventilateur pour charger un nombre arbitraire de messages sur un nombre quelconque de sessions/partitions.</span><span class="sxs-lookup"><span data-stu-id="96cae-168">This sample shows how to utilize Durable Functions' fan out pattern to load an arbitrary number of messages across any number of sessions/partitions.</span></span> <span data-ttu-id="96cae-169">Il cible les files d’attente Service Bus, Event Hubs ou de stockage.</span><span class="sxs-lookup"><span data-stu-id="96cae-169">It targets Service Bus, Event Hubs, or Storage Queues.</span></span> <span data-ttu-id="96cae-170">L’exemple ajoute également la possibilité d’utiliser ces messages avec une autre fonction Azure et de charger les données de minutage qui en résultent dans un autre concentrateur d’événements.</span><span class="sxs-lookup"><span data-stu-id="96cae-170">The sample also adds the ability to consume those messages with another Azure Function and load the resulting timing data in to another Event Hub.</span></span> <span data-ttu-id="96cae-171">Les données sont ensuite ingérées dans Analytics services comme Azure Explorateur de données.</span><span class="sxs-lookup"><span data-stu-id="96cae-171">The data is then ingested into analytics services like Azure Data Explorer.</span></span>

[<span data-ttu-id="96cae-172">Générez et consommez des messages via les files d’attente Service Bus, Event Hubs et de stockage avec Azure Functions</span><span class="sxs-lookup"><span data-stu-id="96cae-172">Produce and Consume messages through Service Bus, Event Hubs, and Storage Queues with Azure Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/durable-functions-producer-consumer/product-consume-messages-az-functions/)

## <a name="recommended-resources"></a><span data-ttu-id="96cae-173">Ressources recommandées</span><span class="sxs-lookup"><span data-stu-id="96cae-173">Recommended resources</span></span>

- [<span data-ttu-id="96cae-174">Azure Functions sur Linux</span><span class="sxs-lookup"><span data-stu-id="96cae-174">Azure Functions on Linux</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-linux-custom-image/azure-functions-on-linux-custom-image-tutorial-sample-project/)
- [<span data-ttu-id="96cae-175">Traitement des données Big Data : MapReduce sans serveur sur Azure</span><span class="sxs-lookup"><span data-stu-id="96cae-175">Big Data Processing: Serverless MapReduce on Azure</span></span>](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/)
- [<span data-ttu-id="96cae-176">Créer des applications sans serveur</span><span class="sxs-lookup"><span data-stu-id="96cae-176">Create serverless applications</span></span>](https://docs.microsoft.com/learn/paths/create-serverless-applications/)
- [<span data-ttu-id="96cae-177">Application de révisions du client avec Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="96cae-177">Customer Reviews App with Cognitive Services</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-customer-reviews/customer-reviews-cognitive-services/)
- [<span data-ttu-id="96cae-178">Traitement des fichiers et validation à l’aide de Azure Functions, Logic Apps et Durable Functions</span><span class="sxs-lookup"><span data-stu-id="96cae-178">File processing and validation using Azure Functions, Logic Apps, and Durable Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/serverless-file-validation/file-processing-and-validation-using-azure-functions-logic-apps-and-durable-functions/)
- [<span data-ttu-id="96cae-179">Implémentation d’une fonction Azure simple avec un client Xamarin. Forms</span><span class="sxs-lookup"><span data-stu-id="96cae-179">Implementing a simple Azure Function with a Xamarin.Forms client</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)
- [<span data-ttu-id="96cae-180">Visualisation de la télémétrie du jeu dans l’éditeur</span><span class="sxs-lookup"><span data-stu-id="96cae-180">In-editor game telemetry visualization</span></span>](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/)
- [<span data-ttu-id="96cae-181">Relais de périphérie Reliable IoT</span><span class="sxs-lookup"><span data-stu-id="96cae-181">IoT Reliable Edge Relay</span></span>](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/)
- [<span data-ttu-id="96cae-182">Générez et consommez des messages via les files d’attente Service Bus, Event Hubs et de stockage avec Azure Functions</span><span class="sxs-lookup"><span data-stu-id="96cae-182">Produce and Consume messages through Service Bus, Event Hubs, and Storage Queues with Azure Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/durable-functions-producer-consumer/product-consume-messages-az-functions/)
- [<span data-ttu-id="96cae-183">Exécuter des applications de console sur Azure Functions</span><span class="sxs-lookup"><span data-stu-id="96cae-183">Run Console Apps on Azure Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-dotnet-migrating-console-apps/run-console-apps-on-azure-functions/)
- [<span data-ttu-id="96cae-184">Fonctions sans serveur pour GraphQL</span><span class="sxs-lookup"><span data-stu-id="96cae-184">Serverless functions for GraphQL</span></span>](https://github.com/softchris/graphql-workshop-dotnet/blob/master/docs/workshop/4.md)
- [<span data-ttu-id="96cae-185">Architecture de référence des microservices sans serveur</span><span class="sxs-lookup"><span data-stu-id="96cae-185">Serverless Microservices reference architecture</span></span>](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/)

>[!div class="step-by-step"]
><span data-ttu-id="96cae-186">[Précédent](orchestration-patterns.md)
>[suivant](serverless-conclusion.md)</span><span class="sxs-lookup"><span data-stu-id="96cae-186">[Previous](orchestration-patterns.md)
[Next](serverless-conclusion.md)</span></span>
