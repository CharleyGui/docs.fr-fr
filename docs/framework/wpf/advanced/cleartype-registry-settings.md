---
title: Paramètres du Registre ClearType
ms.date: 03/30/2017
helpviewer_keywords:
- ClearType [WPF], registry settings
- typography [WPF], ClearType registry settings
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
ms.openlocfilehash: bedd99fcf9b4ca1d10b4c24d7cff9de320e6fd12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186177"
---
# <a name="cleartype-registry-settings"></a>Paramètres du Registre ClearType
Ce sujet donne un aperçu des paramètres du registre Microsoft ClearType qui sont utilisés par les applications WPF.  

<a name="overview"></a>
## <a name="technology-overview"></a>Vue d’ensemble de la technologie  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]les applications qui rendent le texte à un appareil d’affichage utilisent les fonctionnalités ClearType pour offrir une expérience de lecture améliorée. ClearType est une technologie logicielle développée par Microsoft qui améliore la lisibilité du texte sur les écrans de radio(liquid) existants (écrans de cristal liquide), tels que les écrans d’ordinateur portable, les écrans de PC de poche et les moniteurs de panneaux plats. ClearType fonctionne en accédant aux éléments de bande de couleur verticale individuels dans chaque pixel d’un écran LCD. Pour plus d’informations sur ClearType, voir [ClearType Overview](cleartype-overview.md).  
  
 Le texte qui est rendu avec ClearType peut apparaître sensiblement différent lorsqu’il est vu sur divers appareils d’affichage. Par exemple, un petit nombre de moniteurs implémentent les éléments de bande de couleur dans l’ordre bleu, vert, rouge plutôt que l’ordre rouge, vert, bleu (RGB) plus commun.  
  
 Le texte qui est rendu avec ClearType peut également apparaître sensiblement différent lorsqu’il est vu par des individus avec des niveaux variables de sensibilité aux couleurs. Certains individus peuvent détecter mieux que d’autres les variations chromatiques légères.  
  
 Dans chacun de ces cas, les fonctionnalités ClearType doivent être modifiées afin de fournir la meilleure expérience de lecture pour chaque individu.  
  
<a name="registry_settings"></a>
## <a name="registry-settings"></a>Paramètres du Registre  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]spécifie quatre paramètres de registre pour le contrôle des fonctionnalités ClearType :  
  
|Paramètre|Description|  
|-------------|-----------------|  
|Niveau ClearType|Décrit le niveau de clarté de couleur ClearType.|  
|Niveau gamma|Décrit le niveau du composant de couleur des pixels d’un écran d’affichage.|  
|Structure des pixels|Décrit la disposition des pixels d’un écran d’affichage.|  
|Niveau de contraste du texte|Décrit le niveau de contraste du texte affiché.|  
  
 Ces paramètres peuvent être consultés par un utilitaire de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] configuration externe qui sait comment faire référence aux paramètres identifiés du registre ClearType. Ces paramètres peuvent également être créés ou modifiés en accédant directement aux valeurs en utilisant l’éditeur du registre Windows.  
  
 Si [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] les paramètres du registre ClearType ne sont [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pas définis (c’est-à-dire l’état par défaut), l’application interroge les paramètres du système Windows pour les paramètres de lissage des polices.  
  
> [!NOTE]
> Pour plus d’informations sur l’énumération des noms des périphériques d’affichage, consultez la `SystemParametersInfo`fonction Win32.  
  
<a name="ClearType_level"></a>
## <a name="cleartype-level"></a>Niveau ClearType  
 Le niveau ClearType vous permet d’ajuster le rendu du texte en fonction de la sensibilité des couleurs et de la perception d’un individu. Pour certaines personnes, le rendu du texte qui utilise ClearType à son plus haut niveau ne produit pas la meilleure expérience de lecture.  
  
 Le niveau ClearType est une valeur integer qui varie de 0 à 100. Le niveau par défaut est de 100, ce qui signifie que ClearType utilise la capacité maximale des éléments de bande de couleur de l’appareil d’affichage. Cependant, un niveau ClearType de 0 rend le texte comme échelle grise. En définissant le niveau ClearType quelque part entre 0 et 100, vous pouvez créer un niveau intermédiaire qui convient à la sensibilité des couleurs d’un individu.  
  
### <a name="registry-setting"></a>Paramètre de registre  
 L’emplacement de réglage du registre pour le niveau ClearType est un paramètre utilisateur individuel qui correspond à un nom spécifique de périphérique d’affichage :  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pour chaque nom d’appareil `ClearTypeLevel` d’affichage pour un utilisateur, une valeur DWORD est définie. La capture d’écran suivante montre le paramètre De l’éditeur de registre pour le niveau ClearType.  
  
 ![Paramètres ClearType dans l’éditeur de registre.](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]les applications rendent le texte dans l’un des deux modes, avec et sans ClearType. Lorsque le texte est rendu sans ClearType, il est appelé rendu à l’échelle grise.  
  
<a name="gamma_level"></a>
## <a name="gamma-level"></a>Niveau gamma  
 Le niveau gamma fait référence à la relation non linéaire entre une valeur de pixel et la luminance. Ce paramètre doit correspondre aux caractéristiques physiques de l’écran d’affichage ; dans le cas contraire, des distorsions dans le rendu pourraient se produire. Par exemple, le texte peut apparaître trop large ou trop étroit, ou des franges de couleur peuvent apparaître sur les bords des tiges verticales des glyphes.  
  
 Le niveau gamma est une valeur entière comprise entre 1 000 et 2 200. Le niveau par défaut est 1 900.  
  
### <a name="registry-setting"></a>Paramètre de registre  
 Le paramètre du Registre du niveau gamma se trouve dans un paramètre d’ordinateur local correspondant à un nom d’écran d’affichage spécifique :  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pour chaque nom d’appareil `GammaLevel` d’affichage pour un utilisateur, une valeur DWORD est définie. La capture d’écran suivante indique le paramètre du niveau gamma dans l’Éditeur du Registre.  
  
 ![Paramètres de niveau gamma ClearType dans l’éditeur de registre](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="pixel_structure"></a>
## <a name="pixel-structure"></a>Structure des pixels  
 La structure des pixels décrit le type des pixels qui composent un écran d’affichage. Cette structure peut être de trois types :  
  
|Type|Valeur|Description|  
|----------|-----------|-----------------|  
|À deux dimensions|0|L’écran d’affichage n’a aucune structure de pixels. Cela signifie que les sources de lumière de chaque couleur sont étalées de manière uniforme sur la zone de pixel – ce rendu est appelé « rendu en échelle de gris ». C’est ainsi que fonctionne un écran d’affichage standard. ClearType n’est jamais appliqué au texte rendu.|  
|RGB|1|L’écran d’affichage comporte des pixels constitués de trois bandes dans l’ordre suivant : rouge, vert et bleu. ClearType est appliqué au texte rendu.|  
|BVR|2|L’écran d’affichage comporte des pixels constitués de trois bandes dans l’ordre suivant : bleu, vert et rouge. ClearType est appliqué au texte rendu. Notez que l’ordre est inversé par rapport au type RVB.|  
  
 La structure du pixel correspond à une valeur entière comprise entre 0 et 2. Le niveau par défaut est 0, qui représente une structure de pixel plate.  
  
> [!NOTE]
> Pour plus d’informations sur l’énumération des noms des périphériques d’affichage, consultez la `EnumDisplayDevices`fonction Win32.  
  
### <a name="registry-setting"></a>Paramètre de registre  
 Le paramètre du Registre de la structure des pixels se trouve dans un paramètre d’ordinateur local correspondant à un nom d’écran d’affichage spécifique :  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pour chaque nom d’appareil `PixelStructure` d’affichage pour un utilisateur, une valeur DWORD est définie. La capture d’écran suivante indique le paramètre de la structure des pixels dans l’Éditeur du Registre.  
  
 ![Paramètres de niveau gamma ClearType dans l’éditeur de registre](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="text_contrast_level"></a>
## <a name="text-contrast-level"></a>Niveau de contraste du texte  
 Le niveau de contraste du texte vous permet d’ajuster le rendu du texte en fonction de la largeur de trait des glyphes. Le niveau de contraste du texte est une valeur entière comprise entre 0 et 6 ; plus cette valeur est élevée, plus le trait est épais. Le niveau par défaut est 1.  
  
### <a name="registry-setting"></a>Paramètre de registre  
 Le paramètre du Registre du niveau de contraste du texte se trouve dans un paramètre utilisateur individuel correspondant à un nom d’écran d’affichage spécifique :  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pour chaque nom d’appareil `TextContrastLevel` d’affichage pour un utilisateur, une valeur DWORD est définie. La capture d’écran suivante indique le paramètre du niveau de contraste du texte dans l’Éditeur du Registre.  
  
 ![Paramètres ClearType dans l’éditeur de registre.](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble ClearType](cleartype-overview.md)
- [Anticrénelage ClearType](/windows/desktop/gdi/cleartype-antialiasing)
