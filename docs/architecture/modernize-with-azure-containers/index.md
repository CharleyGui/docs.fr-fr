---
title: Moderniser les applications .NET existantes avec le cloud Azure et des conteneurs Windows (2ème édition)
description: Découvrez comment effectuer un lift-and-shift et moderniser les applications existantes avec le cloud Azure et des conteneurs dans ce livre électronique.
ms.date: 04/28/2018
ms.openlocfilehash: 95a5870254481a4c6c9eed82b5be5e1eb10be346
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987944"
---
# <a name="modernize-existing-net-applications-with-azure-cloud-and-windows-containers-2nd-edition"></a>Moderniser les applications .NET existantes avec le cloud Azure et des conteneurs Windows (2ème édition)

![Image de couverture du guide Moderniser les applications .NET.](./media/index/web-application-guide-cover-image.png)

PUBLIÉ PAR  
Microsoft Press et Microsoft DevDiv  
Divisions de Microsoft Corporation  
One Microsoft Way  
Redmond, Washington 98052-6399  

Copyright © 2020 par Microsoft Corporation  

Tous droits réservés. Aucune partie du contenu de ce document ne peut être reproduite sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.

Cet ouvrage est disponible gratuitement sous forme de livre électronique via plusieurs canaux Microsoft, comme <https://dot.net/architecture>.

Si vous avez des questions liées [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book)à ce livre, e-mail à .

Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur. Les points de vue, les opinions et les informations exprimés dans cet ouvrage, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.

 Certains exemples sont fournis à titre indicatif uniquement et sont fictifs. Toute association ou lien est purement involontaire ou fortuit.

Microsoft et les marques commerciales mentionnées dans la page web « Marques » sur <https://www.microsoft.com> sont des marques du groupe Microsoft. Toutes les autres marques sont la propriété de leurs propriétaires respectifs.

Auteur :
> **Cesar de la Torre**, Sr. PM, .NET Product Team, Microsoft Corp.

Participants et réviseurs :
> **Scott Hunter**, chef de projet directeur partenaire, équipe .NET, Microsoft  
> **Paul Yuknewicz**, chef de projet responsable principal, équipe Visual Studio Tools, Microsoft  
> **Lisa Guthrie**, chef de projet senior, équipe Visual Studio Tools, Microsoft  
> **Ankit Asthana**, responsable principal de la gestion de projets, équipe .NET, Microsoft  
> **Unai Zorrilla**, développeur en chef, Plain Concepts  
> **Javier Valero**, chef des opérations chez Grupo Solutio  

## <a name="introduction"></a>Introduction

Quand vous décidez de moderniser vos services ou applications web et de les migrer vers le cloud, vous ne devez pas nécessairement refondre entièrement l’architecture de vos applications. La refonte de l’architecture d’une application avec une approche avancée comme celle des microservices n’est pas toujours possible en raison de contraintes de coûts et de temps. Selon le type de l’application, la refonte de son architecture peut aussi ne pas être pas nécessaire. Pour optimiser la rentabilité de la stratégie de migration vers le cloud de votre organisation, il est important de prendre en compte les besoins de votre activité et les exigences de vos applications. Vous devez déterminer :

- Les applications qui nécessitent une transformation ou une nouvelle architecture.

- Les applications qui doivent être modernisées seulement en partie.

- Les applications pouvant faire l’objet d’un lift-and-shift directement dans le cloud.

## <a name="about-this-guide"></a>À propos de ce guide

Ce guide se concentre principalement sur la modernisation initiale des applications web ou orientées service Microsoft .NET Framework existantes, c’est-à-dire l’action de déplacer une charge de travail vers un environnement plus récent ou plus moderne sans altérer significativement le code de l’application et l’architecture de base.

Ce guide présente aussi les avantages de la migration de vos applications vers le cloud et de la modernisation partielle des applications, avec un ensemble spécifique de nouvelles technologies et approches, comme les conteneurs Windows et les plateformes de calcul associées dans les conteneurs Windows prenant en charge Azure.

## <a name="path-to-the-cloud-for-existing-net-applications"></a>Déplacement vers le cloud des applications .NET existantes

En règle générale, les organisations choisissent de passer au cloud pour apporter souplesse et rapidité à leurs applications. Vous pouvez configurer des milliers de serveurs (des machines virtuelles) dans le cloud en quelques minutes, en comparaison aux semaines généralement nécessaires pour configurer des serveurs locaux.

Il n’existe pas de stratégie unique et universelle pour migrer des applications dans le cloud. La bonne stratégie de migration pour vous dépend des besoins et des priorités de votre organisation, ainsi que du type des applications que vous migrez. Les applications ne justifient pas toutes l’investissement nécessaire pour passer à un modèle Paas ([plateforme en tant que service](https://azure.microsoft.com/overview/what-is-paas/)) ou pour développer un modèle d’application [natif pour le cloud](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications). Dans de nombreux cas, vous pouvez adopter une approche progressive ou incrémentielle quand vous investissez dans le déplacement de vos ressources sur le cloud, en fonction des besoins de votre entreprise.

Pour les applications modernes avec les meilleures agilité et valeur ajoutée à long terme pour l’organisation, vous pouvez tirer profit d’un investissement dans des architectures d’application *cloud natives*. Cependant, pour les applications qui sont des ressources existantes ou héritées, le plus important est de consacrer le moins de temps et d’argent possible (pas de refonte de l’architecture ni de modifications du code) lors de leur passage dans le cloud, de façon à en tirer des avantages significatifs.

La figure 1-1 montre les voies possibles utilisables quand vous faites passer progressivement des applications .NET existantes dans le cloud.

 ![Voies de modernisation pour les applications et les services .NET existants](./media/image1-1.png)

**Figure 1-1**. Voies de modernisation pour les applications et les services .NET existants

Chaque approche de la migration présente des avantages différents et est utilisée pour des raisons différentes. Vous pouvez choisir une même approche quand vous migrez des applications vers le cloud, ou choisir certains composants provenant de plusieurs approches. Les applications individuelles ne sont pas limitées à une seule approche ou à un seul état de maturité. Par exemple, une approche hybride courante consiste à avoir certains des composants en local et d’autres composants dans le cloud.

Voici la définition et une petite explication de chaque niveau de maturité de l’application :

**Niveau 1 : Applications Cloud Infrastructure-Ready** : Dans cette approche de migration, vous migrez ou regelez simplement vos applications actuelles sur site vers une infrastructure en tant que plate-forme de service[(IaaS).](https://azure.microsoft.com/overview/what-is-iaas/) Vos applications ont pratiquement la même composition qu’avant, mais vous les déployez désormais sur des machines virtuelles dans le cloud.
Ce type de migration simple est généralement connu sous le nom de « Lift & Shift » dans le secteur.

**Niveau 2 :** Applications optimisées pour le cloud : à ce niveau et toujours sans rétropuces ni modification de code significatif, vous pouvez tirer des avantages supplémentaires de l’exécution de votre application dans le cloud avec des technologies modernes comme des conteneurs et des services supplémentaires gérés par le cloud. Vous améliorez l’agilité de vos applications pour les livrer plus rapidement, en affinant les processus de fonctionnement du développement (DevOps) dans votre entreprise. C’est possible en utilisant des technologies comme les conteneurs Windows, qui se basent sur le moteur Docker. Les conteneurs suppriment les freins liés aux dépendances des applications quand vous déployez en plusieurs étapes. Dans ce modèle de maturité, vous pouvez déployer des conteneurs sur IaaS ou PaaS tout en utilisant d’autres services managés par le cloud associés aux bases de données, au cache en tant que service, à la supervision et aux pipelines d’intégration continue/de déploiement continu (CI/CD).

Le troisième niveau de maturité est l’objectif ultime dans le cloud, mais il est facultatif pour de nombreuses applications et ne constitue pas l’objet principal de ce guide :

**Niveau 3 : Applications Cloud-Native** : Cette approche de migration est généralement motivée par les besoins de l’entreprise et cible la modernisation de vos applications essentielles à la mission. À ce niveau, vous utilisez des services PaaS pour passer vos applications sur des plateformes informatiques PaaS. Vous implémentez des applications et une architecture de microservices [natives pour le cloud](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) pour faire évoluer les applications avec une agilité à long terme et pour les adapter à de nouvelles limites. Ce type de modernisation nécessite généralement une architecture spécifique pour le cloud. Du nouveau code doit souvent être écrit, en particulier quand vous passez à des modèles d’application natifs pour le cloud et basés sur des microservices. Cette approche peut vous aider à profiter d’avantages difficiles à obtenir dans votre environnement applicatif monolithique et local.

Le tableau 1-1 décrit les principaux avantages et les raisons de choisir chaque approche de migration ou de modernisation.

| **Prêt pour l’infrastructure cloud** <br /> *Soulevez et déplacez* | **Optimisé pour le cloud** <br /> *Moderniser* | **Nuage-autochtone** <br /> *Moderniser, réarchitecturer et réécrire* |
|---|---|---|
| **Cible informatique de l’application** |
| Applications déployées sur des machines virtuelles dans Azure | Applications monolithiques ou multiniveaux déployées sur Azure App Service, Azure Container Instance (ACI), des machines virtuelles avec conteneurs ou Azure Kubernetes Service (AKS) | Microservices conteneurisés sur Azure Kubernetes service (AKS) et/ou microservices serverless basés sur Azure Functions. |
| **Cible de données** |
| SQL ou n’importe quelle base de données relationnelle sur une machine virtuelle | Azure SQL Database Managed Instance ou autre base de données managée dans le cloud. | Bases de données affinées par microservice, basées sur Azure SQL Database, Azure Cosmos DB ou autre base de données managée dans le cloud |
| **Avantages**|
| <li>Pas de refonte de l’architecture, pas de nouveau code <li> Moins de travail pour une migration rapide <li> Plus petit dénominateur commun pris en charge dans Azure <li> Garanties de disponibilité de base <li> Après être passé au cloud, il est plus facile de moderniser encore plus | <li> Aucune refonte de l’architecture <li> Changements de code/configuration minimes <li> Déploiement amélioré et meilleure agilité de DevOps pour la production de nouvelles versions grâce aux conteneurs <li> Densité accrue et coûts de déploiement inférieurs <li> Portabilité des applications et des dépendances <li> Flexibilité des cibles hôtes : PaaS s’approche ou IaaS | <li> Architecte pour le cloud, vous bénéficiez des meilleurs avantages du cloud, mais un nouveau code est nécessaire <li> Approches natives pour le cloud avec des microservices <li> Applications stratégiques modernes, résilientes au cloud et hyper-scalables <li> Services entièrement gérés <li> Optimisé pour la mise à l’échelle <li> Optimisé pour une agilité autonome par sous-système <li> S’appuyant sur le déploiement et sur DevOps |
| **Défis** |
| <li> Valeur cloud inférieure, autre que la variation des dépenses d’exploitation ou la fermeture de centres de données <li> Peu est géré: Pas de système d’exploitation ou de patching middleware; pourrait utiliser des solutions d’infrastructure, comme Terraform, Spinnaker ou Puppet | <li> La conteneurisation est une étape supplémentaire dans le processus d’apprentissage pour les développeurs et les opérations informatiques <li> Les pipelines DevOps et CI/CD sont généralement « indispensables » à cette approche. Si actuellement absent de la culture de l’organisation, risque d’être une difficulté supplémentaire| <li> Nécessite une réarchitecture pour les applications cloud natives et les architectures de microservices, plus généralement une refactorisation de code importante ou une réécriture lors de la modernisation (augmentation du temps et du budget)|
> **Tableau 1-1.** Avantages et difficultés éventuelles des parcours de modernisation pour les applications et les services .NET existants

### <a name="key-technologies-and-architectures-by-maturity-level"></a>Technologies et architectures principales par niveau de maturité

Au départ, les applications .NET Framework démarraient avec le .NET Framework version 1.0, qui a été publié fin 2001. Ensuite, les entreprises sont passées à des versions plus récentes (comme 2.0, 3.5 et .NET 4.x). La plupart de ces applications s’exécutaient sur Windows Server et IIS (Internet Information Server), et utilisaient une base de données relationnelle, comme SQL Server, Oracle, MySQL ou n’importe quel autre SGBDR.

La plupart des applications .NET existantes sont probablement basées sur le .NET Framework 4.x, ou même sur le .NET Framework 3.5, et elles utilisent des frameworks web, comme ASP.NET MVC, ASP.NET Web Forms, ASP.NET Web API, WCF (Windows Communication Foundation), ASP.NET SignalR et ASP.NET Web Pages. Ces technologies .NET Framework répandues dépendent de Windows. Cette dépendance est importante à prendre en compte si vous effectuez simplement une migration d’applications héritées et que vous voulez apporter le moins de modifications possible à votre infrastructure d’application.

La figure 1-2 montre les technologies et les styles d’architecture principaux utilisés pour chacun des trois niveaux de maturité cloud :

![Technologies principales pour chaque niveau de maturité pour la modernisation d’applications web .NET existantes](./media/image1-2.png)

**Figure 1-2.** Technologies principales pour chaque niveau de maturité pour la modernisation d’applications web .NET existantes

La figure 1-2 met en évidence les scénarios les plus courants, mais de nombreuses variations hybrides et mixtes sont possibles concernant l’architecture. Par exemple, les modèles de maturité s’appliquent non seulement aux architectures monolithiques dans les applications web existantes, mais aussi à l’orientation service, au multiniveau et à d’autres variations du style d’architecture. L’intérêt ou le pourcentage plus élevé sur un type d’architecture ou un autre et les technologies associées déterminent le niveau de maturité global de vos applications.

Chaque niveau de maturité du processus de modernisation est associé aux technologies et aux approches principales suivantes :

- **Cloud Infrastructure-Ready** (rehost ou ascenseur de base & décalage) : Dans un premier temps, de nombreuses organisations ne veulent qu’exécuter rapidement une stratégie de migration du cloud. Dans ce cas, les applications sont réhébergées. La plus grande partie du réhébergement peut être automatisée avec [Azure Migrate](https://aka.ms/azuremigrate), service qui fournit de l’aide, des insights et les mécanismes nécessaires pour vous aider à migrer vers Azure, basé sur des outils cloud comme [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/) et [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/). Vous pouvez également configurer manuellement le réhébergement, ce qui vous permet de découvrir des détails d’infrastructure sur vos ressources quand vous déplacez des applications héritées dans le cloud. Par exemple, vous pouvez déplacer vos applications vers des machines virtuelles dans Azure avec peu de modifications, probablement avec juste des changements de configuration mineurs. La mise en réseau est dans ce cas similaire à un environnement local, en particulier si vous créez des réseaux virtuels dans Azure.

- **Cloud-Optimized** (Managed Services and Windows Containers): Ce modèle vise à faire quelques optimisations de déploiement importantes pour tirer des avantages significatifs du cloud, sans changer l’architecture de base de l’application. Le principal est ici d’ajouter la prise en charge des [conteneurs Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) à vos applications .NET Framework existantes. Cette étape importante (conteneurisation) ne demande pas de toucher au code, donc l’effort global de lift-and-shift est léger. Vous pouvez utiliser des outils comme [Image2Docker](https://github.com/docker/communitytools-image2docker-win) ou Visual Studio, avec ses outils pour [Docker](https://www.docker.com/). Visual Studio choisit automatiquement des valeurs par défaut adaptées pour les applications ASP.NET et les images de conteneurs Windows. Ces outils permettent à la fois une boucle interne rapide et une voie rapide pour placer les conteneurs dans Azure. Votre agilité est améliorée quand vous déployez sur plusieurs environnements.
Ensuite, en passant en production, vous pouvez déployer vos conteneurs Windows sur [Azure Web App pour conteneurs](https://azure.microsoft.com/services/app-service/containers/), [Azure Container instances (ACI)](https://azure.microsoft.com/services/container-instances/) et des machines virtuelles Azure avec Windows Server 2016 et des conteneurs, si vous préférez une approche IaaS. Pour les applications multiconteneurs plus complexes, envisagez d’utiliser des orchestrateurs comme [Azure Kubernetes Service (AKS/ACS)](https://azure.microsoft.com/services/container-service/).

Au cours de cette première modernisation, vous pouvez également ajouter des ressources provenant du cloud, comme la supervision avec des outils comme [Azure Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview), des pipelines CI/CD pour les cycles de vie de votre application avec [Azure DevOps Services](https://azure.microsoft.com/services/devops/),et de nombreux autres services de ressources de données qui sont disponibles dans Azure. Par exemple, vous pouvez modifier une application web monolithique qui a été développée à l’origine avec les composants classiques [ASP.NET Web Forms](https://www.asp.net/web-forms) ou [ASP.NET MVC](https://www.asp.net/mvc), mais vous la déployez maintenant en utilisant des conteneurs Windows. Quand vous utilisez des conteneurs Windows, vous devez également migrer vos données vers une base de données qui se trouve dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/), le tout sans modifier l’architecture principale de votre application.

- **Cloud-Native**: Tel qu’introduit, vous devriez penser à l’architecture d’applications [cloud-native](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) lorsque vous ciblez des applications grandes et complexes avec plusieurs équipes de développement indépendantes travaillant sur différents microservices qui peuvent être développés et déployés de manière autonome. Aussi, en raison d’une scalabilité affinée et indépendante par microservice. Ces approches architecturales font face à des difficultés et des complexités très importantes, mais peuvent être considérablement simplifiées à l’aide d’un PaaS cloud et d’orchestrateurs comme [Azure Kubernetes Service (AKS/ACS)](https://azure.microsoft.com/services/container-service/) (Kubernetes managé) et [Azure Functions](https://azure.microsoft.com/services/functions/) pour une approche serverless. Toutes ces approches (comme les microservices et serverless) vous demandent de créer une architecture pour le cloud et d’écrire un nouveau code—du code adapté à des plateformes PaaS spécifiques ou du code qui s’aligne sur des architectures spécifiques, comme les microservices.

La figure 1-3 montre les technologies internes que vous pouvez utiliser pour chaque niveau de maturité :

![Technologies internes pour chaque niveau de maturité de modernisation](./media/image1-3.png)

**Figure 1-3.** Technologies internes pour chaque niveau de maturité de modernisation

## <a name="lift-and-shift-scenario"></a>Scénario de lift-and-shift

Pour les migrations de type lift-and-shift, gardez à l’esprit que vous pouvez utiliser de nombreuses variations de lift-and-shift différentes dans vos scénarios d’application. Si vous réhébergez seulement votre application, vous pouvez avoir un scénario semblable à celui illustré dans la Figure 1-4, où vous utilisez des machines virtuelles dans le cloud seulement pour votre application et pour votre serveur de base de données.

![Exemple de scénario IaaS pur dans le cloud](./media/image1-4.png)

**Figure 1-4**. Exemple de scénario IaaS pur dans le cloud

## <a name="modernization-scenarios"></a>Scénarios de modernisation

Pour les scénarios de modernisation, vous avez probablement une application optimisée pour le cloud pure qui utilise seulement des éléments de ce niveau de maturité. Vous pouvez aussi avoir une application dans un état intermédiaire avec quelques éléments au niveau Prêt pour l’infrastructure cloud et d’autres éléments au niveau Optimisé pour le cloud (un modèle par sélection ou mixte), comme dans la figure 1-5.

![Exemple de scénario « par sélection », avec une base de données sur IaaS, DevOps et des ressources de mise en conteneur](./media/image1-5.png)

**Figure 1-5.** Exemple de scénario « par sélection », avec une base de données sur IaaS, DevOps et des ressources de mise en conteneur

Ensuite, comme scénario idéal pour de nombreuses applications .NET Framework existantes à migrer, vous pouvez migrer vers une application optimisée pour le cloud pour obtenir des avantages significatifs avec peu de travail. Cette approche vous permet aussi d’être prêt pour Cloud natif comme éventuelle évolution future. La figure 1-6 en montre un exemple.

![Exemple de scénario d’applications Optimisées pour le cloud, avec des conteneurs Windows et des services managés](./media/image1-6.png)

**Figure 1-6.** Exemple de scénario d’applications Optimisées pour le cloud, avec des conteneurs Windows et des services managés

Pour aller encore plus loin, vous pouvez étendre votre application Optimisée pour le cloud en ajoutant quelques microservices pour des scénarios spécifiques. Ainsi, vous accéderiez partiellement au niveau du modèle Cloud natif, qui n’est pas le sujet central du présent guide.

## <a name="what-this-guide-does-not-cover"></a>Sujets non abordés dans ce guide

Ce guide couvre un sous-ensemble spécifique des exemples de scénarios, comme le montre la figure 1-7. Il est axé sur les scénarios de lift-and-shift pour arriver au final au modèle Optimisé pour le cloud. Dans le modèle Optimisé pour le cloud, une application .NET Framework est modernisée avec des conteneurs Windows, plus d’autres composants comme la supervision et les pipelines Ci/CD. Chaque composant est fondamental pour permettre un déploiement plus rapide et agile des applications dans le cloud.

![Cloud natif n’est pas abordé dans ce guide.](./media/image1-7.png)

**Figure 1-7.** Cloud natif n’est pas abordé dans ce guide.

L’objet principal de ce guide est spécifique. Il vous montre le cheminement à suivre pour effectuer un lift-and-shift de vos applications .NET existantes, sans refonte de l’architecture ni modification du code. Enfin, il vous montre comment rendre votre application Optimisée pour le cloud.

Ce guide ne vous montre pas comment créer des applications cloud natives, par exemple comment évoluer vers une architecture de microservices. Pour réarchiler vos applications ou pour créer de toutes nouvelles applications basées sur des microservices, consultez le livre électronique [.NET Microservices: Architecture pour les applications .NET conteneurisées](https://aka.ms/microservicesebook).

### <a name="additional-resources"></a>Ressources supplémentaires

- **Cycle de vie de l’application Docker conteneurisé avec la plate-forme et les outils Microsoft** (e-book téléchargeable)
  <https://aka.ms/dockerlifecycleebook>

- **.NET Microservices: Architecture pour les applications conteneurisées .NET** (téléchargement e-book)
  <https://aka.ms/microservicesebook>

- **Architecture des applications web modernes avec ASP.NET Core et Azure** (livre électronique téléchargeable) \
  <https://aka.ms/webappebook>

## <a name="who-should-use-this-guide"></a>Public visé par ce guide

Ce guide a été écrit pour les développeurs et les architectes de solutions qui veulent moderniser des applications web ASP.NET ou des services WCF existants basés sur le .NET Framework, de façon à obtenir une meilleure agilité dans la livraison des applications.

Ce guide peut être utile également si vous êtes décideur informatique, par exemple architecte d’entreprise ou responsable du développement, et souhaitez seulement une vue d’ensemble des bénéfices que vous pouvez obtenir en utilisant des conteneurs Windows et en déployant sur le cloud si vous utilisez Microsoft Azure.

## <a name="how-to-use-this-guide"></a>Comment utiliser ce guide

Ce guide répond à la question « pourquoi » : pourquoi il peut être souhaitable de moderniser vos applications existantes. Il explique aussi quels sont les bénéfices procurés par l’utilisation des conteneurs Windows quand vous déplacez vos applications dans le cloud. Le contenu des premiers chapitres du guide est conçu pour les architectes et les décideurs informatiques qui veulent une vue d’ensemble, mais qui n’ont pas besoin d’informations techniques détaillées sur le processus d’implémentation.

Le dernier chapitre de ce guide contient plusieurs procédures pas à pas centrées sur des scénarios de déploiement spécifiques. Ce guide offre des versions plus courtes des procédures pas à pas, qui résument les scénarios et mettent en avant leurs avantages. Les procédures pas à pas complètes détaillent la configuration et l’implémentation. Elles sont publiées sous la forme d’un ensemble de [billets wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki) dans le [dépôt GitHub](https://github.com/dotnet-architecture/eShopModernizing) où vous trouvez aussi des exemples d’applications associées (présentées dans la section suivante). Le dernier chapitre et les procédures pas à pas du wiki sur GitHub sont plus intéressants pour les développeurs et les architectes qui veulent connaître les détails d’implémentation.

## <a name="sample-apps-for-modernizing-legacy-apps-eshopmodernizing"></a>Exemples d’applications pour la modernisation d’applications héritées : eShopModernizing

Le dépôt [eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing) sur GitHub contient deux exemples d’applications qui simulent des applications web monolithiques héritées. La première application web est développée à l’aide d’ASP.NET MVC ; la deuxième application web est développée à l’aide d’ASP.NET Web Forms et la troisième est une application multiniveau avec une application de bureau client WinForms utilisant un back-end de service WCF. Toutes ces applications sont basées sur le .NET Framework classique. Ces exemples d’applications n’utilisent pas .NET Core ou ASP.NET Core, car elles sont supposées être des applications .NET Framework existantes/héritées à moderniser.

Ces exemples d’applications ont une seconde version, avec le code modernisé, et sont assez simples. La différence la plus importante entre les versions des applications est que leur seconde version utilise les conteneurs Windows comme choix de déploiement. Quelques ajouts ont été apportés aux secondes versions, comme des objets blob Stockage Azure pour la gestion des images, Azure Active Directory pour la gestion de la sécurité et Azure Application Insights pour la surveillance et l’audit des applications.

## <a name="send-your-feedback"></a>Envoyez votre feedback

Ce guide a été écrit pour vous aider à comprendre les options dont vous disposez pour améliorer et moderniser des applications web .NET existantes. Le guide et les exemples d’applications associés sont en constante évolution. Vos commentaires sont les bienvenus. Si vous avez des commentaires sur la façon dont [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book)ce guide pourrait être plus utile, s’il vous plaît envoyez-les à .

>[!div class="step-by-step"]
>[Suivant](lift-and-shift-existing-apps-azure-iaas.md) <!-- Next Chapter -->
