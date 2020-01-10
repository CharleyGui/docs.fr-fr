---
title: Paramètres du Registre ClearType
ms.date: 03/30/2017
helpviewer_keywords:
- ClearType [WPF], registry settings
- typography [WPF], ClearType registry settings
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
ms.openlocfilehash: 6143cf835cc44a6c6cc50372b2ac1a4d24d65311
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740385"
---
# <a name="cleartype-registry-settings"></a>Paramètres du Registre ClearType
Cette rubrique fournit une vue d’ensemble des paramètres de Registre Microsoft ClearType qui sont utilisés par les applications WPF.  

<a name="overview"></a>   
## <a name="technology-overview"></a>Vue d’ensemble de la technologie  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications qui affichent du texte sur un périphérique d’affichage utilisent des fonctionnalités ClearType pour offrir une expérience de lecture améliorée. ClearType est une technologie logicielle développée par Microsoft qui améliore la lisibilité du texte sur les écrans LCD existants (affichages à cristaux liquides), tels que les écrans d’ordinateurs portables, les écrans de Pocket PC et les écrans plats. ClearType fonctionne en accédant aux éléments individuels de la bande de couleur verticale dans chaque pixel d’un écran LCD. Pour plus d’informations sur ClearType, consultez [vue d’ensemble de ClearType](cleartype-overview.md).  
  
 Le texte rendu avec ClearType peut apparaître considérablement différent quand il est affiché sur différents périphériques d’affichage. Par exemple, un petit nombre d’analyses implémentent les éléments de la bande de couleur dans l’ordre bleu, vert et rouge plutôt que dans l’ordre rouge, vert, bleu (RVB) le plus courant.  
  
 Le texte rendu avec ClearType peut également apparaître considérablement différent quand il est affiché par des individus avec des niveaux de sensibilité de couleur différents. Certains individus peuvent détecter mieux que d’autres les variations chromatiques légères.  
  
 Dans chacun de ces cas, les fonctionnalités ClearType doivent être modifiées afin de fournir la meilleure expérience de lecture pour chaque individu.  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>Paramètres du Registre  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] spécifie quatre paramètres de Registre pour le contrôle des fonctionnalités ClearType :  
  
|Paramètre|Description|  
|-------------|-----------------|  
|Niveau ClearType|Décrit le niveau de clarté de la couleur ClearType.|  
|Niveau gamma|Décrit le niveau du composant de couleur des pixels d’un écran d’affichage.|  
|Structure des pixels|Décrit la disposition des pixels d’un écran d’affichage.|  
|Niveau de contraste du texte|Décrit le niveau de contraste du texte affiché.|  
  
 Ces paramètres sont accessibles par un utilitaire de configuration externe qui sait comment référencer les paramètres de Registre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ClearType identifiés. Ces paramètres peuvent également être créés ou modifiés en accédant directement aux valeurs à l’aide de l’éditeur du Registre Windows.  
  
 Si les paramètres du Registre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ClearType ne sont pas définis (ce qui correspond à l’État par défaut), l’application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interroge les informations de paramètres système Windows pour les paramètres de lissage des polices.  
  
> [!NOTE]
> Pour plus d’informations sur l’énumération des noms des appareils d’affichage, consultez la `SystemParametersInfo`fonction Win32.  
  
<a name="ClearType_level"></a>   
## <a name="cleartype-level"></a>Niveau ClearType  
 Le niveau ClearType vous permet d’ajuster le rendu du texte en fonction de la sensibilité de couleur et de la perception d’un individu. Pour certains individus, le rendu du texte qui utilise ClearType à son niveau le plus élevé ne produit pas la meilleure expérience de lecture.  
  
 Le niveau ClearType est une valeur entière comprise entre 0 et 100. Le niveau par défaut est 100, ce qui signifie que ClearType utilise la capacité maximale des éléments de la bande de couleur du périphérique d’affichage. Toutefois, un niveau ClearType de 0 rend le texte sous forme de nuances de gris. En affectant au niveau ClearType une valeur comprise entre 0 et 100, vous pouvez créer un niveau intermédiaire adapté à la sensibilité des couleurs d’un individu.  
  
### <a name="registry-setting"></a>Paramètres du Registre  
 L’emplacement du paramètre de Registre pour le niveau ClearType est un paramètre utilisateur individuel qui correspond à un nom d’écran d’affichage spécifique :  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pour chaque nom de périphérique d’affichage d’un utilisateur, une valeur DWORD `ClearTypeLevel` est définie. La capture d’écran suivante montre le paramètre de l’éditeur du Registre pour le niveau ClearType.  
  
 ![Paramètres ClearType dans l’éditeur du Registre.](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications affichent du texte dans l’un des deux modes, avec et sans ClearType. Quand le texte est rendu sans ClearType, il est appelé rendu en nuances de gris.  
  
<a name="gamma_level"></a>   
## <a name="gamma-level"></a>Niveau gamma  
 Le niveau gamma fait référence à la relation non linéaire entre une valeur de pixel et la luminance. Ce paramètre doit correspondre aux caractéristiques physiques de l’écran d’affichage ; dans le cas contraire, des distorsions dans le rendu pourraient se produire. Par exemple, le texte peut apparaître trop large ou trop étroit, ou des franges de couleur peuvent apparaître sur les bords des tiges verticales de glyphes.  
  
 Le niveau gamma est une valeur entière comprise entre 1 000 et 2 200. Le niveau par défaut est 1 900.  
  
### <a name="registry-setting"></a>Paramètres du Registre  
 Le paramètre du Registre du niveau gamma se trouve dans un paramètre d’ordinateur local correspondant à un nom d’écran d’affichage spécifique :  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pour chaque nom de périphérique d’affichage d’un utilisateur, une valeur DWORD `GammaLevel` est définie. La capture d’écran suivante indique le paramètre du niveau gamma dans l’Éditeur du Registre.  
  
 ![Paramètres du niveau gamma ClearType dans l’éditeur du Registre](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="pixel_structure"></a>   
## <a name="pixel-structure"></a>Structure des pixels  
 La structure des pixels décrit le type des pixels qui composent un écran d’affichage. Cette structure peut être de trois types :  
  
|Type|Value|Description|  
|----------|-----------|-----------------|  
|À deux dimensions|0|L’écran d’affichage n’a aucune structure de pixels. Cela signifie que les sources de lumière de chaque couleur sont étalées de manière uniforme sur la zone de pixel – ce rendu est appelé « rendu en échelle de gris ». C’est ainsi que fonctionne un écran d’affichage standard. ClearType n’est jamais appliqué au texte rendu.|  
|RVB|1|L’écran d’affichage comporte des pixels constitués de trois bandes dans l’ordre suivant : rouge, vert et bleu. ClearType est appliqué au texte rendu.|  
|BVR|2|L’écran d’affichage comporte des pixels constitués de trois bandes dans l’ordre suivant : bleu, vert et rouge. ClearType est appliqué au texte rendu. Notez que l’ordre est inversé par rapport au type RVB.|  
  
 La structure du pixel correspond à une valeur entière comprise entre 0 et 2. Le niveau par défaut est 0, qui représente une structure de pixel plate.  
  
> [!NOTE]
> Pour plus d’informations sur l’énumération des noms des appareils d’affichage, consultez la `EnumDisplayDevices`fonction Win32.  
  
### <a name="registry-setting"></a>Paramètres du Registre  
 Le paramètre du Registre de la structure des pixels se trouve dans un paramètre d’ordinateur local correspondant à un nom d’écran d’affichage spécifique :  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pour chaque nom de périphérique d’affichage d’un utilisateur, une valeur DWORD `PixelStructure` est définie. La capture d’écran suivante indique le paramètre de la structure des pixels dans l’Éditeur du Registre.  
  
 ![Paramètres du niveau gamma ClearType dans l’éditeur du Registre](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="text_contrast_level"></a>   
## <a name="text-contrast-level"></a>Niveau de contraste du texte  
 Le niveau de contraste du texte vous permet d’ajuster le rendu du texte en fonction de la largeur de trait des glyphes. Le niveau de contraste du texte est une valeur entière comprise entre 0 et 6 ; plus cette valeur est élevée, plus le trait est épais. Le niveau par défaut est 1.  
  
### <a name="registry-setting"></a>Paramètres du Registre  
 Le paramètre du Registre du niveau de contraste du texte se trouve dans un paramètre utilisateur individuel correspondant à un nom d’écran d’affichage spécifique :  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pour chaque nom de périphérique d’affichage d’un utilisateur, une valeur DWORD `TextContrastLevel` est définie. La capture d’écran suivante indique le paramètre du niveau de contraste du texte dans l’Éditeur du Registre.  
  
 ![Paramètres ClearType dans l’éditeur du Registre.](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble ClearType](cleartype-overview.md)
- [Anticrénelage ClearType](/windows/desktop/gdi/cleartype-antialiasing)
