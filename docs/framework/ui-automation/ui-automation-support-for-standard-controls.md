---
title: Prise en charge d'UI Automation pour les contrôles standard
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 49277073706444fd611ae41e762442388ac50b71
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789600"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="92e2f-102">Prise en charge d'UI Automation pour les contrôles standard</span><span class="sxs-lookup"><span data-stu-id="92e2f-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="92e2f-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="92e2f-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="92e2f-104">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="92e2f-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="92e2f-105">Cette rubrique contient des informations sur la prise en charge de [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour les contrôles standard dans les applications développées pour les frameworks [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32 et Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="92e2f-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32, and Windows Forms frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="92e2f-106">Contrôles Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="92e2f-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="92e2f-107">Tous les éléments du contrôle [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] qui fournissent des informations ou une prise en charge pour l’interaction utilisateur disposent d’une prise en charge native complète de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92e2f-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="92e2f-108">D’autres éléments, tels que les panneaux, ne sont pas visibles par [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92e2f-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="92e2f-109">Contrôles Win32</span><span class="sxs-lookup"><span data-stu-id="92e2f-109">Win32 Controls</span></span>  
 <span data-ttu-id="92e2f-110">La plupart des contrôles Win32 sont exposés à des [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] via des fournisseurs côté client dans UIAutomationClientsideProviders. dll.</span><span class="sxs-lookup"><span data-stu-id="92e2f-110">Most Win32 controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="92e2f-111">Cet assembly est inscrit automatiquement pour être utilisé avec les applications clientes UI Automation.</span><span class="sxs-lookup"><span data-stu-id="92e2f-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="92e2f-112">La prise en charge complète n’est fournie que pour les contrôles de la version 6 de *ComCtrl32. dll*.</span><span class="sxs-lookup"><span data-stu-id="92e2f-112">Full support is provided only for controls from version 6 of *ComCtrl32.dll*.</span></span>  
  
 <span data-ttu-id="92e2f-113">Les contrôles suivants sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="92e2f-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="92e2f-114">Nom de classe</span><span class="sxs-lookup"><span data-stu-id="92e2f-114">Class name</span></span>|<span data-ttu-id="92e2f-115">Type de contrôle</span><span class="sxs-lookup"><span data-stu-id="92e2f-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="92e2f-116">Button</span><span class="sxs-lookup"><span data-stu-id="92e2f-116">Button</span></span>|<span data-ttu-id="92e2f-117">Button</span><span class="sxs-lookup"><span data-stu-id="92e2f-117">Button</span></span>|  
|<span data-ttu-id="92e2f-118">Button</span><span class="sxs-lookup"><span data-stu-id="92e2f-118">Button</span></span>|<span data-ttu-id="92e2f-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="92e2f-119">RadioButton</span></span>|  
|<span data-ttu-id="92e2f-120">Button</span><span class="sxs-lookup"><span data-stu-id="92e2f-120">Button</span></span>|<span data-ttu-id="92e2f-121">Groupe</span><span class="sxs-lookup"><span data-stu-id="92e2f-121">Group</span></span>|  
|<span data-ttu-id="92e2f-122">Button</span><span class="sxs-lookup"><span data-stu-id="92e2f-122">Button</span></span>|<span data-ttu-id="92e2f-123">Case à cocher</span><span class="sxs-lookup"><span data-stu-id="92e2f-123">CheckBox</span></span>|  
|<span data-ttu-id="92e2f-124">Button</span><span class="sxs-lookup"><span data-stu-id="92e2f-124">Button</span></span>|<span data-ttu-id="92e2f-125">Lien hypertexte</span><span class="sxs-lookup"><span data-stu-id="92e2f-125">Hyperlink</span></span>|  
|<span data-ttu-id="92e2f-126">Button</span><span class="sxs-lookup"><span data-stu-id="92e2f-126">Button</span></span>|<span data-ttu-id="92e2f-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="92e2f-127">SplitButton</span></span>|  
|<span data-ttu-id="92e2f-128">Button</span><span class="sxs-lookup"><span data-stu-id="92e2f-128">Button</span></span>|<span data-ttu-id="92e2f-129">Case à cocher</span><span class="sxs-lookup"><span data-stu-id="92e2f-129">CheckBox</span></span>|  
|<span data-ttu-id="92e2f-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="92e2f-130">ComboBoxEx32</span></span>|<span data-ttu-id="92e2f-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="92e2f-131">ComboBox</span></span>|  
|<span data-ttu-id="92e2f-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="92e2f-132">ComboBox</span></span>|<span data-ttu-id="92e2f-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="92e2f-133">ComboBox</span></span>|  
|<span data-ttu-id="92e2f-134">Edit</span><span class="sxs-lookup"><span data-stu-id="92e2f-134">Edit</span></span>|<span data-ttu-id="92e2f-135">Document</span><span class="sxs-lookup"><span data-stu-id="92e2f-135">Document</span></span>|  
|<span data-ttu-id="92e2f-136">Edit</span><span class="sxs-lookup"><span data-stu-id="92e2f-136">Edit</span></span>|<span data-ttu-id="92e2f-137">Edit</span><span class="sxs-lookup"><span data-stu-id="92e2f-137">Edit</span></span>|  
|<span data-ttu-id="92e2f-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="92e2f-138">SysLink</span></span>|<span data-ttu-id="92e2f-139">Lien hypertexte</span><span class="sxs-lookup"><span data-stu-id="92e2f-139">Hyperlink</span></span>|  
|<span data-ttu-id="92e2f-140">Static</span><span class="sxs-lookup"><span data-stu-id="92e2f-140">Static</span></span>|<span data-ttu-id="92e2f-141">Text</span><span class="sxs-lookup"><span data-stu-id="92e2f-141">Text</span></span>|  
|<span data-ttu-id="92e2f-142">Static</span><span class="sxs-lookup"><span data-stu-id="92e2f-142">Static</span></span>|<span data-ttu-id="92e2f-143">Image</span><span class="sxs-lookup"><span data-stu-id="92e2f-143">Image</span></span>|  
|<span data-ttu-id="92e2f-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="92e2f-144">SysIPAddress32</span></span>|<span data-ttu-id="92e2f-145">Personnalisé</span><span class="sxs-lookup"><span data-stu-id="92e2f-145">Custom</span></span>|  
|<span data-ttu-id="92e2f-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="92e2f-146">SysHeader32</span></span>|<span data-ttu-id="92e2f-147">Header/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="92e2f-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="92e2f-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="92e2f-148">SysListView32</span></span>|<span data-ttu-id="92e2f-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="92e2f-149">DataGrid</span></span>|  
|<span data-ttu-id="92e2f-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="92e2f-150">SysListView32</span></span>|<span data-ttu-id="92e2f-151">Liste</span><span class="sxs-lookup"><span data-stu-id="92e2f-151">List</span></span>|  
|<span data-ttu-id="92e2f-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="92e2f-152">ListBox</span></span>|<span data-ttu-id="92e2f-153">Liste</span><span class="sxs-lookup"><span data-stu-id="92e2f-153">List</span></span>|  
|<span data-ttu-id="92e2f-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="92e2f-154">ListBox</span></span>|<span data-ttu-id="92e2f-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="92e2f-155">ListItem</span></span>|  
|<span data-ttu-id="92e2f-156">#32768</span><span class="sxs-lookup"><span data-stu-id="92e2f-156">#32768</span></span>|<span data-ttu-id="92e2f-157">Menu</span><span class="sxs-lookup"><span data-stu-id="92e2f-157">Menu</span></span>|  
|<span data-ttu-id="92e2f-158">#32768</span><span class="sxs-lookup"><span data-stu-id="92e2f-158">#32768</span></span>|<span data-ttu-id="92e2f-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="92e2f-159">MenuItem</span></span>|  
|<span data-ttu-id="92e2f-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="92e2f-160">msctls_progress32</span></span>|<span data-ttu-id="92e2f-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="92e2f-161">ProgressBar</span></span>|  
|<span data-ttu-id="92e2f-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="92e2f-162">RichEdit</span></span>|<span data-ttu-id="92e2f-163">Document.</span><span class="sxs-lookup"><span data-stu-id="92e2f-163">Document.</span></span> <span data-ttu-id="92e2f-164">Consultez la remarque.</span><span class="sxs-lookup"><span data-stu-id="92e2f-164">See note.</span></span>|  
|<span data-ttu-id="92e2f-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="92e2f-165">RichEdit20A</span></span>|<span data-ttu-id="92e2f-166">Document</span><span class="sxs-lookup"><span data-stu-id="92e2f-166">Document</span></span>|  
|<span data-ttu-id="92e2f-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="92e2f-167">RichEdit20W</span></span>|<span data-ttu-id="92e2f-168">Document</span><span class="sxs-lookup"><span data-stu-id="92e2f-168">Document</span></span>|  
|<span data-ttu-id="92e2f-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="92e2f-169">RichEdit50W</span></span>|<span data-ttu-id="92e2f-170">Document</span><span class="sxs-lookup"><span data-stu-id="92e2f-170">Document</span></span>|  
|<span data-ttu-id="92e2f-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="92e2f-171">ScrollBar</span></span>|<span data-ttu-id="92e2f-172">Curseur</span><span class="sxs-lookup"><span data-stu-id="92e2f-172">Slider</span></span>|  
|<span data-ttu-id="92e2f-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="92e2f-173">msctls_trackbar32</span></span>|<span data-ttu-id="92e2f-174">Curseur</span><span class="sxs-lookup"><span data-stu-id="92e2f-174">Slider</span></span>|  
|<span data-ttu-id="92e2f-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="92e2f-175">msctls_updown32</span></span>|<span data-ttu-id="92e2f-176">Spinner</span><span class="sxs-lookup"><span data-stu-id="92e2f-176">Spinner</span></span>|  
|<span data-ttu-id="92e2f-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="92e2f-177">msctls_statusbar32</span></span>|<span data-ttu-id="92e2f-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="92e2f-178">StatusBar</span></span>|  
|<span data-ttu-id="92e2f-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="92e2f-179">SysTabControl32</span></span>|<span data-ttu-id="92e2f-180">Tab</span><span class="sxs-lookup"><span data-stu-id="92e2f-180">Tab</span></span>|  
|<span data-ttu-id="92e2f-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="92e2f-181">SysTabControl32</span></span>|<span data-ttu-id="92e2f-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="92e2f-182">TabItem</span></span>|  
|<span data-ttu-id="92e2f-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="92e2f-183">ToolbarWindow32</span></span>|<span data-ttu-id="92e2f-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="92e2f-184">ToolBar</span></span>|  
|<span data-ttu-id="92e2f-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="92e2f-185">ToolbarWindow32</span></span>|<span data-ttu-id="92e2f-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="92e2f-186">MenuItem</span></span>|  
|<span data-ttu-id="92e2f-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="92e2f-187">ToolbarWindow32</span></span>|<span data-ttu-id="92e2f-188">Button</span><span class="sxs-lookup"><span data-stu-id="92e2f-188">Button</span></span>|  
|<span data-ttu-id="92e2f-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="92e2f-189">ToolbarWindow32</span></span>|<span data-ttu-id="92e2f-190">Case à cocher</span><span class="sxs-lookup"><span data-stu-id="92e2f-190">CheckBox</span></span>|  
|<span data-ttu-id="92e2f-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="92e2f-191">ToolbarWindow32</span></span>|<span data-ttu-id="92e2f-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="92e2f-192">RadioButton</span></span>|  
|<span data-ttu-id="92e2f-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="92e2f-193">ToolbarWindow32</span></span>|<span data-ttu-id="92e2f-194">Séparateur</span><span class="sxs-lookup"><span data-stu-id="92e2f-194">Separator</span></span>|  
|<span data-ttu-id="92e2f-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="92e2f-195">tooltips_class32</span></span>|<span data-ttu-id="92e2f-196">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="92e2f-196">ToolTip</span></span>|  
|<span data-ttu-id="92e2f-197">#32774</span><span class="sxs-lookup"><span data-stu-id="92e2f-197">#32774</span></span>|<span data-ttu-id="92e2f-198">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="92e2f-198">ToolTip</span></span>|  
|<span data-ttu-id="92e2f-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="92e2f-199">ReBarWindow32</span></span>|<span data-ttu-id="92e2f-200">ToolBar</span><span class="sxs-lookup"><span data-stu-id="92e2f-200">Toolbar</span></span>|  
|<span data-ttu-id="92e2f-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="92e2f-201">SysTreeView32</span></span>|<span data-ttu-id="92e2f-202">Arborescence</span><span class="sxs-lookup"><span data-stu-id="92e2f-202">Tree</span></span>|  
|<span data-ttu-id="92e2f-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="92e2f-203">SysTreeView32</span></span>|<span data-ttu-id="92e2f-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="92e2f-204">TreeItem</span></span>|  
  
 <span data-ttu-id="92e2f-205">**Remarque** Le contrôle RichEdit est pris en charge uniquement pour les versions fournies avec Windows Vista (dans RichEd20. dll version 3,1 et ultérieure, et que dans msftedit. dll version 4,1 et versions ultérieures).</span><span class="sxs-lookup"><span data-stu-id="92e2f-205">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="92e2f-206">Les contrôles suivants ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="92e2f-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="92e2f-207">Nom de classe</span><span class="sxs-lookup"><span data-stu-id="92e2f-207">Class name</span></span>|<span data-ttu-id="92e2f-208">Type de contrôle</span><span class="sxs-lookup"><span data-stu-id="92e2f-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="92e2f-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="92e2f-209">SysAnimate32</span></span>|<span data-ttu-id="92e2f-210">Image</span><span class="sxs-lookup"><span data-stu-id="92e2f-210">Image</span></span>|  
|<span data-ttu-id="92e2f-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="92e2f-211">SysPager</span></span>|<span data-ttu-id="92e2f-212">Spinner</span><span class="sxs-lookup"><span data-stu-id="92e2f-212">Spinner</span></span>|  
|<span data-ttu-id="92e2f-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="92e2f-213">SysDateTimePick32</span></span>|<span data-ttu-id="92e2f-214">Personnalisé</span><span class="sxs-lookup"><span data-stu-id="92e2f-214">Custom</span></span>|  
|<span data-ttu-id="92e2f-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="92e2f-215">SysMonthCal32</span></span>|<span data-ttu-id="92e2f-216">Calendrier</span><span class="sxs-lookup"><span data-stu-id="92e2f-216">Calendar</span></span>|  
|<span data-ttu-id="92e2f-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="92e2f-217">MS_WINNOTE</span></span>|<span data-ttu-id="92e2f-218">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="92e2f-218">Tooltip</span></span>|  
|<span data-ttu-id="92e2f-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="92e2f-219">VBBubble</span></span>|<span data-ttu-id="92e2f-220">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="92e2f-220">Tooltip</span></span>|  
|<span data-ttu-id="92e2f-221">ScrollBar (quand il est utilisé comme contrôle autonome)</span><span class="sxs-lookup"><span data-stu-id="92e2f-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="92e2f-222">Curseur</span><span class="sxs-lookup"><span data-stu-id="92e2f-222">Slider</span></span>|  
|<span data-ttu-id="92e2f-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="92e2f-223">SuperGrid</span></span>|<span data-ttu-id="92e2f-224">Personnalisé</span><span class="sxs-lookup"><span data-stu-id="92e2f-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="92e2f-225">Contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="92e2f-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="92e2f-226">Les contrôles Windows Forms sont exposés à des [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] via des fournisseurs côté client dans UIAutomationClientsideProviders. dll.</span><span class="sxs-lookup"><span data-stu-id="92e2f-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="92e2f-227">Cet assembly est inscrit automatiquement pour être utilisé avec les applications clientes UI Automation.</span><span class="sxs-lookup"><span data-stu-id="92e2f-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="92e2f-228">En général, les contrôles Windows Forms qui sont des wrappers managés pour les contrôles communs Win32 sont pris en charge par les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92e2f-228">Typically, Windows Forms controls that are managed wrappers for Win32 common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="92e2f-229">Les contrôles suivants sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="92e2f-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="92e2f-230">Nom de classe</span><span class="sxs-lookup"><span data-stu-id="92e2f-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="92e2f-231">Button</span><span class="sxs-lookup"><span data-stu-id="92e2f-231">Button</span></span>|  
|<span data-ttu-id="92e2f-232">Case à cocher</span><span class="sxs-lookup"><span data-stu-id="92e2f-232">CheckBox</span></span>|  
|<span data-ttu-id="92e2f-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="92e2f-233">CheckedListBox</span></span>|  
|<span data-ttu-id="92e2f-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="92e2f-234">ColorDialog</span></span>|  
|<span data-ttu-id="92e2f-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="92e2f-235">ComboBox</span></span>|  
|<span data-ttu-id="92e2f-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="92e2f-236">FolderBrowser</span></span>|  
|<span data-ttu-id="92e2f-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="92e2f-237">FontDialog</span></span>|  
|<span data-ttu-id="92e2f-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="92e2f-238">GroupBox</span></span>|  
|<span data-ttu-id="92e2f-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="92e2f-239">HscrollBar</span></span>|  
|<span data-ttu-id="92e2f-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="92e2f-240">ImageList</span></span>|  
|<span data-ttu-id="92e2f-241">Ajouter des contrôles</span><span class="sxs-lookup"><span data-stu-id="92e2f-241">Label</span></span>|  
|<span data-ttu-id="92e2f-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="92e2f-242">ListBox</span></span>|  
|<span data-ttu-id="92e2f-243">Affichage de liste</span><span class="sxs-lookup"><span data-stu-id="92e2f-243">ListView</span></span>|  
|<span data-ttu-id="92e2f-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="92e2f-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="92e2f-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="92e2f-245">MonthCalendar</span></span>|  
|<span data-ttu-id="92e2f-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="92e2f-246">NotifyIcon</span></span>|  
|<span data-ttu-id="92e2f-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="92e2f-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="92e2f-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="92e2f-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="92e2f-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="92e2f-249">PrintDialog</span></span>|  
|<span data-ttu-id="92e2f-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="92e2f-250">ProgressBar</span></span>|  
|<span data-ttu-id="92e2f-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="92e2f-251">RadioButton</span></span>|  
|<span data-ttu-id="92e2f-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="92e2f-252">RichTextBox</span></span>|  
|<span data-ttu-id="92e2f-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="92e2f-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="92e2f-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="92e2f-254">ScrollableControl</span></span>|  
|<span data-ttu-id="92e2f-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="92e2f-255">SoundPlayer</span></span>|  
|<span data-ttu-id="92e2f-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="92e2f-256">StatusBar</span></span>|  
|<span data-ttu-id="92e2f-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="92e2f-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="92e2f-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="92e2f-258">TextBox</span></span>|  
|<span data-ttu-id="92e2f-259">Minuteur</span><span class="sxs-lookup"><span data-stu-id="92e2f-259">Timer</span></span>|  
|<span data-ttu-id="92e2f-260">ToolBar</span><span class="sxs-lookup"><span data-stu-id="92e2f-260">Toolbar</span></span>|  
|<span data-ttu-id="92e2f-261">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="92e2f-261">ToolTip</span></span>|  
|<span data-ttu-id="92e2f-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="92e2f-262">TrackBar</span></span>|  
|<span data-ttu-id="92e2f-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="92e2f-263">TreeView</span></span>|  
|<span data-ttu-id="92e2f-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="92e2f-264">VscrollBar</span></span>|  
|<span data-ttu-id="92e2f-265">Navigateur web</span><span class="sxs-lookup"><span data-stu-id="92e2f-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="92e2f-266">Les contrôles suivants sont exposés à [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] uniquement par le biais de leur prise en charge de Microsoft Active Accessibility.</span><span class="sxs-lookup"><span data-stu-id="92e2f-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="92e2f-267">Certaines fonctionnalités ne sont peut-être pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="92e2f-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="92e2f-268">Nom du contrôle</span><span class="sxs-lookup"><span data-stu-id="92e2f-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="92e2f-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="92e2f-269">BindingSource</span></span>|  
|<span data-ttu-id="92e2f-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="92e2f-270">DataGrid</span></span>|  
|<span data-ttu-id="92e2f-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="92e2f-271">DataGridView</span></span>|  
|<span data-ttu-id="92e2f-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="92e2f-272">DataNavigator</span></span>|  
|<span data-ttu-id="92e2f-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="92e2f-273">DomainUpDown</span></span>|  
|<span data-ttu-id="92e2f-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="92e2f-274">ErrorProvider</span></span>|  
|<span data-ttu-id="92e2f-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="92e2f-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="92e2f-276">Formulaire</span><span class="sxs-lookup"><span data-stu-id="92e2f-276">Form</span></span>|  
|<span data-ttu-id="92e2f-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="92e2f-277">LinkLabel</span></span>|  
|<span data-ttu-id="92e2f-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="92e2f-278">HelpProvider</span></span>|  
|<span data-ttu-id="92e2f-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="92e2f-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="92e2f-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="92e2f-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="92e2f-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="92e2f-281">NumericUpDown</span></span>|  
|<span data-ttu-id="92e2f-282">Volet</span><span class="sxs-lookup"><span data-stu-id="92e2f-282">Panel</span></span>|  
|<span data-ttu-id="92e2f-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="92e2f-283">PictureBox</span></span>|  
|<span data-ttu-id="92e2f-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="92e2f-284">PrintDocument</span></span>|  
|<span data-ttu-id="92e2f-285">PrintPreviewControl</span><span class="sxs-lookup"><span data-stu-id="92e2f-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="92e2f-286">PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="92e2f-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="92e2f-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="92e2f-287">PropertyGrid</span></span>|  
|<span data-ttu-id="92e2f-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="92e2f-288">UserControl</span></span>|  
|<span data-ttu-id="92e2f-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="92e2f-289">ToolStrip</span></span>|  
|<span data-ttu-id="92e2f-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="92e2f-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="92e2f-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="92e2f-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="92e2f-292">Séparation</span><span class="sxs-lookup"><span data-stu-id="92e2f-292">Splitter</span></span>|  
|<span data-ttu-id="92e2f-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="92e2f-293">RaftingContainer</span></span>|  
|<span data-ttu-id="92e2f-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="92e2f-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="92e2f-295">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92e2f-295">See also</span></span>

- [<span data-ttu-id="92e2f-296">UI Automation Control Types</span><span class="sxs-lookup"><span data-stu-id="92e2f-296">UI Automation Control Types</span></span>](ui-automation-control-types.md)
