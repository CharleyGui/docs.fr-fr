---
title: Exemple d’index de code WIF
ms.date: 03/30/2017
ms.assetid: 6711f01a-4743-43ce-95ab-5e2302a363ea
author: BrucePerlerMS
ms.openlocfilehash: 1e90c5f8681706aa0d52c74e6caff08edbf283da
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045158"
---
# <a name="wif-code-sample-index"></a>Exemple d’index de code WIF

Les exemples de code suivants s’appliquent à Windows Identity Foundation 4.5 :

- [ClaimsAwareWebApp](https://go.microsoft.com/fwlink/?LinkID=248405) : cet exemple illustre l’utilisation de base de l’externalisation de l’authentification (vers le service d’émission de jeton de sécurité de test local à partir de l’outil Identity and Access Tool pour Visual Studio 11) sur une application ASP.NET standard (par opposition à un site web).

- [ClaimsAwareWebService](https://go.microsoft.com/fwlink/?LinkID=248406) : cet exemple illustre l’utilisation de base de l’externalisation de l’authentification sur un service WCF standard.

- [ClaimsAwareMvcApplication](https://go.microsoft.com/fwlink/?LinkID=248407) : cet exemple montre comment intégrer WIF avec MVC, y compris une protection non globale et le code qui effectue l’authentification par formulaire et la redirige hors du contrôleur d’ouverture de session.

- [ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408) : cet exemple montre un cache de sessions prêt pour une batterie de serveurs (par opposition à un tokenreplycache) qui vous permet d’utiliser des sessions par référence au lieu d’échanger des cookies de grande taille. Il montre également un moyen plus simple de sécuriser les cookies dans une batterie de serveurs.

- [ClaimsAwareFormsAuthentication](https://go.microsoft.com/fwlink/?LinkID=248409) : cet exemple très simple montre de quelle façon .NET 4.5 vous permet d’obtenir les revendications dans vos principaux, indépendamment de la méthode d’authentification des utilisateurs que vous utilisez.

- [ClaimsBasedAuthorization](https://go.microsoft.com/fwlink/?LinkID=248410): cet exemple montre comment utiliser votre classe ClaimsAuthorizationManager et le ClaimsAuthorizationModule pour appliquer vos propres stratégies d’autorisation.

- [FederationMetadata](https://go.microsoft.com/fwlink/?LinkID=248411) : cet exemple illustre la génération dynamique (sur un STS personnalisé) et l’utilisation dynamique (sur une application par partie de confiance) de documents de métadonnées.

- [CustomToken](https://go.microsoft.com/fwlink/?LinkID=248412) : cet exemple montre comment créer un type de jeton SWT personnalisé.

## <a name="see-also"></a>Voir aussi

- [Windows Identity Foundation](index.md)
