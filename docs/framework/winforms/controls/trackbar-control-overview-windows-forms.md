---
title: Vue d'ensemble du contrôle TrackBar
ms.date: 03/30/2017
f1_keywords:
- TrackBar
helpviewer_keywords:
- sliders [Windows Forms], about sliders
- TrackBar control [Windows Forms], about TrackBar control
- slider controls [Windows Forms], about slider controls
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
ms.openlocfilehash: 6901405100df4633c84850757f55b756bc9a0199
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741469"
---
# <a name="trackbar-control-overview-windows-forms"></a>Vue d'ensemble du contrôle TrackBar (Windows Forms)
Le contrôle Windows Forms <xref:System.Windows.Forms.TrackBar> (parfois appelé « contrôle Slider ») est utilisé pour parcourir une grande quantité d’informations ou pour ajuster visuellement un paramètre numérique. Le contrôle <xref:System.Windows.Forms.TrackBar> comporte deux parties : le curseur de défilement, également appelé curseur et les graduations. Le curseur est la partie qui peut être ajustée. Sa position correspond à la propriété <xref:System.Windows.Forms.TrackBar.Value%2A>. Les graduations sont des indicateurs visuels espacés à intervalles réguliers. Le TrackBar se déplace par incréments que vous spécifiez et peut être aligné horizontalement ou verticalement. Par exemple, vous pouvez utiliser la barre de suivi pour contrôler la fréquence de clignotement du curseur ou la vitesse de la souris pour un système.  
  
## <a name="key-properties"></a>Propriétés de clé  
 Les propriétés de clé du contrôle <xref:System.Windows.Forms.TrackBar> sont <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>et <xref:System.Windows.Forms.TrackBar.Maximum%2A>. <xref:System.Windows.Forms.TrackBar.TickFrequency%2A> est l’espacement des graduations. <xref:System.Windows.Forms.TrackBar.Minimum%2A> et <xref:System.Windows.Forms.TrackBar.Maximum%2A> sont les valeurs les plus petites et les plus grandes qui peuvent être représentées sur la barre de suivi.  
  
 Deux autres propriétés importantes sont <xref:System.Windows.Forms.TrackBar.SmallChange%2A> et <xref:System.Windows.Forms.TrackBar.LargeChange%2A>. La valeur de la propriété <xref:System.Windows.Forms.TrackBar.SmallChange%2A> est le nombre de positions où le curseur se déplace en réponse à une pression sur la touche gauche ou droite. La valeur de la propriété <xref:System.Windows.Forms.TrackBar.LargeChange%2A> est le nombre de positions déplacées par le curseur de défilement en réponse à une pression sur la touche PG. suiv ou PG suiv, ou en réponse à des clics de souris sur la barre de suivi d’un côté ou de l’autre du curseur.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.TrackBar>
- [TrackBar, contrôle](trackbar-control-windows-forms.md)
