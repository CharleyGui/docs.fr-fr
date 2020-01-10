---
title: Vue d'ensemble des régions de technologie
ms.date: 03/30/2017
helpviewer_keywords:
- window regions [WPF]
- Win32 code [WPF], WPF interoperation
- Win32 code [WPF], airspace
- airspace [WPF]
- interoperability [WPF], airspace
- Win32 code [WPF], window regions
ms.assetid: b7cc350f-b9e2-48b1-be14-60f3d853222e
ms.openlocfilehash: 0b6ad222737f992da3074770fb5a2bff17860c00
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740293"
---
# <a name="technology-regions-overview"></a>Vue d'ensemble des régions de technologie
Si plusieurs technologies de présentation sont utilisées dans une application (par exemple, WPF, Win32 ou DirectX), elles doivent partager les zones de rendu dans une fenêtre de niveau supérieur commune. Cette rubrique décrit les problèmes qui peuvent avoir un impact sur la présentation et les entrées de votre application d’interopérabilité WPF.  
  
## <a name="regions"></a>Régions  
 Dans une fenêtre de niveau supérieur, vous pouvez conceptualiser que chaque HWND avec l’une des technologies d’une application d’interopérabilité dispose de sa propre région (également appelée espace de rendu, ou « airspace » en anglais). Chaque pixel de la fenêtre appartient à un seul HWND, qui constitue la région de ce HWND. (En réalité, il existe plusieurs régions [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] s’il y a plusieurs [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND, mais pour les besoins de cette discussion, vous pouvez supposer qu’il n’en existe qu’une seule.) Le concept de région implique que toutes les couches ou autres fenêtres qui tentent d’effectuer un rendu par-dessus ce pixel pendant la durée de vie de l’application doivent utiliser la même technologie de niveau de rendu. Toute tentative de rendu d' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pixels sur Win32 entraîne des résultats indésirables, et n’est pas autorisée dans la mesure du possible via les API d’interopérabilité.  
  
### <a name="region-examples"></a>Exemples de régions  
 L’illustration suivante montre une application qui combine Win32, DirectX et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Chaque technologie utilise son propre jeu distinct de pixels, sans chevauchement, ce qui évite les problèmes entre les régions.  
  
 ![Exemple d’application qui mixe Win32, DirectX et WPF.](./media/technology-regions-overview/win32-directx-windows-presentation-foundation-application.png)  
  
 Supposez que cette application utilise la position du pointeur de la souris pour créer une animation qui tente de s’afficher sur l’une de ces trois régions. Quelle que soit la technologie responsable de l’animation proprement dite, cette technologie donne lieu à une violation des deux autres régions. L’illustration suivante montre une tentative de rendu d’un cercle WPF sur une région Win32.  
  
 ![Tentative de rendu d’un cercle WPF sur une région Win32.](./media/technology-regions-overview/render-windows-presentation-foundation-circle-over-win32-region.png)  
  
 Si vous essayez d’utiliser la transparence ou simulation de transparence entre des technologies différentes, cela constitue également une violation.  Dans l’illustration suivante, la zone de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] enfreint les régions Win32 et DirectX. Étant donné que les pixels de cette boîte de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont semi-transparents, ils doivent être détenus conjointement par DirectX et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ce qui n’est pas possible.  Cela constitue donc une autre violation, le rendu ne peut pas être effectué.  
  
 ![Diagramme montrant une zone WPF enfreignant les régions Win32 et DirectX.](./media/technology-regions-overview/windows-foundation-presentation-box-violate-win32-directx-region.png)  
  
 Les trois exemples précédents ont utilisé des régions rectangulaires, mais des formes différentes sont possibles.  Par exemple, une région peut présenter un espace. L’illustration suivante montre une région Win32 avec un trou rectangulaire. il s’agit de la taille des [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et des régions DirectX combinées.  
  
 ![Diagramme montrant une région Win32 avec un trou rectangulaire.](./media/technology-regions-overview/win32-region-rectangular-hole.png)  
  
 Les régions peuvent également être entièrement non rectangulaires ou toute forme autre par un HRGN Win32 (région).  
  
 ![Diagramme qui affiche une zone non rectangulaire.](./media/technology-regions-overview/nonrectangular-win32-region.png)  
  
## <a name="transparency-and-top-level-windows"></a>Transparence et fenêtres de niveau supérieur  
 Le gestionnaire de fenêtres dans Windows traite uniquement les HWND Win32. Par conséquent, chaque [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> est un HWND. Le HWND <xref:System.Windows.Window> doit respecter les règles générales de tous les HWND. Dans ce HWND, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code peut faire tout ce qui est pris en charge par l’ensemble des API [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Toutefois, pour les interactions avec d’autres HWND sur le bureau, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] doit respecter les règles de traitement et de rendu Win32.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prend en charge les fenêtres non rectangulaires à l’aide des API Win32, hrgn pour les fenêtres non rectangulaires et les fenêtres superposées pour une alpha par pixel.  
  
 Les clés de couleur et les valeurs alpha constantes ne sont pas prises en charge.  Les fonctionnalités de fenêtre superposée Win32 varient selon la plateforme.  
  
 Les fenêtres superposées peuvent rendre toute la fenêtre translucide (semi-transparente) en spécifiant une valeur alpha à appliquer à chaque pixel de la fenêtre.  (En fait, Win32 prend en charge l’alpha par pixel, mais il est très difficile à utiliser dans les programmes pratiques, car dans ce mode, vous devez dessiner vous-même tous les HWND enfants, y compris les boîtes de dialogue et les listes déroulantes).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prend en charge hrgn ; Toutefois, il n’existe aucune API managée pour cette fonctionnalité. Vous pouvez utiliser l’appel de code non managé et <xref:System.Windows.Interop.HwndSource> pour appeler les API Win32 pertinentes. Pour plus d’informations, consultez [Appel à des fonctions natives à partir de code managé](/cpp/dotnet/calling-native-functions-from-managed-code).  
  
 Les fenêtres superposées [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ont des fonctionnalités différentes en fonction des systèmes d’exploitation. En effet, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise DirectX pour le rendu, et les fenêtres superposées étaient principalement conçues pour le rendu GDI, et non pour le rendu DirectX.  
  
- WPF prend en charge les fenêtres superposées à accélération matérielle.  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ne prend pas en charge les clés de couleur de transparence, car [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ne peut pas garantir l’affichage de la couleur exacte demandée, surtout s’il s’agit d’un rendu à accélération matérielle.  
  
## <a name="see-also"></a>Voir aussi

- [Interopérabilité WPF et Win32](wpf-and-win32-interoperation.md)
- [Procédure pas à pas : hébergement d'un WPF Clock dans Win32](walkthrough-hosting-a-wpf-clock-in-win32.md)
- [Hébergement de contenu Win32 dans WPF](hosting-win32-content-in-wpf.md)
