---
title: Modifier l’apparence du contrôle LinkLabel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- LinkLabel properties
- LinkLabel control [Windows Forms], changing appearance of links
- links [Windows Forms], changing appearance
- examples [Windows Forms], LinkLabel control
- LinkLabel control [Windows Forms], examples
ms.assetid: fdc5854f-5162-4457-8cbe-1042feb2d132
ms.openlocfilehash: 0b38722fb1647ea215c3bb8978dd3f54b300a0e0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746620"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a>Comment : modifier l'apparence du contrôle LinkLabel Windows Forms
Vous pouvez modifier le texte affiché par le contrôle <xref:System.Windows.Forms.LinkLabel> pour l’adapter à différentes fins. Par exemple, il est courant d’indiquer à l’utilisateur que le texte peut être cliqué en définissant le texte de façon à ce qu’il s’affiche dans une couleur spécifique avec un soulignement. Une fois que l’utilisateur a cliqué sur le texte, la couleur est remplacée par une couleur différente. Pour contrôler ce comportement, vous pouvez définir cinq propriétés différentes : les propriétés <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>et <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>.  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a>Pour modifier l’apparence d’un contrôle LinkLabel  
  
1. Définissez les propriétés <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> et <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> sur les couleurs de votre choix.  
  
     Vous pouvez effectuer cette opération soit par programmation, soit au moment de la conception dans la fenêtre **Propriétés** .  
  
    ```vb  
    ' You can set the color using decimal values for red, green, and blue  
    LinkLabel1.LinkColor = Color.FromArgb(0, 0, 255)  
    ' Or you can set the color using defined constants  
    LinkLabel1.VisitedLinkColor = Color.Purple  
    ```  
  
    ```csharp  
    // You can set the color using decimal values for red, green, and blue  
    linkLabel1.LinkColor = Color.FromArgb(0, 0, 255);  
    // Or you can set the color using defined constants  
    linkLabel1.VisitedLinkColor = Color.Purple;  
    ```  
  
    ```cpp  
    // You can set the color using decimal values for red, green, and blue  
    linkLabel1->LinkColor = Color::FromArgb(0, 0, 255);  
    // Or you can set the color using defined constants  
    linkLabel1->VisitedLinkColor = Color::Purple;  
    ```  
  
2. Affectez à la propriété <xref:System.Windows.Forms.LinkLabel.Text%2A> une légende appropriée.  
  
     Vous pouvez effectuer cette opération soit par programmation, soit au moment de la conception dans la fenêtre **Propriétés** .  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3. Définissez la propriété <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> pour déterminer la partie de la légende qui sera indiquée comme lien.  
  
     La valeur <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> est représentée par un <xref:System.Windows.Forms.LinkArea> contenant deux nombres, la position du caractère de début et le nombre de caractères. Vous pouvez effectuer cette opération soit par programmation, soit au moment de la conception dans la fenêtre **Propriétés** .  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4. Affectez à la propriété <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> la valeur <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>ou <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.  
  
     S’il est défini sur <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, la partie de la légende déterminée par <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> sera uniquement soulignée lorsque le pointeur se trouve sur celui-ci.  
  
5. Dans le gestionnaire d’événements <xref:System.Windows.Forms.LinkLabel.LinkClicked>, affectez à la propriété <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> la valeur `true`.  
  
     Lorsqu’un lien a été visité, il est courant de modifier son apparence d’une certaine manière, généralement par couleur. Le texte passe à la couleur spécifiée par la propriété <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>.  
  
    ```vb  
    Protected Sub LinkLabel1_LinkClicked (ByVal sender As Object, _  
       ByVal e As EventArgs) Handles LinkLabel1.LinkClicked  
       ' Change the color of the link text  
       ' by setting LinkVisited to True.  
       LinkLabel1.LinkVisited = True  
       ' Then do whatever other action is appropriate  
    End Sub  
    ```  
  
    ```csharp  
    protected void LinkLabel1_LinkClicked(object sender, System.EventArgs e)  
    {  
       // Change the color of the link text by setting LinkVisited   
       // to True.  
       linkLabel1.LinkVisited = true;  
       // Then do whatever other action is appropriate  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void linkLabel1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)  
       {  
          // Change the color of the link text by setting LinkVisited   
          // to True.  
          linkLabel1->LinkVisited = true;  
          // Then do whatever other action is appropriate  
       }  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>
- [Vue d'ensemble du contrôle LinkLabel](linklabel-control-overview-windows-forms.md)
- [Guide pratique pour créer un lien vers un objet ou une page web à l’aide du contrôle LinkLabel Windows Forms](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [LinkLabel, contrôle](linklabel-control-windows-forms.md)
