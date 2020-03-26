---
title: Couches de rendu graphiques
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], performance
- rendering graphics [WPF]
- rendering tiers [WPF]
- graphics rendering tiers [WPF]
- graphics [WPF], rendering tiers
ms.assetid: 08dd1606-02a2-4122-9351-c0afd2ec3a70
ms.openlocfilehash: 05847271cf82739a6a0b609771043c02a7ffc0e9
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291589"
---
# <a name="graphics-rendering-tiers"></a>Couches de rendu graphiques
Une couche de rendu définit un niveau des capacités et des performances du matériel graphique pour un appareil qui exécute une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="graphics_hardware"></a>
## <a name="graphics-hardware"></a>Matériel graphique  
 Les fonctionnalités du matériel graphique qui ont le plus d’impact sur les niveaux de la couche de rendu sont les suivantes :  
  
- **RAM vidéo** La quantité de mémoire vidéo sur le matériel graphique détermine la taille et le nombre de mémoires tampon qui peuvent être utilisées pour la composition de graphiques.  
  
- **Nuanceur de pixels** Un nuanceur de pixels est une fonction de traitement des graphiques qui calcule les effets pixel par pixel. En fonction de la résolution des graphiques affichés, il peut y avoir plusieurs millions de pixels à traiter pour chaque image de l’affichage.  
  
- **Nuanceur de sommets** Un nuanceur de sommets est une fonction de traitement des graphiques qui effectue des opérations mathématiques sur les données de sommet de l’objet.  
  
- **Prise en charge de la multitexture** La prise en charge de la multitexture fait référence à la possibilité d’appliquer au moins deux textures distinctes pendant une opération de mélange sur un objet graphique 3D. Le degré de prise en charge de la multitexture est déterminé par le nombre d’unités de multitexture sur le matériel graphique.  
  
<a name="rendering_tier_definitions"></a>
## <a name="rendering-tier-definitions"></a>Définitions des couches de rendu  
 Les fonctionnalités du matériel graphique déterminent la fonction de rendu d’une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Le système [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] définit trois couches de rendu :  
  
- **Couche de rendu 0** Aucune accélération matérielle graphique. Toutes les fonctionnalités graphiques utilisent l’accélération logicielle. Le niveau de la version DirectX est inférieur à la version 9.0.  
  
- **Couche de rendu 1** Certaines fonctionnalités graphiques utilisent l’accélération matérielle graphique. Le niveau de version DirectX est supérieur ou égal à la version 9.0.  
  
- **Couche de rendu 2** La plupart des fonctionnalités graphiques utilisent l’accélération matérielle graphique. Le niveau de version DirectX est supérieur ou égal à la version 9.0.  
  
 La <xref:System.Windows.Media.RenderCapability.Tier%2A?displayProperty=nameWithType> propriété vous permet de récupérer le niveau de rendu au moment de l’exécution de l’application. La couche de rendu permet de déterminer si l’appareil prend en charge certaines fonctionnalités graphiques à accélération matérielle. Votre application peut alors prendre des chemins de code différents au moment de l’exécution selon la couche de rendu prise en charge par l’appareil.  
  
### <a name="rendering-tier-0"></a>Couche de rendu 0  
 La valeur de couche de rendu 0 signifie qu’aucune accélération matérielle graphique n’est disponible pour l’application sur l’appareil. À ce niveau de la couche, vous devez supposer que tous les graphiques seront restitués par le logiciel sans accélération matérielle. La fonctionnalité de ce niveau correspond à une version DirectX inférieure à 9,0.  
  
### <a name="rendering-tier-1-and-rendering-tier-2"></a>Couche de rendu 1 et couche de rendu 2
  
> [!NOTE]
> À partir du cadre .NET 4, le rendu de niveau 1 a été redéfini pour inclure uniquement le matériel graphique qui prend en charge DirectX 9.0 ou plus. Le matériel graphique qui prend en charge DirectX 7 ou 8 est maintenant défini comme le rendu de niveau 0.  
  
 La valeur de couche de rendu 1 ou 2 signifie que la plupart des fonctionnalités graphiques de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utiliseront l’accélération matérielle si les ressources système nécessaires sont disponibles et n’ont pas été épuisées. Cela correspond à une version DirectX supérieure ou égale à 9,0.  
  
 Le tableau suivant indique les différences entre la couche de rendu 1 et la couche de rendu 2 au niveau des spécifications de matériel graphique :  
  
|Fonctionnalité|Niveau 1|Niveau 2|  
|-------------|------------|------------|  
|Version DirectX|Doit être supérieure ou égale à 9.0.|Doit être supérieure ou égale à 9.0.|  
|RAM vidéo|Doit être supérieur ou égal à 60 Mo.|Doit être supérieur ou égal à 120 Mo.|  
|Nuanceur de pixels|Le niveau de version doit être supérieur ou égal à 2.0.|Le niveau de version doit être supérieur ou égal à 2.0.|  
|Nuanceur de sommets|Aucune spécification.|Le niveau de version doit être supérieur ou égal à 2.0.|  
|Unités de multitexture|Aucune spécification.|Le nombre d’unités doit être supérieur ou égal à 4.|  
  
 Les fonctionnalités et fonctions suivantes sont à accélération matérielle pour les couches de rendu 1 et 2 :  
  
|Fonctionnalité|Notes|  
|-------------|-----------|  
|Rendu 2D|La plupart des types de rendu 2D sont pris en charge.|  
|Rastérisation 3D|La plupart des types de rastérisation 3D sont pris en charge.|  
|Filtrage anisotropique 3D|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tente d’utiliser le filtrage anisotropique lors de l’affichage du contenu 3D. Le filtrage anisotropique correspond à l’amélioration de la qualité d’image des textures des surfaces éloignées et en biais par rapport à l’appareil photo.|  
|Mappage MIP 3D|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tente d’utiliser le mappage MIP lors de l’affichage du contenu 3D. La cartographie du MIP améliore la qualité du rendu de texture <xref:System.Windows.Controls.Viewport3D>lorsqu’une texture occupe un champ de vision plus petit dans un .|  
|Dégradés radiaux|Bien que pris en <xref:System.Windows.Media.RadialGradientBrush> charge, évitez l’utilisation de grands objets.|  
|Calculs d’éclairage 3D|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] exécute l’éclairage par sommet, ce qui signifie qu’une intensité légère doit être calculée à chaque sommet pour chaque matériel appliqué à un maillage.|  
|Rendu de texte|Le rendu de police de sous-pixel utilise les ombrageurs de pixels disponibles sur le matériel graphique.|  
  
 Les fonctionnalités et fonctions suivantes sont à accélération matérielle uniquement pour la couche de rendu 2 :  
  
|Fonctionnalité|Notes|  
|-------------|-----------|  
|Anticrénelage 3D|L’anti-aliasing 3D n’est pris en charge que sur les systèmes d’exploitation qui prennent en charge Windows Display Driver Model (WDDM), tels que Windows Vista et Windows 7.|  
  
 Les fonctionnalités et fonctions suivantes ne sont **pas** à accélération matérielle :  
  
|Fonctionnalité|Notes|  
|-------------|-----------|  
|Contenu imprimé|Tout le contenu imprimé est restitué à l’aide du pipeline logiciel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|  
|Contenu rasterisé qui utilise<xref:System.Windows.Media.Imaging.RenderTargetBitmap>|Tout contenu rendu en <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> utilisant <xref:System.Windows.Media.Imaging.RenderTargetBitmap>la méthode de .|  
|Contenu carrelé qui utilise<xref:System.Windows.Media.TileBrush>|Tout contenu carrelé <xref:System.Windows.Media.TileBrush.TileMode%2A> dans <xref:System.Windows.Media.TileBrush> lequel la <xref:System.Windows.Media.TileMode.Tile>propriété de la est définie à .|  
|Surfaces qui dépassent la taille de texture maximale du matériel graphique|Pour la plupart des matériels graphiques, les grandes surfaces ont une taille de 2048 x 2048 ou 4096 x 4096 pixels.|  
|Toute opération dont la spécification de RAM vidéo dépasse la mémoire du matériel graphique|Vous pouvez surveiller l’utilisation de la RAM vidéo par l’application à l’aide de l’outil Perforator compris dans la suite [WPF Performance Suite](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100)) du SDK Windows.|  
|Fenêtres superposées|Les fenêtres superposées permettent aux applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de restituer le contenu à l’écran dans une fenêtre non rectangulaire. Sur les systèmes d’exploitation qui prennent en charge Windows Display Driver Model (WDDM), tels que Windows Vista et Windows 7, les fenêtres superposées sont accélérées par le matériel. Sur d’autres systèmes, tels que Windows XP, les fenêtres superposées sont rendues par un logiciel sans accélération matérielle.<br /><br /> Vous pouvez activer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] les fenêtres <xref:System.Windows.Window> superposées en définissant les propriétés suivantes :<br /><br /> -   <xref:System.Windows.Window.WindowStyle%2A> = <xref:System.Windows.WindowStyle.None><br />-   <xref:System.Windows.Window.AllowsTransparency%2A> = `true`<br />-   <xref:System.Windows.Controls.Control.Background%2A> = <xref:System.Windows.Media.Brushes.Transparent%2A>|  
  
<a name="other_resources"></a>
## <a name="other-resources"></a>Autres ressources  
 Les ressources suivantes peuvent vous aider à analyser les caractéristiques des performances de votre application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="graphics-rendering-registry-settings"></a>Paramètres du Registre pour le rendu des graphiques  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit quatre paramètres du Registre pour le contrôle du rendu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] :  
  
|Paramètre|Description|  
|-------------|-----------------|  
|**Option Désactiver l’accélération matérielle**|Spécifie si l’accélération matérielle doit être activée.|  
|**Valeur d’échantillonnage multiple maximale**|Spécifie le degré de multisampling pour anti-étiquetage du contenu 3D.|  
|**Paramètre Date de pilote vidéo requise**|Spécifie si le système désactive l’accélération matérielle pour les pilotes commercialisés avant novembre 2004.|  
|**Option Utiliser le rastériseur de référence**|Spécifie si [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] doit utiliser le rastériseur de référence.|  
  
 Ces paramètres sont accessibles à tout utilitaire de configuration externe capable de référencer les paramètres du Registre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Ces paramètres peuvent également être créés ou modifiés en accédant directement aux valeurs en utilisant l’éditeur du registre Windows. Pour plus d’informations, consultez [Paramètres du Registre pour le rendu des graphiques](../graphics-multimedia/graphics-rendering-registry-settings.md).  
  
### <a name="wpf-performance-profiling-tools"></a>Outils de profilage des performances WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit une suite d’outils de profilage des performances qui vous permettent d’analyser le comportement au moment de l’exécution de votre application et de déterminer les types d’optimisations des performances que vous pouvez appliquer. Le tableau suivant répertorie les outils de profilage des performances qui sont inclus dans l’outil Windows SDK, WPF Performance Suite :  
  
|Outil|Description|  
|----------|-----------------|  
|Perforator|À utiliser pour analyser le comportement de rendu.|  
|Visual Profiler|À utiliser pour le profilage de l’utilisation des services [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], tels que la disposition et la gestion des événements, pour chaque élément de l’arborescence d’éléments visuels.|  
  
 L’outil WPF Performance Suite fournit une vue graphique détaillée des données de performances. Pour plus d’informations sur les outils de performances WPF, consultez [WPF Performance Suite](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100)).  
  
### <a name="directx-diagnostic-tool"></a>Outil de diagnostic DirectX  
 L’outil de diagnostic DirectX, Dxdiag.exe, est conçu pour vous aider à résoudre les problèmes liés à DirectX. Le dossier d’installation par défaut pour l’outil de diagnostic DirectX est :  
  
 `~\Windows\System32`  
  
 Lorsque vous exécutez l’outil de diagnostic DirectX, la fenêtre principale contient un ensemble d’onglets qui vous permettent d’afficher et de diagnostiquer les informations relatives à DirectX. Par exemple, l’onglet **Système** fournit des informations système sur votre ordinateur et spécifie la version de DirectX qui est installée sur votre ordinateur.  
  
 ![Capture d’écran: DirectX Diagnostic Tool](./media/directxdiagnostictool-01.png "DirectXDiagnosticTool_01")  
Fenêtre principale de l’outil de diagnostic DirectX  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.RenderCapability>
- <xref:System.Windows.Media.RenderOptions>
- [Optimisation des performances des applications WPF](optimizing-wpf-application-performance.md)
- [WPF Performance Suite](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100))
- [Paramètres du Registre pour le rendu des graphiques](../graphics-multimedia/graphics-rendering-registry-settings.md)
- [Conseils et astuces sur les animations](../graphics-multimedia/animation-tips-and-tricks.md)
