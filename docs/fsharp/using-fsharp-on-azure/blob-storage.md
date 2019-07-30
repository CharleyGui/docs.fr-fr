---
title: Bien démarrer avec le stockage Blob Azure en F#
description: Stockez des données non structurées dans le Cloud avec le stockage d’objets BLOB Azure.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: c8b42339ff1d76f262e956b5e34cc598e0fc855d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630507"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a><span data-ttu-id="b6d90-103">Prise en main du stockage d’objets BLOB Azure à l’aide de F\#</span><span class="sxs-lookup"><span data-stu-id="b6d90-103">Get started with Azure Blob storage using F\#</span></span>

<span data-ttu-id="b6d90-104">Le stockage Blob Azure est un service qui stocke les données non structurées dans le cloud en tant qu’objets/objets blob.</span><span class="sxs-lookup"><span data-stu-id="b6d90-104">Azure Blob storage is a service that stores unstructured data in the cloud as objects/blobs.</span></span> <span data-ttu-id="b6d90-105">Le stockage Blob permet de stocker n’importe quel type de données texte ou binaires, par exemple un document, un fichier multimédia ou un programme d’installation d’application.</span><span class="sxs-lookup"><span data-stu-id="b6d90-105">Blob storage can store any type of text or binary data, such as a document, media file, or application installer.</span></span> <span data-ttu-id="b6d90-106">Le stockage Blob est également appelé stockage d’objets.</span><span class="sxs-lookup"><span data-stu-id="b6d90-106">Blob storage is also referred to as object storage.</span></span>

<span data-ttu-id="b6d90-107">Cet article explique comment effectuer des tâches courantes à l’aide du stockage d’objets BLOB.</span><span class="sxs-lookup"><span data-stu-id="b6d90-107">This article shows you how to perform common tasks using Blob storage.</span></span> <span data-ttu-id="b6d90-108">Les exemples sont écrits à F# l’aide de la bibliothèque cliente de stockage Azure pour .net.</span><span class="sxs-lookup"><span data-stu-id="b6d90-108">The samples are written using F# using the Azure Storage Client Library for .NET.</span></span> <span data-ttu-id="b6d90-109">Les tâches traitées incluent le chargement, la liste, le téléchargement et la suppression d’objets BLOB.</span><span class="sxs-lookup"><span data-stu-id="b6d90-109">The tasks covered include how to upload, list, download, and delete blobs.</span></span>

<span data-ttu-id="b6d90-110">Pour obtenir une vue d’ensemble conceptuelle du stockage d’objets BLOB, consultez [le guide .net pour le stockage d’objets BLOB](/azure/storage/storage-dotnet-how-to-use-blobs).</span><span class="sxs-lookup"><span data-stu-id="b6d90-110">For a conceptual overview of blob storage, see [the .NET guide for blob storage](/azure/storage/storage-dotnet-how-to-use-blobs).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b6d90-111">Prérequis</span><span class="sxs-lookup"><span data-stu-id="b6d90-111">Prerequisites</span></span>

<span data-ttu-id="b6d90-112">Pour utiliser ce guide, vous devez d’abord [créer un compte de stockage Azure](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="b6d90-112">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span> <span data-ttu-id="b6d90-113">Vous avez également besoin de votre clé d’accès de stockage pour ce compte.</span><span class="sxs-lookup"><span data-stu-id="b6d90-113">You also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="b6d90-114">Créer un F# script et démarrer F# interactive</span><span class="sxs-lookup"><span data-stu-id="b6d90-114">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="b6d90-115">Les exemples de cet article peuvent être utilisés dans une F# application ou un F# script.</span><span class="sxs-lookup"><span data-stu-id="b6d90-115">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="b6d90-116">Pour créer un F# script, créez un fichier avec l' `.fsx` extension, par exemple `blobs.fsx`, dans votre F# environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="b6d90-116">To create an F# script, create a file with the `.fsx` extension, for example `blobs.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="b6d90-117">Ensuite, utilisez un [Gestionnaire de package](package-management.md) comme [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) pour installer les `WindowsAzure.Storage` `Microsoft.WindowsAzure.ConfigurationManager` packages et et référence `WindowsAzure.Storage.dll` `Microsoft.WindowsAzure.Configuration.dll` et dans votre script à l' `#r` aide d’une directive.</span><span class="sxs-lookup"><span data-stu-id="b6d90-117">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` and `Microsoft.WindowsAzure.ConfigurationManager` packages and reference `WindowsAzure.Storage.dll` and `Microsoft.WindowsAzure.Configuration.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="b6d90-118">Ajouter des déclarations d’espace de noms</span><span class="sxs-lookup"><span data-stu-id="b6d90-118">Add namespace declarations</span></span>

<span data-ttu-id="b6d90-119">Ajoutez les instructions `open` suivantes au début `blobs.fsx` du fichier:</span><span class="sxs-lookup"><span data-stu-id="b6d90-119">Add the following `open` statements to the top of the `blobs.fsx` file:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="b6d90-120">Obtient votre chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="b6d90-120">Get your connection string</span></span>

<span data-ttu-id="b6d90-121">Vous avez besoin d’une chaîne de connexion de stockage Azure pour ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="b6d90-121">You need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="b6d90-122">Pour plus d’informations sur les chaînes de connexion, consultez [configurer des chaînes de connexion de stockage](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="b6d90-122">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="b6d90-123">Pour le didacticiel, vous entrez votre chaîne de connexion dans votre script, comme suit:</span><span class="sxs-lookup"><span data-stu-id="b6d90-123">For the tutorial, you enter your connection string in your script, like this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

<span data-ttu-id="b6d90-124">Toutefois, cela n’est **pas recommandé** pour les projets réels.</span><span class="sxs-lookup"><span data-stu-id="b6d90-124">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="b6d90-125">Votre clé de compte de stockage est similaire au mot de passe racine de votre compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="b6d90-125">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="b6d90-126">Veillez toujours à protéger votre clé de compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="b6d90-126">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="b6d90-127">Évitez de la distribuer à d’autres utilisateurs, de la coder en dur ou de l’enregistrer dans un fichier texte brut accessible à d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="b6d90-127">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="b6d90-128">Vous pouvez régénérer votre clé à l’aide du portail Azure si vous pensez qu’elle a peut-être été compromise.</span><span class="sxs-lookup"><span data-stu-id="b6d90-128">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="b6d90-129">Pour les applications réelles, la meilleure façon de gérer votre chaîne de connexion de stockage se trouve dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="b6d90-129">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="b6d90-130">Pour extraire la chaîne de connexion d’un fichier de configuration, procédez comme suit:</span><span class="sxs-lookup"><span data-stu-id="b6d90-130">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

<span data-ttu-id="b6d90-131">L’utilisation d’Azure Configuration Manager est facultative.</span><span class="sxs-lookup"><span data-stu-id="b6d90-131">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="b6d90-132">Vous pouvez également utiliser une API telle que le type de `ConfigurationManager` .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b6d90-132">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="b6d90-133">Analyser la chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="b6d90-133">Parse the connection string</span></span>

<span data-ttu-id="b6d90-134">Pour analyser la chaîne de connexion, utilisez:</span><span class="sxs-lookup"><span data-stu-id="b6d90-134">To parse the connection string, use:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

<span data-ttu-id="b6d90-135">Cela retourne un `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="b6d90-135">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-some-local-dummy-data"></a><span data-ttu-id="b6d90-136">Créer des données fictives locales</span><span class="sxs-lookup"><span data-stu-id="b6d90-136">Create some local dummy data</span></span>

<span data-ttu-id="b6d90-137">Avant de commencer, créez des données locales factices dans le répertoire de notre script.</span><span class="sxs-lookup"><span data-stu-id="b6d90-137">Before you begin, create some dummy local data in the directory of our script.</span></span> <span data-ttu-id="b6d90-138">Plus tard, vous téléchargez ces données.</span><span class="sxs-lookup"><span data-stu-id="b6d90-138">Later you upload this data.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a><span data-ttu-id="b6d90-139">Créer le client du service BLOB</span><span class="sxs-lookup"><span data-stu-id="b6d90-139">Create the Blob service client</span></span>

<span data-ttu-id="b6d90-140">Le `CloudBlobClient` type vous permet de récupérer des conteneurs et des objets BLOB stockés dans le stockage d’objets BLOB.</span><span class="sxs-lookup"><span data-stu-id="b6d90-140">The `CloudBlobClient` type enables you to retrieve containers and blobs stored in Blob storage.</span></span> <span data-ttu-id="b6d90-141">Voici un moyen de créer le client de service:</span><span class="sxs-lookup"><span data-stu-id="b6d90-141">Here's one way to create the service client:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

<span data-ttu-id="b6d90-142">Vous êtes maintenant prêt à écrire du code qui lit et écrit des données dans le stockage d’objets BLOB.</span><span class="sxs-lookup"><span data-stu-id="b6d90-142">Now you are ready to write code that reads data from and writes data to Blob storage.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="b6d90-143">Créer un conteneur</span><span class="sxs-lookup"><span data-stu-id="b6d90-143">Create a container</span></span>

<span data-ttu-id="b6d90-144">Cet exemple montre comment créer un conteneur s’il n’existe pas déjà:</span><span class="sxs-lookup"><span data-stu-id="b6d90-144">This example shows how to create a container if it does not already exist:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

<span data-ttu-id="b6d90-145">Par défaut, le nouveau conteneur est privé, ce qui signifie que vous devez spécifier votre clé d’accès de stockage pour télécharger des objets BLOB à partir de ce conteneur.</span><span class="sxs-lookup"><span data-stu-id="b6d90-145">By default, the new container is private, meaning that you must specify your storage access key to download blobs from this container.</span></span> <span data-ttu-id="b6d90-146">Si vous souhaitez que les fichiers du conteneur soient disponibles pour tout le monde, vous pouvez configurer le conteneur pour qu’il soit public à l’aide du code suivant:</span><span class="sxs-lookup"><span data-stu-id="b6d90-146">If you want to make the files within the container available to everyone, you can set the container to be public using the following code:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

<span data-ttu-id="b6d90-147">Toute personne sur Internet peut voir des objets BLOB dans un conteneur public, mais vous pouvez les modifier ou les supprimer uniquement si vous disposez de la clé d’accès de compte appropriée ou d’une signature d’accès partagé.</span><span class="sxs-lookup"><span data-stu-id="b6d90-147">Anyone on the Internet can see blobs in a public container, but you can modify or delete them only if you have the appropriate account access key or a shared access signature.</span></span>

## <a name="upload-a-blob-into-a-container"></a><span data-ttu-id="b6d90-148">Charger un objet BLOB dans un conteneur</span><span class="sxs-lookup"><span data-stu-id="b6d90-148">Upload a blob into a container</span></span>

<span data-ttu-id="b6d90-149">Le stockage d’objets BLOB Azure prend en charge les objets BLOB de blocs et de pages.</span><span class="sxs-lookup"><span data-stu-id="b6d90-149">Azure Blob Storage supports block blobs and page blobs.</span></span> <span data-ttu-id="b6d90-150">Dans la plupart des cas, un objet blob de blocs est le type recommandé à utiliser.</span><span class="sxs-lookup"><span data-stu-id="b6d90-150">In most cases, a block blob is the recommended type to use.</span></span>

<span data-ttu-id="b6d90-151">Pour télécharger un fichier vers un objet blob de blocs, récupérez une référence de conteneur et utilisez-la pour obtenir une référence d’objet blob de blocs.</span><span class="sxs-lookup"><span data-stu-id="b6d90-151">To upload a file to a block blob, get a container reference and use it to get a block blob reference.</span></span> <span data-ttu-id="b6d90-152">Une fois que vous avez une référence d’objet BLOB, vous pouvez charger n’importe quel flux de `UploadFromFile` données en appelant la méthode.</span><span class="sxs-lookup"><span data-stu-id="b6d90-152">Once you have a blob reference, you can upload any stream of data to it by calling the `UploadFromFile` method.</span></span> <span data-ttu-id="b6d90-153">Cette opération crée l’objet BLOB s’il n’existe pas déjà, ou le remplace s’il existe.</span><span class="sxs-lookup"><span data-stu-id="b6d90-153">This operation creates the blob if it didn't previously exist, or overwrite it if it does exist.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a><span data-ttu-id="b6d90-154">Répertorier les objets BLOB dans un conteneur</span><span class="sxs-lookup"><span data-stu-id="b6d90-154">List the blobs in a container</span></span>

<span data-ttu-id="b6d90-155">Pour répertorier les objets BLOB dans un conteneur, commencez par obtenir une référence de conteneur.</span><span class="sxs-lookup"><span data-stu-id="b6d90-155">To list the blobs in a container, first get a container reference.</span></span> <span data-ttu-id="b6d90-156">Vous pouvez ensuite utiliser la méthode du `ListBlobs` conteneur pour récupérer les objets BLOB et/ou les répertoires qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="b6d90-156">You can then use the container's `ListBlobs` method to retrieve the blobs and/or directories within it.</span></span> <span data-ttu-id="b6d90-157">Pour accéder à l’ensemble complet de propriétés et de méthodes pour `IListBlobItem`un retourné, vous devez effectuer un `CloudBlockBlob`cast de celui `CloudBlobDirectory` -ci en un objet, `CloudPageBlob`ou.</span><span class="sxs-lookup"><span data-stu-id="b6d90-157">To access the rich set of properties and methods for a returned `IListBlobItem`, you must cast it to a `CloudBlockBlob`, `CloudPageBlob`, or `CloudBlobDirectory` object.</span></span> <span data-ttu-id="b6d90-158">Si le type est inconnu, vous pouvez utiliser une vérification de type pour déterminer le vers lequel effectuer un cast.</span><span class="sxs-lookup"><span data-stu-id="b6d90-158">If the type is unknown, you can use a type check to determine which to cast it to.</span></span> <span data-ttu-id="b6d90-159">Le code suivant montre comment récupérer et générer l’URI de chaque élément `mydata` du conteneur:</span><span class="sxs-lookup"><span data-stu-id="b6d90-159">The following code demonstrates how to retrieve and output the URI of each item in the `mydata` container:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

<span data-ttu-id="b6d90-160">Vous pouvez également nommer des objets BLOB avec des informations de chemin d’accès dans leurs noms.</span><span class="sxs-lookup"><span data-stu-id="b6d90-160">You can also name blobs with path information in their names.</span></span> <span data-ttu-id="b6d90-161">Cela crée une structure de répertoires virtuels que vous pouvez organiser et parcourir comme un système de fichiers traditionnel.</span><span class="sxs-lookup"><span data-stu-id="b6d90-161">This creates a virtual directory structure that you can organize and traverse as you would a traditional file system.</span></span> <span data-ttu-id="b6d90-162">Notez que la structure de répertoires est virtuelle uniquement-les seules ressources disponibles dans le stockage d’objets BLOB sont des conteneurs et des objets BLOB.</span><span class="sxs-lookup"><span data-stu-id="b6d90-162">Note that the directory structure is virtual only - the only resources available in Blob storage are containers and blobs.</span></span> <span data-ttu-id="b6d90-163">Toutefois, la bibliothèque cliente de stockage `CloudBlobDirectory` offre un objet pour faire référence à un répertoire virtuel et simplifier le processus d’utilisation des objets BLOB organisés de cette façon.</span><span class="sxs-lookup"><span data-stu-id="b6d90-163">However, the storage client library offers a `CloudBlobDirectory` object to refer to a virtual directory and simplify the process of working with blobs that are organized in this way.</span></span>

<span data-ttu-id="b6d90-164">Par exemple, considérez l’ensemble suivant d’objets BLOB de blocs dans `photos`un conteneur nommé:</span><span class="sxs-lookup"><span data-stu-id="b6d90-164">For example, consider the following set of block blobs in a container named `photos`:</span></span>

<span data-ttu-id="b6d90-165">*photo1.jpg*</span><span class="sxs-lookup"><span data-stu-id="b6d90-165">*photo1.jpg*</span></span>\
<span data-ttu-id="b6d90-166">*2015/architecture/description.txt*</span><span class="sxs-lookup"><span data-stu-id="b6d90-166">*2015/architecture/description.txt*</span></span>\
<span data-ttu-id="b6d90-167">*2015/architecture/photo3.jpg*</span><span class="sxs-lookup"><span data-stu-id="b6d90-167">*2015/architecture/photo3.jpg*</span></span>\
<span data-ttu-id="b6d90-168">*2015/architecture/photo4.jpg*</span><span class="sxs-lookup"><span data-stu-id="b6d90-168">*2015/architecture/photo4.jpg*</span></span>\
<span data-ttu-id="b6d90-169">*2016/architecture/photo5.jpg*</span><span class="sxs-lookup"><span data-stu-id="b6d90-169">*2016/architecture/photo5.jpg*</span></span>\
<span data-ttu-id="b6d90-170">*2016/architecture/photo6.jpg*</span><span class="sxs-lookup"><span data-stu-id="b6d90-170">*2016/architecture/photo6.jpg*</span></span>\
<span data-ttu-id="b6d90-171">*2016/architecture/description.txt*</span><span class="sxs-lookup"><span data-stu-id="b6d90-171">*2016/architecture/description.txt*</span></span>\
<span data-ttu-id="b6d90-172">*2016/photo7.jpg*</span><span class="sxs-lookup"><span data-stu-id="b6d90-172">*2016/photo7.jpg*</span></span>\

<span data-ttu-id="b6d90-173">Lorsque vous appelez `ListBlobs` sur un conteneur (comme dans l’exemple ci-dessus), une liste hiérarchique est retournée.</span><span class="sxs-lookup"><span data-stu-id="b6d90-173">When you call `ListBlobs` on a container (as in the above sample), a hierarchical listing is returned.</span></span> <span data-ttu-id="b6d90-174">S’il contient à `CloudBlobDirectory` la `CloudBlockBlob` fois des objets et, représentant respectivement les répertoires et les objets BLOB du conteneur, le résultat obtenu ressemble à ceci:</span><span class="sxs-lookup"><span data-stu-id="b6d90-174">If it contains both `CloudBlobDirectory` and `CloudBlockBlob` objects, representing the directories and blobs in the container, respectively, then the resulting output looks similar to this:</span></span>

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

<span data-ttu-id="b6d90-175">Si vous le souhaitez, vous pouvez `UseFlatBlobListing` définir le paramètre `ListBlobs` de la `true`méthode sur.</span><span class="sxs-lookup"><span data-stu-id="b6d90-175">Optionally, you can set the `UseFlatBlobListing` parameter of the `ListBlobs` method to `true`.</span></span> <span data-ttu-id="b6d90-176">Dans ce cas, tous les objets BLOB du conteneur sont retournés en tant qu' `CloudBlockBlob` objet.</span><span class="sxs-lookup"><span data-stu-id="b6d90-176">In this case, every blob in the container is returned as a `CloudBlockBlob` object.</span></span> <span data-ttu-id="b6d90-177">L’appel à `ListBlobs` pour retourner une liste plate ressemble à ceci:</span><span class="sxs-lookup"><span data-stu-id="b6d90-177">The call to `ListBlobs` to return a flat listing looks like this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

<span data-ttu-id="b6d90-178">et, selon le contenu actuel de votre conteneur, les résultats ressemblent à ceci:</span><span class="sxs-lookup"><span data-stu-id="b6d90-178">and, depending on the current contents of your container, the results look like this:</span></span>

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

## <a name="download-blobs"></a><span data-ttu-id="b6d90-179">Télécharger les objets BLOB</span><span class="sxs-lookup"><span data-stu-id="b6d90-179">Download blobs</span></span>

<span data-ttu-id="b6d90-180">Pour télécharger des objets BLOB, commencez par récupérer une référence d’objet `DownloadToStream` BLOB, puis appelez la méthode.</span><span class="sxs-lookup"><span data-stu-id="b6d90-180">To download blobs, first retrieve a blob reference and then call the `DownloadToStream` method.</span></span> <span data-ttu-id="b6d90-181">L’exemple suivant utilise la `DownloadToStream` méthode pour transférer le contenu de l’objet BLOB vers un objet de flux que vous pouvez ensuite conserver dans un fichier local.</span><span class="sxs-lookup"><span data-stu-id="b6d90-181">The following example uses the `DownloadToStream` method to transfer the blob contents to a stream object that you can then persist to a local file.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

<span data-ttu-id="b6d90-182">Vous pouvez également utiliser la `DownloadToStream` méthode pour télécharger le contenu d’un objet blob sous la forme d’une chaîne de texte.</span><span class="sxs-lookup"><span data-stu-id="b6d90-182">You can also use the `DownloadToStream` method to download the contents of a blob as a text string.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a><span data-ttu-id="b6d90-183">Supprimer les objets BLOB</span><span class="sxs-lookup"><span data-stu-id="b6d90-183">Delete blobs</span></span>

<span data-ttu-id="b6d90-184">Pour supprimer un objet BLOB, commencez par obtenir une référence d’objet BLOB `Delete` , puis appelez la méthode sur celui-ci.</span><span class="sxs-lookup"><span data-stu-id="b6d90-184">To delete a blob, first get a blob reference and then call the `Delete` method on it.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a><span data-ttu-id="b6d90-185">Répertorier les objets BLOB dans les pages de manière asynchrone</span><span class="sxs-lookup"><span data-stu-id="b6d90-185">List blobs in pages asynchronously</span></span>

<span data-ttu-id="b6d90-186">Si vous répertoriez un grand nombre d’objets BLOB ou que vous souhaitez contrôler le nombre de résultats retournés dans une opération de liste, vous pouvez répertorier les objets BLOB dans les pages de résultats.</span><span class="sxs-lookup"><span data-stu-id="b6d90-186">If you are listing a large number of blobs, or you want to control the number of results you return in one listing operation, you can list blobs in pages of results.</span></span> <span data-ttu-id="b6d90-187">Cet exemple montre comment retourner des résultats dans des pages de manière asynchrone, afin que l’exécution ne soit pas bloquée en attendant de retourner un grand nombre de résultats.</span><span class="sxs-lookup"><span data-stu-id="b6d90-187">This example shows how to return results in pages asynchronously, so that execution is not blocked while waiting to return a large set of results.</span></span>

<span data-ttu-id="b6d90-188">Cet exemple montre une liste d’objets BLOB plats, mais vous pouvez également effectuer une liste hiérarchique en affectant `useFlatBlobListing` au paramètre de `ListBlobsSegmentedAsync` la méthode `false`la valeur.</span><span class="sxs-lookup"><span data-stu-id="b6d90-188">This example shows a flat blob listing, but you can also perform a hierarchical listing, by setting the `useFlatBlobListing` parameter of the `ListBlobsSegmentedAsync` method to `false`.</span></span>

<span data-ttu-id="b6d90-189">L’exemple définit une méthode asynchrone à l’aide `async` d’un bloc.</span><span class="sxs-lookup"><span data-stu-id="b6d90-189">The sample defines an asynchronous method, using an `async` block.</span></span> <span data-ttu-id="b6d90-190">Le ``let!`` mot clé interrompt l’exécution de l’exemple de méthode jusqu’à ce que la tâche de liste se termine.</span><span class="sxs-lookup"><span data-stu-id="b6d90-190">The ``let!`` keyword suspends execution of the sample method until the listing task completes.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

<span data-ttu-id="b6d90-191">Nous pouvons maintenant utiliser cette routine asynchrone comme suit.</span><span class="sxs-lookup"><span data-stu-id="b6d90-191">We can now use this asynchronous routine as follows.</span></span> <span data-ttu-id="b6d90-192">Tout d’abord, vous téléchargez des données factices (à l’aide du fichier local créé précédemment dans ce didacticiel).</span><span class="sxs-lookup"><span data-stu-id="b6d90-192">First you upload some dummy data (using the local file created earlier in this tutorial).</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

<span data-ttu-id="b6d90-193">À présent, appelez la routine.</span><span class="sxs-lookup"><span data-stu-id="b6d90-193">Now, call the routine.</span></span> <span data-ttu-id="b6d90-194">Vous utilisez `Async.RunSynchronously` pour forcer l’exécution de l’opération asynchrone.</span><span class="sxs-lookup"><span data-stu-id="b6d90-194">You use `Async.RunSynchronously` to force the execution of the asynchronous operation.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a><span data-ttu-id="b6d90-195">Écriture dans un objet blob d’ajout</span><span class="sxs-lookup"><span data-stu-id="b6d90-195">Writing to an append blob</span></span>

<span data-ttu-id="b6d90-196">Un objet blob d’ajout est optimisé pour les opérations d’ajout, telles que la journalisation.</span><span class="sxs-lookup"><span data-stu-id="b6d90-196">An append blob is optimized for append operations, such as logging.</span></span> <span data-ttu-id="b6d90-197">À l’instar d’un objet blob de blocs, un objet blob d’ajout est constitué de blocs, mais lorsque vous ajoutez un nouveau bloc à un objet blob d’ajout, il est toujours ajouté à la fin de l’objet BLOB.</span><span class="sxs-lookup"><span data-stu-id="b6d90-197">Like a block blob, an append blob is comprised of blocks, but when you add a new block to an append blob, it is always appended to the end of the blob.</span></span> <span data-ttu-id="b6d90-198">Vous ne pouvez pas mettre à jour ou supprimer un bloc existant dans un objet blob d’ajout.</span><span class="sxs-lookup"><span data-stu-id="b6d90-198">You cannot update or delete an existing block in an append blob.</span></span> <span data-ttu-id="b6d90-199">Les ID de bloc d’un objet blob d’ajout ne sont pas exposés, car ils sont destinés à un objet blob de blocs.</span><span class="sxs-lookup"><span data-stu-id="b6d90-199">The block IDs for an append blob are not exposed as they are for a block blob.</span></span>

<span data-ttu-id="b6d90-200">Chaque bloc dans un objet blob d’ajout peut avoir une taille différente, jusqu’à un maximum de 4 Mo, et un objet blob d’ajout peut inclure un maximum de 50 000 blocs.</span><span class="sxs-lookup"><span data-stu-id="b6d90-200">Each block in an append blob can be a different size, up to a maximum of 4 MB, and an append blob can include a maximum of 50,000 blocks.</span></span> <span data-ttu-id="b6d90-201">La taille maximale d’un objet blob d’ajout est donc légèrement supérieure à 195 Go (4 Mo X 50 000 blocs).</span><span class="sxs-lookup"><span data-stu-id="b6d90-201">The maximum size of an append blob is therefore slightly more than 195 GB (4 MB X 50,000 blocks).</span></span>

<span data-ttu-id="b6d90-202">L’exemple suivant crée un nouvel objet blob d’ajout et y ajoute des données, en simulant une opération de journalisation simple.</span><span class="sxs-lookup"><span data-stu-id="b6d90-202">The following example creates a new append blob and appends some data to it, simulating a simple logging operation.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

<span data-ttu-id="b6d90-203">Pour plus d’informations sur les différences entre les trois types d’objets BLOB, consultez Présentation des objets BLOB de [blocs, objets BLOB de pages et objets BLOB d’ajout](https://msdn.microsoft.com/library/azure/ee691964.aspx) .</span><span class="sxs-lookup"><span data-stu-id="b6d90-203">See [Understanding Block Blobs, Page Blobs, and Append Blobs](https://msdn.microsoft.com/library/azure/ee691964.aspx) for more information about the differences between the three types of blobs.</span></span>

## <a name="concurrent-access"></a><span data-ttu-id="b6d90-204">Accès simultané</span><span class="sxs-lookup"><span data-stu-id="b6d90-204">Concurrent access</span></span>

<span data-ttu-id="b6d90-205">Pour prendre en charge l’accès simultané à un objet blob à partir de plusieurs clients ou d' instances de processus, vous pouvez utiliser des ETags ou des **baux**.</span><span class="sxs-lookup"><span data-stu-id="b6d90-205">To support concurrent access to a blob from multiple clients or multiple process instances, you can use **ETags** or **leases**.</span></span>

* <span data-ttu-id="b6d90-206">**ETag** -fournit un moyen de détecter que l’objet BLOB ou le conteneur a été modifié par un autre processus</span><span class="sxs-lookup"><span data-stu-id="b6d90-206">**Etag** - provides a way to detect that the blob or container has been modified by another process</span></span>

* <span data-ttu-id="b6d90-207">**Bail** -fournit un moyen d’obtenir un accès exclusif, renouvelable, en écriture ou en suppression sur un objet BLOB pendant une période donnée.</span><span class="sxs-lookup"><span data-stu-id="b6d90-207">**Lease** - provides a way to obtain exclusive, renewable, write or delete access to a blob for a period of time</span></span>

<span data-ttu-id="b6d90-208">Pour plus d’informations, consultez [gestion de l’accès concurrentiel dans stockage Microsoft Azure](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span><span class="sxs-lookup"><span data-stu-id="b6d90-208">For more information, see [Managing Concurrency in Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span></span>

## <a name="naming-containers"></a><span data-ttu-id="b6d90-209">Nommer des conteneurs</span><span class="sxs-lookup"><span data-stu-id="b6d90-209">Naming containers</span></span>

<span data-ttu-id="b6d90-210">Chaque objet BLOB du stockage Azure doit résider dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="b6d90-210">Every blob in Azure storage must reside in a container.</span></span> <span data-ttu-id="b6d90-211">Le conteneur fait partie du nom de l’objet BLOB.</span><span class="sxs-lookup"><span data-stu-id="b6d90-211">The container forms part of the blob name.</span></span> <span data-ttu-id="b6d90-212">Par exemple, `mydata` est le nom du conteneur dans ces exemples d’URI d’objet BLOB:</span><span class="sxs-lookup"><span data-stu-id="b6d90-212">For example, `mydata` is the name of the container in these sample blob URIs:</span></span>

- https://storagesample.blob.core.windows.net/mydata/blob1.txt
- https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

<span data-ttu-id="b6d90-213">Un nom de conteneur doit être un nom DNS valide, conforme aux règles d’affectation de noms suivantes:</span><span class="sxs-lookup"><span data-stu-id="b6d90-213">A container name must be a valid DNS name, conforming to the following naming rules:</span></span>

1. <span data-ttu-id="b6d90-214">Les noms de conteneur doivent commencer par une lettre ou un chiffre, et ne peuvent contenir que des lettres, des chiffres et des tirets (-).</span><span class="sxs-lookup"><span data-stu-id="b6d90-214">Container names must start with a letter or number, and can contain only letters, numbers, and the dash (-) character.</span></span>
1. <span data-ttu-id="b6d90-215">Chaque tiret (-) doit être immédiatement précédé et suivi d’une lettre ou d’un chiffre. les tirets consécutifs ne sont pas autorisés dans les noms de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="b6d90-215">Every dash (-) character must be immediately preceded and followed by a letter or number; consecutive dashes are not permitted in container names.</span></span>
1. <span data-ttu-id="b6d90-216">Toutes les lettres d’un nom de conteneur doivent être en minuscules.</span><span class="sxs-lookup"><span data-stu-id="b6d90-216">All letters in a container name must be lowercase.</span></span>
1. <span data-ttu-id="b6d90-217">Les noms de conteneur doivent être compris entre 3 et 63 caractères.</span><span class="sxs-lookup"><span data-stu-id="b6d90-217">Container names must be from 3 through 63 characters long.</span></span>

<span data-ttu-id="b6d90-218">Notez que le nom d’un conteneur doit toujours être en minuscules.</span><span class="sxs-lookup"><span data-stu-id="b6d90-218">Note that the name of a container must always be lowercase.</span></span> <span data-ttu-id="b6d90-219">Si vous incluez une lettre majuscule dans un nom de conteneur ou si vous violez les règles d’affectation de noms de conteneurs, vous pouvez recevoir une erreur 400 (requête incorrecte).</span><span class="sxs-lookup"><span data-stu-id="b6d90-219">If you include an upper-case letter in a container name, or otherwise violate the container naming rules, you may receive a 400 error (Bad Request).</span></span>

## <a name="managing-security-for-blobs"></a><span data-ttu-id="b6d90-220">Gestion de la sécurité des objets BLOB</span><span class="sxs-lookup"><span data-stu-id="b6d90-220">Managing security for blobs</span></span>

<span data-ttu-id="b6d90-221">Par défaut, le stockage Azure assure la sécurité de vos données en limitant l’accès au propriétaire du compte, qui est en possession des clés d’accès du compte.</span><span class="sxs-lookup"><span data-stu-id="b6d90-221">By default, Azure Storage keeps your data secure by limiting access to the account owner, who is in possession of the account access keys.</span></span> <span data-ttu-id="b6d90-222">Lorsque vous devez partager des données BLOB dans votre compte de stockage, il est important de le faire sans compromettre la sécurité de vos clés d’accès de votre compte.</span><span class="sxs-lookup"><span data-stu-id="b6d90-222">When you need to share blob data in your storage account, it is important to do so without compromising the security of your account access keys.</span></span> <span data-ttu-id="b6d90-223">En outre, vous pouvez chiffrer les données d’objet BLOB pour vous assurer qu’elles sont sécurisées sur le réseau et dans le stockage Azure.</span><span class="sxs-lookup"><span data-stu-id="b6d90-223">Additionally, you can encrypt blob data to ensure that it is secure going over the wire and in Azure Storage.</span></span>

### <a name="controlling-access-to-blob-data"></a><span data-ttu-id="b6d90-224">Contrôle de l’accès aux données d’objets BLOB</span><span class="sxs-lookup"><span data-stu-id="b6d90-224">Controlling access to blob data</span></span>

<span data-ttu-id="b6d90-225">Par défaut, les données d’objet blob de votre compte de stockage sont accessibles uniquement au propriétaire du compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="b6d90-225">By default, the blob data in your storage account is accessible only to storage account owner.</span></span> <span data-ttu-id="b6d90-226">L’authentification des demandes sur le stockage d’objets BLOB requiert la clé d’accès au compte par défaut.</span><span class="sxs-lookup"><span data-stu-id="b6d90-226">Authenticating requests against Blob storage requires the account access key by default.</span></span> <span data-ttu-id="b6d90-227">Toutefois, vous souhaiterez peut-être mettre certaines données BLOB à la disposition d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="b6d90-227">However, you might want to make certain blob data available to other users.</span></span>

### <a name="encrypting-blob-data"></a><span data-ttu-id="b6d90-228">Chiffrement des données BLOB</span><span class="sxs-lookup"><span data-stu-id="b6d90-228">Encrypting blob data</span></span>

<span data-ttu-id="b6d90-229">Le stockage Azure prend en charge le chiffrement des données BLOB à la fois sur le client et sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="b6d90-229">Azure Storage supports encrypting blob data both at the client and on the server.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b6d90-230">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="b6d90-230">Next steps</span></span>

<span data-ttu-id="b6d90-231">Maintenant que vous avez appris les principes de base du stockage d’objets BLOB, suivez ces liens pour en savoir plus.</span><span class="sxs-lookup"><span data-stu-id="b6d90-231">Now that you've learned the basics of Blob storage, follow these links to learn more.</span></span>

### <a name="tools"></a><span data-ttu-id="b6d90-232">Outils</span><span class="sxs-lookup"><span data-stu-id="b6d90-232">Tools</span></span>

- <span data-ttu-id="b6d90-233">[F#AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)</span><span class="sxs-lookup"><span data-stu-id="b6d90-233">[F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)</span></span>\
<span data-ttu-id="b6d90-234">Fournisseur F# de type qui peut être utilisé pour explorer des ressources de stockage Azure d’objets BLOB, de table et de file d’attente et pour appliquer facilement des opérations CRUD sur ceux-ci.</span><span class="sxs-lookup"><span data-stu-id="b6d90-234">An F# Type Provider which can be used to explore Blob, Table and Queue Azure Storage assets and easily apply CRUD operations on them.</span></span>

- <span data-ttu-id="b6d90-235">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)</span><span class="sxs-lookup"><span data-stu-id="b6d90-235">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)</span></span>\
<span data-ttu-id="b6d90-236">F# API pour l’utilisation du service de stockage de table Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="b6d90-236">An F# API for using Microsoft Azure Table Storage service</span></span>

- <span data-ttu-id="b6d90-237">[Explorateur Stockage Microsoft Azure (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)</span><span class="sxs-lookup"><span data-stu-id="b6d90-237">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)</span></span>\
<span data-ttu-id="b6d90-238">Une application autonome et gratuite de Microsoft qui vous permet de travailler visuellement avec les données de stockage Azure sur Windows, OS X et Linux.</span><span class="sxs-lookup"><span data-stu-id="b6d90-238">A free, standalone app from Microsoft that enables you to work visually with Azure Storage data on Windows, OS X, and Linux.</span></span>

### <a name="blob-storage-reference"></a><span data-ttu-id="b6d90-239">Référence du stockage d’objets BLOB</span><span class="sxs-lookup"><span data-stu-id="b6d90-239">Blob storage reference</span></span>

- [<span data-ttu-id="b6d90-240">API de stockage Azure pour .NET</span><span class="sxs-lookup"><span data-stu-id="b6d90-240">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="b6d90-241">Informations de référence sur l’API REST des services de stockage Azure</span><span class="sxs-lookup"><span data-stu-id="b6d90-241">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a><span data-ttu-id="b6d90-242">Guides connexes</span><span class="sxs-lookup"><span data-stu-id="b6d90-242">Related guides</span></span>

- [<span data-ttu-id="b6d90-243">Prise en main avec le stockage d’objets BLOB Azure dansC#</span><span class="sxs-lookup"><span data-stu-id="b6d90-243">Getting Started with Azure Blob Storage in C#</span></span>](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [<span data-ttu-id="b6d90-244">Transfert de données avec l’utilitaire de ligne de commande AzCopy sur Windows</span><span class="sxs-lookup"><span data-stu-id="b6d90-244">Transfer data with the AzCopy command-line utility on Windows</span></span>](/azure/storage/common/storage-use-azcopy)
- [<span data-ttu-id="b6d90-245">Transfert de données avec l’utilitaire de ligne de commande AzCopy sur Linux</span><span class="sxs-lookup"><span data-stu-id="b6d90-245">Transfer data with the AzCopy command-line utility on Linux</span></span>](/azure/storage/common/storage-use-azcopy-linux)
- [<span data-ttu-id="b6d90-246">Configurer des chaînes de connexion de stockage Azure</span><span class="sxs-lookup"><span data-stu-id="b6d90-246">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="b6d90-247">Blog de l’équipe stockage Azure</span><span class="sxs-lookup"><span data-stu-id="b6d90-247">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [<span data-ttu-id="b6d90-248">Démarrage rapide : Utiliser .NET pour créer un objet BLOB dans le stockage d’objets</span><span class="sxs-lookup"><span data-stu-id="b6d90-248">Quickstart: Use .NET to create a blob in object storage</span></span>](/azure/storage/blobs/storage-quickstart-blobs-dotnet)
