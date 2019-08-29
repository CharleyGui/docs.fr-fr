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
ms.openlocfilehash: 4f1489065a70065700d2f8ceb974e66ecceeebd0
ms.sourcegitcommit: 77e33b682db39955e331b8e8eda4ef1925a24e78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70133812"
---
# <a name="technology-regions-overview"></a>Vue d'ensemble des régions de technologie
Si plusieurs technologies de présentation sont utilisées dans une application (par exemple, WPF, Win32 ou DirectX), elles doivent partager les zones de rendu dans une fenêtre de niveau supérieur commune. Cette rubrique décrit les problèmes qui peuvent avoir un impact sur la présentation et les entrées de votre application d’interopérabilité WPF.  
  
## <a name="regions"></a>Régions  
 Dans une fenêtre de niveau supérieur, vous pouvez conceptualiser que chaque HWND avec l’une des technologies d’une application d’interopérabilité dispose de sa propre région (également appelée espace de rendu, ou « airspace » en anglais). Chaque pixel de la fenêtre appartient à un seul HWND, qui constitue la région de ce HWND. (En réalité, il existe plusieurs régions [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] s’il y a plusieurs [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND, mais pour les besoins de cette discussion, vous pouvez supposer qu’il n’en existe qu’une seule.) Le concept de région implique que toutes les couches ou autres fenêtres qui tentent d’effectuer un rendu par-dessus ce pixel pendant la durée de vie de l’application doivent utiliser la même technologie de niveau de rendu. Si vous tentez de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] restituer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] des pixels sur des résultats indésirables, le plus possible est interdit via les API d’interopérabilité.  
  
### <a name="region-examples"></a>Exemples de régions  
 L’illustration suivante montre une application qui mélange [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], DirectX et. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Chaque technologie utilise son propre jeu distinct de pixels, sans chevauchement, ce qui évite les problèmes entre les régions.  
  
 ![Exemple d’application qui mixe Win32, DirectX et WPF.](./media/technology-regions-overview/win32-directx-windows-presentation-foundation-application.png)  
  
 Supposez que cette application utilise la position du pointeur de la souris pour créer une animation qui tente de s’afficher sur l’une de ces trois régions. Quelle que soit la technologie responsable de l’animation proprement dite, cette technologie donne lieu à une violation des deux autres régions. L’illustration suivante montre une tentative de rendu d’un cercle WPF sur une région Win32.  
  
 ![Tentative de rendu d’un cercle WPF sur une région Win32.](./media/technology-regions-overview/render-windows-presentation-foundation-circle-over-win32-region.png)  
  
 Si vous essayez d’utiliser la transparence ou simulation de transparence entre des technologies différentes, cela constitue également une violation.  Dans l’illustration suivante, la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zone enfreint les [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] régions et DirectX. Étant donné que les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pixels dans cette zone sont semi-transparents, ils doivent être détenus conjointement par DirectX [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]et, ce qui n’est pas possible.  Cela constitue donc une autre violation, le rendu ne peut pas être effectué.  
  
 ![Diagramme montrant une zone WPF enfreignant les régions Win32 et DirectX.](./media/technology-regions-overview/windows-foundation-presentation-box-violate-win32-directx-region.png)  
  
 Les trois exemples précédents ont utilisé des régions rectangulaires, mais des formes différentes sont possibles.  Par exemple, une région peut présenter un espace. L’illustration suivante montre une [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] région avec un trou rectangulaire. il s’agit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de la taille des régions DirectX combinées.  
  
 ![Diagramme montrant une région Win32 avec un trou rectangulaire.](./media/technology-regions-overview/win32-region-rectangular-hole.png)  
  
 Les régions peuvent également avoir une forme non rectangulaire, ou toute autre forme qui peut être décrite par un HRGN [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] (région).  
  
 ![Diagramme qui affiche une zone non rectangulaire.](./media/technology-regions-overview/nonrectangular-win32-region.png)  
  
## <a name="transparency-and-top-level-windows"></a>Transparence et fenêtres de niveau supérieur  
 Le Gestionnaire de fenêtrage Windows ne traite vraiment que les HWND [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Par conséquent, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] chaque <xref:System.Windows.Window> est un HWND. Le <xref:System.Windows.Window> HWND doit respecter les règles générales pour tous les HWND. Dans ce HWND, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le code peut faire tout ce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui est pris en charge par les API globales. Pour les interactions avec d’autres HWND sur les postes de travail, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] doit se conformer aux règles de traitement et de rendu de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]prend en charge les fenêtres non rectangulaires à l’aide [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] d’API, hrgn pour les fenêtres non rectangulaires et les fenêtres superposées pour une alpha par pixel.  
  
 Les clés de couleur et les valeurs alpha constantes ne sont pas prises en charge.  Les fonctionnalités de fenêtre superposée de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] varient selon la plateforme.  
  
 Les fenêtres superposées peuvent rendre toute la fenêtre translucide (semi-transparente) en spécifiant une valeur alpha à appliquer à chaque pixel de la fenêtre.  (En fait, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] prend en charge l’alpha par pixel, mais il est très difficile à utiliser concrètement dans les programmes, car dans ce mode, vous devez dessiner les enfants HWND vous-même, y compris les boîtes de dialogue et les menus déroulants.)  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]prend en charge hrgn; Toutefois, il n’existe aucune API managée pour cette fonctionnalité. Vous pouvez utiliser l’appel de <xref:System.Windows.Interop.HwndSource> code non managé et [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] appeler les API pertinentes. Pour plus d’informations, consultez [Appel à des fonctions natives à partir de code managé](/cpp/dotnet/calling-native-functions-from-managed-code).  
  
 Les fenêtres superposées [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ont des fonctionnalités différentes en fonction des systèmes d’exploitation. Cela est dû [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] au fait que utilise DirectX pour le rendu et que les fenêtres superposées étaient principalement conçues pour le rendu GDI, et non pour le rendu DirectX.  
  
- WPF prend en charge les fenêtres superposées à accélération matérielle.  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ne prend pas en charge les clés de couleur de transparence, car [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ne peut pas garantir l’affichage de la couleur exacte demandée, surtout s’il s’agit d’un rendu à accélération matérielle.  
  
## <a name="see-also"></a>Voir aussi

- [Interopérabilité WPF et Win32](wpf-and-win32-interoperation.md)
- [Procédure pas à pas : Hébergement d’une horloge WPF dans Win32](walkthrough-hosting-a-wpf-clock-in-win32.md)
- [Hébergement de contenu Win32 dans WPF](hosting-win32-content-in-wpf.md)
