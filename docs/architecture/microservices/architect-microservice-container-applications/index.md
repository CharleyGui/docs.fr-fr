---
title: Architecture d’applications conteneur et basées sur des microservices
description: L’architecture d’applications conteneur et basées sur des microservices n’est pas une mince affaire et ne doit pas être prise à la légère. Découvrez les concepts fondamentaux dans ce chapitre.
ms.date: 01/13/2021
ms.openlocfilehash: d87633b6c5073a9098c34c1192bcca1abad00e5c
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189484"
---
# <a name="architecting-container-and-microservice-based-applications"></a>Architecture d’applications conteneur et basées sur des microservices

*Les microservices offrent de nombreux avantages, mais génèrent également de nouveaux défis. Les modèles d’architecture de microservices sont des piliers fondamentaux lors de la création d’une application basée sur des microservices.*

Plus haut dans ce guide, vous avez découvert les concepts de base des conteneurs et de Docker. Ces informations étaient la valeur minimale requise pour la prise en main des conteneurs. Même si les conteneurs sont des activateurs et s’adaptent parfaitement aux microservices, ils ne sont pas obligatoires pour une architecture de microservice et de nombreux concepts architecturaux de cette section d’architecture peuvent également être appliqués sans conteneurs. Cependant, ces recommandations portent sur la confluence des deux du fait de l’importance déjà évoquée des conteneurs.

Les applications d’entreprise peuvent être complexes et sont souvent composées non pas d’un mais de plusieurs services. Dans ce cas, vous devez comprendre d’autres approches architecturales, telles que les microservices et certains modèles de conception Domain-Driven (DDD), ainsi que les concepts d’orchestration de conteneur. Notez que ce chapitre concerne non seulement les microservices présents dans les conteneurs, mais aussi n’importe quelle application en conteneur.

## <a name="container-design-principles"></a>Principes de conception basée sur des conteneurs

Dans le modèle à base de conteneurs, une instance d’image de conteneur représente un processus unique. En définissant une image de conteneur en tant que limite de processus, vous pouvez créer des primitives pouvant servir à mettre à l’échelle le processus ou à le traiter par lots.

Quand vous concevez une image de conteneur, vous constaterez que le fichier Dockerfile contient une définition [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#entrypoint). Cette définition définit le processus dont la durée de vie contrôle la durée de vie du conteneur. Une fois le processus terminé, le cycle de vie du conteneur prend fin. Les conteneurs peuvent représenter des processus de longue durée comme des serveurs web, mais peuvent aussi représentent des processus de courte durée comme les programmes de traitement par lots, qui auraient pu auparavant être implémentés comme des tâches web Azure [WebJobs](https://github.com/Azure/azure-webjobs-sdk/wiki).

Si le processus échoue, le conteneur prend fin et l’orchestrateur prend le contrôle. Si l’orchestrateur a été configuré pour maintenir cinq instances en exécution et qu’une défaillance touche l’une d’elles, l’orchestrateur crée une autre instance de conteneur pour remplacer le processus défaillant. Dans un programme de traitement par lots, le processus démarre avec des paramètres. Quand le processus prend fin, le travail est terminé. Ces considérations s’attachent ultérieurement plus en détails aux orchestrateurs.

Le cas peut se présenter où vous voulez que plusieurs processus s’exécutent dans un même conteneur. Pour ce scénario, comme il ne peut y avoir qu’un seul point d’entrée par conteneur, vous pouvez exécuter un script dans le conteneur qui lance le nombre de programmes voulu. Par exemple, vous pouvez utiliser [Supervisor](http://supervisord.org/) ou un outil similaire pour prendre en charge le lancement de plusieurs processus à l’intérieur d’un même conteneur. Toutefois, même s’il existe des architectures qui contiennent plusieurs processus par conteneur, cette approche n’est pas très courante.

>[!div class="step-by-step"]
>[Précédent](../net-core-net-framework-containers/official-net-docker-images.md) 
> [Suivant](containerize-monolithic-applications.md)
