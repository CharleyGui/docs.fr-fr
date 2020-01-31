---
title: StatusBar, contrôle
ms.date: 03/30/2017
helpviewer_keywords:
- StatusBar control [Windows Forms]
- status bars [Windows Forms], creating
ms.assetid: 6f543e27-cf78-4b7f-b4d0-6a8030155d48
ms.openlocfilehash: 4d48cf497eeedcff6290dfa8ddecf38ce8ff7c63
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742852"
---
# <a name="statusbar-control-windows-forms"></a><span data-ttu-id="ac8b4-102">StatusBar, contrôle (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ac8b4-102">StatusBar Control (Windows Forms)</span></span>
> [!NOTE]
> <span data-ttu-id="ac8b4-103">Le contrôle <xref:System.Windows.Forms.ToolStripStatusLabel> remplace le contrôle <xref:System.Windows.Forms.StatusBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.StatusBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="ac8b4-103">The <xref:System.Windows.Forms.ToolStripStatusLabel> control replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control; however, the <xref:System.Windows.Forms.StatusBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="ac8b4-104">Le contrôle <xref:System.Windows.Forms.StatusBar> Windows Forms est utilisé dans les formulaires tels que les zones, qui s'affichent habituellement au bas d'une fenêtre, et dans lesquelles une application peut afficher différents types d'informations d'état.</span><span class="sxs-lookup"><span data-stu-id="ac8b4-104">The Windows Forms <xref:System.Windows.Forms.StatusBar> control is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="ac8b4-105">les contrôles <xref:System.Windows.Forms.StatusBar> peuvent comporter des panneaux de barre d’État qui affichent des icônes pour indiquer l’État ou une série d’icônes dans une animation indiquant qu’un processus fonctionne ; par exemple, Microsoft Word indique que le document est en cours d’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="ac8b4-105"><xref:System.Windows.Forms.StatusBar> controls can have status-bar panels on them that display icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, Microsoft Word indicating that the document is being saved.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ac8b4-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ac8b4-106">In This Section</span></span>  
 [<span data-ttu-id="ac8b4-107">Vue d’ensemble du contrôle StatusBar</span><span class="sxs-lookup"><span data-stu-id="ac8b4-107">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)  
 <span data-ttu-id="ac8b4-108">Présente les concepts généraux du contrôle <xref:System.Windows.Forms.StatusBar>, qui permet aux utilisateurs de consulter les informations pertinentes pour le contrôle qui a le focus.</span><span class="sxs-lookup"><span data-stu-id="ac8b4-108">Introduces the general concepts of the <xref:System.Windows.Forms.StatusBar> control, which enables users to see relevant information for the control that has focus.</span></span>  
  
 [<span data-ttu-id="ac8b4-109">Guide pratique pour ajouter des panneaux à un contrôle StatusBar</span><span class="sxs-lookup"><span data-stu-id="ac8b4-109">How to: Add Panels to a StatusBar Control</span></span>](how-to-add-panels-to-a-statusbar-control.md)  
 <span data-ttu-id="ac8b4-110">Explique comment ajouter des panneaux programmables au contrôle <xref:System.Windows.Forms.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="ac8b4-110">Explains how to add programmable panels to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="ac8b4-111">Guide pratique pour déterminer le panneau du contrôle StatusBar Windows Forms sur lequel l’utilisateur a cliqué</span><span class="sxs-lookup"><span data-stu-id="ac8b4-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)  
 <span data-ttu-id="ac8b4-112">Explique comment gérer les événements <xref:System.Windows.Forms.Control.Click> déclenchés à partir du contrôle <xref:System.Windows.Forms.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="ac8b4-112">Explains how to handle <xref:System.Windows.Forms.Control.Click> events raised from the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="ac8b4-113">Guide pratique pour définir la taille des panneaux de la barre d'état</span><span class="sxs-lookup"><span data-stu-id="ac8b4-113">How to: Set the Size of Status-Bar Panels</span></span>](how-to-set-the-size-of-status-bar-panels.md)  
 <span data-ttu-id="ac8b4-114">Donne des détails sur les propriétés qui contrôlent le comportement de largeur et de redimensionnement des panneaux de la barre d’État au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ac8b4-114">Gives details on the properties that control the width and resize behavior of status-bar panels at run time.</span></span>  
  
 [<span data-ttu-id="ac8b4-115">Procédure pas à pas : mise à jour des informations de barre d'état au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="ac8b4-115">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)  
 <span data-ttu-id="ac8b4-116">Explique comment contrôler par programmation les données dans les panneaux de la barre d’État.</span><span class="sxs-lookup"><span data-stu-id="ac8b4-116">Explains how to programmatically control the data within status-bar panels.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ac8b4-117">Reference</span><span class="sxs-lookup"><span data-stu-id="ac8b4-117">Reference</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <span data-ttu-id="ac8b4-118">Fournit des informations de référence sur la classe et ses membres.</span><span class="sxs-lookup"><span data-stu-id="ac8b4-118">Provides reference information on the class and its members.</span></span>  
  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <span data-ttu-id="ac8b4-119">Remplace et ajoute des fonctionnalités au contrôle <xref:System.Windows.Forms.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="ac8b4-119">Replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ac8b4-120">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="ac8b4-120">Related Sections</span></span>  
 [<span data-ttu-id="ac8b4-121">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ac8b4-121">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="ac8b4-122">Fournit une liste complète de contrôles Windows Forms, avec des liens vers des informations sur leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="ac8b4-122">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
