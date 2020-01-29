---
title: Prise en charge de l’impression
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
ms.openlocfilehash: d6e8f60db7afe2f1b04eaae6fe71aa93e5c22cae
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732494"
---
# <a name="windows-forms-print-support"></a><span data-ttu-id="70892-102">Prise en charge de l'impression dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="70892-102">Windows Forms Print Support</span></span>
<span data-ttu-id="70892-103">L’impression dans Windows Forms se compose principalement de l’utilisation du composant de [composant PrintDocument](../controls/printdocument-component-windows-forms.md) pour permettre à l’utilisateur d’imprimer, et du contrôle de [contrôle PrintPreviewDialog](../controls/printpreviewdialog-control-windows-forms.md) , du [composant PrintDialog](../controls/printdialog-component-windows-forms.md) et des composants du [composant PageSetupDialog](../controls/pagesetupdialog-component-windows-forms.md) pour fournir une interface graphique familière aux utilisateurs habitués au système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="70892-103">Printing in Windows Forms consists primarily of using the [PrintDocument Component](../controls/printdocument-component-windows-forms.md) component to enable the user to print, and the [PrintPreviewDialog Control](../controls/printpreviewdialog-control-windows-forms.md) control, [PrintDialog Component](../controls/printdialog-component-windows-forms.md) and [PageSetupDialog Component](../controls/pagesetupdialog-component-windows-forms.md) components to provide a familiar graphical interface to users accustomed to the Windows operating system.</span></span>  
  
 <span data-ttu-id="70892-104">En général, vous créez une nouvelle instance du composant <xref:System.Drawing.Printing.PrintDocument>, définissez les propriétés qui décrivent les éléments à imprimer à l’aide des classes <xref:System.Drawing.Printing.PrinterSettings> et <xref:System.Drawing.Printing.PageSettings>, puis appelez la méthode <xref:System.Drawing.Printing.PrintDocument.Print%2A> pour imprimer le document.</span><span class="sxs-lookup"><span data-stu-id="70892-104">Typically, you create a new instance of the <xref:System.Drawing.Printing.PrintDocument> component, set the properties that describe what to print using the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to actually print the document.</span></span>  
  
 <span data-ttu-id="70892-105">Au cours de l’impression à partir d’une application Windows, le composant <xref:System.Drawing.Printing.PrintDocument> affiche une boîte de dialogue annuler l’impression pour avertir les utilisateurs du fait que l’impression est en cours et pour autoriser l’annulation du travail d’impression.</span><span class="sxs-lookup"><span data-stu-id="70892-105">During the course of printing from a Windows-based application, the <xref:System.Drawing.Printing.PrintDocument> component will show an abort print dialog box to alert users to the fact that printing is occurring and to allow the print job to be canceled.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="70892-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="70892-106">In This Section</span></span>  
 [<span data-ttu-id="70892-107">Guide pratique pour créer des travaux d’impression Windows Forms standard</span><span class="sxs-lookup"><span data-stu-id="70892-107">How to: Create Standard Windows Forms Print Jobs</span></span>](how-to-create-standard-windows-forms-print-jobs.md)  
 <span data-ttu-id="70892-108">Explique comment utiliser le composant <xref:System.Drawing.Printing.PrintDocument> pour imprimer à partir d’un Windows Form.</span><span class="sxs-lookup"><span data-stu-id="70892-108">Explains how to use the <xref:System.Drawing.Printing.PrintDocument> component to print from a Windows Form.</span></span>  
  
 [<span data-ttu-id="70892-109">Guide pratique pour capturer une entrée d’utilisateur à partir d’un composant PrintDialog au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="70892-109">How to: Capture User Input from a PrintDialog at Run Time</span></span>](how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 <span data-ttu-id="70892-110">Explique comment modifier les options d’impression sélectionnées par programme à l’aide du composant <xref:System.Windows.Forms.PrintDialog>.</span><span class="sxs-lookup"><span data-stu-id="70892-110">Explains how to modify selected print options programmatically using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="70892-111">Guide pratique pour choisir les imprimantes connectées à l'ordinateur d'un utilisateur dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="70892-111">How to: Choose the Printers Attached to a User's Computer in Windows Forms</span></span>](how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 <span data-ttu-id="70892-112">Décrit la modification de l’imprimante à utiliser pour l’impression à l’aide du composant <xref:System.Windows.Forms.PrintDialog> au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="70892-112">Describes changing the printer to print to using the <xref:System.Windows.Forms.PrintDialog> component at run time.</span></span>  
  
 [<span data-ttu-id="70892-113">Comment : imprimer des graphiques dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="70892-113">How to: Print Graphics in Windows Forms</span></span>](how-to-print-graphics-in-windows-forms.md)  
 <span data-ttu-id="70892-114">Décrit l’envoi de graphiques à l’imprimante.</span><span class="sxs-lookup"><span data-stu-id="70892-114">Describes sending graphics to the printer.</span></span>  
  
 [<span data-ttu-id="70892-115">Comment : imprimer un fichier texte composé de plusieurs pages dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="70892-115">How to: Print a Multi-Page Text File in Windows Forms</span></span>](how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 <span data-ttu-id="70892-116">Décrit l’envoi de texte à l’imprimante.</span><span class="sxs-lookup"><span data-stu-id="70892-116">Describes sending text to the printer.</span></span>  
  
 [<span data-ttu-id="70892-117">Guide pratique pour terminer des travaux d'impression Windows Forms</span><span class="sxs-lookup"><span data-stu-id="70892-117">How to: Complete Windows Forms Print Jobs</span></span>](how-to-complete-windows-forms-print-jobs.md)  
 <span data-ttu-id="70892-118">Explique comment avertir les utilisateurs de l’achèvement d’un travail d’impression.</span><span class="sxs-lookup"><span data-stu-id="70892-118">Explains how to alert users to the completion of a print job.</span></span>  
  
 [<span data-ttu-id="70892-119">Guide pratique pour imprimer un Windows Form</span><span class="sxs-lookup"><span data-stu-id="70892-119">How to: Print a Windows Form</span></span>](how-to-print-a-windows-form.md)  
 <span data-ttu-id="70892-120">Montre comment imprimer une copie du formulaire actif.</span><span class="sxs-lookup"><span data-stu-id="70892-120">Shows how to print a copy of the current form.</span></span>  
  
 [<span data-ttu-id="70892-121">Guide pratique pour imprimer dans les Windows Forms en utilisant l'aperçu avant impression</span><span class="sxs-lookup"><span data-stu-id="70892-121">How to: Print in Windows Forms Using Print Preview</span></span>](how-to-print-in-windows-forms-using-print-preview.md)  
 <span data-ttu-id="70892-122">Montre comment utiliser une <xref:System.Windows.Forms.PrintPreviewDialog> pour l’impression d’un document.</span><span class="sxs-lookup"><span data-stu-id="70892-122">Shows how to use a <xref:System.Windows.Forms.PrintPreviewDialog> for printing a document.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="70892-123">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="70892-123">Related Sections</span></span>  
 [<span data-ttu-id="70892-124">Composant PrintDocument</span><span class="sxs-lookup"><span data-stu-id="70892-124">PrintDocument Component</span></span>](../controls/printdocument-component-windows-forms.md)  
 <span data-ttu-id="70892-125">Explique l’utilisation du composant <xref:System.Drawing.Printing.PrintDocument>.</span><span class="sxs-lookup"><span data-stu-id="70892-125">Explains usage of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 [<span data-ttu-id="70892-126">PrintDialog, composant</span><span class="sxs-lookup"><span data-stu-id="70892-126">PrintDialog Component</span></span>](../controls/printdialog-component-windows-forms.md)  
 <span data-ttu-id="70892-127">Explique l’utilisation du composant <xref:System.Windows.Forms.PrintDialog>.</span><span class="sxs-lookup"><span data-stu-id="70892-127">Explains usage of the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="70892-128">PrintPreviewDialog, contrôle</span><span class="sxs-lookup"><span data-stu-id="70892-128">PrintPreviewDialog Control</span></span>](../controls/printpreviewdialog-control-windows-forms.md)  
 <span data-ttu-id="70892-129">Explique l’utilisation du contrôle <xref:System.Windows.Forms.PrintPreviewDialog>.</span><span class="sxs-lookup"><span data-stu-id="70892-129">Explains usage of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
 [<span data-ttu-id="70892-130">PageSetupDialog Component</span><span class="sxs-lookup"><span data-stu-id="70892-130">PageSetupDialog Component</span></span>](../controls/pagesetupdialog-component-windows-forms.md)  
 <span data-ttu-id="70892-131">Explique l’utilisation du composant <xref:System.Windows.Forms.PageSetupDialog>.</span><span class="sxs-lookup"><span data-stu-id="70892-131">Explains usage of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="70892-132">Décrit les classes de l’espace de noms <xref:System.Drawing.Printing>.</span><span class="sxs-lookup"><span data-stu-id="70892-132">Describes the classes in the <xref:System.Drawing.Printing> namespace.</span></span>
