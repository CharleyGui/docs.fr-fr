---
title: 'Procédure : imprimer dans Windows Forms à l’aide de l’aperçu avant impression'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
ms.openlocfilehash: d803c9bec180f45c80e362af49c8eaa12bb9d985
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592957"
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a><span data-ttu-id="c7afd-102">Procédure : imprimer dans Windows Forms à l’aide de l’aperçu avant impression</span><span class="sxs-lookup"><span data-stu-id="c7afd-102">How to: Print in Windows Forms Using Print Preview</span></span>
<span data-ttu-id="c7afd-103">Il est très courant, dans la programmation Windows Forms, d'offrir un aperçu avant impression en plus des services d'impression.</span><span class="sxs-lookup"><span data-stu-id="c7afd-103">It is very common in Windows Forms programming to offer print preview in addition to printing services.</span></span> <span data-ttu-id="c7afd-104">L'un des moyens les plus simples pour ajouter des services d'aperçu avant impression à votre application consiste à utiliser un contrôle <xref:System.Windows.Forms.PrintPreviewDialog> avec la logique de gestion d'événements <xref:System.Drawing.Printing.PrintDocument.PrintPage> pour l'impression d'un fichier.</span><span class="sxs-lookup"><span data-stu-id="c7afd-104">An easy way to add print preview services to your application is to use a <xref:System.Windows.Forms.PrintPreviewDialog> control in combination with the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event-handling logic for printing a file.</span></span>  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a><span data-ttu-id="c7afd-105">Pour afficher un aperçu d'un document texte avec un contrôle PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="c7afd-105">To preview a text document with a PrintPreviewDialog control</span></span>  
  
1. <span data-ttu-id="c7afd-106">Ajoutez un <xref:System.Windows.Forms.PrintPreviewDialog>, un <xref:System.Drawing.Printing.PrintDocument>et deux chaînes à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="c7afd-106">Add a <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>, and two strings to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2. <span data-ttu-id="c7afd-107">Affectez comme valeur de la propriété <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> le document que vous souhaitez imprimer, puis ouvrez et lisez le contenu du document dans la chaîne que vous avez ajoutée précédemment.</span><span class="sxs-lookup"><span data-stu-id="c7afd-107">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the document's contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3. <span data-ttu-id="c7afd-108">Comme vous le feriez pour imprimer le document, dans le gestionnaire d'événements <xref:System.Drawing.Printing.PrintDocument.PrintPage> , utilisez la propriété <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> de la classe <xref:System.Drawing.Printing.PrintPageEventArgs> et le contenu du fichier pour calculer les lignes par page et restituer le contenu du document.</span><span class="sxs-lookup"><span data-stu-id="c7afd-108">As you would for printing the document, in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the file contents to calculate lines per page and render the document's contents.</span></span> <span data-ttu-id="c7afd-109">Après chaque dessin de page, vérifiez s'il s'agit de la dernière page et définissez la propriété <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> de <xref:System.Drawing.Printing.PrintPageEventArgs> en conséquence.</span><span class="sxs-lookup"><span data-stu-id="c7afd-109">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="c7afd-110">L'événement <xref:System.Drawing.Printing.PrintDocument.PrintPage> est déclenché jusqu'à ce que <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> soit `false`.</span><span class="sxs-lookup"><span data-stu-id="c7afd-110">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="c7afd-111">Une fois le rendu du document terminé, réinitialisez la chaîne à restituer.</span><span class="sxs-lookup"><span data-stu-id="c7afd-111">When the document has finished rendering, reset the string to be rendered.</span></span> <span data-ttu-id="c7afd-112">Assurez-vous aussi que l'événement <xref:System.Drawing.Printing.PrintDocument.PrintPage> est associé à sa méthode de gestion d'événements.</span><span class="sxs-lookup"><span data-stu-id="c7afd-112">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c7afd-113">Vous avez peut-être déjà effectué les étapes 2 et 3 si vous avez implémenté l'impression dans votre application.</span><span class="sxs-lookup"><span data-stu-id="c7afd-113">You may have already completed steps 2 and 3 if you have implemented printing in your application.</span></span>  
  
     <span data-ttu-id="c7afd-114">Dans l'exemple de code suivant, le gestionnaire d'événements est utilisé pour imprimer le fichier « testPage.txt » avec la même police que celle utilisée sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="c7afd-114">In the following code example, the event handler is used to print the "testPage.txt" file in the same font used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4. <span data-ttu-id="c7afd-115">Affectez comme valeur de la propriété <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> du contrôle <xref:System.Windows.Forms.PrintPreviewDialog> le composant <xref:System.Drawing.Printing.PrintDocument> sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="c7afd-115">Set the <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintPreviewDialog> control to the <xref:System.Drawing.Printing.PrintDocument> component on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5. <span data-ttu-id="c7afd-116">Appelez la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> sur le contrôle <xref:System.Windows.Forms.PrintPreviewDialog> .</span><span class="sxs-lookup"><span data-stu-id="c7afd-116">Call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method on the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="c7afd-117">Vous appelez généralement <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> à partir de la méthode de gestion d'événements <xref:System.Windows.Forms.Control.Click> d'un bouton.</span><span class="sxs-lookup"><span data-stu-id="c7afd-117">You would typically call <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> from the <xref:System.Windows.Forms.Control.Click> event-handling method of a button.</span></span> <span data-ttu-id="c7afd-118">L'appel de <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> déclenche l'événement <xref:System.Drawing.Printing.PrintDocument.PrintPage> et affiche la sortie du contrôle <xref:System.Windows.Forms.PrintPreviewDialog> .</span><span class="sxs-lookup"><span data-stu-id="c7afd-118">Calling <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> raises the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event and renders the output to the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="c7afd-119">Quand l'utilisateur clique sur l'icône d'impression dans la boîte de dialogue, l'événement <xref:System.Drawing.Printing.PrintDocument.PrintPage> est redéclenché et envoie la sortie vers l'imprimante plutôt que vers la boîte de dialogue d'aperçu.</span><span class="sxs-lookup"><span data-stu-id="c7afd-119">When the user clicks the print icon on the dialog, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised again, sending the output to the printer instead of the preview dialog.</span></span> <span data-ttu-id="c7afd-120">C'est pourquoi la chaîne est réinitialisée à la fin du processus de rendu à l'étape 3.</span><span class="sxs-lookup"><span data-stu-id="c7afd-120">This is why the string is reset at the end of the rendering process in step 3.</span></span>  
  
     <span data-ttu-id="c7afd-121">L'exemple de code suivant montre la méthode de gestion d'événements <xref:System.Windows.Forms.Control.Click> pour un bouton sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="c7afd-121">The following code example shows the <xref:System.Windows.Forms.Control.Click> event-handling method for a button on the form.</span></span> <span data-ttu-id="c7afd-122">Cette méthode de gestion d'événements appelle les méthodes pour lire le document et afficher la boîte de dialogue Aperçu avant impression.</span><span class="sxs-lookup"><span data-stu-id="c7afd-122">This event-handling method calls the methods to read the document and show the print preview dialog.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="c7afd-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="c7afd-123">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c7afd-124">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="c7afd-124">Compiling the Code</span></span>  
 <span data-ttu-id="c7afd-125">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="c7afd-125">This example requires:</span></span>  
  
- <span data-ttu-id="c7afd-126">Références aux assemblys System, System.Windows.Forms, System.Drawing.</span><span class="sxs-lookup"><span data-stu-id="c7afd-126">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7afd-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7afd-127">See also</span></span>

- [<span data-ttu-id="c7afd-128">Guide pratique pour Imprimer un fichier texte de plusieurs pages dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7afd-128">How to: Print a Multi-Page Text File in Windows Forms</span></span>](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [<span data-ttu-id="c7afd-129">Prise en charge de l’impression dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7afd-129">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
- [<span data-ttu-id="c7afd-130">Impression plus sécurisée dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7afd-130">More Secure Printing in Windows Forms</span></span>](../more-secure-printing-in-windows-forms.md)
