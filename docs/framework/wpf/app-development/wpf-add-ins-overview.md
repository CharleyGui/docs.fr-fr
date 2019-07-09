---
title: Vue d'ensemble des compléments WPF
ms.date: 03/30/2017
helpviewer_keywords:
- add-ins and XAML browser applications [WPF]
- add-ins overview [WPF]
- add-ins [WPF], performance
- add-ins [WPF], benefits
- .NET Framework add-in model [WPF]
- add-ins [WPF], user interface
- add-ins and the user interface [WPF]
- add-ins [WPF], architecture
- add-ins [WPF], limitations
ms.assetid: 00b4c776-29a8-4dba-b603-280a0cdc2ade
ms.openlocfilehash: 05e7c1558f37ac9f89b98bf3ac66379add10e66c
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664150"
---
# <a name="wpf-add-ins-overview"></a>Vue d'ensemble des compléments WPF

<a name="Introduction"></a> Le .NET Framework inclut un modèle de complément, qui permet aux développeurs de créer des applications qui prennent en charge d’extensibilité des compléments. Ce modèle de complément permet de créer des compléments qui s’intègrent aux applications et étendent leurs fonctionnalités. Dans certains scénarios, les applications doivent également afficher les interfaces utilisateur qui sont fournies par des compléments. Cette rubrique montre comment WPF étend le modèle de complément .NET Framework pour activer ces scénarios, l’architecture sous-jacente, ses avantages et ses limitations.

<a name="Requirements"></a>

## <a name="prerequisites"></a>Prérequis

Vous êtes familiarisé avec le modèle de complément .NET Framework est requise. Pour plus d’informations, consultez [Compléments et extensibilité](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).

<a name="AddInsOverview"></a>

## <a name="add-ins-overview"></a>Vue d’ensemble des compléments

Pour éviter la complexité des tâches de redéploiement et de recompilation des applications durant l’incorporation de nouvelles fonctionnalités, les applications offrent des mécanismes d’extensibilité qui permettent aux développeurs (aussi bien internes que tiers) de créer d’autres applications qui s’y intègrent. La méthode la plus répandue pour prendre en charge ce type d’extensibilité consiste à utiliser des compléments (également appelés « modules complémentaires », « extensions » et « plug-ins »). Voici quelques exemples d’applications réelles qui offrent une extensibilité à l’aide de compléments :

- modules complémentaires d’Internet Explorer ;

- plug-ins du Lecteur Windows Media ;

- compléments Visual Studio.

Par exemple, le modèle de complément du Lecteur Windows Media permet aux développeurs tiers d’implémenter des « plug-ins » pour étendre le Lecteur Windows Media de différentes façons, notamment en créant des décodeurs et encodeurs de formats multimédias non pris en charge en mode natif par le Lecteur Windows Media (DVD, MP3, par exemple), des effets audio et des apparences. Chaque modèle de complément est conçu pour exposer les fonctionnalités uniques d’une application, bien que plusieurs entités et comportements soient communs à tous les modèles de compléments.

Les trois principales entités de solutions d’extensibilité des compléments classiques sont les *contrats*, les *compléments* et les *applications hôtes*. Les contrats définissent la manière dont les compléments s’intègrent aux applications hôtes de deux manières :

- Les compléments s’intègrent aux fonctionnalités implémentées par les applications hôtes.

- Les applications hôtes exposent les fonctionnalités auxquelles les compléments peuvent s’intégrer.

Pour permettre l’utilisation des compléments, les applications hôtes doivent les rechercher et les charger au moment de l’exécution. Ainsi, les applications qui prennent en charge des compléments ont les responsabilités supplémentaires suivantes :

- **Découverte**: Recherche des compléments adhérant aux contrats pris en charge par les applications hôtes.

- **L’activation**: Le chargement en cours d’exécution et établissement de la communication avec des compléments.

- **Isolation**: À l’aide de domaines d’application ou de processus pour établir des limites d’isolation protégeant les applications de sécurité potentielle et problèmes d’exécution avec des compléments.

- **Communication**: Ce qui permet des compléments et héberger des applications de communiquer entre eux sur des limites d’isolement en appelant des méthodes et de passer des données.

- **Gestion de la durée de vie**: Chargement et déchargement des domaines d’application et les processus de façon propre et prévisible (consultez [domaines d’Application](../../app-domains/application-domains.md)).

- **Le contrôle de version**: S’assurer que héberger des applications et des compléments peuvent toujours communiquer lors de la création de nouvelles versions des.

Enfin, le développement d’un modèle de complément robuste est une tâche non négligeable. Pour cette raison, le .NET Framework fournit une infrastructure pour générer des modèles de complément.

> [!NOTE]
> Pour plus d’informations sur les compléments, consultez [Compléments et extensibilité](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).

<a name="NETFrameworkAddInModelOverview"></a>

## <a name="net-framework-add-in-model-overview"></a>Vue d’ensemble du modèle de complément du .NET Framework

Le .NET Framework-modèle de complément, trouvé dans le <xref:System.AddIn> espace de noms, contient un ensemble de types qui sont conçus pour simplifier le développement d’extensibilité du complément. L’unité fondamentale du modèle de complément .NET Framework est la *contrat*, qui définit comment une application hôte et un complément communiquent entre eux. Un contrat est exposé à une application hôte à l’aide d’une *vue* spécifique à l’application hôte du contrat. De même, une *vue* spécifique au complément du contrat est exposée au complément. Un *adaptateur* permet à une application hôte et à un complément de communiquer entre les vues respectives du contrat. Les contrats, les vues et les adaptateurs sont appelés des segments. Un ensemble de segments connexes constitue un *pipeline*. Les pipelines sont la Fondation sur laquelle le modèle de complément .NET Framework prend en charge la découverte, l’activation, isolation de sécurité, l’isolation d’exécution (à l’aide de domaines d’application et processus), communication, gestion de la durée de vie et le contrôle de version.

L’ensemble de cette prise en charge permet aux développeurs de générer des compléments qui s’intègrent aux fonctionnalités d’une application hôte. Toutefois, certains scénarios nécessitent des applications hôtes doivent afficher les interfaces utilisateur fournies par les compléments. Étant donné que chaque technologie de présentation dans le .NET Framework a son propre modèle pour l’implémentation des interfaces utilisateur, le modèle de complément .NET Framework ne prend pas en charge aucune technologie de présentation particulière. Au lieu de cela, WPF étend le modèle de complément .NET Framework avec prise en charge de l’interface utilisateur pour des compléments.

<a name="WPFAddInModel"></a>

## <a name="wpf-add-ins"></a>Compléments WPF

WPF, conjointement avec le .NET Framework-modèle de complément, vous permet de résoudre un large éventail de scénarios qui requièrent des applications hôtes doivent afficher des interfaces utilisateur à partir de compléments. En particulier, ces scénarios sont traités par WPF avec les deux modèles de programmation suivantes :

1. **Le complément retourne une IU (interface utilisateur)** . Un complément retourne une interface utilisateur à l’application hôte via un appel de méthode, tel que défini par le contrat. Ce scénario est utilisé dans les cas suivants :

    - L’apparence d’une interface utilisateur qui est retournée par un complément est dépend des données ou les conditions qui n’existent qu’au moment de l’exécution, telles que dynamiquement les rapports générés.

    - L’interface utilisateur pour les services fournis par un complément diffère de l’interface utilisateur des applications hôtes qui peuvent utiliser le complément.

    - Principalement le complément exécute un service pour l’application hôte et signale l’état à l’application hôte avec une interface utilisateur.

2. **Le complément est une interface utilisateur**. Un complément est une interface utilisateur, tel que défini par le contrat. Ce scénario est utilisé dans les cas suivants :

    - Un complément ne fournit pas d’autres services que celui d’être affiché, par exemple une publicité.

    - L’interface utilisateur des services fournis par un complément est commune à toutes les applications hôtes qui peuvent utiliser ce complément, par exemple une calculatrice ou un sélecteur de couleurs.

Ces scénarios requièrent que les objets de l’interface utilisateur peuvent être passés entre l’application hôte et les domaines d’application du complément. Depuis le modèle de complément s’appuie sur la communication à distance pour la communication entre domaines d’application de .NET Framework, les objets qui sont passés entre eux doivent être accessibles à distance.

Un objet accessible à distance est une instance d’une classe qui effectue une ou plusieurs des opérations suivantes :

- Dérive le <xref:System.MarshalByRefObject> classe.

- Implémente l'interface <xref:System.Runtime.Serialization.ISerializable>.

- A la <xref:System.SerializableAttribute> attribut appliqué.

> [!NOTE]
> Pour plus d’informations sur la création d’objets de .NET Framework accessibles à distance, consultez [rendre objets accessibles à distance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100)).

Les types WPF UI ne sont pas accessibles à distance. Pour résoudre ce problème, WPF étend le modèle de complément .NET Framework pour activer UI WPF créés par des compléments à afficher à partir d’applications hôtes. Cette prise en charge est fournie par WPF par deux types : les <xref:System.AddIn.Contract.INativeHandleContract> interface et deux méthodes statiques implémentées par le <xref:System.AddIn.Pipeline.FrameworkElementAdapters> classe : <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> et <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. À un niveau élevé, ces types et méthodes sont utilisés de la manière suivante :

1. WPF nécessite que les interfaces utilisateur fournies par les compléments sont des classes qui dérivent directement ou indirectement de <xref:System.Windows.FrameworkElement>, tels que des formes, des contrôles, des contrôles utilisateur, des panneaux de disposition et des pages.

2. Chaque fois que le contrat déclare qu’une interface utilisateur sera transmise entre le complément et l’application hôte, elle doit être déclarée comme un <xref:System.AddIn.Contract.INativeHandleContract> (pas un <xref:System.Windows.FrameworkElement>) ; <xref:System.AddIn.Contract.INativeHandleContract> est une représentation accessible à distance de l’ajouter dans l’interface utilisateur qui peut être passée au-delà des limites d’isolation.

3. Avant d’être passée à partir de domaine d’application de la macro complémentaire, un <xref:System.Windows.FrameworkElement> est empaqueté comme un <xref:System.AddIn.Contract.INativeHandleContract> en appelant <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.

4. Après avoir été transmis au domaine d’application de l’application hôte, le <xref:System.AddIn.Contract.INativeHandleContract> doivent être transformées en un <xref:System.Windows.FrameworkElement> en appelant <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>.

Comment <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, et <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> sont utilisés dépend du scénario spécifique. Les sections suivantes fournissent des détails sur chaque modèle de programmation.

<a name="ReturnUIFromAddInContract"></a>

## <a name="add-in-returns-a-user-interface"></a>Le complément retourne une interface utilisateur

Pour un complément retourner une interface utilisateur à une application hôte, les éléments suivants sont requis :

1. L’application hôte, d’un complément et d’un pipeline doivent être créés, comme décrit par le .NET Framework [des compléments et extensibilité](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)) documentation.

2. Le contrat doit implémenter <xref:System.AddIn.Contract.IContract> et, pour retourner une interface utilisateur, le contrat doit déclarer une méthode avec une valeur de retour de type <xref:System.AddIn.Contract.INativeHandleContract>.

3. L’interface utilisateur qui est transmise entre le complément et l’application hôte doit dériver directement ou indirectement de <xref:System.Windows.FrameworkElement>.

4. L’interface utilisateur qui est retourné par le complément doit être converti à partir d’un <xref:System.Windows.FrameworkElement> à un <xref:System.AddIn.Contract.INativeHandleContract> avant de traverser la limite d’isolation.

5. L’interface utilisateur qui est retourné doit être converti à partir d’un <xref:System.AddIn.Contract.INativeHandleContract> à un <xref:System.Windows.FrameworkElement> après avoir traversé la limite d’isolation.

6. L’application hôte affiche retourné <xref:System.Windows.FrameworkElement>.

Pour obtenir un exemple qui montre comment implémenter un complément qui retourne une interface utilisateur, consultez [créer un complément qui retourne une interface utilisateur](how-to-create-an-add-in-that-returns-a-ui.md).

<a name="AddInIsAUI"></a>

## <a name="add-in-is-a-user-interface"></a>Le complément est une interface utilisateur

Lorsqu’un complément est une interface utilisateur, les éléments suivants sont requis :

1. L’application hôte, d’un complément et d’un pipeline doivent être créés, comme décrit par le .NET Framework [des compléments et extensibilité](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)) documentation.

2. L’interface de contrat pour le complément doit implémenter <xref:System.AddIn.Contract.INativeHandleContract>.

3. Le complément, qui est passé à l’application hôte doit dériver directement ou indirectement de <xref:System.Windows.FrameworkElement>.

4. Le complément doit être converti à partir d’un <xref:System.Windows.FrameworkElement> à un <xref:System.AddIn.Contract.INativeHandleContract> avant de traverser la limite d’isolation.

5. Le complément doit être converti à partir d’un <xref:System.AddIn.Contract.INativeHandleContract> à un <xref:System.Windows.FrameworkElement> après avoir traversé la limite d’isolation.

6. L’application hôte affiche retourné <xref:System.Windows.FrameworkElement>.

Pour obtenir un exemple qui montre comment implémenter un complément qui est une interface utilisateur, consultez [créer un complément qui est une interface utilisateur](how-to-create-an-add-in-that-is-a-ui.md).

<a name="ReturningMultipleUIsFromAnAddIn"></a>

## <a name="returning-multiple-uis-from-an-add-in"></a>Retour de plusieurs interfaces utilisateur à partir d’un complément

Compléments proposent souvent plusieurs interfaces utilisateur pour applications hôtes doivent afficher. Par exemple, considérez un complément qui est une interface utilisateur qui fournit également des informations d’état à l’application hôte, également comme une interface utilisateur. Un complément de ce type peut être implémenté à l’aide d’une combinaison de techniques provenant des modèles [Le complément retourne une interface utilisateur](#ReturnUIFromAddInContract) et [Le complément est une interface utilisateur](#AddInIsAUI).

<a name="AddInsAndXBAPs"></a>

## <a name="add-ins-and-xaml-browser-applications"></a>Compléments et applications de navigateur XAML

Dans les exemples présentés jusqu’à maintenant, l’application hôte a été installée en tant qu’application autonome. Toutefois, les applications [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] peuvent également héberger des compléments, bien que ceux-ci s’accompagnent des exigences de génération et d’implémentation supplémentaires suivantes :

- Le manifeste de l’application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] doit être configuré spécialement pour télécharger le pipeline (dossiers et assemblys) et l’assembly de complément dans le cache d’application [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] sur la machine cliente, dans le même dossier que l’application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].

- Le code de l’application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] permettant de découvrir et de charger les compléments doit utiliser le cache d’application [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] pour l’application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] comme emplacement de pipeline et de complément.

- L’application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] doit charger le complément dans un contexte de sécurité spécial si ce complément référence des fichiers libres situés sur le site d’origine. Quand ils sont hébergés par l’application [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], les compléments peuvent uniquement référencer les fichiers libres situés sur le site d’origine de l’application hôte.

Ces tâches sont décrites en détail dans les sous-sections suivantes.

### <a name="configuring-the-pipeline-and-add-in-for-clickonce-deployment"></a>Configuration du pipeline et du complément pour un déploiement ClickOnce

Les applications [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] sont téléchargées et exécutées dans un dossier sécurisé du cache de déploiement [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)]. Pour qu’une application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] héberge un complément, l’assembly de pipeline et de complément doit également être téléchargé dans ce dossier sécurisé. Ainsi, vous devez configurer le manifeste de l’application pour qu’il contienne l’assembly de pipeline et de complément à télécharger. Le plus simple est d’effectuer cette opération dans [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]. Toutefois, l’assembly de pipeline et de complément doit se trouver dans le dossier racine du projet d’application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] de l’hôte pour que [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] puisse détecter les assemblys de pipeline.

La première étape consiste donc à générer l’assembly de pipeline et de complément à la racine du projet [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] en définissant la sortie de build de chaque projet d’assembly de pipeline et d’assembly de complément. Le tableau suivant présente les chemins de sortie de build des projets d’assembly de pipeline et du projet d’assembly de complément se trouvant dans le même dossier solution et racine que le projet [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] de l’hôte.

Tableau 1 : Générer des chemins d’accès de sortie pour les assemblys de Pipeline hébergés par une application XBAP

|Projet d’assembly de pipeline|Chemin de sortie de la génération|
|-------------------------------|-----------------------|
|Contrat|`..\HostXBAP\Contracts\`|
|Vue de complément|`..\HostXBAP\AddInViews\`|
|Adaptateur côté complément|`..\HostXBAP\AddInSideAdapters\`|
|Adaptateur côté hôte|`..\HostXBAP\HostSideAdapters\`|
|Complément|`..\HostXBAP\AddIns\WPFAddIn1`|

L’étape suivante consiste à spécifier les assemblys de pipeline et l’assembly de complément en tant que fichiers de contenu [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] dans [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] en effectuant les opérations ci-dessous :

1. Ajoutez l’assembly de pipeline et de complément au projet en cliquant avec le bouton droit sur chaque dossier de pipeline dans l’Explorateur de solutions, puis choisissez **Inclure dans le projet**.

2. Affectez à l’**Action de génération** de chaque assembly de pipeline et de complément le **Contenu** de la fenêtre **Propriétés**.

La dernière étape consiste à configurer le manifeste de l’application pour inclure les fichiers d’assembly de pipeline et de complément à télécharger. Les fichiers doivent se trouver dans des dossiers situés à la racine du dossier du cache [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] occupé par l’application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Vous pouvez procéder à la configuration dans [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] en effectuant les opérations suivantes :

1. Cliquez avec le bouton droit sur le projet [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], cliquez sur **Propriétés**, sur **Publier**, puis sur le bouton **Fichiers d’application**.

2. Dans la boîte de dialogue **Fichiers d’application**, affectez à l’**État de la publication** de chaque DLL de pipeline et de complément la valeur **Inclure (automatique)** , puis affectez au **Groupe de téléchargement** de chaque DLL de pipeline et de complément la valeur **(Requis)** .

### <a name="using-the-pipeline-and-add-in-from-the-application-base"></a>Utilisation du pipeline et du complément à partir de la base de l’application

Quand le pipeline et le complément sont configurés pour le déploiement [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)], ils sont téléchargés dans le même dossier de cache [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] que l’application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Pour permettre l’utilisation du pipeline et du complément à partir de l’application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], le code de l’application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] doit les obtenir à partir de la base de l’application. Les différents types et membres du modèle de complément .NET Framework pour l’utilisation des pipelines et des compléments fournissent une prise en charge spéciale pour ce scénario. Tout d’abord, le chemin d’accès est identifié par le <xref:System.AddIn.Hosting.PipelineStoreLocation.ApplicationBase> valeur d’énumération. Vous utilisez cette valeur avec les surcharges des membres de complément adéquats pour utiliser des pipelines incluant les éléments suivants :

- <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

### <a name="accessing-the-hosts-site-of-origin"></a>Accès au site d’origine de l’hôte

Pour garantir qu’un complément puisse référencer des fichiers à partir du site d’origine, ce complément doit être chargé avec l’isolation de sécurité équivalente à l’application hôte. Ce niveau de sécurité est identifié par le <xref:System.AddIn.Hosting.AddInSecurityLevel.Host?displayProperty=nameWithType> valeur d’énumération et transmis à la <xref:System.AddIn.Hosting.AddInToken.Activate%2A> méthode lorsqu’un complément est activé.

<a name="WPFAddInModelArchitecture"></a>

## <a name="wpf-add-in-architecture"></a>Architecture des compléments WPF

Le niveau le plus élevé, comme nous l’avons vu, WPF permet de compléments .NET Framework implémenter des interfaces utilisateur (qui dérivent directement ou indirectement <xref:System.Windows.FrameworkElement>) à l’aide de <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> et <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. Le résultat est que l’application hôte est retournée une <xref:System.Windows.FrameworkElement> qui est affichée à partir de l’interface utilisateur dans l’application hôte.

Pour l’interface utilisateur Ajouter dans des scénarios simples, il s’agit de toutes les informations dont un développeur a besoin. Pour des scénarios plus complexes, en particulier ceux qui essaient d’utiliser des services WPF supplémentaires telles que la mise en page, les ressources et la liaison de données, les connaissances plus détaillée de la façon dont WPF étend le modèle de complément .NET Framework avec prise en charge de l’interface utilisateur sont nécessaire pour comprendre ses avantages et les limitations.

Fondamentalement, WPF ne passe pas une interface utilisateur à partir d’un complément à une application hôte ; au lieu de cela, WPF passe le handle de fenêtre Win32 pour l’interface utilisateur à l’aide de l’interopérabilité WPF. Par conséquent, lorsqu’une interface utilisateur à partir d’un complément est passée à une application hôte, les événements suivants se produisent :

- Sur le côté complément, WPF acquiert un handle de fenêtre pour l’interface utilisateur qui sera affiché par l’application hôte. Le handle de fenêtre est encapsulé par une classe WPF interne qui dérive de <xref:System.Windows.Interop.HwndSource> et implémente <xref:System.AddIn.Contract.INativeHandleContract>. Une instance de cette classe est retournée par <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> et est marshalée du domaine d’application du complément au domaine d’application de l’application hôte.

- Du côté application hôte, WPF Repackage le <xref:System.Windows.Interop.HwndSource> en tant que classe WPF interne qui dérive de <xref:System.Windows.Interop.HwndHost> et consomme <xref:System.AddIn.Contract.INativeHandleContract>. Une instance de cette classe est retournée par <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> à l’application hôte.

<xref:System.Windows.Interop.HwndHost> existe pour afficher les interfaces utilisateur, identifiés par les handles de fenêtres, des interfaces utilisateur WPF. Pour plus d’informations, consultez [Interopérabilité WPF et Win32](../advanced/wpf-and-win32-interoperation.md).

En résumé, <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, et <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> existent pour permettre le handle de fenêtre pour une UI WPF à passer à partir d’un complément à une application hôte, où il est encapsulé par un <xref:System.Windows.Interop.HwndHost> et affiche l’interface utilisateur de l’application hôte.

> [!NOTE]
> Étant donné que l’application hôte obtienne un <xref:System.Windows.Interop.HwndHost>, l’application hôte ne peut pas convertir l’objet retourné par <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> au type, il est implémenté par le complément (par exemple, un <xref:System.Windows.Controls.UserControl>).

Par sa nature, <xref:System.Windows.Interop.HwndHost> a certaines limitations qui affectent comment héberger des applications peuvent les utiliser. Toutefois, WPF étend <xref:System.Windows.Interop.HwndHost> avec plusieurs fonctionnalités pour les scénarios de complément. Ces avantages et limitations sont décrits ci-dessous.

<a name="WPFAddInModelBenefits"></a>

## <a name="wpf-add-in-benefits"></a>Avantages des compléments WPF

Étant donné que les interfaces utilisateur WPF sont affichés à partir d’héberger des applications à l’aide d’une classe interne qui dérive de <xref:System.Windows.Interop.HwndHost>, ces interfaces utilisateur sont limitées par les capacités de <xref:System.Windows.Interop.HwndHost> en ce qui concerne les services WPF UI telles que la mise en page, rendu, la liaison de données, styles, modèles et de ressources. Toutefois, WPF augmente son texte interne <xref:System.Windows.Interop.HwndHost> sous-classe avec des fonctionnalités supplémentaires qui incluent les éléments suivants :

- Tabulation entre l’interface utilisateur d’une application hôte et l’interface utilisateur d’un complément. Notez que le modèle de programmation « add-in est une interface utilisateur » requiert l’adaptateur côté complément remplace <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> pour permettre la tabulation, si le complément est entièrement fiable ou partiellement fiable.

- En respectant les critères d’accessibilité pour les interfaces utilisateur qui sont affichés à partir des interfaces utilisateur d’application hôte.

- L’activation des applications WPF exécuter en toute sécurité dans plusieurs scénarios de domaine d’application.

- Empêcher l’accès non conforme pour l’interface utilisateur du complément handles de fenêtre quand des compléments s’exécutent avec l’isolation de sécurité (autrement dit, un sandbox de sécurité de confiance partielle). Appel <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> garantit cette sécurité :

  - Pour le modèle de programmation « complément retourne une interface utilisateur », la seule façon de passer le handle de fenêtre pour une interface utilisateur en au-delà de la limite d’isolation consiste à appeler <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.

  - Pour le modèle de programmation « add-in est une interface utilisateur », remplaçant <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> sur l’adaptateur côté complément et l’appel <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> (comme indiqué dans les exemples précédents) est nécessaire, comme l’adaptateur côté complément appelle `QueryContract` implémentation à partir de la adaptateur côté hôte.

- Protection de l’exécution de plusieurs domaines d’application. En raison des limitations liées aux domaines d’application, les exceptions non prises en charge qui sont levées dans les domaines d’application de complément entraînent l’arrêt brutal de l’application, même s’il existe une limite d’isolation. Toutefois, WPF et le modèle de complément .NET Framework fournissent un moyen simple de contourner ce problème et d’améliorer la stabilité de l’application. Un complément WPF qui affiche une interface utilisateur crée un <xref:System.Windows.Threading.Dispatcher> pour le thread qui le domaine d’application s’exécute, et si l’application hôte est une application WPF. Vous pouvez détecter des exceptions non gérées qui se produisent dans le domaine d’application en gérant la <xref:System.Windows.Threading.Dispatcher.UnhandledException> événement du complément WPF <xref:System.Windows.Threading.Dispatcher>. Vous pouvez obtenir le <xref:System.Windows.Threading.Dispatcher> à partir de la <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A> propriété.

<a name="WPFAddInModelLimitations"></a>

## <a name="wpf-add-in-limitations"></a>Limitations des compléments WPF

Au-delà des avantages que WPF ajoute aux comportements par défaut fournis par <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost>et les handles de fenêtre, il existe également des limitations pour les interfaces utilisateur qui sont affichés à partir d’héberger des applications :

- Interfaces utilisateur de complément affichées à partir d’une application hôte ne respectent pas le comportement de découpage de l’application hôte.

- Le concept d’*espace de rendu* des scénarios d’interopérabilité s’applique également aux compléments (consultez [Vue d’ensemble des régions de technologie](../advanced/technology-regions-overview.md)).

- Services de l’interface utilisateur d’une application hôte, tels que l’héritage de ressources, la liaison de données et leur exécution, ne sont pas automatiquement disponibles à ajouter dans les interfaces utilisateur. Pour fournir ces services au complément, vous devez mettre à jour le pipeline.

- Une interface utilisateur complément ne peut pas faire pivoter, mis à l’échelle, inclinée ou sinon affectée par une transformation (consultez [transforme la vue d’ensemble](../graphics-multimedia/transforms-overview.md)).

- Contenu à l’intérieur des interfaces utilisateur du complément qui est restitué en dessinant des opérations à partir de la <xref:System.Drawing> espace de noms peut inclure une fusion alpha. Toutefois, un complément, l’interface utilisateur et l’interface utilisateur qui le contient d’application hôte doivent être 100 % opaque ; en d’autres termes, le `Opacity` propriété sur les deux doit être définie sur 1.

- Si le <xref:System.Windows.Window.AllowsTransparency%2A> a la valeur de propriété d’une fenêtre dans l’application hôte qui contient une interface utilisateur complément `true`, le complément est invisible. Cela est vrai même si l’interface utilisateur complément est opaque à 100 % (autrement dit, le `Opacity` propriété a la valeur 1).

- Une interface utilisateur complément doit apparaître au-dessus des autres éléments WPF dans la même fenêtre de niveau supérieur.

- Aucune partie de l’interface utilisateur d’un complément ne permettre être rendue grâce à un <xref:System.Windows.Media.VisualBrush>. Au lieu de cela, le complément peut prendre un instantané de l’interface utilisateur générée pour créer une image bitmap qui peut être passé à l’application hôte à l’aide des méthodes définies par le contrat.

- Impossible de lire des fichiers multimédias à partir d’un <xref:System.Windows.Controls.MediaElement> dans une interface utilisateur de compléments.

- Événements de souris générés pour l’interface utilisateur complément ne sont ni reçus, ni déclenchés par l’application hôte et le `IsMouseOver` propriété d’interface utilisateur d’application hôte a la valeur `false`.

- Lorsque la sélection se déplace entre les contrôles dans une interface utilisateur complément, la `GotFocus` et `LostFocus` événements ne sont ni reçus, ni déclenchés par l’application hôte.

- La partie d’une application hôte qui contient une interface utilisateur complément apparaît en blanche lors de l’impression.

- Tous les répartiteurs (consultez <xref:System.Windows.Threading.Dispatcher>) créé par le complément, l’interface utilisateur doive être arrêté manuellement avant que le module additionnel propriétaire soit déchargé si l’application hôte continue l’exécution. Le contrat peut implémenter des méthodes qui permettent à l’application hôte signaler le complément avant que le complément soit déchargé, ce qui permet l’interface utilisateur Ajouter à arrêter ses répartiteurs.

- Si une interface utilisateur complément est une <xref:System.Windows.Controls.InkCanvas> ou contient un <xref:System.Windows.Controls.InkCanvas>, vous ne pouvez pas décharger le complément.

<a name="PerformanceOptimization"></a>

## <a name="performance-optimization"></a>Optimisation des performances

Par défaut, lorsque plusieurs domaines d’application sont utilisés, les différents assemblys .NET Framework requises par chaque application sont tous chargés dans ce domaine d’application. Ainsi, le temps nécessaire à la création de domaines d’application et au démarrage des applications dans ces domaines peut affecter les performances. Toutefois, le .NET Framework fournit un moyen de réduire les heures de début en indiquant aux applications de partager des assemblages entre domaines d’application si ceux-ci sont déjà chargés. Pour cela, vous devez utiliser le <xref:System.LoaderOptimizationAttribute> attribut, qui doit être appliqué à la méthode de point d’entrée (`Main`). Dans ce cas, utilisez uniquement du code pour implémenter votre définition d’application (consultez [Vue d’ensemble de la gestion d’applications](application-management-overview.md)).

## <a name="see-also"></a>Voir aussi

- <xref:System.LoaderOptimizationAttribute>
- [Compléments et extensibilité](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Domaines d’application](../../app-domains/application-domains.md)
- [Vue d’ensemble de .NET framework Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kwdt6w2k(v=vs.100))
- [Objets accessibles à distance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100))
- [Rubriques de guide pratique](how-to-topics.md)
