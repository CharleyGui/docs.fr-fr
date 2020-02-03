---
title: Hôte WPF (PresentationHost.exe)
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: bda7efbb1b7a4760199215bdb58c12b3063e290c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743401"
---
# <a name="wpf-host-presentationhostexe"></a>Hôte WPF (PresentationHost.exe)
L’hôte Windows Presentation Foundation (WPF) (PresentationHost. exe) est l’application qui permet aux applications WPF d’être hébergées dans des navigateurs compatibles (y compris Microsoft Internet Explorer 6 et versions ultérieures). Par défaut, l’hôte Windows Presentation Foundation (WPF) est inscrit en tant que gestionnaire de Shell et de MIME pour le contenu WPF hébergé par le navigateur, ce qui comprend les éléments suivants :  
  
- les fichiers [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (.xaml) libre (non compilés) ;  
  
- Application du navigateur XAML (XBAP) (. XBAP).  
  
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
|-event \<eventname>|Ouvrez l’événement portant ce nom et signalez-le quand PresentationHost. exe est initialisé et prêt à héberger du contenu WPF. PresentationHost.exe se termine si une erreur se produit à l’ouverture de l’événement, par exemple s’il n’a pas encore été créé.|  
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

- [Sécurité](../security-wpf.md)
