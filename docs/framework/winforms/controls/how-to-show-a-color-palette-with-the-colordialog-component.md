---
title: "Comment : afficher une palette de couleurs à l'aide du composant ColorDialog"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- palettes [Windows Forms], showing color
- color dialog box [Windows Forms], showing color palettes
- colors [Windows Forms], allowing users to select
- color palettes [Windows Forms], dialog box
- ColorDialog component [Windows Forms], showing color palettes
- color palettes [Windows Forms], showing in ColorDialog component
- colors [Windows Forms], showing palettes
ms.assetid: ee050f61-dbc8-4436-ba22-51360981ab48
ms.openlocfilehash: 0406ef7a32678bd149c0024348a7adf1f0b72926
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141781"
---
# <a name="how-to-show-a-color-palette-with-the-colordialog-component"></a><span data-ttu-id="f1118-102">Comment : afficher une palette de couleurs à l'aide du composant ColorDialog</span><span class="sxs-lookup"><span data-stu-id="f1118-102">How to: Show a Color Palette with the ColorDialog Component</span></span>
<span data-ttu-id="f1118-103">Le composant [ColorDialog](colordialog-component-windows-forms.md) affiche une palette de couleurs et renvoie une propriété contenant la couleur choisie par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f1118-103">The [ColorDialog](colordialog-component-windows-forms.md) component displays a palette of colors and returns a property containing the color the user has selected.</span></span>  
  
### <a name="to-choose-a-color-using-the-colordialog-component"></a><span data-ttu-id="f1118-104">Pour choisir une couleur à l’aide du composant ColorDialog</span><span class="sxs-lookup"><span data-stu-id="f1118-104">To choose a color using the ColorDialog component</span></span>  
  
1. <span data-ttu-id="f1118-105">Affichez la boîte <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> de dialogue à l’aide de la méthode.</span><span class="sxs-lookup"><span data-stu-id="f1118-105">Display the dialog box using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
2. <span data-ttu-id="f1118-106">Utilisez <xref:System.Windows.Forms.DialogResult> la propriété pour déterminer comment la boîte de dialogue a été fermée.</span><span class="sxs-lookup"><span data-stu-id="f1118-106">Use the <xref:System.Windows.Forms.DialogResult> property to determine how the dialog box was closed.</span></span>  
  
3. <span data-ttu-id="f1118-107">Utilisez <xref:System.Windows.Forms.ColorDialog.Color%2A> la propriété <xref:System.Windows.Forms.ColorDialog> du composant pour définir la couleur choisie.</span><span class="sxs-lookup"><span data-stu-id="f1118-107">Use the <xref:System.Windows.Forms.ColorDialog.Color%2A> property of the <xref:System.Windows.Forms.ColorDialog> component to set the chosen color.</span></span>  
  
     <span data-ttu-id="f1118-108">Dans l’exemple <xref:System.Windows.Forms.Button> ci-dessous, le gestionnaire d’événements du <xref:System.Windows.Forms.Control.Click> contrôle ouvre un <xref:System.Windows.Forms.ColorDialog> composant.</span><span class="sxs-lookup"><span data-stu-id="f1118-108">In the example below, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens a <xref:System.Windows.Forms.ColorDialog> component.</span></span> <span data-ttu-id="f1118-109">Lorsqu’une couleur est choisie et que <xref:System.Windows.Forms.Button> l’utilisateur clique **sur OK,** la couleur de fond du contrôle est réglée sur la couleur choisie.</span><span class="sxs-lookup"><span data-stu-id="f1118-109">When a color is chosen and the user clicks **OK**, the <xref:System.Windows.Forms.Button> control's background color is set to the chosen color.</span></span> <span data-ttu-id="f1118-110">L’exemple suppose que <xref:System.Windows.Forms.Button> votre formulaire <xref:System.Windows.Forms.ColorDialog> a un contrôle et un composant.</span><span class="sxs-lookup"><span data-stu-id="f1118-110">The example assumes your form has a <xref:System.Windows.Forms.Button> control and a <xref:System.Windows.Forms.ColorDialog> component.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       If ColorDialog1.ShowDialog() = DialogResult.OK Then  
          Button1.BackColor = ColorDialog1.Color  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(colorDialog1.ShowDialog() == DialogResult.OK)  
       {  
          button1.BackColor = colorDialog1.Color;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,
          System::EventArgs ^ e)  
       {  
          if(colorDialog1->ShowDialog() == DialogResult::OK)  
          {  
             button1->BackColor = colorDialog1->Color;  
          }  
       }  
    ```  
  
     <span data-ttu-id="f1118-111">(Visual C, Visual CMMD) Placez le code suivant dans le constructeur du formulaire pour enregistrer le gestionnaire de l’événement.</span><span class="sxs-lookup"><span data-stu-id="f1118-111">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f1118-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1118-112">See also</span></span>

- <xref:System.Windows.Forms.ColorDialog>
- [<span data-ttu-id="f1118-113">ColorDialog, composant</span><span class="sxs-lookup"><span data-stu-id="f1118-113">ColorDialog Component</span></span>](colordialog-component-windows-forms.md)
