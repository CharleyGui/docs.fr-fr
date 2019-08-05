---
title: État et données dans les applications Docker
description: Gestion des états et des données dans les applications Docker. Les instances de microservice sont extensibles, mais PAS LES DONNÉES. Comment prendre cela en charge à l’aide des microservices ?
ms.date: 09/20/2018
ms.openlocfilehash: 9d7b0ff0e73267c6b80be2f1c956c3b4eae140e2
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68673126"
---
# <a name="state-and-data-in-docker-applications"></a>État et données dans les applications Docker

Dans la plupart des cas, vous pouvez considérer qu’un conteneur est une instance d’un processus. Un processus ne conserve pas un état persistant. Si un conteneur peut écrire dans son stockage local, supposer qu’une instance sera présente indéfiniment revient à supposer qu’un seul emplacement en mémoire pourra perdurer. Vous devez partir de l’hypothèse que les images conteneur, par exemple les processus, ont plusieurs instances ou qu’elles vont finir par être tuées. Si elles sont managées à l’aide d’un orchestrateur de conteneurs, vous devez supposer qu’elles peuvent être déplacés d’un nœud (ou d’une machine virtuelle) vers un autre.

Les solutions suivantes sont utilisées pour gérer les données persistantes dans les applications Docker :

À partir de l’hôte Docker, sous forme de [volumes Docker](https://docs.docker.com/engine/admin/volumes/) :

- Les **volumes** sont stockés dans une zone du système de fichiers hôte managée par Docker.

- Les **montages de liaison** peuvent être mappés à n’importe quel dossier du système de fichiers hôte. L’accès ne peut donc pas être contrôlé à partir du processus Docker, ce qui peut poser un risque pour la sécurité, car un conteneur peut accéder aux dossiers sensibles du système d’exploitation.

- Les **montages tmpfs** sont semblables à des dossiers virtuels qui existent uniquement dans la mémoire de l’hôte et qui ne sont jamais écrits dans le système de fichiers.

À partir du stockage distant :

- Le service [Stockage Azure](https://azure.microsoft.com/documentation/services/storage/), qui fournit un stockage géographiquement distribuable, offrant une bonne solution de persistance à long terme pour les conteneurs.

- Des bases de données relationnelles distantes, comme [Azure SQL Database](https://azure.microsoft.com/services/sql-database/), ou des bases de données NoSQL, comme [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction), ou des services de cache, comme [Redis](https://redis.io/).

À partir du conteneur Docker :

> Docker fournit une fonctionnalité appelée *système de fichiers par superposition*. Elle implémente une tâche de copie sur écriture qui stocke les informations mises à jour dans le système de fichiers racine du conteneur. Ces informations s’ajoutent à l’image d’origine sur laquelle le conteneur est basé. Si le conteneur est supprimé du système, ces modifications sont perdues. Ainsi, bien qu’il soit possible d’enregistrer l’état d’un conteneur dans son stockage local, la conception d’un système selon cette solution est en conflit avec le principe de conception des conteneurs, lesquels sont par défaut sans état.
>
> Toutefois, les volumes Docker présentés constituent désormais le mode privilégié de gestion des données Docker locales. Pour plus d’informations sur le stockage dans les conteneurs, consultez [Pilotes de stockage Docker](https://docs.docker.com/storage/storagedriver/select-storage-driver/) et [À propos des pilotes de stockage](https://docs.docker.com/storage/storagedriver/).

Ces options sont détaillées ci-dessous :

Les **volumes** sont des répertoires mappés du système d’exploitation hôte à des répertoires situés dans les conteneurs. Quand le code du conteneur a accès au répertoire, cet accès se fait en réalité à un répertoire sur le système d’exploitation hôte. Ce répertoire n’est pas lié à la durée de vie du conteneur, il est managé par Docker et isolé de la fonctionnalité principale de la machine hôte. Ainsi, les volumes de données sont conçus pour rendre des données persistantes indépendamment de la durée de vie du conteneur. Si vous supprimez un conteneur ou une image de l’hôte Docker, les données rendues persistantes dans le volume de données ne sont pas supprimées.

Les volumes peuvent être nommés ou anonymes (par défaut). Les volumes nommés correspondent à l’évolution des **conteneurs de volumes de données**. Ils facilitent le partage de données entre les conteneurs. Les volumes prennent également en charge les pilotes de volume, qui permettent entre autres de stocker des données sur des hôtes distants.

Les **montages de liaison** existent depuis longtemps. Ils permettent de mapper des dossiers à un point de montage d’un conteneur. Les montages de liaison ont plus de limitations que les volumes et présentent certains problèmes de sécurité importants. Les volumes sont donc l’option recommandée.

Les **montages tmpfs** sont essentiellement des dossiers virtuels qui résident uniquement dans la mémoire de l’hôte et qui ne sont jamais écrits dans le système de fichiers. Ils sont rapides et sécurisés, mais ils consomment de la mémoire et sont conçus uniquement pour des données non persistantes.

Comme le montre la figure 4-5, les volumes Docker standard peuvent être stockés en dehors des conteneurs eux-mêmes, mais dans les limites physiques du serveur ou de la machine virtuelle hôte. Toutefois, les conteneurs Docker ne peuvent pas accéder à un volume d’un serveur hôte ou d’une machine virtuelle depuis un autre serveur hôte ou une autre machine virtuelle. En d’autres termes, avec ces volumes, il n’est pas possible de gérer les données partagées entre des conteneurs qui s’exécutent sur des hôtes Docker distincts. Toutefois, cela est possible avec un pilote de volume qui prend en charge les hôtes distants.

![Les volumes peuvent être partagés entre les conteneurs, mais uniquement sur le même hôte, sauf si vous utilisez un pilote distant qui prend en charge les hôtes distants. ](./media/image5.png)

**Figure 4-5**. Volumes et sources de données externes pour applications conteneurisées

De plus, quand des conteneurs Docker sont managés par un orchestrateur, ils peuvent être « déplacés » entre les hôtes, en fonction des optimisations effectuées par le cluster. Il n’est donc pas recommandé d’utiliser des volumes de données pour les données métier. Toutefois, ils constituent un bon mécanisme pour travailler avec des fichiers de trace, des fichiers temporels ou des fichiers similaires qui n’ont pas d’impact sur la cohérence des données métier.

Des **sources de données distantes et des outils de mise en cache**, comme Azure SQL Database, Azure Cosmos DB ou un cache à distance comme Redis, peuvent être utilisés dans des applications en conteneur de la même façon qu’ils sont utilisés dans des développements sans conteneurs. Il s’agit d’un moyen éprouvé pour stocker des données d’application métier.

**Stockage Azure** Les données métier doivent généralement être placées dans des ressources ou des bases de données externes, comme le service Stockage Azure. Concrètement, Stockage Azure fournit les services suivants dans le cloud :

- Stockage Blob stocke les données des objets non structurés. Un objet blob peut être n’importe quel type de données texte ou binaires, comme des fichiers de document ou multimédias (fichiers image, audio et vidéo). Stockage Blob est également appelé Stockage d’objets.

- Stockage Fichier offre un stockage partagé pour les applications héritées avec le protocole SMB standard. Les machines virtuelles et les services cloud Azure peuvent partager des données de fichiers entre des composants d’application via des partages montés. Les applications locales peuvent accéder aux données des fichiers d’un partage via l’API REST du service Fichier.

- Stockage Table stocke les jeux de données structurés. Stockage Table est un magasin de données clé-attribut NoSQL, qui permet le développement rapide et un accès rapide à de grandes quantités de données.

**Bases de données relationnelles et bases de données NoSQL.** De nombreux choix sont disponibles pour les bases de données externes, qui vont des bases de données relationnelles, comme SQL Server, PostgreSQL ou Oracle, aux bases de données NoSQL, comme Azure Cosmos DB, MongoDB, etc. Ces bases de données ne sont pas présentées dans ce guide, car il s’agit d’un tout autre sujet.

>[!div class="step-by-step"]
>[Précédent](containerize-monolithic-applications.md)
>[Suivant](service-oriented-architecture.md)
