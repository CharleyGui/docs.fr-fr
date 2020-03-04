---
title: Types de systèmes de coordonnées
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], page
- unit of measure
- world coordinate system
- page coordinate system
- page transformation
- device coordinate system
- world transformation
- coordinate systems
- transformations [Windows Forms], world
ms.assetid: c61ff50a-eb1d-4e6c-83cd-f7e9764cfa9f
ms.openlocfilehash: bbb0d4908d4a281499336d262c653d7b72f3ccdc
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159804"
---
# <a name="types-of-coordinate-systems"></a>Types de systèmes de coordonnées
GDI+ utilise trois espaces de coordonnées : World, page et Device. Les coordonnées universelles sont les coordonnées utilisées pour modéliser un environnement graphique particulier et sont les coordonnées que vous transmettez aux méthodes dans le .NET Framework. Les coordonnées de page font référence au système de coordonnées utilisé par une surface de dessin, telle qu’un formulaire ou un contrôle. Les coordonnées de l’appareil sont les coordonnées utilisées par l’appareil physique sur lequel le dessin est réalisé, tel qu’un écran ou une feuille de papier. Quand vous effectuez l’appel `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, les points que vous transmettez à la méthode <xref:System.Drawing.Graphics.DrawLine%2A>,`(0, 0)` et `(160, 80)`, se trouvent dans l’espace de coordonnées universel. Avant que GDI+ puisse dessiner la ligne sur l’écran, les coordonnées passent par une séquence de transformations. Une transformation, appelée transformation universelle, convertit les coordonnées universelles en coordonnées de page et une autre transformation, appelée transformation de page, convertit les coordonnées de page en coordonnées de périphérique.  
  
## <a name="transforms-and-coordinate-systems"></a>Transformations et systèmes de coordonnées  
 Supposons que vous souhaitiez utiliser un système de coordonnées dont l’origine se trouve dans le corps de la zone cliente plutôt que dans le coin supérieur gauche. Par exemple, imaginons que vous souhaitiez que l’origine soit de 100 pixels du bord gauche de la zone cliente et de 50 pixels en haut de la zone cliente. L’illustration suivante montre un tel système de coordonnées.  
  
 ![Système de coordonnées](./media/aboutgdip05-art01.gif "AboutGdip05_art01")  
  
 Lorsque vous effectuez l’appel `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, vous recevez la ligne indiquée dans l’illustration suivante.  
  
 ![Système de coordonnées](./media/aboutgdip05-art02.gif "AboutGdip05_art02")  
  
 Les coordonnées des points de terminaison de votre ligne dans les trois espaces de coordonnées sont les suivantes :  
  
|||  
|-|-|  
|Réelles|(0, 0) à (160, 80)|  
|Page|(100, 50) vers (260, 130)|  
|Appareil|(100, 50) vers (260, 130)|  
  
 Notez que l’espace de coordonnées de la page a son origine dans l’angle supérieur gauche de la zone cliente. ce sera toujours le cas. Notez également que, étant donné que l’unité de mesure est le pixel, les coordonnées de l’appareil sont les mêmes que les coordonnées de la page. Si vous définissez l’unité de mesure sur une valeur autre que les pixels (par exemple, pouces), les coordonnées de l’appareil seront différentes des coordonnées de la page.  
  
 La transformation universelle, qui mappe les coordonnées universelles aux coordonnées de la page, est conservée dans la propriété <xref:System.Drawing.Graphics.Transform%2A> de la classe <xref:System.Drawing.Graphics>. Dans l’exemple précédent, la transformation universelle est une translation de 100 unités sur la direction x et de 50 unités sur l’axe y. L’exemple suivant définit la transformation universelle d’un objet <xref:System.Drawing.Graphics>, puis utilise cet objet <xref:System.Drawing.Graphics> pour dessiner la ligne indiquée dans la figure précédente :  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 La transformation de page mappe les coordonnées de page aux coordonnées de l’appareil. La classe <xref:System.Drawing.Graphics> fournit les propriétés <xref:System.Drawing.Graphics.PageUnit%2A> et <xref:System.Drawing.Graphics.PageScale%2A> pour la manipulation de la transformation de page. La classe <xref:System.Drawing.Graphics> fournit également deux propriétés en lecture seule, <xref:System.Drawing.Graphics.DpiX%2A> et <xref:System.Drawing.Graphics.DpiY%2A>, pour l’examen des points horizontaux et verticaux par pouce du périphérique d’affichage.  
  
 Vous pouvez utiliser la propriété <xref:System.Drawing.Graphics.PageUnit%2A> de la classe <xref:System.Drawing.Graphics> pour spécifier une unité de mesure autre que le pixel.  
  
> [!NOTE]
> Vous ne pouvez pas définir la propriété <xref:System.Drawing.Graphics.PageUnit%2A> sur <xref:System.Drawing.GraphicsUnit.World>, car il ne s’agit pas d’une unité physique et lève une exception.  
  
 L’exemple suivant dessine une ligne de (0,0) à (2, 1), où le point (2, 1) est de 2 pouces à droite et de 1 pouce en dessous du point (0, 0) :  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
> Si vous ne spécifiez pas de largeur du stylet lorsque vous construisez votre stylet, l’exemple précédent dessine une ligne d’une largeur d’un pouce. Vous pouvez spécifier la largeur du stylet dans le deuxième argument du constructeur <xref:System.Drawing.Pen> :  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 Si nous supposons que le périphérique d’affichage a 96 points par pouce dans la direction horizontale et 96 points par pouce dans la direction verticale, les points de terminaison de la ligne de l’exemple précédent ont les coordonnées suivantes dans les trois espaces de coordonnées :  
  
|||  
|-|-|  
|Réelles|(0, 0) à (2, 1)|  
|Page|(0, 0) à (2, 1)|  
|Appareil|(0, 0) à (192, 96)|  
  
 Notez que, étant donné que l’origine de l’espace de coordonnées universel est située dans le coin supérieur gauche de la zone cliente, les coordonnées de page sont les mêmes que les coordonnées universelles.  
  
 Vous pouvez combiner les transformations universelles et de page pour obtenir un grand nombre d’effets. Par exemple, supposons que vous souhaitiez utiliser des pouces comme unité de mesure et que vous souhaitez que l’origine de votre système de coordonnées soit de 2 pouces à partir du bord gauche de la zone cliente et de 1/2 centimètres à partir du haut de la zone cliente. L’exemple suivant définit les transformations universelles et de page d’un objet <xref:System.Drawing.Graphics>, puis dessine une ligne de (0,0) à (2,3) :  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 L’illustration suivante montre la ligne et le système de coordonnées.  
  
 ![Système de coordonnées](./media/aboutgdip05-art03.gif "AboutGdip05_art03")  
  
 Si nous supposons que le périphérique d’affichage a 96 points par pouce dans la direction horizontale et 96 points par pouce dans la direction verticale, les points de terminaison de la ligne de l’exemple précédent ont les coordonnées suivantes dans les trois espaces de coordonnées :  
  
|||  
|-|-|  
|Réelles|(0, 0) à (2, 1)|  
|Page|(2, 0,5) à (4, 1,5)|  
|Appareil|(192, 48) vers (384, 144)|  
  
## <a name="see-also"></a>Voir aussi

- [Systèmes de coordonnées et transformations](coordinate-systems-and-transformations.md)
- [Représentation matricielle des transformations](matrix-representation-of-transformations.md)
