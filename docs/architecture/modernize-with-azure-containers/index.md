---
title: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure (2e édition)
description: Apprenez à déplacer et à moderniser les applications existantes dans le Cloud Azure et les conteneurs avec ce livre électronique.
ms.date: 04/28/2018
ms.openlocfilehash: ab2b58441af7aed6a8cd868751339b555a345565
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "70222843"
---
# <a name="modernize-existing-net-applications-with-azure-cloud-and-windows-containers-2nd-edition"></a>Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure (2e édition)

![Image de couverture du Guide des applications .NET de Modernis.](./media/index/web-application-guide-cover-image.png)

PUBLIÉ PAR  
Microsoft Press et Microsoft DevDiv  
Divisions de Microsoft Corporation  
One Microsoft Way  
Redmond, Washington 98052-6399  

Copyright © 2018 Microsoft Corporation  

Tous droits réservés. Aucune partie du contenu de ce document ne peut être reproduite sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.

Ce livre est disponible gratuitement sous la forme d’un livre électronique (livre électronique) disponible sur plusieurs canaux chez Microsoft, par exemple <https://dot.net/architecture>.

Si vous avez des questions liées à cet ouvrage, envoyez un e-mail à [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book)

Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur. Les vues, les opinions et les informations exprimées dans ce livre, y compris les URL et autres références à des sites Web Internet, peuvent changer sans préavis.

Certains exemples décrits dans ce document ne sont fournis qu’à titre d’illustration et sont purement fictifs. Toute ressemblance ou tout lien avec le monde réel sont purement fortuits et involontaires.

Microsoft et les marques commerciales mentionnées dans la page web « Marques » sur <https://www.microsoft.com> sont des marques du groupe Microsoft. Toutes les autres marques sont la propriété de leurs propriétaires respectifs.

Auteur :
> **Cesar de la Torre**, SR. pm, équipe du produit .net, Microsoft Corp.

Participants et réviseurs :
> **Scott Hunter**, chef de projet directeur partenaire, équipe .NET, Microsoft  
> **Paul Yuknewicz**, chef de projet responsable principal, équipe Visual Studio Tools, Microsoft  
> **Lisa Guthrie**, SR. PM, Visual Studio Tools Team, Microsoft  
> **Ankit Asthana**, responsable principal de la gestion de projets, équipe .NET, Microsoft  
> **Unai Zorrilla**, développeur en chef, Plain Concepts  
> **Javier Valero**, chef des opérations chez Grupo Solutio  

## <a name="introduction"></a>Présentation

Lorsque vous décidez de moderniser vos applications ou services Web et de les déplacer vers le Cloud, vous ne devez pas nécessairement remanier entièrement vos applications. Le remaniement de l’architecture d’une application à l’aide d’une approche avancée comme les microservices n’est pas toujours une option en raison des restrictions de coûts et de temps. Selon le type d’application, il est également possible que le remaniement d’une application ne soit pas nécessaire. Pour optimiser la rentabilité de la stratégie de migration vers le cloud de votre organisation, il est important de prendre en compte les besoins de votre activité et les exigences de vos applications. Vous devez déterminer :

- Les applications qui requièrent une transformation ou une reconception.

- Les applications qui doivent être modernisées seulement en partie.

- Les applications pouvant faire l’objet d’un lift-and-shift directement dans le cloud.

## <a name="about-this-guide"></a>À propos de ce guide

Ce guide se concentre principalement sur la modernisation initiale des applications Web ou orientées service existantes de Microsoft .NET Framework, ce qui signifie que l’action consiste à déplacer une charge de travail vers un environnement plus récent ou plus moderne sans altérer significativement le code de l’application et l’architecture de base. 

Ce guide souligne également les avantages du déplacement de vos applications dans le Cloud et de la modernisation partielle des applications à l’aide d’un ensemble spécifique de nouvelles technologies et approches, comme les conteneurs Windows et les plateformes de calcul associées dans Azure prenant en charge les conteneurs Windows.

## <a name="path-to-the-cloud-for-existing-net-applications"></a>Déplacement vers le cloud des applications .NET existantes

En règle générale, les organisations choisissent de passer au cloud pour apporter souplesse et rapidité à leurs applications. Vous pouvez configurer des milliers de serveurs (des machines virtuelles) dans le cloud en quelques minutes, en comparaison aux semaines généralement nécessaires pour configurer des serveurs locaux.

Il n’existe pas de stratégie unique et universelle pour migrer des applications dans le cloud. La bonne stratégie de migration pour vous dépend des besoins et des priorités de votre organisation, ainsi que du type des applications que vous migrez. Les applications ne justifient pas toutes l’investissement nécessaire pour passer à un modèle Paas ([plateforme en tant que service](https://azure.microsoft.com/overview/what-is-paas/)) ou pour développer un modèle d’application [natif pour le cloud](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications). Dans de nombreux cas, vous pouvez adopter une approche progressive ou incrémentielle quand vous investissez dans le déplacement de vos ressources sur le cloud, en fonction des besoins de votre entreprise.

Pour les applications modernes avec la meilleure agilité à long terme et la valeur ajoutée pour l’organisation, vous pouvez tirer parti de l’investissement dans les architectures d’application natives dans le *Cloud* . Toutefois, pour les applications qui sont des ressources existantes ou héritées, la clé consiste à consacrer un minimum de temps et d’argent (aucune modification de l’architecture ou du code) tout en les déplaçant vers le Cloud, afin de bénéficier d’avantages significatifs.

La figure 1-1 montre les voies possibles utilisables quand vous faites passer progressivement des applications .NET existantes dans le cloud.

 ![Voies de modernisation pour les applications et les services .NET existants](./media/image1-1.png)

> **Figure 1-1**. Voies de modernisation pour les applications et les services .NET existants

Chaque approche de la migration présente des avantages différents et est utilisée pour des raisons différentes. Vous pouvez choisir une même approche quand vous migrez des applications vers le cloud, ou choisir certains composants provenant de plusieurs approches. Les applications individuelles ne sont pas limitées à une seule approche ou à un seul état de maturité. Par exemple, une approche hybride courante consiste à avoir certains des composants en local et d’autres composants dans le cloud.

La définition et une brève explication pour chaque niveau de maturité de l’application sont les suivantes:

**Niveau 1: Applications prêtes** pour l’infrastructure cloud: Dans cette approche de migration, vous migrez ou réhébergez simplement vos applications locales actuelles sur une plateforme infrastructure as a service ([IaaS](https://azure.microsoft.com/overview/what-is-iaas/)). Vos applications ont pratiquement la même composition qu’avant, mais vous les déployez désormais sur des machines virtuelles dans le cloud.
Ce type de migration simple est généralement connu sous le nom de «ascenseur & Shift».

**Niveau 2: Applications optimisées** pour le Cloud: À ce niveau et sans avoir à remanier le code significatif, vous pouvez tirer des avantages supplémentaires de l’exécution de votre application dans le Cloud avec des technologies modernes telles que des conteneurs et des services gérés dans le Cloud supplémentaires. Vous améliorez l’agilité de vos applications pour les livrer plus rapidement, en affinant les processus de fonctionnement du développement (DevOps) dans votre entreprise. Pour ce faire, vous utilisez des technologies comme les conteneurs Windows, qui sont basées sur le moteur de l’ancrage. Les conteneurs suppriment les frottements provoqués par les dépendances des applications lorsque vous déployez en plusieurs étapes. Dans ce modèle de maturité, vous pouvez déployer des conteneurs sur IaaS ou PaaS tout en utilisant des services gérés par le Cloud supplémentaires liés aux bases de données, au cache en tant que service, à la surveillance et aux pipelines d’intégration continue/de déploiement continu (CI/CD).

Le troisième niveau de maturité est l’objectif ultime dans le cloud, mais il est facultatif pour de nombreuses applications et ne constitue pas l’objet principal de ce guide :

**Niveau 3: Applications Cloud natives** : Cette approche de migration est généralement motivée par les besoins de l’entreprise et par les cibles de la modernisation de vos applications stratégiques. À ce niveau, vous utilisez des services PaaS pour passer vos applications sur des plateformes informatiques PaaS. Vous implémentez des applications et une architecture de microservices [natives pour le cloud](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) pour faire évoluer les applications avec une agilité à long terme et pour les adapter à de nouvelles limites. Ce type de modernisation nécessite généralement une architecture spécifique pour le cloud. Du nouveau code doit souvent être écrit, en particulier quand vous passez à des modèles d’application natifs pour le cloud et basés sur des microservices. Cette approche peut vous aider à profiter d’avantages difficiles à obtenir dans votre environnement applicatif monolithique et local.

Le tableau 1-1 décrit les principaux avantages et les raisons de choisir chaque approche de migration ou de modernisation.

| **Prêt pour l’infrastructure cloud** <br /> *Lift-and-shift* | **Optimisé pour le Cloud** <br /> *Moderniser* | **Cloud-Native** <br /> *Moderniser, remanier et réécrire* |
|---|---|---|
| **Cible informatique de l’application** |
| Applications déployées sur des machines virtuelles dans Azure | Applications monolithiques ou multicouches déployées sur Azure App Service, Azure Container instance (ACI), machines virtuelles avec conteneurs ou AKS (service Kubernetes Azure) | Microservices en conteneur sur Azure Kubernetes service (AKS) et/ou les microservices sans serveur basés sur Azure Functions. |
| **Cible de données** |
| SQL ou n’importe quelle base de données relationnelle sur une machine virtuelle | Azure SQL Database Managed Instance ou une autre base de données gérée dans le Cloud. | Bases de données affinées par Microservice, basées sur Azure SQL Database, Azure Cosmos DB ou une autre base de données gérée dans le Cloud |
| **Avantages**|
| <li>Aucune remaniement, aucun nouveau code <li> Moins de travail pour une migration rapide <li> Plus petit dénominateur commun pris en charge dans Azure <li> Garanties de disponibilité de base <li> Après être passé au cloud, il est plus facile de moderniser encore plus | <li> Aucune remaniement <li> Nombre minimal de modifications de code/configuration <li> Déploiement amélioré et meilleure agilité de DevOps pour la production de nouvelles versions grâce aux conteneurs <li> Densité accrue et coûts de déploiement inférieurs <li> Portabilité des applications et des dépendances <li> Flexibilité des cibles de l’hôte: Approches PaaS ou IaaS | <li> Architecte pour le Cloud, vous bénéficiez des meilleurs avantages du Cloud, mais vous avez besoin d’un nouveau code <li> Approches natives pour le cloud avec des microservices <li> Applications stratégiques modernes, hyper-Scalable résistant au Cloud <li> Services entièrement gérés <li> Optimisé pour la mise à l’échelle <li> Optimisé pour une agilité autonome par sous-système <li> S’appuyant sur le déploiement et sur DevOps |
| **Difficultés éventuelles** |
| <li> Valeur cloud inférieure, autre que la variation des dépenses d’exploitation ou la fermeture de centres de données <li> Peu géré: Aucune mise à jour corrective du système d’exploitation ou du middleware; peut utiliser des solutions d’infrastructure, telles que Terraform, Spinnaker ou marionnette | <li> La mise en conteneur est une étape supplémentaire dans la courbe d’apprentissage pour les développeurs et les opérations informatiques <li> Les pipelines DevOps et CI/CD sont généralement «un doit» pour cette approche. S’il n’est pas actuellement présent dans la culture de l’organisation, il peut s’agir d’un défi supplémentaire.| <li> Nécessite une rearchitecture pour les applications Cloud natives et les architectures de microservices et nécessite généralement une refactorisation de code importante ou une réécriture lors de la modernisation (augmentation du temps et du budget)|
> **Tableau 1-1.** Avantages et difficultés éventuelles des parcours de modernisation pour les applications et les services .NET existants

### <a name="key-technologies-and-architectures-by-maturity-level"></a>Technologies et architectures principales par niveau de maturité

Au départ, les applications .NET Framework démarraient avec le .NET Framework version 1.0, qui a été publié fin 2001. Ensuite, les entreprises sont passées à des versions plus récentes (comme 2.0, 3.5 et .NET 4.x). La plupart de ces applications s’exécutaient sur Windows Server et Internet Information Server (IIS) et utilisaient une base de données relationnelle, comme SQL Server, Oracle, MySQL ou tout autre SGBDR.

La plupart des applications .NET existantes sont probablement basées sur le .NET Framework 4.x, ou même sur le .NET Framework 3.5, et elles utilisent des frameworks web, comme ASP.NET MVC, ASP.NET Web Forms, ASP.NET Web API, WCF (Windows Communication Foundation), ASP.NET SignalR et ASP.NET Web Pages. Ces technologies .NET Framework répandues dépendent de Windows. Cette dépendance est importante à prendre en compte si vous effectuez simplement une migration d’applications héritées et que vous voulez apporter le moins de modifications possible à votre infrastructure d’application.

La figure 1-2 montre les technologies et les styles d’architecture principaux utilisés pour chacun des trois niveaux de maturité cloud :

![Technologies principales pour chaque niveau de maturité pour la modernisation d’applications web .NET existantes](./media/image1-2.png)

> **Figure 1-2.** Technologies principales pour chaque niveau de maturité pour la modernisation d’applications web .NET existantes

La figure 1-2 met en évidence les scénarios les plus courants, mais de nombreuses variations hybrides et mixtes sont possibles concernant l’architecture. Par exemple, les modèles de maturité s’appliquent non seulement aux architectures monolithiques dans les applications web existantes, mais aussi à l’orientation service, au multiniveau et à d’autres variations du style d’architecture. La concentration ou le pourcentage plus élevés sur un type d’architecture ou sur un autre et les technologies associées déterminent le niveau de maturité global de vos applications.

Chaque niveau de maturité du processus de modernisation est associé aux technologies et aux approches principales suivantes :

- **Prêt pour l’infrastructure cloud** (réhébergement ou élévation de base & Shift): Dans un premier temps, de nombreuses organisations veulent uniquement exécuter rapidement une stratégie de migration Cloud. Dans ce cas, les applications sont réhébergées. La plus grande partie du réhébergement peut être automatisée avec [Azure Migrate](https://aka.ms/azuremigrate), service qui fournit de l’aide, des insights et les mécanismes nécessaires pour vous aider à migrer vers Azure, basé sur des outils cloud comme [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/) et [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/). Vous pouvez également configurer manuellement le réhébergement, ce qui vous permet de découvrir des détails d’infrastructure sur vos ressources quand vous déplacez des applications héritées dans le cloud. Par exemple, vous pouvez déplacer vos applications vers des machines virtuelles dans Azure avec peu de modifications, probablement avec uniquement des modifications mineures de la configuration. La mise en réseau est dans ce cas similaire à un environnement local, en particulier si vous créez des réseaux virtuels dans Azure.

- **Optimisé pour le Cloud** (Services managés et conteneurs Windows): Ce modèle consiste à effectuer quelques optimisations de déploiement importantes pour tirer des avantages significatifs du Cloud, sans modifier l’architecture de base de l’application. Le principal est ici d’ajouter la prise en charge des [conteneurs Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) à vos applications .NET Framework existantes. Cette étape importante (conteneur) ne nécessite pas le toucher du code, de sorte que l’effort global d’élévation et de déplacement est clair. Vous pouvez utiliser des outils comme [Image2Docker](https://github.com/docker/communitytools-image2docker-win) ou Visual Studio, avec ses outils pour [Docker](https://www.docker.com/). Visual Studio choisit automatiquement des valeurs par défaut adaptées pour les applications ASP.NET et les images de conteneurs Windows. Ces outils permettent à la fois une boucle interne rapide et une voie rapide pour placer les conteneurs dans Azure. Votre agilité est améliorée quand vous déployez sur plusieurs environnements. Ensuite, en passant à la production, vous pouvez déployer vos conteneurs Windows sur [azure Web App pour conteneurs](https://azure.microsoft.com/services/app-service/containers/), [Azure Container instances (ACI)](https://azure.microsoft.com/services/container-instances/)et les machines virtuelles azure avec Windows Server 2016 et les conteneurs si vous préférez une approche IaaS. Pour les applications à plusieurs conteneurs plus complexes, envisagez d’utiliser des orchestrateurs comme [Azure Kubernetes service (AKS/ACS)](https://azure.microsoft.com/services/container-service/). 

Au cours de cette modernisation initiale, vous pouvez également ajouter des ressources à partir du Cloud, telles que la surveillance avec des outils tels que [Azure application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview). Pipelines CI/CD pour le cycle de vie de vos applications avec [Azure DevOps services](https://azure.microsoft.com/services/devops/); et de nombreux autres services de ressources de données disponibles dans Azure. Par exemple, vous pouvez modifier une application web monolithique qui a été développée à l’origine avec les composants classiques [ASP.NET Web Forms](https://www.asp.net/web-forms) ou [ASP.NET MVC](https://www.asp.net/mvc), mais vous la déployez maintenant en utilisant des conteneurs Windows. Quand vous utilisez des conteneurs Windows, vous devez également migrer vos données vers une base de données qui se trouve dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/), le tout sans modifier l’architecture principale de votre application.

- **Cloud-natif**: Comme nous l’avons vu, vous devez envisager de concevoir des applications [Cloud natives](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) lorsque vous ciblez des applications volumineuses et complexes avec plusieurs équipes de développement indépendantes qui travaillent sur différents microservices qui peuvent être développés et déployés. façon autonome. En outre, en raison de l’extensibilité granulaire et indépendante par Microservice. Ces approches architecturales font face à des défis et des complexités très importants, mais peuvent être considérablement simplifiés à l’aide du PaaS Cloud et des orchestrateurs comme [Azure Kubernetes service (AKS/ACS)](https://azure.microsoft.com/services/container-service/) (Managed Kubernetes) et [Azure Functions](https://azure.microsoft.com/services/functions/) pour un approche sans serveur. Toutes ces approches (telles que les microservices et sans serveur) requièrent généralement que vous conceviez le Cloud et écriviez du nouveau code, du code adapté à des plateformes PaaS spécifiques ou du code qui s’aligne sur des architectures spécifiques, comme les microservices.

La figure 1-3 montre les technologies internes que vous pouvez utiliser pour chaque niveau de maturité :

![Technologies internes pour chaque niveau de maturité de modernisation](./media/image1-3.png)

> **Figure 1-3.** Technologies internes pour chaque niveau de maturité de modernisation

## <a name="lift-and-shift-scenario"></a>Scénario d’élévation et de décalage

Pour les migrations de type lift-and-shift, gardez à l’esprit que vous pouvez utiliser de nombreuses variations de lift-and-shift différentes dans vos scénarios d’application. Si vous réhébergez seulement votre application, vous pouvez avoir un scénario semblable à celui illustré dans la Figure 1-4, où vous utilisez des machines virtuelles dans le cloud seulement pour votre application et pour votre serveur de base de données.

![Exemple de scénario IaaS pur dans le cloud](./media/image1-4.png)

> **Figure 1-4**. Exemple de scénario IaaS pur dans le cloud

## <a name="modernization-scenarios"></a>Scénarios de modernisation

Pour les scénarios de modernisation, vous pouvez avoir une application purement optimisée pour le Cloud qui utilise uniquement des éléments de ce niveau de maturité. Vous pouvez également disposer d’une application d’état intermédiaire avec certains éléments de l’infrastructure cloud, prêts à l’emploi et d’autres éléments à partir d’un environnement optimisé pour le Cloud (un «pick and choose» ou un modèle mixte), comme dans la figure 1-5.

![Exemple de scénario « par sélection », avec une base de données sur IaaS, DevOps et des ressources de mise en conteneur](./media/image1-5.png)

> **Figure 1-5.** Exemple de scénario « par sélection », avec une base de données sur IaaS, DevOps et des ressources de mise en conteneur

Ensuite, comme scénario idéal pour de nombreuses applications de .NET Framework existantes à migrer, vous pouvez migrer vers une application optimisée pour le Cloud, afin d’obtenir des avantages significatifs par rapport à un travail minime. Cette approche vous permet également de définir le Cloud-Native comme une évolution possible. La figure 1-6 en montre un exemple.

![Exemple de scénario d’applications optimisées pour le Cloud, avec des conteneurs Windows et des services gérés](./media/image1-6.png)

> **Figure 1-6.** Exemple de scénario d’applications optimisées pour le Cloud, avec des conteneurs Windows et des services gérés

Pour aller encore plus loin, vous pouvez étendre votre application optimisée pour le Cloud existante en ajoutant quelques microservices pour des scénarios spécifiques. Cela vous permet de vous déplacer partiellement vers le niveau de modèle natif du Cloud, ce qui n’est pas le principal objectif de ce guide.

## <a name="what-this-guide-does-not-cover"></a>Sujets non abordés dans ce guide

Ce guide couvre un sous-ensemble spécifique des exemples de scénarios, comme le montre la figure 1-7. Ce guide se concentre uniquement sur les scénarios d’élévation et de déplacement, et enfin sur le modèle optimisé pour le Cloud. Dans le modèle optimisé pour le Cloud, une application de .NET Framework est moderne à l’aide de conteneurs Windows, ainsi que des composants supplémentaires tels que des pipelines de surveillance et d’intégration continue/de CD. Chaque composant est fondamental pour permettre un déploiement plus rapide et agile des applications dans le cloud.

![Cloud-Native n’est pas abordé dans ce guide](./media/image1-7.png)

> **Figure 1-7.** Cloud-Native n’est pas abordé dans ce guide

L’objet principal de ce guide est spécifique. Il vous montre le chemin d’accès que vous pouvez suivre pour obtenir une élévation et un déplacement de vos applications .NET existantes, sans remaniement de l’architecture et sans modification du code. Enfin, il vous montre comment rendre votre application optimisée pour le Cloud.

Ce guide ne vous montre pas comment créer des applications Cloud natives, telles que la façon d’évoluer vers une architecture de microservices. Pour remanier vos applications ou pour créer de nouvelles applications basées sur des microservices, consultez les microservices .net du livre [électronique: Architecture pour les applications](https://aka.ms/microservicesebook).net en conteneur.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Cycle de vie des applications de l’arrimeur en conteneur avec la plateforme et les outils Microsoft** (livre électronique téléchargeable) \
  <https://aka.ms/dockerlifecycleebook>

- **Microservices .NET : Architecture pour les applications** .net en conteneur (livre électronique téléchargeable) \
  <https://aka.ms/microservicesebook>

- **Conception d’applications Web modernes avec ASP.net Core et Azure** (livre électronique téléchargeable) \
  <https://aka.ms/webappebook>

## <a name="who-should-use-this-guide"></a>Public visé par ce guide

Ce guide a été rédigé pour les développeurs et les architectes de solutions qui veulent moderniser les applications Web ASP.NET existantes ou les services WCF basés sur les .NET Framework, pour une plus grande agilité dans l’expédition et la publication d’applications.

Ce guide peut être utile également si vous êtes décideur informatique, par exemple architecte d’entreprise ou responsable du développement, et souhaitez seulement une vue d’ensemble des bénéfices que vous pouvez obtenir en utilisant des conteneurs Windows et en déployant sur le cloud si vous utilisez Microsoft Azure.

## <a name="how-to-use-this-guide"></a>Comment utiliser ce guide

Ce guide répond à la question « pourquoi » : pourquoi il peut être souhaitable de moderniser vos applications existantes. Il explique aussi quels sont les bénéfices procurés par l’utilisation des conteneurs Windows quand vous déplacez vos applications dans le cloud. Le contenu des premiers chapitres du guide est conçu pour les architectes et les décideurs informatiques qui veulent une vue d’ensemble, mais qui n’ont pas besoin d’informations techniques détaillées sur le processus d’implémentation.

Le dernier chapitre de ce guide contient plusieurs procédures pas à pas centrées sur des scénarios de déploiement spécifiques. Ce guide propose des versions plus courtes des procédures pas à pas, pour résumer les scénarios et mettre en évidence leurs avantages. Les procédures pas à pas complètes détaillent la configuration et l’implémentation. Elles sont publiées sous la forme d’un ensemble de [billets wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki) dans le [dépôt GitHub](https://github.com/dotnet-architecture/eShopModernizing) où vous trouvez aussi des exemples d’applications associées (présentées dans la section suivante). Le dernier chapitre et les procédures pas à pas du wiki sur GitHub sont plus intéressants pour les développeurs et les architectes qui veulent connaître les détails d’implémentation.

## <a name="sample-apps-for-modernizing-legacy-apps-eshopmodernizing"></a>Exemples d’applications pour la modernisation d’applications héritées : eShopModernizing

Le dépôt [eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing) sur GitHub contient deux exemples d’applications qui simulent des applications web monolithiques héritées. Une application Web est développée à l’aide de ASP.NET MVC. la deuxième application Web est développée à l’aide de ASP.NET Web Forms et la troisième application est une application multiniveau avec une application de bureau client WinForms utilisant un backend de service WCF. Toutes ces applications sont basées sur le .NET Framework traditionnel. Ces exemples d’applications n’utilisent pas .NET Core ou ASP.NET Core, car elles sont supposées être des applications .NET Framework existantes/héritées à moderniser.

Ces exemples d’applications ont une deuxième version, avec du code moderne, et qui sont relativement simples. La différence la plus importante entre les versions des applications est que leur seconde version utilise les conteneurs Windows comme choix de déploiement. Quelques ajouts ont été apportés aux secondes versions, comme des objets blob Stockage Azure pour la gestion des images, Azure Active Directory pour la gestion de la sécurité et Azure Application Insights pour la surveillance et l’audit des applications.

## <a name="send-your-feedback"></a>Envoyez votre feedback

Ce guide a été rédigé pour vous aider à comprendre vos options pour améliorer et moderniser des applications Web .NET existantes. Le guide et les exemples d’applications associés sont en constante évolution. Vos commentaires sont les bienvenus! Si vous avez des commentaires à formuler sur la façon dont ce guide peut être amélioré, envoyez-les à l’adresse : [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book).

>[!div class="step-by-step"]
>[Next](lift-and-shift-existing-apps-azure-iaas.md) <!-- Next Chapter -->
