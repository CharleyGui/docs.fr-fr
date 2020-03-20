---
title: Prise en charge d'UI Automation pour les contrôles standard
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 36028d589e98177f6a0e83092edd656860b1a8d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179852"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="e7400-102">Prise en charge d'UI Automation pour les contrôles standard</span><span class="sxs-lookup"><span data-stu-id="e7400-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="e7400-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="e7400-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e7400-104">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="e7400-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="e7400-105">Ce sujet contient [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] des informations sur la [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]prise en charge des contrôles standard dans les applications développées pour les cadres , Win32 et Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e7400-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32, and Windows Forms frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="e7400-106">Contrôles Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="e7400-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="e7400-107">Tous les éléments du contrôle [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] qui fournissent des informations ou une prise en charge pour l’interaction utilisateur disposent d’une prise en charge native complète de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e7400-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="e7400-108">D’autres éléments, tels que les panneaux, ne sont pas visibles par [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e7400-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>
## <a name="win32-controls"></a><span data-ttu-id="e7400-109">Contrôles Win32</span><span class="sxs-lookup"><span data-stu-id="e7400-109">Win32 Controls</span></span>  
 <span data-ttu-id="e7400-110">La plupart des contrôles [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Win32 sont exposés par l’intermédiaire de fournisseurs côté client dans UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="e7400-110">Most Win32 controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="e7400-111">Cet assembly est inscrit automatiquement pour être utilisé avec les applications clientes UI Automation.</span><span class="sxs-lookup"><span data-stu-id="e7400-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="e7400-112">Le support complet est fourni uniquement pour les contrôles de la version 6 de *ComCtrl32.dll*.</span><span class="sxs-lookup"><span data-stu-id="e7400-112">Full support is provided only for controls from version 6 of *ComCtrl32.dll*.</span></span>  
  
 <span data-ttu-id="e7400-113">Les contrôles suivants sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="e7400-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="e7400-114">Nom de classe</span><span class="sxs-lookup"><span data-stu-id="e7400-114">Class name</span></span>|<span data-ttu-id="e7400-115">Type de contrôle</span><span class="sxs-lookup"><span data-stu-id="e7400-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="e7400-116">Bouton</span><span class="sxs-lookup"><span data-stu-id="e7400-116">Button</span></span>|<span data-ttu-id="e7400-117">Bouton</span><span class="sxs-lookup"><span data-stu-id="e7400-117">Button</span></span>|  
|<span data-ttu-id="e7400-118">Bouton</span><span class="sxs-lookup"><span data-stu-id="e7400-118">Button</span></span>|<span data-ttu-id="e7400-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="e7400-119">RadioButton</span></span>|  
|<span data-ttu-id="e7400-120">Bouton</span><span class="sxs-lookup"><span data-stu-id="e7400-120">Button</span></span>|<span data-ttu-id="e7400-121">Groupe</span><span class="sxs-lookup"><span data-stu-id="e7400-121">Group</span></span>|  
|<span data-ttu-id="e7400-122">Bouton</span><span class="sxs-lookup"><span data-stu-id="e7400-122">Button</span></span>|<span data-ttu-id="e7400-123">Case à cocher</span><span class="sxs-lookup"><span data-stu-id="e7400-123">CheckBox</span></span>|  
|<span data-ttu-id="e7400-124">Bouton</span><span class="sxs-lookup"><span data-stu-id="e7400-124">Button</span></span>|<span data-ttu-id="e7400-125">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="e7400-125">Hyperlink</span></span>|  
|<span data-ttu-id="e7400-126">Bouton</span><span class="sxs-lookup"><span data-stu-id="e7400-126">Button</span></span>|<span data-ttu-id="e7400-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="e7400-127">SplitButton</span></span>|  
|<span data-ttu-id="e7400-128">Bouton</span><span class="sxs-lookup"><span data-stu-id="e7400-128">Button</span></span>|<span data-ttu-id="e7400-129">Case à cocher</span><span class="sxs-lookup"><span data-stu-id="e7400-129">CheckBox</span></span>|  
|<span data-ttu-id="e7400-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="e7400-130">ComboBoxEx32</span></span>|<span data-ttu-id="e7400-131">Liste déroulante</span><span class="sxs-lookup"><span data-stu-id="e7400-131">ComboBox</span></span>|  
|<span data-ttu-id="e7400-132">Liste déroulante</span><span class="sxs-lookup"><span data-stu-id="e7400-132">ComboBox</span></span>|<span data-ttu-id="e7400-133">Liste déroulante</span><span class="sxs-lookup"><span data-stu-id="e7400-133">ComboBox</span></span>|  
|<span data-ttu-id="e7400-134">Modifier</span><span class="sxs-lookup"><span data-stu-id="e7400-134">Edit</span></span>|<span data-ttu-id="e7400-135">Document</span><span class="sxs-lookup"><span data-stu-id="e7400-135">Document</span></span>|  
|<span data-ttu-id="e7400-136">Modifier</span><span class="sxs-lookup"><span data-stu-id="e7400-136">Edit</span></span>|<span data-ttu-id="e7400-137">Modifier</span><span class="sxs-lookup"><span data-stu-id="e7400-137">Edit</span></span>|  
|<span data-ttu-id="e7400-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="e7400-138">SysLink</span></span>|<span data-ttu-id="e7400-139">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="e7400-139">Hyperlink</span></span>|  
|<span data-ttu-id="e7400-140">statique</span><span class="sxs-lookup"><span data-stu-id="e7400-140">Static</span></span>|<span data-ttu-id="e7400-141">Texte</span><span class="sxs-lookup"><span data-stu-id="e7400-141">Text</span></span>|  
|<span data-ttu-id="e7400-142">statique</span><span class="sxs-lookup"><span data-stu-id="e7400-142">Static</span></span>|<span data-ttu-id="e7400-143">Image</span><span class="sxs-lookup"><span data-stu-id="e7400-143">Image</span></span>|  
|<span data-ttu-id="e7400-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="e7400-144">SysIPAddress32</span></span>|<span data-ttu-id="e7400-145">Custom</span><span class="sxs-lookup"><span data-stu-id="e7400-145">Custom</span></span>|  
|<span data-ttu-id="e7400-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="e7400-146">SysHeader32</span></span>|<span data-ttu-id="e7400-147">Header/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="e7400-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="e7400-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="e7400-148">SysListView32</span></span>|<span data-ttu-id="e7400-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="e7400-149">DataGrid</span></span>|  
|<span data-ttu-id="e7400-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="e7400-150">SysListView32</span></span>|<span data-ttu-id="e7400-151">List</span><span class="sxs-lookup"><span data-stu-id="e7400-151">List</span></span>|  
|<span data-ttu-id="e7400-152">Zone de liste</span><span class="sxs-lookup"><span data-stu-id="e7400-152">ListBox</span></span>|<span data-ttu-id="e7400-153">List</span><span class="sxs-lookup"><span data-stu-id="e7400-153">List</span></span>|  
|<span data-ttu-id="e7400-154">Zone de liste</span><span class="sxs-lookup"><span data-stu-id="e7400-154">ListBox</span></span>|<span data-ttu-id="e7400-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="e7400-155">ListItem</span></span>|  
|<span data-ttu-id="e7400-156">#32768</span><span class="sxs-lookup"><span data-stu-id="e7400-156">#32768</span></span>|<span data-ttu-id="e7400-157">Menu</span><span class="sxs-lookup"><span data-stu-id="e7400-157">Menu</span></span>|  
|<span data-ttu-id="e7400-158">#32768</span><span class="sxs-lookup"><span data-stu-id="e7400-158">#32768</span></span>|<span data-ttu-id="e7400-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="e7400-159">MenuItem</span></span>|  
|<span data-ttu-id="e7400-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="e7400-160">msctls_progress32</span></span>|<span data-ttu-id="e7400-161">Barre de progression</span><span class="sxs-lookup"><span data-stu-id="e7400-161">ProgressBar</span></span>|  
|<span data-ttu-id="e7400-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="e7400-162">RichEdit</span></span>|<span data-ttu-id="e7400-163">Document.</span><span class="sxs-lookup"><span data-stu-id="e7400-163">Document.</span></span> <span data-ttu-id="e7400-164">Consultez la remarque.</span><span class="sxs-lookup"><span data-stu-id="e7400-164">See note.</span></span>|  
|<span data-ttu-id="e7400-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="e7400-165">RichEdit20A</span></span>|<span data-ttu-id="e7400-166">Document</span><span class="sxs-lookup"><span data-stu-id="e7400-166">Document</span></span>|  
|<span data-ttu-id="e7400-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="e7400-167">RichEdit20W</span></span>|<span data-ttu-id="e7400-168">Document</span><span class="sxs-lookup"><span data-stu-id="e7400-168">Document</span></span>|  
|<span data-ttu-id="e7400-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="e7400-169">RichEdit50W</span></span>|<span data-ttu-id="e7400-170">Document</span><span class="sxs-lookup"><span data-stu-id="e7400-170">Document</span></span>|  
|<span data-ttu-id="e7400-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="e7400-171">ScrollBar</span></span>|<span data-ttu-id="e7400-172">Curseur</span><span class="sxs-lookup"><span data-stu-id="e7400-172">Slider</span></span>|  
|<span data-ttu-id="e7400-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="e7400-173">msctls_trackbar32</span></span>|<span data-ttu-id="e7400-174">Curseur</span><span class="sxs-lookup"><span data-stu-id="e7400-174">Slider</span></span>|  
|<span data-ttu-id="e7400-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="e7400-175">msctls_updown32</span></span>|<span data-ttu-id="e7400-176">Spinner</span><span class="sxs-lookup"><span data-stu-id="e7400-176">Spinner</span></span>|  
|<span data-ttu-id="e7400-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="e7400-177">msctls_statusbar32</span></span>|<span data-ttu-id="e7400-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="e7400-178">StatusBar</span></span>|  
|<span data-ttu-id="e7400-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="e7400-179">SysTabControl32</span></span>|<span data-ttu-id="e7400-180">Onglet</span><span class="sxs-lookup"><span data-stu-id="e7400-180">Tab</span></span>|  
|<span data-ttu-id="e7400-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="e7400-181">SysTabControl32</span></span>|<span data-ttu-id="e7400-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="e7400-182">TabItem</span></span>|  
|<span data-ttu-id="e7400-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="e7400-183">ToolbarWindow32</span></span>|<span data-ttu-id="e7400-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="e7400-184">ToolBar</span></span>|  
|<span data-ttu-id="e7400-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="e7400-185">ToolbarWindow32</span></span>|<span data-ttu-id="e7400-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="e7400-186">MenuItem</span></span>|  
|<span data-ttu-id="e7400-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="e7400-187">ToolbarWindow32</span></span>|<span data-ttu-id="e7400-188">Bouton</span><span class="sxs-lookup"><span data-stu-id="e7400-188">Button</span></span>|  
|<span data-ttu-id="e7400-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="e7400-189">ToolbarWindow32</span></span>|<span data-ttu-id="e7400-190">Case à cocher</span><span class="sxs-lookup"><span data-stu-id="e7400-190">CheckBox</span></span>|  
|<span data-ttu-id="e7400-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="e7400-191">ToolbarWindow32</span></span>|<span data-ttu-id="e7400-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="e7400-192">RadioButton</span></span>|  
|<span data-ttu-id="e7400-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="e7400-193">ToolbarWindow32</span></span>|<span data-ttu-id="e7400-194">Séparateur</span><span class="sxs-lookup"><span data-stu-id="e7400-194">Separator</span></span>|  
|<span data-ttu-id="e7400-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="e7400-195">tooltips_class32</span></span>|<span data-ttu-id="e7400-196">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="e7400-196">ToolTip</span></span>|  
|<span data-ttu-id="e7400-197">#32774</span><span class="sxs-lookup"><span data-stu-id="e7400-197">#32774</span></span>|<span data-ttu-id="e7400-198">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="e7400-198">ToolTip</span></span>|  
|<span data-ttu-id="e7400-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="e7400-199">ReBarWindow32</span></span>|<span data-ttu-id="e7400-200">Barre d'outils</span><span class="sxs-lookup"><span data-stu-id="e7400-200">Toolbar</span></span>|  
|<span data-ttu-id="e7400-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="e7400-201">SysTreeView32</span></span>|<span data-ttu-id="e7400-202">Arborescence</span><span class="sxs-lookup"><span data-stu-id="e7400-202">Tree</span></span>|  
|<span data-ttu-id="e7400-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="e7400-203">SysTreeView32</span></span>|<span data-ttu-id="e7400-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="e7400-204">TreeItem</span></span>|  
  
 <span data-ttu-id="e7400-205">**Note** Le contrôle RichEdit est pris en charge uniquement pour les versions expédiées avec Windows Vista (dans la version 3.1 richEd20.dll et plus tard, et MsftEdit.dll version 4.1 et plus tard).</span><span class="sxs-lookup"><span data-stu-id="e7400-205">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="e7400-206">Les contrôles suivants ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="e7400-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="e7400-207">Nom de classe</span><span class="sxs-lookup"><span data-stu-id="e7400-207">Class name</span></span>|<span data-ttu-id="e7400-208">Type de contrôle</span><span class="sxs-lookup"><span data-stu-id="e7400-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="e7400-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="e7400-209">SysAnimate32</span></span>|<span data-ttu-id="e7400-210">Image</span><span class="sxs-lookup"><span data-stu-id="e7400-210">Image</span></span>|  
|<span data-ttu-id="e7400-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="e7400-211">SysPager</span></span>|<span data-ttu-id="e7400-212">Spinner</span><span class="sxs-lookup"><span data-stu-id="e7400-212">Spinner</span></span>|  
|<span data-ttu-id="e7400-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="e7400-213">SysDateTimePick32</span></span>|<span data-ttu-id="e7400-214">Custom</span><span class="sxs-lookup"><span data-stu-id="e7400-214">Custom</span></span>|  
|<span data-ttu-id="e7400-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="e7400-215">SysMonthCal32</span></span>|<span data-ttu-id="e7400-216">Calendrier</span><span class="sxs-lookup"><span data-stu-id="e7400-216">Calendar</span></span>|  
|<span data-ttu-id="e7400-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="e7400-217">MS_WINNOTE</span></span>|<span data-ttu-id="e7400-218">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="e7400-218">Tooltip</span></span>|  
|<span data-ttu-id="e7400-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="e7400-219">VBBubble</span></span>|<span data-ttu-id="e7400-220">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="e7400-220">Tooltip</span></span>|  
|<span data-ttu-id="e7400-221">ScrollBar (quand il est utilisé comme contrôle autonome)</span><span class="sxs-lookup"><span data-stu-id="e7400-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="e7400-222">Curseur</span><span class="sxs-lookup"><span data-stu-id="e7400-222">Slider</span></span>|  
|<span data-ttu-id="e7400-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="e7400-223">SuperGrid</span></span>|<span data-ttu-id="e7400-224">Custom</span><span class="sxs-lookup"><span data-stu-id="e7400-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>
## <a name="windows-forms-controls"></a><span data-ttu-id="e7400-225">contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e7400-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="e7400-226">Les contrôles des [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] formulaires Windows sont exposés par l’intermédiaire de fournisseurs côté client dans UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="e7400-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="e7400-227">Cet assembly est inscrit automatiquement pour être utilisé avec les applications clientes UI Automation.</span><span class="sxs-lookup"><span data-stu-id="e7400-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="e7400-228">Typiquement, les contrôles de formulaires Windows qui sont des [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]emballages gérés pour les contrôles communs Win32 sont pris en charge par .</span><span class="sxs-lookup"><span data-stu-id="e7400-228">Typically, Windows Forms controls that are managed wrappers for Win32 common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="e7400-229">Les contrôles suivants sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="e7400-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="e7400-230">Nom de la classe</span><span class="sxs-lookup"><span data-stu-id="e7400-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="e7400-231">Bouton</span><span class="sxs-lookup"><span data-stu-id="e7400-231">Button</span></span>|  
|<span data-ttu-id="e7400-232">Case à cocher</span><span class="sxs-lookup"><span data-stu-id="e7400-232">CheckBox</span></span>|  
|<span data-ttu-id="e7400-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="e7400-233">CheckedListBox</span></span>|  
|<span data-ttu-id="e7400-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="e7400-234">ColorDialog</span></span>|  
|<span data-ttu-id="e7400-235">Liste déroulante</span><span class="sxs-lookup"><span data-stu-id="e7400-235">ComboBox</span></span>|  
|<span data-ttu-id="e7400-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="e7400-236">FolderBrowser</span></span>|  
|<span data-ttu-id="e7400-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="e7400-237">FontDialog</span></span>|  
|<span data-ttu-id="e7400-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="e7400-238">GroupBox</span></span>|  
|<span data-ttu-id="e7400-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="e7400-239">HscrollBar</span></span>|  
|<span data-ttu-id="e7400-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="e7400-240">ImageList</span></span>|  
|<span data-ttu-id="e7400-241">Étiquette</span><span class="sxs-lookup"><span data-stu-id="e7400-241">Label</span></span>|  
|<span data-ttu-id="e7400-242">Zone de liste</span><span class="sxs-lookup"><span data-stu-id="e7400-242">ListBox</span></span>|  
|<span data-ttu-id="e7400-243">Affichage de liste</span><span class="sxs-lookup"><span data-stu-id="e7400-243">ListView</span></span>|  
|<span data-ttu-id="e7400-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="e7400-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="e7400-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="e7400-245">MonthCalendar</span></span>|  
|<span data-ttu-id="e7400-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="e7400-246">NotifyIcon</span></span>|  
|<span data-ttu-id="e7400-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="e7400-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="e7400-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="e7400-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="e7400-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="e7400-249">PrintDialog</span></span>|  
|<span data-ttu-id="e7400-250">Barre de progression</span><span class="sxs-lookup"><span data-stu-id="e7400-250">ProgressBar</span></span>|  
|<span data-ttu-id="e7400-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="e7400-251">RadioButton</span></span>|  
|<span data-ttu-id="e7400-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="e7400-252">RichTextBox</span></span>|  
|<span data-ttu-id="e7400-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="e7400-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="e7400-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="e7400-254">ScrollableControl</span></span>|  
|<span data-ttu-id="e7400-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="e7400-255">SoundPlayer</span></span>|  
|<span data-ttu-id="e7400-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="e7400-256">StatusBar</span></span>|  
|<span data-ttu-id="e7400-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="e7400-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="e7400-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="e7400-258">TextBox</span></span>|  
|<span data-ttu-id="e7400-259">Minuterie</span><span class="sxs-lookup"><span data-stu-id="e7400-259">Timer</span></span>|  
|<span data-ttu-id="e7400-260">Barre d'outils</span><span class="sxs-lookup"><span data-stu-id="e7400-260">Toolbar</span></span>|  
|<span data-ttu-id="e7400-261">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="e7400-261">ToolTip</span></span>|  
|<span data-ttu-id="e7400-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="e7400-262">TrackBar</span></span>|  
|<span data-ttu-id="e7400-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="e7400-263">TreeView</span></span>|  
|<span data-ttu-id="e7400-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="e7400-264">VscrollBar</span></span>|  
|<span data-ttu-id="e7400-265">Navigateur web</span><span class="sxs-lookup"><span data-stu-id="e7400-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="e7400-266">Les contrôles suivants [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] ne sont exposés qu’en supportant Microsoft Active Accessibility.</span><span class="sxs-lookup"><span data-stu-id="e7400-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="e7400-267">Certaines fonctionnalités ne sont peut-être pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="e7400-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="e7400-268">Nom du contrôle</span><span class="sxs-lookup"><span data-stu-id="e7400-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="e7400-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="e7400-269">BindingSource</span></span>|  
|<span data-ttu-id="e7400-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="e7400-270">DataGrid</span></span>|  
|<span data-ttu-id="e7400-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="e7400-271">DataGridView</span></span>|  
|<span data-ttu-id="e7400-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="e7400-272">DataNavigator</span></span>|  
|<span data-ttu-id="e7400-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="e7400-273">DomainUpDown</span></span>|  
|<span data-ttu-id="e7400-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="e7400-274">ErrorProvider</span></span>|  
|<span data-ttu-id="e7400-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="e7400-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="e7400-276">Formulaire</span><span class="sxs-lookup"><span data-stu-id="e7400-276">Form</span></span>|  
|<span data-ttu-id="e7400-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="e7400-277">LinkLabel</span></span>|  
|<span data-ttu-id="e7400-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="e7400-278">HelpProvider</span></span>|  
|<span data-ttu-id="e7400-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="e7400-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="e7400-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="e7400-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="e7400-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="e7400-281">NumericUpDown</span></span>|  
|<span data-ttu-id="e7400-282">Volet</span><span class="sxs-lookup"><span data-stu-id="e7400-282">Panel</span></span>|  
|<span data-ttu-id="e7400-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="e7400-283">PictureBox</span></span>|  
|<span data-ttu-id="e7400-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="e7400-284">PrintDocument</span></span>|  
|<span data-ttu-id="e7400-285">PrintPreviewControl</span><span class="sxs-lookup"><span data-stu-id="e7400-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="e7400-286">PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="e7400-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="e7400-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="e7400-287">PropertyGrid</span></span>|  
|<span data-ttu-id="e7400-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="e7400-288">UserControl</span></span>|  
|<span data-ttu-id="e7400-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="e7400-289">ToolStrip</span></span>|  
|<span data-ttu-id="e7400-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="e7400-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="e7400-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="e7400-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="e7400-292">Séparateur</span><span class="sxs-lookup"><span data-stu-id="e7400-292">Splitter</span></span>|  
|<span data-ttu-id="e7400-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="e7400-293">RaftingContainer</span></span>|  
|<span data-ttu-id="e7400-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="e7400-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7400-295">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7400-295">See also</span></span>

- [<span data-ttu-id="e7400-296">UI Automation Control Types</span><span class="sxs-lookup"><span data-stu-id="e7400-296">UI Automation Control Types</span></span>](ui-automation-control-types.md)
