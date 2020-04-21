---
title: Bien démarrer avec le stockage Fichier Azure en F#
description: Stockez des données de fichier dans le cloud à l’aide du stockage de fichiers Azure, puis montez le partage de fichiers cloud à partir d’une machine virtuelle Azure ou d’une application locale exécutant Windows.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 1b38ee53f2f73f7b7f4ee12f712f487cb726d41e
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739595"
---
# <a name="get-started-with-azure-file-storage-using-f"></a>Démarez avec le stockage Azure File à l’aide de F\#

Azure File storage est un service qui offre des partages de fichiers dans le cloud à l’aide du protocole standard [Server Message Block (SMB).](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx) Les protocoles SMB 2.1 et SMB 3.0 sont pris en charge. Avec le stockage de fichiers Azure, vous pouvez migrer vers Azure des applications héritées qui s’appuient sur des partages de fichiers, rapidement et sans réécritures onéreuses. Les applications s’exécutant sur des machines virtuelles Azure, dans des services cloud ou à partir de clients locaux peuvent monter un partage de fichiers dans le cloud, tout comme une application de bureau monte un partage SMB standard. Un nombre illimité de composants d’application peuvent ensuite monter un partage de stockage de fichiers et y accéder simultanément.

Pour un aperçu conceptuel du stockage de fichiers, consultez [le guide .NET pour le stockage de fichiers](https://docs.microsoft.com/azure/storage/storage-dotnet-how-to-use-files).

## <a name="prerequisites"></a>Prérequis

Pour utiliser ce guide, vous devez [d’abord créer un compte de stockage Azure](https://docs.microsoft.com/azure/storage/storage-create-storage-account).
Vous aurez également besoin de votre clé d’accès au stockage pour ce compte.

## <a name="create-an-f-script-and-start-f-interactive"></a>Créer un script et démarrer en interactif

Les échantillons de cet article peuvent être utilisés dans une application F ou un script F. Pour créer un script F, créez `.fsx` un fichier `files.fsx`avec l’extension, par exemple, dans votre environnement de développement F.

Ensuite, utilisez un [gestionnaire de paquets](package-management.md) tel `WindowsAzure.Storage` que [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) pour installer le paquet et la référence `WindowsAzure.Storage.dll` dans votre script à l’aide d’une `#r` directive.

### <a name="add-namespace-declarations"></a>Ajout de déclarations d'espaces de noms

Ajoutez les instructions `open` suivantes au début du fichier `files.fsx` :

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Obtenir votre chaîne de connexion

Vous aurez besoin d’une chaîne de connexion Azure Storage pour ce tutoriel. Pour plus d’informations sur les chaînes de connexion, voir [Configurer les chaînes de connexion de stockage](https://docs.microsoft.com/azure/storage/storage-configure-connection-string).

Pour le tutoriel, vous entrerez votre chaîne de connexion dans votre script, comme ceci:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

Cependant, cela **n’est pas recommandé** pour les projets réels. Votre clé de compte de stockage est similaire au mot de passe racine pour votre compte de stockage. Veillez toujours à protéger votre clé de compte de stockage. Évitez de la communiquer à d’autres utilisateurs, de la coder en dur ou de l’enregistrer dans un fichier texte brut accessible à d’autres personnes. Vous pouvez régénérer votre clé à l’aide du portail Azure si vous pensez qu’elle a pu être compromise.

Pour les applications réelles, la meilleure façon de maintenir votre chaîne de connexion de stockage est dans un fichier de configuration. Pour récupérer la chaîne de connexion à partir d’un fichier de configuration, vous pouvez le faire :

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

L’utilisation d’Azure Configuration Manager est facultative. Vous pouvez également utiliser une API comme `ConfigurationManager` le type .NET Framework.

### <a name="parse-the-connection-string"></a>Analyse de la chaîne de connexion

Pour analyser la chaîne de connexion, utilisez :

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

Cela rendra `CloudStorageAccount`un .

### <a name="create-the-file-service-client"></a>Créer le client du service de fichiers

Le `CloudFileClient` type vous permet d’utiliser programmatiquement des fichiers stockés dans le stockage de fichiers. Voici un moyen de créer le client du service :

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

Maintenant, vous êtes prêt à écrire du code qui lit les données à partir et écrit des données au stockage de fichiers.

## <a name="create-a-file-share"></a>Créer un partage de fichiers

Cet exemple montre comment créer une part de fichier s’il n’existe pas déjà :

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a>Créer un répertoire racine et une sous-direction

Ici, vous obtenez le répertoire racine et obtenir une sous-direction de la racine. Vous créez les deux s’ils n’existent pas déjà.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a>Télécharger du texte comme un fichier

Cet exemple montre comment télécharger du texte sous forme de fichier.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a>Téléchargez un fichier sur une copie locale du fichier

Ici, vous téléchargez le fichier vient de créer, appending le contenu à un fichier local.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a>Définition de la taille maximale d’un partage de fichiers

L’exemple ci-dessous illustre comment vérifier l’utilisation actuelle pour un partage et comment définir le quota pour le partage. `FetchAttributes`doit être appelé à remplir `Properties`une `SetProperties` action, et à propager des modifications locales au stockage de fichiers Azure.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a>Génération d’une signature d’accès partagé pour un fichier ou partage de fichiers

Vous pouvez générer une signature d’accès partagé (SAP) pour un partage de fichiers ou un fichier individuel. Vous pouvez également créer une stratégie d’accès partagé sur un partage de fichiers pour gérer les signatures d’accès partagé. Créer une stratégie d’accès partagé est recommandé, car cette opération permet de révoquer la SAP si elle doit être compromise.

Ici, vous créez une politique d’accès partagé sur une part, puis utilisez cette politique pour fournir les contraintes pour un SAS sur un fichier dans la part.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

Pour plus d’informations sur la création et l’utilisation de signatures d’accès partagé, consultez [Utilisation des signatures d’accès partagé (SAP)](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1) et [Créer et utiliser une signature d’accès partagé avec Blob Storage](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-2).

### <a name="copy-files"></a>Copie des fichiers

Vous pouvez copier un fichier à un autre fichier ou à un blob, ou un blob à un fichier. Si vous copiez un blob à un fichier ou un fichier à un blob, vous *devez* utiliser une signature d’accès partagé (SAS) pour authentifier l’objet source, même si vous copiez dans le même compte de stockage.

### <a name="copy-a-file-to-another-file"></a>Copier un fichier dans un autre

Ici, vous copiez un fichier à un autre fichier dans la même part. Étant donné que cette opération de copie a lieu entre des fichiers du même compte de stockage, vous pouvez utiliser l’authentification Clé partagée pour l’effectuer.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a>Copier un fichier dans un objet blob

Ici, vous créez un fichier et le copiez à un blob dans le même compte de stockage. Vous créez un SAS pour le fichier source, que le service utilise pour authentifier l’accès au fichier source pendant l’opération de copie.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

Vous pouvez copier un objet blob dans un fichier de la même façon. Si l’objet source est un objet blob, créez une SAP pour authentifier l’accès à cet objet blob pendant l’opération de copie.

## <a name="troubleshooting-file-storage-using-metrics"></a>Résolution des problèmes de stockage de fichiers à l’aide de métriques

Azure Storage Analytics prend en charge les mesures de stockage de fichiers. Avec les données de métriques, vous pouvez suivre les demandes et diagnostiquer les problèmes.

Vous pouvez activer des mesures pour le stockage de fichiers à partir du [portail Azure,](https://portal.azure.com)ou vous pouvez le faire à partir de F 'comme ceci:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur le stockage de fichiers Azure, consultez ces liens.

### <a name="conceptual-articles-and-videos"></a>Vidéos et articles conceptuels

- [Stockage de fichiers Azure : un système de fichiers SMB dans le cloud sans friction pour Windows et Linux](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [Comment utiliser Azure File Storage avec Linux](https://docs.microsoft.com/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a>Outils pris en charge pour le stockage de fichiers

- [Utilisation d'Azure PowerShell avec Azure Storage](https://docs.microsoft.com/azure/storage/storage-powershell-guide-full)
- [Utilisation de AzCopy avec Microsoft Azure Storage](https://docs.microsoft.com/azure/storage/storage-use-azcopy)
- [Créer, télécharger et lister des objets blob avec Azure CLI](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-cli#create-and-manage-file-shares)

### <a name="reference"></a>Référence

- [Référence de la bibliothèque cliente de stockage pour .NET](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [Référence de l’API REST du service de fichiers](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a>Billets de blog :

- [Le stockage de fichiers Azure est désormais mis à la disposition générale](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [À l’intérieur azure De stockage de fichiers](https://azure.microsoft.com/blog/inside-azure-file-storage/)
- [Présentation de Microsoft Azure File Service](https://docs.microsoft.com/archive/blogs/windowsazurestorage/introducing-microsoft-azure-file-service)
- [Conservation des connexions vers les fichiers Microsoft Azure](https://docs.microsoft.com/archive/blogs/windowsazurestorage/persisting-connections-to-microsoft-azure-files)
