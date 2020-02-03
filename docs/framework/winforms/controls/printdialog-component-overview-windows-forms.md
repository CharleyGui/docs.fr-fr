---
title: Vue d'ensemble du composant PrintDialog
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: 0ed7f7a1f9770f71b75ae744a056b6943335c852
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728668"
---
# <a name="printdialog-component-overview-windows-forms"></a><span data-ttu-id="c99d4-102">Vue d'ensemble du composant PrintDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="c99d4-102">PrintDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="c99d4-103">Le composant [PrintDialog](printdialog-component-windows-forms.md) Windows Forms est une boîte de dialogue préconfigurée qui permet de sélectionner une imprimante, de choisir les pages à imprimer et d’autres paramètres relatifs à l’impression dans les applications Windows.</span><span class="sxs-lookup"><span data-stu-id="c99d4-103">The Windows Forms [PrintDialog](printdialog-component-windows-forms.md) component is a pre-configured dialog box used to select a printer, choose the pages to print, and determine other print-related settings in Windows-based applications.</span></span> <span data-ttu-id="c99d4-104">Utilisez-le comme un moyen simple de sélectionner une imprimante ou des paramètres d'impression au lieu de configurer votre propre boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="c99d4-104">Use it as a simple solution for printer and print-related settings selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="c99d4-105">Vous pouvez autoriser les utilisateurs à imprimer plusieurs parties de leurs documents : imprimer tout, imprimer une plage de pages sélectionnée ou imprimer une sélection.</span><span class="sxs-lookup"><span data-stu-id="c99d4-105">You can enable users to print many parts of their documents: print all, print a selected page range, or print a selection.</span></span> <span data-ttu-id="c99d4-106">En vous appuyant sur des boîtes de dialogue Windows standard, vous pouvez créer des applications dont la fonction de base est immédiatement familière aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="c99d4-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="c99d4-107">Le composant <xref:System.Windows.Forms.PrintDialog> hérite de la classe <xref:System.Windows.Forms.CommonDialog>.</span><span class="sxs-lookup"><span data-stu-id="c99d4-107">The <xref:System.Windows.Forms.PrintDialog> component inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>

## <a name="working-with-the-component"></a><span data-ttu-id="c99d4-108">Utilisation du composant</span><span class="sxs-lookup"><span data-stu-id="c99d4-108">Working with the Component</span></span>

<span data-ttu-id="c99d4-109">Utilisez la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> pour afficher la boîte de dialogue au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="c99d4-109">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="c99d4-110">Ce composant a des propriétés qui sont liées à un travail d’impression unique (<xref:System.Drawing.Printing.PrintDocument> classe) ou aux paramètres d’une imprimante (<xref:System.Drawing.Printing.PrinterSettings> classe).</span><span class="sxs-lookup"><span data-stu-id="c99d4-110">This component has properties that relate to either a single print job (<xref:System.Drawing.Printing.PrintDocument> class) or the settings of an individual printer (<xref:System.Drawing.Printing.PrinterSettings> class).</span></span> <span data-ttu-id="c99d4-111">L’une ou l’autre, à son tour, peut être partagée par plusieurs imprimantes.</span><span class="sxs-lookup"><span data-stu-id="c99d4-111">Either of these, in turn, may be shared by multiple printers.</span></span>

<span data-ttu-id="c99d4-112">Lorsqu’il est ajouté à un formulaire, le composant <xref:System.Windows.Forms.PrintDialog> s’affiche dans la barre d’État en bas de la Concepteur Windows Forms dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c99d4-112">When it is added to a form, the <xref:System.Windows.Forms.PrintDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="c99d4-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c99d4-113">See also</span></span>

- <xref:System.Windows.Forms.PrintDialog>
- [<span data-ttu-id="c99d4-114">PrintDialog, composant</span><span class="sxs-lookup"><span data-stu-id="c99d4-114">PrintDialog Component</span></span>](printdialog-component-windows-forms.md)
