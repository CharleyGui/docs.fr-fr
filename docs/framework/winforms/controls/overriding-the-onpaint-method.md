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
ms.openlocfilehash: e3c48aec830cdc3ccceb8683f93e3a99ee6364e2
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506196"
---
# <a name="overriding-the-onpaint-method"></a>Substitution de la méthode OnPaint
Les étapes de base pour la substitution d’un événement défini dans le .NET Framework sont identiques et sont résumés dans la liste suivante.  
  
#### <a name="to-override-an-inherited-event"></a>Pour remplacer un événement hérité  
  
1. Remplacer l’élément protégé `On` *EventName* (méthode).  
  
2. Appeler le `On` *EventName* méthode de la classe de base à partir de l’élément substitué `On` *EventName* (méthode), afin que les délégués inscrits reçoivent l’événement.  
  
 Le <xref:System.Windows.Forms.Control.Paint> événement est décrit en détail ici, car tous les contrôles Windows Forms doivent substituer la <xref:System.Windows.Forms.Control.Paint> événement qu’il hérite <xref:System.Windows.Forms.Control>. La base de <xref:System.Windows.Forms.Control> classe ne sait pas comment un contrôle dérivé doit être dessiné et ne fournit pas de logique de peinture dans le <xref:System.Windows.Forms.Control.OnPaint%2A> (méthode). Le <xref:System.Windows.Forms.Control.OnPaint%2A> méthode de <xref:System.Windows.Forms.Control> distribue simplement le <xref:System.Windows.Forms.Control.Paint> événement aux récepteurs d’événements inscrits.  
  
 Si vous avez utilisé l’exemple dans [Comment : Développer un contrôle de formulaires Windows Simple](how-to-develop-a-simple-windows-forms-control.md), vous avez vu un exemple de substitution le <xref:System.Windows.Forms.Control.OnPaint%2A> (méthode). Le fragment de code suivant provient de cet exemple.  
  
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
  
 Le <xref:System.Windows.Forms.PaintEventArgs> classe contient des données pour le <xref:System.Windows.Forms.Control.Paint> événement. Il a deux propriétés, comme indiqué dans le code suivant.  
  
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
  
 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> est le rectangle à peindre et la <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> propriété fait référence à un <xref:System.Drawing.Graphics> objet. Les classes dans le <xref:System.Drawing?displayProperty=nameWithType> espace de noms sont gérés les classes qui fournissent l’accès aux fonctionnalités de GDI +, la nouvelle bibliothèque de graphiques Windows. Le <xref:System.Drawing.Graphics> objet possède des méthodes pour dessiner des points, chaînes, lignes, arcs, points de suspension et de nombreuses autres formes.  
  
 Un contrôle appelle son <xref:System.Windows.Forms.Control.OnPaint%2A> méthode chaque fois qu’il doit modifier son affichage visuel. Cette méthode déclenche à son tour le <xref:System.Windows.Forms.Control.Paint> événement.  
  
## <a name="see-also"></a>Voir aussi

- [Événements](../../../standard/events/index.md)
- [Rendu d'un contrôle Windows Forms](rendering-a-windows-forms-control.md)
- [Définition d’un événement](defining-an-event-in-windows-forms-controls.md)
