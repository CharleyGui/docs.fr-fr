---
title: 'Procédure : afficher l’aperçu avant impression dans des applications Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print preview [Windows Forms], displaying
- printing [Windows Forms], print preview
- examples [Windows Forms], print preview
ms.assetid: e394134c-0886-4517-bd8d-edc4a3749eb5
ms.openlocfilehash: 8252906de9a574f49617609a4cb08a1e8aa6a992
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929009"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a><span data-ttu-id="a4942-102">Procédure : afficher l’aperçu avant impression dans des applications Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a4942-102">How to: Display Print Preview in Windows Forms Applications</span></span>
<span data-ttu-id="a4942-103">Vous pouvez utiliser le <xref:System.Windows.Forms.PrintPreviewDialog> contrôle pour permettre aux utilisateurs d’afficher un document, souvent avant qu’il ne soit imprimé.</span><span class="sxs-lookup"><span data-stu-id="a4942-103">You can use the <xref:System.Windows.Forms.PrintPreviewDialog> control to enable users to display a document, often before it is to be printed.</span></span>  
  
 <span data-ttu-id="a4942-104">Pour ce faire, vous devez spécifier une instance de la <xref:System.Drawing.Printing.PrintDocument> classe; il s’agit du document à imprimer.</span><span class="sxs-lookup"><span data-stu-id="a4942-104">To do this, you need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class; this is the document to be printed.</span></span> <span data-ttu-id="a4942-105">Pour plus d’informations sur l’utilisation de l' <xref:System.Drawing.Printing.PrintDocument> aperçu avant impression [avec le composant, consultez Procédure: Imprimer en Windows Forms à l’aide](../advanced/how-to-print-in-windows-forms-using-print-preview.md)de l’aperçu avant impression.</span><span class="sxs-lookup"><span data-stu-id="a4942-105">For more information about using print preview with the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print in Windows Forms Using Print Preview](../advanced/how-to-print-in-windows-forms-using-print-preview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4942-106">Pour utiliser le <xref:System.Windows.Forms.PrintPreviewDialog> contrôle au moment de l’exécution, les utilisateurs doivent disposer d’une imprimante installée sur leur ordinateur, localement ou via un réseau, car il s' <xref:System.Windows.Forms.PrintPreviewDialog> agit en fait de la façon dont le composant détermine la façon dont un document doit être imprimé.</span><span class="sxs-lookup"><span data-stu-id="a4942-106">To use the <xref:System.Windows.Forms.PrintPreviewDialog> control at run time, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PrintPreviewDialog> component determines how a document will look when printed.</span></span>  
  
 <span data-ttu-id="a4942-107">Le <xref:System.Windows.Forms.PrintPreviewDialog> contrôle utilise la <xref:System.Drawing.Printing.PrinterSettings> classe.</span><span class="sxs-lookup"><span data-stu-id="a4942-107">The <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span> <span data-ttu-id="a4942-108">En outre, le <xref:System.Windows.Forms.PrintPreviewDialog> contrôle utilise la <xref:System.Drawing.Printing.PageSettings> classe, tout comme le <xref:System.Windows.Forms.PrintPreviewDialog> fait le composant.</span><span class="sxs-lookup"><span data-stu-id="a4942-108">Additionally, the <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PageSettings> class, just as the <xref:System.Windows.Forms.PrintPreviewDialog> component does.</span></span> <span data-ttu-id="a4942-109">Le document d’impression spécifié dans <xref:System.Windows.Forms.PrintPreviewDialog> la propriété <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> du contrôle fait référence <xref:System.Drawing.Printing.PrinterSettings> aux instances des classes <xref:System.Drawing.Printing.PageSettings> et, et celles-ci sont utilisées pour restituer le document dans la fenêtre d’aperçu.</span><span class="sxs-lookup"><span data-stu-id="a4942-109">The print document specified in the <xref:System.Windows.Forms.PrintPreviewDialog> control's <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> property refers to instances of both the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and these are used to render the document in the preview window.</span></span>  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a><span data-ttu-id="a4942-110">Pour afficher les pages à l’aide du contrôle PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="a4942-110">To view pages using the PrintPreviewDialog control</span></span>  
  
- <span data-ttu-id="a4942-111">Utilisez la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> pour afficher la boîte de dialogue, en spécifiant le <xref:System.Drawing.Printing.PrintDocument> à utiliser.</span><span class="sxs-lookup"><span data-stu-id="a4942-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="a4942-112">Dans l’exemple de code suivant, <xref:System.Windows.Forms.Button> le gestionnaire <xref:System.Windows.Forms.Control.Click> d’événements du contrôle <xref:System.Windows.Forms.PrintPreviewDialog> ouvre une instance du contrôle.</span><span class="sxs-lookup"><span data-stu-id="a4942-112">In the following code example, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="a4942-113">Le document d’impression est spécifié dans <xref:System.Windows.Forms.PrintDialog.Document%2A> la propriété.</span><span class="sxs-lookup"><span data-stu-id="a4942-113">The print document is specified in the <xref:System.Windows.Forms.PrintDialog.Document%2A> property.</span></span> <span data-ttu-id="a4942-114">Dans l’exemple ci-dessous, aucun document d’impression n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="a4942-114">In the example below, no print document is specified.</span></span>  
  
     <span data-ttu-id="a4942-115">L’exemple requiert que votre formulaire ait un <xref:System.Windows.Forms.Button> contrôle, un <xref:System.Drawing.Printing.PrintDocument> composant nommé `myDocument`et un <xref:System.Windows.Forms.PrintPreviewDialog> contrôle.</span><span class="sxs-lookup"><span data-stu-id="a4942-115">The example requires that your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       ' The print document 'myDocument' used below  
       ' is merely for an example.  
       ' You will have to specify your own print document.  
       PrintPreviewDialog1.Document = myDocument  
       PrintPreviewDialog1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // The print document 'myDocument' used below  
       // is merely for an example.  
       // You will have to specify your own print document.  
       printPreviewDialog1.Document = myDocument;  
       printPreviewDialog1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // The print document 'myDocument' used below  
          // is merely for an example.  
          // You will have to specify your own print document.  
          printPreviewDialog1->Document = myDocument;  
          printPreviewDialog1->ShowDialog();  
       }  
    ```  
  
     <span data-ttu-id="a4942-116">(Visuel C#, visuel C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="a4942-116">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a4942-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4942-117">See also</span></span>

- [<span data-ttu-id="a4942-118">Composant PrintDocument</span><span class="sxs-lookup"><span data-stu-id="a4942-118">PrintDocument Component</span></span>](printdocument-component-windows-forms.md)
- [<span data-ttu-id="a4942-119">PrintPreviewDialog, contrôle</span><span class="sxs-lookup"><span data-stu-id="a4942-119">PrintPreviewDialog Control</span></span>](printpreviewdialog-control-windows-forms.md)
- [<span data-ttu-id="a4942-120">Prise en charge de l’impression dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a4942-120">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="a4942-121">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a4942-121">Windows Forms</span></span>](../index.md)
