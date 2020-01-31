---
title: Vue d'ensemble du composant PageSetupDialog
ms.date: 03/30/2017
f1_keywords:
- PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
ms.openlocfilehash: a891cb8cc77007d7591d41461c94f61c077eb300
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744342"
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a><span data-ttu-id="e4f56-102">Vue d'ensemble du composant PageSetupDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e4f56-102">PageSetupDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="e4f56-103">Le composant Windows Forms <xref:System.Windows.Forms.PageSetupDialog> est une boîte de dialogue préconfigurée utilisée pour définir les détails de la page d’impression dans les applications Windows.</span><span class="sxs-lookup"><span data-stu-id="e4f56-103">The Windows Forms <xref:System.Windows.Forms.PageSetupDialog> component is a pre-configured dialog box used to set page details for printing in Windows-based applications.</span></span> <span data-ttu-id="e4f56-104">Utilisez-le au sein de votre application Windows comme une solution simple permettant aux utilisateurs de définir des préférences de page plutôt que de configurer votre propre boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="e4f56-104">Use it within your Windows-based application as a simple solution for users to set page preferences in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="e4f56-105">Vous pouvez permettre aux utilisateurs de définir des ajustements de bordure et de marge, des en-têtes et des pieds de page, ainsi que l’orientation portrait ou paysage.</span><span class="sxs-lookup"><span data-stu-id="e4f56-105">You can enable users to set border and margin adjustments, headers and footers, and portrait or landscape orientation.</span></span> <span data-ttu-id="e4f56-106">En vous appuyant sur des boîtes de dialogue Windows standard, vous pouvez créer des applications dont la fonction de base est immédiatement familière aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="e4f56-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span>

## <a name="key-properties-and-methods"></a><span data-ttu-id="e4f56-107">Propriétés et méthodes de clé</span><span class="sxs-lookup"><span data-stu-id="e4f56-107">Key Properties and Methods</span></span>

<span data-ttu-id="e4f56-108">Utilisez la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> pour afficher la boîte de dialogue au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e4f56-108">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="e4f56-109">Ce composant contient des propriétés que vous pouvez définir en relation avec une seule page (<xref:System.Drawing.Printing.PrintDocument> classe) ou n’importe quel document (classe<xref:System.Drawing.Printing.PageSettings>).</span><span class="sxs-lookup"><span data-stu-id="e4f56-109">This component has properties you can set that relate to either a single page (<xref:System.Drawing.Printing.PrintDocument> class) or any document (<xref:System.Drawing.Printing.PageSettings> class).</span></span> <span data-ttu-id="e4f56-110">En outre, le composant <xref:System.Windows.Forms.PageSetupDialog> peut être utilisé pour déterminer des paramètres d’imprimante spécifiques, qui sont stockés dans la classe <xref:System.Drawing.Printing.PrinterSettings>.</span><span class="sxs-lookup"><span data-stu-id="e4f56-110">Additionally, the <xref:System.Windows.Forms.PageSetupDialog> component can be used to determine specific printer settings, which are stored in the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span>

<span data-ttu-id="e4f56-111">Lorsqu’il est ajouté à un formulaire, le composant <xref:System.Windows.Forms.PageSetupDialog> s’affiche dans la barre d’État en bas de la Concepteur Windows Forms dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e4f56-111">When it is added to a form, the <xref:System.Windows.Forms.PageSetupDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="e4f56-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4f56-112">See also</span></span>

- <xref:System.Windows.Forms.PageSetupDialog>
- [<span data-ttu-id="e4f56-113">PageSetupDialog Component</span><span class="sxs-lookup"><span data-stu-id="e4f56-113">PageSetupDialog Component</span></span>](pagesetupdialog-component-windows-forms.md)
