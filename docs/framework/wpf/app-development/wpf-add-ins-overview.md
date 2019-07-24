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
ms.openlocfilehash: 4fd8fe00fe6974bdcbf7b4af4da25150996de8c3
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401700"
---
# <a name="wpf-add-ins-overview"></a>Vue d'ensemble des compléments WPF

<a name="Introduction"></a>Le .NET Framework comprend un modèle de complément que les développeurs peuvent utiliser pour créer des applications qui prennent en charge l’extensibilité des compléments. Ce modèle de complément permet de créer des compléments qui s’intègrent aux applications et étendent leurs fonctionnalités. Dans certains scénarios, les applications doivent également afficher les interfaces utilisateur fournies par les compléments. Cette rubrique montre comment WPF augmente le modèle de complément .NET Framework pour activer ces scénarios, l’architecture sous-jacente, ses avantages et ses limitations.

<a name="Requirements"></a>

## <a name="prerequisites"></a>Prérequis

Vous devez être familiarisé avec le modèle de complément .NET Framework. Pour plus d’informations, consultez [Compléments et extensibilité](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).

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

- **Détection**: Recherche de compléments qui adhèrent aux contrats pris en charge par les applications hôtes.

- **Activation**: Le chargement, l’exécution et l’établissement de la communication avec les compléments.

- **Isolation** : À l’aide de domaines d’application ou de processus pour établir des limites d’isolation qui protègent les applications des problèmes potentiels de sécurité et d’exécution avec les compléments.

- **Communication**: Autoriser les compléments et les applications hôtes à communiquer les uns avec les autres à travers les limites d’isolation en appelant des méthodes et en passant des données.

- **Gestion**de la durée de vie: Chargement et déchargement des domaines d’application et des processus de manière propre et prévisible (consultez [domaines d’application](../../app-domains/application-domains.md)).

- Contrôle de **version**: S’assurer que les applications hôtes et les compléments peuvent toujours communiquer quand de nouvelles versions de sont créées.

Enfin, le développement d’un modèle de complément robuste est une tâche non négligeable. C’est la raison pour laquelle le .NET Framework fournit une infrastructure pour la création de modèles de compléments.

> [!NOTE]
> Pour plus d’informations sur les compléments, consultez [Compléments et extensibilité](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).

<a name="NETFrameworkAddInModelOverview"></a>

## <a name="net-framework-add-in-model-overview"></a>Vue d’ensemble du modèle de complément du .NET Framework

Le modèle de complément .NET Framework, situé dans l' <xref:System.AddIn> espace de noms, contient un ensemble de types conçus pour simplifier le développement de l’extensibilité des compléments. L’unité fondamentale du modèle de complément .NET Framework est le *contrat*, qui définit la façon dont une application hôte et un complément communiquent les uns avec les autres. Un contrat est exposé à une application hôte à l’aide d’une *vue* spécifique à l’application hôte du contrat. De même, une *vue* spécifique au complément du contrat est exposée au complément. Un *adaptateur* permet à une application hôte et à un complément de communiquer entre les vues respectives du contrat. Les contrats, les vues et les adaptateurs sont appelés des segments. Un ensemble de segments connexes constitue un *pipeline*. Les pipelines sont la base sur laquelle le modèle de complément .NET Framework prend en charge la découverte, l’activation, l’isolation de sécurité, l’isolation d’exécution (à l’aide de domaines d’application et de processus), la communication, la gestion de la durée de vie et le contrôle de version.

L’ensemble de cette prise en charge permet aux développeurs de générer des compléments qui s’intègrent aux fonctionnalités d’une application hôte. Toutefois, certains scénarios requièrent que les applications hôtes affichent les interfaces utilisateur fournies par les compléments. Étant donné que chaque technologie de présentation présente dans le .NET Framework possède son propre modèle pour l’implémentation d’interfaces utilisateur, le modèle de complément .NET Framework ne prend en charge aucune technologie de présentation particulière. Au lieu de cela, WPF étend le modèle de complément .NET Framework avec la prise en charge de l’interface utilisateur pour les compléments.

<a name="WPFAddInModel"></a>

## <a name="wpf-add-ins"></a>Compléments WPF

WPF, conjointement avec le modèle de complément .NET Framework, vous permet de gérer un large éventail de scénarios qui requièrent que les applications hôtes affichent des interfaces utilisateur à partir de compléments. En particulier, ces scénarios sont traités par WPF avec les deux modèles de programmation suivants:

1. **Le complément retourne une IU (interface utilisateur)** . Un complément retourne une interface utilisateur à l’application hôte via un appel de méthode, comme défini par le contrat. Ce scénario est utilisé dans les cas suivants :

    - L’apparence d’une interface utilisateur retournée par un complément dépend des données ou des conditions qui existent uniquement au moment de l’exécution, telles que les rapports générés dynamiquement.

    - L’interface utilisateur pour les services fournis par un complément diffère de l’interface utilisateur des applications hôtes qui peuvent utiliser le complément.

    - Le complément exécute principalement un service pour l’application hôte et signale l’État à l’application hôte avec une interface utilisateur.

2. **Le complément est une interface utilisateur**. Un complément est une interface utilisateur, comme défini par le contrat. Ce scénario est utilisé dans les cas suivants :

    - Un complément ne fournit pas d’autres services que celui d’être affiché, par exemple une publicité.

    - L’interface utilisateur pour les services fournis par un complément est commune à toutes les applications hôtes qui peuvent utiliser ce complément, telles qu’une calculatrice ou un sélecteur de couleurs.

Ces scénarios requièrent que les objets d’interface utilisateur puissent être transmis entre les domaines d’application hôte et de complément. Étant donné que le modèle de complément .NET Framework repose sur la communication à distance pour communiquer entre les domaines d’application, les objets passés entre eux doivent être accessibles à distance.

Un objet accessible à distance est une instance d’une classe qui effectue une ou plusieurs des opérations suivantes :

- Dérive de la <xref:System.MarshalByRefObject> classe.

- Implémente l'interface <xref:System.Runtime.Serialization.ISerializable>.

- A l' <xref:System.SerializableAttribute> attribut appliqué.

> [!NOTE]
> Pour plus d’informations sur la création d’objets .NET Framework accessibles à distance, consultez [rendre des objets accessibles à distance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100)).

Les types d’interface utilisateur WPF ne sont pas accessibles à distance. Pour résoudre le problème, WPF étend le modèle de complément .NET Framework pour permettre l’affichage de l’interface utilisateur WPF créée par les compléments à partir d’applications hôtes. Cette prise en charge est assurée par WPF par deux types <xref:System.AddIn.Contract.INativeHandleContract> : l’interface et deux méthodes statiques <xref:System.AddIn.Pipeline.FrameworkElementAdapters> implémentées par <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>la classe: <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> et. À un niveau élevé, ces types et méthodes sont utilisés de la manière suivante :

1. WPF requiert que les interfaces utilisateur fournies par les compléments soient des classes qui dérivent <xref:System.Windows.FrameworkElement>directement ou indirectement de, telles que des formes, des contrôles, des contrôles utilisateur, des panneaux de disposition et des pages.

2. Chaque fois que le contrat déclare qu’une interface utilisateur sera passée entre le complément et l’application hôte, elle doit être déclarée comme un <xref:System.AddIn.Contract.INativeHandleContract> (et non <xref:System.Windows.FrameworkElement>un); <xref:System.AddIn.Contract.INativeHandleContract> est une représentation accessible à distance de l’interface utilisateur du complément qui peut être passée à travers les limites d’isolation.

3. Avant d’être passé à partir du domaine d’application du complément, <xref:System.Windows.FrameworkElement> un est empaqueté en <xref:System.AddIn.Contract.INativeHandleContract> tant que <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>en appelant.

4. Une fois passé au domaine d’application de l’application hôte, <xref:System.AddIn.Contract.INativeHandleContract> le doit être reconditionné <xref:System.Windows.FrameworkElement> en appelant <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>.

La <xref:System.AddIn.Contract.INativeHandleContract>manière <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>dont, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> et sont utilisées dépend du scénario spécifique. Les sections suivantes fournissent des détails sur chaque modèle de programmation.

<a name="ReturnUIFromAddInContract"></a>

## <a name="add-in-returns-a-user-interface"></a>Le complément retourne une interface utilisateur

Pour qu’un complément retourne une interface utilisateur à une application hôte, les conditions suivantes sont requises:

1. L’application hôte, le complément et le pipeline doivent être créés, comme décrit dans la documentation relative aux [compléments et](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)) à l’extensibilité de .NET Framework.

2. Le contrat doit implémenter <xref:System.AddIn.Contract.IContract> et, pour retourner une interface utilisateur, le contrat doit déclarer une méthode avec une valeur de retour de type. <xref:System.AddIn.Contract.INativeHandleContract>

3. L’interface utilisateur qui est passée entre le complément et l’application hôte doit dériver directement ou indirectement de <xref:System.Windows.FrameworkElement>.

4. L’interface utilisateur retournée par le complément doit être convertie d’un <xref:System.Windows.FrameworkElement> en un <xref:System.AddIn.Contract.INativeHandleContract> avant de traverser la limite d’isolation.

5. L’interface utilisateur retournée doit être convertie <xref:System.AddIn.Contract.INativeHandleContract> d’un <xref:System.Windows.FrameworkElement> en un après avoir franchi la limite d’isolation.

6. L’application hôte affiche le retourné <xref:System.Windows.FrameworkElement>.

Pour obtenir un exemple qui montre comment implémenter un complément qui retourne une interface utilisateur, consultez [créer un complément qui retourne une interface utilisateur](how-to-create-an-add-in-that-returns-a-ui.md).

<a name="AddInIsAUI"></a>

## <a name="add-in-is-a-user-interface"></a>Le complément est une interface utilisateur

Quand un complément est une interface utilisateur, les conditions suivantes sont requises:

1. L’application hôte, le complément et le pipeline doivent être créés, comme décrit dans la documentation relative aux [compléments et](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)) à l’extensibilité de .NET Framework.

2. L’interface de contrat pour le complément doit implémenter <xref:System.AddIn.Contract.INativeHandleContract>.

3. Le complément qui est passé à l’application hôte doit dériver directement ou indirectement de <xref:System.Windows.FrameworkElement>.

4. Le complément doit être converti d’un <xref:System.Windows.FrameworkElement> en un <xref:System.AddIn.Contract.INativeHandleContract> avant de traverser la limite d’isolation.

5. Le complément doit être converti d’un <xref:System.AddIn.Contract.INativeHandleContract> en un <xref:System.Windows.FrameworkElement> après avoir franchi la limite d’isolation.

6. L’application hôte affiche le retourné <xref:System.Windows.FrameworkElement>.

Pour obtenir un exemple qui montre comment implémenter un complément qui est une interface utilisateur, consultez [créer un complément qui est une interface utilisateur](how-to-create-an-add-in-that-is-a-ui.md).

<a name="ReturningMultipleUIsFromAnAddIn"></a>

## <a name="returning-multiple-uis-from-an-add-in"></a>Retour de plusieurs interfaces utilisateur à partir d’un complément

Les compléments fournissent souvent plusieurs interfaces utilisateur que les applications hôtes doivent afficher. Par exemple, considérez un complément qui est une interface utilisateur qui fournit également des informations d’État à l’application hôte, également en tant qu’interface utilisateur. Un complément de ce type peut être implémenté à l’aide d’une combinaison de techniques provenant des modèles [Le complément retourne une interface utilisateur](#ReturnUIFromAddInContract) et [Le complément est une interface utilisateur](#AddInIsAUI).

<a name="AddInsAndXBAPs"></a>

## <a name="add-ins-and-xaml-browser-applications"></a>Compléments et applications de navigateur XAML

Dans les exemples présentés jusqu’à maintenant, l’application hôte a été installée en tant qu’application autonome. Toutefois, les applications [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] peuvent également héberger des compléments, bien que ceux-ci s’accompagnent des exigences de génération et d’implémentation supplémentaires suivantes :

- Le [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] manifeste de l’application doit être configuré spécialement pour télécharger le pipeline (dossiers et assemblys) et l’assembly du complément dans le cache d’application ClickOnce sur l’ordinateur client, dans [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]le même dossier que le.

- Le [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] code permettant de détecter et de charger les compléments doit utiliser le cache d’application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ClickOnce pour le comme emplacement de pipeline et de complément.

- L’application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] doit charger le complément dans un contexte de sécurité spécial si ce complément référence des fichiers libres situés sur le site d’origine. Quand ils sont hébergés par l’application [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], les compléments peuvent uniquement référencer les fichiers libres situés sur le site d’origine de l’application hôte.

Ces tâches sont décrites en détail dans les sous-sections suivantes.

### <a name="configuring-the-pipeline-and-add-in-for-clickonce-deployment"></a>Configuration du pipeline et du complément pour un déploiement ClickOnce

[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]sont téléchargés et exécutés à partir d’un dossier sécurisé dans le cache de déploiement ClickOnce. Pour qu’une application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] héberge un complément, l’assembly de pipeline et de complément doit également être téléchargé dans ce dossier sécurisé. Ainsi, vous devez configurer le manifeste de l’application pour qu’il contienne l’assembly de pipeline et de complément à télécharger. Le plus simple est d’effectuer cette opération dans [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]. Toutefois, l’assembly de pipeline et de complément doit se trouver dans le dossier racine du projet d’application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] de l’hôte pour que [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] puisse détecter les assemblys de pipeline.

La première étape consiste donc à générer l’assembly de pipeline et de complément à la racine du projet [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] en définissant la sortie de build de chaque projet d’assembly de pipeline et d’assembly de complément. Le tableau suivant présente les chemins de sortie de build des projets d’assembly de pipeline et du projet d’assembly de complément se trouvant dans le même dossier solution et racine que le projet [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] de l’hôte.

Tableau 1 : Chemins de sortie de la génération pour les assemblys de pipeline qui sont hébergés par un XBAP

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

La dernière étape consiste à configurer le manifeste de l’application pour inclure les fichiers d’assembly de pipeline et de complément à télécharger. Les fichiers doivent se trouver dans des dossiers à la racine du dossier dans le cache ClickOnce que l' [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] application occupe. Vous pouvez procéder à la configuration dans [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] en effectuant les opérations suivantes :

1. Cliquez avec le bouton droit sur le projet [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], cliquez sur **Propriétés**, sur **Publier**, puis sur le bouton **Fichiers d’application**.

2. Dans la boîte de dialogue **Fichiers d’application**, affectez à l’**État de la publication** de chaque DLL de pipeline et de complément la valeur **Inclure (automatique)** , puis affectez au **Groupe de téléchargement** de chaque DLL de pipeline et de complément la valeur **(Requis)** .

### <a name="using-the-pipeline-and-add-in-from-the-application-base"></a>Utilisation du pipeline et du complément à partir de la base de l’application

Lorsque le pipeline et le complément sont configurés pour le déploiement ClickOnce, ils sont téléchargés dans le même dossier de [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]cache ClickOnce que le. Pour permettre l’utilisation du pipeline et du complément à partir de l’application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], le code de l’application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] doit les obtenir à partir de la base de l’application. Les différents types et membres du modèle de complément .NET Framework pour l’utilisation de pipelines et de compléments fournissent une prise en charge spéciale pour ce scénario. Tout d’abord, le chemin d’accès <xref:System.AddIn.Hosting.PipelineStoreLocation.ApplicationBase> est identifié par la valeur d’énumération. Vous utilisez cette valeur avec les surcharges des membres de complément adéquats pour utiliser des pipelines incluant les éléments suivants :

- <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

### <a name="accessing-the-hosts-site-of-origin"></a>Accès au site d’origine de l’hôte

Pour garantir qu’un complément puisse référencer des fichiers à partir du site d’origine, ce complément doit être chargé avec l’isolation de sécurité équivalente à l’application hôte. Ce niveau de sécurité est identifié par <xref:System.AddIn.Hosting.AddInSecurityLevel.Host?displayProperty=nameWithType> la valeur d’énumération et passé <xref:System.AddIn.Hosting.AddInToken.Activate%2A> à la méthode lorsqu’un complément est activé.

<a name="WPFAddInModelArchitecture"></a>

## <a name="wpf-add-in-architecture"></a>Architecture des compléments WPF

Au niveau le plus élevé, comme nous l’avons vu, WPF permet .NET Framework compléments d’implémenter des interfaces utilisateur (qui dérivent directement <xref:System.AddIn.Contract.INativeHandleContract>ou indirectement <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>de <xref:System.Windows.FrameworkElement>) à l’aide de, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> et. Le résultat est que l’application hôte est retournée <xref:System.Windows.FrameworkElement> , qui est affichée à partir de l’interface utilisateur dans l’application hôte.

Pour les scénarios de compléments d’interface utilisateur simples, c’est autant de détails qu’un développeur a besoin. Pour les scénarios plus complexes, en particulier ceux qui essaient d’utiliser des services WPF supplémentaires tels que la disposition, les ressources et la liaison de données, une connaissance détaillée de la façon dont WPF étend le modèle de complément .NET Framework avec prise en charge de l’interface utilisateur est nécessaire pour comprendre ses avantages. et limitations.

Fondamentalement, WPF ne transmet pas une interface utilisateur à partir d’un complément à une application hôte; au lieu de cela, WPF passe le handle de fenêtre Win32 pour l’interface utilisateur à l’aide de l’interopérabilité WPF. Par conséquent, lorsqu’une interface utilisateur d’un complément est passée à une application hôte, les éléments suivants se produisent:

- Du côté du complément, WPF acquiert un handle de fenêtre pour l’interface utilisateur qui sera affichée par l’application hôte. Le handle de fenêtre est encapsulé par une classe WPF interne qui dérive de <xref:System.Windows.Interop.HwndSource> et <xref:System.AddIn.Contract.INativeHandleContract>implémente. Une instance de cette classe est retournée <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> par et est marshalée à partir du domaine d’application du complément vers le domaine d’application de l’application hôte.

- Côté application hôte, WPF reconditionne le <xref:System.Windows.Interop.HwndSource> comme une classe WPF interne qui dérive de <xref:System.Windows.Interop.HwndHost> et consomme <xref:System.AddIn.Contract.INativeHandleContract>. Une instance de cette classe est retournée <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> par à l’application hôte.

<xref:System.Windows.Interop.HwndHost>existe pour afficher les interfaces utilisateur, identifiées par les handles de fenêtre, à partir des interfaces utilisateur WPF. Pour plus d’informations, consultez [Interopérabilité WPF et Win32](../advanced/wpf-and-win32-interoperation.md).

En résumé, <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>et <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> existent pour autoriser le handle de fenêtre d’une interface utilisateur WPF à passer d’un complément à une application hôte, où il est encapsulé par un <xref:System.Windows.Interop.HwndHost> et qui affiche l’interface utilisateur de l’application hôte.

> [!NOTE]
> Étant donné que l’application hôte <xref:System.Windows.Interop.HwndHost>obtient un, l’application hôte ne peut pas convertir l’objet <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> retourné par en type implémenté par le complément (par exemple, a <xref:System.Windows.Controls.UserControl>).

Par nature, <xref:System.Windows.Interop.HwndHost> a certaines limitations qui affectent la façon dont les applications hôtes peuvent les utiliser. Toutefois, WPF s' <xref:System.Windows.Interop.HwndHost> étend avec plusieurs fonctionnalités pour les scénarios de compléments. Ces avantages et limitations sont décrits ci-dessous.

<a name="WPFAddInModelBenefits"></a>

## <a name="wpf-add-in-benefits"></a>Avantages des compléments WPF

Étant donné que les interfaces utilisateur du complément WPF sont affichées à partir d’applications hôtes à l’aide d' <xref:System.Windows.Interop.HwndHost>une classe interne qui dérive de, ces interfaces utilisateur sont <xref:System.Windows.Interop.HwndHost> restreintes par les fonctionnalités de en ce qui concerne les services d’interface utilisateur WPF tels que la disposition, rendu, liaison de données, styles, modèles et ressources. Toutefois, WPF augmente sa sous- <xref:System.Windows.Interop.HwndHost> classe interne avec des fonctionnalités supplémentaires qui incluent les éléments suivants:

- Tabulation entre l’interface utilisateur d’une application hôte et l’interface utilisateur d’un complément. Notez que le modèle de programmation «le complément est une interface utilisateur» requiert que l’adaptateur côté complément soit substitué <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> pour permettre la tabulation, que le complément soit d’un niveau de confiance totale ou partiel.

- Respect des exigences d’accessibilité pour les interfaces utilisateur du complément affichées à partir des interfaces utilisateur de l’application hôte.

- Permet aux applications WPF de s’exécuter en toute sécurité dans plusieurs scénarios de domaine d’application.

- Empêcher l’accès illégal aux handles de la fenêtre de l’interface utilisateur du complément lorsque les compléments s’exécutent avec l’isolation de sécurité (autrement dit, un bac à sable de sécurité de confiance partielle). L' <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> appel de garantit cette sécurité:

  - Pour le modèle de programmation «le complément retourne une interface utilisateur», le seul moyen de passer le handle de fenêtre pour une interface utilisateur de complément à travers la limite d' <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>isolation consiste à appeler.

  - Pour le modèle de programmation «le complément est une interface utilisateur», la <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> substitution de l’adaptateur côté complément et l’appel <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> de (comme indiqué dans les exemples précédents) sont nécessaires, tout comme l’appel de l' `QueryContract` implémentation de l’adaptateur côté complément à partir du adaptateur côté hôte.

- Protection de l’exécution de plusieurs domaines d’application. En raison des limitations liées aux domaines d’application, les exceptions non prises en charge qui sont levées dans les domaines d’application de complément entraînent l’arrêt brutal de l’application, même s’il existe une limite d’isolation. Toutefois, WPF et le modèle de complément .NET Framework offrent un moyen simple de contourner ce problème et d’améliorer la stabilité de l’application. Un complément WPF qui affiche une interface utilisateur crée un <xref:System.Windows.Threading.Dispatcher> pour le thread sur lequel s’exécute le domaine d’application, si l’application hôte est une application WPF. Vous pouvez détecter toutes les exceptions non gérées qui se produisent dans le domaine d’application <xref:System.Windows.Threading.Dispatcher.UnhandledException> en gérant l’événement du complément <xref:System.Windows.Threading.Dispatcher>WPF. Vous pouvez récupérer le <xref:System.Windows.Threading.Dispatcher> à partir <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A> de la propriété.

<a name="WPFAddInModelLimitations"></a>

## <a name="wpf-add-in-limitations"></a>Limitations des compléments WPF

Outre les avantages que WPF ajoute aux comportements par défaut fournis par <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost>et les handles de fenêtre, il existe également des limitations pour les interfaces utilisateur de compléments qui sont affichées à partir d’applications hôtes:

- Les interfaces utilisateur de compléments affichées à partir d’une application hôte ne respectent pas le comportement de découpage de l’application hôte.

- Le concept d’*espace de rendu* des scénarios d’interopérabilité s’applique également aux compléments (consultez [Vue d’ensemble des régions de technologie](../advanced/technology-regions-overview.md)).

- Les services d’interface utilisateur d’une application hôte, tels que l’héritage de ressources, la liaison de données et l’exécution de commandes, ne sont pas automatiquement disponibles pour les interfaces utilisateur du complément. Pour fournir ces services au complément, vous devez mettre à jour le pipeline.

- Une interface utilisateur de complément ne peut pas être pivotée, mise à l’échelle, inclinée ou affectée par une transformation (consultez [vue d’ensemble](../graphics-multimedia/transforms-overview.md)des transformations).

- Le contenu à l’intérieur des interfaces utilisateur de compléments rendues par des <xref:System.Drawing> opérations de dessin à partir de l’espace de noms peut inclure la fusion alpha. Toutefois, une interface utilisateur de complément et l’interface utilisateur de l’application hôte qui la contient doivent être opaques à 100%; en d’autres termes, `Opacity` la propriété des deux doit avoir la valeur 1.

- Si la <xref:System.Windows.Window.AllowsTransparency%2A> propriété d’une fenêtre de l’application hôte qui contient une interface utilisateur de complément a la `true`valeur, le complément est invisible. Cela est vrai même si l’interface utilisateur du complément est 100% opaque (autrement dit, la `Opacity` propriété a la valeur 1).

- Une interface utilisateur de complément doit apparaître au-dessus des autres éléments WPF dans la même fenêtre de niveau supérieur.

- Aucune partie de l’interface utilisateur d’un complément ne peut être rendue à <xref:System.Windows.Media.VisualBrush>l’aide d’un. Au lieu de cela, le complément peut prendre un instantané de l’interface utilisateur générée pour créer une image bitmap qui peut être transmise à l’application hôte à l’aide des méthodes définies par le contrat.

- Les fichiers multimédias ne peuvent pas <xref:System.Windows.Controls.MediaElement> être lus à partir d’un dans une interface utilisateur de complément.

- Les événements de souris générés pour l’interface utilisateur du complément ne sont ni reçus ni déclenchés par l' `IsMouseOver` application hôte, et la propriété de l’interface `false`utilisateur de l’application hôte a la valeur.

- Lorsque le focus se déplace entre les contrôles d’une interface utilisateur de complément `GotFocus` , `LostFocus` les événements et ne sont ni reçus ni déclenchés par l’application hôte.

- La partie d’une application hôte qui contient une interface utilisateur de complément apparaît en blanc lorsqu’elle est imprimée.

- Tous les répartiteurs ( <xref:System.Windows.Threading.Dispatcher>voir) créés par l’interface utilisateur du complément doivent être arrêtés manuellement avant que le complément propriétaire ne soit déchargé si l’exécution de l’application hôte se poursuit. Le contrat peut implémenter des méthodes qui permettent à l’application hôte de signaler le complément avant que le complément ne soit déchargé, ce qui permet à l’interface utilisateur du complément d’arrêter ses répartiteurs.

- Si une interface utilisateur de complément est un <xref:System.Windows.Controls.InkCanvas> ou si contient <xref:System.Windows.Controls.InkCanvas>un, vous ne pouvez pas décharger le complément.

<a name="PerformanceOptimization"></a>

## <a name="performance-optimization"></a>Optimisation des performances

Par défaut, lorsque plusieurs domaines d’application sont utilisés, les différents assemblys .NET Framework requis par chaque application sont tous chargés dans le domaine de cette application. Ainsi, le temps nécessaire à la création de domaines d’application et au démarrage des applications dans ces domaines peut affecter les performances. Toutefois, l' .NET Framework offre un moyen de réduire les heures de démarrage en ordonnant aux applications de partager des assemblys entre les domaines d’application s’ils sont déjà chargés. Pour ce faire, vous utilisez <xref:System.LoaderOptimizationAttribute> l’attribut, qui doit être appliqué à la méthode de point`Main`d’entrée (). Dans ce cas, utilisez uniquement du code pour implémenter votre définition d’application (consultez [Vue d’ensemble de la gestion d’applications](application-management-overview.md)).

## <a name="see-also"></a>Voir aussi

- <xref:System.LoaderOptimizationAttribute>
- [Compléments et extensibilité](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Domaines d’application](../../app-domains/application-domains.md)
- [Vue d’ensemble de la communication à distance .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kwdt6w2k(v=vs.100))
- [Rendre les objets accessibles à distance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100))
- [Rubriques de guide pratique](how-to-topics.md)
