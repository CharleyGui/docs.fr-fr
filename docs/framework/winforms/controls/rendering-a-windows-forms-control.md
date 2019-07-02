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
ms.openlocfilehash: 76506e504fdaca83fee502111dbadab5cb41d9b9
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506179"
---
# <a name="rendering-a-windows-forms-control"></a>Rendu d'un contrôle Windows Forms
Le rendu désigne le processus de création d’une représentation visuelle sur l’écran d’un utilisateur. Windows Forms utilise GDI (la nouvelle bibliothèque de graphiques Windows) pour le rendu. Les classes managées qui fournissent l’accès à GDI sont dans le <xref:System.Drawing?displayProperty=nameWithType> espace de noms et ses sous-espaces de noms.  
  
 Les éléments suivants sont impliqués dans le rendu du contrôle :  
  
- Fonctionnalités de dessin fournies par la classe de base <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
- Les éléments essentiels de la bibliothèque de graphiques GDI.  
  
- La géométrie de la zone de dessin.  
  
- La procédure pour libérer les ressources graphiques.  
  
## <a name="drawing-functionality-provided-by-control"></a>La fonctionnalité fournie par le contrôle de dessin  
 La classe de base <xref:System.Windows.Forms.Control> fournit des fonctionnalités de dessin via son <xref:System.Windows.Forms.Control.Paint> événement. Un contrôle déclenche le <xref:System.Windows.Forms.Control.Paint> événement chaque fois qu’il doit mettre à jour son affichage. Pour plus d’informations sur les événements dans le .NET Framework, consultez [gestion et déclenchement d’événements](../../../standard/events/index.md).  
  
 Les données d’événement de classe pour le <xref:System.Windows.Forms.Control.Paint> événement, <xref:System.Windows.Forms.PaintEventArgs>, contient les données nécessaires pour dessiner un contrôle, un handle vers un objet graphique et un objet rectangle qui représente la région du dessin. Ces objets sont affichés en gras dans le fragment de code suivant.  
  
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
  
 <xref:System.Drawing.Graphics> est une classe managée qui encapsule les fonctionnalités de dessin, comme décrit dans la discussion de GDI plus loin dans cette rubrique. Le <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> est une instance de la <xref:System.Drawing.Rectangle> structurer et définit la zone disponible dans laquelle un contrôle peut être dessiné. Un développeur de contrôles peut calculer la <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> à l’aide de la <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> propriété d’un contrôle, comme décrit dans la discussion de géométrie plus loin dans cette rubrique.  
  
 Un contrôle doit fournir une logique de rendu en substituant la <xref:System.Windows.Forms.Control.OnPaint%2A> méthode qu’elle hérite <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control.OnPaint%2A> Obtient l’accès à un objet graphics et un rectangle à dessiner via la <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> et le <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> propriétés de la <xref:System.Windows.Forms.PaintEventArgs> instance passée à ce dernier.  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 Le <xref:System.Windows.Forms.Control.OnPaint%2A> méthode de la base de <xref:System.Windows.Forms.Control> classe n’implémente pas les fonctionnalités de dessin, mais appelle simplement les délégués d’événements qui sont inscrits avec le <xref:System.Windows.Forms.Control.Paint> événement. Lorsque vous substituez <xref:System.Windows.Forms.Control.OnPaint%2A>, vous devez généralement appeler le <xref:System.Windows.Forms.Control.OnPaint%2A> réception de la méthode de la classe de base afin que les délégués inscrits le <xref:System.Windows.Forms.Control.Paint> événement. Toutefois, les contrôles qui peignent la totalité de leur surface ne doivent pas appeler de la classe de base <xref:System.Windows.Forms.Control.OnPaint%2A>, car cela entraîne le scintillement. Pour obtenir un exemple de substitution de la <xref:System.Windows.Forms.Control.OnPaint%2A> événement, consultez le [Comment : Créer un contrôle Windows Forms affiche la progression](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
> [!NOTE]
>  N’appelez pas <xref:System.Windows.Forms.Control.OnPaint%2A> directement à partir de votre contrôle ; au lieu de cela, appelez le <xref:System.Windows.Forms.Control.Invalidate%2A> (méthode) (héritée de <xref:System.Windows.Forms.Control>) ou toute autre méthode qui appelle <xref:System.Windows.Forms.Control.Invalidate%2A>. Le <xref:System.Windows.Forms.Control.Invalidate%2A> méthode appelle à son tour <xref:System.Windows.Forms.Control.OnPaint%2A>. Le <xref:System.Windows.Forms.Control.Invalidate%2A> méthode est surchargée et, selon les arguments fournis à <xref:System.Windows.Forms.Control.Invalidate%2A> `e`, un contrôle redessine une partie ou la totalité de sa zone d’écran.  
  
 La base de <xref:System.Windows.Forms.Control> classe définit une autre méthode qui est utile pour le dessin, le <xref:System.Windows.Forms.Control.OnPaintBackground%2A> (méthode).  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> peint l’arrière-plan (et donc la forme) de la fenêtre et est garanti être rapide, tout en <xref:System.Windows.Forms.Control.OnPaint%2A> peint les détails et peut être plus lent, car les demandes de peinture individuelles sont combinées en une seule <xref:System.Windows.Forms.Control.Paint> événement qui couvre tous les domaines qui doivent être redessinée. Vous souhaiterez peut-être appeler le <xref:System.Windows.Forms.Control.OnPaintBackground%2A> si, par exemple, vous souhaitez dessiner un arrière-plan dégradé de couleur pour votre contrôle.  
  
 Bien que <xref:System.Windows.Forms.Control.OnPaintBackground%2A> possède une nomenclature de type événement et prend le même argument que la `OnPaint` (méthode), <xref:System.Windows.Forms.Control.OnPaintBackground%2A> n’est pas une véritable méthode d’événements. Il existe aucune `PaintBackground` événement et <xref:System.Windows.Forms.Control.OnPaintBackground%2A> n’appelle pas de délégués d’événements. Lors du remplacement de la <xref:System.Windows.Forms.Control.OnPaintBackground%2A> méthode, une classe dérivée n’est pas requise pour appeler le <xref:System.Windows.Forms.Control.OnPaintBackground%2A> méthode de sa classe de base.  
  
## <a name="gdi-basics"></a>Principes de base GDI +  
 Le <xref:System.Drawing.Graphics> classe fournit des méthodes permettant de dessiner diverses formes, telles que des cercles, des triangles, des arcs et des ellipses, ainsi que des méthodes pour l’affichage de texte. Le <xref:System.Drawing?displayProperty=nameWithType> espace de noms et ses sous-espaces de noms contiennent des classes qui encapsulent des éléments graphiques tels que les formes (cercles, rectangles, des arcs et autres), des couleurs, des polices, des pinceaux et ainsi de suite. Pour plus d’informations sur GDI, consultez [à l’aide des Classes managées graphiques](../advanced/using-managed-graphics-classes.md). L’essentiel de GDI est également décrits dans le [Comment : Créer un contrôle Windows Forms affiche la progression](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## <a name="geometry-of-the-drawing-region"></a>Géométrie de la zone de dessin  
 Le <xref:System.Windows.Forms.Control.ClientRectangle%2A> propriété d’un contrôle spécifie la région rectangulaire disponible pour le contrôle sur l’écran de l’utilisateur, tandis que le <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> propriété du <xref:System.Windows.Forms.PaintEventArgs> spécifie la zone qui est réellement peint. (N’oubliez pas que la peinture est effectuée le <xref:System.Windows.Forms.Control.Paint> méthode d’événement qui prend un <xref:System.Windows.Forms.PaintEventArgs> instance comme argument). Un contrôle deviez peindre uniquement une partie de sa zone disponible, comme c’est le cas lorsqu’une petite section de modifications d’affichage du contrôle. Dans ces situations, un développeur de contrôle doit calculer le rectangle réel pour dessiner dans et transmettez-la à <xref:System.Windows.Forms.Control.Invalidate%2A>. Les versions surchargées de <xref:System.Windows.Forms.Control.Invalidate%2A> qui prennent un <xref:System.Drawing.Rectangle> ou <xref:System.Drawing.Region> en tant qu’argument utilisent cet argument pour générer la <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> propriété du <xref:System.Windows.Forms.PaintEventArgs>.  
  
 Le code suivant fragment montre comment la `FlashTrackBar` contrôle personnalisé calcule la zone rectangulaire dans laquelle dessiner. Le `client` variable désigne le <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> propriété. Pour obtenir un exemple complet, consultez [Comment : Créer un contrôle Windows Forms affiche la progression](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a>Libération des ressources graphiques  
 Objets graphiques sont coûteux, car elles utilisent des ressources système. Ces objets incluent des instances de la <xref:System.Drawing.Graphics?displayProperty=nameWithType> classe ainsi que des instances de <xref:System.Drawing.Brush?displayProperty=nameWithType>, <xref:System.Drawing.Pen?displayProperty=nameWithType>et d’autres classes de graphiques. Il est important que vous créez une ressource de graphiques uniquement lorsque vous en avez besoin et libérez-le dès que vous avez fini de l’utiliser. Si vous créez un type qui implémente le <xref:System.IDisposable> l’interface, appeler ses <xref:System.IDisposable.Dispose%2A> méthode lorsque vous avez terminé avec lui afin de libérer des ressources.  
  
 Le code suivant fragment montre comment la `FlashTrackBar` contrôle personnalisé crée et libère un <xref:System.Drawing.Brush> ressource. Pour le code source complet, consultez [Comment : Créer un contrôle Windows Forms affiche la progression](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour Créer un contrôle Windows Forms affiche la progression](how-to-create-a-windows-forms-control-that-shows-progress.md)
