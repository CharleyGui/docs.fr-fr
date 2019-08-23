---
title: Contrôles dessinés par l'utilisateur
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user-drawn
- OnPaint method [Windows Forms]
- user-drawn controls [Windows Forms]
ms.assetid: 034af4b5-457f-4160-a937-22891817faa8
ms.openlocfilehash: 50036f5bef323368b4970a080ca7a70cf94252d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966486"
---
# <a name="user-drawn-controls"></a>Contrôles dessinés par l'utilisateur
Le .NET Framework vous permet de développer facilement vos propres contrôles. Vous pouvez créer un contrôle utilisateur, qui est un ensemble de contrôles standard liés ensemble par du code, ou vous pouvez concevoir votre propre contrôle à partir de zéro. Vous pouvez même utiliser l’héritage pour créer un contrôle qui hérite d’un contrôle existant et l’ajouter à ses fonctionnalités inhérentes. Quelle que soit l’approche que vous utilisez, le .NET Framework fournit les fonctionnalités permettant de dessiner une interface graphique personnalisée pour n’importe quel contrôle que vous créez.  
  
 La peinture d’un contrôle est effectuée par l’exécution de code dans la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> du contrôle. L’argument unique de la <xref:System.Windows.Forms.Control.OnPaint%2A> méthode est un <xref:System.Windows.Forms.PaintEventArgs> objet qui fournit toutes les informations et les fonctionnalités requises pour restituer votre contrôle. <xref:System.Windows.Forms.PaintEventArgs> Fournit comme propriétés deux objets principal qui seront utilisés dans le rendu de votre contrôle:  
  
- <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>Object: rectangle qui représente la partie du contrôle qui sera dessinée. Il peut s’agir du contrôle entier ou d’une partie du contrôle en fonction de la façon dont le contrôle est dessiné.  
  
- <xref:System.Drawing.Graphics>objet: encapsule plusieurs objets et méthodes graphiques qui fournissent les fonctionnalités nécessaires pour dessiner votre contrôle.  
  
 Pour plus d’informations sur <xref:System.Drawing.Graphics> l’objet et sur son utilisation, consultez [procédure: Créez des objets graphiques pour](../advanced/how-to-create-graphics-objects-for-drawing.md)le dessin.  
  
 L' <xref:System.Windows.Forms.Control.OnPaint%2A> événement est déclenché chaque fois que le contrôle est dessiné ou actualisé à l’écran, et l' <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> objet représente le rectangle dans lequel la peinture aura lieu. Si l’intégralité du contrôle doit être actualisée, le <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> représentera la taille de l’ensemble du contrôle. Toutefois, si seule une partie du contrôle doit être actualisée, l' <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> objet ne représente que la région qui doit être redessinée. C’est le cas, par exemple, lorsqu’un contrôle était partiellement masqué par un autre contrôle ou formulaire dans l’interface utilisateur.  
  
 Lorsque vous héritez de <xref:System.Windows.Forms.Control> la classe, vous devez substituer <xref:System.Windows.Forms.Control.OnPaint%2A> la méthode et fournir le code de rendu graphique dans. Si vous souhaitez fournir une interface graphique personnalisée à un contrôle utilisateur ou à un contrôle hérité, vous pouvez également le faire en substituant la <xref:System.Windows.Forms.Control.OnPaint%2A> méthode. Un exemple est illustré ci-dessous:  
  
```vb  
Protected Overrides Sub OnPaint(ByVal e As PaintEventArgs)  
   ' Call the OnPaint method of the base class.  
   MyBase.OnPaint(e)  
  
   ' Declare and instantiate a drawing pen.  
   Using myPen As System.Drawing.Pen = New System.Drawing.Pen(Color.Aqua)  
      ' Draw an aqua rectangle in the rectangle represented by the control.  
      e.Graphics.DrawRectangle(myPen, New Rectangle(Me.Location, Me.Size))  
   End Using
End Sub  
```  
  
```csharp  
protected override void OnPaint(PaintEventArgs e)  
{  
   // Call the OnPaint method of the base class.  
   base.OnPaint(e);  
  
   // Declare and instantiate a new pen.  
   using (System.Drawing.Pen myPen = new System.Drawing.Pen(Color.Aqua))  
   {
      // Draw an aqua rectangle in the rectangle represented by the control.  
      e.Graphics.DrawRectangle(myPen, new Rectangle(this.Location,   
         this.Size));  
   }
}  
```  
  
 L’exemple précédent montre comment restituer un contrôle avec une représentation graphique très simple. Elle appelle la <xref:System.Windows.Forms.Control.OnPaint%2A> méthode de la classe de base, elle crée <xref:System.Drawing.Pen> un objet avec lequel dessiner, puis dessine une ellipse dans <xref:System.Windows.Forms.Control.Location%2A> le rectangle déterminé par et <xref:System.Windows.Forms.Control.Size%2A> du contrôle. Bien que la plupart des codes de rendu soient beaucoup plus compliqués, cet exemple illustre l’utilisation <xref:System.Drawing.Graphics> de l’objet contenu <xref:System.Windows.Forms.PaintEventArgs> dans l’objet. Notez que si vous héritez d’une classe qui possède déjà une représentation graphique, telle que <xref:System.Windows.Forms.UserControl> ou <xref:System.Windows.Forms.Button>, et que vous ne souhaitez pas incorporer cette représentation dans votre rendu, vous ne devez pas appeler la classe de <xref:System.Windows.Forms.Control.OnPaint%2A> base méthode.  
  
 Le code de la <xref:System.Windows.Forms.Control.OnPaint%2A> méthode de votre contrôle s’exécute lorsque le contrôle est dessiné pour la première fois, et chaque fois qu’il est actualisé. Pour vous assurer que votre contrôle est redessiné chaque fois qu’il est redimensionné, ajoutez la ligne suivante au constructeur de votre contrôle:  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
> Utilisez la <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> propriété pour implémenter un contrôle non rectangulaire.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [Guide pratique pour Créer des objets graphiques pour le dessin](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [Contrôles constitutifs](constituent-controls.md)
- [Variétés de contrôles personnalisés](varieties-of-custom-controls.md)
