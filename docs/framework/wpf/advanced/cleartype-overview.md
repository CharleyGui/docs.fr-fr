---
title: Vue d'ensemble de ClearType
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], ClearType technology
- ClearType [WPF], technology
ms.assetid: 7e2392e0-75dc-463d-a716-908772782431
ms.openlocfilehash: dbef816a995d9f4909a887f017da29bab6fc3702
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015638"
---
# <a name="cleartype-overview"></a>Vue d'ensemble de ClearType
Cette rubrique fournit une vue d’ensemble de la technologie Microsoft ClearType disponible [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]dans le.  

<a name="overview"></a>   
## <a name="technology-overview"></a>Vue d’ensemble de la technologie  
 ClearType est une technologie logicielle développée par Microsoft qui améliore la lisibilité du texte sur les écrans LCD existants (affichages à cristaux liquides), tels que les écrans d’ordinateurs portables, les écrans de Pocket PC et les écrans plats.  ClearType fonctionne en accédant aux éléments individuels de la bande de couleur verticale dans chaque pixel d’un écran LCD. Avant ClearType, le plus petit niveau de détail qu’un ordinateur peut afficher était un pixel unique, mais avec ClearType exécuté sur un moniteur LCD, nous pouvons maintenant afficher des fonctionnalités de texte aussi petites qu’une fraction d’un pixel en largeur. Cette résolution accrue augmente la netteté des détails dans l’affichage textuel, ce qui facilite grandement la lecture pendant des périodes prolongées.  
  
 Le ClearType disponible dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] est la dernière génération de ClearType qui offre plusieurs améliorations par rapport à la version de Microsoft Windows Graphics Device Interface (GDI).  
  
<a name="sub-pixel_positioning"></a>   
## <a name="sub-pixel-positioning"></a>Positionnement du sous-pixel  
 L’une des améliorations significatives par rapport à la version précédente de ClearType est l’utilisation du positionnement sous-pixel. Contrairement à l’implémentation ClearType trouvée dans GDI, le ClearType trouvé [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] dans permet aux glyphes de démarrer dans le pixel et pas seulement dans la limite de début du pixel. Grâce à cette résolution supérieure du positionnement des glyphes, l’espacement et les proportions des glyphes sont plus précis et cohérents.  
  
 Les deux exemples suivants montrent de quelle manière les glyphes peuvent commencer sur une limite de sous-pixel quand le positionnement du sous-pixel est utilisé. L’exemple de gauche est rendu à l’aide de la version antérieure du convertisseur ClearType, qui n’utilisait pas le positionnement du sous-pixel. L’exemple de droite est rendu à l’aide de la nouvelle version du convertisseur ClearType, en utilisant le positionnement du sous-pixel. Comme vous pouvez le constater, les lettres **e** et **l** de l’image de droite sont restituées de manière légèrement différente car elles démarrent toutes sur un sous-pixel différent. Quand vous affichez le texte à sa taille normale sur l’écran, cette différence n’est pas visible en raison du contraste élevé de l’image de glyphe. Cela est possible uniquement en raison d’un filtrage de couleurs sophistiqué incorporé dans ClearType.  
  
 ![Texte affiché avec deux versions de ClearType](./media/wcpsdk-mmgraphics-text-cleartype-overview-01.png "wcpsdk_mmgraphics_text_cleartype_overview_01")  
Texte affiché avec l’ancienne et la nouvelle version de ClearType  
  
 Les deux exemples suivants comparent la sortie de l’ancien convertisseur ClearType à la nouvelle version du convertisseur ClearType. Le positionnement du sous-pixel, illustré à droite, améliore considérablement l’espacement de type sur l’écran, en particulier à de petites tailles, quand la différence entre un sous-pixel et un pixel entier représente une proportion importante de la largeur du glyphe. Notez que l’espacement entre les lettres est plus régulier dans la deuxième image. L’avantage cumulatif du positionnement des sous-pixels sur l’apparence globale d’un écran de texte est considérablement augmenté et représente une évolution significative de la technologie ClearType.  
  
 ![Texte affiché avec une version antérieure de ClearType](./media/wcpsdk-mmgraphics-text-cleartype-overview-02.png "wcpsdk_mmgraphics_text_cleartype_overview_02")  
Texte avec l’ancienne et la nouvelle version de ClearType  
  
<a name="y-direction_antialiasing"></a>   
## <a name="y-direction-antialiasing"></a>Anticrénelage de direction y  
 Une autre amélioration de ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] dans est l’anticrénelage de direction y. Le ClearType dans GDI sans anticrénelage de direction y offre une meilleure résolution sur l’axe x, mais pas sur l’axe y. Sur le haut et le bas des courbes marquées, les bords dentelés diminuent la lisibilité.  
  
 L’exemple suivant montre le résultat obtenu en l’absence d’anticrénelage de direction y. Dans ce cas, les bords dentelés sur le haut et le bas de la lettre sont apparents.  
  
 ![Texte avec bords dentelés sur les courbes superficielles](./media/wcpsdk-mmgraphics-text-cleartype-overview-03.png "wcpsdk_mmgraphics_text_cleartype_overview_03")  
Texte avec bords dentelés sur les courbes marquées  
  
 ClearType dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit l’anticrénelage sur le niveau de direction y pour lisser les bords dentelés. Cette fonctionnalité est particulièrement importante pour améliorer la lisibilité des langues d’Extrême-Orient, dont les idéogrammes comptent quasiment autant de courbes marquées horizontales que verticales.  
  
 L’exemple suivant montre le résultat de l’anticrénelage de direction y. Dans ce cas, le haut et le bas de la lettre affichent une courbe lissée.  
  
 ![Texte avec l’anticrénelage&#45;de direction&#45;y ClearType](./media/wcpsdk-mmgraphics-text-cleartype-overview-04.png "wcpsdk_mmgraphics_text_cleartype_overview_04")  
Texte avec anticrénelage ClearType dans la direction y  
  
<a name="hardware_acceleration"></a>   
## <a name="hardware-acceleration"></a>Accélération matérielle  
 ClearType dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] peut tirer parti de l’accélération matérielle pour améliorer les performances et réduire la charge du processeur et les besoins en mémoire système. En utilisant les nuanceurs de pixels et la mémoire vidéo d’une carte graphique, ClearType permet un rendu plus rapide du texte, en particulier lorsque l’animation est utilisée.  
  
 ClearType dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ne modifie pas les paramètres ClearType à l’ensemble du système. La désactivation de ClearType dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Windows définit l’anticrénelage en mode nuances de gris. En outre, ClearType dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ne modifie pas les paramètres du [PowerToy de tuner ClearType](https://www.microsoft.com/typography/ClearTypePowerToy.mspx).  
  
 En ce qui concerne la conception architecturale de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], il a notamment été décidé d’améliorer la prise en charge par la disposition indépendante de la résolution des moniteurs DPI de résolution supérieure, qui sont de plus en plus répandus. De ce fait, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ne prend pas en charge le rendu de texte crénelé ni les bitmaps de certaines polices d’Asie de l'Est, qui sont tous deux dépendants de la résolution.  
  
<a name="further_information"></a>   
## <a name="further-information"></a>Informations complémentaires  
 [Informations sur ClearType](https://www.microsoft.com/typography/ClearTypeInfo.mspx)  
  
 [ClearType Tuner PowerToy](https://www.microsoft.com/typography/ClearTypePowerToy.mspx)  
  
## <a name="see-also"></a>Voir aussi

- [Paramètres du Registre ClearType](cleartype-registry-settings.md)
