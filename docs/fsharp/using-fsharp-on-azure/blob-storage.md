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
# <a name="get-started-with-azure-blob-storage-using-f"></a>Prise en main du stockage d’objets BLOB Azure à l’aide de F\#

Le stockage Blob Azure est un service qui stocke les données non structurées dans le cloud en tant qu’objets/objets blob. Le stockage Blob permet de stocker n’importe quel type de données texte ou binaires, par exemple un document, un fichier multimédia ou un programme d’installation d’application. Le stockage Blob est également appelé stockage d’objets.

Cet article explique comment effectuer des tâches courantes à l’aide du stockage d’objets BLOB. Les exemples sont écrits à F# l’aide de la bibliothèque cliente de stockage Azure pour .net. Les tâches traitées incluent le chargement, la liste, le téléchargement et la suppression d’objets BLOB.

Pour obtenir une vue d’ensemble conceptuelle du stockage d’objets BLOB, consultez [le guide .net pour le stockage d’objets BLOB](/azure/storage/storage-dotnet-how-to-use-blobs).

## <a name="prerequisites"></a>Prérequis

Pour utiliser ce guide, vous devez d’abord [créer un compte de stockage Azure](/azure/storage/storage-create-storage-account). Vous avez également besoin de votre clé d’accès de stockage pour ce compte.

## <a name="create-an-f-script-and-start-f-interactive"></a>Créer un F# script et démarrer F# interactive

Les exemples de cet article peuvent être utilisés dans une F# application ou un F# script. Pour créer un F# script, créez un fichier avec l' `.fsx` extension, par exemple `blobs.fsx`, dans votre F# environnement de développement.

Ensuite, utilisez un [Gestionnaire de package](package-management.md) comme [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) pour installer les `WindowsAzure.Storage` `Microsoft.WindowsAzure.ConfigurationManager` packages et et référence `WindowsAzure.Storage.dll` `Microsoft.WindowsAzure.Configuration.dll` et dans votre script à l' `#r` aide d’une directive.

### <a name="add-namespace-declarations"></a>Ajouter des déclarations d’espace de noms

Ajoutez les instructions `open` suivantes au début `blobs.fsx` du fichier:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Obtient votre chaîne de connexion

Vous avez besoin d’une chaîne de connexion de stockage Azure pour ce didacticiel. Pour plus d’informations sur les chaînes de connexion, consultez [configurer des chaînes de connexion de stockage](/azure/storage/storage-configure-connection-string).

Pour le didacticiel, vous entrez votre chaîne de connexion dans votre script, comme suit:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

Toutefois, cela n’est **pas recommandé** pour les projets réels. Votre clé de compte de stockage est similaire au mot de passe racine de votre compte de stockage. Veillez toujours à protéger votre clé de compte de stockage. Évitez de la distribuer à d’autres utilisateurs, de la coder en dur ou de l’enregistrer dans un fichier texte brut accessible à d’autres utilisateurs. Vous pouvez régénérer votre clé à l’aide du portail Azure si vous pensez qu’elle a peut-être été compromise.

Pour les applications réelles, la meilleure façon de gérer votre chaîne de connexion de stockage se trouve dans un fichier de configuration. Pour extraire la chaîne de connexion d’un fichier de configuration, procédez comme suit:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

L’utilisation d’Azure Configuration Manager est facultative. Vous pouvez également utiliser une API telle que le type de `ConfigurationManager` .NET Framework.

### <a name="parse-the-connection-string"></a>Analyser la chaîne de connexion

Pour analyser la chaîne de connexion, utilisez:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

Cela retourne un `CloudStorageAccount`.

### <a name="create-some-local-dummy-data"></a>Créer des données fictives locales

Avant de commencer, créez des données locales factices dans le répertoire de notre script. Plus tard, vous téléchargez ces données.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a>Créer le client du service BLOB

Le `CloudBlobClient` type vous permet de récupérer des conteneurs et des objets BLOB stockés dans le stockage d’objets BLOB. Voici un moyen de créer le client de service:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

Vous êtes maintenant prêt à écrire du code qui lit et écrit des données dans le stockage d’objets BLOB.

## <a name="create-a-container"></a>Créer un conteneur

Cet exemple montre comment créer un conteneur s’il n’existe pas déjà:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

Par défaut, le nouveau conteneur est privé, ce qui signifie que vous devez spécifier votre clé d’accès de stockage pour télécharger des objets BLOB à partir de ce conteneur. Si vous souhaitez que les fichiers du conteneur soient disponibles pour tout le monde, vous pouvez configurer le conteneur pour qu’il soit public à l’aide du code suivant:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

Toute personne sur Internet peut voir des objets BLOB dans un conteneur public, mais vous pouvez les modifier ou les supprimer uniquement si vous disposez de la clé d’accès de compte appropriée ou d’une signature d’accès partagé.

## <a name="upload-a-blob-into-a-container"></a>Charger un objet BLOB dans un conteneur

Le stockage d’objets BLOB Azure prend en charge les objets BLOB de blocs et de pages. Dans la plupart des cas, un objet blob de blocs est le type recommandé à utiliser.

Pour télécharger un fichier vers un objet blob de blocs, récupérez une référence de conteneur et utilisez-la pour obtenir une référence d’objet blob de blocs. Une fois que vous avez une référence d’objet BLOB, vous pouvez charger n’importe quel flux de `UploadFromFile` données en appelant la méthode. Cette opération crée l’objet BLOB s’il n’existe pas déjà, ou le remplace s’il existe.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a>Répertorier les objets BLOB dans un conteneur

Pour répertorier les objets BLOB dans un conteneur, commencez par obtenir une référence de conteneur. Vous pouvez ensuite utiliser la méthode du `ListBlobs` conteneur pour récupérer les objets BLOB et/ou les répertoires qu’il contient. Pour accéder à l’ensemble complet de propriétés et de méthodes pour `IListBlobItem`un retourné, vous devez effectuer un `CloudBlockBlob`cast de celui `CloudBlobDirectory` -ci en un objet, `CloudPageBlob`ou. Si le type est inconnu, vous pouvez utiliser une vérification de type pour déterminer le vers lequel effectuer un cast. Le code suivant montre comment récupérer et générer l’URI de chaque élément `mydata` du conteneur:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

Vous pouvez également nommer des objets BLOB avec des informations de chemin d’accès dans leurs noms. Cela crée une structure de répertoires virtuels que vous pouvez organiser et parcourir comme un système de fichiers traditionnel. Notez que la structure de répertoires est virtuelle uniquement-les seules ressources disponibles dans le stockage d’objets BLOB sont des conteneurs et des objets BLOB. Toutefois, la bibliothèque cliente de stockage `CloudBlobDirectory` offre un objet pour faire référence à un répertoire virtuel et simplifier le processus d’utilisation des objets BLOB organisés de cette façon.

Par exemple, considérez l’ensemble suivant d’objets BLOB de blocs dans `photos`un conteneur nommé:

*photo1.jpg*\
*2015/architecture/description.txt*\
*2015/architecture/photo3.jpg*\
*2015/architecture/photo4.jpg*\
*2016/architecture/photo5.jpg*\
*2016/architecture/photo6.jpg*\
*2016/architecture/description.txt*\
*2016/photo7.jpg*\

Lorsque vous appelez `ListBlobs` sur un conteneur (comme dans l’exemple ci-dessus), une liste hiérarchique est retournée. S’il contient à `CloudBlobDirectory` la `CloudBlockBlob` fois des objets et, représentant respectivement les répertoires et les objets BLOB du conteneur, le résultat obtenu ressemble à ceci:

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

Si vous le souhaitez, vous pouvez `UseFlatBlobListing` définir le paramètre `ListBlobs` de la `true`méthode sur. Dans ce cas, tous les objets BLOB du conteneur sont retournés en tant qu' `CloudBlockBlob` objet. L’appel à `ListBlobs` pour retourner une liste plate ressemble à ceci:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

et, selon le contenu actuel de votre conteneur, les résultats ressemblent à ceci:

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

## <a name="download-blobs"></a>Télécharger les objets BLOB

Pour télécharger des objets BLOB, commencez par récupérer une référence d’objet `DownloadToStream` BLOB, puis appelez la méthode. L’exemple suivant utilise la `DownloadToStream` méthode pour transférer le contenu de l’objet BLOB vers un objet de flux que vous pouvez ensuite conserver dans un fichier local.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

Vous pouvez également utiliser la `DownloadToStream` méthode pour télécharger le contenu d’un objet blob sous la forme d’une chaîne de texte.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a>Supprimer les objets BLOB

Pour supprimer un objet BLOB, commencez par obtenir une référence d’objet BLOB `Delete` , puis appelez la méthode sur celui-ci.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a>Répertorier les objets BLOB dans les pages de manière asynchrone

Si vous répertoriez un grand nombre d’objets BLOB ou que vous souhaitez contrôler le nombre de résultats retournés dans une opération de liste, vous pouvez répertorier les objets BLOB dans les pages de résultats. Cet exemple montre comment retourner des résultats dans des pages de manière asynchrone, afin que l’exécution ne soit pas bloquée en attendant de retourner un grand nombre de résultats.

Cet exemple montre une liste d’objets BLOB plats, mais vous pouvez également effectuer une liste hiérarchique en affectant `useFlatBlobListing` au paramètre de `ListBlobsSegmentedAsync` la méthode `false`la valeur.

L’exemple définit une méthode asynchrone à l’aide `async` d’un bloc. Le ``let!`` mot clé interrompt l’exécution de l’exemple de méthode jusqu’à ce que la tâche de liste se termine.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

Nous pouvons maintenant utiliser cette routine asynchrone comme suit. Tout d’abord, vous téléchargez des données factices (à l’aide du fichier local créé précédemment dans ce didacticiel).

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

À présent, appelez la routine. Vous utilisez `Async.RunSynchronously` pour forcer l’exécution de l’opération asynchrone.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a>Écriture dans un objet blob d’ajout

Un objet blob d’ajout est optimisé pour les opérations d’ajout, telles que la journalisation. À l’instar d’un objet blob de blocs, un objet blob d’ajout est constitué de blocs, mais lorsque vous ajoutez un nouveau bloc à un objet blob d’ajout, il est toujours ajouté à la fin de l’objet BLOB. Vous ne pouvez pas mettre à jour ou supprimer un bloc existant dans un objet blob d’ajout. Les ID de bloc d’un objet blob d’ajout ne sont pas exposés, car ils sont destinés à un objet blob de blocs.

Chaque bloc dans un objet blob d’ajout peut avoir une taille différente, jusqu’à un maximum de 4 Mo, et un objet blob d’ajout peut inclure un maximum de 50 000 blocs. La taille maximale d’un objet blob d’ajout est donc légèrement supérieure à 195 Go (4 Mo X 50 000 blocs).

L’exemple suivant crée un nouvel objet blob d’ajout et y ajoute des données, en simulant une opération de journalisation simple.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

Pour plus d’informations sur les différences entre les trois types d’objets BLOB, consultez Présentation des objets BLOB de [blocs, objets BLOB de pages et objets BLOB d’ajout](https://msdn.microsoft.com/library/azure/ee691964.aspx) .

## <a name="concurrent-access"></a>Accès simultané

Pour prendre en charge l’accès simultané à un objet blob à partir de plusieurs clients ou d' instances de processus, vous pouvez utiliser des ETags ou des **baux**.

* **ETag** -fournit un moyen de détecter que l’objet BLOB ou le conteneur a été modifié par un autre processus

* **Bail** -fournit un moyen d’obtenir un accès exclusif, renouvelable, en écriture ou en suppression sur un objet BLOB pendant une période donnée.

Pour plus d’informations, consultez [gestion de l’accès concurrentiel dans stockage Microsoft Azure](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).

## <a name="naming-containers"></a>Nommer des conteneurs

Chaque objet BLOB du stockage Azure doit résider dans un conteneur. Le conteneur fait partie du nom de l’objet BLOB. Par exemple, `mydata` est le nom du conteneur dans ces exemples d’URI d’objet BLOB:

- https://storagesample.blob.core.windows.net/mydata/blob1.txt
- https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

Un nom de conteneur doit être un nom DNS valide, conforme aux règles d’affectation de noms suivantes:

1. Les noms de conteneur doivent commencer par une lettre ou un chiffre, et ne peuvent contenir que des lettres, des chiffres et des tirets (-).
1. Chaque tiret (-) doit être immédiatement précédé et suivi d’une lettre ou d’un chiffre. les tirets consécutifs ne sont pas autorisés dans les noms de conteneurs.
1. Toutes les lettres d’un nom de conteneur doivent être en minuscules.
1. Les noms de conteneur doivent être compris entre 3 et 63 caractères.

Notez que le nom d’un conteneur doit toujours être en minuscules. Si vous incluez une lettre majuscule dans un nom de conteneur ou si vous violez les règles d’affectation de noms de conteneurs, vous pouvez recevoir une erreur 400 (requête incorrecte).

## <a name="managing-security-for-blobs"></a>Gestion de la sécurité des objets BLOB

Par défaut, le stockage Azure assure la sécurité de vos données en limitant l’accès au propriétaire du compte, qui est en possession des clés d’accès du compte. Lorsque vous devez partager des données BLOB dans votre compte de stockage, il est important de le faire sans compromettre la sécurité de vos clés d’accès de votre compte. En outre, vous pouvez chiffrer les données d’objet BLOB pour vous assurer qu’elles sont sécurisées sur le réseau et dans le stockage Azure.

### <a name="controlling-access-to-blob-data"></a>Contrôle de l’accès aux données d’objets BLOB

Par défaut, les données d’objet blob de votre compte de stockage sont accessibles uniquement au propriétaire du compte de stockage. L’authentification des demandes sur le stockage d’objets BLOB requiert la clé d’accès au compte par défaut. Toutefois, vous souhaiterez peut-être mettre certaines données BLOB à la disposition d’autres utilisateurs.

### <a name="encrypting-blob-data"></a>Chiffrement des données BLOB

Le stockage Azure prend en charge le chiffrement des données BLOB à la fois sur le client et sur le serveur.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez appris les principes de base du stockage d’objets BLOB, suivez ces liens pour en savoir plus.

### <a name="tools"></a>Outils

- [F#AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)\
Fournisseur F# de type qui peut être utilisé pour explorer des ressources de stockage Azure d’objets BLOB, de table et de file d’attente et pour appliquer facilement des opérations CRUD sur ceux-ci.

- [FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)\
F# API pour l’utilisation du service de stockage de table Microsoft Azure

- [Explorateur Stockage Microsoft Azure (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)\
Une application autonome et gratuite de Microsoft qui vous permet de travailler visuellement avec les données de stockage Azure sur Windows, OS X et Linux.

### <a name="blob-storage-reference"></a>Référence du stockage d’objets BLOB

- [API de stockage Azure pour .NET](/dotnet/api/overview/azure/storage)
- [Informations de référence sur l’API REST des services de stockage Azure](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a>Guides connexes

- [Prise en main avec le stockage d’objets BLOB Azure dansC#](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [Transfert de données avec l’utilitaire de ligne de commande AzCopy sur Windows](/azure/storage/common/storage-use-azcopy)
- [Transfert de données avec l’utilitaire de ligne de commande AzCopy sur Linux](/azure/storage/common/storage-use-azcopy-linux)
- [Configurer des chaînes de connexion de stockage Azure](/azure/storage/common/storage-configure-connection-string)
- [Blog de l’équipe stockage Azure](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Démarrage rapide : Utiliser .NET pour créer un objet BLOB dans le stockage d’objets](/azure/storage/blobs/storage-quickstart-blobs-dotnet)
