---
title: Bien démarrer avec le stockage Table Azure en F#
description: Stockez des données structurées dans le Cloud à l’aide du stockage table Azure ou Azure Cosmos DB.
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: 6833e2264f7543f50b94892b6980140e4bf1cdd1
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424607"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a>Prise en main du stockage table Azure et du Azure Cosmos DB API Table à l’aide de F\#

Le stockage table Azure est un service qui stocke des données NoSQL structurées dans le Cloud. Le stockage table est un magasin de clés/attributs avec une conception sans schéma. Étant donné que le stockage de tables est sans schéma, il est facile d’adapter vos données à mesure que les besoins de votre application évoluent. L’accès aux données est rapide et économique pour tous les types d’applications. Le stockage de table est généralement beaucoup plus économique que le SQL traditionnel pour des volumes de données similaires.

Vous pouvez utiliser le stockage de tables pour stocker des jeux de données flexibles, tels que des données utilisateur pour des applications Web, des carnets d’adresses, des informations sur les appareils et tout autre type de métadonnées requis par votre service. Vous pouvez stocker n’importe quel nombre d’entités dans une table et un compte de stockage peut contenir un nombre illimité de tables, jusqu’à la limite de capacité du compte de stockage.

Azure Cosmos DB fournit la API Table pour les applications écrites pour le stockage de tables Azure et qui nécessitent des fonctionnalités Premium telles que :

- Distribution mondiale clé en main.
- Débit dédié dans le monde entier.
- Latences à un chiffre en millisecondes au 99e centile.
- Haute disponibilité garantie.
- Indexation secondaire automatique.

Les applications écrites pour le stockage de tables Azure peuvent migrer vers Azure Cosmos DB à l’aide de la API Table sans aucune modification de code et tirer parti des fonctionnalités Premium. Le API Table possède des kits de développement logiciel (SDK) clients disponibles pour .NET, Java, Python et node. js.

Pour plus d’informations, consultez [Introduction à Azure Cosmos DB API table](https://docs.microsoft.com/azure/cosmos-db/table-introduction).

## <a name="about-this-tutorial"></a>À propos de ce didacticiel

Ce didacticiel montre comment écrire F# du code pour effectuer des tâches courantes à l’aide du stockage table Azure ou de la API table Azure Cosmos dB, notamment la création et la suppression d’une table et l’insertion, la mise à jour, la suppression et l’interrogation de données de table.

## <a name="prerequisites"></a>Configuration requise

Pour utiliser ce guide, vous devez d’abord [créer un compte de stockage Azure ou un](/azure/storage/storage-create-storage-account) compte de [Azure Cosmos DB](https://azure.microsoft.com/try/cosmosdb/).

## <a name="create-an-f-script-and-start-f-interactive"></a>Créer un F# script et démarrer F# interactive

Les exemples de cet article peuvent être utilisés dans une F# application ou un F# script. Pour créer un F# script, créez un fichier avec l’extension `.fsx`, par exemple `tables.fsx`, dans votre F# environnement de développement.

Ensuite, utilisez un [Gestionnaire de package](package-management.md) comme [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) pour installer le package `WindowsAzure.Storage` et référencez `WindowsAzure.Storage.dll` dans votre script à l’aide d’une directive `#r`. Réexécutez-le pour `Microsoft.WindowsAzure.ConfigurationManager` afin d’obtenir l’espace de noms Microsoft. Azure.

### <a name="add-namespace-declarations"></a>Ajouter des déclarations d’espace de noms

Ajoutez les instructions `open` suivantes en haut du fichier `tables.fsx` :

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a>Récupérer votre chaîne de connexion de stockage Azure

Si vous vous connectez à un service de table de stockage Azure, vous aurez besoin de votre chaîne de connexion pour ce didacticiel. Vous pouvez copier votre chaîne de connexion à partir du Portail Azure. Pour plus d’informations sur les chaînes de connexion, consultez [configurer des chaînes de connexion de stockage](/azure/storage/storage-configure-connection-string).

### <a name="get-your-azure-cosmos-db-connection-string"></a>Obtient votre chaîne de connexion Azure Cosmos DB

Si vous vous connectez à Azure Cosmos DB, vous aurez besoin de votre chaîne de connexion pour ce didacticiel. Vous pouvez copier votre chaîne de connexion à partir du Portail Azure. Dans le Portail Azure, dans votre compte Cosmos DB, accédez à **paramètres** > **chaîne de connexion**, puis cliquez sur le bouton **copier** pour copier votre chaîne de connexion principale.

Pour le didacticiel, entrez votre chaîne de connexion dans votre script, comme dans l’exemple suivant :

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

Toutefois, cela n’est **pas recommandé** pour les projets réels. Votre clé de compte de stockage est similaire au mot de passe racine de votre compte de stockage. Veillez toujours à protéger votre clé de compte de stockage. Évitez de la distribuer à d’autres utilisateurs, de la coder en dur ou de l’enregistrer dans un fichier texte brut accessible à d’autres utilisateurs. Vous pouvez régénérer votre clé à l’aide du portail Azure si vous pensez qu’elle a peut-être été compromise.

Pour les applications réelles, la meilleure façon de gérer votre chaîne de connexion de stockage se trouve dans un fichier de configuration. Pour extraire la chaîne de connexion d’un fichier de configuration, procédez comme suit :

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

L’utilisation d’Azure Configuration Manager est facultative. Vous pouvez également utiliser une API telle que le type `ConfigurationManager` de .NET Framework.

### <a name="parse-the-connection-string"></a>Analyser la chaîne de connexion

Pour analyser la chaîne de connexion, utilisez :

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

Cela retourne un `CloudStorageAccount`.

### <a name="create-the-table-service-client"></a>Créer le client du service de table

La classe `CloudTableClient` vous permet de récupérer des tables et des entités dans le stockage table. Voici un moyen de créer le client de service :

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

Vous êtes maintenant prêt à écrire du code qui lit et écrit des données dans le stockage de table.

### <a name="create-a-table"></a>Créer une table

Cet exemple montre comment créer une table si elle n’existe pas déjà :

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a>Ajouter une entité à une table

Une entité doit avoir un type qui hérite de `TableEntity`. Vous pouvez étendre `TableEntity` comme vous le souhaitez, mais votre type *doit* avoir un constructeur sans paramètre. Seules les propriétés qui ont à la fois `get` et `set` sont stockées dans votre table Azure.

La clé de partition et de ligne d’une entité identifie de façon unique l’entité dans la table. Les entités avec la même clé de partition peuvent être interrogées plus rapidement que celles avec des clés de partition différentes, mais l’utilisation de clés de partition diverses permet une plus grande évolutivité des opérations parallèles.

Voici un exemple de `Customer` qui utilise la `lastName` comme clé de partition et la `firstName` comme clé de ligne.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

À présent, ajoutez `Customer` à la table. Pour ce faire, créez un `TableOperation` qui s’exécute sur la table. Dans ce cas, vous créez une opération `Insert`.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a>Insérer un lot d’entités

Vous pouvez insérer un lot d’entités dans une table à l’aide d’une seule opération d’écriture. Les opérations de traitement par lots vous permettent de combiner des opérations en une seule exécution, mais elles présentent des restrictions :

- Vous pouvez effectuer des mises à jour, des suppressions et des insertions dans la même opération de traitement par lot.
- Une opération par lot peut inclure jusqu’à 100 entités.
- Toutes les entités d’une opération de traitement par lot doivent avoir la même clé de partition.
- Bien qu’il soit possible d’exécuter une requête dans le cadre d’une opération de traitement par lot, il doit s’agir de la seule opération dans le lot.

Voici du code qui combine deux insertions dans une opération de traitement par lot :

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a>Récupérer toutes les entités d’une partition

Pour interroger une table pour toutes les entités d’une partition, utilisez un objet `TableQuery`. Ici, vous filtrez les entités où « Smith » est la clé de partition.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

Vous allez maintenant imprimer les résultats :

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]

### <a name="retrieve-a-range-of-entities-in-a-partition"></a>Récupérer une plage d’entités dans une partition

Si vous ne souhaitez pas interroger toutes les entités d’une partition, vous pouvez spécifier une plage en combinant le filtre de clé de partition avec un filtre de clé de ligne. Ici, vous utilisez deux filtres pour obtenir toutes les entités dans la partition « Smith » où la clé de ligne (prénom) commence par une lettre antérieure à « M » dans l’alphabet.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

Vous allez maintenant imprimer les résultats :

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a>Récupérer une seule entité

Vous pouvez écrire une requête pour récupérer une seule entité spécifique. Ici, vous utilisez un `TableOperation` pour spécifier le client « Ben Smith ». Au lieu d’une collection, vous récupérez une `Customer`. La méthode la plus rapide pour récupérer une seule entité à partir du service de table consiste à spécifier à la fois la clé de partition et la clé de ligne dans une requête.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

Vous allez maintenant imprimer les résultats :

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]

### <a name="replace-an-entity"></a>Remplacer une entité

Pour mettre à jour une entité, récupérez-la à partir du service de table, modifiez l’objet d’entité, puis enregistrez les modifications dans le service de table à l’aide d’une opération `Replace`. Cela entraîne le remplacement complet de l’entité sur le serveur, sauf si l’entité sur le serveur a changé depuis sa récupération, auquel cas l’opération échoue. Cet échec consiste à empêcher votre application de remplacer par inadvertance les modifications à partir d’autres sources.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a>Insérer ou remplacer une entité

Parfois, vous ne savez pas si une entité existe dans la table. Et si c’est le cas, les valeurs actuelles stockées dans celui-ci ne sont plus nécessaires. Vous pouvez utiliser `InsertOrReplace` pour créer l’entité, ou la remplacer si elle existe, quel que soit son état.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a>Interroger un sous-ensemble de propriétés d’entité

Une requête de table peut récupérer uniquement quelques propriétés à partir d’une entité, et non pas toutes. Cette technique, appelée projection, peut améliorer les performances des requêtes, en particulier pour les entités volumineuses. Ici, vous retournez uniquement les adresses de messagerie à l’aide de `DynamicTableEntity` et `EntityResolver`. Notez que la projection n’est pas prise en charge sur l’émulateur de stockage local, de sorte que ce code s’exécute uniquement lorsque vous utilisez un compte sur le service de table.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a>Récupérer des entités dans des pages de manière asynchrone

Si vous lisez un grand nombre d’entités et que vous souhaitez les traiter à mesure qu’elles sont récupérées au lieu d’attendre qu’elles soient retournées, vous pouvez utiliser une requête segmentée. Ici, vous retournez les résultats dans les pages à l’aide d’un flux de travail asynchrone afin que l’exécution ne soit pas bloquée pendant que vous attendez un grand nombre de résultats à retourner.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

Vous exécutez maintenant ce calcul de façon synchrone :

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a>Supprimer une entité

Vous pouvez supprimer une entité après l’avoir récupérée. Comme pour la mise à jour d’une entité, cette opération échoue si l’entité a changé depuis que vous l’avez récupérée.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a>Supprimer une table

Vous pouvez supprimer une table d’un compte de stockage. Une table qui a été supprimée ne peut pas être recréée pendant une période de temps après la suppression.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez appris les principes de base du stockage table, suivez ces liens pour en savoir plus sur les tâches de stockage plus complexes et le Azure Cosmos DB API Table.

- [Présentation de Azure Cosmos DB API Table](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [Référence de la bibliothèque cliente de stockage pour .NET](https://docs.microsoft.com/dotnet/api/overview/azure/storage)
- [Fournisseur de type de stockage Azure](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [Blog de l’équipe stockage Azure](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Configuration de chaînes de connexion](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
