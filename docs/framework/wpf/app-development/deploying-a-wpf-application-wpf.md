---
title: Déployer une application
ms.date: 03/30/2017
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
ms.openlocfilehash: 54d14503a0f65bb50f2dfb14d40af3b47d51589c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186314"
---
# <a name="deploy-a-wpf-application"></a>Déployer une application WPF

Une fois les applications de la Windows Presentation Foundation (WPF) construites, elles doivent être déployées. Windows et le cadre .NET comprennent plusieurs technologies de déploiement. La technologie de déploiement utilisée pour déployer une application WPF dépend du type d’application. Ce sujet fournit un bref aperçu de chaque technologie de déploiement et de la façon dont elles sont utilisées en conjonction avec les exigences de déploiement de chaque type d’application WPF.

<a name="Deployment_Technologies"></a>
## <a name="deployment-technologies"></a>Technologies de déploiement  
 Windows et le cadre .NET comprennent plusieurs technologies de déploiement, y compris :  
  
- Déploiement XCopy.  
  
- Déploiement de l’installateur Windows.  
  
- Déploiement ClickOnce.  
  
<a name="XCopy_Deployment"></a>
### <a name="xcopy-deployment"></a>Déploiement XCopy  
 Le déploiement XCopy fait référence à l’utilisation du programme en ligne de commande XCopy pour copier les fichiers d’un emplacement vers un autre. Le déploiement XCopy convient dans les cas suivants :  
  
- L’application est autonome. Elle n’a pas besoin de mettre à jour le client pour fonctionner.  
  
- Les fichiers de demande doivent être transférés d’un endroit à l’autre, par exemple d’un emplacement de construction (disque local, part de fichier UNC, et ainsi de suite) à un emplacement de publication (site Web, partage de fichiers UNC, et ainsi de suite).  
  
- L’application ne nécessite pas d’interface intégrée (raccourci du menu Démarrer, icône sur le Bureau, et ainsi de suite).  
  
 XCopy convient pour les scénarios de déploiement simples. Toutefois, il est limité quand des fonctions de déploiement plus complexes sont requises. En particulier, l’utilisation de XCopy entraîne souvent une surcharge de temps afin de créer, d’exécuter et de gérer des scripts permettant de gérer le déploiement de manière fiable. En outre, XCopy ne prend pas en charge la gestion de version, la désinstallation ni la restauration.  
  
<a name="Windows_Installer"></a>
### <a name="windows-installer"></a>Windows Installer  
 Windows Install permet d’emballer les applications comme exécutables autonomes qui peuvent être facilement distribués aux clients et exécutés. En outre, Windows Install est installé avec Windows et permet l’intégration avec le bureau, le menu Démarrer et le panneau de contrôle des programmes.  
  
 Windows Installer simplifie l’installation et la désinstallation des applications, mais il ne fournit pas d’installations pour s’assurer que les applications installées sont mises à jour d’un point de vue de version.  
  
 Pour plus d’informations sur Windows Install, voir [déploiement d’installateur Windows](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).
  
<a name="ClickOnce_Deployment"></a>
### <a name="clickonce-deployment"></a>Déploiement ClickOnce  
 ClickOnce permet le déploiement d’applications de type Web pour les applications non-Web. Les applications sont publiées vers et déployées depuis des serveurs de fichiers ou web. Bien que ClickOnce ne prend pas en charge la gamme complète des fonctionnalités client que les applications installées par Windows Installer ne, il prend en charge un sous-ensemble qui comprend ce qui suit:  
  
- Intégration au menu Démarrer et au Panneau de configuration des programmes.  
  
- Gestion de version, restauration et désinstallation.  
  
- Mode d’installation en ligne, qui lance toujours une application à partir de l’emplacement de déploiement.  
  
- Mise à jour automatique quand de nouvelles versions sont disponibles.  
  
- Inscription d’extensions de fichiers.  
  
 Pour plus d’informations sur ClickOnce, voir [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).  
  
<a name="Deploying_WPF_Applications"></a>
## <a name="deploying-wpf-applications"></a>Déploiement d’applications WPF  
 Les options de déploiement d’une application WPF dépendent du type d’application. Du point de vue du déploiement, WPF dispose de trois types d’applications importants :  
  
- Applications autonomes.  
  
- Applications [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] à balisage.  
  
- Applications de navigateur XAML (XBAP).  
  
<a name="Deploying_Standalone_Applications"></a>
### <a name="deploying-standalone-applications"></a>Déploiement d’applications autonomes  
 Les applications autonomes sont déployées à l’aide de ClickOnce ou de Windows Install. Dans tous les cas, pour pouvoir être exécutées, les applications autonomes nécessitent un niveau de confiance totale. La pleine confiance est automatiquement accordée aux applications autonomes déployées à l’aide de Windows Installer. Les applications autonomes déployées à l’aide de ClickOnce ne bénéficient pas automatiquement d’une pleine confiance. Au lieu de cela, ClickOnce affiche un dialogue d’avertissement de sécurité que les utilisateurs doivent accepter avant qu’une application autonome soit installée. Si l’avertissement est accepté, l’application autonome est installée et bénéficie de la confiance totale. Dans le cas contraire, l’application autonome n’est pas installée.  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>
### <a name="deploying-markup-only-xaml-applications"></a>Déploiement d’applications XAML à balisage  
 Les pages [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Markup-only sont généralement publiées sur des serveurs Web, comme les pages HTML, et peuvent être consultées à l’aide d’Internet Explorer. Les pages [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] à balisage sont exécutées dans un bac à sable (sandbox) de sécurité de confiance partielle en fonction de restrictions définies par le jeu d’autorisations de la zone Internet. Cela fournit un bac à sable de sécurité équivalent aux applications Web basées sur HTML.  
  
 Pour plus d’informations sur la sécurité des applications WPF, voir [Sécurité](../security-wpf.md).  
  
 Les pages [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de balisage uniquement peuvent être installées sur le système de fichiers local en utilisant XCopy ou Windows Install. Ces pages peuvent être consultées à l’aide d’Internet Explorer ou de Windows Explorer.  
  
 Pour plus d’informations sur XAML, consultez [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md).  
  
<a name="Deploying_XAML_Browser_Applications"></a>
### <a name="deploying-xaml-browser-applications"></a>Déploiement d’applications du navigateur XAML  
 Les XAP sont des applications compilées qui exigent le déploiement des trois fichiers suivants :  
  
- *NomApplication*.exe : fichier d’application de l’assembly exécutable.  
  
- *NomApplication*.xbap : manifeste de déploiement.  
  
- *NomApplication*.exe.manifest : manifeste d’application.  
  
> [!NOTE]
> Pour plus d’informations sur les manifestes de déploiement et d’application, consultez [Génération d’une application WPF](building-a-wpf-application-wpf.md).  
  
 Ces fichiers sont produits lors de la construction d’un XBAP. Pour plus d’informations, consultez [Guide pratique pour créer un projet d’application de navigateur WPF](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100)). Comme les pages [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de balisage seulement, les XAP sont généralement publiés sur un serveur Web et consultés à l’aide d’Internet Explorer.  
  
 Les XAP peuvent être déployés aux clients en utilisant l’une ou l’autre des techniques de déploiement. Cependant, ClickOnce est recommandé car il fournit les capacités suivantes:  
  
1. Mises à jour automatiques quand une nouvelle version est publiée.  
  
2. Privilèges d’élévation pour le XBAP en cours d’exécution avec pleine confiance.  
  
 Par défaut, ClickOnce publie les fichiers d’application avec l’extension .deploy. Cela peut s’avérer problématique, mais peut être désactivé. Pour plus d’informations, consultez [Problèmes de configuration de serveur et de client lors de déploiements ClickOnce](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments).  
  
 Pour plus d’informations sur le déploiement des applications de navigateur XAML (XBAP), voir [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md).  
  
<a name="Installing__NET_Framework_3_0"></a>
## <a name="installing-the-net-framework"></a>Installation du .NET Framework  
 Pour exécuter une application WPF, le cadre Microsoft .NET doit être installé sur le client. Internet Explorer détecte automatiquement si les clients sont installés avec .NET Framework lorsque les applications hébergées par le navigateur WPF sont consultées. Si le cadre .NET n’est pas installé, Internet Explorer invite les utilisateurs à l’installer.  
  
 Pour détecter si le cadre .NET est installé, Internet Explorer comprend une application bootstrapper qui est enregistré comme le repli Multipurpose Internet Mail Extensions (MIME) gestionnaire pour les fichiers de contenu avec les extensions suivantes: .xaml, .xps, .xbap , et .application. Si vous naviguez vers ces types de fichiers et que le cadre .NET n’est pas installé sur le client, l’application bootstrapper demande la permission de l’installer. Si l’autorisation n’est pas fournie, ni le cadre .NET ni l’application n’est installé.  
  
 Si l’autorisation est accordée, Internet Explorer télécharge et installe le cadre .NET à l’aide du Microsoft Background Intelligent Transfer Service (BITS). Après l’installation réussie du cadre .NET, le fichier demandé à l’origine est ouvert dans une nouvelle fenêtre de navigateur.  
  
 Pour plus d’informations, consultez [Déploiement d’applications et du .NET Framework](../../deployment/index.md).  
  
## <a name="see-also"></a>Voir aussi

- [Génération d'une application WPF](building-a-wpf-application-wpf.md)
- [Sécurité](../security-wpf.md)
