---
title: Adressabilité des microservices et registre des services
description: Découvrez le rôle des registres d’images conteneur dans l’architecture des microservices.
ms.date: 01/13/2021
ms.openlocfilehash: 363a307d44d30125563863bbe3ebeb5f5b9ad2bc
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188411"
---
# <a name="microservices-addressability-and-the-service-registry"></a>Adressabilité des microservices et registre des services

Chaque microservice a un nom unique (URL) qui est utilisé pour résoudre son emplacement. Votre microservice doit être adressable partout où il est exécuté. Si vous devez commencer à réfléchir pour savoir quel ordinateur exécute quel microservice, les choses peuvent devenir rapidement ingérables. De la même façon que le DNS résout une URL vers un ordinateur spécifique, votre microservice doit avoir un nom unique de sorte que son emplacement actuel puisse être découvert. Les microservices nécessitent des noms adressables qui les rendent indépendants de l’infrastructure sur laquelle ils s’exécutent. Cette approche implique qu’il y a une interaction entre le mode de déploiement de votre service et la façon dont il est découvert, car il doit exister un [Registre de service](https://microservices.io/patterns/service-registry.html). De la même façon, quand un ordinateur connaît une défaillance, le registre des services doit être en mesure d’indiquer où le service s’exécute désormais.

Le [modèle de registre des services](https://microservices.io/patterns/service-registry.html) est une partie essentielle dans la découverte des services. Le registre est une base de données qui contient les emplacements réseau des instances de service. Un registre des services doit être hautement disponible et à jour. Les clients peuvent mettre en cache les emplacements réseau obtenus auprès du registre des services. Cependant, ces informations finissent par être obsolètes et les clients ne peuvent alors plus découvrir les instances des services. Par conséquent, un registre de service est constitué d’un cluster de serveurs qui utilisent un protocole de réplication pour maintenir la cohérence.

Dans certains environnements de déploiement de microservices (appelés clusters, pour être couverts dans une section ultérieure), la découverte du service est intégrée. Par exemple, un environnement Azure Container Service avec Kubernetes (AKS) peut prendre en charge l’inscription et la désinscription des instances de service. Il exécute également un proxy sur chaque hôte de cluster, qui joue le rôle de routeur de découverte côté serveur.

## <a name="additional-resources"></a>Ressources supplémentaires

- **Chris Richardson. Modèle : Registre de service** \
  <https://microservices.io/patterns/service-registry.html>

- **Auth0. Registre de service** \
  <https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/>

- **Gabriel Schenker. Détection du service** \
  <https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/>

>[!div class="step-by-step"]
>[Précédent](maintain-microservice-apis.md) 
> [Suivant](microservice-based-composite-ui-shape-layout.md)
