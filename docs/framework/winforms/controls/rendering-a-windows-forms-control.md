---
title: Rendu d'un contrôle Windows Forms
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
ms.openlocfilehash: b24fbefac0dcfb666e25ad1d1726ef2cf8a5d84e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968276"
---
# <a name="rendering-a-windows-forms-control"></a>Rendu d'un contrôle Windows Forms
Le rendu fait référence au processus de création d’une représentation visuelle sur l’écran d’un utilisateur. Windows Forms utilise GDI (la nouvelle bibliothèque de graphiques Windows) pour le rendu. Les classes managées qui fournissent l’accès à GDI se <xref:System.Drawing?displayProperty=nameWithType> trouvent dans l’espace de noms et ses sous-espaces de noms.  
  
 Les éléments suivants sont impliqués dans le rendu de contrôle:  
  
- La fonctionnalité de dessin fournie par la classe <xref:System.Windows.Forms.Control?displayProperty=nameWithType>de base.  
  
- Éléments essentiels de la bibliothèque de graphiques GDI.  
  
- Géométrie de la zone de dessin.  
  
- Procédure de libération des ressources graphiques.  
  
## <a name="drawing-functionality-provided-by-control"></a>Fonctionnalités de dessin fournies par le contrôle  
 La classe <xref:System.Windows.Forms.Control> de base fournit des fonctionnalités de <xref:System.Windows.Forms.Control.Paint> dessin via son événement. Un contrôle déclenche l' <xref:System.Windows.Forms.Control.Paint> événement chaque fois qu’il doit mettre à jour son affichage. Pour plus d’informations sur les événements dans le .NET Framework, consultez [gestion et déclenchement d’événements](../../../standard/events/index.md).  
  
 La classe de données d’événement <xref:System.Windows.Forms.Control.Paint> de l' <xref:System.Windows.Forms.PaintEventArgs>événement,, contient les données nécessaires pour dessiner un contrôle: un handle vers un objet Graphics et un objet rectangle qui représente la zone dans laquelle dessiner. Ces objets sont affichés en gras dans le fragment de code suivant.  
  
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
  
 <xref:System.Drawing.Graphics>est une classe managée qui encapsule les fonctionnalités de dessin, comme décrit dans la discussion sur GDI plus loin dans cette rubrique. Est une instance de la <xref:System.Drawing.Rectangle> structure et définit la zone disponible dans laquelle un contrôle peut être dessiné. <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> Un développeur de contrôle peut calculer <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> à l’aide de la <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> propriété d’un contrôle, comme décrit dans la section géométrie plus loin dans cette rubrique.  
  
 Un contrôle doit fournir une logique de rendu en substituant la <xref:System.Windows.Forms.Control.OnPaint%2A> méthode dont il hérite. <xref:System.Windows.Forms.Control> <xref:System.Windows.Forms.Control.OnPaint%2A>Obtient l’accès à un objet Graphics et un rectangle dans lequel dessiner <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> par le <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> biais des propriétés <xref:System.Windows.Forms.PaintEventArgs> et de l’instance qui lui est passée.  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 La <xref:System.Windows.Forms.Control.OnPaint%2A> méthode de la classe <xref:System.Windows.Forms.Control> de base n’implémente pas de fonctionnalité de dessin, mais appelle simplement les délégués d’événements inscrits <xref:System.Windows.Forms.Control.Paint> avec l’événement. Lorsque vous substituez <xref:System.Windows.Forms.Control.OnPaint%2A>, vous devez généralement appeler la <xref:System.Windows.Forms.Control.OnPaint%2A> méthode de la classe de base afin que les délégués inscrits <xref:System.Windows.Forms.Control.Paint> reçoivent l’événement. Toutefois, les contrôles qui peignent leur surface entière ne doivent pas appeler la <xref:System.Windows.Forms.Control.OnPaint%2A>classe de base, car cela introduit le scintillement. Pour obtenir un exemple de substitution de <xref:System.Windows.Forms.Control.OnPaint%2A> l’événement, consultez [la procédure: Créez un contrôle de Windows Forms qui affiche](how-to-create-a-windows-forms-control-that-shows-progress.md)la progression.  
  
> [!NOTE]
> N’appelez <xref:System.Windows.Forms.Control.OnPaint%2A> pas directement à partir de votre contrôle. Appelez plutôt <xref:System.Windows.Forms.Control.Invalidate%2A> la méthode (héritée de <xref:System.Windows.Forms.Control> <xref:System.Windows.Forms.Control.Invalidate%2A>) ou une autre méthode qui appelle. La <xref:System.Windows.Forms.Control.Invalidate%2A> méthode<xref:System.Windows.Forms.Control.OnPaint%2A>appelle à son tour. La <xref:System.Windows.Forms.Control.Invalidate%2A> méthode est surchargée et, selon les arguments fournis à <xref:System.Windows.Forms.Control.Invalidate%2A> `e`, un contrôle redessine une partie ou la totalité de sa zone d’écran.  
  
 La classe <xref:System.Windows.Forms.Control> de base définit une autre méthode utile pour le dessin, <xref:System.Windows.Forms.Control.OnPaintBackground%2A> la méthode.  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A>peint l’arrière-plan (et par conséquent la forme) de la fenêtre et est garanti être rapide <xref:System.Windows.Forms.Control.OnPaint%2A> , tandis que peint les détails et peut être plus lent, car les <xref:System.Windows.Forms.Control.Paint> demandes de peinture individuelles sont combinées en un événement qui couvre toutes les zones devant être redessiné. Vous souhaiterez peut-être <xref:System.Windows.Forms.Control.OnPaintBackground%2A> appeler si, par exemple, vous souhaitez dessiner un arrière-plan de couleur de dégradé pour votre contrôle.  
  
 Bien <xref:System.Windows.Forms.Control.OnPaintBackground%2A> que ait une nomenclature de type événement et accepte le même argument que `OnPaint` la méthode <xref:System.Windows.Forms.Control.OnPaintBackground%2A> , n’est pas une véritable méthode d’événement. Il n’y `PaintBackground` a aucun <xref:System.Windows.Forms.Control.OnPaintBackground%2A> événement et n’appelle pas les délégués d’événement. Lors de la substitution <xref:System.Windows.Forms.Control.OnPaintBackground%2A> de la méthode, une classe dérivée n’est pas <xref:System.Windows.Forms.Control.OnPaintBackground%2A> requise pour appeler la méthode de sa classe de base.  
  
## <a name="gdi-basics"></a>Notions de base sur GDI+  
 La <xref:System.Drawing.Graphics> classe fournit des méthodes pour dessiner différentes formes, telles que des cercles, des triangles, des arcs et des ellipses, ainsi que des méthodes pour afficher du texte. L' <xref:System.Drawing?displayProperty=nameWithType> espace de noms et ses sous-espaces de noms contiennent des classes qui encapsulent des éléments graphiques tels que des formes (cercles, rectangles, arcs et autres), des couleurs, des polices, des pinceaux, etc. Pour plus d’informations sur GDI, consultez [utilisation de classes graphiques managées](../advanced/using-managed-graphics-classes.md). Les notions fondamentales de GDI sont également décrites dans la [procédure: Créez un contrôle de Windows Forms qui affiche](how-to-create-a-windows-forms-control-that-shows-progress.md)la progression.  
  
## <a name="geometry-of-the-drawing-region"></a>Géométrie de la zone de dessin  
 La <xref:System.Windows.Forms.Control.ClientRectangle%2A> propriété d’un contrôle spécifie la zone rectangulaire disponible pour le contrôle sur l’écran de l’utilisateur, <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> tandis <xref:System.Windows.Forms.PaintEventArgs> que la propriété de spécifie la zone effectivement peinte. (N’oubliez pas que la peinture est <xref:System.Windows.Forms.Control.Paint> effectuée dans la méthode d' <xref:System.Windows.Forms.PaintEventArgs> événement qui prend une instance comme argument). Un contrôle peut avoir besoin de peindre uniquement une partie de sa zone disponible, comme c’est le cas lorsqu’une petite section de l’affichage du contrôle change. Dans ce cas, un développeur de contrôles doit calculer le rectangle réel à dessiner dans et le passer à <xref:System.Windows.Forms.Control.Invalidate%2A>. Les versions surchargées de <xref:System.Windows.Forms.Control.Invalidate%2A> qui acceptent un <xref:System.Drawing.Rectangle> ou <xref:System.Drawing.Region> comme argument utilisent cet argument pour générer la <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> propriété de <xref:System.Windows.Forms.PaintEventArgs>.  
  
 Le fragment de code suivant montre comment `FlashTrackBar` le contrôle personnalisé calcule la zone rectangulaire dans laquelle dessiner. La `client` variable désigne la <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> propriété. Pour obtenir un exemple complet, [consultez Procédure: Créez un contrôle de Windows Forms qui affiche](how-to-create-a-windows-forms-control-that-shows-progress.md)la progression.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a>Libération des ressources graphiques  
 Les objets graphiques sont coûteux car ils utilisent des ressources système. Ces objets incluent des instances de <xref:System.Drawing.Graphics?displayProperty=nameWithType> la classe ainsi que des instances <xref:System.Drawing.Brush?displayProperty=nameWithType>de <xref:System.Drawing.Pen?displayProperty=nameWithType>, et d’autres classes graphiques. Il est important de créer une ressource Graphics uniquement lorsque vous en avez besoin et de la libérer dès que vous avez fini de l’utiliser. Si vous créez un type qui implémente l' <xref:System.IDisposable> interface, appelez sa <xref:System.IDisposable.Dispose%2A> méthode lorsque vous en avez terminé pour libérer des ressources.  
  
 Le fragment de code suivant montre comment `FlashTrackBar` le contrôle personnalisé crée et libère <xref:System.Drawing.Brush> une ressource. Pour obtenir le code source complet, [consultez Comment: Créez un contrôle de Windows Forms qui affiche](how-to-create-a-windows-forms-control-that-shows-progress.md)la progression.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour Créer un contrôle de Windows Forms qui affiche la progression](how-to-create-a-windows-forms-control-that-shows-progress.md)
