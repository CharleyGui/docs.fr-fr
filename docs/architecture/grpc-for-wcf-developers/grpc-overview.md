---
title: Vue d’ensemble de gRPC-gRPC pour les développeurs WCF
description: En savoir plus sur l’ensemble de principes guidant le développement de gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: a92fe7ca2f8e17126025362fcc3c190024ebf7d3
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967762"
---
# <a name="grpc-overview"></a>présentation de gRPC

Après avoir examiné les Genesis de WCF et gRPC dans le dernier chapitre, ce chapitre traite des principales fonctionnalités de gRPC et de la façon dont elles sont comparées à WCF.

ASP.NET Core 3,0 est la première version de ASP.NET qui prend en charge gRPC en mode natif en tant que citoyen de première classe, avec les équipes Microsoft qui contribuent à l’implémentation officielle .NET de gRPC. Il est recommandé d’utiliser la meilleure approche pour créer des applications distribuées avec .NET, qui peuvent interagir avec tous les autres langages et infrastructures de programmation principaux.

## <a name="key-principles"></a>Principes clés

Comme indiqué dans le chapitre 1, Google souhaitait utiliser l’introduction du protocole HTTP/2 pour remplacer Stubby, son infrastructure RPC interne et à usage général. gRPC, basé sur Stubby, peut désormais tirer parti de la normalisation et étendre son applicabilité à l’informatique mobile, au Cloud et aux Internet des objets.

Pour y parvenir, [CNCF (Cloud Native Computing Foundation)](https://www.cncf.io/) a établi un ensemble de principes qui régissent gRPC. La liste suivante présente les éléments les plus pertinents, principalement liés à l’optimisation de l’accessibilité et de la convivialité :

- **Gratuit et ouvert** : tous les artefacts doivent être open source avec des licences qui ne contraignent pas les développeurs à adopter gRPC.
- **Couverture et simplicité** : gRPC doit être disponible sur toutes les plateformes populaires et être suffisamment simple pour être généré sur n’importe quelle plateforme.
- **Interopérabilité et portée** : il doit être possible d’utiliser gRPC sur n’importe quel réseau, indépendamment de la bande passante ou de la latence, à l’aide de normes réseau largement disponibles.
- **Usage général et performant** : l’infrastructure doit être utilisable par autant de cas d’utilisation que possible sans compromettre les performances.
- **Streaming** : le protocole doit fournir une sémantique de diffusion en continu pour les jeux de données volumineux ou la messagerie asynchrone.
- **Échange de métadonnées** : le protocole permet aux données non professionnelles, telles que les jetons d’authentification, d’être gérées séparément des données métier réelles.
- **Codes d’État normalisés** : la variabilité des codes d’erreur doit être réduite pour que les décisions de gestion des erreurs soient plus claires et, dans le cas où une meilleure gestion des erreurs plus riche est nécessaire, un mécanisme de gestion de ce mécanisme doit être fourni pour gérer ce problème au sein de l’échange de métadonnées.

>[!div class="step-by-step"]
>[Précédent](introduction.md)
>[Suivant](approach.md)
