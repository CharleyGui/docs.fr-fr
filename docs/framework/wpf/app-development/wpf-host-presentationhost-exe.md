---
title: Hôte WPF (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: ec8ec42c174d87834af5d4c651c1e8c8bde3b3e2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581703"
---
# <a name="wpf-host-presentationhostexe"></a>Hôte WPF (PresentationHost.exe)
L’hôte Windows Presentation Foundation (WPF) (PresentationHost. exe) est l’application qui permet à [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications d’être hébergées dans des navigateurs compatibles (y compris Microsoft Internet Explorer 6 et versions ultérieures). Par défaut, l’hôte Windows Presentation Foundation (WPF) est inscrit en tant que gestionnaire d’interpréteur de commandes et de gestionnaire MIME pour le contenu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] hébergé par le navigateur, notamment :  
  
- les fichiers [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (.xaml) libre (non compilés) ;  
  
- l’application [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] (.xbap).  
  
 Pour les fichiers de ces types, Windows Presentation Foundation hôte (WPF) :  
  
- Lance le gestionnaire HTML inscrit pour héberger le contenu Windows Presentation Foundation (WPF).  
  
- Charge les versions appropriées des assemblys common language runtime (CLR) et Windows Presentation Foundation (WPF) requis.  
  
- vérifie la mise en place des niveaux d’autorisation appropriés pour la zone de déploiement.  
  
 Cette rubrique décrit les paramètres de ligne de commande qui peuvent être utilisés avec PresentationHost.exe.  
  
## <a name="usage"></a>Utilisation  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|filename|Chemin du fichier à activer. Peut également être un URI.|  
|-debug|Au moment d’activer une application, n’effectue pas sa validation ou son exécution à partir du magasin. Fonctionne uniquement quand un fichier local est activé.|  
|-debugSecurityZoneURL \<url>|Utilisé avec une valeur d’URL pour indiquer à PresentationHost. exe qu’une application doit être déboguée comme si elle était déployée à partir de l’URL spécifiée. Cela permet de déterminer à la fois la zone de déploiement et le site d’origine.|  
|-embedding|Imposé par OLE. Si le paramètre `-event` ou `-debug` est spécifié, il n’est pas nécessaire de spécifier le paramètre `-embedding`, car celui-ci est défini de façon interne.|  
|-event \<eventname>|Ouvrez l’événement ayant ce nom, puis signalez-le quand PresentationHost.exe est initialisé et prêt à héberger le contenu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. PresentationHost.exe se termine si une erreur se produit à l’ouverture de l’événement, par exemple s’il n’a pas encore été créé.|  
|-launchApplication \<url>|Lance une application ClickOnce autonome à partir de l’URL spécifiée. La stratégie de sécurité Internet Explorer et WinINet concernant les applications .NET sont appliquées.|  
  
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

- [Security](../security-wpf.md)
