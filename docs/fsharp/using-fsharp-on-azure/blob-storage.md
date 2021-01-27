---
title: 'Prise en main du stockage d’objets BLOB Azure à l’aide de F #'
description: Stockez des données non structurées dans le Cloud avec le stockage d’objets BLOB Azure.
author: sylvanc
ms.date: 09/20/2016
ms.custom: devx-track-fsharp
ms.openlocfilehash: 58c120c26a1e99481b49ae3a0fb096a2188f359e
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794811"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a><span data-ttu-id="07af5-103">Prise en main du stockage d’objets BLOB Azure à l’aide de F\#</span><span class="sxs-lookup"><span data-stu-id="07af5-103">Get started with Azure Blob Storage using F\#</span></span>

<span data-ttu-id="07af5-104">Le stockage BLOB Azure est un service qui stocke des données non structurées dans le Cloud en tant qu’objets/objets BLOB.</span><span class="sxs-lookup"><span data-stu-id="07af5-104">Azure Blob Storage is a service that stores unstructured data in the cloud as objects/blobs.</span></span> <span data-ttu-id="07af5-105">Ce service peut stocker tout type de données texte ou binaires, par exemple, un document, un fichier multimédia ou un programme d’installation d’application.</span><span class="sxs-lookup"><span data-stu-id="07af5-105">Blob storage can store any type of text or binary data, such as a document, media file, or application installer.</span></span> <span data-ttu-id="07af5-106">Le stockage d’objets blob est également appelé Stockage Blob.</span><span class="sxs-lookup"><span data-stu-id="07af5-106">Blob storage is also referred to as object storage.</span></span>

<span data-ttu-id="07af5-107">Cet article explique comment effectuer des tâches courantes à l’aide du stockage d’objets BLOB.</span><span class="sxs-lookup"><span data-stu-id="07af5-107">This article shows you how to perform common tasks using Blob storage.</span></span> <span data-ttu-id="07af5-108">Les exemples sont écrits à l’aide de F # à l’aide de la bibliothèque cliente Azure Storage pour .NET.</span><span class="sxs-lookup"><span data-stu-id="07af5-108">The samples are written using F# using the Azure Storage Client Library for .NET.</span></span> <span data-ttu-id="07af5-109">Les tâches traitées incluent le chargement, la liste, le téléchargement et la suppression d’objets BLOB.</span><span class="sxs-lookup"><span data-stu-id="07af5-109">The tasks covered include how to upload, list, download, and delete blobs.</span></span>

<span data-ttu-id="07af5-110">Pour obtenir une vue d’ensemble conceptuelle du stockage d’objets BLOB, consultez [le guide .net pour le stockage d’objets BLOB](/azure/storage/blobs/storage-quickstart-blobs-dotnet).</span><span class="sxs-lookup"><span data-stu-id="07af5-110">For a conceptual overview of blob storage, see [the .NET guide for blob storage](/azure/storage/blobs/storage-quickstart-blobs-dotnet).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="07af5-111">Prérequis</span><span class="sxs-lookup"><span data-stu-id="07af5-111">Prerequisites</span></span>

<span data-ttu-id="07af5-112">Pour utiliser ce guide, vous devez d’abord [créer un compte de stockage Azure](/azure/storage/common/storage-account-create).</span><span class="sxs-lookup"><span data-stu-id="07af5-112">To use this guide, you must first [create an Azure storage account](/azure/storage/common/storage-account-create).</span></span> <span data-ttu-id="07af5-113">Vous avez également besoin de votre clé d’accès de stockage pour ce compte.</span><span class="sxs-lookup"><span data-stu-id="07af5-113">You also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="07af5-114">Créer un script F # et démarrer F# Interactive</span><span class="sxs-lookup"><span data-stu-id="07af5-114">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="07af5-115">Les exemples de cet article peuvent être utilisés dans une application F # ou un script F #.</span><span class="sxs-lookup"><span data-stu-id="07af5-115">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="07af5-116">Pour créer un script F #, créez un fichier avec l' `.fsx` extension, par exemple `blobs.fsx` , dans votre environnement de développement f #.</span><span class="sxs-lookup"><span data-stu-id="07af5-116">To create an F# script, create a file with the `.fsx` extension, for example `blobs.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="07af5-117">Ensuite, utilisez un [Gestionnaire de package](package-management.md) comme [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) pour installer les `WindowsAzure.Storage` `Microsoft.WindowsAzure.ConfigurationManager` packages et et référence et `WindowsAzure.Storage.dll` `Microsoft.WindowsAzure.Configuration.dll` dans votre script à l’aide d’une `#r` directive.</span><span class="sxs-lookup"><span data-stu-id="07af5-117">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` and `Microsoft.WindowsAzure.ConfigurationManager` packages and reference `WindowsAzure.Storage.dll` and `Microsoft.WindowsAzure.Configuration.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="07af5-118">Ajout de déclarations d'espaces de noms</span><span class="sxs-lookup"><span data-stu-id="07af5-118">Add namespace declarations</span></span>

<span data-ttu-id="07af5-119">Ajoutez les instructions `open` suivantes au début du fichier `blobs.fsx` :</span><span class="sxs-lookup"><span data-stu-id="07af5-119">Add the following `open` statements to the top of the `blobs.fsx` file:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="07af5-120">Obtention de votre chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="07af5-120">Get your connection string</span></span>

<span data-ttu-id="07af5-121">Vous avez besoin d’une chaîne de connexion de stockage Azure pour ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="07af5-121">You need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="07af5-122">Pour plus d’informations sur les chaînes de connexion, consultez [configurer des chaînes de connexion de stockage](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="07af5-122">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="07af5-123">Pour le didacticiel, vous entrez votre chaîne de connexion dans votre script, comme suit :</span><span class="sxs-lookup"><span data-stu-id="07af5-123">For the tutorial, you enter your connection string in your script, like this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

<span data-ttu-id="07af5-124">Toutefois, cela n’est **pas recommandé** pour les projets réels.</span><span class="sxs-lookup"><span data-stu-id="07af5-124">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="07af5-125">Votre clé de compte de stockage est similaire au mot de passe racine pour votre compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="07af5-125">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="07af5-126">Veillez toujours à protéger votre clé de compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="07af5-126">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="07af5-127">Évitez de la communiquer à d’autres utilisateurs, de la coder en dur ou de l’enregistrer dans un fichier texte brut accessible à d’autres personnes.</span><span class="sxs-lookup"><span data-stu-id="07af5-127">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="07af5-128">Vous pouvez régénérer votre clé à l’aide de la Portail Azure si vous pensez qu’elle a peut-être été compromise.</span><span class="sxs-lookup"><span data-stu-id="07af5-128">You can regenerate your key using the Azure portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="07af5-129">Pour les applications réelles, la meilleure façon de gérer votre chaîne de connexion de stockage se trouve dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="07af5-129">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="07af5-130">Pour extraire la chaîne de connexion d’un fichier de configuration, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="07af5-130">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

<span data-ttu-id="07af5-131">L’utilisation d’Azure Configuration Manager est facultative.</span><span class="sxs-lookup"><span data-stu-id="07af5-131">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="07af5-132">Vous pouvez également utiliser une API telle que le type de .NET Framework `ConfigurationManager` .</span><span class="sxs-lookup"><span data-stu-id="07af5-132">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="07af5-133">Analyse de la chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="07af5-133">Parse the connection string</span></span>

<span data-ttu-id="07af5-134">Pour analyser la chaîne de connexion, utilisez :</span><span class="sxs-lookup"><span data-stu-id="07af5-134">To parse the connection string, use:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

<span data-ttu-id="07af5-135">Cela retourne un `CloudStorageAccount` .</span><span class="sxs-lookup"><span data-stu-id="07af5-135">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-some-local-dummy-data"></a><span data-ttu-id="07af5-136">Créer des données fictives locales</span><span class="sxs-lookup"><span data-stu-id="07af5-136">Create some local dummy data</span></span>

<span data-ttu-id="07af5-137">Avant de commencer, créez des données locales factices dans le répertoire de notre script.</span><span class="sxs-lookup"><span data-stu-id="07af5-137">Before you begin, create some dummy local data in the directory of our script.</span></span> <span data-ttu-id="07af5-138">Plus tard, vous téléchargez ces données.</span><span class="sxs-lookup"><span data-stu-id="07af5-138">Later you upload this data.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a><span data-ttu-id="07af5-139">Créer le client du service Blob</span><span class="sxs-lookup"><span data-stu-id="07af5-139">Create the Blob service client</span></span>

<span data-ttu-id="07af5-140">Le `CloudBlobClient` type vous permet de récupérer des conteneurs et des objets BLOB stockés dans le stockage d’objets BLOB.</span><span class="sxs-lookup"><span data-stu-id="07af5-140">The `CloudBlobClient` type enables you to retrieve containers and blobs stored in Blob storage.</span></span> <span data-ttu-id="07af5-141">Voici un moyen de créer le client du service :</span><span class="sxs-lookup"><span data-stu-id="07af5-141">Here's one way to create the service client:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

<span data-ttu-id="07af5-142">Vous êtes maintenant prêt à écrire du code qui lit et écrit des données dans le Blob Storage.</span><span class="sxs-lookup"><span data-stu-id="07af5-142">Now you are ready to write code that reads data from and writes data to Blob storage.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="07af5-143">Créez un conteneur.</span><span class="sxs-lookup"><span data-stu-id="07af5-143">Create a container</span></span>

<span data-ttu-id="07af5-144">Cet exemple montre comment créer un conteneur, si celui-ci n’existe pas encore :</span><span class="sxs-lookup"><span data-stu-id="07af5-144">This example shows how to create a container if it does not already exist:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

<span data-ttu-id="07af5-145">Le nouveau conteneur est privé par défaut, ce qui signifie que vous devez indiquer votre clé d’accès de stockage pour télécharger des objets blob depuis ce conteneur.</span><span class="sxs-lookup"><span data-stu-id="07af5-145">By default, the new container is private, meaning that you must specify your storage access key to download blobs from this container.</span></span> <span data-ttu-id="07af5-146">Si vous voulez que les fichiers du conteneur soient publics, vous pouvez configurer le conteneur en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="07af5-146">If you want to make the files within the container available to everyone, you can set the container to be public using the following code:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

<span data-ttu-id="07af5-147">Tous les utilisateurs d’Internet peuvent afficher des objets blob d’un conteneur public, mais vous ne pouvez les modifier ou les supprimer que si vous disposez de la clé d’accès du compte ou de la signature d'accès partagé adéquate.</span><span class="sxs-lookup"><span data-stu-id="07af5-147">Anyone on the Internet can see blobs in a public container, but you can modify or delete them only if you have the appropriate account access key or a shared access signature.</span></span>

## <a name="upload-a-blob-into-a-container"></a><span data-ttu-id="07af5-148">Charger un objet blob dans un conteneur</span><span class="sxs-lookup"><span data-stu-id="07af5-148">Upload a blob into a container</span></span>

<span data-ttu-id="07af5-149">Le service de stockage d’objets blob Azure prend en charge les objets blob de blocs et de page.</span><span class="sxs-lookup"><span data-stu-id="07af5-149">Azure Blob Storage supports block blobs and page blobs.</span></span> <span data-ttu-id="07af5-150">Dans la plupart des cas, un objet blob de blocs est le type recommandé à utiliser.</span><span class="sxs-lookup"><span data-stu-id="07af5-150">In most cases, a block blob is the recommended type to use.</span></span>

<span data-ttu-id="07af5-151">Pour télécharger un fichier vers un objet blob de blocs, obtenez une référence de conteneur et utilisez-la pour obtenir une référence d’objet blob de blocs.</span><span class="sxs-lookup"><span data-stu-id="07af5-151">To upload a file to a block blob, get a container reference and use it to get a block blob reference.</span></span> <span data-ttu-id="07af5-152">Une fois que vous avez une référence d’objet BLOB, vous pouvez charger n’importe quel flux de données en appelant la `UploadFromFile` méthode.</span><span class="sxs-lookup"><span data-stu-id="07af5-152">Once you have a blob reference, you can upload any stream of data to it by calling the `UploadFromFile` method.</span></span> <span data-ttu-id="07af5-153">Cette opération crée l’objet BLOB s’il n’existe pas déjà, ou le remplace s’il existe.</span><span class="sxs-lookup"><span data-stu-id="07af5-153">This operation creates the blob if it didn't previously exist, or overwrite it if it does exist.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a><span data-ttu-id="07af5-154">Créer la liste des objets blob d’un conteneur</span><span class="sxs-lookup"><span data-stu-id="07af5-154">List the blobs in a container</span></span>

<span data-ttu-id="07af5-155">Pour créer une liste d’objets blob dans un conteneur, commencez par obtenir une référence pointant vers un conteneur.</span><span class="sxs-lookup"><span data-stu-id="07af5-155">To list the blobs in a container, first get a container reference.</span></span> <span data-ttu-id="07af5-156">Vous pouvez ensuite utiliser la méthode du conteneur `ListBlobs` pour récupérer les objets BLOB et/ou les répertoires qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="07af5-156">You can then use the container's `ListBlobs` method to retrieve the blobs and/or directories within it.</span></span> <span data-ttu-id="07af5-157">Pour accéder à l’ensemble complet de propriétés et de méthodes pour un retourné `IListBlobItem` , vous devez effectuer un cast de celui-ci en un `CloudBlockBlob` `CloudPageBlob` objet, ou `CloudBlobDirectory` .</span><span class="sxs-lookup"><span data-stu-id="07af5-157">To access the rich set of properties and methods for a returned `IListBlobItem`, you must cast it to a `CloudBlockBlob`, `CloudPageBlob`, or `CloudBlobDirectory` object.</span></span> <span data-ttu-id="07af5-158">Si vous ne connaissez pas le type, vous pouvez lancer une vérification de type pour déterminer la cible de l’appel.</span><span class="sxs-lookup"><span data-stu-id="07af5-158">If the type is unknown, you can use a type check to determine which to cast it to.</span></span> <span data-ttu-id="07af5-159">Le code suivant illustre la récupération et la génération de l’URI de chaque élément du conteneur `mydata` :</span><span class="sxs-lookup"><span data-stu-id="07af5-159">The following code demonstrates how to retrieve and output the URI of each item in the `mydata` container:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

<span data-ttu-id="07af5-160">Vous pouvez également nommer des objets BLOB avec des informations de chemin d’accès dans leurs noms.</span><span class="sxs-lookup"><span data-stu-id="07af5-160">You can also name blobs with path information in their names.</span></span> <span data-ttu-id="07af5-161">Vous obtenez alors une structure de répertoires virtuels que vous pouvez organiser et parcourir de la même manière qu’un système de fichiers traditionnel.</span><span class="sxs-lookup"><span data-stu-id="07af5-161">This creates a virtual directory structure that you can organize and traverse as you would a traditional file system.</span></span> <span data-ttu-id="07af5-162">La structure de répertoires est virtuelle uniquement-les seules ressources disponibles dans le stockage d’objets BLOB sont des conteneurs et des objets BLOB.</span><span class="sxs-lookup"><span data-stu-id="07af5-162">The directory structure is virtual only - the only resources available in Blob storage are containers and blobs.</span></span> <span data-ttu-id="07af5-163">Toutefois, la bibliothèque cliente de stockage offre un `CloudBlobDirectory` objet pour faire référence à un répertoire virtuel et simplifier le processus d’utilisation des objets BLOB organisés de cette façon.</span><span class="sxs-lookup"><span data-stu-id="07af5-163">However, the storage client library offers a `CloudBlobDirectory` object to refer to a virtual directory and simplify the process of working with blobs that are organized in this way.</span></span>

<span data-ttu-id="07af5-164">Par exemple, prenez l’ensemble d’objets blob de blocs suivant, situé dans un conteneur nommé `photos`:</span><span class="sxs-lookup"><span data-stu-id="07af5-164">For example, consider the following set of block blobs in a container named `photos`:</span></span>

<span data-ttu-id="07af5-165">*photo1.jpg*</span><span class="sxs-lookup"><span data-stu-id="07af5-165">*photo1.jpg*</span></span>\
<span data-ttu-id="07af5-166">*2015/architecture/description.txt*</span><span class="sxs-lookup"><span data-stu-id="07af5-166">*2015/architecture/description.txt*</span></span>\
<span data-ttu-id="07af5-167">*2015/architecture/photo3.jpg*</span><span class="sxs-lookup"><span data-stu-id="07af5-167">*2015/architecture/photo3.jpg*</span></span>\
<span data-ttu-id="07af5-168">*2015/architecture/photo4.jpg*</span><span class="sxs-lookup"><span data-stu-id="07af5-168">*2015/architecture/photo4.jpg*</span></span>\
<span data-ttu-id="07af5-169">*2016/architecture/photo5.jpg*</span><span class="sxs-lookup"><span data-stu-id="07af5-169">*2016/architecture/photo5.jpg*</span></span>\
<span data-ttu-id="07af5-170">*2016/architecture/photo6.jpg*</span><span class="sxs-lookup"><span data-stu-id="07af5-170">*2016/architecture/photo6.jpg*</span></span>\
<span data-ttu-id="07af5-171">*2016/architecture/description.txt*</span><span class="sxs-lookup"><span data-stu-id="07af5-171">*2016/architecture/description.txt*</span></span>\
<span data-ttu-id="07af5-172">*2016/photo7.jpg*</span><span class="sxs-lookup"><span data-stu-id="07af5-172">*2016/photo7.jpg*</span></span>\

<span data-ttu-id="07af5-173">Lorsque vous appelez `ListBlobs` sur un conteneur (comme dans l’exemple ci-dessus), une liste hiérarchique est retournée.</span><span class="sxs-lookup"><span data-stu-id="07af5-173">When you call `ListBlobs` on a container (as in the above sample), a hierarchical listing is returned.</span></span> <span data-ttu-id="07af5-174">S’il contient à la fois des `CloudBlobDirectory` `CloudBlockBlob` objets et, représentant respectivement les répertoires et les objets BLOB du conteneur, le résultat obtenu ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="07af5-174">If it contains both `CloudBlobDirectory` and `CloudBlockBlob` objects, representing the directories and blobs in the container, respectively, then the resulting output looks similar to this:</span></span>

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

<span data-ttu-id="07af5-175">Si vous le souhaitez, vous pouvez définir le `UseFlatBlobListing` paramètre de la `ListBlobs` méthode sur `true` .</span><span class="sxs-lookup"><span data-stu-id="07af5-175">Optionally, you can set the `UseFlatBlobListing` parameter of the `ListBlobs` method to `true`.</span></span> <span data-ttu-id="07af5-176">Dans ce cas, tous les objets BLOB du conteneur sont retournés en tant qu' `CloudBlockBlob` objet.</span><span class="sxs-lookup"><span data-stu-id="07af5-176">In this case, every blob in the container is returned as a `CloudBlockBlob` object.</span></span> <span data-ttu-id="07af5-177">L’appel à `ListBlobs` pour retourner une liste plate ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="07af5-177">The call to `ListBlobs` to return a flat listing looks like this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

<span data-ttu-id="07af5-178">et, selon le contenu actuel de votre conteneur, les résultats ressemblent à ceci :</span><span class="sxs-lookup"><span data-stu-id="07af5-178">and, depending on the current contents of your container, the results look like this:</span></span>

```console
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2015/architecture/description.txt
Block blob of length 314618: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo3.jpg
Block blob of length 522713: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo4.jpg
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2016/architecture/description.txt
Block blob of length 419048: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo5.jpg
Block blob of length 506388: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo6.jpg
Block blob of length 399751: https://<accountname>.blob.core.windows.net/photos/2016/photo7.jpg
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

## <a name="download-blobs"></a><span data-ttu-id="07af5-179">Télécharger des objets blob</span><span class="sxs-lookup"><span data-stu-id="07af5-179">Download blobs</span></span>

<span data-ttu-id="07af5-180">Pour télécharger des objets BLOB, commencez par récupérer une référence d’objet BLOB, puis appelez la `DownloadToStream` méthode.</span><span class="sxs-lookup"><span data-stu-id="07af5-180">To download blobs, first retrieve a blob reference and then call the `DownloadToStream` method.</span></span> <span data-ttu-id="07af5-181">L’exemple suivant utilise la `DownloadToStream` méthode pour transférer le contenu de l’objet BLOB vers un objet de flux que vous pouvez ensuite conserver dans un fichier local.</span><span class="sxs-lookup"><span data-stu-id="07af5-181">The following example uses the `DownloadToStream` method to transfer the blob contents to a stream object that you can then persist to a local file.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

<span data-ttu-id="07af5-182">Vous pouvez également utiliser la `DownloadToStream` méthode pour télécharger le contenu d’un objet blob sous la forme d’une chaîne de texte.</span><span class="sxs-lookup"><span data-stu-id="07af5-182">You can also use the `DownloadToStream` method to download the contents of a blob as a text string.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a><span data-ttu-id="07af5-183">Suppression d’objets blob</span><span class="sxs-lookup"><span data-stu-id="07af5-183">Delete blobs</span></span>

<span data-ttu-id="07af5-184">Pour supprimer un objet BLOB, commencez par obtenir une référence d’objet BLOB, puis appelez la `Delete` méthode sur celui-ci.</span><span class="sxs-lookup"><span data-stu-id="07af5-184">To delete a blob, first get a blob reference and then call the `Delete` method on it.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a><span data-ttu-id="07af5-185">Création d’une liste d’objets blob dans des pages de manière asynchrone</span><span class="sxs-lookup"><span data-stu-id="07af5-185">List blobs in pages asynchronously</span></span>

<span data-ttu-id="07af5-186">Si vous répertoriez un grand nombre d’objets blob ou que vous souhaitez contrôler le nombre de résultats renvoyés lors d’une opération de création de liste, vous pouvez répertorier les objets blob dans des pages de résultats.</span><span class="sxs-lookup"><span data-stu-id="07af5-186">If you are listing a large number of blobs, or you want to control the number of results you return in one listing operation, you can list blobs in pages of results.</span></span> <span data-ttu-id="07af5-187">Cet exemple montre comment renvoyer les résultats dans des pages de manière asynchrone afin que l’exécution ne soit pas bloquée lorsqu’un ensemble volumineux de résultats est attendu.</span><span class="sxs-lookup"><span data-stu-id="07af5-187">This example shows how to return results in pages asynchronously, so that execution is not blocked while waiting to return a large set of results.</span></span>

<span data-ttu-id="07af5-188">Cet exemple montre une liste d’objets BLOB plats, mais vous pouvez également effectuer une liste hiérarchique en affectant au `useFlatBlobListing` paramètre de la méthode la valeur `ListBlobsSegmentedAsync` `false` .</span><span class="sxs-lookup"><span data-stu-id="07af5-188">This example shows a flat blob listing, but you can also perform a hierarchical listing, by setting the `useFlatBlobListing` parameter of the `ListBlobsSegmentedAsync` method to `false`.</span></span>

<span data-ttu-id="07af5-189">L’exemple définit une méthode asynchrone à l’aide d’un `async` bloc.</span><span class="sxs-lookup"><span data-stu-id="07af5-189">The sample defines an asynchronous method, using an `async` block.</span></span> <span data-ttu-id="07af5-190">Le ``let!`` mot clé interrompt l’exécution de l’exemple de méthode jusqu’à ce que la tâche de liste se termine.</span><span class="sxs-lookup"><span data-stu-id="07af5-190">The ``let!`` keyword suspends execution of the sample method until the listing task completes.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

<span data-ttu-id="07af5-191">Nous pouvons maintenant utiliser cette routine asynchrone comme suit.</span><span class="sxs-lookup"><span data-stu-id="07af5-191">We can now use this asynchronous routine as follows.</span></span> <span data-ttu-id="07af5-192">Tout d’abord, vous téléchargez des données factices (à l’aide du fichier local créé précédemment dans ce didacticiel).</span><span class="sxs-lookup"><span data-stu-id="07af5-192">First you upload some dummy data (using the local file created earlier in this tutorial).</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

<span data-ttu-id="07af5-193">À présent, appelez la routine.</span><span class="sxs-lookup"><span data-stu-id="07af5-193">Now, call the routine.</span></span> <span data-ttu-id="07af5-194">Vous utilisez `Async.RunSynchronously` pour forcer l’exécution de l’opération asynchrone.</span><span class="sxs-lookup"><span data-stu-id="07af5-194">You use `Async.RunSynchronously` to force the execution of the asynchronous operation.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a><span data-ttu-id="07af5-195">Écriture dans un objet blob d’ajout</span><span class="sxs-lookup"><span data-stu-id="07af5-195">Writing to an append blob</span></span>

<span data-ttu-id="07af5-196">Il est optimisé pour les opérations d’ajout, telles que la journalisation.</span><span class="sxs-lookup"><span data-stu-id="07af5-196">An append blob is optimized for append operations, such as logging.</span></span> <span data-ttu-id="07af5-197">À l’instar d’un objet blob de blocs, un objet blob d’ajout est composé de blocs, mais lorsque vous ajoutez un nouveau bloc à un objet blob d’ajout, il est toujours ajouté à la fin de l’objet BLOB.</span><span class="sxs-lookup"><span data-stu-id="07af5-197">Like a block blob, an append blob is composed of blocks, but when you add a new block to an append blob, it is always appended to the end of the blob.</span></span> <span data-ttu-id="07af5-198">Vous ne pouvez pas mettre à jour ou supprimer un bloc dans un objet blob d’ajout.</span><span class="sxs-lookup"><span data-stu-id="07af5-198">You cannot update or delete an existing block in an append blob.</span></span> <span data-ttu-id="07af5-199">Les ID de bloc dans un objet blob d’ajout ne sont pas visibles, comme pour un objet blob de blocs.</span><span class="sxs-lookup"><span data-stu-id="07af5-199">The block IDs for an append blob are not exposed as they are for a block blob.</span></span>

<span data-ttu-id="07af5-200">Chaque bloc d’un objet blob d’ajout peut avoir une taille différente (jusqu’à 4 Mo), et un objet blob d’ajout peut contenir au maximum 50 000 blocs.</span><span class="sxs-lookup"><span data-stu-id="07af5-200">Each block in an append blob can be a different size, up to a maximum of 4 MB, and an append blob can include a maximum of 50,000 blocks.</span></span> <span data-ttu-id="07af5-201">La taille maximale d’un objet blob d’ajout est donc légèrement supérieure à 195 Go (4 Mo x 50 000 blocs).</span><span class="sxs-lookup"><span data-stu-id="07af5-201">The maximum size of an append blob is therefore slightly more than 195 GB (4 MB X 50,000 blocks).</span></span>

<span data-ttu-id="07af5-202">L’exemple suivant crée un nouvel objet blob d’ajout et y ajoute des données, en simulant une opération de journalisation simple.</span><span class="sxs-lookup"><span data-stu-id="07af5-202">The following example creates a new append blob and appends some data to it, simulating a simple logging operation.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

<span data-ttu-id="07af5-203">Pour plus d’informations sur les différences entre les trois types d’objets blob, consultez la page [Présentation des objets blob de blocs, des objets blob d’ajout et des objets blob de pages](/rest/api/storageservices/Understanding-Block-Blobs--Append-Blobs--and-Page-Blobs) .</span><span class="sxs-lookup"><span data-stu-id="07af5-203">See [Understanding Block Blobs, Page Blobs, and Append Blobs](/rest/api/storageservices/Understanding-Block-Blobs--Append-Blobs--and-Page-Blobs) for more information about the differences between the three types of blobs.</span></span>

## <a name="concurrent-access"></a><span data-ttu-id="07af5-204">Accès simultané</span><span class="sxs-lookup"><span data-stu-id="07af5-204">Concurrent access</span></span>

<span data-ttu-id="07af5-205">Pour activer la prise en charge de l’accès simultané à un objet blob par plusieurs clients ou instances de processus, vous pouvez utiliser **ETags** ou **leases**.</span><span class="sxs-lookup"><span data-stu-id="07af5-205">To support concurrent access to a blob from multiple clients or multiple process instances, you can use **ETags** or **leases**.</span></span>

- <span data-ttu-id="07af5-206">**Etag** : permet de détecter la modification de l’objet blob ou du conteneur par un autre processus</span><span class="sxs-lookup"><span data-stu-id="07af5-206">**Etag** - provides a way to detect that the blob or container has been modified by another process</span></span>

- <span data-ttu-id="07af5-207">**Bail** -fournit un moyen d’obtenir un accès exclusif, renouvelable, d’écriture ou de suppression à un objet BLOB pendant une période donnée.</span><span class="sxs-lookup"><span data-stu-id="07af5-207">**Lease** - provides a way to obtain exclusive, renewable, write, or delete access to a blob for a period of time</span></span>

<span data-ttu-id="07af5-208">Pour plus d’informations, consultez [gestion de l’accès concurrentiel dans stockage Microsoft Azure](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span><span class="sxs-lookup"><span data-stu-id="07af5-208">For more information, see [Managing Concurrency in Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span></span>

## <a name="naming-containers"></a><span data-ttu-id="07af5-209">Nommer des conteneurs</span><span class="sxs-lookup"><span data-stu-id="07af5-209">Naming containers</span></span>

<span data-ttu-id="07af5-210">Chaque objet blob du stockage Azure doit résider dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="07af5-210">Every blob in Azure storage must reside in a container.</span></span> <span data-ttu-id="07af5-211">Le conteneur fait partie du nom d'objet blob.</span><span class="sxs-lookup"><span data-stu-id="07af5-211">The container forms part of the blob name.</span></span> <span data-ttu-id="07af5-212">Par exemple, `mydata` est le nom du conteneur dans ces exemples d’URI d’objet blob :</span><span class="sxs-lookup"><span data-stu-id="07af5-212">For example, `mydata` is the name of the container in these sample blob URIs:</span></span>

- `https://storagesample.blob.core.windows.net/mydata/blob1.txt`
- `https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg`

<span data-ttu-id="07af5-213">Un conteneur doit posséder un nom DNS valide, conforme aux règles de nommage suivantes :</span><span class="sxs-lookup"><span data-stu-id="07af5-213">A container name must be a valid DNS name, conforming to the following naming rules:</span></span>

1. <span data-ttu-id="07af5-214">Les noms de conteneur doivent commencer par une lettre ou un chiffre, et peuvent comporter uniquement des lettres, des chiffres et des tirets (-).</span><span class="sxs-lookup"><span data-stu-id="07af5-214">Container names must start with a letter or number, and can contain only letters, numbers, and the dash (-) character.</span></span>
1. <span data-ttu-id="07af5-215">Chaque tiret (-) doit être immédiatement précédé et suivi d’une lettre ou d’un chiffre ; les tirets consécutifs sont interdits.</span><span class="sxs-lookup"><span data-stu-id="07af5-215">Every dash (-) character must be immediately preceded and followed by a letter or number; consecutive dashes are not permitted in container names.</span></span>
1. <span data-ttu-id="07af5-216">Toutes les lettres du conteneur doivent être minuscules.</span><span class="sxs-lookup"><span data-stu-id="07af5-216">All letters in a container name must be lowercase.</span></span>
1. <span data-ttu-id="07af5-217">Les noms de conteneurs doivent comporter entre 3 et 63 caractères.</span><span class="sxs-lookup"><span data-stu-id="07af5-217">Container names must be from 3 through 63 characters long.</span></span>

<span data-ttu-id="07af5-218">Le nom d’un conteneur doit toujours être en minuscules.</span><span class="sxs-lookup"><span data-stu-id="07af5-218">The name of a container must always be lowercase.</span></span> <span data-ttu-id="07af5-219">Si vous incluez une majuscule dans un nom de conteneur ou si vous ne respectez pas les règles d'affectation de noms, vous pouvez recevoir une erreur 400 (demande incorrecte).</span><span class="sxs-lookup"><span data-stu-id="07af5-219">If you include an upper-case letter in a container name, or otherwise violate the container naming rules, you may receive a 400 error (Bad Request).</span></span>

## <a name="managing-security-for-blobs"></a><span data-ttu-id="07af5-220">Gestion de la sécurité pour les objets blob</span><span class="sxs-lookup"><span data-stu-id="07af5-220">Managing security for blobs</span></span>

<span data-ttu-id="07af5-221">Par défaut, Azure Storage préserve la sécurité de vos données en limitant l’accès au propriétaire du compte, qui est en possession des clés d’accès au compte.</span><span class="sxs-lookup"><span data-stu-id="07af5-221">By default, Azure Storage keeps your data secure by limiting access to the account owner, who is in possession of the account access keys.</span></span> <span data-ttu-id="07af5-222">Lorsque vous avez besoin de partager des données d’objets blob de votre compte de stockage, il est important de le faire sans compromettre la sécurité de vos clés d’accès au compte.</span><span class="sxs-lookup"><span data-stu-id="07af5-222">When you need to share blob data in your storage account, it is important to do so without compromising the security of your account access keys.</span></span> <span data-ttu-id="07af5-223">En outre, vous pouvez chiffrer les données d’objets blob pour vous assurer qu’elles sont sécurisées lors de leur transfert et dans Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="07af5-223">Additionally, you can encrypt blob data to ensure that it is secure going over the wire and in Azure Storage.</span></span>

### <a name="controlling-access-to-blob-data"></a><span data-ttu-id="07af5-224">Contrôle de l’accès aux données d’objets blob</span><span class="sxs-lookup"><span data-stu-id="07af5-224">Controlling access to blob data</span></span>

<span data-ttu-id="07af5-225">Par défaut, les données d’objets blob de votre compte de stockage sont accessibles uniquement par le propriétaire du compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="07af5-225">By default, the blob data in your storage account is accessible only to storage account owner.</span></span> <span data-ttu-id="07af5-226">L’authentification des demandes vis-à-vis du stockage d’objets blob requiert la clé d’accès par défaut.</span><span class="sxs-lookup"><span data-stu-id="07af5-226">Authenticating requests against Blob storage requires the account access key by default.</span></span> <span data-ttu-id="07af5-227">Toutefois, vous souhaiterez peut-être mettre certaines données BLOB à la disposition d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="07af5-227">However, you might want to make certain blob data available to other users.</span></span>

### <a name="encrypting-blob-data"></a><span data-ttu-id="07af5-228">Chiffrement des données d’objets blob</span><span class="sxs-lookup"><span data-stu-id="07af5-228">Encrypting blob data</span></span>

<span data-ttu-id="07af5-229">Le stockage Azure prend en charge le chiffrement des données BLOB à la fois sur le client et sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="07af5-229">Azure Storage supports encrypting blob data both at the client and on the server.</span></span>

## <a name="next-steps"></a><span data-ttu-id="07af5-230">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="07af5-230">Next steps</span></span>

<span data-ttu-id="07af5-231">Maintenant que vous connaissez les bases du stockage d’objets blob, consultez les liens suivants pour en savoir plus.</span><span class="sxs-lookup"><span data-stu-id="07af5-231">Now that you've learned the basics of Blob storage, follow these links to learn more.</span></span>

### <a name="tools"></a><span data-ttu-id="07af5-232">Outils</span><span class="sxs-lookup"><span data-stu-id="07af5-232">Tools</span></span>

- <span data-ttu-id="07af5-233">[AzureStorageTypeProvider F #](https://fsprojects.github.io/AzureStorageTypeProvider/)</span><span class="sxs-lookup"><span data-stu-id="07af5-233">[F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)</span></span>\
<span data-ttu-id="07af5-234">Fournisseur de type F # qui peut être utilisé pour explorer des ressources de stockage Azure d’objets BLOB, de tables et de files d’attente et pour appliquer facilement des opérations CRUD sur ces derniers.</span><span class="sxs-lookup"><span data-stu-id="07af5-234">An F# Type Provider that can be used to explore Blob, Table, and Queue Azure Storage assets and easily apply CRUD operations on them.</span></span>

- <span data-ttu-id="07af5-235">[FSharp. Azure. Storage](https://github.com/fsprojects/FSharp.Azure.Storage)</span><span class="sxs-lookup"><span data-stu-id="07af5-235">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)</span></span>\
<span data-ttu-id="07af5-236">API F # pour l’utilisation du service de stockage de table Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="07af5-236">An F# API for using Microsoft Azure Table Storage service</span></span>

- <span data-ttu-id="07af5-237">[Explorateur Stockage Microsoft Azure (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)</span><span class="sxs-lookup"><span data-stu-id="07af5-237">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)</span></span>\
<span data-ttu-id="07af5-238">Une application autonome et gratuite de Microsoft qui vous permet de travailler visuellement avec les données de stockage Azure sur Windows, OS X et Linux.</span><span class="sxs-lookup"><span data-stu-id="07af5-238">A free, standalone app from Microsoft that enables you to work visually with Azure Storage data on Windows, OS X, and Linux.</span></span>

### <a name="blob-storage-reference"></a><span data-ttu-id="07af5-239">Documentation de référence sur le stockage d’objets blob</span><span class="sxs-lookup"><span data-stu-id="07af5-239">Blob storage reference</span></span>

- [<span data-ttu-id="07af5-240">API de stockage Azure pour .NET</span><span class="sxs-lookup"><span data-stu-id="07af5-240">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="07af5-241">Référence de l'API REST des services de Stockage Azure</span><span class="sxs-lookup"><span data-stu-id="07af5-241">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/)

### <a name="related-guides"></a><span data-ttu-id="07af5-242">Guides connexes</span><span class="sxs-lookup"><span data-stu-id="07af5-242">Related guides</span></span>

- [<span data-ttu-id="07af5-243">Exemples de stockage d’objets blob Azure pour .NET</span><span class="sxs-lookup"><span data-stu-id="07af5-243">Azure Blob Storage Samples for .NET</span></span>](/samples/azure-samples/storage-blob-dotnet-getting-started/storage-blob-dotnet-getting-started/)
- [<span data-ttu-id="07af5-244">Bien démarrer avec AzCopy</span><span class="sxs-lookup"><span data-stu-id="07af5-244">Get started with AzCopy</span></span>](/azure/storage/common/storage-use-azcopy-v10)
- [<span data-ttu-id="07af5-245">Configuration des chaînes de connexion du Stockage Azure</span><span class="sxs-lookup"><span data-stu-id="07af5-245">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="07af5-246">Blog de l'équipe Azure Storage</span><span class="sxs-lookup"><span data-stu-id="07af5-246">Azure Storage Team Blog</span></span>](/archive/blogs/windowsazurestorage/)
- [<span data-ttu-id="07af5-247">Démarrage rapide : Utiliser .NET pour créer un objet blob dans le stockage d’objets</span><span class="sxs-lookup"><span data-stu-id="07af5-247">Quickstart: Use .NET to create a blob in object storage</span></span>](/azure/storage/blobs/storage-quickstart-blobs-dotnet)
