---
title: Bien démarrer avec le stockage Fichier Azure en F#
description: Stockez les données de fichier dans le Cloud avec le stockage de fichiers Azure, puis montez votre partage de fichiers Cloud à partir d’une machine virtuelle Azure ou d’une application locale exécutant Windows.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 9c25ab930abcbe7b358ae63c709aba4e97aed3be
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423864"
---
# <a name="get-started-with-azure-file-storage-using-f"></a>Prise en main du stockage de fichiers Azure à l’aide de F\#

Le stockage de fichiers Azure est un service qui offre des partages de fichiers dans le Cloud à l’aide du [protocole SMB (Server Message Block)](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx)standard. SMB 2,1 et SMB 3,0 sont tous deux pris en charge. Avec stockage fichier Azure, vous pouvez migrer des applications héritées qui s’appuient sur des partages de fichiers vers Azure rapidement et sans réécriture coûteuse. Les applications qui s’exécutent sur des machines virtuelles Azure ou des services Cloud ou à partir de clients locaux peuvent monter un partage de fichiers dans le Cloud, tout comme une application de bureau monte un partage SMB standard. Un nombre quelconque de composants d’application peut ensuite monter le partage de stockage de fichiers et y accéder simultanément.

Pour obtenir une vue d’ensemble conceptuelle du stockage de fichiers, consultez [le guide .net pour le stockage de fichiers](/azure/storage/storage-dotnet-how-to-use-files).

## <a name="prerequisites"></a>Configuration requise

Pour utiliser ce guide, vous devez d’abord [créer un compte de stockage Azure](/azure/storage/storage-create-storage-account).
Vous aurez également besoin de votre clé d’accès de stockage pour ce compte.

## <a name="create-an-f-script-and-start-f-interactive"></a>Créer un F# script et démarrer F# interactive

Les exemples de cet article peuvent être utilisés dans une F# application ou un F# script. Pour créer un F# script, créez un fichier avec l’extension `.fsx`, par exemple `files.fsx`, dans votre F# environnement de développement.

Ensuite, utilisez un [Gestionnaire de package](package-management.md) comme [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) pour installer le package `WindowsAzure.Storage` et référencez `WindowsAzure.Storage.dll` dans votre script à l’aide d’une directive `#r`.

### <a name="add-namespace-declarations"></a>Ajouter des déclarations d’espace de noms

Ajoutez les instructions `open` suivantes en haut du fichier `files.fsx` :

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Obtient votre chaîne de connexion

Vous aurez besoin d’une chaîne de connexion de stockage Azure pour ce didacticiel. Pour plus d’informations sur les chaînes de connexion, consultez [configurer des chaînes de connexion de stockage](/azure/storage/storage-configure-connection-string).

Pour le didacticiel, vous allez entrer votre chaîne de connexion dans votre script, comme suit :

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

Toutefois, cela n’est **pas recommandé** pour les projets réels. Votre clé de compte de stockage est similaire au mot de passe racine de votre compte de stockage. Veillez toujours à protéger votre clé de compte de stockage. Évitez de la distribuer à d’autres utilisateurs, de la coder en dur ou de l’enregistrer dans un fichier texte brut accessible à d’autres utilisateurs. Vous pouvez régénérer votre clé à l’aide du portail Azure si vous pensez qu’elle a peut-être été compromise.

Pour les applications réelles, la meilleure façon de gérer votre chaîne de connexion de stockage se trouve dans un fichier de configuration. Pour extraire la chaîne de connexion d’un fichier de configuration, procédez comme suit :

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

L’utilisation d’Azure Configuration Manager est facultative. Vous pouvez également utiliser une API telle que le type `ConfigurationManager` de .NET Framework.

### <a name="parse-the-connection-string"></a>Analyser la chaîne de connexion

Pour analyser la chaîne de connexion, utilisez :

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

Une `CloudStorageAccount`est alors retournée.

### <a name="create-the-file-service-client"></a>Créer le client du service de fichiers

Le type de `CloudFileClient` vous permet d’utiliser par programme des fichiers stockés dans le stockage de fichiers. Voici un moyen de créer le client de service :

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

Vous êtes maintenant prêt à écrire du code qui lit et écrit des données dans le stockage de fichiers.

## <a name="create-a-file-share"></a>Créer un partage de fichiers

Cet exemple montre comment créer un partage de fichiers s’il n’existe pas déjà :

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a>Créer un répertoire racine et un sous-répertoire

Ici, vous pouvez obtenir le répertoire racine et obtenir un sous-répertoire de la racine. Vous créez les deux s’ils n’existent pas déjà.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a>Charger du texte sous forme de fichier

Cet exemple montre comment charger du texte sous la forme d’un fichier.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a>Télécharger un fichier vers une copie locale du fichier

Ici, vous téléchargez le fichier que vous venez de créer, en ajoutant le contenu à un fichier local.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a>Définir la taille maximale d’un partage de fichiers

L’exemple ci-dessous montre comment vérifier l’utilisation actuelle d’un partage et comment définir le quota pour le partage. `FetchAttributes` doit être appelé pour remplir le `Properties`d’un partage, et `SetProperties` pour propager les modifications locales au stockage fichier Azure.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a>Générer une signature d’accès partagé pour un fichier ou un partage de fichiers

Vous pouvez générer une signature d’accès partagé (SAP) pour un partage de fichiers ou un fichier individuel. Vous pouvez également créer une stratégie d’accès partagé sur un partage de fichiers pour gérer les signatures d’accès partagé. La création d’une stratégie d’accès partagé est recommandée, car elle fournit un moyen de révoquer la SAP si elle doit être compromise.

Ici, vous créez une stratégie d’accès partagé sur un partage, puis vous utilisez cette stratégie pour fournir les contraintes pour une SAP sur un fichier du partage.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

Pour plus d’informations sur la création et l’utilisation de signatures d’accès partagé, consultez [utilisation des signatures d’accès partagé (SAP)](/azure/storage/storage-dotnet-shared-access-signature-part-1) et [créer et utiliser une signature d’accès partagé avec un stockage d’objets BLOB](/azure/storage/storage-dotnet-shared-access-signature-part-2).

### <a name="copy-files"></a>Copier les fichiers

Vous pouvez copier un fichier vers un autre fichier ou un objet BLOB, ou un objet BLOB dans un fichier. Si vous copiez un objet BLOB dans un fichier ou un fichier dans un objet BLOB, vous *devez* utiliser une signature d’accès partagé (SAP) pour authentifier l’objet source, même si vous effectuez une copie dans le même compte de stockage.

### <a name="copy-a-file-to-another-file"></a>Copier un fichier dans un autre fichier

Ici, vous copiez un fichier dans un autre fichier du même partage. Étant donné que cette opération de copie copie entre des fichiers dans le même compte de stockage, vous pouvez utiliser l’authentification par clé partagée pour effectuer la copie.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a>Copier un fichier dans un objet BLOB

Ici, vous créez un fichier et le copiez dans un objet BLOB au sein du même compte de stockage. Vous créez une SAP pour le fichier source, que le service utilise pour authentifier l’accès au fichier source pendant l’opération de copie.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

Vous pouvez copier un objet BLOB dans un fichier de la même façon. Si l’objet source est un objet BLOB, créez une SAP pour authentifier l’accès à cet objet BLOB pendant l’opération de copie.

## <a name="troubleshooting-file-storage-using-metrics"></a>Résolution des problèmes de stockage de fichiers à l’aide de mesures

Azure Storage Analytics prend en charge les métriques pour le stockage de fichiers. Avec les données de métriques, vous pouvez suivre les demandes et diagnostiquer les problèmes.

Vous pouvez activer les métriques pour le stockage de fichiers à partir du [portail Azure](https://portal.azure.com), ou vous F# pouvez le faire de la manière suivante :

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur le stockage de fichiers Azure, consultez les liens suivants.

### <a name="conceptual-articles-and-videos"></a>Articles et vidéos conceptuelles

- [Stockage Azure Files : système de fichiers SMB Cloud sans friction pour Windows et Linux](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [Utilisation du stockage de fichiers Azure avec Linux](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a>Prise en charge des outils pour le stockage de fichiers

- [Utilisation de Azure PowerShell avec le stockage Azure](/azure/storage/storage-powershell-guide-full)
- [Utilisation de AzCopy avec Stockage Microsoft Azure](/azure/storage/storage-use-azcopy)
- [Utilisation de l’Azure CLI avec le stockage Azure](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a>Reference

- [Référence de la bibliothèque cliente de stockage pour .NET](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [Référence de l’API REST du service de fichiers](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a>Billets de blog

- [Le stockage de fichiers Azure est désormais mis à la disposition générale](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [À l’intérieur du stockage fichier Azure](https://azure.microsoft.com/blog/inside-azure-file-storage/)
- [Présentation du service de fichiers Microsoft Azure](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/12/introducing-microsoft-azure-file-service/)
- [Persistance des connexions aux fichiers Microsoft Azure](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/26/persisting-connections-to-microsoft-azure-files/)
