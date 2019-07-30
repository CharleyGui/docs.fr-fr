---
title: Bien démarrer avec le stockage File d’attente Azure en F#
description: Les files d’attente Azure fournissent une messagerie fiable et asynchrone entre les composants de l’application. La messagerie Cloud permet à vos composants d’application d’évoluer indépendamment.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 65af98fb88e91d709eb0e35907cbc2dc097634d0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630484"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a><span data-ttu-id="134b5-104">Prise en main du stockage de files d’attente Azure à l’aide de F\#</span><span class="sxs-lookup"><span data-stu-id="134b5-104">Get started with Azure Queue storage using F\#</span></span>

<span data-ttu-id="134b5-105">Le stockage de files d’attente Azure fournit une messagerie Cloud entre les composants d’application.</span><span class="sxs-lookup"><span data-stu-id="134b5-105">Azure Queue storage provides cloud messaging between application components.</span></span> <span data-ttu-id="134b5-106">Dans la conception d’applications à des fins de mise à l’échelle, les composants d’application sont souvent découplés, afin qu’ils puissent être mis à l’échelle indépendamment.</span><span class="sxs-lookup"><span data-stu-id="134b5-106">In designing applications for scale, application components are often decoupled, so that they can scale independently.</span></span> <span data-ttu-id="134b5-107">Le stockage file d’attente offre une messagerie asynchrone pour la communication entre les composants de l’application, qu’ils s’exécutent dans le Cloud, sur le bureau, sur un serveur local ou sur un appareil mobile.</span><span class="sxs-lookup"><span data-stu-id="134b5-107">Queue storage delivers asynchronous messaging for communication between application components, whether they are running in the cloud, on the desktop, on an on-premises server, or on a mobile device.</span></span> <span data-ttu-id="134b5-108">Le stockage de files d’attente prend également en charge la gestion des tâches asynchrones et la création de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="134b5-108">Queue storage also supports managing asynchronous tasks and building process work flows.</span></span>

### <a name="about-this-tutorial"></a><span data-ttu-id="134b5-109">À propos de ce didacticiel</span><span class="sxs-lookup"><span data-stu-id="134b5-109">About this tutorial</span></span>

<span data-ttu-id="134b5-110">Ce didacticiel montre comment écrire F# du code pour certaines tâches courantes à l’aide du stockage de files d’attente Azure.</span><span class="sxs-lookup"><span data-stu-id="134b5-110">This tutorial shows how to write F# code for some common tasks using Azure Queue storage.</span></span> <span data-ttu-id="134b5-111">Les tâches couvertes incluent la création et la suppression de files d’attente, ainsi que l’ajout, la lecture et la suppression de messages de file d’attente.</span><span class="sxs-lookup"><span data-stu-id="134b5-111">Tasks covered include creating and deleting queues and adding, reading, and deleting queue messages.</span></span>

<span data-ttu-id="134b5-112">Pour obtenir une vue d’ensemble conceptuelle du stockage de files d’attente, consultez [le guide .net pour le stockage de files d’attente](/azure/storage/storage-dotnet-how-to-use-queues).</span><span class="sxs-lookup"><span data-stu-id="134b5-112">For a conceptual overview of queue storage, please see [the .NET guide for queue storage](/azure/storage/storage-dotnet-how-to-use-queues).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="134b5-113">Prérequis</span><span class="sxs-lookup"><span data-stu-id="134b5-113">Prerequisites</span></span>

<span data-ttu-id="134b5-114">Pour utiliser ce guide, vous devez d’abord [créer un compte de stockage Azure](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="134b5-114">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="134b5-115">Vous aurez également besoin de votre clé d’accès de stockage pour ce compte.</span><span class="sxs-lookup"><span data-stu-id="134b5-115">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="134b5-116">Créer un F# script et démarrer F# interactive</span><span class="sxs-lookup"><span data-stu-id="134b5-116">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="134b5-117">Les exemples de cet article peuvent être utilisés dans une F# application ou un F# script.</span><span class="sxs-lookup"><span data-stu-id="134b5-117">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="134b5-118">Pour créer un F# script, créez un fichier avec l' `.fsx` extension, par exemple `queues.fsx`, dans votre F# environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="134b5-118">To create an F# script, create a file with the `.fsx` extension, for example `queues.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="134b5-119">Ensuite, utilisez un [Gestionnaire de package](package-management.md) comme [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) pour installer le `WindowsAzure.Storage` package et la `WindowsAzure.Storage.dll` référence dans votre script à `#r` l’aide d’une directive.</span><span class="sxs-lookup"><span data-stu-id="134b5-119">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="134b5-120">Ajouter des déclarations d’espace de noms</span><span class="sxs-lookup"><span data-stu-id="134b5-120">Add namespace declarations</span></span>

<span data-ttu-id="134b5-121">Ajoutez les instructions `open` suivantes au début `queues.fsx` du fichier:</span><span class="sxs-lookup"><span data-stu-id="134b5-121">Add the following `open` statements to the top of the `queues.fsx` file:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a><span data-ttu-id="134b5-122">Obtient votre chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="134b5-122">Get your connection string</span></span>

<span data-ttu-id="134b5-123">Vous aurez besoin d’une chaîne de connexion de stockage Azure pour ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="134b5-123">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="134b5-124">Pour plus d’informations sur les chaînes de connexion, consultez [configurer des chaînes de connexion de stockage](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="134b5-124">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="134b5-125">Pour le didacticiel, vous allez entrer votre chaîne de connexion dans votre script, comme suit:</span><span class="sxs-lookup"><span data-stu-id="134b5-125">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

<span data-ttu-id="134b5-126">Toutefois, cela n’est **pas recommandé** pour les projets réels.</span><span class="sxs-lookup"><span data-stu-id="134b5-126">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="134b5-127">Votre clé de compte de stockage est similaire au mot de passe racine de votre compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="134b5-127">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="134b5-128">Veillez toujours à protéger votre clé de compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="134b5-128">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="134b5-129">Évitez de la distribuer à d’autres utilisateurs, de la coder en dur ou de l’enregistrer dans un fichier texte brut accessible à d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="134b5-129">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="134b5-130">Vous pouvez régénérer votre clé à l’aide du portail Azure si vous pensez qu’elle a peut-être été compromise.</span><span class="sxs-lookup"><span data-stu-id="134b5-130">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="134b5-131">Pour les applications réelles, la meilleure façon de gérer votre chaîne de connexion de stockage se trouve dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="134b5-131">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="134b5-132">Pour extraire la chaîne de connexion d’un fichier de configuration, procédez comme suit:</span><span class="sxs-lookup"><span data-stu-id="134b5-132">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

<span data-ttu-id="134b5-133">L’utilisation d’Azure Configuration Manager est facultative.</span><span class="sxs-lookup"><span data-stu-id="134b5-133">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="134b5-134">Vous pouvez également utiliser une API telle que le type de `ConfigurationManager` .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="134b5-134">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="134b5-135">Analyser la chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="134b5-135">Parse the connection string</span></span>

<span data-ttu-id="134b5-136">Pour analyser la chaîne de connexion, utilisez:</span><span class="sxs-lookup"><span data-stu-id="134b5-136">To parse the connection string, use:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

<span data-ttu-id="134b5-137">Cela renverra un `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="134b5-137">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-queue-service-client"></a><span data-ttu-id="134b5-138">Créer le client service de File d’attente</span><span class="sxs-lookup"><span data-stu-id="134b5-138">Create the Queue service client</span></span>

<span data-ttu-id="134b5-139">La `CloudQueueClient` classe vous permet de récupérer des files d’attente stockées dans le stockage de files d’attente.</span><span class="sxs-lookup"><span data-stu-id="134b5-139">The `CloudQueueClient` class enables you to retrieve queues stored in Queue storage.</span></span> <span data-ttu-id="134b5-140">Voici un moyen de créer le client de service:</span><span class="sxs-lookup"><span data-stu-id="134b5-140">Here's one way to create the service client:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

<span data-ttu-id="134b5-141">Vous êtes maintenant prêt à écrire du code qui lit et écrit des données dans le stockage de files d’attente.</span><span class="sxs-lookup"><span data-stu-id="134b5-141">Now you are ready to write code that reads data from and writes data to Queue storage.</span></span>

## <a name="create-a-queue"></a><span data-ttu-id="134b5-142">Créer une file d’attente</span><span class="sxs-lookup"><span data-stu-id="134b5-142">Create a queue</span></span>

<span data-ttu-id="134b5-143">Cet exemple montre comment créer une file d’attente si elle n’existe pas déjà:</span><span class="sxs-lookup"><span data-stu-id="134b5-143">This example shows how to create a queue if it doesn't already exist:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a><span data-ttu-id="134b5-144">Insérer un message dans une file d’attente</span><span class="sxs-lookup"><span data-stu-id="134b5-144">Insert a message into a queue</span></span>

<span data-ttu-id="134b5-145">Pour insérer un message dans une file d’attente existante, commencez par `CloudQueueMessage`créer un nouveau.</span><span class="sxs-lookup"><span data-stu-id="134b5-145">To insert a message into an existing queue, first create a new `CloudQueueMessage`.</span></span> <span data-ttu-id="134b5-146">Ensuite, appelez la `AddMessage` méthode.</span><span class="sxs-lookup"><span data-stu-id="134b5-146">Next, call the `AddMessage` method.</span></span> <span data-ttu-id="134b5-147">Un `CloudQueueMessage` peut être créé à partir d’une chaîne (au format UTF-8) ou `byte` d’un tableau, comme suit:</span><span class="sxs-lookup"><span data-stu-id="134b5-147">A `CloudQueueMessage` can be created from either a string (in UTF-8 format) or a `byte` array, like this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a><span data-ttu-id="134b5-148">Lire le message suivant</span><span class="sxs-lookup"><span data-stu-id="134b5-148">Peek at the next message</span></span>

<span data-ttu-id="134b5-149">Vous pouvez lire le message au début de la file d’attente, sans le supprimer de la file d’attente, en `PeekMessage` appelant la méthode.</span><span class="sxs-lookup"><span data-stu-id="134b5-149">You can peek at the message in the front of a queue, without removing it from the queue, by calling the `PeekMessage` method.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a><span data-ttu-id="134b5-150">Obtenir le message suivant à traiter</span><span class="sxs-lookup"><span data-stu-id="134b5-150">Get the next message for processing</span></span>

<span data-ttu-id="134b5-151">Vous pouvez récupérer le message au début de la file d’attente à des fins de `GetMessage` traitement en appelant la méthode.</span><span class="sxs-lookup"><span data-stu-id="134b5-151">You can retrieve the message at the front of a queue for processing by calling the `GetMessage` method.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

<span data-ttu-id="134b5-152">Vous indiquez par la suite le traitement réussi du message `DeleteMessage`à l’aide de.</span><span class="sxs-lookup"><span data-stu-id="134b5-152">You later indicate successful processing of the message by using `DeleteMessage`.</span></span>

## <a name="change-the-contents-of-a-queued-message"></a><span data-ttu-id="134b5-153">Modifier le contenu d’un message en file d’attente</span><span class="sxs-lookup"><span data-stu-id="134b5-153">Change the contents of a queued message</span></span>

<span data-ttu-id="134b5-154">Vous pouvez modifier le contenu d’un message récupéré sur place dans la file d’attente.</span><span class="sxs-lookup"><span data-stu-id="134b5-154">You can change the contents of a retrieved message in-place in the queue.</span></span> <span data-ttu-id="134b5-155">Si le message représente une tâche de travail, vous pouvez utiliser cette fonctionnalité pour mettre à jour l’état de la tâche de travail.</span><span class="sxs-lookup"><span data-stu-id="134b5-155">If the message represents a work task, you could use this feature to update the status of the work task.</span></span> <span data-ttu-id="134b5-156">Le code suivant met à jour le message de file d’attente avec le nouveau contenu et définit le délai d’expiration de la visibilité pour étendre une autre 60 secondes.</span><span class="sxs-lookup"><span data-stu-id="134b5-156">The following code updates the queue message with new contents, and sets the visibility timeout to extend another 60 seconds.</span></span> <span data-ttu-id="134b5-157">Cela permet d’enregistrer l’état du travail associé au message et de donner au client une autre minute pour continuer à travailler sur le message.</span><span class="sxs-lookup"><span data-stu-id="134b5-157">This saves the state of work associated with the message, and gives the client another minute to continue working on the message.</span></span> <span data-ttu-id="134b5-158">Vous pouvez utiliser cette technique pour effectuer le suivi des flux de travail à plusieurs étapes sur les messages de la file d’attente, sans devoir recommencer depuis le début si une étape de traitement échoue en raison d’une défaillance matérielle ou logicielle.</span><span class="sxs-lookup"><span data-stu-id="134b5-158">You could use this technique to track multi-step workflows on queue messages, without having to start over from the beginning if a processing step fails due to hardware or software failure.</span></span> <span data-ttu-id="134b5-159">En règle générale, vous conservez également un nombre de nouvelles tentatives, et si le message est retenté plus d’un certain nombre de fois, vous le supprimez.</span><span class="sxs-lookup"><span data-stu-id="134b5-159">Typically, you would keep a retry count as well, and if the message is retried more than some number of times, you would delete it.</span></span> <span data-ttu-id="134b5-160">Cela protège contre un message qui déclenche une erreur d’application à chaque fois qu’il est traité.</span><span class="sxs-lookup"><span data-stu-id="134b5-160">This protects against a message that triggers an application error each time it is processed.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a><span data-ttu-id="134b5-161">Retirer le message suivant de la file d’attente</span><span class="sxs-lookup"><span data-stu-id="134b5-161">De-queue the next message</span></span>

<span data-ttu-id="134b5-162">Votre code met en file d’attente un message de la file d’attente en deux étapes.</span><span class="sxs-lookup"><span data-stu-id="134b5-162">Your code de-queues a message from a queue in two steps.</span></span> <span data-ttu-id="134b5-163">Lorsque vous appelez `GetMessage`, vous recevez le message suivant dans une file d’attente.</span><span class="sxs-lookup"><span data-stu-id="134b5-163">When you call `GetMessage`, you get the next message in a queue.</span></span> <span data-ttu-id="134b5-164">Un message retourné par `GetMessage` devient invisible à tout autre code lisant les messages de cette file d’attente.</span><span class="sxs-lookup"><span data-stu-id="134b5-164">A message returned from `GetMessage` becomes invisible to any other code reading messages from this queue.</span></span> <span data-ttu-id="134b5-165">Par défaut, ce message reste invisible pendant 30 secondes.</span><span class="sxs-lookup"><span data-stu-id="134b5-165">By default, this message stays invisible for 30 seconds.</span></span> <span data-ttu-id="134b5-166">Pour terminer la suppression du message de la file d’attente, vous `DeleteMessage`devez également appeler.</span><span class="sxs-lookup"><span data-stu-id="134b5-166">To finish removing the message from the queue, you must also call `DeleteMessage`.</span></span> <span data-ttu-id="134b5-167">Ce processus de suppression d’un message en deux étapes garantit que, si votre code ne parvient pas à traiter un message en raison d’une défaillance matérielle ou logicielle, une autre instance de votre code peut obtenir le même message et réessayer.</span><span class="sxs-lookup"><span data-stu-id="134b5-167">This two-step process of removing a message assures that if your code fails to process a message due to hardware or software failure, another instance of your code can get the same message and try again.</span></span> <span data-ttu-id="134b5-168">Votre code appelle `DeleteMessage` juste après le traitement du message.</span><span class="sxs-lookup"><span data-stu-id="134b5-168">Your code calls `DeleteMessage` right after the message has been processed.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a><span data-ttu-id="134b5-169">Utiliser des flux de travail asynchrones avec des API de stockage de files d’attente courantes</span><span class="sxs-lookup"><span data-stu-id="134b5-169">Use Async workflows with common Queue storage APIs</span></span>

<span data-ttu-id="134b5-170">Cet exemple montre comment utiliser un flux de travail asynchrone avec les API de stockage de files d’attente courantes.</span><span class="sxs-lookup"><span data-stu-id="134b5-170">This example shows how to use an async workflow with common Queue storage APIs.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a><span data-ttu-id="134b5-171">Options supplémentaires pour la suppression de la mise en file d’attente des messages</span><span class="sxs-lookup"><span data-stu-id="134b5-171">Additional options for de-queuing messages</span></span>

<span data-ttu-id="134b5-172">Il existe deux façons de personnaliser la récupération des messages à partir d’une file d’attente.</span><span class="sxs-lookup"><span data-stu-id="134b5-172">There are two ways you can customize message retrieval from a queue.</span></span>
<span data-ttu-id="134b5-173">Tout d’abord, vous pouvez obtenir un lot de messages (jusqu’à 32).</span><span class="sxs-lookup"><span data-stu-id="134b5-173">First, you can get a batch of messages (up to 32).</span></span> <span data-ttu-id="134b5-174">Deuxièmement, vous pouvez définir un délai d’invisibilité plus long ou plus faible, ce qui permet de traiter votre code plus ou moins rapidement pour traiter complètement chaque message.</span><span class="sxs-lookup"><span data-stu-id="134b5-174">Second, you can set a longer or shorter invisibility timeout, allowing your code more or less time to fully process each message.</span></span> <span data-ttu-id="134b5-175">L’exemple de code suivant `GetMessages` utilise pour recevoir 20 messages dans un appel, puis traite chaque message.</span><span class="sxs-lookup"><span data-stu-id="134b5-175">The following code example uses `GetMessages` to get 20 messages in one call and then processes each message.</span></span> <span data-ttu-id="134b5-176">Il définit également le délai d’expiration de l’invisibilité sur cinq minutes pour chaque message.</span><span class="sxs-lookup"><span data-stu-id="134b5-176">It also sets the invisibility timeout to five minutes for each message.</span></span> <span data-ttu-id="134b5-177">Notez que les 5 minutes commencent pour tous les messages en même temps. par conséquent, après 5 minutes écoulées depuis l' `GetMessages`appel à, tous les messages qui n’ont pas été supprimés sont à nouveau visibles.</span><span class="sxs-lookup"><span data-stu-id="134b5-177">Note that the 5 minutes starts for all messages at the same time, so after 5 minutes have passed since the call to `GetMessages`, any messages which have not been deleted will become visible again.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a><span data-ttu-id="134b5-178">Obtient la longueur de la file d’attente</span><span class="sxs-lookup"><span data-stu-id="134b5-178">Get the queue length</span></span>

<span data-ttu-id="134b5-179">Vous pouvez obtenir une estimation du nombre de messages dans une file d’attente.</span><span class="sxs-lookup"><span data-stu-id="134b5-179">You can get an estimate of the number of messages in a queue.</span></span> <span data-ttu-id="134b5-180">La `FetchAttributes` méthode demande à l’service de file d’attente de récupérer les attributs de la file d’attente, y compris le nombre de messages.</span><span class="sxs-lookup"><span data-stu-id="134b5-180">The `FetchAttributes` method asks the Queue service to retrieve the queue attributes, including the message count.</span></span> <span data-ttu-id="134b5-181">La `ApproximateMessageCount` propriété retourne la dernière valeur extraite par `FetchAttributes` la méthode, sans appeler l’service de file d’attente.</span><span class="sxs-lookup"><span data-stu-id="134b5-181">The `ApproximateMessageCount` property returns the last value retrieved by the `FetchAttributes` method, without calling the Queue service.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a><span data-ttu-id="134b5-182">Supprimer une file d’attente</span><span class="sxs-lookup"><span data-stu-id="134b5-182">Delete a queue</span></span>

<span data-ttu-id="134b5-183">Pour supprimer une file d’attente et tous les messages qu’elle contient, `Delete` appelez la méthode sur l’objet file d’attente.</span><span class="sxs-lookup"><span data-stu-id="134b5-183">To delete a queue and all the messages contained in it, call the `Delete` method on the queue object.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a><span data-ttu-id="134b5-184">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="134b5-184">Next steps</span></span>

<span data-ttu-id="134b5-185">Maintenant que vous avez appris les bases du stockage de files d’attente, suivez ces liens pour en savoir plus sur les tâches de stockage plus complexes.</span><span class="sxs-lookup"><span data-stu-id="134b5-185">Now that you've learned the basics of Queue storage, follow these links to learn about more complex storage tasks.</span></span>

- [<span data-ttu-id="134b5-186">API de stockage Azure pour .NET</span><span class="sxs-lookup"><span data-stu-id="134b5-186">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="134b5-187">Fournisseur de type de stockage Azure</span><span class="sxs-lookup"><span data-stu-id="134b5-187">Azure Storage Type Provider</span></span>](https://github.com/fsprojects/AzureStorageTypeProvider)
- [<span data-ttu-id="134b5-188">Blog de l’équipe stockage Azure</span><span class="sxs-lookup"><span data-stu-id="134b5-188">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [<span data-ttu-id="134b5-189">Configurer des chaînes de connexion de stockage Azure</span><span class="sxs-lookup"><span data-stu-id="134b5-189">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="134b5-190">Informations de référence sur l’API REST des services de stockage Azure</span><span class="sxs-lookup"><span data-stu-id="134b5-190">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
