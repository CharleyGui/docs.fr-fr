---
title: Choisir l’option d’hébergement Azure appropriée
description: Découvrez le chemin de migration Azure adapté à votre application web ASP.NET.
author: CESARDELATORRE
ms.author: cesardl
ms.date: 03/01/2020
ms.openlocfilehash: a8ad946b03f97272cb8685620858af6b21a372dc
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "82072108"
---
# <a name="choose-the-right-azure-hosting-option"></a>Choisir l’option d’hébergement Azure appropriée

Cet article fournit des considérations et des comparaisons entre les multiples choix que vous avez dans Azure lors de la migration de vos applications cadre .NET existantes de sur place à Azure.

Les zones fondamentales à prendre en considération lors de la migration d’applications .NET existantes vers Azure sont les suivantes :

1. Choix de calcul
1. Choix de la base de données
1. Considérations relatives au réseau et à la sécurité
1. Considérations relatives à l’authentification et à l’autorisation

## <a name="compute-choices"></a>Choix de calcul

Lorsque vous migrez des applications .NET Framework existantes vers Azure, plusieurs choix s’offrent à vous. Toutefois, étant donné que .NET Framework dépend de Windows, les choix suivants sont limités aux services de calcul basés sur Windows.

Le tableau suivant comporte plusieurs comparaisons et recommandations qui vont vous aider à choisir le chemin de migration de calcul adapté à votre application .NET. existante.

|                 | Machines virtuelles Azure | Azure App Service | Conteneurs Windows |
|-----------------|-----------|-------------------|--------------------|
|Quand l’utiliser      |<ul><li>L’application dépend fortement des installations .msi en local et sur le serveur.</li><li>Vous recherchez le chemin de migration d’application le plus simple qui soit</li></ul>|L’application ne dispose d’aucune dépendance sur le serveur. Il s’agit simplement d’une application web ASP.NET propre (MVC, Web Forms) ou d’une application multiniveau (API web, WCf) accédant à un serveur de base de données. |<ul><li>L’application possède des dépendances sur le serveur d’origine, mais ces dernières peuvent être incluses dans l’image Windows Docker.</li><li>Vous voulez moderniser l’application afin qu’il soit [Cloud DevOps-Ready](../../architecture/modernize-with-azure-containers/modernize-existing-apps-to-cloud-optimized/reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)</li></ul>|
|Avantages  |<ul><li>Le chemin de migration le plus simple</li><li>Un environnement familier. L’environnement de déploiement est un VM, il est donc similaire aux serveurs sur place.</li></ul> |La maintenance PaaS continue est la façon la plus simple de gérer et de mettre à l’échelle des applications dans Azure. |<ul><li>Préparé pour l’avenir, Cloud DevOps-Ready avec des dépendances incluses dans les conteneurs de l’application.</li><li>Presque pas besoin de refactor .NET / code C.</li></ul> |
|Inconvénients             |Il s’agit d’une IaaS. La maintenance est coûteuse. Vous devez gérer l’infrastructure de la VM sur le réseautage, l’équilibreur des charges, l’échelle, la gestion de l’IIS, et ainsi de suite. |<ul><li>Toutes les applications ne sont [pas prises en charge](https://appmigration.microsoft.com/assessment).</li><li>Certaines applications peuvent avoir besoin d’être refactorisées et même légèrement réaménodicées, de sorte qu’elles prennent en charge Azure App Service.</li></ul> |<ul><li>Courbe d’apprentissage des compétences de Docker</li><li>Modification de certains paramètres de configuration d’application et de code</li></ul>|
|Spécifications |Machine virtuelle Windows Server avec la même configuration que l’application pour un environnement local | Exigences azure App Service spécifiées dans [les contrôles de préparation](https://github.com/Azure/App-Service-Migration-Assistant/wiki/Readiness-Checks). |<ul><li>[Docker Engine - Enterprise pour Windows Server 2019](https://azuremarketplace.microsoft.com/marketplace/apps/cloud-infrastructure-services.docker-windows-2019)<br />or</li><li>[Azure Container Service (AKS)](https://azure.microsoft.com/services/container-service/) (il s’agit de l’orchestrateur Kubernetes)<br />or<li>Orchestrateur [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)</li></ul> |
|Migration |Voir [Migrate to Azure Virtual Machines](vm.md) (Migrer vers des machines virtuelles Azure) | Voir [Migrate Azure App Service](app-service.md) (Migrer Azure App Service) | Suivez les considérations, les scénarios et les procédures à pas expliquées dans les [applications .NET existantes modernisantes avec Azure et Windows Containers eBook](https://aka.ms/liftandshiftwithcontainersebook) |

Le diagramme de flowchart suivant montre un arbre de décision lors de la planification d’une migration vers Azure pour vos applications cadre .NET existantes. Si c’est viable, essayez d’abord l’option A, mais l’option B est le chemin le plus facile à exécuter.

![Diagramme montrant l’arbre de décision d’hébergement](../media/migration/choose/decision-tree.png)

## <a name="database-choices"></a>Choix de la base de données

Lorsque vous migrez des bases de données relationnelles vers Azure, plusieurs choix s’offrent à vous. Consultez [Migrer votre base de données SQL Server vers Azure SQL Database](sql.md) pour vous aider à choisir le chemin de migration de base de données adapté pour votre application .NET existante.

## <a name="networking-and-security-considerations"></a>Considérations relatives au réseau et à la sécurité

Lors du déploiement d’applications dans un cloud public comme Microsoft Azure, vous souhaiterez peut-être isoler et sécuriser certains réseaux en [créant des DMZ de réseau](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/), comme un [DMZ entre Azure et l’environnement local](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-hybrid) ou un [DMZ entre Azure et Internet](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-dmz). Les DMZ peuvent être implémentés avec un [réseau virtuel Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).

Grâce aux réseaux virtuels Azure vous pouvez :

- Créer une infrastructure hybride que vous contrôlez
- Utiliser vos propres adresses IP et serveurs DNS
- Sécuriser vos connexions avec un VPN IPsec ou ExpressRoute
- Profiter d’un contrôle granulaire du trafic entre les sous-réseaux
- Créer des topologies réseau sophistiquées avec les appliances virtuelles
- Obtenez un environnement isolé et hautement sécurisé pour vos applications

Pour commencer à créer votre propre réseau virtuel, consultez la [documentation relative au réseau virtuel Azure](https://docs.microsoft.com/azure/virtual-network/).

## <a name="authentication-and-authorization-considerations-when-migrating-to-azure"></a>Considérations relatives à l’authentification et à l’autorisation lors de migration vers Azure

La sécurité est la priorité de toute organisation migrant vers le cloud. La plupart des entreprises ont investi beaucoup de temps, d’argent et d’ingénierie dans la conception et l’élaboration d’un modèle de sécurité, et il est important qu’elles soient en mesure de tirer parti des investissements existants tels que les magasins d’identité et les solutions d’inscription unique.

Nombreuses sont les applications B2E .NET d’entreprise existantes s’exécutant sur site à utiliser Active Directory pour l’authentification et la gestion des identités. Azure AD Connect permet d’intégrer vos répertoires locaux à Azure Active Directory. Pour commencer, consultez [Intégrer vos répertoires locaux à Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).

Consultez [Identity requirements for your hybrid identity solution](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-business-needs) (Exigences relatives à l’identité pour votre solution d’identité hybride) pour améliorer la planification relative à Azure Active Directory.

Les autres choix de protocole d’authentification sont [OAuth](https://en.wikipedia.org/wiki/OAuth) et [OpenID](https://en.wikipedia.org/wiki/OpenID), qui sont courants dans les applications destinées aux consommateurs. Lorsque vous utilisez des bases de données d’identité autonomes, par exemple une base de données ASP.NET Identity SQL encapsulée par IdentityServer4 utilisant OAuth, aucune connectivité aux bases de données ou répertoires locaux n’est généralement requise.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Migrez une application web ASP.NET vers Azure App Service](app-service.md)
