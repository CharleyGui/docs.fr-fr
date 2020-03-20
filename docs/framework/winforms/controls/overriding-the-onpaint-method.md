---
title: Substitution de la méthode OnPaint
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Paint event [Windows Forms], handling in Windows Forms custom control
- OnPaint method [Windows Forms], overriding in Windows Forms custom controls
ms.assetid: e9ca2723-0107-4540-bb21-4f5ffb4a9906
ms.openlocfilehash: 863726a6264f01de9f00296b4a64b9fd1bb96765
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182032"
---
# <a name="overriding-the-onpaint-method"></a>Substitution de la méthode OnPaint
Les étapes de base pour prépondérer tout événement défini dans le cadre .NET sont identiques et sont résumées dans la liste suivante.  
  
#### <a name="to-override-an-inherited-event"></a>Remplacer un événement héréditaire  
  
1. Remplacer la `On`méthode *protégée EventName.*  
  
2. Appelez `On`la méthode *EventName* de la classe `On`de base à partir de la méthode *EventName,* de sorte que les délégués inscrits reçoivent l’événement.  
  
 L’événement <xref:System.Windows.Forms.Control.Paint> est discuté en détail ici parce <xref:System.Windows.Forms.Control.Paint> que chaque contrôle <xref:System.Windows.Forms.Control>des formulaires Windows doit remplacer l’événement dont il hérite . La <xref:System.Windows.Forms.Control> classe de base ne sait pas comment un contrôle dérivé doit <xref:System.Windows.Forms.Control.OnPaint%2A> être dessiné et ne fournit aucune logique de peinture dans la méthode. La <xref:System.Windows.Forms.Control.OnPaint%2A> méthode <xref:System.Windows.Forms.Control> de simplement <xref:System.Windows.Forms.Control.Paint> envoyer l’événement aux récepteurs d’événements enregistrés.  
  
 Si vous avez travaillé à travers l’échantillon dans [Comment: Développer un contrôle simple des formulaires Windows](how-to-develop-a-simple-windows-forms-control.md), vous avez vu un exemple de dépassement de la <xref:System.Windows.Forms.Control.OnPaint%2A> méthode. Le fragment de code suivant provient de cet échantillon.  
  
```vb  
Public Class FirstControl  
   Inherits Control  
  
   Public Sub New()  
   End Sub  
  
   Protected Overrides Sub OnPaint(e As PaintEventArgs)  
      ' Call the OnPaint method of the base class.  
      MyBase.OnPaint(e)  
      ' Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, New SolidBrush(ForeColor), RectangleF.op_Implicit(ClientRectangle))  
   End Sub  
End Class
```  
  
```csharp  
public class FirstControl : Control {  
   public FirstControl() {}  
   protected override void OnPaint(PaintEventArgs e) {  
      // Call the OnPaint method of the base class.  
      base.OnPaint(e);  
      // Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, new SolidBrush(ForeColor), ClientRectangle);  
   }
}
```  
  
 La <xref:System.Windows.Forms.PaintEventArgs> classe contient <xref:System.Windows.Forms.Control.Paint> des données pour l’événement. Il a deux propriétés, comme indiqué dans le code suivant.  
  
```vb  
Public Class PaintEventArgs  
   Inherits EventArgs  
   ...  
   Public ReadOnly Property ClipRectangle() As System.Drawing.Rectangle  
      ...  
   End Property  
  
   Public ReadOnly Property Graphics() As System.Drawing.Graphics  
      ...  
   End Property
   ...  
End Class  
```  
  
```csharp  
public class PaintEventArgs : EventArgs {  
...  
    public System.Drawing.Rectangle ClipRectangle {}  
    public System.Drawing.Graphics Graphics {}  
...  
}  
```  
  
 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>est le rectangle à peindre, et <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> la <xref:System.Drawing.Graphics> propriété se réfère à un objet. Les classes <xref:System.Drawing?displayProperty=nameWithType> dans l’espace de nom sont des classes gérées qui donnent accès à la fonctionnalité de GDI, la nouvelle bibliothèque graphique Windows. L’objet <xref:System.Drawing.Graphics> a des méthodes pour dessiner des points, des cordes, des lignes, des arcs, des ellipses, et beaucoup d’autres formes.  
  
 Un contrôle invoque sa <xref:System.Windows.Forms.Control.OnPaint%2A> méthode chaque fois qu’il a besoin de changer son affichage visuel. Cette méthode soulève <xref:System.Windows.Forms.Control.Paint> à son tour l’événement.  
  
## <a name="see-also"></a>Voir aussi

- [Événements](../../../standard/events/index.md)
- [Rendu d'un contrôle Windows Forms](rendering-a-windows-forms-control.md)
- [Définition d’un événement](defining-an-event-in-windows-forms-controls.md)
