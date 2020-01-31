---
title: Vue d'ensemble du contrôle StatusBar
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: b0b97bc3cb0291871e1fd113d82d0b480b53cdba
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742867"
---
# <a name="statusbar-control-overview-windows-forms"></a><span data-ttu-id="2f055-102">Vue d'ensemble du contrôle StatusBar (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="2f055-102">StatusBar Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="2f055-103">Les contrôles <xref:System.Windows.Forms.StatusStrip> et <xref:System.Windows.Forms.ToolStripStatusLabel> remplacent et ajoutent des fonctionnalités aux contrôles <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> ; Toutefois, les contrôles <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> sont conservés pour la compatibilité descendante et l’utilisation future, si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="2f055-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="2f055-104">Le [contrôle Windows Forms StatusBar](statusbar-control-windows-forms.md) est utilisé sur les formulaires comme une zone, généralement affichée en bas d’une fenêtre, dans laquelle une application peut afficher différents types d’informations d’État.</span><span class="sxs-lookup"><span data-stu-id="2f055-104">The Windows Forms [StatusBar Control](statusbar-control-windows-forms.md) is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="2f055-105">les contrôles <xref:System.Windows.Forms.StatusBar> peuvent comporter des panneaux de barre d’État qui affichent du texte ou des icônes pour indiquer l’État, ou une série d’icônes dans une animation indiquant qu’un processus fonctionne ; par exemple, Microsoft Word indique que le document est en cours d’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="2f055-105"><xref:System.Windows.Forms.StatusBar> controls can have status bar panels on them that display text or icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, Microsoft Word indicating that the document is being saved.</span></span>  
  
## <a name="using-the-statusbar-control"></a><span data-ttu-id="2f055-106">Utilisation du contrôle StatusBar</span><span class="sxs-lookup"><span data-stu-id="2f055-106">Using the StatusBar Control</span></span>  
 <span data-ttu-id="2f055-107">Internet Explorer utilise une barre d’État pour indiquer l’URL d’une page lorsque la souris passe sur le lien hypertexte ; Microsoft Word vous donne des informations sur l’emplacement de la page, l’emplacement de la section et les modes de modification tels que le défrappe et le suivi des révisions. et Visual Studio utilise la barre d’État pour fournir des informations contextuelles, telles que la manipulation des fenêtres ancrables, ancrées ou flottantes.</span><span class="sxs-lookup"><span data-stu-id="2f055-107">Internet Explorer uses a status bar to indicate the URL of a page when the mouse rolls over the hyperlink; Microsoft Word gives you information on page location, section location, and editing modes such as overtype and revision tracking; and Visual Studio uses the status bar to give context-sensitive information, such as telling you how to manipulate dockable windows as either docked or floating.</span></span>  
  
 <span data-ttu-id="2f055-108">Vous pouvez afficher un seul message dans la barre d’État en affectant à la propriété <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> la valeur `false` (valeur par défaut) et en affectant à la propriété <xref:System.Windows.Forms.StatusBar.Text%2A> de la barre d’État le texte que vous souhaitez voir apparaître dans la barre d’État.</span><span class="sxs-lookup"><span data-stu-id="2f055-108">You can display a single message on the status bar by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `false` (the default) and setting the <xref:System.Windows.Forms.StatusBar.Text%2A> property of the status bar to the text you want to appear in the status bar.</span></span> <span data-ttu-id="2f055-109">Vous pouvez diviser la barre d’État en panneaux pour afficher plusieurs types d’informations en affectant à la propriété <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> la valeur `true` et à l’aide de la méthode <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> de <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span><span class="sxs-lookup"><span data-stu-id="2f055-109">You can divide the status bar into panels to display more than one type of information by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true` and using the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> method of <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f055-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f055-110">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="2f055-111">Guide pratique pour déterminer le panneau du contrôle StatusBar Windows Forms sur lequel l’utilisateur a cliqué</span><span class="sxs-lookup"><span data-stu-id="2f055-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
