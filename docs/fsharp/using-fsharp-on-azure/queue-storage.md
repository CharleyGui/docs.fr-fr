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
# <a name="get-started-with-azure-queue-storage-using-f"></a>Prise en main du stockage de files d’attente Azure à l’aide de F\#

Le stockage de files d’attente Azure fournit une messagerie Cloud entre les composants d’application. Dans la conception d’applications à des fins de mise à l’échelle, les composants d’application sont souvent découplés, afin qu’ils puissent être mis à l’échelle indépendamment. Le stockage file d’attente offre une messagerie asynchrone pour la communication entre les composants de l’application, qu’ils s’exécutent dans le Cloud, sur le bureau, sur un serveur local ou sur un appareil mobile. Le stockage de files d’attente prend également en charge la gestion des tâches asynchrones et la création de flux de travail.

### <a name="about-this-tutorial"></a>À propos de ce didacticiel

Ce didacticiel montre comment écrire F# du code pour certaines tâches courantes à l’aide du stockage de files d’attente Azure. Les tâches couvertes incluent la création et la suppression de files d’attente, ainsi que l’ajout, la lecture et la suppression de messages de file d’attente.

Pour obtenir une vue d’ensemble conceptuelle du stockage de files d’attente, consultez [le guide .net pour le stockage de files d’attente](/azure/storage/storage-dotnet-how-to-use-queues).

## <a name="prerequisites"></a>Prérequis

Pour utiliser ce guide, vous devez d’abord [créer un compte de stockage Azure](/azure/storage/storage-create-storage-account).
Vous aurez également besoin de votre clé d’accès de stockage pour ce compte.

## <a name="create-an-f-script-and-start-f-interactive"></a>Créer un F# script et démarrer F# interactive

Les exemples de cet article peuvent être utilisés dans une F# application ou un F# script. Pour créer un F# script, créez un fichier avec l' `.fsx` extension, par exemple `queues.fsx`, dans votre F# environnement de développement.

Ensuite, utilisez un [Gestionnaire de package](package-management.md) comme [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) pour installer le `WindowsAzure.Storage` package et la `WindowsAzure.Storage.dll` référence dans votre script à `#r` l’aide d’une directive.

### <a name="add-namespace-declarations"></a>Ajouter des déclarations d’espace de noms

Ajoutez les instructions `open` suivantes au début `queues.fsx` du fichier:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>Obtient votre chaîne de connexion

Vous aurez besoin d’une chaîne de connexion de stockage Azure pour ce didacticiel. Pour plus d’informations sur les chaînes de connexion, consultez [configurer des chaînes de connexion de stockage](/azure/storage/storage-configure-connection-string).

Pour le didacticiel, vous allez entrer votre chaîne de connexion dans votre script, comme suit:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

Toutefois, cela n’est **pas recommandé** pour les projets réels. Votre clé de compte de stockage est similaire au mot de passe racine de votre compte de stockage. Veillez toujours à protéger votre clé de compte de stockage. Évitez de la distribuer à d’autres utilisateurs, de la coder en dur ou de l’enregistrer dans un fichier texte brut accessible à d’autres utilisateurs. Vous pouvez régénérer votre clé à l’aide du portail Azure si vous pensez qu’elle a peut-être été compromise.

Pour les applications réelles, la meilleure façon de gérer votre chaîne de connexion de stockage se trouve dans un fichier de configuration. Pour extraire la chaîne de connexion d’un fichier de configuration, procédez comme suit:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

L’utilisation d’Azure Configuration Manager est facultative. Vous pouvez également utiliser une API telle que le type de `ConfigurationManager` .NET Framework.

### <a name="parse-the-connection-string"></a>Analyser la chaîne de connexion

Pour analyser la chaîne de connexion, utilisez:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

Cela renverra un `CloudStorageAccount`.

### <a name="create-the-queue-service-client"></a>Créer le client service de File d’attente

La `CloudQueueClient` classe vous permet de récupérer des files d’attente stockées dans le stockage de files d’attente. Voici un moyen de créer le client de service:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

Vous êtes maintenant prêt à écrire du code qui lit et écrit des données dans le stockage de files d’attente.

## <a name="create-a-queue"></a>Créer une file d’attente

Cet exemple montre comment créer une file d’attente si elle n’existe pas déjà:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>Insérer un message dans une file d’attente

Pour insérer un message dans une file d’attente existante, commencez par `CloudQueueMessage`créer un nouveau. Ensuite, appelez la `AddMessage` méthode. Un `CloudQueueMessage` peut être créé à partir d’une chaîne (au format UTF-8) ou `byte` d’un tableau, comme suit:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>Lire le message suivant

Vous pouvez lire le message au début de la file d’attente, sans le supprimer de la file d’attente, en `PeekMessage` appelant la méthode.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>Obtenir le message suivant à traiter

Vous pouvez récupérer le message au début de la file d’attente à des fins de `GetMessage` traitement en appelant la méthode.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

Vous indiquez par la suite le traitement réussi du message `DeleteMessage`à l’aide de.

## <a name="change-the-contents-of-a-queued-message"></a>Modifier le contenu d’un message en file d’attente

Vous pouvez modifier le contenu d’un message récupéré sur place dans la file d’attente. Si le message représente une tâche de travail, vous pouvez utiliser cette fonctionnalité pour mettre à jour l’état de la tâche de travail. Le code suivant met à jour le message de file d’attente avec le nouveau contenu et définit le délai d’expiration de la visibilité pour étendre une autre 60 secondes. Cela permet d’enregistrer l’état du travail associé au message et de donner au client une autre minute pour continuer à travailler sur le message. Vous pouvez utiliser cette technique pour effectuer le suivi des flux de travail à plusieurs étapes sur les messages de la file d’attente, sans devoir recommencer depuis le début si une étape de traitement échoue en raison d’une défaillance matérielle ou logicielle. En règle générale, vous conservez également un nombre de nouvelles tentatives, et si le message est retenté plus d’un certain nombre de fois, vous le supprimez. Cela protège contre un message qui déclenche une erreur d’application à chaque fois qu’il est traité.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>Retirer le message suivant de la file d’attente

Votre code met en file d’attente un message de la file d’attente en deux étapes. Lorsque vous appelez `GetMessage`, vous recevez le message suivant dans une file d’attente. Un message retourné par `GetMessage` devient invisible à tout autre code lisant les messages de cette file d’attente. Par défaut, ce message reste invisible pendant 30 secondes. Pour terminer la suppression du message de la file d’attente, vous `DeleteMessage`devez également appeler. Ce processus de suppression d’un message en deux étapes garantit que, si votre code ne parvient pas à traiter un message en raison d’une défaillance matérielle ou logicielle, une autre instance de votre code peut obtenir le même message et réessayer. Votre code appelle `DeleteMessage` juste après le traitement du message.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>Utiliser des flux de travail asynchrones avec des API de stockage de files d’attente courantes

Cet exemple montre comment utiliser un flux de travail asynchrone avec les API de stockage de files d’attente courantes.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>Options supplémentaires pour la suppression de la mise en file d’attente des messages

Il existe deux façons de personnaliser la récupération des messages à partir d’une file d’attente.
Tout d’abord, vous pouvez obtenir un lot de messages (jusqu’à 32). Deuxièmement, vous pouvez définir un délai d’invisibilité plus long ou plus faible, ce qui permet de traiter votre code plus ou moins rapidement pour traiter complètement chaque message. L’exemple de code suivant `GetMessages` utilise pour recevoir 20 messages dans un appel, puis traite chaque message. Il définit également le délai d’expiration de l’invisibilité sur cinq minutes pour chaque message. Notez que les 5 minutes commencent pour tous les messages en même temps. par conséquent, après 5 minutes écoulées depuis l' `GetMessages`appel à, tous les messages qui n’ont pas été supprimés sont à nouveau visibles.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>Obtient la longueur de la file d’attente

Vous pouvez obtenir une estimation du nombre de messages dans une file d’attente. La `FetchAttributes` méthode demande à l’service de file d’attente de récupérer les attributs de la file d’attente, y compris le nombre de messages. La `ApproximateMessageCount` propriété retourne la dernière valeur extraite par `FetchAttributes` la méthode, sans appeler l’service de file d’attente.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>Supprimer une file d’attente

Pour supprimer une file d’attente et tous les messages qu’elle contient, `Delete` appelez la méthode sur l’objet file d’attente.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez appris les bases du stockage de files d’attente, suivez ces liens pour en savoir plus sur les tâches de stockage plus complexes.

- [API de stockage Azure pour .NET](/dotnet/api/overview/azure/storage)
- [Fournisseur de type de stockage Azure](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Blog de l’équipe stockage Azure](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Configurer des chaînes de connexion de stockage Azure](/azure/storage/common/storage-configure-connection-string)
- [Informations de référence sur l’API REST des services de stockage Azure](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
