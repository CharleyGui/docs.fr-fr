---
title: Vue d’ensemble de gRPC-gRPC pour les développeurs WCF
description: En savoir plus sur l’ensemble de principes guidant le développement de gRPC.
ms.date: 12/15/2020
ms.openlocfilehash: 99e1bdb1f49469f444044027c3ac5d927f9cab13
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938401"
---
# <a name="grpc-overview"></a>présentation de gRPC

Après avoir examiné les Genesis des deux Windows Communication Foundation (WCF) et gRPC dans le dernier chapitre, ce chapitre traite des principales fonctionnalités de gRPC et de la façon dont elles sont comparées à WCF.

ASP.NET Core 3,0 est la première version de ASP.NET qui prend en charge gRPC en mode natif en tant que citoyen de première classe, avec les équipes Microsoft qui contribuent à l’implémentation officielle .NET de gRPC. Il est recommandé de créer des applications distribuées avec .NET qui peuvent interagir avec tous les autres langages et infrastructures de programmation principaux.

## <a name="key-principles"></a>Principes clés

Comme indiqué dans le chapitre 1, Google souhaitait utiliser l’introduction du protocole HTTP/2 pour remplacer Stubby, son infrastructure RPC interne et à usage général. gRPC, basé sur Stubby, peut désormais tirer parti de la normalisation et étendre son applicabilité à l’informatique mobile, au Cloud et aux Internet des objets.

Pour réaliser cette normalisation, [CNCF (Cloud Native Computing Foundation)](https://www.cncf.io/) a établi un ensemble de principes qui régissent gRPC. La liste suivante présente les éléments les plus pertinents, principalement liés à l’optimisation de l’accessibilité et de la convivialité :

- **Gratuit et ouvert** : tous les artefacts doivent être open source, avec une licence qui ne contraint pas les développeurs à adopter gRPC.
- **Couverture et simplicité** : gRPC doit être disponible sur toutes les plateformes populaires et être suffisamment simple pour s’appuyer sur n’importe quelle plateforme.
- **Interopérabilité et portée** : il doit être possible d’utiliser gRPC sur n’importe quel réseau, indépendamment de la bande passante ou de la latence, en utilisant des normes réseau largement disponibles.
- **Usage général et performant** : l’infrastructure doit être utilisable par autant de cas d’utilisation que possible, sans compromettre les performances.
- **Streaming** : le protocole doit fournir une sémantique de diffusion en continu pour les jeux de données volumineux ou la messagerie asynchrone.
- **Échange de métadonnées** : le protocole permet aux données non professionnelles, telles que les jetons d’authentification, d’être gérées séparément des données métier réelles.
- **Codes d’État normalisés** : la variabilité des codes d’erreur doit être réduite pour rendre les décisions de gestion des erreurs plus claires. Là où une gestion des erreurs plus riche est nécessaire, un mécanisme doit être fourni pour gérer le comportement au sein de l’échange de métadonnées.

>[!div class="step-by-step"]
>[Précédent](introduction.md) 
> [Suivant](approach.md)
