---
title: Restituer un contrôle
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- OnPaintBackground method [Windows Forms], invoking in Windows Forms custom controls
- custom controls [Windows Forms], graphics resources
- custom controls [Windows Forms], invalidation and painting
ms.assetid: aae8e1e6-4786-432b-a15e-f4c44760d302
ms.openlocfilehash: 0e1a7ca5dc0414d518c081b1db2dca5477d4f743
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742388"
---
# <a name="rendering-a-windows-forms-control"></a>Rendu d'un contrôle Windows Forms
Le rendu fait référence au processus de création d’une représentation visuelle sur l’écran d’un utilisateur. Windows Forms utilise GDI (la nouvelle bibliothèque de graphiques Windows) pour le rendu. Les classes managées qui fournissent l’accès à GDI se trouvent dans l’espace de noms <xref:System.Drawing?displayProperty=nameWithType> et dans ses sous-espaces de noms.  
  
 Les éléments suivants sont impliqués dans le rendu de contrôle :  
  
- La fonctionnalité de dessin fournie par la classe de base <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
- Éléments essentiels de la bibliothèque de graphiques GDI.  
  
- Géométrie de la zone de dessin.  
  
- Procédure de libération des ressources graphiques.  
  
## <a name="drawing-functionality-provided-by-control"></a>Fonctionnalités de dessin fournies par le contrôle  
 La classe de base <xref:System.Windows.Forms.Control> fournit des fonctionnalités de dessin via son événement <xref:System.Windows.Forms.Control.Paint>. Un contrôle déclenche l’événement <xref:System.Windows.Forms.Control.Paint> chaque fois qu’il doit mettre à jour son affichage. Pour plus d’informations sur les événements dans le .NET Framework, consultez [gestion et déclenchement d’événements](../../../standard/events/index.md).  
  
 La classe de données d’événement pour l’événement <xref:System.Windows.Forms.Control.Paint>, <xref:System.Windows.Forms.PaintEventArgs>, contient les données nécessaires pour dessiner un contrôle : un handle vers un objet Graphics et un objet rectangle qui représente la zone dans laquelle dessiner. Ces objets sont affichés en gras dans le fragment de code suivant.  
  
```vb  
Public Class PaintEventArgs  
   Inherits EventArgs  
   Implements IDisposable  
  
   Public ReadOnly Property ClipRectangle() As System.Drawing.Rectangle  
      ...  
   End Property  
  
   Public ReadOnly Property Graphics() As System.Drawing.Graphics  
      ...  
   End Property  
   ' Other properties and methods.  
   ...  
End Class  
```  
  
```csharp  
public class PaintEventArgs : EventArgs, IDisposable {  
public System.Drawing.Rectangle ClipRectangle {get;}  
public System.Drawing.Graphics Graphics {get;}  
// Other properties and methods.  
...  
}  
```  
  
 <xref:System.Drawing.Graphics> est une classe managée qui encapsule les fonctionnalités de dessin, comme décrit dans la discussion sur GDI plus loin dans cette rubrique. Le <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> est une instance de la structure <xref:System.Drawing.Rectangle> et définit la zone disponible dans laquelle un contrôle peut être dessiné. Un développeur de contrôle peut calculer le <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> à l’aide de la propriété <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> d’un contrôle, comme décrit dans la section géométrie plus loin dans cette rubrique.  
  
 Un contrôle doit fournir une logique de rendu en substituant la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> qu’il hérite de <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control.OnPaint%2A> obtient l’accès à un objet Graphics et un rectangle dans lequel dessiner via le <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> et les propriétés <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> de l’instance <xref:System.Windows.Forms.PaintEventArgs> qui lui est transmise.  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 La méthode <xref:System.Windows.Forms.Control.OnPaint%2A> de la classe de <xref:System.Windows.Forms.Control> de base n’implémente pas de fonctionnalité de dessin, mais appelle simplement les délégués d’événements inscrits avec l’événement <xref:System.Windows.Forms.Control.Paint>. Lorsque vous substituez <xref:System.Windows.Forms.Control.OnPaint%2A>, vous devez généralement appeler la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> de la classe de base afin que les délégués inscrits reçoivent l’événement <xref:System.Windows.Forms.Control.Paint>. Toutefois, les contrôles qui peignent leur surface entière ne doivent pas appeler la <xref:System.Windows.Forms.Control.OnPaint%2A>de la classe de base, car cela introduit le scintillement. Pour obtenir un exemple de substitution de l’événement <xref:System.Windows.Forms.Control.OnPaint%2A>, consultez la rubrique [Comment : créer un contrôle Windows Forms qui affiche la progression](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
> [!NOTE]
> N’appelez pas <xref:System.Windows.Forms.Control.OnPaint%2A> directement à partir de votre contrôle ; au lieu de cela, appelez la méthode <xref:System.Windows.Forms.Control.Invalidate%2A> (héritée de <xref:System.Windows.Forms.Control>) ou une autre méthode qui appelle <xref:System.Windows.Forms.Control.Invalidate%2A>. La méthode <xref:System.Windows.Forms.Control.Invalidate%2A> à son tour appelle <xref:System.Windows.Forms.Control.OnPaint%2A>. La méthode <xref:System.Windows.Forms.Control.Invalidate%2A> est surchargée et, selon les arguments fournis à <xref:System.Windows.Forms.Control.Invalidate%2A> `e`, un contrôle redessine une partie ou la totalité de sa zone d’écran.  
  
 La classe de <xref:System.Windows.Forms.Control> de base définit une autre méthode qui est utile pour le dessin, la méthode <xref:System.Windows.Forms.Control.OnPaintBackground%2A>.  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> peint l’arrière-plan (et par conséquent la forme) de la fenêtre et est assuré d’être rapide, tandis que <xref:System.Windows.Forms.Control.OnPaint%2A> peint les détails et peut être plus lent, car les demandes de peinture individuelles sont combinées en un événement <xref:System.Windows.Forms.Control.Paint> qui couvre toutes les zones devant être redessinées. Vous pouvez appeler l' <xref:System.Windows.Forms.Control.OnPaintBackground%2A> si, par exemple, vous souhaitez dessiner un arrière-plan de couleur de dégradé pour votre contrôle.  
  
 Bien que <xref:System.Windows.Forms.Control.OnPaintBackground%2A> ait une nomenclature de type événement et accepte le même argument que la méthode `OnPaint`, <xref:System.Windows.Forms.Control.OnPaintBackground%2A> n’est pas une véritable méthode d’événement. Il n’y a aucun événement `PaintBackground` et <xref:System.Windows.Forms.Control.OnPaintBackground%2A> n’appelle pas les délégués d’événement. Lors de la substitution de la méthode <xref:System.Windows.Forms.Control.OnPaintBackground%2A>, une classe dérivée n’est pas requise pour appeler la méthode <xref:System.Windows.Forms.Control.OnPaintBackground%2A> de sa classe de base.  
  
## <a name="gdi-basics"></a>Notions de base sur GDI+  
 La classe <xref:System.Drawing.Graphics> fournit des méthodes pour dessiner différentes formes, telles que des cercles, des triangles, des arcs et des ellipses, ainsi que des méthodes pour afficher du texte. L’espace de noms <xref:System.Drawing?displayProperty=nameWithType> et ses sous-espaces de noms contiennent des classes qui encapsulent des éléments graphiques tels que des formes (cercles, rectangles, arcs et autres), des couleurs, des polices, des pinceaux, etc. Pour plus d’informations sur GDI, consultez [utilisation de classes graphiques managées](../advanced/using-managed-graphics-classes.md). Les notions fondamentales de GDI sont également décrites dans la rubrique [Comment : créer un contrôle de Windows Forms qui affiche la progression](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## <a name="geometry-of-the-drawing-region"></a>Géométrie de la zone de dessin  
 La propriété <xref:System.Windows.Forms.Control.ClientRectangle%2A> d’un contrôle spécifie la zone rectangulaire disponible pour le contrôle sur l’écran de l’utilisateur, tandis que la propriété <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> de <xref:System.Windows.Forms.PaintEventArgs> spécifie la zone effectivement peinte. (N’oubliez pas que la peinture est effectuée dans la méthode d’événement <xref:System.Windows.Forms.Control.Paint> qui prend une instance <xref:System.Windows.Forms.PaintEventArgs> comme argument). Un contrôle peut avoir besoin de peindre uniquement une partie de sa zone disponible, comme c’est le cas lorsqu’une petite section de l’affichage du contrôle change. Dans ce cas, un développeur de contrôle doit calculer le rectangle réel à dessiner et le passer à <xref:System.Windows.Forms.Control.Invalidate%2A>. Les versions surchargées de <xref:System.Windows.Forms.Control.Invalidate%2A> qui prennent un <xref:System.Drawing.Rectangle> ou <xref:System.Drawing.Region> comme argument utilisent cet argument pour générer la propriété <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> de <xref:System.Windows.Forms.PaintEventArgs>.  
  
 Le fragment de code suivant montre comment le `FlashTrackBar` contrôle personnalisé calcule la zone rectangulaire dans laquelle dessiner. La variable `client` désigne la propriété <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>. Pour obtenir un exemple complet, consultez [Comment : créer un contrôle de Windows Forms qui affiche la progression](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a>Libération des ressources graphiques  
 Les objets graphiques sont coûteux car ils utilisent des ressources système. Ces objets incluent des instances de la classe <xref:System.Drawing.Graphics?displayProperty=nameWithType> ainsi que des instances de <xref:System.Drawing.Brush?displayProperty=nameWithType>, <xref:System.Drawing.Pen?displayProperty=nameWithType>et d’autres classes graphiques. Il est important de créer une ressource Graphics uniquement lorsque vous en avez besoin et de la libérer dès que vous avez fini de l’utiliser. Si vous créez un type qui implémente l’interface <xref:System.IDisposable>, appelez sa méthode <xref:System.IDisposable.Dispose%2A> lorsque vous en avez terminé pour libérer des ressources.  
  
 Le fragment de code suivant montre comment le `FlashTrackBar` contrôle personnalisé crée et libère une ressource <xref:System.Drawing.Brush>. Pour obtenir le code source complet, consultez [Comment : créer un contrôle de Windows Forms qui affiche la progression](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour créer un contrôle Windows Forms qui affiche la progression](how-to-create-a-windows-forms-control-that-shows-progress.md)
