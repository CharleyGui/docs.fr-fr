---
title: Sélectionner du texte dans le contrôle TextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], selecting text programmatically
- text boxes [Windows Forms], selecting text programmatically
- text [Windows Forms], selecting in text boxes programmatically
ms.assetid: 8c591546-6a01-45c7-8e03-f78431f903b1
ms.openlocfilehash: 8a32e40f14ddae6f8ddcaa6d62337329df6fde26
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745317"
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a><span data-ttu-id="66403-102">Comment : sélectionner du texte dans le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="66403-102">How to: Select Text in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="66403-103">Vous pouvez sélectionner du texte par programmation dans le contrôle Windows Forms <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="66403-103">You can select text programmatically in the Windows Forms <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="66403-104">Par exemple, si vous créez une fonction qui recherche du texte pour une chaîne particulière, vous pouvez sélectionner le texte pour alerter visuellement le lecteur de la position de la chaîne trouvée.</span><span class="sxs-lookup"><span data-stu-id="66403-104">For example, if you create a function that searches text for a particular string, you can select the text to visually alert the reader of the found string's position.</span></span>  
  
### <a name="to-select-text-programmatically"></a><span data-ttu-id="66403-105">Pour sélectionner du texte par programmation</span><span class="sxs-lookup"><span data-stu-id="66403-105">To select text programmatically</span></span>  
  
1. <span data-ttu-id="66403-106">Définissez la propriété <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> au début du texte que vous souhaitez sélectionner.</span><span class="sxs-lookup"><span data-stu-id="66403-106">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property to the beginning of the text you want to select.</span></span>  
  
     <span data-ttu-id="66403-107">La propriété <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> est un nombre qui indique le point d’insertion dans la chaîne de texte, 0 étant la position la plus à gauche.</span><span class="sxs-lookup"><span data-stu-id="66403-107">The <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property is a number that indicates the insertion point within the string of text, with 0 being the left-most position.</span></span> <span data-ttu-id="66403-108">Si la propriété <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> est définie sur une valeur supérieure ou égale au nombre de caractères dans la zone de texte, le point d’insertion est placé après le dernier caractère.</span><span class="sxs-lookup"><span data-stu-id="66403-108">If the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property is set to a value equal to or greater than the number of characters in the text box, the insertion point is placed after the last character.</span></span>  
  
2. <span data-ttu-id="66403-109">Affectez à la propriété <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> la longueur du texte que vous souhaitez sélectionner.</span><span class="sxs-lookup"><span data-stu-id="66403-109">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property to the length of the text you want to select.</span></span>  
  
     <span data-ttu-id="66403-110">La propriété <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> est une valeur numérique qui définit la largeur du point d’insertion.</span><span class="sxs-lookup"><span data-stu-id="66403-110">The <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property is a numeric value that sets the width of the insertion point.</span></span> <span data-ttu-id="66403-111">La définition de la <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> sur un nombre supérieur à 0 provoque la sélection de ce nombre de caractères, en commençant par le point d’insertion actuel.</span><span class="sxs-lookup"><span data-stu-id="66403-111">Setting the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> to a number greater than 0 causes that number of characters to be selected, starting from the current insertion point.</span></span>  
  
3. <span data-ttu-id="66403-112">Facultatif Accédez au texte sélectionné par le biais de la propriété <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A>.</span><span class="sxs-lookup"><span data-stu-id="66403-112">(Optional) Access the selected text through the <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> property.</span></span>  
  
     <span data-ttu-id="66403-113">Le code ci-dessous sélectionne le contenu d’une zone de texte lorsque l’événement <xref:System.Windows.Forms.Control.Enter> du contrôle se produit.</span><span class="sxs-lookup"><span data-stu-id="66403-113">The code below selects the contents of a text box when the control's <xref:System.Windows.Forms.Control.Enter> event occurs.</span></span> <span data-ttu-id="66403-114">Cet exemple vérifie si la zone de texte a une valeur pour la propriété <xref:System.Windows.Forms.TextBox.Text%2A> qui n’est pas `null` ou une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="66403-114">This example checks if the text box has a value for the <xref:System.Windows.Forms.TextBox.Text%2A> property that is not `null` or an empty string.</span></span> <span data-ttu-id="66403-115">Lorsque la zone de texte reçoit le focus, le texte actuel de la zone de texte est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="66403-115">When the text box receives the focus, the current text in the text box is selected.</span></span> <span data-ttu-id="66403-116">Le gestionnaire d’événements `TextBox1_Enter` doit être lié au contrôle ; Pour plus d’informations, consultez [Comment : créer des gestionnaires d’événements au moment de l’exécution pour Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="66403-116">The `TextBox1_Enter` event handler must be bound to the control; for more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
     <span data-ttu-id="66403-117">Pour tester cet exemple, appuyez sur la touche Tab jusqu’à ce que la zone de texte ait le focus.</span><span class="sxs-lookup"><span data-stu-id="66403-117">To test this example, press the Tab key until the text box has the focus.</span></span> <span data-ttu-id="66403-118">Si vous cliquez dans la zone de texte, le texte est désélectionné.</span><span class="sxs-lookup"><span data-stu-id="66403-118">If you click in the text box, the text is unselected.</span></span>  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       If (Not String.IsNullOrEmpty(TextBox1.Text)) Then  
          TextBox1.SelectionStart = 0  
          TextBox1.SelectionLength = TextBox1.Text.Length  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(object sender, System.EventArgs e){  
       if (!String.IsNullOrEmpty(textBox1.Text))  
       {  
          textBox1.SelectionStart = 0;  
          textBox1.SelectionLength = textBox1.Text.Length;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^ sender,  
          System::EventArgs ^ e) {  
       if (!System::String::IsNullOrEmpty(textBox1->Text))  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = textBox1->Text->Length;  
       }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="66403-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66403-119">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="66403-120">Vue d’ensemble du contrôle TextBox</span><span class="sxs-lookup"><span data-stu-id="66403-120">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="66403-121">Guide pratique pour contrôler le point d’insertion dans un contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="66403-121">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="66403-122">Guide pratique pour créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="66403-122">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="66403-123">Guide pratique pour créer une zone de texte en lecture seule</span><span class="sxs-lookup"><span data-stu-id="66403-123">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="66403-124">Guide pratique pour insérer des guillemets dans une chaîne</span><span class="sxs-lookup"><span data-stu-id="66403-124">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="66403-125">Guide pratique pour afficher des lignes multiples dans le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="66403-125">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="66403-126">TextBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="66403-126">TextBox Control</span></span>](textbox-control-windows-forms.md)
