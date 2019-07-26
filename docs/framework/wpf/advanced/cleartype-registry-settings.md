---
title: Paramètres du Registre ClearType
ms.date: 03/30/2017
helpviewer_keywords:
- ClearType [WPF], registry settings
- typography [WPF], ClearType registry settings
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
ms.openlocfilehash: db7d6ec5663d657969e1508bd0b9f62c25e491b0
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484691"
---
# <a name="cleartype-registry-settings"></a>Paramètres du Registre ClearType
Cette rubrique fournit une vue d’ensemble [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] des paramètres du Registre qui sont [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilisés par les [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] applications.  

<a name="overview"></a>   
## <a name="technology-overview"></a>Vue d’ensemble de la technologie  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]les applications qui restituent du texte sur un périphérique d’affichage utilisent des fonctionnalités ClearType pour offrir une expérience de lecture améliorée. ClearType est une technologie logicielle développée par [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] qui améliore la lisibilité du texte sur les écrans LCD existants (affichages à cristaux liquides), tels que les écrans d’ordinateurs portables, les écrans de Pocket PC et les écrans plats. ClearType fonctionne en accédant aux éléments individuels de la bande de couleur verticale dans chaque pixel d’un écran LCD. Pour plus d’informations sur ClearType, consultez [vue d’ensemble de ClearType](cleartype-overview.md).  
  
 Le texte rendu avec ClearType peut apparaître considérablement différent quand il est affiché sur différents périphériques d’affichage. Par exemple, un petit nombre d’analyses implémentent les éléments de la bande de couleur dans l’ordre bleu, vert, rouge plutôt que dans l’ordre rouge, [!INCLUDE[TLA#tla_rgb](../../../../includes/tlasharptla-rgb-md.md)]vert, bleu () le plus courant.  
  
 Le texte rendu avec ClearType peut également apparaître considérablement différent quand il est affiché par des individus avec des niveaux de sensibilité de couleur différents. Certains individus peuvent détecter mieux que d’autres les variations chromatiques légères.  
  
 Dans chacun de ces cas, les fonctionnalités ClearType doivent être modifiées afin de fournir la meilleure expérience de lecture pour chaque individu.  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>Paramètres du Registre  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]spécifie quatre paramètres de Registre pour le contrôle des fonctionnalités ClearType:  
  
|Paramètre|Description|  
|-------------|-----------------|  
|Niveau ClearType|Décrit le niveau de clarté de la couleur ClearType.|  
|Niveau gamma|Décrit le niveau du composant de couleur des pixels d’un écran d’affichage.|  
|Structure des pixels|Décrit la disposition des pixels d’un écran d’affichage.|  
|Niveau de contraste du texte|Décrit le niveau de contraste du texte affiché.|  
  
 Ces paramètres sont accessibles par un utilitaire de configuration externe qui sait comment référencer les paramètres [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]du Registre ClearType identifiés. Ces paramètres peuvent également être créés ou modifiés en accédant directement aux valeurs à l’aide de l’Éditeur du Registre [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  
  
 Si les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]paramètres du Registre ClearType ne sont pas définis (ce qui correspond à l’état [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] par défaut) [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] , l’application interroge les informations de paramètres système pour les paramètres de lissage des polices.  
  
> [!NOTE]
>  Pour plus d’informations sur l’énumération des noms d' `SystemParametersInfo` appareils d’affichage, consultez la [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fonction.  
  
<a name="ClearType_level"></a>   
## <a name="cleartype-level"></a>Niveau ClearType  
 Le niveau ClearType vous permet d’ajuster le rendu du texte en fonction de la sensibilité de couleur et de la perception d’un individu. Pour certains individus, le rendu du texte qui utilise ClearType à son niveau le plus élevé ne produit pas la meilleure expérience de lecture.  
  
 Le niveau ClearType est une valeur entière comprise entre 0 et 100. Le niveau par défaut est 100, ce qui signifie que ClearType utilise la capacité maximale des éléments de la bande de couleur du périphérique d’affichage. Toutefois, un niveau ClearType de 0 rend le texte sous forme de nuances de gris. En affectant au niveau ClearType une valeur comprise entre 0 et 100, vous pouvez créer un niveau intermédiaire adapté à la sensibilité des couleurs d’un individu.  
  
### <a name="registry-setting"></a>Paramètre du Registre  
 L’emplacement du paramètre de Registre pour le niveau ClearType est un paramètre utilisateur individuel qui correspond à un nom d’écran d’affichage spécifique:  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pour chaque nom de périphérique d’affichage d’un utilisateur `ClearTypeLevel` , une valeur DWORD est définie. La capture d’écran suivante montre le paramètre de l’éditeur du Registre pour le niveau ClearType.  
  
 ![Paramètres ClearType dans l’éditeur du Registre.](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]les applications restituent le texte dans l’un des deux modes, avec et sans ClearType. Quand le texte est rendu sans ClearType, il est appelé rendu en nuances de gris.  
  
<a name="gamma_level"></a>   
## <a name="gamma-level"></a>Niveau gamma  
 Le niveau gamma fait référence à la relation non linéaire entre une valeur de pixel et la luminance. Ce paramètre doit correspondre aux caractéristiques physiques de l’écran d’affichage ; dans le cas contraire, des distorsions dans le rendu pourraient se produire. Par exemple, un test peut apparaître trop large ou trop étroit, ou encore des franges de couleurs peuvent apparaître sur les bords des traits verticaux des glyphes.  
  
 Le niveau gamma est une valeur entière comprise entre 1 000 et 2 200. Le niveau par défaut est 1 900.  
  
### <a name="registry-setting"></a>Paramètre du Registre  
 Le paramètre du Registre du niveau gamma se trouve dans un paramètre d’ordinateur local correspondant à un nom d’écran d’affichage spécifique :  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pour chaque nom de périphérique d’affichage d’un utilisateur `GammaLevel` , une valeur DWORD est définie. La capture d’écran suivante indique le paramètre du niveau gamma dans l’Éditeur du Registre.  
  
 ![Paramètres du niveau gamma ClearType dans l’éditeur du Registre](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="pixel_structure"></a>   
## <a name="pixel-structure"></a>Structure des pixels  
 La structure des pixels décrit le type des pixels qui composent un écran d’affichage. Cette structure peut être de trois types :  
  
|Type|`Value`|Description|  
|----------|-----------|-----------------|  
|À deux dimensions|0|L’écran d’affichage n’a aucune structure de pixels. Cela signifie que les sources de lumière de chaque couleur sont étalées de manière uniforme sur la zone de pixel – ce rendu est appelé « rendu en échelle de gris ». C’est ainsi que fonctionne un écran d’affichage standard. ClearType n’est jamais appliqué au texte rendu.|  
|RVB|1|L’écran d’affichage comporte des pixels constitués de trois bandes dans l’ordre suivant : rouge, vert et bleu. ClearType est appliqué au texte rendu.|  
|BVR|2|L’écran d’affichage comporte des pixels constitués de trois bandes dans l’ordre suivant : bleu, vert et rouge. ClearType est appliqué au texte rendu. Notez que l’ordre est inversé par rapport au type RVB.|  
  
 La structure du pixel correspond à une valeur entière comprise entre 0 et 2. Le niveau par défaut est 0, qui représente une structure de pixel plate.  
  
> [!NOTE]
>  Pour plus d’informations sur l’énumération des noms d' `EnumDisplayDevices` appareils d’affichage, consultez la [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fonction.  
  
### <a name="registry-setting"></a>Paramètre du Registre  
 Le paramètre du Registre de la structure des pixels se trouve dans un paramètre d’ordinateur local correspondant à un nom d’écran d’affichage spécifique :  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pour chaque nom de périphérique d’affichage d’un utilisateur `PixelStructure` , une valeur DWORD est définie. La capture d’écran suivante indique le paramètre de la structure des pixels dans l’Éditeur du Registre.  
  
 ![Paramètres du niveau gamma ClearType dans l’éditeur du Registre](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="text_contrast_level"></a>   
## <a name="text-contrast-level"></a>Niveau de contraste du texte  
 Le niveau de contraste du texte vous permet d’ajuster le rendu du texte en fonction de la largeur de trait des glyphes. Le niveau de contraste du texte est une valeur entière comprise entre 0 et 6 ; plus cette valeur est élevée, plus le trait est épais. Le niveau par défaut est 1.  
  
### <a name="registry-setting"></a>Paramètre du Registre  
 Le paramètre du Registre du niveau de contraste du texte se trouve dans un paramètre utilisateur individuel correspondant à un nom d’écran d’affichage spécifique :  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pour chaque nom de périphérique d’affichage d’un utilisateur `TextContrastLevel` , une valeur DWORD est définie. La capture d’écran suivante indique le paramètre du niveau de contraste du texte dans l’Éditeur du Registre.  
  
 ![Paramètres ClearType dans l’éditeur du Registre.](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble ClearType](cleartype-overview.md)
- [Anticrénelage ClearType](/windows/desktop/gdi/cleartype-antialiasing)
