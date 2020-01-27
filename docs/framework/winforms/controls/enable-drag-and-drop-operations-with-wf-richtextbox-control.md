---
title: Activer les opérations de glisser-déplacer avec le contrôle RichTextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], text boxes
- drag and drop [Windows Forms], richTextBox control
- text boxes [Windows Forms], drag-and-drop operations
- RichTextBox control [Windows Forms], drag-and-drop operations
ms.assetid: ca167d1c-2014-4cf0-96a0-20598470be3b
ms.openlocfilehash: 3c17560dee012912aea2938654f1dc4dc56e0725
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745823"
---
# <a name="how-to-enable-drag-and-drop-operations-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="546d5-102">Comment : activer les opérations glisser-déplacer avec le contrôle RichTextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="546d5-102">How to: Enable Drag-and-Drop Operations with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="546d5-103">Les opérations glisser-déplacer avec le contrôle Windows Forms <xref:System.Windows.Forms.RichTextBox> s’effectuent en gérant les événements <xref:System.Windows.Forms.RichTextBox.DragEnter> et <xref:System.Windows.Forms.RichTextBox.DragDrop> .</span><span class="sxs-lookup"><span data-stu-id="546d5-103">Drag-and-drop operations with the Windows Forms <xref:System.Windows.Forms.RichTextBox> control are done by handling the <xref:System.Windows.Forms.RichTextBox.DragEnter> and <xref:System.Windows.Forms.RichTextBox.DragDrop> events.</span></span> <span data-ttu-id="546d5-104">De ce fait, ces opérations sont extrêmement simples avec le contrôle <xref:System.Windows.Forms.RichTextBox> .</span><span class="sxs-lookup"><span data-stu-id="546d5-104">Thus, drag-and-drop operations are extremely simple with the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
### <a name="to-enable-drag-operations-in-a-richtextbox-control"></a><span data-ttu-id="546d5-105">Pour permettre les opérations glisser dans un contrôle RichTextBox</span><span class="sxs-lookup"><span data-stu-id="546d5-105">To enable drag operations in a RichTextBox control</span></span>  
  
1. <span data-ttu-id="546d5-106">Affectez à la propriété <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> du contrôle <xref:System.Windows.Forms.RichTextBox> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="546d5-106">Set the <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> property of the <xref:System.Windows.Forms.RichTextBox> control to `true`.</span></span>  
  
2. <span data-ttu-id="546d5-107">Écrivez du code dans le gestionnaire d’événements de l’événement <xref:System.Windows.Forms.RichTextBox.DragEnter> .</span><span class="sxs-lookup"><span data-stu-id="546d5-107">Write code in the event handler of the <xref:System.Windows.Forms.RichTextBox.DragEnter> event.</span></span> <span data-ttu-id="546d5-108">Utilisez une instruction `if` pour vous assurer que les données glissées sont d’un type acceptable (dans ce cas, text).</span><span class="sxs-lookup"><span data-stu-id="546d5-108">Use an `if` statement to ensure that the data being dragged is of an acceptable type (in this case, text).</span></span> <span data-ttu-id="546d5-109">La valeur de la propriété <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> peut être n’importe quelle valeur de l’énumération <xref:System.Windows.Forms.DragDropEffects> .</span><span class="sxs-lookup"><span data-stu-id="546d5-109">The <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> property can be set to any value of the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span>  
  
    ```vb  
    Private Sub RichTextBox1_DragEnter(ByVal sender As Object, _   
       ByVal e As System.Windows.Forms.DragEventArgs) _   
       Handles RichTextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
          e.Effect = DragDropEffects.Copy  
       Else  
          e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void richTextBox1_DragEnter(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))   
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    ```cpp  
    private:  
       void richTextBox1_DragEnter(System::Object ^  sender,  
          System::Windows::Forms::DragEventArgs ^  e)  
       {  
          if (e->Data->GetDataPresent(DataFormats::Text))  
             e->Effect = DragDropEffects::Copy;  
          else  
             e->Effect = DragDropEffects::None;  
       }  
    ```  
  
     <span data-ttu-id="546d5-110">(Visuel C# et visuel C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="546d5-110">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.richTextBox1.DragEnter += new  
        System.Windows.Forms.DragEventHandler  
        (this.richTextBox1_DragEnter);  
    ```  
  
    ```cpp  
    this->richTextBox1->DragEnter += gcnew  
       System::Windows::Forms::DragEventHandler  
       (this, &Form1::richTextBox1_DragEnter);  
    ```  
  
3. <span data-ttu-id="546d5-111">Écrivez du code pour gérer l’événement <xref:System.Windows.Forms.RichTextBox.DragDrop> .</span><span class="sxs-lookup"><span data-stu-id="546d5-111">Write code to handle the <xref:System.Windows.Forms.RichTextBox.DragDrop> event.</span></span> <span data-ttu-id="546d5-112">Utilisez la méthode <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> pour récupérer les données glissées.</span><span class="sxs-lookup"><span data-stu-id="546d5-112">Use the <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> method to retrieve the data being dragged.</span></span>  
  
     <span data-ttu-id="546d5-113">Dans l’exemple ci-dessous, le code définit la propriété <xref:System.Windows.Forms.RichTextBox.Text%2A> du contrôle <xref:System.Windows.Forms.RichTextBox> comme étant égale aux données glissées.</span><span class="sxs-lookup"><span data-stu-id="546d5-113">In the example below, the code sets the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control equal to the data being dragged.</span></span> <span data-ttu-id="546d5-114">Si le contrôle <xref:System.Windows.Forms.RichTextBox> contient déjà du texte, le texte glissé est inséré au point d’insertion.</span><span class="sxs-lookup"><span data-stu-id="546d5-114">If there is already text in the <xref:System.Windows.Forms.RichTextBox> control, the dragged text is inserted at the insertion point.</span></span>  
  
    ```vb  
    Private Sub RichTextBox1_DragDrop(ByVal sender As Object, _   
       ByVal e As System.Windows.Forms.DragEventArgs) _   
       Handles RichTextBox1.DragDrop  
       Dim i As Int16   
       Dim s As String  
  
       ' Get start position to drop the text.  
       i = RichTextBox1.SelectionStart  
       s = RichTextBox1.Text.Substring(i)  
       RichTextBox1.Text = RichTextBox1.Text.Substring(0, i)  
  
       ' Drop the text on to the RichTextBox.  
       RichTextBox1.Text = RichTextBox1.Text + _  
          e.Data.GetData(DataFormats.Text).ToString()  
       RichTextBox1.Text = RichTextBox1.Text + s  
    End Sub  
    ```  
  
    ```csharp  
    private void richTextBox1_DragDrop(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       int i;  
       String s;  
  
       // Get start position to drop the text.  
       i = richTextBox1.SelectionStart;  
       s = richTextBox1.Text.Substring(i);  
       richTextBox1.Text = richTextBox1.Text.Substring(0,i);  
  
       // Drop the text on to the RichTextBox.  
       richTextBox1.Text = richTextBox1.Text +   
          e.Data.GetData(DataFormats.Text).ToString();  
       richTextBox1.Text = richTextBox1.Text + s;  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void richTextBox1_DragDrop(System::Object ^  sender,  
          System::Windows::Forms::DragEventArgs ^  e)  
       {  
          int i;  
          String ^s;  
  
       // Get start position to drop the text.  
       i = richTextBox1->SelectionStart;  
       s = richTextBox1->Text->Substring(i);  
       richTextBox1->Text = richTextBox1->Text->Substring(0,i);  
  
       // Drop the text on to the RichTextBox.  
       String ^str = String::Concat(richTextBox1->Text, e->Data  
       ->GetData(DataFormats->Text)->ToString());   
       richTextBox1->Text = String::Concat(str, s);  
       }  
    ```  
  
     <span data-ttu-id="546d5-115">(Visuel C# et visuel C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="546d5-115">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.richTextBox1.DragDrop += new  
        System.Windows.Forms.DragEventHandler  
        (this.richTextBox1_DragDrop);  
    ```  
  
    ```cpp  
    this->richTextBox1->DragDrop += gcnew   
       System::Windows::Forms::DragEventHandler  
       (this, &Form1::richTextBox1_DragDrop);  
    ```  
  
### <a name="to-test-the-drag-and-drop-functionality-in-your-application"></a><span data-ttu-id="546d5-116">Pour tester la fonctionnalité de glisser-déplacer dans votre application</span><span class="sxs-lookup"><span data-stu-id="546d5-116">To test the drag-and-drop functionality in your application</span></span>  
  
1. <span data-ttu-id="546d5-117">Enregistrez et générez votre application.</span><span class="sxs-lookup"><span data-stu-id="546d5-117">Save and build your application.</span></span> <span data-ttu-id="546d5-118">Pendant son exécution, exécutez WordPad.</span><span class="sxs-lookup"><span data-stu-id="546d5-118">While it is running, run WordPad.</span></span>  
  
     <span data-ttu-id="546d5-119">WordPad est un éditeur de texte installé par Windows qui permet les opérations de glisser-déplacer.</span><span class="sxs-lookup"><span data-stu-id="546d5-119">WordPad is a text editor installed by Windows that allows drag-and-drop operations.</span></span> <span data-ttu-id="546d5-120">Pour y accéder, cliquez sur le bouton **Démarrer** , sélectionnez **Exécuter**, tapez `WordPad` dans la zone de texte de la boîte de dialogue **Exécuter** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="546d5-120">It is accessible by clicking the **Start** button, selecting **Run**, typing `WordPad` in the text box of the **Run** dialog box, and then clicking **OK**.</span></span>  
  
2. <span data-ttu-id="546d5-121">Une fois que WordPad est ouvert, tapez-y une chaîne de texte.</span><span class="sxs-lookup"><span data-stu-id="546d5-121">Once WordPad is open, type a string of text in it.</span></span> <span data-ttu-id="546d5-122">À l’aide de la souris, sélectionnez le texte, puis faites-le glisser sur le contrôle <xref:System.Windows.Forms.RichTextBox> dans votre application Windows.</span><span class="sxs-lookup"><span data-stu-id="546d5-122">Using the mouse, select the text, and then drag the selected text over to the <xref:System.Windows.Forms.RichTextBox> control in your Windows application.</span></span>  
  
     <span data-ttu-id="546d5-123">Notez que quand vous pointez la souris sur le contrôle <xref:System.Windows.Forms.RichTextBox> (et que donc vous déclenchez l’événement <xref:System.Windows.Forms.RichTextBox.DragEnter> ), le pointeur de la souris se transforme et vous pouvez déposer le texte sélectionné dans le contrôle <xref:System.Windows.Forms.RichTextBox> .</span><span class="sxs-lookup"><span data-stu-id="546d5-123">Notice that when you point the mouse at the <xref:System.Windows.Forms.RichTextBox> control (and, consequently, raise the <xref:System.Windows.Forms.RichTextBox.DragEnter> event), the mouse pointer changes and you can drop the selected text into the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
     <span data-ttu-id="546d5-124">Quand vous relâchez le bouton de la souris, le texte sélectionné est déposé (autrement dit, l’événement <xref:System.Windows.Forms.RichTextBox.DragDrop> est déclenché) et inséré dans le contrôle <xref:System.Windows.Forms.RichTextBox> .</span><span class="sxs-lookup"><span data-stu-id="546d5-124">When you release the mouse button, the selected text is dropped (that is, the <xref:System.Windows.Forms.RichTextBox.DragDrop> event is raised) and is inserted within the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="546d5-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="546d5-125">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="546d5-126">Guide pratique pour exécuter des opérations de glisser-déposer entre des applications</span><span class="sxs-lookup"><span data-stu-id="546d5-126">How to: Perform Drag-and-Drop Operations Between Applications</span></span>](../advanced/how-to-perform-drag-and-drop-operations-between-applications.md)
- [<span data-ttu-id="546d5-127">RichTextBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="546d5-127">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="546d5-128">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="546d5-128">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
