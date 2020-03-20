---
title: Contrôles constitutifs
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], constituent controls
- constituent controls [Windows Forms]
- user controls [Windows Forms], constituent controls
ms.assetid: 5565e720-198b-4bbd-a2bd-c447ba641798
ms.openlocfilehash: 2865a3d85bd56151038ee90c18d199d3a584b5d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182413"
---
# <a name="constituent-controls"></a>Contrôles constitutifs
Les contrôles qui composent un contrôle utilisateur, appelés *contrôles constitutifs*, sont relativement peu flexibles en matière de rendu graphique personnalisé. Tous les contrôles Windows Forms gèrent <xref:System.Windows.Forms.Control.OnPaint%2A> leur propre rendu à travers leur propre méthode. Comme cette méthode est protégée, elle n’est pas accessible au développeur et il n’est pas possible d’empêcher son exécution quand le contrôle est dessiné. Cela ne signifie pas pour autant que vous ne pouvez pas ajouter du code pour modifier l’apparence des contrôles constitutifs. Un rendu supplémentaire est possible en ajoutant un gestionnaire d’événements. Par exemple, supposons que <xref:System.Windows.Forms.UserControl> vous étiez `MyButton`l’auteur d’un bouton nommé . Si vous souhaitez avoir un rendu supplémentaire <xref:System.Web.UI.WebControls.Button>au-delà de ce qui a été fourni par le , vous ajouteriez du code à votre contrôle utilisateur similaire à ce qui suit:  
  
```vb  
Public Sub MyPaint(ByVal sender as Object, e as PaintEventArgs) Handles _  
   MyButton.Paint  
   'Additional rendering code goes here  
End Sub  
```  
  
```csharp  
// Add the event handler to the button's Paint event.  
MyButton.Paint +=
   new System.Windows.Forms.PaintEventHandler (this.MyPaint);  
// Create the custom painting method.  
protected void MyPaint (object sender,
System.Windows.Forms.PaintEventArgs e)  
{  
   // Additional rendering code goes here.  
}  
```  
  
> [!NOTE]
> Certains contrôles de formulaires Windows, tels que <xref:System.Windows.Forms.TextBox>, sont peints directement par Windows. Dans ces cas, la méthode n’est <xref:System.Windows.Forms.Control.OnPaint%2A> jamais appelée, et donc l’exemple ci-dessus ne sera jamais appelé.  
  
 Ceci crée une méthode qui s’exécute chaque fois que l’événement `MyButton.Paint` s’exécute, ce qui ajoute une représentation graphique supplémentaire à votre contrôle. Notez que ceci n’empêche pas l’exécution de `MyButton.OnPaint`, et tout le dessin généralement effectué par un bouton est donc exécuté en plus de votre dessin personnalisé. Pour plus d’informations sur la technologie GDI+ et le rendu personnalisé, consultez [Création d’images graphiques avec GDI+](../advanced/how-to-create-graphics-objects-for-drawing.md). Si vous voulez avoir une représentation unique de votre contrôle, le mieux est de créer un contrôle hérité et d’écrire pour celui-ci du code de rendu personnalisé. Pour plus d’informations, consultez [Contrôles dessinés par l’utilisateur](user-drawn-controls.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Contrôles dessinés par l’utilisateur](user-drawn-controls.md)
- [Comment : créer des objets graphiques pour le dessin](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [Variétés de contrôles personnalisés](varieties-of-custom-controls.md)
