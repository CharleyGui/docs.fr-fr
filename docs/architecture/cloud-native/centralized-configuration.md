---
title: Configuration centralisée
description: La configuration centralisée à l’aide de Azure Key Vault peut faciliter la gestion des applications Cloud natives.
ms.date: 06/30/2019
ms.openlocfilehash: f4f495591550abccf2c64ef24cbe7620b039d8ca
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183517"
---
# <a name="centralized-configuration"></a>Configuration centralisée

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Les applications Cloud natives impliquent beaucoup plus de services en cours d’exécution que les applications monolithiques à instance unique traditionnelles. La gestion des paramètres de configuration pour des dizaines de services interdépendants peut être difficile, c’est pourquoi les banques de configuration centralisées sont souvent implémentées pour les applications distribuées.

Comme indiqué dans le [Chapitre 1](introduction.md), les recommandations relatives aux applications à douze facteurs requièrent une séparation stricte entre le code et la configuration. Cela signifie que le stockage des paramètres de configuration en tant que constantes ou valeurs littérales dans le code est une violation. Cette recommandation existe car le même code doit être utilisé dans plusieurs environnements, y compris le développement, le test, la mise en lots et la production. Toutefois, les valeurs de configuration sont susceptibles de varier d’un environnement à l’autre. Par conséquent, les valeurs de configuration doivent être stockées dans l’environnement lui-même, ou l’environnement doit stocker les informations d’identification dans un magasin de configuration centralisé.

L’application eShopOnContainers comprend des fichiers de paramètres d’application locaux avec chaque microservice. Ces fichiers sont archivés dans le contrôle de code source, mais n’incluent pas les secrets de production tels que les chaînes de connexion ou les clés API. En production, des paramètres individuels peuvent être remplacés par des variables d’environnement par service. Il s’agit d’une pratique courante pour les applications hébergées, mais elle ne fournit pas de magasin de configuration centralisé. Pour prendre en charge la gestion centralisée des paramètres de configuration, chaque microservice comprend un paramètre permettant de basculer entre l’utilisation des paramètres locaux et des paramètres de Azure Key Vault.

## <a name="azure-key-vault"></a>Azure Key Vault

Azure Key Vault fournit un stockage sécurisé des jetons, des mots de passe, des certificats, des clés d’API et d’autres secrets sensibles. L’accès à Key Vault nécessite une authentification et une autorisation appropriées de l’appelant, ce qui, dans le cas des microservices eShopOnContainers, est l’utilisation d’une combinaison ClientId/ClientSecret. N’archivez pas ces informations d’identification dans le contrôle de code source, mais définissez-les à la place dans l’environnement de l’application. L’accès direct aux Key Vault à partir de AKS peut être obtenu à l’aide de [Key Vault FlexVolume](https://github.com/Azure/kubernetes-keyvault-flexvol).

Avec la configuration centralisée, les paramètres qui s’appliquent à l’ensemble de l’application, tels que le point de terminaison de journalisation centralisée, peuvent être définis une fois et utilisés par chaque partie de l’application distribuée. Bien que les microservices doivent être indépendants les uns des autres, il y a généralement des dépendances partagées dont les détails de configuration peuvent tirer parti d’un magasin de configuration centralisé.

>[!div class="step-by-step"]
>[Précédent](deploy-eshoponcontainers-azure.md)
>[Suivant](scale-applications.md) <!-- Next Chapter -->
