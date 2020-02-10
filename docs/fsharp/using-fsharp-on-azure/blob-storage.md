---
title: Bien démarrer avec le stockage Blob Azure en F#
description: Stockez des données non structurées dans le Cloud avec le stockage d’objets BLOB Azure.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 79f6a559ac603b0544916764126a988d3f3f43d7
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092627"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a>Prise en main du stockage d’objets BLOB Azure à l’aide de F\#

Le stockage d’objets blob Azure est un service qui stocke des données non structurées dans le cloud en tant qu’objets/blobs. Ce service peut stocker tout type de données texte ou binaires, par exemple, un document, un fichier multimédia ou un programme d’installation d’application. Le stockage d’objets blob est également appelé Stockage Blob.

Cet article explique comment effectuer des tâches courantes à l’aide du stockage d’objets BLOB. Les exemples sont écrits à F# l’aide de la bibliothèque cliente de stockage Azure pour .net. Les tâches traitées incluent le chargement, la liste, le téléchargement et la suppression d’objets BLOB.

Pour obtenir une vue d’ensemble conceptuelle du stockage d’objets BLOB, consultez [le guide .net pour le stockage d’objets BLOB](/azure/storage/blobs/storage-quickstart-blobs-dotnet).

## <a name="prerequisites"></a>Conditions préalables requises

Pour utiliser ce guide, vous devez d’abord [créer un compte de stockage Azure](/azure/storage/common/storage-account-create). Vous avez également besoin de votre clé d’accès de stockage pour ce compte.

## <a name="create-an-f-script-and-start-f-interactive"></a>Créer un F# script et démarrer F# interactive

Les exemples de cet article peuvent être utilisés dans une F# application ou un F# script. Pour créer un F# script, créez un fichier avec l’extension `.fsx`, par exemple `blobs.fsx`, dans votre F# environnement de développement.

Ensuite, utilisez un [Gestionnaire de package](package-management.md) comme [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) pour installer les packages `WindowsAzure.Storage` et `Microsoft.WindowsAzure.ConfigurationManager`, ainsi que les `WindowsAzure.Storage.dll` de référence et `Microsoft.WindowsAzure.Configuration.dll` dans votre script à l’aide d’une directive `#r`.

### <a name="add-namespace-declarations"></a>Ajout de déclarations d'espaces de noms

Ajoutez les instructions `open` suivantes au début du fichier `blobs.fsx` :

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Obtenir votre chaîne de connexion

Vous avez besoin d’une chaîne de connexion de stockage Azure pour ce didacticiel. Pour plus d’informations sur les chaînes de connexion, consultez [configurer des chaînes de connexion de stockage](/azure/storage/storage-configure-connection-string).

Pour le didacticiel, vous entrez votre chaîne de connexion dans votre script, comme suit :

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

Toutefois, cela n’est **pas recommandé** pour les projets réels. Votre clé de compte de stockage est similaire au mot de passe racine pour votre compte de stockage. Veillez toujours à protéger votre clé de compte de stockage. Évitez de la communiquer à d’autres utilisateurs, de la coder en dur ou de l’enregistrer dans un fichier texte brut accessible à d’autres personnes. Vous pouvez régénérer votre clé à l’aide du portail Azure si vous pensez qu’elle a peut-être été compromise.

Pour les applications réelles, la meilleure façon de gérer votre chaîne de connexion de stockage se trouve dans un fichier de configuration. Pour extraire la chaîne de connexion d’un fichier de configuration, procédez comme suit :

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

L’utilisation d’Azure Configuration Manager est facultative. Vous pouvez également utiliser une API telle que le type de `ConfigurationManager` du .NET Framework.

### <a name="parse-the-connection-string"></a>Analyse de la chaîne de connexion

Pour analyser la chaîne de connexion, utilisez :

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

Cela retourne un `CloudStorageAccount`.

### <a name="create-some-local-dummy-data"></a>Créer des données fictives locales

Avant de commencer, créez des données locales factices dans le répertoire de notre script. Plus tard, vous téléchargez ces données.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a>Créer le client du service Blob

Le type de `CloudBlobClient` vous permet de récupérer des conteneurs et des objets BLOB stockés dans le stockage d’objets BLOB. Voici un moyen de créer le client du service :

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

Vous êtes maintenant prêt à écrire du code qui lit et écrit des données dans le Blob Storage.

## <a name="create-a-container"></a>Créez un conteneur.

Cet exemple montre comment créer un conteneur, si celui-ci n’existe pas encore :

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

Le nouveau conteneur est privé par défaut, ce qui signifie que vous devez indiquer votre clé d’accès de stockage pour télécharger des objets blob depuis ce conteneur. Si vous voulez que les fichiers du conteneur soient publics, vous pouvez configurer le conteneur en utilisant le code suivant :

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

Tous les utilisateurs d’Internet peuvent afficher des objets blob d’un conteneur public, mais vous ne pouvez les modifier ou les supprimer que si vous disposez de la clé d’accès du compte ou de la signature d'accès partagé adéquate.

## <a name="upload-a-blob-into-a-container"></a>Charger un objet blob dans un conteneur

Le service de stockage d’objets blob Azure prend en charge les objets blob de blocs et de page. Dans la plupart des cas, un objet blob de blocs est le type recommandé à utiliser.

Pour télécharger un fichier vers un objet blob de blocs, obtenez une référence de conteneur et utilisez-la pour obtenir une référence d’objet blob de blocs. Une fois que vous avez une référence d’objet BLOB, vous pouvez charger n’importe quel flux de données en appelant la méthode `UploadFromFile`. Cette opération crée l’objet BLOB s’il n’existe pas déjà, ou le remplace s’il existe.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a>Créer la liste des objets blob d’un conteneur

Pour créer une liste d’objets blob dans un conteneur, commencez par obtenir une référence pointant vers un conteneur. Vous pouvez ensuite utiliser la méthode `ListBlobs` du conteneur pour récupérer les objets BLOB et/ou les répertoires qu’il contient. Pour accéder à l’ensemble complet de propriétés et de méthodes pour une `IListBlobItem`retournée, vous devez effectuer un cast de celui-ci en objet `CloudBlockBlob`, `CloudPageBlob`ou `CloudBlobDirectory`. Si vous ne connaissez pas le type, vous pouvez lancer une vérification de type pour déterminer la cible de l’appel. Le code suivant illustre la récupération et la génération de l’URI de chaque élément du conteneur `mydata` :

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

Vous pouvez également nommer des objets BLOB avec des informations de chemin d’accès dans leurs noms. Vous obtenez alors une structure de répertoires virtuels que vous pouvez organiser et parcourir de la même manière qu’un système de fichiers traditionnel. Notez que la structure de répertoires est uniquement virtuelle : les seules ressources disponibles dans le stockage d’objets blob sont des conteneurs et des objets blob. Toutefois, la bibliothèque cliente de stockage offre un objet `CloudBlobDirectory` pour faire référence à un répertoire virtuel et simplifier le processus d’utilisation des objets BLOB organisés de cette façon.

Par exemple, prenez l’ensemble d’objets blob de blocs suivant, situé dans un conteneur nommé `photos`:

*PHOTO1. jpg*\
*2015/architecture/Description. txt*\
*2015/architecture/Photo3. jpg*\
*2015/architecture/Photo4. jpg*\
*2016/architecture/Photo5. jpg*\
*2016/architecture/Photo6. jpg*\
*2016/architecture/Description. txt*\
\ *2016/Photo7. jpg*

Lorsque vous appelez `ListBlobs` sur un conteneur (comme dans l’exemple ci-dessus), une liste hiérarchique est retournée. S’il contient à la fois des objets `CloudBlobDirectory` et `CloudBlockBlob`, représentant respectivement les répertoires et les objets BLOB du conteneur, le résultat obtenu ressemble à ceci :

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

Si vous le souhaitez, vous pouvez définir le paramètre `UseFlatBlobListing` de la méthode `ListBlobs` sur `true`. Dans ce cas, tous les objets BLOB du conteneur sont retournés en tant qu’objet `CloudBlockBlob`. L’appel à `ListBlobs` pour retourner une liste plate ressemble à ceci :

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

et, selon le contenu actuel de votre conteneur, les résultats ressemblent à ceci :

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

## <a name="download-blobs"></a>Télécharger des objets blob

Pour télécharger des objets BLOB, commencez par récupérer une référence d’objet BLOB, puis appelez la méthode `DownloadToStream`. L’exemple suivant utilise la méthode `DownloadToStream` pour transférer le contenu de l’objet BLOB vers un objet de flux que vous pouvez ensuite conserver dans un fichier local.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

Vous pouvez également utiliser la méthode `DownloadToStream` pour télécharger le contenu d’un objet blob sous la forme d’une chaîne de texte.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a>Suppression d’objets blob

Pour supprimer un objet BLOB, commencez par obtenir une référence d’objet BLOB, puis appelez la méthode `Delete` dessus.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a>Création d’une liste d’objets blob dans des pages de manière asynchrone

Si vous répertoriez un grand nombre d’objets blob ou que vous souhaitez contrôler le nombre de résultats renvoyés lors d’une opération de création de liste, vous pouvez répertorier les objets blob dans des pages de résultats. Cet exemple montre comment renvoyer les résultats dans des pages de manière asynchrone afin que l’exécution ne soit pas bloquée lorsqu’un ensemble volumineux de résultats est attendu.

Cet exemple montre une liste d’objets BLOB plats, mais vous pouvez également effectuer une liste hiérarchique en définissant le paramètre `useFlatBlobListing` de la méthode `ListBlobsSegmentedAsync` sur `false`.

L’exemple définit une méthode asynchrone à l’aide d’un bloc `async`. Le mot clé ``let!`` interrompt l’exécution de l’exemple de méthode jusqu’à ce que la tâche de listage se termine.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

Nous pouvons maintenant utiliser cette routine asynchrone comme suit. Tout d’abord, vous téléchargez des données factices (à l’aide du fichier local créé précédemment dans ce didacticiel).

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

À présent, appelez la routine. Vous utilisez `Async.RunSynchronously` pour forcer l’exécution de l’opération asynchrone.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a>Écriture dans un objet blob d’ajout

Il est optimisé pour les opérations d’ajout, telles que la journalisation. Comme un objet blob de blocs, un objet blob d’ajout est composé de blocs. Mais lorsqu’il est ajouté à un objet blob d’ajout, un nouveau bloc l’est toujours à la fin. Vous ne pouvez pas mettre à jour ou supprimer un bloc dans un objet blob d’ajout. Les ID de bloc dans un objet blob d’ajout ne sont pas visibles, comme pour un objet blob de blocs.

Chaque bloc d’un objet blob d’ajout peut avoir une taille différente (jusqu’à 4 Mo), et un objet blob d’ajout peut contenir au maximum 50 000 blocs. La taille maximale d’un objet blob d’ajout est donc légèrement supérieure à 195 Go (4 Mo x 50 000 blocs).

L’exemple suivant crée un nouvel objet blob d’ajout et y ajoute des données, en simulant une opération de journalisation simple.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

Pour plus d’informations sur les différences entre les trois types d’objets blob, consultez la page [Présentation des objets blob de blocs, des objets blob d’ajout et des objets blob de pages](https://msdn.microsoft.com/library/azure/ee691964.aspx) .

## <a name="concurrent-access"></a>Accès simultané

Pour activer la prise en charge de l’accès simultané à un objet blob par plusieurs clients ou instances de processus, vous pouvez utiliser **ETags** ou **leases**.

- **Etag** : permet de détecter la modification de l’objet blob ou du conteneur par un autre processus

- **Lease** : permet d’obtenir l’accès exclusif, renouvelable, en écriture ou en suppression à un objet blob pour une période donnée

Pour plus d’informations, consultez [gestion de l’accès concurrentiel dans stockage Microsoft Azure](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).

## <a name="naming-containers"></a>Nommer des conteneurs

Chaque objet blob du stockage Azure doit résider dans un conteneur. Le conteneur fait partie du nom d'objet blob. Par exemple, `mydata` est le nom du conteneur dans ces exemples d’URI d’objet blob :

- `https://storagesample.blob.core.windows.net/mydata/blob1.txt`
- `https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg`

Un conteneur doit posséder un nom DNS valide, conforme aux règles de nommage suivantes :

1. Les noms de conteneur doivent commencer par une lettre ou un chiffre, et peuvent comporter uniquement des lettres, des chiffres et des tirets (-).
1. Chaque tiret (-) doit être immédiatement précédé et suivi d’une lettre ou d’un chiffre ; les tirets consécutifs sont interdits.
1. Toutes les lettres du conteneur doivent être minuscules.
1. Les noms de conteneurs doivent comporter entre 3 et 63 caractères.

Notez que le nom d'un conteneur doit toujours être en minuscules. Si vous incluez une majuscule dans un nom de conteneur ou si vous ne respectez pas les règles d'affectation de noms, vous pouvez recevoir une erreur 400 (demande incorrecte).

## <a name="managing-security-for-blobs"></a>Gestion de la sécurité pour les objets blob

Par défaut, Azure Storage préserve la sécurité de vos données en limitant l’accès au propriétaire du compte, qui est en possession des clés d’accès au compte. Lorsque vous avez besoin de partager des données d’objets blob de votre compte de stockage, il est important de le faire sans compromettre la sécurité de vos clés d’accès au compte. En outre, vous pouvez chiffrer les données d’objets blob pour vous assurer qu’elles sont sécurisées lors de leur transfert et dans Azure Storage.

### <a name="controlling-access-to-blob-data"></a>Contrôle de l’accès aux données d’objets blob

Par défaut, les données d’objets blob de votre compte de stockage sont accessibles uniquement par le propriétaire du compte de stockage. L’authentification des demandes vis-à-vis du stockage d’objets blob requiert la clé d’accès par défaut. Toutefois, vous souhaiterez peut-être mettre certaines données BLOB à la disposition d’autres utilisateurs.

### <a name="encrypting-blob-data"></a>Chiffrement des données d’objets blob

Le stockage Azure prend en charge le chiffrement des données BLOB à la fois sur le client et sur le serveur.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous connaissez les bases du stockage d’objets blob, consultez les liens suivants pour en savoir plus.

### <a name="tools"></a>Outils

- [ F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)\
Fournisseur F# de type qui peut être utilisé pour explorer des ressources de stockage Azure d’objets BLOB, de table et de file d’attente et pour appliquer facilement des opérations CRUD sur ceux-ci.

- [FSharp. Azure. Storage](https://github.com/fsprojects/FSharp.Azure.Storage)\
F# API pour l’utilisation du service de stockage de table Microsoft Azure

- [Explorateur stockage Microsoft Azure (Mase)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)\
Une application autonome et gratuite de Microsoft qui vous permet de travailler visuellement avec les données de stockage Azure sur Windows, OS X et Linux.

### <a name="blob-storage-reference"></a>Documentation de référence sur le stockage d’objets blob

- [API de stockage Azure pour .NET](/dotnet/api/overview/azure/storage)
- [Azure Storage Services REST API Reference](/rest/api/storageservices/) (Informations de référence de l’API REST des services Stockage Azure)

### <a name="related-guides"></a>Guides connexes

- [Exemples de stockage d’objets blob Azure pour .NET](https://docs.microsoft.com/samples/azure-samples/storage-blob-dotnet-getting-started/storage-blob-dotnet-getting-started/)
- [Bien démarrer avec AzCopy](/azure/storage/common/storage-use-azcopy-v10)
- [Configuration des chaînes de connexion du Stockage Azure](/azure/storage/common/storage-configure-connection-string)
- [Blog de l'équipe Azure Storage](https://docs.microsoft.com/archive/blogs/windowsazurestorage/)
- [Démarrage rapide : utiliser .NET pour créer un objet BLOB dans le stockage d’objets](/azure/storage/blobs/storage-quickstart-blobs-dotnet)
