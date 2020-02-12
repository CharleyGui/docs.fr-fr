---
title: Modules complémentaires de Firefox pour la prise en charge du déploiement d'applications .NET
ms.date: 03/30/2017
helpviewer_keywords:
- Firefox add-ons for .NET application deployment
- WPF plug-in for Firefox
- .NET application deployment [WPF], deploying with Firefox add-ons
- .NET Framework Assistant for Firefox
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
ms.openlocfilehash: 56f5f633092d8aa0bfabdb0570ec26f14221838d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124609"
---
# <a name="firefox-add-ons-to-support-net-application-deployment"></a>Modules complémentaires de Firefox pour la prise en charge du déploiement d'applications .NET
Le plug-in Windows Presentation Foundation (WPF) pour Firefox et l’Assistant .NET Framework pour Firefox autorisent les applications de navigateur XAML (XBAP), les [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]libres et les applications ClickOnce à fonctionner avec le navigateur Mozilla Firefox.  
  
## <a name="wpf-plug-in-for-firefox"></a>Plug-in WPF pour Firefox  
 Le plug-in WPF pour Firefox permet d’accéder aux applications XBAP et aux fichiers [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] libres, et de les exécuter au niveau supérieur ou dans un IFRAME HTML dans le navigateur Firefox. Une application XBAP est une application WPF qui peut être publiée sur un serveur Web et lancée dans des navigateurs pris en charge. Le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] libre est un fichier XAML qui peut être parcouru et affiché dans les navigateurs pris en charge, de manière similaire à un fichier XML.  
  
 Le plug-in WPF de Firefox est installé avec le .NET Framework 3,5. La fenêtre 7 inclut le .NET Framework 3,5, mais n’inclut pas le plug-in WPF pour Firefox. Vous ne pouvez pas installer le plug-in WPF pour Firefox sur Windows 7.  
  
 Le .NET Framework 4 n’inclut pas le plug-in WPF pour Firefox. Toutefois, si les .NET Framework 3,5 et .NET Framework 4 sont installés, le plug-in WPF de Firefox est installé avec le .NET Framework 3,5. Par conséquent, .NET Framework 4 applications continueront à s’exécuter, car l’hôte WPF chargera la version appropriée du Framework. Pour plus d’informations, consultez [hôte WPF (PresentationHost. exe)](wpf-host-presentationhost-exe.md).  
  
## <a name="net-framework-assistant-for-firefox"></a>assistant .NET Framework pour Firefox  
 L’Assistant .NET Framework pour Firefox permet aux applications ClickOnce autonomes de s’exécuter à partir du navigateur Firefox. L’Assistant .NET Framework pour Firefox fonctionne de manière identique lorsqu’il est installé avant et après le navigateur Firefox. Lorsque le navigateur Firefox est lancé et que la .NET Framework 3,5 SP1 est installée, Firefox recherche et installe l’Assistant .NET Framework pour Firefox. Les utilisateurs peuvent configurer l’Assistant .NET Framework pour Firefox pour effectuer les opérations suivantes :  
  
- Invite avant l’exécution de l’application ClickOnce.  
  
- Signale toutes les versions installées du .NET Framework ou simplement la version la plus récente.  
  
 L’Assistant .NET Framework pour Firefox est inclus dans le .NET Framework 3,5 SP1. Pour plus d’informations sur la suppression de l’Assistant .NET Framework pour Firefox, consultez [Comment supprimer l’assistant .NET Framework pour Firefox](https://support.microsoft.com/help/963707/how-to-remove-the-net-framework-assistant-for-firefox).  
  
## <a name="see-also"></a>Voir aussi

- [Déploiement d’une application WPF](deploying-a-wpf-application-wpf.md)
- [Vue d’ensemble des applications du navigateur XAML WPF](wpf-xaml-browser-applications-overview.md)
- [Détecter si le plug-in WPF de Firefox est installé](how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)
