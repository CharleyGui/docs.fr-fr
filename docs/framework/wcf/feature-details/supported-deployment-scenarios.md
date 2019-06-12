---
title: Scénarios de déploiement pris en charge - WCF
ms.date: 03/30/2017
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
ms.openlocfilehash: 7b508f53365c1b4b90e2883ddb9d5f2a71c7e814
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025627"
---
# <a name="supported-deployment-scenarios"></a>Scénarios de déploiement pris en charge

Le sous-ensemble de fonctionnalités de Windows Communication Foundation (WCF) prises en charge pour une utilisation dans les applications de confiance partielle est conçu pour répondre aux exigences de certains, mais pas tous, scénarios pour l’utilisation de WCF. Sur le serveur, WCF répond aux exigences de l’échelle d’Internet, les fournisseurs d’hébergement partagés qui exécutent des applications tierces dans l’autorisation ASP.NET 2.0 Medium Trust définies pour des raisons de sécurité. Sur le client, prise en charge de la confiance partielle WCF est conçu pour répondre aux exigences de technologies de déploiement telles que [déploiement ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) ou [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]de technologie d’Application de navigateur XAML permettant transparentes et sécurisées déploiement d’applications bureautiques à partir de sites non approuvés.

## <a name="minimum-permission-requirements"></a>Autorisations minimales requises

WCF prend en charge un sous-ensemble de fonctionnalités dans les applications qui s’exécutent sous des ensembles d’autorisations nommés standard suivants :

- Autorisations de confiance moyenne

- Autorisations de la zone Internet

Tentative d’utilisation de WCF dans les applications de confiance partielle avec des autorisations plus restrictives peut entraîner des exceptions de sécurité lors de l’exécution.

Pour plus d’informations sur les fonctionnalités prises en charge dans ces jeux d’autorisations, consultez [Partial Trust Feature Compatibility](partial-trust-feature-compatibility.md).

## <a name="partial-trust-on-the-server"></a>Confiance partielle sur le serveur

Nombreux fournisseurs commerciaux de services d’hébergement d’applications Web ASP.NET imposent que les applications en cours d’exécution sur leurs serveurs s’exécutent dans le jeu d’autorisations ASP.NET 2.0 Medium Trust. WCF services peuvent s’exécuter dans ces environnements fournis s’ils utilisent le <xref:System.ServiceModel.BasicHttpBinding>, le <xref:System.ServiceModel.WebHttpBinding>, ou le <xref:System.ServiceModel.WSHttpBinding> avec la sécurité au niveau du transport.

Les services WCF en cours d’exécution dans les environnements d’hébergement de confiance moyenne peuvent également agir en tant que services de niveau intermédiaire en envoyant des messages vers d’autres serveurs en réponse aux demandes des clients. Les scénarios de couche intermédiaire sur le serveur sont pris en charge si l'environnement d'hébergement a accordé le <xref:System.Net.WebPermission> approprié à l'application pour effectuer des demandes sortantes vers le serveur souhaité.

Outre la messagerie SOAP à l’aide d’une des liaisons SOAP prises en charge, WCF prend en charge la <xref:System.ServiceModel.WebHttpBinding> pour la création de services de style Web dans les applications partiellement fiables. Le [modèle de programmation WCF Web HTTP](wcf-web-http-programming-model.md), [Syndication WCF](wcf-syndication.md), et [intégration d’AJAX et prise en charge JSON](ajax-integration-and-json-support.md) fonctionnalités de WCF sont toutes prises en charge en mode de confiance partielle.

Les services de workflow requièrent des autorisations de confiance totale et ne peuvent pas être utilisés dans les applications de confiance partielle.

Pour plus d'informations, voir [Procédure : Utiliser la confiance moyenne dans ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=84603).

## <a name="partial-trust-on-the-client"></a>Confiance partielle sur le client

Certaines précautions de sécurité doivent être prises lors du téléchargement et de l'exécution du code à partir de sites Internet non fiables. La technologie [ClickOnce Deployment](/visualstudio/deployment/clickonce-security-and-deployment) (Déploiement ClickOnce) et la technologie d’application du navigateur XAML (XBAP) de [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]utilisent la confiance de niveau partiel pour accorder des autorisations limitées (zone Internet) au code non fiable.

WCF peut être utilisé pour communiquer avec des serveurs distants à partir d’applications de confiance partiel déployées par soit [déploiement ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) ou XBAP. Le jeu d’autorisations de Zone Internet inclut <xref:System.Net.WebPermission> pour l’hôte d’origine, ce qui autorise ces applications à communiquer avec leur serveur d’origine en utilisant l’une des liaisons WCF pris en charge décrites dans [Partial Trust Feature Compatibility ](partial-trust-feature-compatibility.md).

## <a name="see-also"></a>Voir aussi

- [Sécurité d’accès du code](../../misc/code-access-security.md)
- [Vue d’ensemble de Windows Presentation Foundation Applications hébergées par un navigateur](../../wpf/app-development/wpf-xaml-browser-applications-overview.md)
- [Confiance partielle](partial-trust.md)
- [ASP.NET Trust Levels and Policy Files](https://docs.microsoft.com/previous-versions/wyts434y(v=vs.140))
