---
title: Développement de l'application
ms.date: 01/26/2018
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
ms.openlocfilehash: 405a8d3c8b922d0f74e522e85ea3096d989c478e
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582499"
---
# <a name="application-development"></a>Développement de l'application
<a name="introduction"></a>Windows Presentation Foundation (WPF) est une infrastructure de présentation qui peut être utilisée pour développer les types d’applications suivants :  
  
- Applications autonomes (applications Windows de style traditionnel générées sous forme d’assemblys exécutables qui sont installés et exécutés sur l’ordinateur client).  
  
- [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] (applications composées de pages de navigation générées sous forme d’assemblys exécutables et hébergées par des navigateurs Web tels que Microsoft Internet Explorer ou Mozilla Firefox).  
  
- Bibliothèques de contrôles personnalisés (assemblys non exécutables contenant des contrôles réutilisables).  
  
- Bibliothèques de classes (assemblys non exécutables contenant des classes réutilisables).  
  
> [!NOTE]
> L’utilisation de types WPF dans un service Windows est fortement déconseillée. Si vous tentez d’utiliser ces fonctionnalités dans un service Windows, elles risquent de ne pas fonctionner comme prévu.  
  
 Pour générer cet ensemble d’applications, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] implémente de nombreux services. Cette rubrique fournit une vue d’ensemble de ces services et explique où trouver plus d’informations.  

<a name="Application_Management"></a>   
## <a name="application-management"></a>Gestion des applications  
 Les applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] exécutables nécessitent généralement un ensemble principal de fonctionnalités qui inclut les opérations suivantes :  
  
- Création et gestion de l’infrastructure d’application commune (dont la création d’une méthode de point d’entrée et une boucle de messages Windows pour recevoir les messages système et d’entrée).  
  
- Suivi et interaction avec la durée de vie d’une application.  
  
- Récupération et traitement des paramètres de ligne de commande.  
  
- Partage des propriétés de portée application et des ressources [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
- Détection et traitement des exceptions non gérées.  
  
- Retour de codes de sortie.  
  
- Gestion des fenêtres dans des applications autonomes.  
  
- Suivi de la navigation dans les [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)], et applications autonomes avec des fenêtres et des frames de navigation.  
  
 Ces fonctionnalités sont implémentées par la classe <xref:System.Windows.Application> que vous ajoutez à vos applications à l’aide d’une *définition d’application*.  
  
 Pour plus d’informations, consultez [Vue d’ensemble de la gestion d’applications](application-management-overview.md).  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>   
## <a name="wpf-application-resource-content-and-data-files"></a>Fichiers de ressources, de contenu et de données d'une application WPF  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] étend la prise en charge de base dans l’infrastructure Microsoft .NET pour les ressources incorporées avec la prise en charge de trois types de fichiers de données non exécutables : ressource, contenu et données. Pour plus d’informations, consultez [Fichiers de ressources, de contenu et de données d’une application WPF](wpf-application-resource-content-and-data-files.md).  
  
 Un composant clé de la prise en charge des fichiers de données non exécutables WPF est la possibilité de les identifier et de les charger à l’aide d’un URI unique. Pour plus d’informations, consultez [URI à en-tête pack dans WPF](pack-uris-in-wpf.md).  
  
<a name="Windows_and_Dialog_Boxes"></a>   
## <a name="windows-and-dialog-boxes"></a>Fenêtres et boîtes de dialogue  
 Les utilisateurs interagissent avec les applications autonomes [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] par le biais de fenêtres. Le rôle d’une fenêtre est d’héberger le contenu d’une application et de présenter les fonctionnalités de l’application qui permettent généralement aux utilisateurs d’interagir avec le contenu. Dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], les fenêtres sont encapsulées par la classe <xref:System.Windows.Window>, qui prend en charge les opérations suivantes :  
  
- Création et affichage des fenêtres.  
  
- Établissement des relations entre fenêtres parentes et fenêtres enfants.  
  
- Configuration de l’aspect des fenêtres (par exemple taille, emplacement, icônes, texte de barre de titre, bordure).  
  
- Suivi et interaction avec la durée de vie d’une fenêtre.  
  
 Pour plus d’informations, consultez [Vue d’ensemble des fenêtres WPF](wpf-windows-overview.md).  
  
 <xref:System.Windows.Window> prend en charge la capacité à créer un type spécial de fenêtre appelé « boîte de dialogue ». Deux types de boîtes de dialogue, modales et non modales, peuvent être créés.  
  
 Pour des raisons pratiques, ainsi que des avantages de la réutilisation et d’une expérience utilisateur cohérente entre les applications, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] expose trois boîtes de dialogue Windows communes : <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog> et <xref:System.Windows.Controls.PrintDialog>.  
  
 Une boîte de message est un type spécial de boîte de dialogue qui permet d’afficher des informations textuelles importantes aux utilisateurs et de poser des questions simples du type Oui/Non/OK/Annuler. Vous utilisez la classe <xref:System.Windows.MessageBox> pour créer et afficher des boîtes de message.  
  
 Pour plus d’informations, consultez [Vue d’ensemble des boîtes de dialogue](dialog-boxes-overview.md).  
  
<a name="Navigation"></a>   
## <a name="navigation"></a>Navigation  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] prend en charge la navigation de type web à l’aide de pages (<xref:System.Windows.Controls.Page>) et de liens hypertexte (<xref:System.Windows.Documents.Hyperlink>). La navigation peut être implémentée de diverses manières, notamment :  
  
- Pages autonomes hébergées dans un navigateur web.  
  
- Pages compilées dans une [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] qui est hébergée dans un navigateur web.  
  
- Pages compilées dans une application autonome et hébergées par une fenêtre de navigation (<xref:System.Windows.Navigation.NavigationWindow>).  
  
- Pages hébergées par un frame (<xref:System.Windows.Controls.Frame>) qui peut être hébergé dans une page autonome, ou page compilée dans une [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ou une application autonome.  
  
 Pour faciliter la navigation, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] implémente les éléments suivants :  
  
- <xref:System.Windows.Navigation.NavigationService>, le moteur de navigation partagé pour traiter les demandes de navigation qui est utilisé par <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow> et [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] afin de prendre en charge la navigation intra-applications.  
  
- Méthodes de navigation pour lancer la navigation.  
  
- Événements de navigation pour suivre et interagir avec la durée de vie de la navigation.  
  
- Mémorisation de la navigation en avant et en arrière à l’aide d’un journal pouvant également être inspecté et manipulé.  
  
 Pour plus d’informations, consultez [Vue d’ensemble de la navigation](navigation-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] prend également en charge un type spécial de navigation appelé « navigation structurée ». La navigation structurée peut être utilisée pour appeler une ou plusieurs pages qui retournent des données de manière structurée et prévisible cohérente avec les appels de fonctions. Cette fonction dépend de la classe <xref:System.Windows.Navigation.PageFunction%601>, décrite plus loin dans [Vue d’ensemble de la navigation structurée](structured-navigation-overview.md). <xref:System.Windows.Navigation.PageFunction%601> permet également de simplifier la création de topologies de navigation complexes, décrites dans [Vue d’ensemble des topologies de navigation](navigation-topologies-overview.md).  
  
<a name="Hosting"></a>   
## <a name="hosting"></a>Hébergement  
 les [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] peuvent être hébergés dans Microsoft Internet Explorer ou Firefox. Chaque modèle d’hébergement possède son propre ensemble de considérations et de contraintes qui sont couvertes dans la rubrique [Hébergement d’applications WPF](hosting-wpf-applications.md).  
  
<a name="Build_and_Deploy"></a>   
## <a name="build-and-deploy"></a>Génération et déploiement  
 Bien que des applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] simples puissent être générées à partir d’une invite de commandes utilisant des compilateurs de ligne de commande, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] s’intègre à [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] pour assurer une prise en charge supplémentaire qui simplifie le développement et le processus de génération. Pour plus d’informations, consultez [Génération d’une application WPF](building-a-wpf-application-wpf.md).  
  
 Selon le type d’application que vous générez, vous avez le choix entre une ou plusieurs options de déploiement. Pour plus d’informations, consultez [Déploiement d’une application WPF](deploying-a-wpf-application-wpf.md).  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Vue d’ensemble de la gestion d’applications](application-management-overview.md)|Fournit une vue d’ensemble de la classe <xref:System.Windows.Application>, dont la gestion de la durée de vie de l’application, des fenêtres, des ressources de l’application et de la navigation.|  
|[Fenêtres dans les applications WPF](windows-in-wpf-applications.md)|Fournit des détails sur la gestion des fenêtres dans votre application, notamment la manière d’utiliser la classe <xref:System.Windows.Window> et les boîtes de dialogue.|  
|[Vue d’ensemble de la navigation](navigation-overview.md)|Fournit une vue d’ensemble de la gestion de la navigation entre les pages de votre application.|  
|[Hébergement](hosting-wpf-applications.md)|Présente une vue d'ensemble de [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].|  
|[Génération et déploiement d’applications WPF](building-and-deploying-wpf-applications.md)|Décrit comment générer et déployer votre application WPF.|  
|[Présentation de WPF dans Visual Studio](../getting-started/introduction-to-wpf-in-vs.md)|Décrit les principales fonctionnalités de WPF.|  
|[Procédure pas à pas : ma première application de bureau WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)|Procédure pas à pas qui indique comment créer une application WPF à l’aide de la navigation entre les pages, la disposition, les contrôles, les images, les styles et la liaison.|
