---
title: Présentation de l’application de référence eShopOnContainers
description: Présentation de l’application de référence eShopOnContainers Cloud Native microservices pour ASP.NET Core et Azure.
ms.date: 05/13/2020
ms.openlocfilehash: a6f3defabec809eaf1cb143e2b521904248b74f2
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613965"
---
# <a name="introducing-eshoponcontainers-reference-app"></a>Présentation de l’application de référence eShopOnContainers

Microsoft, en partenariat avec les principaux experts de la Communauté, a produit une application de référence de microservices Cloud native complète, eShopOnContainers. Cette application est conçue pour s’intégrer à l’aide de .NET Core et de docker, et éventuellement Azure, Kubernetes et Visual Studio, pour créer une boutique en ligne.

![Capture d’écran de l’exemple d’application eShopOnContainers.](./media/eshoponcontainers-sample-app-screenshot.png)

**Figure 2-1**. Capture d’écran de l’exemple d’application eShopOnContainers.

Avant de commencer ce chapitre, nous vous recommandons de télécharger l' [application de référence eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers). Dans ce cas, il est plus facile de suivre les informations présentées.

## <a name="features-and-requirements"></a>Fonctionnalités et configuration requise

Commençons par une revue des fonctionnalités et des exigences de l’application. L’application eShopOnContainers représente un magasin en ligne qui vend divers produits physiques tels que des tee-shirts et des tasses à café. Si vous avez acheté des éléments en ligne auparavant, l’expérience de l’utilisation du magasin doit être relativement familière. Voici quelques-unes des fonctionnalités de base implémentées par le Store :

- Répertorier les éléments du catalogue
- Filtrer les éléments par type
- Filtrer les éléments par la personnalisation
- Ajouter des éléments au panier d’achat
- Modifier ou supprimer des éléments du panier
- Checkout
- Inscrire un compte
- Se connecter
- Se déconnecter
- Passer en revue les commandes

L’application présente également les exigences non fonctionnelles suivantes :

- Elle doit être hautement disponible et doit être mise à l’échelle automatiquement pour répondre à l’augmentation du trafic (et à la mise à l’échelle une fois le trafic).
- Il doit fournir une surveillance facile à utiliser de ses journaux d’intégrité et de diagnostic pour aider à résoudre les problèmes qu’il rencontre.
- Il doit prendre en charge un processus de développement Agile, y compris la prise en charge de l’intégration et du déploiement continus (CI/CD).
- Outre les deux serveurs Web frontaux (application traditionnelle et à page unique), l’application doit également prendre en charge les applications clientes mobiles exécutant différents types de systèmes d’exploitation.
- Il doit prendre en charge l’hébergement multiplateforme et le développement interplateforme.

![eShopOnContainers référence de l’architecture de développement d’applications.](./media/eshoponcontainers-development-architecture.png)

**Figure 2-2**. eShopOnContainers référence de l’architecture de développement d’applications.

L’application eShopOnContainers est accessible à partir de clients Web ou mobiles qui accèdent à l’application via le protocole HTTPs ciblant soit l’application de serveur ASP.NET Core MVC, soit une passerelle d’API appropriée. Les passerelles d’API offrent plusieurs avantages, tels que le découplage des services principaux de clients frontaux individuels et une meilleure sécurité. L’application utilise également un modèle associé connu sous le nom de « serveurs principaux-pour-frontends » (BFF), qui recommande de créer des passerelles d’API distinctes pour chaque client frontal. L’architecture de référence montre comment fractionner les passerelles d’API selon que la demande provient d’un client Web ou mobile.

La fonctionnalité de l’application est divisée en plusieurs microservices distincts. Des services sont responsables de l’authentification et de l’identité, de la liste des éléments du catalogue de produits, de la gestion des paniers d’achat des utilisateurs et du placement des commandes. Chacun de ces services distincts a son propre stockage persistant. Il n’existe pas de magasin de données maître unique avec lequel tous les services interagissent. Au lieu de cela, la coordination et la communication entre les services s’effectuent en fonction des besoins et à l’aide d’un bus de messages.

Chacun des différents microservices est conçu différemment, en fonction de leurs besoins individuels. Cela signifie que leur pile technologique peut varier, bien qu’elles soient toutes créées à l’aide de .NET Core et conçues pour le Cloud. Les services plus simples offrent un accès de base en création-lecture-mise à jour-suppression (CRUD) aux magasins de données sous-jacents, tandis que les services plus avancés utilisent des approches de conception pilotées par domaine et des modèles pour gérer la complexité des activités.

![Différents genres de microservices](./media/different-kinds-of-microservices.png)

**Figure 2-3**. Différents genres de microservices.

## <a name="overview-of-the-code"></a>Vue d’ensemble du code

Étant donné qu’il tire parti des microservices, l’application eShopOnContainers comprend un certain nombre de projets et de solutions distincts dans son référentiel GitHub. En plus des solutions et des fichiers exécutables distincts, les différents services sont conçus pour s’exécuter dans leurs propres conteneurs, à la fois pendant le développement local et au moment de l’exécution en production. La figure 2-4 illustre la solution Visual Studio complète, dans laquelle les différents projets sont organisés.

![Projets dans la solution Visual Studio.](./media/projects-in-visual-studio-solution.png)

**Figure 2-4**. Projets dans la solution Visual Studio.

Le code est organisé pour prendre en charge les différents microservices, et au sein de chaque microservice, le code est divisé en logique de domaine, en problèmes d’infrastructure et en interface utilisateur ou point de terminaison de service. Dans de nombreux cas, les dépendances de chaque service peuvent être exécutées par les services Azure en production, ainsi que des options alternatives pour le développement local. Examinons comment les exigences de l’application sont mappées aux services Azure.

## <a name="understanding-microservices"></a>Compréhension des microservices

Ce document se concentre sur les applications Cloud natives créées à l’aide de la technologie Azure. Pour en savoir plus sur les meilleures pratiques relatives aux microservices et sur l’architecture des applications basées sur des microservices, consultez la documentation complémentaire sur les microservices [.net : architecture pour les applications .net en conteneur](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook).

>[!div class="step-by-step"]
>[Précédent](candidate-apps.md) 
> [Suivant](map-eshoponcontainers-azure-services.md)
