---
title: Vue d'ensemble du composant PrintDocument
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: a82cc0cdcb8cfae796c9c6bf60ab73873f85a291
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728542"
---
# <a name="printdocument-component-overview-windows-forms"></a><span data-ttu-id="7f394-102">Vue d'ensemble du composant PrintDocument (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="7f394-102">PrintDocument Component Overview (Windows Forms)</span></span>

<span data-ttu-id="7f394-103">Le composant [PrintDocument](printdocument-component-windows-forms.md) Windows Forms permet de définir les propriétés qui décrivent les éléments à imprimer, puis d’imprimer le document dans des applications Windows.</span><span class="sxs-lookup"><span data-stu-id="7f394-103">The Windows Forms [PrintDocument](printdocument-component-windows-forms.md) component is used to set the properties that describe what to print and the ability to print the document within Windows-based applications.</span></span> <span data-ttu-id="7f394-104">Il peut être utilisé conjointement avec le composant [PrintDialog](printdialog-component-windows-forms.md) pour contrôler tous les aspects de l’impression du document.</span><span class="sxs-lookup"><span data-stu-id="7f394-104">It can be used in conjunction with the [PrintDialog](printdialog-component-windows-forms.md) component to be in control of all aspects of document printing.</span></span>

## <a name="working-with-the-printdocument-component"></a><span data-ttu-id="7f394-105">Utilisation du composant PrintDocument</span><span class="sxs-lookup"><span data-stu-id="7f394-105">Working with the PrintDocument Component</span></span>

<span data-ttu-id="7f394-106">Deux des principaux scénarios qui impliquent le composant <xref:System.Drawing.Printing.PrintDocument> sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="7f394-106">Two of the main scenarios that involve the <xref:System.Drawing.Printing.PrintDocument> component are:</span></span>

- <span data-ttu-id="7f394-107">Travaux d’impression simples, tels que l’impression d’un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="7f394-107">Simple print jobs, such as printing an individual text file.</span></span> <span data-ttu-id="7f394-108">Dans ce cas, vous devez ajouter le composant <xref:System.Drawing.Printing.PrintDocument> à un Windows Form, puis ajouter une logique de programmation qui imprime un fichier dans le gestionnaire d’événements <xref:System.Drawing.Printing.PrintDocument.PrintPage>.</span><span class="sxs-lookup"><span data-stu-id="7f394-108">In such a case you would add the <xref:System.Drawing.Printing.PrintDocument> component to a Windows Form, then add programming logic that prints a file in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler.</span></span> <span data-ttu-id="7f394-109">La logique de programmation doit se déboucher sur la méthode <xref:System.Drawing.Printing.PrintDocument.Print%2A> pour imprimer le document.</span><span class="sxs-lookup"><span data-stu-id="7f394-109">The programming logic should culminate with the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to print the document.</span></span> <span data-ttu-id="7f394-110">Cette méthode envoie un objet <xref:System.Drawing.Graphics>, contenu dans la propriété <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> de la classe <xref:System.Drawing.Printing.PrintPageEventArgs>, à l’imprimante.</span><span class="sxs-lookup"><span data-stu-id="7f394-110">This method sends a <xref:System.Drawing.Graphics> object, contained in the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class, to the printer.</span></span> <span data-ttu-id="7f394-111">Pour obtenir un exemple qui montre comment imprimer un document texte à l’aide du composant <xref:System.Drawing.Printing.PrintDocument>, consultez [Comment : imprimer un fichier texte à plusieurs pages dans Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="7f394-111">For an example that shows how to print a text document using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print a Multi-Page Text File in Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span></span>

- <span data-ttu-id="7f394-112">Travaux d’impression plus complexes, comme lorsque vous souhaitez réutiliser la logique d’impression que vous avez écrite.</span><span class="sxs-lookup"><span data-stu-id="7f394-112">More complex print jobs, such as a situation where you will want to reuse printing logic you have written.</span></span> <span data-ttu-id="7f394-113">Dans ce cas, vous devez dériver un nouveau composant du composant <xref:System.Drawing.Printing.PrintDocument> et remplacer (consultez [substitutions](../../../visual-basic/language-reference/modifiers/overrides.md) pour Visual Basic ou [remplacer](../../../csharp/language-reference/keywords/override.md) pour C#) l’événement <xref:System.Drawing.Printing.PrintDocument.PrintPage>.</span><span class="sxs-lookup"><span data-stu-id="7f394-113">In such a case you would derive a new component from the <xref:System.Drawing.Printing.PrintDocument> component and override (see [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md) for Visual Basic or [override](../../../csharp/language-reference/keywords/override.md) for C#) the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>

<span data-ttu-id="7f394-114">Lorsqu’il est ajouté à un formulaire, le composant <xref:System.Drawing.Printing.PrintDocument> s’affiche dans la barre d’État en bas de la Concepteur Windows Forms dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7f394-114">When it is added to a form, the <xref:System.Drawing.Printing.PrintDocument> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f394-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f394-115">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="7f394-116">Prise en charge de l’impression dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7f394-116">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="7f394-117">Composant PrintDocument</span><span class="sxs-lookup"><span data-stu-id="7f394-117">PrintDocument Component</span></span>](printdocument-component-windows-forms.md)
