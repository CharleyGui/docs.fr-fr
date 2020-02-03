---
title: Coordinates
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms coordinates
- screen coordinates
- client coordinates
- coordinates [Windows Forms], Windows Forms
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
ms.openlocfilehash: c95888f31bfc867e9c028d53072ab3d710256708
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734665"
---
# <a name="windows-forms-coordinates"></a>Coordonnées Windows Forms
Le système de coordonnées d’un Windows Form est basé sur les coordonnées de l’appareil, et l’unité de mesure de base lors du dessin dans Windows Forms est l’unité de l’appareil (en général, le pixel). Les points sur l’écran sont décrits par des paires de coordonnées x et y, avec les coordonnées x qui s’accroissent à droite et les coordonnées y qui s’incrémentent de haut en bas. L’emplacement de l’origine, par rapport à l’écran, varie selon que vous spécifiez des coordonnées d’écran ou de client.  
  
## <a name="screen-coordinates"></a>Coordonnées d’écran  
 Une application Windows Forms spécifie la position d’une fenêtre sur l’écran en coordonnées d’écran. Pour les coordonnées d’écran, l’origine est l’angle supérieur gauche de l’écran. La position complète d’une fenêtre est souvent décrite par une structure <xref:System.Drawing.Rectangle> contenant les coordonnées d’écran de deux points qui définissent les angles supérieur gauche et inférieur droit de la fenêtre.  
  
## <a name="client-coordinates"></a>Coordonnées clientes  
 Une application Windows Forms spécifie la position des points dans un formulaire ou un contrôle à l’aide de coordonnées clientes. L’origine des coordonnées clientes est l’angle supérieur gauche de la zone cliente du contrôle ou du formulaire. Les coordonnées clientes garantissent qu’une application peut utiliser des valeurs de coordonnées cohérentes lors du dessin dans un formulaire ou un contrôle, indépendamment de la position du formulaire ou du contrôle sur l’écran.  
  
 Les dimensions de la zone cliente sont également décrites par une structure <xref:System.Drawing.Rectangle> qui contient les coordonnées clientes pour la zone. Dans tous les cas, la coordonnée supérieure gauche du rectangle est incluse dans la zone cliente, tandis que la coordonnée inférieure droite est exclue. Les opérations graphiques n’incluent pas les bords droits et inférieurs d’une zone cliente. Par exemple, la méthode <xref:System.Drawing.Graphics.FillRectangle%2A> se remplit à droite et à la limite inférieure du rectangle spécifié, mais n’inclut pas ces bords.  
  
## <a name="mapping-from-one-type-of-coordinate-to-another"></a>Mappage d’un type de coordonnée à un autre  
 Parfois, vous devrez peut-être mapper les coordonnées d’écran aux coordonnées clientes. Vous pouvez facilement le faire à l’aide des méthodes <xref:System.Windows.Forms.Control.PointToClient%2A> et <xref:System.Windows.Forms.Control.PointToScreen%2A> disponibles dans la classe <xref:System.Windows.Forms.Control>. Par exemple, la propriété <xref:System.Windows.Forms.Control.MousePosition%2A> de <xref:System.Windows.Forms.Control> est signalée dans les coordonnées d’écran, mais vous pouvez les convertir en coordonnées clientes.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Control.PointToClient%2A>
- <xref:System.Windows.Forms.Control.PointToScreen%2A>
