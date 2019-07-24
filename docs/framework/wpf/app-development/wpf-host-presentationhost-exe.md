---
title: Hôte WPF (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: 16618042324387bfc15f4685f4759378c50a80b7
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401721"
---
# <a name="wpf-host-presentationhostexe"></a>Hôte WPF (PresentationHost.exe)
L’hôte Windows Presentation Foundation (WPF) (PresentationHost. exe) est l’application qui [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] permet aux applications d’être hébergées dans des navigateurs compatibles (y compris [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] et versions ultérieures). Par défaut, l’hôte Windows Presentation Foundation (WPF) est inscrit en tant que [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] Shell et gestionnaire pour le [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] contenu hébergé par le navigateur, ce qui comprend les éléments suivants:  
  
- les fichiers [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (.xaml) libre (non compilés) ;  
  
- l’application [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] (.xbap).  
  
 Pour les fichiers de ces types, Windows Presentation Foundation hôte (WPF):  
  
- Lance le gestionnaire [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] inscrit pour héberger le contenu Windows Presentation Foundation (WPF).  
  
- Charge les versions appropriées des assemblys common language runtime (CLR) et Windows Presentation Foundation (WPF) requis.  
  
- vérifie la mise en place des niveaux d’autorisation appropriés pour la zone de déploiement.  
  
 Cette rubrique décrit les paramètres de ligne de commande qui peuvent être utilisés avec PresentationHost.exe.  
  
## <a name="usage"></a>Utilisation  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|filename|Chemin du fichier à activer. Il peut également s’agir d’un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].|  
|-debug|Au moment d’activer une application, n’effectue pas sa validation ou son exécution à partir du magasin. Fonctionne uniquement quand un fichier local est activé.|  
|-debugSecurityZoneURL \<url>|Utilisé avec une valeur [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] pour indiquer à PresentationHost.exe qu’une application doit être déboguée comme si elle était déployée à partir de la valeur [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] spécifiée. Cela permet de déterminer à la fois la zone de déploiement et le site d’origine.|  
|-embedding|Imposé par OLE. Si le paramètre `-event` ou `-debug` est spécifié, il n’est pas nécessaire de spécifier le paramètre `-embedding`, car celui-ci est défini de façon interne.|  
|-event \<eventname>|Ouvrez l’événement ayant ce nom, puis signalez-le quand PresentationHost.exe est initialisé et prêt à héberger le contenu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. PresentationHost.exe se termine si une erreur se produit à l’ouverture de l’événement, par exemple s’il n’a pas encore été créé.|  
|-launchApplication \<url>|Lance une application ClickOnce autonome à partir de l’URL spécifiée. Les stratégies de sécurité [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] et WinINet relatives aux applications .NET sont appliquées.|  
  
## <a name="scenarios"></a>Scénarios  
  
### <a name="shell-handler"></a>Gestionnaire d’interpréteur de commandes  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a>Gestionnaire MIME  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a>Débogage Visual Studio  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a>Débogage Visual Studio dans la zone  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a>Voir aussi

- [Sécurité](../security-wpf.md)
