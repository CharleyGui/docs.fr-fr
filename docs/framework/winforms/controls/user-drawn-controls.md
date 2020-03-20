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
ms.openlocfilehash: c68c8c88376cfe7295962264c466030115f2f3db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182007"
---
# <a name="user-drawn-controls"></a>Contrôles dessinés par l'utilisateur
Le cadre .NET vous offre la possibilité de développer facilement vos propres contrôles. Vous pouvez créer un contrôle utilisateur, qui est un ensemble de contrôles standard liés entre eux par code, ou vous pouvez concevoir votre propre contrôle à partir de zéro. Vous pouvez même utiliser l’héritage pour créer un contrôle qui hérite d’un contrôle existant et ajouter à sa fonctionnalité inhérente. Quelle que soit l’approche que vous utilisez, le cadre .NET fournit la fonctionnalité pour dessiner une interface graphique personnalisée pour tout contrôle que vous créez.  
  
 La peinture d’un contrôle est accomplie par <xref:System.Windows.Forms.Control.OnPaint%2A> l’exécution du code dans la méthode du contrôle. L’argument unique <xref:System.Windows.Forms.Control.OnPaint%2A> de <xref:System.Windows.Forms.PaintEventArgs> la méthode est un objet qui fournit toutes les informations et fonctionnalités nécessaires pour rendre votre contrôle. Les <xref:System.Windows.Forms.PaintEventArgs> fournit comme propriétés deux objets principaux qui seront utilisés dans le rendu de votre contrôle:  
  
- <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>objet - le rectangle qui représente la partie du contrôle qui sera dessiné. Cela peut être l’ensemble du contrôle, ou une partie du contrôle en fonction de la façon dont le contrôle est établi.  
  
- <xref:System.Drawing.Graphics>objet - encapsule plusieurs objets et méthodes graphiques qui fournissent la fonctionnalité nécessaire pour dessiner votre contrôle.  
  
 Pour plus d’informations sur l’objet et comment l’utiliser, <xref:System.Drawing.Graphics> voir Comment : Créer des objets [graphiques pour le dessin](../advanced/how-to-create-graphics-objects-for-drawing.md).  
  
 L’événement <xref:System.Windows.Forms.Control.OnPaint%2A> est déclenché chaque fois que le contrôle <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> est dessiné ou rafraîchi sur l’écran, et l’objet représente le rectangle dans lequel la peinture aura lieu. Si l’ensemble du contrôle doit <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> être rafraîchi, le représentera la taille de l’ensemble du contrôle. Si seulement une partie du contrôle doit être <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> rafraîchie, cependant, l’objet ne représentera que la région qui doit être redessinée. Un exemple d’un tel cas serait quand un contrôle a été partiellement obscurci par un autre contrôle ou forme dans l’interface utilisateur.  
  
 Lorsque vous héritez de la <xref:System.Windows.Forms.Control> <xref:System.Windows.Forms.Control.OnPaint%2A> classe, vous devez passer outre à la méthode et fournir un code de rendu graphique à l’intérieur. Si vous souhaitez fournir une interface graphique personnalisée à un contrôle utilisateur ou à un <xref:System.Windows.Forms.Control.OnPaint%2A> contrôle hérité, vous pouvez également le faire en l’emportent sur la méthode. Voici un exemple :  
  
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
  
 L’exemple précédent montre comment rendre un contrôle avec une représentation graphique très simple. Il appelle <xref:System.Windows.Forms.Control.OnPaint%2A> la méthode de la <xref:System.Drawing.Pen> classe de base, il crée un objet avec lequel dessiner, et tire enfin une ellipse dans le rectangle déterminé par le <xref:System.Windows.Forms.Control.Location%2A> et <xref:System.Windows.Forms.Control.Size%2A> du contrôle. Bien que la plupart des codes de rendu seront beaucoup plus <xref:System.Drawing.Graphics> compliqués <xref:System.Windows.Forms.PaintEventArgs> que celui-ci, cet exemple démontre l’utilisation de l’objet contenu dans l’objet. Notez que si vous héritez d’une classe qui <xref:System.Windows.Forms.UserControl> <xref:System.Windows.Forms.Button>a déjà une représentation graphique, telle que ou, et que vous <xref:System.Windows.Forms.Control.OnPaint%2A> ne souhaitez pas intégrer cette représentation dans votre rendu, vous ne devriez pas appeler la méthode de votre classe de base.  
  
 Le code <xref:System.Windows.Forms.Control.OnPaint%2A> dans la méthode de votre contrôle s’exécute lorsque le contrôle est tiré pour la première fois, et chaque fois qu’il est actualisé. Pour vous assurer que votre contrôle est redessiné chaque fois qu’il est resized, ajoutez la ligne suivante au constructeur de votre contrôle :  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
> Utilisez <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> la propriété pour mettre en œuvre un contrôle non rectangulaire.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [Comment : créer des objets graphiques pour le dessin](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [Contrôles constitutifs](constituent-controls.md)
- [Variétés de contrôles personnalisés](varieties-of-custom-controls.md)
