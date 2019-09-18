---
title: Prise en charge d'UI Automation pour les contrôles standard
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 6cbf31c8a1cdf6e853e56445d22f4a7513bd1859
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71041998"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="45fd5-102">Prise en charge d'UI Automation pour les contrôles standard</span><span class="sxs-lookup"><span data-stu-id="45fd5-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="45fd5-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="45fd5-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="45fd5-104">Pour obtenir les informations les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]plus récentes [sur, consultez API Windows Automation: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="45fd5-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="45fd5-105">Cette rubrique contient des informations sur la prise en charge d’ [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour les contrôles standard dans les applications développées pour les infrastructures [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]et [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="45fd5-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="45fd5-106">Contrôles Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="45fd5-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="45fd5-107">Tous les éléments du contrôle [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] qui fournissent des informations ou une prise en charge pour l’interaction utilisateur disposent d’une prise en charge native complète de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="45fd5-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="45fd5-108">D’autres éléments, tels que les panneaux, ne sont pas visibles par [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="45fd5-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="45fd5-109">Contrôles Win32</span><span class="sxs-lookup"><span data-stu-id="45fd5-109">Win32 Controls</span></span>  
 <span data-ttu-id="45fd5-110">La plupart des contrôles [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] sont exposés à [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] via des fournisseurs côté client dans UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="45fd5-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="45fd5-111">Cet assembly est inscrit automatiquement pour être utilisé avec les applications clientes UI Automation.</span><span class="sxs-lookup"><span data-stu-id="45fd5-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="45fd5-112">La prise en charge complète n’est fournie que pour les contrôles de la version 6 de ComCtrl32.dll (disponible avec [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] et les versions ultérieures).</span><span class="sxs-lookup"><span data-stu-id="45fd5-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="45fd5-113">Les contrôles suivants sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="45fd5-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="45fd5-114">Nom de classe</span><span class="sxs-lookup"><span data-stu-id="45fd5-114">Class name</span></span>|<span data-ttu-id="45fd5-115">Type de contrôle</span><span class="sxs-lookup"><span data-stu-id="45fd5-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="45fd5-116">Bouton</span><span class="sxs-lookup"><span data-stu-id="45fd5-116">Button</span></span>|<span data-ttu-id="45fd5-117">Bouton</span><span class="sxs-lookup"><span data-stu-id="45fd5-117">Button</span></span>|  
|<span data-ttu-id="45fd5-118">Bouton</span><span class="sxs-lookup"><span data-stu-id="45fd5-118">Button</span></span>|<span data-ttu-id="45fd5-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="45fd5-119">RadioButton</span></span>|  
|<span data-ttu-id="45fd5-120">Bouton</span><span class="sxs-lookup"><span data-stu-id="45fd5-120">Button</span></span>|<span data-ttu-id="45fd5-121">Regrouper</span><span class="sxs-lookup"><span data-stu-id="45fd5-121">Group</span></span>|  
|<span data-ttu-id="45fd5-122">Bouton</span><span class="sxs-lookup"><span data-stu-id="45fd5-122">Button</span></span>|<span data-ttu-id="45fd5-123">Case à cocher</span><span class="sxs-lookup"><span data-stu-id="45fd5-123">CheckBox</span></span>|  
|<span data-ttu-id="45fd5-124">Bouton</span><span class="sxs-lookup"><span data-stu-id="45fd5-124">Button</span></span>|<span data-ttu-id="45fd5-125">Lien hypertexte</span><span class="sxs-lookup"><span data-stu-id="45fd5-125">Hyperlink</span></span>|  
|<span data-ttu-id="45fd5-126">Bouton</span><span class="sxs-lookup"><span data-stu-id="45fd5-126">Button</span></span>|<span data-ttu-id="45fd5-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="45fd5-127">SplitButton</span></span>|  
|<span data-ttu-id="45fd5-128">Bouton</span><span class="sxs-lookup"><span data-stu-id="45fd5-128">Button</span></span>|<span data-ttu-id="45fd5-129">Case à cocher</span><span class="sxs-lookup"><span data-stu-id="45fd5-129">CheckBox</span></span>|  
|<span data-ttu-id="45fd5-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="45fd5-130">ComboBoxEx32</span></span>|<span data-ttu-id="45fd5-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="45fd5-131">ComboBox</span></span>|  
|<span data-ttu-id="45fd5-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="45fd5-132">ComboBox</span></span>|<span data-ttu-id="45fd5-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="45fd5-133">ComboBox</span></span>|  
|<span data-ttu-id="45fd5-134">Modifier</span><span class="sxs-lookup"><span data-stu-id="45fd5-134">Edit</span></span>|<span data-ttu-id="45fd5-135">Document</span><span class="sxs-lookup"><span data-stu-id="45fd5-135">Document</span></span>|  
|<span data-ttu-id="45fd5-136">Modifier</span><span class="sxs-lookup"><span data-stu-id="45fd5-136">Edit</span></span>|<span data-ttu-id="45fd5-137">Modifier</span><span class="sxs-lookup"><span data-stu-id="45fd5-137">Edit</span></span>|  
|<span data-ttu-id="45fd5-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="45fd5-138">SysLink</span></span>|<span data-ttu-id="45fd5-139">Lien hypertexte</span><span class="sxs-lookup"><span data-stu-id="45fd5-139">Hyperlink</span></span>|  
|<span data-ttu-id="45fd5-140">statique</span><span class="sxs-lookup"><span data-stu-id="45fd5-140">Static</span></span>|<span data-ttu-id="45fd5-141">Text</span><span class="sxs-lookup"><span data-stu-id="45fd5-141">Text</span></span>|  
|<span data-ttu-id="45fd5-142">Statique</span><span class="sxs-lookup"><span data-stu-id="45fd5-142">Static</span></span>|<span data-ttu-id="45fd5-143">Image</span><span class="sxs-lookup"><span data-stu-id="45fd5-143">Image</span></span>|  
|<span data-ttu-id="45fd5-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="45fd5-144">SysIPAddress32</span></span>|<span data-ttu-id="45fd5-145">Personnalisé</span><span class="sxs-lookup"><span data-stu-id="45fd5-145">Custom</span></span>|  
|<span data-ttu-id="45fd5-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="45fd5-146">SysHeader32</span></span>|<span data-ttu-id="45fd5-147">Header/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="45fd5-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="45fd5-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="45fd5-148">SysListView32</span></span>|<span data-ttu-id="45fd5-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="45fd5-149">DataGrid</span></span>|  
|<span data-ttu-id="45fd5-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="45fd5-150">SysListView32</span></span>|<span data-ttu-id="45fd5-151">Énumérer</span><span class="sxs-lookup"><span data-stu-id="45fd5-151">List</span></span>|  
|<span data-ttu-id="45fd5-152">Listbox</span><span class="sxs-lookup"><span data-stu-id="45fd5-152">ListBox</span></span>|<span data-ttu-id="45fd5-153">Énumérer</span><span class="sxs-lookup"><span data-stu-id="45fd5-153">List</span></span>|  
|<span data-ttu-id="45fd5-154">Listbox</span><span class="sxs-lookup"><span data-stu-id="45fd5-154">ListBox</span></span>|<span data-ttu-id="45fd5-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="45fd5-155">ListItem</span></span>|  
|<span data-ttu-id="45fd5-156">#32768</span><span class="sxs-lookup"><span data-stu-id="45fd5-156">#32768</span></span>|<span data-ttu-id="45fd5-157">Menu</span><span class="sxs-lookup"><span data-stu-id="45fd5-157">Menu</span></span>|  
|<span data-ttu-id="45fd5-158">#32768</span><span class="sxs-lookup"><span data-stu-id="45fd5-158">#32768</span></span>|<span data-ttu-id="45fd5-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="45fd5-159">MenuItem</span></span>|  
|<span data-ttu-id="45fd5-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="45fd5-160">msctls_progress32</span></span>|<span data-ttu-id="45fd5-161">Barre de progression</span><span class="sxs-lookup"><span data-stu-id="45fd5-161">ProgressBar</span></span>|  
|<span data-ttu-id="45fd5-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="45fd5-162">RichEdit</span></span>|<span data-ttu-id="45fd5-163">Document.</span><span class="sxs-lookup"><span data-stu-id="45fd5-163">Document.</span></span> <span data-ttu-id="45fd5-164">Consultez la remarque.</span><span class="sxs-lookup"><span data-stu-id="45fd5-164">See note.</span></span>|  
|<span data-ttu-id="45fd5-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="45fd5-165">RichEdit20A</span></span>|<span data-ttu-id="45fd5-166">Document</span><span class="sxs-lookup"><span data-stu-id="45fd5-166">Document</span></span>|  
|<span data-ttu-id="45fd5-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="45fd5-167">RichEdit20W</span></span>|<span data-ttu-id="45fd5-168">Document</span><span class="sxs-lookup"><span data-stu-id="45fd5-168">Document</span></span>|  
|<span data-ttu-id="45fd5-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="45fd5-169">RichEdit50W</span></span>|<span data-ttu-id="45fd5-170">Document</span><span class="sxs-lookup"><span data-stu-id="45fd5-170">Document</span></span>|  
|<span data-ttu-id="45fd5-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="45fd5-171">ScrollBar</span></span>|<span data-ttu-id="45fd5-172">Curseur</span><span class="sxs-lookup"><span data-stu-id="45fd5-172">Slider</span></span>|  
|<span data-ttu-id="45fd5-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="45fd5-173">msctls_trackbar32</span></span>|<span data-ttu-id="45fd5-174">Curseur</span><span class="sxs-lookup"><span data-stu-id="45fd5-174">Slider</span></span>|  
|<span data-ttu-id="45fd5-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="45fd5-175">msctls_updown32</span></span>|<span data-ttu-id="45fd5-176">Spinner</span><span class="sxs-lookup"><span data-stu-id="45fd5-176">Spinner</span></span>|  
|<span data-ttu-id="45fd5-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="45fd5-177">msctls_statusbar32</span></span>|<span data-ttu-id="45fd5-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="45fd5-178">StatusBar</span></span>|  
|<span data-ttu-id="45fd5-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="45fd5-179">SysTabControl32</span></span>|<span data-ttu-id="45fd5-180">Onglet</span><span class="sxs-lookup"><span data-stu-id="45fd5-180">Tab</span></span>|  
|<span data-ttu-id="45fd5-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="45fd5-181">SysTabControl32</span></span>|<span data-ttu-id="45fd5-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="45fd5-182">TabItem</span></span>|  
|<span data-ttu-id="45fd5-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="45fd5-183">ToolbarWindow32</span></span>|<span data-ttu-id="45fd5-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="45fd5-184">ToolBar</span></span>|  
|<span data-ttu-id="45fd5-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="45fd5-185">ToolbarWindow32</span></span>|<span data-ttu-id="45fd5-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="45fd5-186">MenuItem</span></span>|  
|<span data-ttu-id="45fd5-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="45fd5-187">ToolbarWindow32</span></span>|<span data-ttu-id="45fd5-188">Bouton</span><span class="sxs-lookup"><span data-stu-id="45fd5-188">Button</span></span>|  
|<span data-ttu-id="45fd5-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="45fd5-189">ToolbarWindow32</span></span>|<span data-ttu-id="45fd5-190">Case à cocher</span><span class="sxs-lookup"><span data-stu-id="45fd5-190">CheckBox</span></span>|  
|<span data-ttu-id="45fd5-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="45fd5-191">ToolbarWindow32</span></span>|<span data-ttu-id="45fd5-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="45fd5-192">RadioButton</span></span>|  
|<span data-ttu-id="45fd5-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="45fd5-193">ToolbarWindow32</span></span>|<span data-ttu-id="45fd5-194">Séparateur</span><span class="sxs-lookup"><span data-stu-id="45fd5-194">Separator</span></span>|  
|<span data-ttu-id="45fd5-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="45fd5-195">tooltips_class32</span></span>|<span data-ttu-id="45fd5-196">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="45fd5-196">ToolTip</span></span>|  
|<span data-ttu-id="45fd5-197">#32774</span><span class="sxs-lookup"><span data-stu-id="45fd5-197">#32774</span></span>|<span data-ttu-id="45fd5-198">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="45fd5-198">ToolTip</span></span>|  
|<span data-ttu-id="45fd5-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="45fd5-199">ReBarWindow32</span></span>|<span data-ttu-id="45fd5-200">ToolBar</span><span class="sxs-lookup"><span data-stu-id="45fd5-200">Toolbar</span></span>|  
|<span data-ttu-id="45fd5-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="45fd5-201">SysTreeView32</span></span>|<span data-ttu-id="45fd5-202">Arborescence</span><span class="sxs-lookup"><span data-stu-id="45fd5-202">Tree</span></span>|  
|<span data-ttu-id="45fd5-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="45fd5-203">SysTreeView32</span></span>|<span data-ttu-id="45fd5-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="45fd5-204">TreeItem</span></span>|  
  
 <span data-ttu-id="45fd5-205">**Remarque** Le contrôle RichEdit est pris en charge uniquement pour les versions fournies avec [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (dans RichEd20.dll version 3.1 et version ultérieure, ainsi que dans MsftEdit.dll version 4.1 et version ultérieure).</span><span class="sxs-lookup"><span data-stu-id="45fd5-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="45fd5-206">Les contrôles suivants ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="45fd5-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="45fd5-207">Nom de classe</span><span class="sxs-lookup"><span data-stu-id="45fd5-207">Class name</span></span>|<span data-ttu-id="45fd5-208">Type de contrôle</span><span class="sxs-lookup"><span data-stu-id="45fd5-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="45fd5-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="45fd5-209">SysAnimate32</span></span>|<span data-ttu-id="45fd5-210">Image</span><span class="sxs-lookup"><span data-stu-id="45fd5-210">Image</span></span>|  
|<span data-ttu-id="45fd5-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="45fd5-211">SysPager</span></span>|<span data-ttu-id="45fd5-212">Spinner</span><span class="sxs-lookup"><span data-stu-id="45fd5-212">Spinner</span></span>|  
|<span data-ttu-id="45fd5-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="45fd5-213">SysDateTimePick32</span></span>|<span data-ttu-id="45fd5-214">Personnalisé</span><span class="sxs-lookup"><span data-stu-id="45fd5-214">Custom</span></span>|  
|<span data-ttu-id="45fd5-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="45fd5-215">SysMonthCal32</span></span>|<span data-ttu-id="45fd5-216">Calendrier</span><span class="sxs-lookup"><span data-stu-id="45fd5-216">Calendar</span></span>|  
|<span data-ttu-id="45fd5-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="45fd5-217">MS_WINNOTE</span></span>|<span data-ttu-id="45fd5-218">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="45fd5-218">Tooltip</span></span>|  
|<span data-ttu-id="45fd5-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="45fd5-219">VBBubble</span></span>|<span data-ttu-id="45fd5-220">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="45fd5-220">Tooltip</span></span>|  
|<span data-ttu-id="45fd5-221">ScrollBar (quand il est utilisé comme contrôle autonome)</span><span class="sxs-lookup"><span data-stu-id="45fd5-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="45fd5-222">Curseur</span><span class="sxs-lookup"><span data-stu-id="45fd5-222">Slider</span></span>|  
|<span data-ttu-id="45fd5-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="45fd5-223">SuperGrid</span></span>|<span data-ttu-id="45fd5-224">Personnalisé</span><span class="sxs-lookup"><span data-stu-id="45fd5-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="45fd5-225">contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="45fd5-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="45fd5-226">Les contrôles Windows Forms sont exposés [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] à via des fournisseurs côté client dans UIAutomationClientsideProviders. dll.</span><span class="sxs-lookup"><span data-stu-id="45fd5-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="45fd5-227">Cet assembly est inscrit automatiquement pour être utilisé avec les applications clientes UI Automation.</span><span class="sxs-lookup"><span data-stu-id="45fd5-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="45fd5-228">En général, les contrôles Windows Forms qui sont des wrappers managés pour [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]contrôles communs sont pris en charge par.</span><span class="sxs-lookup"><span data-stu-id="45fd5-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="45fd5-229">Les contrôles suivants sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="45fd5-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="45fd5-230">Nom de classe</span><span class="sxs-lookup"><span data-stu-id="45fd5-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="45fd5-231">Bouton</span><span class="sxs-lookup"><span data-stu-id="45fd5-231">Button</span></span>|  
|<span data-ttu-id="45fd5-232">Case à cocher</span><span class="sxs-lookup"><span data-stu-id="45fd5-232">CheckBox</span></span>|  
|<span data-ttu-id="45fd5-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="45fd5-233">CheckedListBox</span></span>|  
|<span data-ttu-id="45fd5-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="45fd5-234">ColorDialog</span></span>|  
|<span data-ttu-id="45fd5-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="45fd5-235">ComboBox</span></span>|  
|<span data-ttu-id="45fd5-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="45fd5-236">FolderBrowser</span></span>|  
|<span data-ttu-id="45fd5-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="45fd5-237">FontDialog</span></span>|  
|<span data-ttu-id="45fd5-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="45fd5-238">GroupBox</span></span>|  
|<span data-ttu-id="45fd5-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="45fd5-239">HscrollBar</span></span>|  
|<span data-ttu-id="45fd5-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="45fd5-240">ImageList</span></span>|  
|<span data-ttu-id="45fd5-241">Etiquette</span><span class="sxs-lookup"><span data-stu-id="45fd5-241">Label</span></span>|  
|<span data-ttu-id="45fd5-242">Listbox</span><span class="sxs-lookup"><span data-stu-id="45fd5-242">ListBox</span></span>|  
|<span data-ttu-id="45fd5-243">Affichage de liste</span><span class="sxs-lookup"><span data-stu-id="45fd5-243">ListView</span></span>|  
|<span data-ttu-id="45fd5-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="45fd5-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="45fd5-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="45fd5-245">MonthCalendar</span></span>|  
|<span data-ttu-id="45fd5-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="45fd5-246">NotifyIcon</span></span>|  
|<span data-ttu-id="45fd5-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="45fd5-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="45fd5-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="45fd5-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="45fd5-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="45fd5-249">PrintDialog</span></span>|  
|<span data-ttu-id="45fd5-250">Barre de progression</span><span class="sxs-lookup"><span data-stu-id="45fd5-250">ProgressBar</span></span>|  
|<span data-ttu-id="45fd5-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="45fd5-251">RadioButton</span></span>|  
|<span data-ttu-id="45fd5-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="45fd5-252">RichTextBox</span></span>|  
|<span data-ttu-id="45fd5-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="45fd5-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="45fd5-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="45fd5-254">ScrollableControl</span></span>|  
|<span data-ttu-id="45fd5-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="45fd5-255">SoundPlayer</span></span>|  
|<span data-ttu-id="45fd5-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="45fd5-256">StatusBar</span></span>|  
|<span data-ttu-id="45fd5-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="45fd5-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="45fd5-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="45fd5-258">TextBox</span></span>|  
|<span data-ttu-id="45fd5-259">Minuterie</span><span class="sxs-lookup"><span data-stu-id="45fd5-259">Timer</span></span>|  
|<span data-ttu-id="45fd5-260">ToolBar</span><span class="sxs-lookup"><span data-stu-id="45fd5-260">Toolbar</span></span>|  
|<span data-ttu-id="45fd5-261">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="45fd5-261">ToolTip</span></span>|  
|<span data-ttu-id="45fd5-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="45fd5-262">TrackBar</span></span>|  
|<span data-ttu-id="45fd5-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="45fd5-263">TreeView</span></span>|  
|<span data-ttu-id="45fd5-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="45fd5-264">VscrollBar</span></span>|  
|<span data-ttu-id="45fd5-265">Navigateur web</span><span class="sxs-lookup"><span data-stu-id="45fd5-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="45fd5-266">Les contrôles suivants sont exposés à [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] uniquement via leur prise en charge de Microsoft Active Accessibility.</span><span class="sxs-lookup"><span data-stu-id="45fd5-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="45fd5-267">Certaines fonctionnalités ne sont peut-être pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="45fd5-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="45fd5-268">Nom du contrôle</span><span class="sxs-lookup"><span data-stu-id="45fd5-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="45fd5-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="45fd5-269">BindingSource</span></span>|  
|<span data-ttu-id="45fd5-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="45fd5-270">DataGrid</span></span>|  
|<span data-ttu-id="45fd5-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="45fd5-271">DataGridView</span></span>|  
|<span data-ttu-id="45fd5-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="45fd5-272">DataNavigator</span></span>|  
|<span data-ttu-id="45fd5-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="45fd5-273">DomainUpDown</span></span>|  
|<span data-ttu-id="45fd5-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="45fd5-274">ErrorProvider</span></span>|  
|<span data-ttu-id="45fd5-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="45fd5-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="45fd5-276">Formulaire</span><span class="sxs-lookup"><span data-stu-id="45fd5-276">Form</span></span>|  
|<span data-ttu-id="45fd5-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="45fd5-277">LinkLabel</span></span>|  
|<span data-ttu-id="45fd5-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="45fd5-278">HelpProvider</span></span>|  
|<span data-ttu-id="45fd5-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="45fd5-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="45fd5-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="45fd5-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="45fd5-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="45fd5-281">NumericUpDown</span></span>|  
|<span data-ttu-id="45fd5-282">Volet</span><span class="sxs-lookup"><span data-stu-id="45fd5-282">Panel</span></span>|  
|<span data-ttu-id="45fd5-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="45fd5-283">PictureBox</span></span>|  
|<span data-ttu-id="45fd5-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="45fd5-284">PrintDocument</span></span>|  
|<span data-ttu-id="45fd5-285">PrintPreviewControl</span><span class="sxs-lookup"><span data-stu-id="45fd5-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="45fd5-286">PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="45fd5-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="45fd5-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="45fd5-287">PropertyGrid</span></span>|  
|<span data-ttu-id="45fd5-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="45fd5-288">UserControl</span></span>|  
|<span data-ttu-id="45fd5-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="45fd5-289">ToolStrip</span></span>|  
|<span data-ttu-id="45fd5-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="45fd5-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="45fd5-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="45fd5-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="45fd5-292">Séparateur</span><span class="sxs-lookup"><span data-stu-id="45fd5-292">Splitter</span></span>|  
|<span data-ttu-id="45fd5-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="45fd5-293">RaftingContainer</span></span>|  
|<span data-ttu-id="45fd5-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="45fd5-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="45fd5-295">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45fd5-295">See also</span></span>

- [<span data-ttu-id="45fd5-296">Types de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="45fd5-296">UI Automation Control Types</span></span>](ui-automation-control-types.md)
