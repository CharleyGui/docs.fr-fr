---
title: Vue d'ensemble du composant PrintDocument (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: 16a7f3a34ccb280f7bf91c52e29b20edc22130b9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928991"
---
# <a name="printdocument-component-overview-windows-forms"></a><span data-ttu-id="91809-102">Vue d'ensemble du composant PrintDocument (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="91809-102">PrintDocument Component Overview (Windows Forms)</span></span>

<span data-ttu-id="91809-103">Le composant [PrintDocument](printdocument-component-windows-forms.md) Windows Forms permet de définir les propriétés qui décrivent les éléments à imprimer, puis d’imprimer le document dans des applications Windows.</span><span class="sxs-lookup"><span data-stu-id="91809-103">The Windows Forms [PrintDocument](printdocument-component-windows-forms.md) component is used to set the properties that describe what to print and the ability to print the document within Windows-based applications.</span></span> <span data-ttu-id="91809-104">Il peut être utilisé conjointement avec le composant [PrintDialog](printdialog-component-windows-forms.md) pour contrôler tous les aspects de l’impression du document.</span><span class="sxs-lookup"><span data-stu-id="91809-104">It can be used in conjunction with the [PrintDialog](printdialog-component-windows-forms.md) component to be in control of all aspects of document printing.</span></span>

## <a name="working-with-the-printdocument-component"></a><span data-ttu-id="91809-105">Utilisation du composant PrintDocument</span><span class="sxs-lookup"><span data-stu-id="91809-105">Working with the PrintDocument Component</span></span>

<span data-ttu-id="91809-106">Deux des principaux scénarios qui impliquent le <xref:System.Drawing.Printing.PrintDocument> composant sont les suivants:</span><span class="sxs-lookup"><span data-stu-id="91809-106">Two of the main scenarios that involve the <xref:System.Drawing.Printing.PrintDocument> component are:</span></span>

- <span data-ttu-id="91809-107">Travaux d’impression simples, tels que l’impression d’un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="91809-107">Simple print jobs, such as printing an individual text file.</span></span> <span data-ttu-id="91809-108">Dans ce cas, vous devez ajouter le <xref:System.Drawing.Printing.PrintDocument> composant à un Windows Form, puis ajouter une logique de programmation qui imprime un <xref:System.Drawing.Printing.PrintDocument.PrintPage> fichier dans le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="91809-108">In such a case you would add the <xref:System.Drawing.Printing.PrintDocument> component to a Windows Form, then add programming logic that prints a file in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler.</span></span> <span data-ttu-id="91809-109">La logique de programmation doit se déboucher sur la <xref:System.Drawing.Printing.PrintDocument.Print%2A> méthode pour imprimer le document.</span><span class="sxs-lookup"><span data-stu-id="91809-109">The programming logic should culminate with the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to print the document.</span></span> <span data-ttu-id="91809-110">Cette méthode envoie un <xref:System.Drawing.Graphics> objet, contenu dans la <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> propriété de la <xref:System.Drawing.Printing.PrintPageEventArgs> classe, à l’imprimante.</span><span class="sxs-lookup"><span data-stu-id="91809-110">This method sends a <xref:System.Drawing.Graphics> object, contained in the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class, to the printer.</span></span> <span data-ttu-id="91809-111">Pour obtenir un exemple qui montre comment imprimer un document texte à l' <xref:System.Drawing.Printing.PrintDocument> aide du composant [, consultez Procédure: Imprimez un fichier texte contenant plusieurs pages](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)dans Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="91809-111">For an example that shows how to print a text document using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print a Multi-Page Text File in Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span></span>

- <span data-ttu-id="91809-112">Travaux d’impression plus complexes, comme lorsque vous souhaitez réutiliser la logique d’impression que vous avez écrite.</span><span class="sxs-lookup"><span data-stu-id="91809-112">More complex print jobs, such as a situation where you will want to reuse printing logic you have written.</span></span> <span data-ttu-id="91809-113">Dans ce cas, vous devez dériver un nouveau composant du <xref:System.Drawing.Printing.PrintDocument> composant et remplacer (consultez [substitutions](../../../visual-basic/language-reference/modifiers/overrides.md) pour Visual Basic ou [remplacer](../../../csharp/language-reference/keywords/override.md) pour C#) l' <xref:System.Drawing.Printing.PrintDocument.PrintPage> événement.</span><span class="sxs-lookup"><span data-stu-id="91809-113">In such a case you would derive a new component from the <xref:System.Drawing.Printing.PrintDocument> component and override (see [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md) for Visual Basic or [override](../../../csharp/language-reference/keywords/override.md) for C#) the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>

<span data-ttu-id="91809-114">Lorsqu’il est ajouté à un formulaire, le <xref:System.Drawing.Printing.PrintDocument> composant apparaît dans la barre d’État en bas de la Concepteur Windows Forms dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="91809-114">When it is added to a form, the <xref:System.Drawing.Printing.PrintDocument> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="91809-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91809-115">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="91809-116">Prise en charge de l’impression dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="91809-116">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="91809-117">Composant PrintDocument</span><span class="sxs-lookup"><span data-stu-id="91809-117">PrintDocument Component</span></span>](printdocument-component-windows-forms.md)
