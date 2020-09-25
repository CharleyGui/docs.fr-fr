---
title: Présentation de Docker
description: Architecture des microservices .NET pour les applications .NET en conteneur | Présentation de Docker
ms.date: 08/31/2018
ms.openlocfilehash: 7d4b419f46f32fa4acdeb1ac7d5e0c2b2c199fc5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172402"
---
# <a name="what-is-docker"></a>Présentation de Docker

[Docker](https://www.docker.com/) est un [projet open source](https://github.com/docker/docker) permettant d’automatiser le déploiement d’applications en tant que conteneurs portables et autonomes exécutables sur le cloud ou localement. Docker est également une [entreprise](https://www.docker.com/) qui développe et diffuse cette technologie, en collaboration avec des fournisseurs de services cloud, Linux et Windows, notamment Microsoft.

![Diagramme montrant les emplacements que les conteneurs de l’ancrage peuvent exécuter.](./media/docker-defined/docker-containers-run-anywhere.png)

**Figure 2-2**. L’arrimeur déploie des conteneurs sur toutes les couches du Cloud hybride.

Les conteneurs Docker peuvent s’exécuter n’importe où, en local dans le centre de données client, dans un fournisseur de services externe ou dans le cloud, sur Azure. Les conteneurs d’images Docker peuvent s’exécuter en mode natif sur Linux et Windows. Toutefois, les images Windows peuvent s’exécuter uniquement sur des hôtes Windows et les images Linux peuvent s’exécuter sur des hôtes Linux et des hôtes Windows (à l’aide d’une machine virtuelle Linux Hyper-V, jusqu’à présent), où le terme « hôte » désigne un serveur ou une machine virtuelle.

Les développeurs peuvent utiliser des environnements de développement sur Windows, Linux ou macOS. Sur l’ordinateur de développement, le développeur exécute un hôte Docker sur lequel sont déployées les images Docker, y compris l’application et ses dépendances. Les développeurs qui travaillent sur Linux ou Mac OS utilisent un hôte de station d’accueil qui est basé sur Linux et peuvent créer des images uniquement pour les conteneurs Linux. (Les développeurs qui travaillent sur macOS peuvent modifier le code ou exécuter l’interface de commande de l’ancrer à partir de macOS, mais au moment de la rédaction de cet article, les conteneurs ne s’exécutent pas directement sur macOS.) Les développeurs qui travaillent sur Windows peuvent créer des images pour les conteneurs Linux ou Windows.

Pour héberger des conteneurs dans un environnement de développement et fournir des outils de développement supplémentaires, Docker fournit [Docker Community Edition (CE)](https://www.docker.com/community-edition) pour Windows ou macOS. Ces produits installent la machine virtuelle nécessaire (l’hôte Docker) pour héberger les conteneurs. Docker fournit aussi [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition), conçu pour le développement en entreprise et utilisé par les équipes informatiques qui génèrent, livrent et exécutent des applications métier stratégiques volumineuses en production.

Les [conteneurs Windows](/virtualization/windowscontainers/about/) fonctionnent avec deux types de runtime :

- Les conteneurs Windows Server assurent l’isolation des applications par le biais d’une technologie d’isolation des processus et des espaces de noms. Un conteneur Windows Server partage un noyau avec l’hôte conteneur et avec tous les conteneurs exécutés sur l’hôte.

- Les conteneurs Hyper-V étendent l’isolation fournie par les conteneurs Windows Server en exécutant chaque conteneur sur une machine virtuelle hautement optimisée. Dans cette configuration, le noyau de l’hôte conteneur n’est pas partagé avec les conteneurs Hyper-V, ce qui garantit une meilleure isolation.

Les images de ces deux types de conteneurs sont créées et fonctionnent de la même façon. La différence réside dans la façon dont le conteneur est créé à partir de l’image, l’exécution d’un conteneur Hyper-V nécessite un paramètre supplémentaire. Pour plus d’informations, consultez [Conteneurs Hyper-V](/virtualization/windowscontainers/manage-containers/hyperv-container).

## <a name="comparing-docker-containers-with-virtual-machines"></a>Comparaison entre les conteneurs Docker et les machines virtuelles

La figure 2-3 compare les machines virtuelles et les conteneurs Docker.

| Virtual Machines | Conteneurs Docker |
| -----------------| ------------------|
|![Diagramme montrant la pile matérielle/logicielle d’une machine virtuelle traditionnelle.](./media/docker-defined/virtual-machine-hardware-software.png)|![Diagramme montrant la pile matérielle/logicielle pour les conteneurs de l’ancrage.](./media/docker-defined/docker-container-hardware-software.png)|
|Les machines virtuelles incluent l’application, les bibliothèques ou binaires requis, et un système d’exploitation invité complet. La virtualisation complète nécessite plus de ressources que la mise en conteneur. | Les conteneurs incluent l’application et toutes ses dépendances. Toutefois, ils partagent le noyau du système d’exploitation avec d’autres conteneurs, exécutés en tant que processus isolés dans l’espace utilisateur sur le système d’exploitation hôte. (Ce n’est pas le cas des conteneurs Hyper-V, où chaque conteneur s’exécute sur une machine virtuelle spécifique.) |

**Figure 2-3**. Comparaison entre les machines virtuelles traditionnelles et les conteneurs Docker

Pour les machines virtuelles, il existe trois couches de base dans le serveur hôte, de bas en haut : infrastructure, système d’exploitation hôte et un hyperviseur, et par-dessus chaque machine virtuelle a son propre système d’exploitation et toutes les bibliothèques nécessaires. Pour Docker, le serveur hôte comprend uniquement l’infrastructure et le système d’exploitation, et par-dessus, le moteur de conteneur, qui conserve le conteneur isolé tout en partageant les services de système d’exploitation de base.

Du fait que les conteneurs nécessitent beaucoup moins de ressources (par exemple, ils n’ont pas besoin d’un système d’exploitation complet), leur démarrage est rapide et leur déploiement est simple. Cela vous permet d’avoir une densité plus élevée, ce qui vous permet d’exécuter plus de services sur la même unité matérielle, limitant les coûts.

Comme effet secondaire de l’exécution sur le même noyau, vous obtenez une moins bonne isolation que sur les machines virtuelles.

L’objectif principal d’une image est de garantir un environnement (dépendances) identique entre les différents déploiements. Vous pouvez ainsi la déboguer sur votre machine et la déployer sur une autre machine en étant sûr de garder le même environnement.

Une image conteneur est un moyen d’empaqueter une application ou un service et de les déployer ensuite d’une façon fiable et reproductible. Plus qu’une simple technologie, Docker peut également être vu comme une philosophie et un processus.

Les développeurs qui utilisent Docker ne disent pas : « Cela fonctionne sur ma machine, alors pourquoi pas en production ? » Ils peuvent simplement dire « Cela s’exécute sur Docker », car l’application Docker empaquetée peut être exécutée sur n’importe quel environnement Docker pris en charge et elle s’exécute comme prévu sur toutes les cibles de déploiement (par exemple développement, assurance qualité, intermédiaire et production).

## <a name="a-simple-analogy"></a>Une simple analogie

Peut-être qu’une analogie simple peut aider à bien comprendre le concept de base de Docker.

Retournons dans les années 1950 un instant. Le traitement de texte n’existait pas et les photocopieurs étaient utilisés partout (ou presque).

Imaginez que vous devez émettre rapidement des lots de lettres à envoyer aux clients, avec du papier et des enveloppes, et les livrer physiquement à l’adresse de chaque client (l’e-mail n’existait pas à l’époque).

À un moment donné, vous réalisez que les lettres sont simplement une composition d’un grand ensemble de paragraphes, qui sont organisés en fonction des besoins, selon l’objectif de la lettre, donc vous concevez un système permettant d’émettre des lettres rapidement, afin d’obtenir une augmentation importante.

Le système est simple :

1. Vous commencez avec un jeu de feuilles transparentes contenant chacune un paragraphe.

2. Pour émettre un ensemble de lettres, vous choisissez les feuilles avec les paragraphes dont vous avez besoin, vous les empilez et les alignez afin de pouvoir les lire correctement.

3. Enfin, vous placez l’ensemble dans la photocopieuse, puis appuyez sur démarrer pour produire autant de lettres que nécessaire.

C’est cela l’idée fondamentale de Docker (en version simplifiée).

Dans Docker, chaque couche est un jeu de résultats des modifications qui se produisent dans le système de fichiers après l’exécution d’une commande, par exemple, l’installation d’un programme.

Par conséquent, lorsque vous « regardez » le système de fichiers une fois que la couche a été copiée, vous voyez tous les fichiers, y compris la couche lorsque le programme a été installé.

Vous pouvez considérer une image en tant que disque dur en lecture seule auxiliaire prêt à être installé dans un « ordinateur » où le système d’exploitation est déjà installé.

De même, vous pouvez considérer un conteneur comme « l’ordinateur » avec le disque dur de l’image installé. Le conteneur, tout comme un ordinateur, peut être activé ou désactivé.

>[!div class="step-by-step"]
>[Précédent](index.md) 
> [Suivant](docker-terminology.md)
