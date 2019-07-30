---
title: Bien démarrer avec le stockage Fichier Azure en F#
description: Stockez les données de fichier dans le Cloud avec le stockage de fichiers Azure, puis montez votre partage de fichiers Cloud à partir d’une machine virtuelle Azure ou d’une application locale exécutant Windows.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: a0e3cab56ba0f3db27335822616b4976a5d9de62
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630494"
---
# <a name="get-started-with-azure-file-storage-using-f"></a><span data-ttu-id="591b9-103">Prise en main du stockage de fichiers Azure à l’aide de F\#</span><span class="sxs-lookup"><span data-stu-id="591b9-103">Get started with Azure File storage using F\#</span></span>

<span data-ttu-id="591b9-104">Le stockage de fichiers Azure est un service qui offre des partages de fichiers dans le Cloud à l’aide du [protocole SMB (Server Message Block)](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx)standard.</span><span class="sxs-lookup"><span data-stu-id="591b9-104">Azure File storage is a service that offers file shares in the cloud using the standard [Server Message Block (SMB) Protocol](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span></span> <span data-ttu-id="591b9-105">SMB 2,1 et SMB 3,0 sont tous deux pris en charge.</span><span class="sxs-lookup"><span data-stu-id="591b9-105">Both SMB 2.1 and SMB 3.0 are supported.</span></span> <span data-ttu-id="591b9-106">Avec stockage fichier Azure, vous pouvez migrer des applications héritées qui s’appuient sur des partages de fichiers vers Azure rapidement et sans réécriture coûteuse.</span><span class="sxs-lookup"><span data-stu-id="591b9-106">With Azure File storage, you can migrate legacy applications that rely on file shares to Azure quickly and without costly rewrites.</span></span> <span data-ttu-id="591b9-107">Les applications qui s’exécutent sur des machines virtuelles Azure ou des services Cloud ou à partir de clients locaux peuvent monter un partage de fichiers dans le Cloud, tout comme une application de bureau monte un partage SMB standard.</span><span class="sxs-lookup"><span data-stu-id="591b9-107">Applications running in Azure virtual machines or cloud services or from on-premises clients can mount a file share in the cloud, just as a desktop application mounts a typical SMB share.</span></span> <span data-ttu-id="591b9-108">Un nombre quelconque de composants d’application peut ensuite monter le partage de stockage de fichiers et y accéder simultanément.</span><span class="sxs-lookup"><span data-stu-id="591b9-108">Any number of application components can then mount and access the File storage share simultaneously.</span></span>

<span data-ttu-id="591b9-109">Pour obtenir une vue d’ensemble conceptuelle du stockage de fichiers, consultez [le guide .net pour le stockage de fichiers](/azure/storage/storage-dotnet-how-to-use-files).</span><span class="sxs-lookup"><span data-stu-id="591b9-109">For a conceptual overview of file storage, please see [the .NET guide for file storage](/azure/storage/storage-dotnet-how-to-use-files).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="591b9-110">Prérequis</span><span class="sxs-lookup"><span data-stu-id="591b9-110">Prerequisites</span></span>

<span data-ttu-id="591b9-111">Pour utiliser ce guide, vous devez d’abord [créer un compte de stockage Azure](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="591b9-111">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="591b9-112">Vous aurez également besoin de votre clé d’accès de stockage pour ce compte.</span><span class="sxs-lookup"><span data-stu-id="591b9-112">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="591b9-113">Créer un F# script et démarrer F# interactive</span><span class="sxs-lookup"><span data-stu-id="591b9-113">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="591b9-114">Les exemples de cet article peuvent être utilisés dans une F# application ou un F# script.</span><span class="sxs-lookup"><span data-stu-id="591b9-114">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="591b9-115">Pour créer un F# script, créez un fichier avec l' `.fsx` extension, par exemple `files.fsx`, dans votre F# environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="591b9-115">To create an F# script, create a file with the `.fsx` extension, for example `files.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="591b9-116">Ensuite, utilisez un [Gestionnaire de package](package-management.md) comme [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) pour installer le `WindowsAzure.Storage` package et la `WindowsAzure.Storage.dll` référence dans votre script à `#r` l’aide d’une directive.</span><span class="sxs-lookup"><span data-stu-id="591b9-116">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="591b9-117">Ajouter des déclarations d’espace de noms</span><span class="sxs-lookup"><span data-stu-id="591b9-117">Add namespace declarations</span></span>

<span data-ttu-id="591b9-118">Ajoutez les instructions `open` suivantes au début `files.fsx` du fichier:</span><span class="sxs-lookup"><span data-stu-id="591b9-118">Add the following `open` statements to the top of the `files.fsx` file:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="591b9-119">Obtient votre chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="591b9-119">Get your connection string</span></span>

<span data-ttu-id="591b9-120">Vous aurez besoin d’une chaîne de connexion de stockage Azure pour ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="591b9-120">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="591b9-121">Pour plus d’informations sur les chaînes de connexion, consultez [configurer des chaînes de connexion de stockage](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="591b9-121">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="591b9-122">Pour le didacticiel, vous allez entrer votre chaîne de connexion dans votre script, comme suit:</span><span class="sxs-lookup"><span data-stu-id="591b9-122">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

<span data-ttu-id="591b9-123">Toutefois, cela n’est **pas recommandé** pour les projets réels.</span><span class="sxs-lookup"><span data-stu-id="591b9-123">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="591b9-124">Votre clé de compte de stockage est similaire au mot de passe racine de votre compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="591b9-124">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="591b9-125">Veillez toujours à protéger votre clé de compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="591b9-125">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="591b9-126">Évitez de la distribuer à d’autres utilisateurs, de la coder en dur ou de l’enregistrer dans un fichier texte brut accessible à d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="591b9-126">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="591b9-127">Vous pouvez régénérer votre clé à l’aide du portail Azure si vous pensez qu’elle a peut-être été compromise.</span><span class="sxs-lookup"><span data-stu-id="591b9-127">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="591b9-128">Pour les applications réelles, la meilleure façon de gérer votre chaîne de connexion de stockage se trouve dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="591b9-128">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="591b9-129">Pour extraire la chaîne de connexion d’un fichier de configuration, procédez comme suit:</span><span class="sxs-lookup"><span data-stu-id="591b9-129">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

<span data-ttu-id="591b9-130">L’utilisation d’Azure Configuration Manager est facultative.</span><span class="sxs-lookup"><span data-stu-id="591b9-130">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="591b9-131">Vous pouvez également utiliser une API telle que le type de `ConfigurationManager` .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="591b9-131">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="591b9-132">Analyser la chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="591b9-132">Parse the connection string</span></span>

<span data-ttu-id="591b9-133">Pour analyser la chaîne de connexion, utilisez:</span><span class="sxs-lookup"><span data-stu-id="591b9-133">To parse the connection string, use:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

<span data-ttu-id="591b9-134">Cela renverra un `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="591b9-134">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-file-service-client"></a><span data-ttu-id="591b9-135">Créer le client du service de fichiers</span><span class="sxs-lookup"><span data-stu-id="591b9-135">Create the File service client</span></span>

<span data-ttu-id="591b9-136">Le `CloudFileClient` type vous permet d’utiliser par programme des fichiers stockés dans le stockage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="591b9-136">The `CloudFileClient` type enables you to programmatically use files stored in File storage.</span></span> <span data-ttu-id="591b9-137">Voici un moyen de créer le client de service:</span><span class="sxs-lookup"><span data-stu-id="591b9-137">Here's one way to create the service client:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

<span data-ttu-id="591b9-138">Vous êtes maintenant prêt à écrire du code qui lit et écrit des données dans le stockage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="591b9-138">Now you are ready to write code that reads data from and writes data to File storage.</span></span>

## <a name="create-a-file-share"></a><span data-ttu-id="591b9-139">Créer un partage de fichiers</span><span class="sxs-lookup"><span data-stu-id="591b9-139">Create a file share</span></span>

<span data-ttu-id="591b9-140">Cet exemple montre comment créer un partage de fichiers s’il n’existe pas déjà:</span><span class="sxs-lookup"><span data-stu-id="591b9-140">This example shows how to create a file share if it does not already exist:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a><span data-ttu-id="591b9-141">Créer un répertoire racine et un sous-répertoire</span><span class="sxs-lookup"><span data-stu-id="591b9-141">Create a root directory and a subdirectory</span></span>

<span data-ttu-id="591b9-142">Ici, vous pouvez obtenir le répertoire racine et obtenir un sous-répertoire de la racine.</span><span class="sxs-lookup"><span data-stu-id="591b9-142">Here, you get the root directory and get a sub-directory of the root.</span></span> <span data-ttu-id="591b9-143">Vous créez les deux s’ils n’existent pas déjà.</span><span class="sxs-lookup"><span data-stu-id="591b9-143">You create both if they don't already exist.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a><span data-ttu-id="591b9-144">Charger du texte sous forme de fichier</span><span class="sxs-lookup"><span data-stu-id="591b9-144">Upload text as a file</span></span>

<span data-ttu-id="591b9-145">Cet exemple montre comment charger du texte sous la forme d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="591b9-145">This example shows how to upload text as a file.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a><span data-ttu-id="591b9-146">Télécharger un fichier vers une copie locale du fichier</span><span class="sxs-lookup"><span data-stu-id="591b9-146">Download a file to a local copy of the file</span></span>

<span data-ttu-id="591b9-147">Ici, vous téléchargez le fichier que vous venez de créer, en ajoutant le contenu à un fichier local.</span><span class="sxs-lookup"><span data-stu-id="591b9-147">Here you download the file just created, appending the contents to a local file.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a><span data-ttu-id="591b9-148">Définir la taille maximale d’un partage de fichiers</span><span class="sxs-lookup"><span data-stu-id="591b9-148">Set the maximum size for a file share</span></span>

<span data-ttu-id="591b9-149">L’exemple ci-dessous montre comment vérifier l’utilisation actuelle d’un partage et comment définir le quota pour le partage.</span><span class="sxs-lookup"><span data-stu-id="591b9-149">The example below shows how to check the current usage for a share and how to set the quota for the share.</span></span> <span data-ttu-id="591b9-150">`FetchAttributes`doit être appelé pour remplir un partage `Properties`et `SetProperties` pour propager les modifications locales au stockage fichier Azure.</span><span class="sxs-lookup"><span data-stu-id="591b9-150">`FetchAttributes` must be called to populate a share's `Properties`, and `SetProperties` to propagate local changes to Azure File storage.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a><span data-ttu-id="591b9-151">Générer une signature d’accès partagé pour un fichier ou un partage de fichiers</span><span class="sxs-lookup"><span data-stu-id="591b9-151">Generate a shared access signature for a file or file share</span></span>

<span data-ttu-id="591b9-152">Vous pouvez générer une signature d’accès partagé (SAP) pour un partage de fichiers ou un fichier individuel.</span><span class="sxs-lookup"><span data-stu-id="591b9-152">You can generate a shared access signature (SAS) for a file share or for an individual file.</span></span> <span data-ttu-id="591b9-153">Vous pouvez également créer une stratégie d’accès partagé sur un partage de fichiers pour gérer les signatures d’accès partagé.</span><span class="sxs-lookup"><span data-stu-id="591b9-153">You can also create a shared access policy on a file share to manage shared access signatures.</span></span> <span data-ttu-id="591b9-154">La création d’une stratégie d’accès partagé est recommandée, car elle fournit un moyen de révoquer la SAP si elle doit être compromise.</span><span class="sxs-lookup"><span data-stu-id="591b9-154">Creating a shared access policy is recommended, as it provides a means of revoking the SAS if it should be compromised.</span></span>

<span data-ttu-id="591b9-155">Ici, vous créez une stratégie d’accès partagé sur un partage, puis vous utilisez cette stratégie pour fournir les contraintes pour une SAP sur un fichier du partage.</span><span class="sxs-lookup"><span data-stu-id="591b9-155">Here, you create a shared access policy on a share, and then use that policy to provide the constraints for a SAS on a file in the share.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

<span data-ttu-id="591b9-156">Pour plus d’informations sur la création et l’utilisation de signatures d’accès partagé, consultez [utilisation des signatures d’accès partagé (SAP)](/azure/storage/storage-dotnet-shared-access-signature-part-1) et [créer et utiliser une signature d’accès partagé avec un stockage d’objets BLOB](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span><span class="sxs-lookup"><span data-stu-id="591b9-156">For more information about creating and using shared access signatures, see [Using Shared Access Signatures (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) and [Create and use a SAS with Blob storage](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span></span>

### <a name="copy-files"></a><span data-ttu-id="591b9-157">Copier les fichiers</span><span class="sxs-lookup"><span data-stu-id="591b9-157">Copy files</span></span>

<span data-ttu-id="591b9-158">Vous pouvez copier un fichier vers un autre fichier ou un objet BLOB, ou un objet BLOB dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="591b9-158">You can copy a file to another file or to a blob, or a blob to a file.</span></span> <span data-ttu-id="591b9-159">Si vous copiez un objet BLOB dans un fichier ou un fichier dans un objet BLOB, vous *devez* utiliser une signature d’accès partagé (SAP) pour authentifier l’objet source, même si vous effectuez une copie dans le même compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="591b9-159">If you are copying a blob to a file, or a file to a blob, you *must* use a shared access signature (SAS) to authenticate the source object, even if you are copying within the same storage account.</span></span>

### <a name="copy-a-file-to-another-file"></a><span data-ttu-id="591b9-160">Copier un fichier dans un autre fichier</span><span class="sxs-lookup"><span data-stu-id="591b9-160">Copy a file to another file</span></span>

<span data-ttu-id="591b9-161">Ici, vous copiez un fichier dans un autre fichier du même partage.</span><span class="sxs-lookup"><span data-stu-id="591b9-161">Here, you copy a file to another file in the same share.</span></span> <span data-ttu-id="591b9-162">Étant donné que cette opération de copie copie entre des fichiers dans le même compte de stockage, vous pouvez utiliser l’authentification par clé partagée pour effectuer la copie.</span><span class="sxs-lookup"><span data-stu-id="591b9-162">Because this copy operation copies between files in the same storage account, you can use Shared Key authentication to perform the copy.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a><span data-ttu-id="591b9-163">Copier un fichier dans un objet BLOB</span><span class="sxs-lookup"><span data-stu-id="591b9-163">Copy a file to a blob</span></span>

<span data-ttu-id="591b9-164">Ici, vous créez un fichier et le copiez dans un objet BLOB au sein du même compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="591b9-164">Here, you create a file and copy it to a blob within the same storage account.</span></span> <span data-ttu-id="591b9-165">Vous créez une SAP pour le fichier source, que le service utilise pour authentifier l’accès au fichier source pendant l’opération de copie.</span><span class="sxs-lookup"><span data-stu-id="591b9-165">You create a SAS for the source file, which the service uses to authenticate access to the source file during the copy operation.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

<span data-ttu-id="591b9-166">Vous pouvez copier un objet BLOB dans un fichier de la même façon.</span><span class="sxs-lookup"><span data-stu-id="591b9-166">You can copy a blob to a file in the same way.</span></span> <span data-ttu-id="591b9-167">Si l’objet source est un objet BLOB, créez une SAP pour authentifier l’accès à cet objet BLOB pendant l’opération de copie.</span><span class="sxs-lookup"><span data-stu-id="591b9-167">If the source object is a blob, then create a SAS to authenticate access to that blob during the copy operation.</span></span>

## <a name="troubleshooting-file-storage-using-metrics"></a><span data-ttu-id="591b9-168">Résolution des problèmes de stockage de fichiers à l’aide de mesures</span><span class="sxs-lookup"><span data-stu-id="591b9-168">Troubleshooting File storage using metrics</span></span>

<span data-ttu-id="591b9-169">Azure Storage Analytics prend en charge les métriques pour le stockage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="591b9-169">Azure Storage Analytics supports metrics for File storage.</span></span> <span data-ttu-id="591b9-170">Avec les données de métriques, vous pouvez suivre les demandes et diagnostiquer les problèmes.</span><span class="sxs-lookup"><span data-stu-id="591b9-170">With metrics data, you can trace requests and diagnose issues.</span></span>

<span data-ttu-id="591b9-171">Vous pouvez activer les métriques pour le stockage de fichiers à partir du [portail Azure](https://portal.azure.com), ou vous F# pouvez le faire de la manière suivante:</span><span class="sxs-lookup"><span data-stu-id="591b9-171">You can enable metrics for File storage from the [Azure Portal](https://portal.azure.com), or you can do it from F# like this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a><span data-ttu-id="591b9-172">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="591b9-172">Next steps</span></span>

<span data-ttu-id="591b9-173">Pour plus d’informations sur le stockage de fichiers Azure, consultez les liens suivants.</span><span class="sxs-lookup"><span data-stu-id="591b9-173">See these links for more information about Azure File storage.</span></span>

### <a name="conceptual-articles-and-videos"></a><span data-ttu-id="591b9-174">Articles et vidéos conceptuelles</span><span class="sxs-lookup"><span data-stu-id="591b9-174">Conceptual articles and videos</span></span>

- [<span data-ttu-id="591b9-175">Stockage Azure Files: système de fichiers SMB Cloud sans friction pour Windows et Linux</span><span class="sxs-lookup"><span data-stu-id="591b9-175">Azure Files Storage: a frictionless cloud SMB file system for Windows and Linux</span></span>](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [<span data-ttu-id="591b9-176">Utilisation du stockage de fichiers Azure avec Linux</span><span class="sxs-lookup"><span data-stu-id="591b9-176">How to use Azure File Storage with Linux</span></span>](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a><span data-ttu-id="591b9-177">Prise en charge des outils pour le stockage de fichiers</span><span class="sxs-lookup"><span data-stu-id="591b9-177">Tooling support for File storage</span></span>

- [<span data-ttu-id="591b9-178">Utilisation de Azure PowerShell avec le stockage Azure</span><span class="sxs-lookup"><span data-stu-id="591b9-178">Using Azure PowerShell with Azure Storage</span></span>](/azure/storage/storage-powershell-guide-full)
- [<span data-ttu-id="591b9-179">Utilisation de AzCopy avec Stockage Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="591b9-179">How to use AzCopy with Microsoft Azure Storage</span></span>](/azure/storage/storage-use-azcopy)
- [<span data-ttu-id="591b9-180">Utilisation de l’Azure CLI avec le stockage Azure</span><span class="sxs-lookup"><span data-stu-id="591b9-180">Using the Azure CLI with Azure Storage</span></span>](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a><span data-ttu-id="591b9-181">Référence</span><span class="sxs-lookup"><span data-stu-id="591b9-181">Reference</span></span>

- [<span data-ttu-id="591b9-182">Référence de la bibliothèque cliente de stockage pour .NET</span><span class="sxs-lookup"><span data-stu-id="591b9-182">Storage Client Library for .NET reference</span></span>](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [<span data-ttu-id="591b9-183">Référence de l’API REST du service de fichiers</span><span class="sxs-lookup"><span data-stu-id="591b9-183">File Service REST API reference</span></span>](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a><span data-ttu-id="591b9-184">Billets de blog</span><span class="sxs-lookup"><span data-stu-id="591b9-184">Blog posts</span></span>

- [<span data-ttu-id="591b9-185">Le stockage de fichiers Azure est désormais mis à la disposition générale</span><span class="sxs-lookup"><span data-stu-id="591b9-185">Azure File storage is now generally available</span></span>](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [<span data-ttu-id="591b9-186">À l’intérieur du stockage fichier Azure</span><span class="sxs-lookup"><span data-stu-id="591b9-186">Inside Azure File Storage</span></span>](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [<span data-ttu-id="591b9-187">Présentation de Microsoft Azure File Service</span><span class="sxs-lookup"><span data-stu-id="591b9-187">Introducing Microsoft Azure File Service</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/12/introducing-microsoft-azure-file-service/)
- [<span data-ttu-id="591b9-188">Conservation des connexions vers les fichiers Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="591b9-188">Persisting connections to Microsoft Azure Files</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/26/persisting-connections-to-microsoft-azure-files/)
