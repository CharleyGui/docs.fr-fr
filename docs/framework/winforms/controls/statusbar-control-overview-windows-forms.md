---
title: Vue d'ensemble du contrôle StatusBar (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: 4e1816ef221641f5ad54fb429442ed43289b592a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505425"
---
# <a name="statusbar-control-overview-windows-forms"></a><span data-ttu-id="b933b-102">Vue d'ensemble du contrôle StatusBar (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="b933b-102">StatusBar Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="b933b-103">Le <xref:System.Windows.Forms.StatusStrip> et <xref:System.Windows.Forms.ToolStripStatusLabel> contrôles remplacent et ajoutent des fonctionnalités à la <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> contrôle ; Toutefois, le <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> contrôles ont été conservés pour la compatibilité descendante et une utilisation ultérieure, si vous Choisissez.</span><span class="sxs-lookup"><span data-stu-id="b933b-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="b933b-104">Les formulaires Windows [du contrôle StatusBar](statusbar-control-windows-forms.md) est utilisé sur les formulaires comme une zone, généralement affichée en bas d’une fenêtre dans laquelle une application peut afficher différents types d’informations d’état.</span><span class="sxs-lookup"><span data-stu-id="b933b-104">The Windows Forms [StatusBar Control](statusbar-control-windows-forms.md) is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="b933b-105"><xref:System.Windows.Forms.StatusBar> contrôles peuvent avoir des panneaux de barre d’état affiche du texte ou des icônes pour indiquer l’état, ou une série d’icônes dans une animation qui indiquent le qu'utilisation d’un processus ; par exemple, Microsoft Word indiquant que le document est enregistré.</span><span class="sxs-lookup"><span data-stu-id="b933b-105"><xref:System.Windows.Forms.StatusBar> controls can have status bar panels on them that display text or icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, Microsoft Word indicating that the document is being saved.</span></span>  
  
## <a name="using-the-statusbar-control"></a><span data-ttu-id="b933b-106">Utilisation du contrôle StatusBar</span><span class="sxs-lookup"><span data-stu-id="b933b-106">Using the StatusBar Control</span></span>  
 <span data-ttu-id="b933b-107">Internet Explorer utilise une barre d’état pour indiquer l’URL d’une page lorsque la souris passe sur le lien hypertexte ; Microsoft Word vous donne des informations sur l’emplacement de la page, l’emplacement de la section et modes d’édition comme refrappe et le suivi des révisions. et Visual Studio utilise la barre d’état pour donner des informations contextuelles, telles que de vous indiquer comment manipuler les fenêtres ancrables ou flottantes.</span><span class="sxs-lookup"><span data-stu-id="b933b-107">Internet Explorer uses a status bar to indicate the URL of a page when the mouse rolls over the hyperlink; Microsoft Word gives you information on page location, section location, and editing modes such as overtype and revision tracking; and Visual Studio uses the status bar to give context-sensitive information, such as telling you how to manipulate dockable windows as either docked or floating.</span></span>  
  
 <span data-ttu-id="b933b-108">Vous pouvez afficher un message sur la barre d’état en définissant le <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> propriété `false` (la valeur par défaut) et en définissant le <xref:System.Windows.Forms.StatusBar.Text%2A> propriété de la barre d’état pour le texte que vous souhaitez voir apparaître dans la barre d’état.</span><span class="sxs-lookup"><span data-stu-id="b933b-108">You can display a single message on the status bar by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `false` (the default) and setting the <xref:System.Windows.Forms.StatusBar.Text%2A> property of the status bar to the text you want to appear in the status bar.</span></span> <span data-ttu-id="b933b-109">Vous pouvez diviser la barre d’état en panneaux pour afficher plusieurs types d’informations en définissant le <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> propriété `true` et à l’aide de la <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> méthode de <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span><span class="sxs-lookup"><span data-stu-id="b933b-109">You can divide the status bar into panels to display more than one type of information by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true` and using the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> method of <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b933b-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b933b-110">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="b933b-111">Guide pratique pour Déterminer l’utilisateur a cliqué sur le panneau du contrôle StatusBar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b933b-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
