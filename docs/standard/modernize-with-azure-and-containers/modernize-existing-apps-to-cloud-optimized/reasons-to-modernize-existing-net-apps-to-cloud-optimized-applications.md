---
title: Raisons de moderniser des applications .NET existantes aux applications optimisé pour le Cloud
description: Moderniser des applications .NET existantes avec des conteneurs de Cloud Azure et Windows | Raisons de moderniser des applications .NET existantes aux applications optimisé pour le Cloud
ms.date: 04/28/2018
ms.openlocfilehash: 5aa9828f65f76138461c18711fe03bdbe6a70ffd
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758749"
---
# <a name="reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications"></a>Raisons de moderniser des applications .NET existantes aux applications optimisé pour le Cloud

Avec une application optimisé pour le Cloud, vous pouvez rapidement et à plusieurs reprises distribuer des applications fiables à vos clients. Vous bénéficiez essentielle agilité et la fiabilité en différant la complexité opérationnelle de votre application sur la plateforme.

Si vous ne recevez pas vos applications à commercialiser rapidement, au moment où que vous envoyez votre application, le marché que vous cibliez sera ont évolué. Vous serez peut-être trop tard, quel que soit l’application a été conçue ou conçue. Vous pourrez être échoue ou n’atteignent votre potentiel, car vous ne pouvez pas synchroniser livraison d’applications avec les besoins du marché.

La nécessité d’innovation de continuité d’activité exécute un push des équipes de développement et les opérations à la limite. La seule façon d’atteindre l’agilité que vous avez besoin dans l’innovation de continuité d’activité est par la modernisation de vos applications avec les technologies telles que les conteneurs et les principes de l’application optimisé pour le Cloud spécifique.

L’essentiel est que lorsqu’une organisation génère et gère les applications qui sont optimisées sur le Cloud, il peut placer des solutions dans les mains des clients plus tôt et donner des idées nouvelles sur le marché lorsqu’elles sont pertinentes.

## <a name="cloud-optimized-application-principles-and-tenets"></a>Principes et aux principes de l’application optimisé pour le cloud 

Améliorations dans le cloud sont principalement centrées sur deux objectifs : Réduire les coûts et améliorer la croissance de l’entreprise en améliorant la réactivité. Ces objectifs sont atteints en qui simplifie les processus et en réduisant les frictions lorsque vous relâchez et livrer des applications.

Votre application est optimisé pour le Cloud si vous pouvez dans agile manière-développer votre application autonome à partir d’autres applications locales, puis relâchez la souris, déployez, l’échelle automatique, surveiller et résoudre les problèmes de votre application dans le cloud.

La clé est *agilité*. Vous ne pouvez pas fournis avec agilité, sauf si vous réduisez au strict minimum de n’importe quel déploiement pour la production problèmes et les problèmes d’environnement de développement/test. Conteneurs (plus précisément, Docker, comme une norme de facto) et les services gérés ont été conçus spécialement à cet effet.

Pour atteindre l’agilité, vous devez également les processus DevOps automatisés qui sont basées sur les pipelines CI/CD qui passent en plates-formes évolutives dans le cloud. Plates-formes de CI/CD (comme Azure DevOps Services ou Jenkins) déploiement sur une plateforme cloud évolutive et résiliente (comme Azure App Service ou Azure Kubernetes Service) sont des technologies clés permettant d’atteindre l’agilité dans le cloud.

La liste suivante décrit les principes principales ou les pratiques pour les applications optimisé pour le Cloud. Notez que vous pouvez adopter tout ou uniquement certains de ces principes, dans une approche progressive ou incrémentielle :

- **Conteneurs**. Conteneurs vous permettent d’inclure les dépendances d’application avec l’application elle-même. Mise en conteneur réduit considérablement le nombre de problèmes que vous pouvez rencontrer lorsque vous déployez pour les environnements de production ou de test dans les environnements intermédiaires. Au final, les conteneurs améliorent l’agilité de livraison d’applications.

- **Cloud résilient et évolutif**. Le cloud offre une plateforme qui est géré, élastique, évolutive et résiliente. Ces caractéristiques sont fondamentaux pour obtenir des améliorations de coût et de livrer des applications disponibles et fiables, hautement dans une livraison continue. Les services gérés, tels que les bases de données managées, gérés mettre en cache comme un service (CaaS) et le stockage géré sont des éléments fondamentaux en limitant les coûts de maintenance de votre application.

- **Surveillance**. Vous ne pouvez avoir une application fiable sans avoir un bon moyen de détecter et diagnostiquer les exceptions et les problèmes de performances des applications. Vous devez obtenir des insights actionnables via la gestion des performances d’application et l’analytique instantanée.

- **DevOps culture et la livraison continue**. Adopter les pratiques DevOps nécessite un changement culturel dans lequel les équipes ne fonctionnent plus dans des silos indépendants. Pipelines CI/CD sont possibles uniquement s’il existe une amélioration de la collaboration entre le développement et les équipes informatiques, pris en charge par les conteneurs et les outils de CI/CD.

Figure 4-2 illustre les principaux piliers de facultatifs d’une application optimisé pour le Cloud. Les piliers plus que vous implémentez, la meilleure votre application sera pour réussir dans répondant aux attentes de vos clients.

> ![Axes principaux d’une application optimisé pour le Cloud](./media/image2.png)
>
> **Figure 4-2.** Axes principaux d’une application optimisé pour le Cloud

Pour résumer, une application optimisé pour le Cloud est une approche pour la création et la gestion des applications qui tire parti du cloud computing de modèle, tout en utilisant une combinaison de conteneurs, l’infrastructure de cloud géré, techniques de résilience de l’application, surveillance, la livraison continue et DevOps, tout ceci sans devoir remanier l’architecture et de réécrire vos applications existantes.

Votre organisation peut adopter ces approches et technologies progressivement. Vous n’êtes pas obligé d’adopter tous, à la fois. Vous pouvez adopter les progressivement, selon les priorités de l’entreprise et les besoins de l’utilisateur.

## <a name="benefits-of-a-cloud-optimized-application"></a>Avantages d’une application optimisé pour le Cloud

Vous pouvez obtenir les avantages suivants en convertissant une application existante vers une application optimisé pour le Cloud (sans modifier l’architecture ou de codage) :

- **Réduire les coûts, car l’infrastructure managée est géré par le fournisseur de cloud**. Optimisé pour le cloud des applications bénéficiez des avantages du cloud à l’aide de l’élasticité du cloud out-of-the-box, mise à l’échelle et haute disponibilité. Avantages associés non seulement pour les fonctionnalités de calcul (machines virtuelles et conteneurs), mais dépendent également des ressources dans le cloud, tels que DBaaS, CaaS et n’importe quelle infrastructure, une application peut nécessaire.

- **Résilience de l’application et infrastructure**. Lorsque vous migrez vers le cloud, vous devez gérer les défaillances transitoires ; échecs seront produit dans le cloud. En outre, matériel et l’infrastructure de cloud sont « remplaçables, » ce qui augmente les opportunités pour des temps morts temporaires. En même temps, les fonctionnalités de cloud interne et certaines techniques de développement d’application qui implémentent la résilience et d’automatiser la récupération rendent beaucoup plus facile de défaillances inattendues dans le cloud.

- **Des insights approfondis sur les performances de l’application**. Outils de surveillance, comme Azure Application Insights fournissent la visualisation pour la gestion de la santé, de journalisation et de notifications sur le cloud. Journaux d’audit rendent les applications facile à déboguer et à auditer, fondamental pour une application cloud fiable.

- **Portabilité des applications, avec les déploiements agiles**. Les conteneurs (Linux ou Windows des conteneurs basés sur le moteur Docker) offrent la meilleure solution pour éviter une application verrouillée de cloud. À l’aide de conteneurs, les hôtes Docker et les orchestrateurs de multicloud, vous pouvez facilement déplacer d’un environnement ou cloud vers un autre. Conteneurs éliminent la friction qui se produit généralement lors de déploiements sur n’importe quel environnement (étape/test/production).

Tous ces avantages fournissent au final des réductions des coûts de clés pour votre application de bout en bout du cycle de vie.

Dans les sections suivantes, ces avantages sont expliquées plus en détail et sont liés à des technologies spécifiques.

>[!div class="step-by-step"]
>[Précédent](index.md)
>[Suivant](microsoft-technologies-in-cloud-optimized-applications.md)
