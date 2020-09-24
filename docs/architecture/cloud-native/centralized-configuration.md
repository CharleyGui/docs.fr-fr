---
title: Configuration centralisée
description: Centralisation de la configuration des applications Cloud natives à l’aide de Azure App configuration et du coffre AzureKey.
ms.date: 05/13/2020
ms.openlocfilehash: 0d40c5b2d70f30beb17489dfd55900f7c5fc1a75
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160877"
---
# <a name="centralized-configuration"></a>Configuration centralisée

Contrairement à une application monolithique dans laquelle tous les éléments s’exécutent au sein d’une instance unique, une application Cloud Native se compose de services indépendants répartis sur des machines virtuelles, des conteneurs et des régions géographiques. La gestion des paramètres de configuration pour des dizaines de services interdépendants peut être difficile. Les copies dupliquées des paramètres de configuration dans différents emplacements sont sujettes aux erreurs et difficiles à gérer. La configuration centralisée est une condition essentielle pour les applications Cloud natives distribuées.

Comme indiqué dans le [Chapitre 1](introduction.md), les recommandations relatives aux applications à douze facteurs requièrent une séparation stricte entre le code et la configuration. La configuration doit être stockée en externe à partir de l’application et lue en fonction des besoins. Le stockage des valeurs de configuration en tant que constantes ou valeurs littérales dans le code est une violation. Les mêmes valeurs de configuration sont souvent utilisées par de nombreux services dans la même application. En outre, nous devons prendre en charge les mêmes valeurs dans plusieurs environnements, tels que le développement, les tests et la production. La meilleure pratique consiste à les stocker dans un magasin de configuration centralisé.

Le Cloud Azure présente plusieurs options intéressantes.

## <a name="azure-app-configuration"></a>Azure App Configuration

[Azure App configuration](/azure/azure-app-configuration/overview) est un service Azure entièrement géré qui stocke les paramètres de configuration non-secret dans un emplacement centralisé et sécurisé. Les valeurs stockées peuvent être partagées entre plusieurs services et applications.

Le service est simple à utiliser et offre plusieurs avantages :

- Représentations et mappages de clé/valeur flexibles
- Balisage avec des étiquettes Azure
- Interface utilisateur dédiée pour la gestion
- Chiffrement des informations sensibles
- Interrogation et récupération par lots

Azure App configuration conserve les modifications apportées aux paramètres de clé-valeur pendant sept jours. La fonctionnalité d’instantané à un point dans le temps vous permet de reconstruire l’historique d’un paramètre et même de revenir en arrière pour un déploiement qui a échoué.

La configuration d’application met automatiquement en cache chaque paramètre pour éviter des appels excessifs au magasin de configurations. L’opération d’actualisation attend que la valeur mise en cache d’un paramètre ait expiré avant de mettre ce dernier à jour, même si sa valeur change dans le magasin de configuration. Le délai d’expiration du cache par défaut est de 30 secondes. Vous pouvez remplacer le délai d’expiration.

La configuration d’application chiffre toutes les valeurs de configuration en transit et au repos. Les noms de clés et les étiquettes servent d’index pour récupérer les données de configuration et ne sont pas chiffrés.

Bien que la configuration des applications offre une sécurité renforcée, Azure Key Vault est toujours le meilleur emplacement pour le stockage des secrets d’application. Key Vault propose un chiffrement au niveau du matériel, des stratégies d’accès précises, ainsi que des opérations de gestion, comme la rotation des certificats. Vous pouvez créer des valeurs de configuration d’application qui font référence à des secrets stockés dans un Key Vault.

## <a name="azure-key-vault"></a>Azure Key Vault

Key Vault est un service géré pour stocker et accéder en toute sécurité aux secrets. Un secret est un élément pour lequel vous voulez contrôler étroitement l’accès. Il peut s’agir de clés d’API, de mots de passe ou de certificats. Un coffre est un groupe logique de secrets.

Key Vault réduit considérablement les risques de fuite accidentelle des secrets. Grâce à Key Vault, les développeurs d’applications n’ont plus besoin de stocker les informations de sécurité dans leur application. Cette pratique élimine la nécessité de stocker ces informations dans votre code. Considérons l’exemple d’une application ayant besoin de se connecter à une base de données. Dans ce cas, plutôt que d’inclure la chaîne de connexion dans le code de l’application, vous pouvez simplement la stocker en toute sécurité dans Key Vault.

Vos applications peuvent accéder en toute sécurité aux informations nécessaires en utilisant des URI. Ces URI permettent aux applications de récupérer des versions spécifiques d’un secret. Il n’est pas nécessaire d’écrire du code personnalisé pour protéger les informations secrètes stockées dans Key Vault.

L’accès à Key Vault nécessite une authentification et une autorisation appropriées de l’appelant. En règle générale, chaque microservice Cloud natif utilise une combinaison ClientId/ClientSecret. Il est important de conserver ces informations d’identification en dehors du contrôle de code source. Une bonne pratique consiste à les définir dans l’environnement de l’application. L’accès direct aux Key Vault à partir de AKS peut être obtenu à l’aide de [Key Vault FlexVolume](https://github.com/Azure/kubernetes-keyvault-flexvol).

## <a name="configuration-in-eshop"></a>Configuration dans eShop

L’application eShopOnContainers comprend des fichiers de paramètres d’application locaux avec chaque microservice. Ces fichiers sont archivés dans le contrôle de code source, mais n’incluent pas les secrets de production tels que les chaînes de connexion ou les clés API. En production, des paramètres individuels peuvent être remplacés par des variables d’environnement par service. L’injection de secrets dans les variables d’environnement est une pratique courante pour les applications hébergées, mais elle ne fournit pas de magasin de configuration centralisé. Pour prendre en charge la gestion centralisée des paramètres de configuration, chaque microservice comprend un paramètre permettant de basculer entre l’utilisation des paramètres locaux et des paramètres de Azure Key Vault.

## <a name="references"></a>Références

- [Architecture eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Architecture)
- [Orchestration des microservices et des applications à plusieurs conteneurs pour une grande scalabilité et une haute disponibilité](../microservices/architect-microservice-container-applications/scalable-available-multi-container-microservice-applications.md)
- [Gestion des API Azure](/azure/api-management/api-management-key-concepts)
- [Présentation de Azure SQL Database](/azure/sql-database/sql-database-technical-overview)
- [Cache Azure pour Redis](https://azure.microsoft.com/services/cache/)
- [API pour MongoDB d’Azure Cosmos DB](/azure/cosmos-db/mongodb-introduction)
- [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview)
- [Vue d’ensemble d’Azure Monitor](/azure/azure-monitor/overview)
- [eShopOnContainers : créer un cluster Kubernetes dans AKS](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Deploy-to-Azure-Kubernetes-Service-(AKS)#create-kubernetes-cluster-in-aks)
- [eShopOnContainers : Azure Dev Spaces](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Azure-Dev-Spaces)
- [Azure Dev Spaces](/azure/dev-spaces/about)

>[!div class="step-by-step"]
>[Précédent](deploy-eshoponcontainers-azure.md) 
> [Suivant](scale-applications.md)
