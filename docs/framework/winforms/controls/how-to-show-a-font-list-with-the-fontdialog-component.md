---
title: 'Procédure : afficher la liste des polices avec le composant FontDialog'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- fonts [Windows Forms], showing list
- FontDialog component [Windows Forms]
- fonts [Windows Forms], attributes
- Font property [Windows Forms], setting with FontDialog component
- Font dialog box [Windows Forms], displaying
- fonts [Windows Forms], selecting
ms.assetid: 35692c1b-0937-4b7a-9207-1ae6bdc244a0
ms.openlocfilehash: 05e9b5e1280d0318354b0d47f4d78f7ec1c5f4e7
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053449"
---
# <a name="how-to-show-a-font-list-with-the-fontdialog-component"></a><span data-ttu-id="84ff1-102">Procédure : afficher la liste des polices avec le composant FontDialog</span><span class="sxs-lookup"><span data-stu-id="84ff1-102">How to: Show a Font List with the FontDialog Component</span></span>
<span data-ttu-id="84ff1-103">Le [FontDialog](fontdialog-component-windows-forms.md) composant permet aux utilisateurs de sélectionner une police, mais aussi modifier ses aspects de l’affichage, telles que son poids et la taille.</span><span class="sxs-lookup"><span data-stu-id="84ff1-103">The [FontDialog](fontdialog-component-windows-forms.md) component allows users to select a font, as well as change its display aspects, such as its weight and size.</span></span>  
  
 <span data-ttu-id="84ff1-104">La police sélectionnée dans la boîte de dialogue est retournée dans le <xref:System.Windows.Forms.FontDialog.Font%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="84ff1-104">The font selected in the dialog box is returned in the <xref:System.Windows.Forms.FontDialog.Font%2A> property.</span></span> <span data-ttu-id="84ff1-105">Par conséquent, en tirant parti de la police sélectionnée par l’utilisateur est aussi simple que la lecture d’une propriété.</span><span class="sxs-lookup"><span data-stu-id="84ff1-105">Thus, taking advantage of the font selected by the user is as easy as reading a property.</span></span>  
  
### <a name="to-select-font-properties-using-the-fontdialog-component"></a><span data-ttu-id="84ff1-106">Pour sélectionner les propriétés de police à l’aide du composant FontDialog</span><span class="sxs-lookup"><span data-stu-id="84ff1-106">To select font properties using the FontDialog Component</span></span>  
  
1. <span data-ttu-id="84ff1-107">Afficher la boîte de dialogue à l’aide de la <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="84ff1-107">Display the dialog box using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
2. <span data-ttu-id="84ff1-108">Utilisez le <xref:System.Windows.Forms.DialogResult> propriété afin de déterminer comment la boîte de dialogue a été fermée.</span><span class="sxs-lookup"><span data-stu-id="84ff1-108">Use the <xref:System.Windows.Forms.DialogResult> property to determine how the dialog box was closed.</span></span>  
  
3. <span data-ttu-id="84ff1-109">Utilisez le <xref:System.Windows.Forms.FontDialog.Font%2A> propriété à définir la police souhaitée.</span><span class="sxs-lookup"><span data-stu-id="84ff1-109">Use the <xref:System.Windows.Forms.FontDialog.Font%2A> property to set the desired font.</span></span>  
  
     <span data-ttu-id="84ff1-110">Dans l’exemple ci-dessous, le <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements ouvre un <xref:System.Windows.Forms.FontDialog> composant.</span><span class="sxs-lookup"><span data-stu-id="84ff1-110">In the example below, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens a <xref:System.Windows.Forms.FontDialog> component.</span></span> <span data-ttu-id="84ff1-111">Quand une police est sélectionné et l’utilisateur clique sur **OK**, le <xref:System.Windows.Forms.FontDialog.Font%2A> propriété d’un <xref:System.Windows.Forms.TextBox> contrôle qui se trouve sur le formulaire est défini sur la police choisie.</span><span class="sxs-lookup"><span data-stu-id="84ff1-111">When a font is chosen and the user clicks **OK**, the <xref:System.Windows.Forms.FontDialog.Font%2A> property of a <xref:System.Windows.Forms.TextBox> control that is on the form is set to the chosen font.</span></span> <span data-ttu-id="84ff1-112">L’exemple suppose que votre formulaire contient un <xref:System.Windows.Forms.Button> contrôle, un <xref:System.Windows.Forms.TextBox> contrôle et un <xref:System.Windows.Forms.FontDialog> composant.</span><span class="sxs-lookup"><span data-stu-id="84ff1-112">The example assumes your form has a <xref:System.Windows.Forms.Button> control, a  <xref:System.Windows.Forms.TextBox> control, and a <xref:System.Windows.Forms.FontDialog> component.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       If FontDialog1.ShowDialog() = DialogResult.OK Then  
          TextBox1.Font = FontDialog1.Font  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(fontDialog1.ShowDialog() == DialogResult.OK)  
       {  
          textBox1.Font = fontDialog1.Font;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if(fontDialog1->ShowDialog() == DialogResult::OK)  
          {  
             textBox1->Font = fontDialog1->Font;  
          }  
       }  
    ```  
  
     <span data-ttu-id="84ff1-113">(Visual C# et Visual C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="84ff1-113">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="84ff1-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84ff1-114">See also</span></span>

- <xref:System.Windows.Forms.FontDialog>
- [<span data-ttu-id="84ff1-115">FontDialog, composant</span><span class="sxs-lookup"><span data-stu-id="84ff1-115">FontDialog Component</span></span>](fontdialog-component-windows-forms.md)
