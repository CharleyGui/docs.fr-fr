---
title: Déployer une application
description: Explorez les technologies de déploiement que Windows et le .NET Framework utiliser pour les applications Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
ms.openlocfilehash: 62904ccd47800c8340d68c223e50688902170063
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619297"
---
# <a name="deploy-a-wpf-application"></a>Déployer une application WPF

Une fois les applications Windows Presentation Foundation (WPF) générées, elles doivent être déployées. Windows et le .NET Framework incluent plusieurs technologies de déploiement. La technologie de déploiement utilisée pour déployer une application WPF dépend du type d’application. Cette rubrique fournit une brève présentation de chaque technologie de déploiement et explique comment elles sont utilisées conjointement avec les exigences de déploiement de chaque type d’application WPF.

<a name="Deployment_Technologies"></a>
## <a name="deployment-technologies"></a>Technologies de déploiement  
 Windows et le .NET Framework incluent plusieurs technologies de déploiement, notamment :  
  
- Déploiement XCopy.  
  
- Windows Installer déploiement.  
  
- Déploiement ClickOnce.  
  
<a name="XCopy_Deployment"></a>
### <a name="xcopy-deployment"></a>Déploiement XCopy  
 Le déploiement XCopy fait référence à l’utilisation du programme en ligne de commande XCopy pour copier les fichiers d’un emplacement vers un autre. Le déploiement XCopy convient dans les cas suivants :  
  
- L’application est autonome. Elle n’a pas besoin de mettre à jour le client pour fonctionner.  
  
- Les fichiers d’application doivent être déplacés d’un emplacement à un autre, par exemple à partir d’un emplacement de build (disque local, partage de fichiers UNC, etc.) vers un emplacement de publication (site Web, partage de fichiers UNC, etc.).  
  
- L’application ne nécessite pas d’interface intégrée (raccourci du menu Démarrer, icône sur le Bureau, et ainsi de suite).  
  
 XCopy convient pour les scénarios de déploiement simples. Toutefois, il est limité quand des fonctions de déploiement plus complexes sont requises. En particulier, l’utilisation de XCopy entraîne souvent une surcharge de temps afin de créer, d’exécuter et de gérer des scripts permettant de gérer le déploiement de manière fiable. En outre, XCopy ne prend pas en charge la gestion de version, la désinstallation ni la restauration.  
  
<a name="Windows_Installer"></a>
### <a name="windows-installer"></a>Windows Installer  
 Windows Installer permet aux applications d’être empaquetées comme des fichiers exécutables autonomes qui peuvent être facilement distribués aux clients et exécutés. En outre, Windows Installer est installé avec Windows et permet l’intégration avec le bureau, le menu Démarrer et le panneau de configuration programmes.  
  
 Windows Installer simplifie l’installation et la désinstallation d’applications, mais il ne fournit pas de fonctions permettant de s’assurer que les applications installées sont tenues à jour du point de vue du contrôle de version.  
  
 Pour plus d’informations sur la Windows Installer, consultez [Windows Installer le déploiement](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).
  
<a name="ClickOnce_Deployment"></a>
### <a name="clickonce-deployment"></a>Déploiement ClickOnce  
 ClickOnce permet le déploiement d’applications de style Web pour les applications non-Web. Les applications sont publiées vers et déployées depuis des serveurs de fichiers ou web. Bien que ClickOnce ne prenne pas en charge la gamme complète des fonctionnalités clientes prises par Windows Installer applications installées, il prend en charge un sous-ensemble qui comprend les éléments suivants :  
  
- Intégration au menu Démarrer et au Panneau de configuration des programmes.  
  
- Gestion de version, restauration et désinstallation.  
  
- Mode d’installation en ligne, qui lance toujours une application à partir de l’emplacement de déploiement.  
  
- Mise à jour automatique quand de nouvelles versions sont disponibles.  
  
- Inscription d’extensions de fichiers.  
  
 Pour plus d’informations sur ClickOnce, consultez [sécurité et déploiement ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment).  
  
<a name="Deploying_WPF_Applications"></a>
## <a name="deploying-wpf-applications"></a>Déploiement d’applications WPF  
 Les options de déploiement pour une application WPF dépendent du type d’application. Du point de vue du déploiement, WPF a trois types d’applications significatifs :  
  
- Applications autonomes.  
  
- Applications [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] à balisage.  
  
- Applications de navigateur XAML (XBAP).  
  
<a name="Deploying_Standalone_Applications"></a>
### <a name="deploying-standalone-applications"></a>Déploiement d’applications autonomes  
 Les applications autonomes sont déployées à l’aide de ClickOnce ou de Windows Installer. Dans tous les cas, pour pouvoir être exécutées, les applications autonomes nécessitent un niveau de confiance totale. La confiance totale est accordée automatiquement aux applications autonomes déployées à l’aide de Windows Installer. Les applications autonomes déployées à l’aide de ClickOnce ne bénéficient pas automatiquement d’une confiance totale. Au lieu de cela, ClickOnce affiche une boîte de dialogue d’avertissement de sécurité que les utilisateurs doivent accepter avant l’installation d’une application autonome. Si l’avertissement est accepté, l’application autonome est installée et bénéficie de la confiance totale. Dans le cas contraire, l’application autonome n’est pas installée.  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>
### <a name="deploying-markup-only-xaml-applications"></a>Déploiement d’applications XAML à balisage  
 Les pages à balisage uniquement [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sont généralement publiées sur des serveurs Web, comme des pages HTML, et peuvent être affichées à l’aide d’Internet Explorer. Les pages [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] à balisage sont exécutées dans un bac à sable (sandbox) de sécurité de confiance partielle en fonction de restrictions définies par le jeu d’autorisations de la zone Internet. Cela fournit un bac à sable (sandbox) de sécurité équivalent aux applications Web HTML.  
  
 Pour plus d’informations sur la sécurité des applications WPF, consultez [sécurité](../security-wpf.md).  
  
 Les pages à balisage uniquement [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] peuvent être installées dans le système de fichiers local à l’aide de xcopy ou de Windows Installer. Ces pages peuvent être affichées à l’aide d’Internet Explorer ou de l’Explorateur Windows.  
  
 Pour plus d’informations sur XAML, consultez [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md).  
  
<a name="Deploying_XAML_Browser_Applications"></a>
### <a name="deploying-xaml-browser-applications"></a>Déploiement d’applications du navigateur XAML  
 Les applications XBAP sont des applications compilées qui nécessitent le déploiement des trois fichiers suivants :  
  
- *NomApplication*.exe : fichier d’application de l’assembly exécutable.  
  
- *NomApplication*.xbap : manifeste de déploiement.  
  
- *NomApplication*.exe.manifest : manifeste d’application.  
  
> [!NOTE]
> Pour plus d’informations sur les manifestes de déploiement et d’application, consultez [Génération d’une application WPF](building-a-wpf-application-wpf.md).  
  
 Ces fichiers sont générés lors de la génération d’une application XBAP. Pour plus d’informations, consultez [Guide pratique pour créer un projet d’application de navigateur WPF](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100)). Comme les pages à balisage uniquement [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , les XBAP sont généralement publiées sur un serveur Web et affichées à l’aide d’Internet Explorer.  
  
 Les applications XBAP peuvent être déployées sur les clients à l’aide de l’une des techniques de déploiement. Toutefois, ClickOnce est recommandé, car il offre les fonctionnalités suivantes :  
  
1. Mises à jour automatiques quand une nouvelle version est publiée.  
  
2. Privilèges d’élévation pour le XBAP exécuté avec un niveau de confiance totale.  
  
 Par défaut, ClickOnce publie les fichiers d’application avec l’extension .deploy. Cela peut s’avérer problématique, mais peut être désactivé. Pour plus d’informations, consultez [Problèmes de configuration de serveur et de client lors de déploiements ClickOnce](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments).  
  
 Pour plus d’informations sur le déploiement d’applications de navigateur XAML (XBAP), consultez [vue d’ensemble des applications de navigateur XAML WPF](wpf-xaml-browser-applications-overview.md).  
  
<a name="Installing__NET_Framework_3_0"></a>
## <a name="installing-the-net-framework"></a>Installation du .NET Framework  
 Pour exécuter une application WPF, le Microsoft .NET Framework doit être installé sur le client. Internet Explorer détecte automatiquement si les clients sont installés avec .NET Framework lorsque les applications hébergées dans le navigateur WPF sont affichées. Si le .NET Framework n’est pas installé, Internet Explorer invite l’utilisateur à l’installer.  
  
 Pour détecter si la .NET Framework est installée, Internet Explorer comprend une application de programme d’amorçage qui est inscrite en tant que gestionnaire MIME (Multipurpose Internet Mail Extensions) de secours pour les fichiers de contenu ayant les extensions suivantes :. xaml,. XPS,. XBAP et. application. Si vous accédez à ces types de fichiers et que le .NET Framework n’est pas installé sur le client, l’application du programme d’amorçage demande l’autorisation de l’installer. Si aucune autorisation n’est fournie, le .NET Framework ou l’application n’est pas installé.  
  
 Si l’autorisation est accordée, Internet Explorer télécharge et installe le .NET Framework à l’aide de Microsoft Service de transfert intelligent en arrière-plan (BITS). Une fois l’installation de la .NET Framework réussie, le fichier demandé à l’origine est ouvert dans une nouvelle fenêtre de navigateur.  
  
 Pour plus d’informations, consultez [Déploiement d’applications et du .NET Framework](../../deployment/index.md).  
  
## <a name="see-also"></a>Voir aussi

- [Génération d'une application WPF](building-a-wpf-application-wpf.md)
- [Sécurité](../security-wpf.md)
