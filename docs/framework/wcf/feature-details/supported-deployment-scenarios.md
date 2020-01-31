---
title: Scénarios de déploiement pris en charge
ms.date: 03/30/2017
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
ms.openlocfilehash: 5be9ab3d300da2095a45846d334512382b4067f6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743452"
---
# <a name="supported-deployment-scenarios"></a>Scénarios de déploiement pris en charge

Le sous-ensemble de fonctionnalités de Windows Communication Foundation (WCF) prises en charge pour une utilisation dans des applications de confiance partielle est conçu pour répondre aux exigences de certains scénarios, mais pas tous, pour l’utilisation de WCF. Sur le serveur, WCF répond aux exigences des fournisseurs d’hébergement partagé à l’échelle d’Internet qui exécutent des applications tierces dans le jeu d’autorisations de confiance moyenne ASP.NET 2,0 pour des raisons de sécurité. Sur le client, la prise en charge de la confiance partielle de WCF est conçue pour répondre aux exigences des technologies de déploiement telles que le [déploiement ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) ou la technologie d’application du navigateur XAML de WPF, qui permet un déploiement transparent et sécurisé d’applications de bureau à partir de sites non approuvés.

## <a name="minimum-permission-requirements"></a>Conditions minimales requises pour les autorisations

WCF prend en charge un sous-ensemble de fonctionnalités dans les applications qui s’exécutent sous l’un des jeux d’autorisations nommés standard suivants :

- Autorisations de confiance moyenne

- Autorisations de la zone Internet

Toute tentative d’utilisation de WCF dans des applications de confiance partielle avec des autorisations plus restrictives peut entraîner des exceptions de sécurité au moment de l’exécution.

Pour plus d’informations sur les fonctionnalités prises en charge dans ces jeux d’autorisations, consultez [Partial Trust Feature Compatibility](partial-trust-feature-compatibility.md).

## <a name="partial-trust-on-the-server"></a>Confiance partielle sur le serveur

De nombreux fournisseurs commerciaux de services d’hébergement d’applications Web ASP.NET obligent les applications qui s’exécutent sur leurs serveurs à s’exécuter dans le jeu d’autorisations ASP.NET 2,0 moyenne Trust. Les services WCF peuvent s’exécuter dans ces environnements, à condition qu’ils utilisent le <xref:System.ServiceModel.BasicHttpBinding>, le <xref:System.ServiceModel.WebHttpBinding>ou le <xref:System.ServiceModel.WSHttpBinding> avec la sécurité au niveau du transport.

Les services WCF s’exécutant dans des environnements d’hébergement de confiance moyenne peuvent également servir de services de couche intermédiaire en envoyant des messages à d’autres serveurs en réponse aux demandes des clients. Les scénarios de couche intermédiaire sur le serveur sont pris en charge si l'environnement d'hébergement a accordé le <xref:System.Net.WebPermission> approprié à l'application pour effectuer des demandes sortantes vers le serveur souhaité.

En plus de la messagerie SOAP utilisant l’une des liaisons SOAP prises en charge, WCF prend en charge les <xref:System.ServiceModel.WebHttpBinding> pour la création de services de style Web dans des applications de confiance partielle. Le [modèle de programmation http Web WCF](wcf-web-http-programming-model.md), la [syndication WCF](wcf-syndication.md)et l' [intégration Ajax et les fonctionnalités de prise en charge JSON](ajax-integration-and-json-support.md) de WCF sont toutes prises en charge en mode de confiance partielle.

Les services de workflow requièrent des autorisations de confiance totale et ne peuvent pas être utilisés dans les applications de confiance partielle.

Pour plus d’informations, consultez [procédure : utiliser la confiance moyenne dans ASP.NET 2,0](https://docs.microsoft.com/previous-versions/msp-n-p/ff648344(v=pandp.10)).

## <a name="partial-trust-on-the-client"></a>Confiance partielle sur le client

Certaines précautions de sécurité doivent être prises lors du téléchargement et de l'exécution du code à partir de sites Internet non fiables. Le [déploiement ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) et la technologie d’application du navigateur XAML de WPF utilisent la confiance partielle pour accorder des autorisations limitées (zone Internet) à du code non fiable.

WCF peut être utilisé pour communiquer avec des serveurs distants à partir d’applications de confiance partielle déployées par un [déploiement ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) ou une application XBAP. Le jeu d’autorisations de la zone Internet comprend <xref:System.Net.WebPermission> pour l’hôte d’origine, ce qui permet à ces applications de communiquer avec leur serveur d’origine à l’aide de l’une des liaisons WCF prises en charge décrites dans [compatibilité de fonctionnalités de confiance partielle](partial-trust-feature-compatibility.md).

## <a name="see-also"></a>Voir aussi

- [Sécurité d’accès du code](../../misc/code-access-security.md)
- [Vue d’ensemble des applications hébergées par un navigateur Windows Presentation Foundation](../../wpf/app-development/wpf-xaml-browser-applications-overview.md)
- [Confiance partielle](partial-trust.md)
- [Niveaux de confiance ASP.NET et fichiers de stratégie](https://docs.microsoft.com/previous-versions/wyts434y(v=vs.140))
