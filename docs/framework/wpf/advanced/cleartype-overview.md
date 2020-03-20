---
title: Vue d'ensemble de ClearType
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], ClearType technology
- ClearType [WPF], technology
ms.assetid: 7e2392e0-75dc-463d-a716-908772782431
ms.openlocfilehash: b76c0cb04e5de498374cbf28c8813fe5c95d41ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186163"
---
# <a name="cleartype-overview"></a>Vue d'ensemble de ClearType
Ce sujet fournit un aperçu de la technologie [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Microsoft ClearType trouvé dans le .  

<a name="overview"></a>
## <a name="technology-overview"></a>Vue d’ensemble de la technologie  
 ClearType est une technologie logicielle développée par Microsoft qui améliore la lisibilité du texte sur les écrans de radio(liquid) existants (écrans de cristal liquide), tels que les écrans d’ordinateur portable, les écrans de PC de poche et les moniteurs de panneaux plats.  ClearType fonctionne en accédant aux éléments de bande de couleur verticale individuels dans chaque pixel d’un écran LCD. Avant ClearType, le plus petit niveau de détail qu’un ordinateur pouvait afficher était un seul pixel, mais avec ClearType fonctionnant sur un écran LCD, nous pouvons maintenant afficher des fonctionnalités de texte aussi petites qu’une fraction de pixel de largeur. Cette résolution accrue augmente la netteté des détails dans l’affichage textuel, ce qui facilite grandement la lecture pendant des périodes prolongées.  
  
 Le ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] disponible est la dernière génération de ClearType qui a plusieurs améliorations par rapport à la version trouvée dans Microsoft Windows Graphics Device Interface (GDI).  
  
<a name="sub-pixel_positioning"></a>
## <a name="sub-pixel-positioning"></a>Positionnement du sous-pixel  
 Une amélioration significative par rapport à la version précédente de ClearType est l’utilisation du positionnement sous-pixel. Contrairement à l’implémentation ClearType trouvée [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] dans GDI, le ClearType trouvé dans permet aux glyphes de démarrer dans le pixel et pas seulement la limite de début du pixel. Grâce à cette résolution supérieure du positionnement des glyphes, l’espacement et les proportions des glyphes sont plus précis et cohérents.  
  
 Les deux exemples suivants montrent de quelle manière les glyphes peuvent commencer sur une limite de sous-pixel quand le positionnement du sous-pixel est utilisé. L’exemple à gauche est rendu à l’aide de la version antérieure du rendu ClearType, qui n’utilisait pas de positionnement sous-pixel. L’exemple à droite est rendu à l’aide de la nouvelle version du rendu ClearType, à l’aide d’un positionnement sous-pixel. Comme vous pouvez le constater, les lettres **e** et **l** de l’image de droite sont restituées de manière légèrement différente car elles démarrent toutes sur un sous-pixel différent. Quand vous affichez le texte à sa taille normale sur l’écran, cette différence n’est pas visible en raison du contraste élevé de l’image de glyphe. Ceci n’est possible qu’en raison du filtrage des couleurs sophistiqué qui est incorporé dans ClearType.  
  
 ![Texte affiché avec deux versions de ClearType](./media/wcpsdk-mmgraphics-text-cleartype-overview-01.png "wcpsdk_mmgraphics_text_cleartype_overview_01")  
Texte affiché avec l’ancienne et la nouvelle version de ClearType  
  
 Les deux exemples suivants comparent la sortie du rendu ClearType antérieur avec la nouvelle version du rendu ClearType. Le positionnement du sous-pixel, illustré à droite, améliore considérablement l’espacement de type sur l’écran, en particulier à de petites tailles, quand la différence entre un sous-pixel et un pixel entier représente une proportion importante de la largeur du glyphe. Notez que l’espacement entre les lettres est plus régulier dans la deuxième image. L’avantage cumulatif du positionnement sous-pixel à l’apparence globale d’un écran de texte est considérablement augmenté, et représente une évolution significative dans la technologie ClearType.  
  
 ![Texte affiché avec une version antérieure de ClearType](./media/wcpsdk-mmgraphics-text-cleartype-overview-02.png "wcpsdk_mmgraphics_text_cleartype_overview_02")  
Texte avec l’ancienne et la nouvelle version de ClearType  
  
<a name="y-direction_antialiasing"></a>
## <a name="y-direction-antialiasing"></a>Anticrénelage de direction y  
 Une autre amélioration de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ClearType est y-direction anti-aliasing. Le ClearType en GDI sans anti-aliasing y-direction offre une meilleure résolution sur l’axe x, mais pas le y-axe. Sur le haut et le bas des courbes marquées, les bords dentelés diminuent la lisibilité.  
  
 L’exemple suivant montre le résultat obtenu en l’absence d’anticrénelage de direction y. Dans ce cas, les bords dentelés sur le haut et le bas de la lettre sont apparents.  
  
 ![Texte avec bords dentelés sur les courbes marquées](./media/wcpsdk-mmgraphics-text-cleartype-overview-03.png "wcpsdk_mmgraphics_text_cleartype_overview_03")  
Texte avec bords dentelés sur les courbes marquées  
  
 ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] in fournit antialiasing sur le niveau y-direction pour lisser les bords déchiquetés. Cette fonctionnalité est particulièrement importante pour améliorer la lisibilité des langues d’Extrême-Orient, dont les idéogrammes comptent quasiment autant de courbes marquées horizontales que verticales.  
  
 L’exemple suivant montre le résultat de l’anticrénelage de direction y. Dans ce cas, le haut et le bas de la lettre affichent une courbe lissée.  
  
 ![Texte avec anticrénelage ClearType dans la direction y](./media/wcpsdk-mmgraphics-text-cleartype-overview-04.png "wcpsdk_mmgraphics_text_cleartype_overview_04")  
Texte avec anticrénelage ClearType dans la direction y  
  
<a name="hardware_acceleration"></a>
## <a name="hardware-acceleration"></a>Accélération matérielle  
 ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] in peut profiter de l’accélération matérielle pour de meilleures performances et pour réduire la charge de processeur et les exigences de mémoire du système. En utilisant les ombrageurs de pixels et la mémoire vidéo d’une carte graphique, ClearType fournit un rendu plus rapide du texte, en particulier lorsque l’animation est utilisée.  
  
 ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] in ne modifie pas les paramètres ClearType à l’échelle du système. Désactiver ClearType dans Windows [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] définit l’antianage en mode à l’échelle grise. En outre, ClearType in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ne modifie pas les paramètres de la [ClearType Tuner PowerToy](https://www.microsoft.com/typography/ClearTypePowerToy.mspx).  
  
 En ce qui concerne la conception architecturale de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], il a notamment été décidé d’améliorer la prise en charge par la disposition indépendante de la résolution des moniteurs DPI de résolution supérieure, qui sont de plus en plus répandus. De ce fait, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ne prend pas en charge le rendu de texte crénelé ni les bitmaps de certaines polices d’Extrême-Orient, qui sont tous deux dépendants de la résolution.  
  
<a name="further_information"></a>
## <a name="further-information"></a>Informations complémentaires  
 [Informations sur ClearType](https://www.microsoft.com/typography/ClearTypeInfo.mspx)  
  
 [ClearType Tuner PowerToy](https://www.microsoft.com/typography/ClearTypePowerToy.mspx)  
  
## <a name="see-also"></a>Voir aussi

- [Paramètres du Registre ClearType](cleartype-registry-settings.md)
