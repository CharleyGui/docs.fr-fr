---
title: 'Prise en main du stockage de files d’attente Azure à l’aide de F #'
description: Les files d’attente Azure fournissent une messagerie asynchrone fiable entre les composants d’application. La messagerie cloud permet de mettre à l’échelle vos composants d’application indépendamment.
author: sylvanc
ms.date: 09/20/2016
ms.custom: devx-track-fsharp
ms.openlocfilehash: 0ab131647e37985d45073966ffc01b9a7f379e2f
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899293"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a>Prise en main du stockage de files d’attente Azure à l’aide de F\#

Le Stockage File d’attente Azure fournit une messagerie cloud entre les composants d’application. Lors de la conception d'applications pour la mise à l'échelle, des composants d'application sont souvent découplés, de sorte qu'ils peuvent être mis à l'échelle indépendamment. Le Stockage File d’attente offre une messagerie asynchrone pour la communication entre les composants d’application, qu’ils soient exécutés dans le cloud, sur le bureau, sur un serveur local ou sur un appareil mobile. Le stockage de files d’attente prend également en charge la gestion des tâches asynchrones et la création des flux de travail de processus.

### <a name="about-this-tutorial"></a>À propos de ce didacticiel

Ce didacticiel montre comment écrire du code F # pour certaines tâches courantes à l’aide du stockage de files d’attente Azure. Les tâches couvertes incluent la création et la suppression de files d’attente, ainsi que l’ajout, la lecture et la suppression de messages de file d’attente.

Pour obtenir une vue d’ensemble conceptuelle du stockage de files d’attente, consultez [le guide .net pour le stockage de files d’attente](/azure/storage/storage-dotnet-how-to-use-queues).

## <a name="prerequisites"></a>Prérequis

Pour utiliser ce guide, vous devez d’abord [créer un compte de stockage Azure](/azure/storage/storage-create-storage-account).
Vous aurez également besoin de votre clé d’accès de stockage pour ce compte.

## <a name="create-an-f-script-and-start-f-interactive"></a>Créer un script F # et démarrer F# Interactive

Les exemples de cet article peuvent être utilisés dans une application F # ou un script F #. Pour créer un script F #, créez un fichier avec l' `.fsx` extension, par exemple `queues.fsx` , dans votre environnement de développement f #.

Ensuite, utilisez un [Gestionnaire de package](package-management.md) comme [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) pour installer le `WindowsAzure.Storage` package et la référence `WindowsAzure.Storage.dll` dans votre script à l’aide d’une `#r` directive.

### <a name="add-namespace-declarations"></a>Ajout de déclarations d'espaces de noms

Ajoutez les instructions `open` suivantes au début du fichier `queues.fsx` :

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>Obtention de votre chaîne de connexion

Vous aurez besoin d’une chaîne de connexion de stockage Azure pour ce didacticiel. Pour plus d’informations sur les chaînes de connexion, consultez [configurer des chaînes de connexion de stockage](/azure/storage/storage-configure-connection-string).

Pour le didacticiel, vous allez entrer votre chaîne de connexion dans votre script, comme suit :

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

Toutefois, cela n’est **pas recommandé** pour les projets réels. Votre clé de compte de stockage est similaire au mot de passe racine pour votre compte de stockage. Veillez toujours à protéger votre clé de compte de stockage. Évitez de la communiquer à d’autres utilisateurs, de la coder en dur ou de l’enregistrer dans un fichier texte brut accessible à d’autres personnes. Vous pouvez régénérer votre clé à l’aide de la Portail Azure si vous pensez qu’elle a peut-être été compromise.

Pour les applications réelles, la meilleure façon de gérer votre chaîne de connexion de stockage se trouve dans un fichier de configuration. Pour extraire la chaîne de connexion d’un fichier de configuration, procédez comme suit :

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

L’utilisation d’Azure Configuration Manager est facultative. Vous pouvez également utiliser une API telle que le type de .NET Framework `ConfigurationManager` .

### <a name="parse-the-connection-string"></a>Analyse de la chaîne de connexion

Pour analyser la chaîne de connexion, utilisez :

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

Cela renverra un `CloudStorageAccount` .

### <a name="create-the-queue-service-client"></a>Création du client du service Queue

La `CloudQueueClient` classe vous permet de récupérer des files d’attente stockées dans le stockage de files d’attente. Voici un moyen de créer le client du service :

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

Vous êtes maintenant prêt à écrire du code qui lit et écrit des données dans le Queue Storage.

## <a name="create-a-queue"></a>Créer une file d’attente

Cet exemple montre comment créer une file d’attente si elle n’existe pas déjà :

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>Insertion d'un message dans une file d'attente

Pour insérer un message dans une file d’attente existante, commencez par créer un `CloudQueueMessage`. Appelez ensuite la méthode `AddMessage`. Un `CloudQueueMessage` peut être créé à partir d’une chaîne (au format UTF-8) ou d’un `byte` tableau, comme suit :

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>Lecture furtive du message suivant

Vous pouvez lire le message au début de la file d’attente, sans le supprimer de la file d’attente, en appelant la `PeekMessage` méthode.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>Obtenir le message suivant à traiter

Vous pouvez récupérer le message au début de la file d’attente à des fins de traitement en appelant la `GetMessage` méthode.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

Vous indiquez par la suite le traitement réussi du message à l’aide de `DeleteMessage` .

## <a name="change-the-contents-of-a-queued-message"></a>Modification du contenu d'un message en file d'attente

Vous pouvez modifier le contenu d’un message récupéré sur place dans la file d’attente. Si le message représente une tâche, vous pouvez utiliser cette fonctionnalité pour mettre à jour l'état de la tâche. Le code suivant met à jour le message de la file d'attente avec un nouveau contenu et ajoute 60 secondes au délai d'expiration de la visibilité. Cette opération enregistre l'état de la tâche associée au message et accorde une minute supplémentaire au client pour traiter le message. Vous pouvez utiliser cette technique pour suivre des flux de travail à plusieurs étapes sur les messages de file d'attente, sans devoir reprendre du début si une étape du traitement échoue à cause d'une défaillance matérielle ou logicielle. En règle générale, vous conservez également un nombre de nouvelles tentatives, et si le message est retenté plus d’un certain nombre de fois, vous le supprimez. Cela protège du déclenchement d'une erreur d'application par un message chaque fois qu'il est traité.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>Enlèvement du message suivant de la file d'attente

Votre code enlève un message d'une file d'attente en deux étapes. Lorsque vous appelez `GetMessage`, vous obtenez le message suivant dans une file d'attente. Un message renvoyé par `GetMessage` devient invisible par les autres codes lisant les messages de cette file d'attente. Par défaut, ce message reste invisible pendant 30 secondes. Pour finaliser la suppression du message de la file d’attente, vous devez aussi appeler `DeleteMessage`. Ce processus de suppression d'un message en deux étapes garantit que, si votre code ne parvient pas à traiter un message à cause d'une défaillance matérielle ou logicielle, une autre instance de votre code peut obtenir le même message et réessayer. Votre code appelle `DeleteMessage` juste après le traitement du message.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>Utiliser des flux de travail asynchrones avec des API de stockage de files d’attente courantes

Cet exemple montre comment utiliser un flux de travail asynchrone avec les API de stockage de files d’attente courantes.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>Options supplémentaires pour l'extraction de messages

Il existe deux façons de personnaliser la récupération des messages à partir d'une file d'attente.
Premièrement, vous pouvez obtenir un lot de messages (jusqu'à 32). Deuxièmement, vous pouvez définir un délai d'expiration de l'invisibilité plus long ou plus court afin d'accorder à votre code plus ou moins de temps pour traiter complètement chaque message. L’exemple de code suivant utilise `GetMessages` pour recevoir 20 messages dans un appel, puis traite chaque message. Il définit également le délai d'expiration de l'invisibilité sur cinq minutes pour chaque message. Les 5 minutes commencent pour tous les messages en même temps. par conséquent, après 5 minutes écoulées depuis l’appel à `GetMessages` , tous les messages qui n’ont pas été supprimés sont à nouveau visibles.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>Obtention de la longueur de la file d'attente

Vous pouvez obtenir une estimation du nombre de messages dans une file d'attente. La `FetchAttributes` méthode demande à l’service de file d’attente de récupérer les attributs de la file d’attente, y compris le nombre de messages. La `ApproximateMessageCount` propriété retourne la dernière valeur extraite par la `FetchAttributes` méthode, sans appeler l’service de file d’attente.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>Suppression d'une file d'attente

Pour supprimer une file d’attente et tous les messages qu’elle contient, appelez la méthode `Delete` sur l’objet file d’attente.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous connaissez les bases du stockage des files d'attente, consultez les liens suivants pour apprendre à exécuter les tâches de stockage plus complexes.

- [API de stockage Azure pour .NET](/dotnet/api/overview/azure/storage)
- [Fournisseur de type de stockage Azure](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Blog de l'équipe Azure Storage](/archive/blogs/windowsazurestorage/)
- [Configuration des chaînes de connexion du Stockage Azure](/azure/storage/common/storage-configure-connection-string)
- [Référence de l'API REST des services de Stockage Azure](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
