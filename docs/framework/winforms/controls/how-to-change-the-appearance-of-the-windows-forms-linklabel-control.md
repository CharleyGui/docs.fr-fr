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
ms.openlocfilehash: df66991289373a05fc7c27b7768a96643e3bbae0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142128"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a>Comment : modifier l'apparence du contrôle LinkLabel Windows Forms
Vous pouvez modifier le <xref:System.Windows.Forms.LinkLabel> texte affiché par le contrôle en fonction d’une variété de buts. Par exemple, il est courant d’indiquer à l’utilisateur que le texte peut être cliqué en définissant le texte pour apparaître dans une couleur spécifique avec un soulignement. Après que l’utilisateur clique sur le texte, la couleur change à une couleur différente. Pour contrôler ce comportement, vous pouvez <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>définir <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>cinq <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>propriétés différentes: le , , , et les <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> propriétés.  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a>Pour changer l’apparence d’un contrôle LinkLabel  
  
1. Définissez <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> les couleurs que vous voulez et les propriétés.  
  
     Cela peut être fait soit programmatiquement ou au moment de la conception dans la fenêtre **Propriétés.**  
  
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
  
2. Définissez <xref:System.Windows.Forms.LinkLabel.Text%2A> la propriété à une légende appropriée.  
  
     Cela peut être fait soit programmatiquement ou au moment de la conception dans la fenêtre **Propriétés.**  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3. Définissez <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> la propriété pour déterminer quelle partie de la légende sera indiquée comme lien.  
  
     La <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> valeur est représentée <xref:System.Windows.Forms.LinkArea> avec un contenant deux numéros, la position de caractère de départ et le nombre de caractères. Cela peut être fait soit programmatiquement ou au moment de la conception dans la fenêtre **Propriétés.**  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4. Réglez <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> la propriété à <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, ou <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.  
  
     Si elle est <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>configurée à , <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> la partie de la légende déterminée par ne sera soulignée que lorsque le pointeur repose sur elle.  
  
5. Dans <xref:System.Windows.Forms.LinkLabel.LinkClicked> le gestionnaire d’événement, définissez la <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> propriété à `true`.  
  
     Quand un lien a été visité, il est courant de changer son apparence d’une certaine manière, généralement par couleur. Le texte va changer à <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> la couleur spécifiée par la propriété.  
  
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
- [Vue d’ensemble du contrôle LinkLabel](linklabel-control-overview-windows-forms.md)
- [Guide pratique pour créer un lien vers un objet ou une page web à l’aide du contrôle LinkLabel Windows Forms](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [LinkLabel, contrôle](linklabel-control-windows-forms.md)
