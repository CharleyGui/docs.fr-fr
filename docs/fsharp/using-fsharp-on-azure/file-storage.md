---
title: 'Prise en main du stockage de fichiers Azure à l’aide de F #'
description: Stockez les données de fichier dans le Cloud avec le stockage de fichiers Azure, puis montez votre partage de fichiers Cloud à partir d’une machine virtuelle Azure ou d’une application locale exécutant Windows.
author: sylvanc
ms.date: 09/20/2016
ms.custom: devx-track-fsharp
ms.openlocfilehash: bcea58b4bf756fc9d696cd5a1010b0feffb127a7
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899422"
---
# <a name="get-started-with-azure-file-storage-using-f"></a><span data-ttu-id="899bf-103">Prise en main du stockage de fichiers Azure à l’aide de F\#</span><span class="sxs-lookup"><span data-stu-id="899bf-103">Get started with Azure File Storage using F\#</span></span>

<span data-ttu-id="899bf-104">Le stockage de fichiers Azure est un service qui offre des partages de fichiers dans le Cloud à l’aide du [protocole SMB (Server Message Block)](/windows/win32/fileio/microsoft-smb-protocol-and-cifs-protocol-overview)standard.</span><span class="sxs-lookup"><span data-stu-id="899bf-104">Azure File Storage is a service that offers file shares in the cloud using the standard [Server Message Block (SMB) Protocol](/windows/win32/fileio/microsoft-smb-protocol-and-cifs-protocol-overview).</span></span> <span data-ttu-id="899bf-105">Les protocoles SMB 2.1 et SMB 3.0 sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="899bf-105">Both SMB 2.1 and SMB 3.0 are supported.</span></span> <span data-ttu-id="899bf-106">Avec stockage fichier Azure, vous pouvez migrer des applications héritées qui s’appuient sur des partages de fichiers vers Azure rapidement et sans réécriture coûteuse.</span><span class="sxs-lookup"><span data-stu-id="899bf-106">With Azure File Storage, you can migrate legacy applications that rely on file shares to Azure quickly and without costly rewrites.</span></span> <span data-ttu-id="899bf-107">Les applications s’exécutant sur des machines virtuelles Azure, dans des services cloud ou à partir de clients locaux peuvent monter un partage de fichiers dans le cloud, tout comme une application de bureau monte un partage SMB standard.</span><span class="sxs-lookup"><span data-stu-id="899bf-107">Applications running in Azure virtual machines or cloud services or from on-premises clients can mount a file share in the cloud, just as a desktop application mounts a typical SMB share.</span></span> <span data-ttu-id="899bf-108">Un nombre illimité de composants d’application peuvent ensuite monter un partage de stockage de fichiers et y accéder simultanément.</span><span class="sxs-lookup"><span data-stu-id="899bf-108">Any number of application components can then mount and access the File storage share simultaneously.</span></span>

<span data-ttu-id="899bf-109">Pour obtenir une vue d’ensemble conceptuelle du stockage de fichiers, consultez [le guide .net pour le stockage de fichiers](/azure/storage/storage-dotnet-how-to-use-files).</span><span class="sxs-lookup"><span data-stu-id="899bf-109">For a conceptual overview of file storage, see [the .NET guide for file storage](/azure/storage/storage-dotnet-how-to-use-files).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="899bf-110">Prérequis</span><span class="sxs-lookup"><span data-stu-id="899bf-110">Prerequisites</span></span>

<span data-ttu-id="899bf-111">Pour utiliser ce guide, vous devez d’abord [créer un compte de stockage Azure](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="899bf-111">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="899bf-112">Vous aurez également besoin de votre clé d’accès de stockage pour ce compte.</span><span class="sxs-lookup"><span data-stu-id="899bf-112">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="899bf-113">Créer un script F # et démarrer F# Interactive</span><span class="sxs-lookup"><span data-stu-id="899bf-113">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="899bf-114">Les exemples de cet article peuvent être utilisés dans une application F # ou un script F #.</span><span class="sxs-lookup"><span data-stu-id="899bf-114">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="899bf-115">Pour créer un script F #, créez un fichier avec l' `.fsx` extension, par exemple `files.fsx` , dans votre environnement de développement f #.</span><span class="sxs-lookup"><span data-stu-id="899bf-115">To create an F# script, create a file with the `.fsx` extension, for example `files.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="899bf-116">Ensuite, utilisez un [Gestionnaire de package](package-management.md) comme [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) pour installer le `WindowsAzure.Storage` package et la référence `WindowsAzure.Storage.dll` dans votre script à l’aide d’une `#r` directive.</span><span class="sxs-lookup"><span data-stu-id="899bf-116">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="899bf-117">Ajout de déclarations d'espaces de noms</span><span class="sxs-lookup"><span data-stu-id="899bf-117">Add namespace declarations</span></span>

<span data-ttu-id="899bf-118">Ajoutez les instructions `open` suivantes au début du fichier `files.fsx` :</span><span class="sxs-lookup"><span data-stu-id="899bf-118">Add the following `open` statements to the top of the `files.fsx` file:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="899bf-119">Obtention de votre chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="899bf-119">Get your connection string</span></span>

<span data-ttu-id="899bf-120">Vous aurez besoin d’une chaîne de connexion de stockage Azure pour ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="899bf-120">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="899bf-121">Pour plus d’informations sur les chaînes de connexion, consultez [configurer des chaînes de connexion de stockage](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="899bf-121">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="899bf-122">Pour le didacticiel, vous allez entrer votre chaîne de connexion dans votre script, comme suit :</span><span class="sxs-lookup"><span data-stu-id="899bf-122">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

<span data-ttu-id="899bf-123">Toutefois, cela n’est **pas recommandé** pour les projets réels.</span><span class="sxs-lookup"><span data-stu-id="899bf-123">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="899bf-124">Votre clé de compte de stockage est similaire au mot de passe racine pour votre compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="899bf-124">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="899bf-125">Veillez toujours à protéger votre clé de compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="899bf-125">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="899bf-126">Évitez de la communiquer à d’autres utilisateurs, de la coder en dur ou de l’enregistrer dans un fichier texte brut accessible à d’autres personnes.</span><span class="sxs-lookup"><span data-stu-id="899bf-126">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="899bf-127">Vous pouvez régénérer votre clé à l’aide de la Portail Azure si vous pensez qu’elle a peut-être été compromise.</span><span class="sxs-lookup"><span data-stu-id="899bf-127">You can regenerate your key using the Azure portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="899bf-128">Pour les applications réelles, la meilleure façon de gérer votre chaîne de connexion de stockage se trouve dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="899bf-128">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="899bf-129">Pour extraire la chaîne de connexion d’un fichier de configuration, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="899bf-129">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

<span data-ttu-id="899bf-130">L’utilisation d’Azure Configuration Manager est facultative.</span><span class="sxs-lookup"><span data-stu-id="899bf-130">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="899bf-131">Vous pouvez également utiliser une API telle que le type de .NET Framework `ConfigurationManager` .</span><span class="sxs-lookup"><span data-stu-id="899bf-131">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="899bf-132">Analyse de la chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="899bf-132">Parse the connection string</span></span>

<span data-ttu-id="899bf-133">Pour analyser la chaîne de connexion, utilisez :</span><span class="sxs-lookup"><span data-stu-id="899bf-133">To parse the connection string, use:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

<span data-ttu-id="899bf-134">Cela renverra un `CloudStorageAccount` .</span><span class="sxs-lookup"><span data-stu-id="899bf-134">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-file-service-client"></a><span data-ttu-id="899bf-135">Créer le client du service de fichiers</span><span class="sxs-lookup"><span data-stu-id="899bf-135">Create the File service client</span></span>

<span data-ttu-id="899bf-136">Le `CloudFileClient` type vous permet d’utiliser par programme des fichiers stockés dans le stockage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="899bf-136">The `CloudFileClient` type enables you to programmatically use files stored in File storage.</span></span> <span data-ttu-id="899bf-137">Voici un moyen de créer le client du service :</span><span class="sxs-lookup"><span data-stu-id="899bf-137">Here's one way to create the service client:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

<span data-ttu-id="899bf-138">Vous êtes maintenant prêt à écrire du code qui lit et écrit des données dans le stockage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="899bf-138">Now you are ready to write code that reads data from and writes data to File storage.</span></span>

## <a name="create-a-file-share"></a><span data-ttu-id="899bf-139">Créer un partage de fichier</span><span class="sxs-lookup"><span data-stu-id="899bf-139">Create a file share</span></span>

<span data-ttu-id="899bf-140">Cet exemple montre comment créer un partage de fichiers s’il n’existe pas déjà :</span><span class="sxs-lookup"><span data-stu-id="899bf-140">This example shows how to create a file share if it does not already exist:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a><span data-ttu-id="899bf-141">Créer un répertoire racine et un sous-répertoire</span><span class="sxs-lookup"><span data-stu-id="899bf-141">Create a root directory and a subdirectory</span></span>

<span data-ttu-id="899bf-142">Ici, vous pouvez obtenir le répertoire racine et obtenir un sous-répertoire de la racine.</span><span class="sxs-lookup"><span data-stu-id="899bf-142">Here, you get the root directory and get a subdirectory of the root.</span></span> <span data-ttu-id="899bf-143">Vous créez les deux s’ils n’existent pas déjà.</span><span class="sxs-lookup"><span data-stu-id="899bf-143">You create both if they don't already exist.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a><span data-ttu-id="899bf-144">Charger du texte sous forme de fichier</span><span class="sxs-lookup"><span data-stu-id="899bf-144">Upload text as a file</span></span>

<span data-ttu-id="899bf-145">Cet exemple montre comment charger du texte sous la forme d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="899bf-145">This example shows how to upload text as a file.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a><span data-ttu-id="899bf-146">Télécharger un fichier vers une copie locale du fichier</span><span class="sxs-lookup"><span data-stu-id="899bf-146">Download a file to a local copy of the file</span></span>

<span data-ttu-id="899bf-147">Ici, vous téléchargez le fichier que vous venez de créer, en ajoutant le contenu à un fichier local.</span><span class="sxs-lookup"><span data-stu-id="899bf-147">Here you download the file just created, appending the contents to a local file.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a><span data-ttu-id="899bf-148">Définition de la taille maximale d’un partage de fichiers</span><span class="sxs-lookup"><span data-stu-id="899bf-148">Set the maximum size for a file share</span></span>

<span data-ttu-id="899bf-149">L’exemple ci-dessous illustre comment vérifier l’utilisation actuelle pour un partage et comment définir le quota pour le partage.</span><span class="sxs-lookup"><span data-stu-id="899bf-149">The example below shows how to check the current usage for a share and how to set the quota for the share.</span></span> <span data-ttu-id="899bf-150">`FetchAttributes` doit être appelé pour remplir un partage `Properties` et `SetProperties` pour propager les modifications locales au stockage fichier Azure.</span><span class="sxs-lookup"><span data-stu-id="899bf-150">`FetchAttributes` must be called to populate a share's `Properties`, and `SetProperties` to propagate local changes to Azure File Storage.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a><span data-ttu-id="899bf-151">Génération d’une signature d’accès partagé pour un fichier ou partage de fichiers</span><span class="sxs-lookup"><span data-stu-id="899bf-151">Generate a shared access signature for a file or file share</span></span>

<span data-ttu-id="899bf-152">Vous pouvez générer une signature d’accès partagé (SAP) pour un partage de fichiers ou un fichier individuel.</span><span class="sxs-lookup"><span data-stu-id="899bf-152">You can generate a shared access signature (SAS) for a file share or for an individual file.</span></span> <span data-ttu-id="899bf-153">Vous pouvez également créer une stratégie d’accès partagé sur un partage de fichiers pour gérer les signatures d’accès partagé.</span><span class="sxs-lookup"><span data-stu-id="899bf-153">You can also create a shared access policy on a file share to manage shared access signatures.</span></span> <span data-ttu-id="899bf-154">Créer une stratégie d’accès partagé est recommandé, car cette opération permet de révoquer la SAP si elle doit être compromise.</span><span class="sxs-lookup"><span data-stu-id="899bf-154">Creating a shared access policy is recommended, as it provides a means of revoking the SAS if it should be compromised.</span></span>

<span data-ttu-id="899bf-155">Ici, vous créez une stratégie d’accès partagé sur un partage, puis vous utilisez cette stratégie pour fournir les contraintes pour une SAP sur un fichier du partage.</span><span class="sxs-lookup"><span data-stu-id="899bf-155">Here, you create a shared access policy on a share, and then use that policy to provide the constraints for a SAS on a file in the share.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

<span data-ttu-id="899bf-156">Pour plus d’informations sur la création et l’utilisation de signatures d’accès partagé, consultez [Utilisation des signatures d’accès partagé (SAP)](/azure/storage/storage-dotnet-shared-access-signature-part-1) et [Créer et utiliser une signature d’accès partagé avec Blob Storage](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span><span class="sxs-lookup"><span data-stu-id="899bf-156">For more information about creating and using shared access signatures, see [Using Shared Access Signatures (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) and [Create and use a SAS with Blob storage](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span></span>

### <a name="copy-files"></a><span data-ttu-id="899bf-157">Copie des fichiers</span><span class="sxs-lookup"><span data-stu-id="899bf-157">Copy files</span></span>

<span data-ttu-id="899bf-158">Vous pouvez copier un fichier vers un autre fichier ou un objet BLOB, ou un objet BLOB dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="899bf-158">You can copy a file to another file or to a blob, or a blob to a file.</span></span> <span data-ttu-id="899bf-159">Si vous copiez un objet BLOB dans un fichier ou un fichier dans un objet BLOB, vous *devez* utiliser une signature d’accès partagé (SAP) pour authentifier l’objet source, même si vous effectuez une copie dans le même compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="899bf-159">If you are copying a blob to a file, or a file to a blob, you *must* use a shared access signature (SAS) to authenticate the source object, even if you are copying within the same storage account.</span></span>

### <a name="copy-a-file-to-another-file"></a><span data-ttu-id="899bf-160">Copier un fichier dans un autre</span><span class="sxs-lookup"><span data-stu-id="899bf-160">Copy a file to another file</span></span>

<span data-ttu-id="899bf-161">Ici, vous copiez un fichier dans un autre fichier du même partage.</span><span class="sxs-lookup"><span data-stu-id="899bf-161">Here, you copy a file to another file in the same share.</span></span> <span data-ttu-id="899bf-162">Étant donné que cette opération de copie a lieu entre des fichiers du même compte de stockage, vous pouvez utiliser l’authentification Clé partagée pour l’effectuer.</span><span class="sxs-lookup"><span data-stu-id="899bf-162">Because this copy operation copies between files in the same storage account, you can use Shared Key authentication to perform the copy.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a><span data-ttu-id="899bf-163">Copier un fichier dans un objet blob</span><span class="sxs-lookup"><span data-stu-id="899bf-163">Copy a file to a blob</span></span>

<span data-ttu-id="899bf-164">Ici, vous créez un fichier et le copiez dans un objet BLOB au sein du même compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="899bf-164">Here, you create a file and copy it to a blob within the same storage account.</span></span> <span data-ttu-id="899bf-165">Vous créez une SAP pour le fichier source, que le service utilise pour authentifier l’accès au fichier source pendant l’opération de copie.</span><span class="sxs-lookup"><span data-stu-id="899bf-165">You create a SAS for the source file, which the service uses to authenticate access to the source file during the copy operation.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

<span data-ttu-id="899bf-166">Vous pouvez copier un objet blob dans un fichier de la même façon.</span><span class="sxs-lookup"><span data-stu-id="899bf-166">You can copy a blob to a file in the same way.</span></span> <span data-ttu-id="899bf-167">Si l’objet source est un objet blob, créez une SAP pour authentifier l’accès à cet objet blob pendant l’opération de copie.</span><span class="sxs-lookup"><span data-stu-id="899bf-167">If the source object is a blob, then create a SAS to authenticate access to that blob during the copy operation.</span></span>

## <a name="troubleshooting-file-storage-using-metrics"></a><span data-ttu-id="899bf-168">Résolution des problèmes de stockage de fichiers à l’aide de métriques</span><span class="sxs-lookup"><span data-stu-id="899bf-168">Troubleshooting File storage using metrics</span></span>

<span data-ttu-id="899bf-169">Azure Storage Analytics prend en charge les métriques pour le stockage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="899bf-169">Azure Storage Analytics supports metrics for File storage.</span></span> <span data-ttu-id="899bf-170">Avec les données de métriques, vous pouvez suivre les demandes et diagnostiquer les problèmes.</span><span class="sxs-lookup"><span data-stu-id="899bf-170">With metrics data, you can trace requests and diagnose issues.</span></span>

<span data-ttu-id="899bf-171">Vous pouvez activer les métriques pour le stockage de fichiers à partir de la [portail Azure](https://portal.azure.com), ou vous pouvez le faire à partir de F # comme suit :</span><span class="sxs-lookup"><span data-stu-id="899bf-171">You can enable metrics for File storage from the [Azure portal](https://portal.azure.com), or you can do it from F# like this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a><span data-ttu-id="899bf-172">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="899bf-172">Next steps</span></span>

<span data-ttu-id="899bf-173">Pour plus d’informations sur le stockage de fichiers Azure, consultez les liens suivants.</span><span class="sxs-lookup"><span data-stu-id="899bf-173">For more information about Azure File Storage, see these links.</span></span>

### <a name="conceptual-articles-and-videos"></a><span data-ttu-id="899bf-174">Vidéos et articles conceptuels</span><span class="sxs-lookup"><span data-stu-id="899bf-174">Conceptual articles and videos</span></span>

- [<span data-ttu-id="899bf-175">Stockage de fichiers Azure : un système de fichiers SMB dans le cloud sans friction pour Windows et Linux</span><span class="sxs-lookup"><span data-stu-id="899bf-175">Azure Files Storage: a frictionless cloud SMB file system for Windows and Linux</span></span>](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [<span data-ttu-id="899bf-176">Utilisation du stockage de fichiers Azure avec Linux</span><span class="sxs-lookup"><span data-stu-id="899bf-176">How to use Azure File Storage with Linux</span></span>](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a><span data-ttu-id="899bf-177">Outils pris en charge pour le stockage de fichiers</span><span class="sxs-lookup"><span data-stu-id="899bf-177">Tooling support for File storage</span></span>

- [<span data-ttu-id="899bf-178">Utilisation d'Azure PowerShell avec Azure Storage</span><span class="sxs-lookup"><span data-stu-id="899bf-178">Using Azure PowerShell with Azure Storage</span></span>](/azure/storage/storage-powershell-guide-full)
- [<span data-ttu-id="899bf-179">Utilisation de AzCopy avec Microsoft Azure Storage</span><span class="sxs-lookup"><span data-stu-id="899bf-179">How to use AzCopy with Microsoft Azure Storage</span></span>](/azure/storage/storage-use-azcopy)
- [<span data-ttu-id="899bf-180">Créer, télécharger et lister des objets blob avec Azure CLI</span><span class="sxs-lookup"><span data-stu-id="899bf-180">Create, download, and list blobs with Azure CLI</span></span>](/azure/storage/blobs/storage-quickstart-blobs-cli#create-and-manage-file-shares)

### <a name="reference"></a><span data-ttu-id="899bf-181">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="899bf-181">Reference</span></span>

- [<span data-ttu-id="899bf-182">Référence de la bibliothèque cliente de stockage pour .NET</span><span class="sxs-lookup"><span data-stu-id="899bf-182">Storage Client Library for .NET reference</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="899bf-183">Référence de l’API REST du service de fichiers</span><span class="sxs-lookup"><span data-stu-id="899bf-183">File Service REST API reference</span></span>](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a><span data-ttu-id="899bf-184">Billets de blog :</span><span class="sxs-lookup"><span data-stu-id="899bf-184">Blog posts</span></span>

- [<span data-ttu-id="899bf-185">Le stockage de fichiers Azure est désormais mis à la disposition générale</span><span class="sxs-lookup"><span data-stu-id="899bf-185">Azure File Storage is now generally available</span></span>](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [<span data-ttu-id="899bf-186">Stockage de fichiers dans Azure</span><span class="sxs-lookup"><span data-stu-id="899bf-186">Inside Azure File Storage</span></span>](https://azure.microsoft.com/blog/inside-azure-file-storage/)
- [<span data-ttu-id="899bf-187">Présentation de Microsoft Azure File Service</span><span class="sxs-lookup"><span data-stu-id="899bf-187">Introducing Microsoft Azure File Service</span></span>](/archive/blogs/windowsazurestorage/introducing-microsoft-azure-file-service)
- [<span data-ttu-id="899bf-188">Conservation des connexions vers les fichiers Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="899bf-188">Persisting connections to Microsoft Azure Files</span></span>](/archive/blogs/windowsazurestorage/persisting-connections-to-microsoft-azure-files)
