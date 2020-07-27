---
title: Prise en charge d'UI Automation pour les contrôles standard
description: Obtenir des informations sur la prise en charge d’UI Automation pour les contrôles standard dans les applications développées pour Windows Presentation Foundation (WPF), Win32 et Windows Forms.
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 17916a6978008439e91caae00d8b6f26045f9018
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166118"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="1ecce-103">Prise en charge d'UI Automation pour les contrôles standard</span><span class="sxs-lookup"><span data-stu-id="1ecce-103">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="1ecce-104">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="1ecce-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="1ecce-105">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="1ecce-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="1ecce-106">Cette rubrique contient des informations sur [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] la prise en charge des contrôles standard dans les applications développées pour les [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] frameworks, Win32 et Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1ecce-106">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32, and Windows Forms frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="1ecce-107">Contrôles Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="1ecce-107">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="1ecce-108">Tous les éléments du contrôle [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] qui fournissent des informations ou une prise en charge pour l’interaction utilisateur disposent d’une prise en charge native complète de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1ecce-108">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="1ecce-109">D’autres éléments, tels que les panneaux, ne sont pas visibles par [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1ecce-109">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>
## <a name="win32-controls"></a><span data-ttu-id="1ecce-110">Contrôles Win32</span><span class="sxs-lookup"><span data-stu-id="1ecce-110">Win32 Controls</span></span>  
 <span data-ttu-id="1ecce-111">La plupart des contrôles Win32 sont exposés à [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] via des fournisseurs côté client dans UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="1ecce-111">Most Win32 controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="1ecce-112">Cet assembly est inscrit automatiquement pour être utilisé avec les applications clientes UI Automation.</span><span class="sxs-lookup"><span data-stu-id="1ecce-112">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="1ecce-113">La prise en charge complète n’est fournie que pour les contrôles de la version 6 de *ComCtrl32.dll*.</span><span class="sxs-lookup"><span data-stu-id="1ecce-113">Full support is provided only for controls from version 6 of *ComCtrl32.dll*.</span></span>  
  
 <span data-ttu-id="1ecce-114">Les contrôles suivants sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="1ecce-114">The following controls are supported.</span></span>  
  
|<span data-ttu-id="1ecce-115">Nom de classe</span><span class="sxs-lookup"><span data-stu-id="1ecce-115">Class name</span></span>|<span data-ttu-id="1ecce-116">Type de contrôle</span><span class="sxs-lookup"><span data-stu-id="1ecce-116">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="1ecce-117">Button</span><span class="sxs-lookup"><span data-stu-id="1ecce-117">Button</span></span>|<span data-ttu-id="1ecce-118">Button</span><span class="sxs-lookup"><span data-stu-id="1ecce-118">Button</span></span>|  
|<span data-ttu-id="1ecce-119">Button</span><span class="sxs-lookup"><span data-stu-id="1ecce-119">Button</span></span>|<span data-ttu-id="1ecce-120">RadioButton</span><span class="sxs-lookup"><span data-stu-id="1ecce-120">RadioButton</span></span>|  
|<span data-ttu-id="1ecce-121">Bouton</span><span class="sxs-lookup"><span data-stu-id="1ecce-121">Button</span></span>|<span data-ttu-id="1ecce-122">Groupe</span><span class="sxs-lookup"><span data-stu-id="1ecce-122">Group</span></span>|  
|<span data-ttu-id="1ecce-123">Bouton</span><span class="sxs-lookup"><span data-stu-id="1ecce-123">Button</span></span>|<span data-ttu-id="1ecce-124">CheckBox</span><span class="sxs-lookup"><span data-stu-id="1ecce-124">CheckBox</span></span>|  
|<span data-ttu-id="1ecce-125">Bouton</span><span class="sxs-lookup"><span data-stu-id="1ecce-125">Button</span></span>|<span data-ttu-id="1ecce-126">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="1ecce-126">Hyperlink</span></span>|  
|<span data-ttu-id="1ecce-127">Bouton</span><span class="sxs-lookup"><span data-stu-id="1ecce-127">Button</span></span>|<span data-ttu-id="1ecce-128">SplitButton</span><span class="sxs-lookup"><span data-stu-id="1ecce-128">SplitButton</span></span>|  
|<span data-ttu-id="1ecce-129">Bouton</span><span class="sxs-lookup"><span data-stu-id="1ecce-129">Button</span></span>|<span data-ttu-id="1ecce-130">CheckBox</span><span class="sxs-lookup"><span data-stu-id="1ecce-130">CheckBox</span></span>|  
|<span data-ttu-id="1ecce-131">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="1ecce-131">ComboBoxEx32</span></span>|<span data-ttu-id="1ecce-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="1ecce-132">ComboBox</span></span>|  
|<span data-ttu-id="1ecce-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="1ecce-133">ComboBox</span></span>|<span data-ttu-id="1ecce-134">ComboBox</span><span class="sxs-lookup"><span data-stu-id="1ecce-134">ComboBox</span></span>|  
|<span data-ttu-id="1ecce-135">Modifier</span><span class="sxs-lookup"><span data-stu-id="1ecce-135">Edit</span></span>|<span data-ttu-id="1ecce-136">Document</span><span class="sxs-lookup"><span data-stu-id="1ecce-136">Document</span></span>|  
|<span data-ttu-id="1ecce-137">Modifier</span><span class="sxs-lookup"><span data-stu-id="1ecce-137">Edit</span></span>|<span data-ttu-id="1ecce-138">Modifier</span><span class="sxs-lookup"><span data-stu-id="1ecce-138">Edit</span></span>|  
|<span data-ttu-id="1ecce-139">SysLink</span><span class="sxs-lookup"><span data-stu-id="1ecce-139">SysLink</span></span>|<span data-ttu-id="1ecce-140">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="1ecce-140">Hyperlink</span></span>|  
|<span data-ttu-id="1ecce-141">statique</span><span class="sxs-lookup"><span data-stu-id="1ecce-141">Static</span></span>|<span data-ttu-id="1ecce-142">Texte</span><span class="sxs-lookup"><span data-stu-id="1ecce-142">Text</span></span>|  
|<span data-ttu-id="1ecce-143">statique</span><span class="sxs-lookup"><span data-stu-id="1ecce-143">Static</span></span>|<span data-ttu-id="1ecce-144">Image</span><span class="sxs-lookup"><span data-stu-id="1ecce-144">Image</span></span>|  
|<span data-ttu-id="1ecce-145">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="1ecce-145">SysIPAddress32</span></span>|<span data-ttu-id="1ecce-146">Personnalisé</span><span class="sxs-lookup"><span data-stu-id="1ecce-146">Custom</span></span>|  
|<span data-ttu-id="1ecce-147">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="1ecce-147">SysHeader32</span></span>|<span data-ttu-id="1ecce-148">Header/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="1ecce-148">Header/HeaderItem</span></span>|  
|<span data-ttu-id="1ecce-149">SysListView32</span><span class="sxs-lookup"><span data-stu-id="1ecce-149">SysListView32</span></span>|<span data-ttu-id="1ecce-150">DataGrid</span><span class="sxs-lookup"><span data-stu-id="1ecce-150">DataGrid</span></span>|  
|<span data-ttu-id="1ecce-151">SysListView32</span><span class="sxs-lookup"><span data-stu-id="1ecce-151">SysListView32</span></span>|<span data-ttu-id="1ecce-152">List</span><span class="sxs-lookup"><span data-stu-id="1ecce-152">List</span></span>|  
|<span data-ttu-id="1ecce-153">ListBox</span><span class="sxs-lookup"><span data-stu-id="1ecce-153">ListBox</span></span>|<span data-ttu-id="1ecce-154">List</span><span class="sxs-lookup"><span data-stu-id="1ecce-154">List</span></span>|  
|<span data-ttu-id="1ecce-155">ListBox</span><span class="sxs-lookup"><span data-stu-id="1ecce-155">ListBox</span></span>|<span data-ttu-id="1ecce-156">ListItem</span><span class="sxs-lookup"><span data-stu-id="1ecce-156">ListItem</span></span>|  
|<span data-ttu-id="1ecce-157">#32768</span><span class="sxs-lookup"><span data-stu-id="1ecce-157">#32768</span></span>|<span data-ttu-id="1ecce-158">Menu</span><span class="sxs-lookup"><span data-stu-id="1ecce-158">Menu</span></span>|  
|<span data-ttu-id="1ecce-159">#32768</span><span class="sxs-lookup"><span data-stu-id="1ecce-159">#32768</span></span>|<span data-ttu-id="1ecce-160">MenuItem</span><span class="sxs-lookup"><span data-stu-id="1ecce-160">MenuItem</span></span>|  
|<span data-ttu-id="1ecce-161">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="1ecce-161">msctls_progress32</span></span>|<span data-ttu-id="1ecce-162">Barre de progression</span><span class="sxs-lookup"><span data-stu-id="1ecce-162">ProgressBar</span></span>|  
|<span data-ttu-id="1ecce-163">RichEdit</span><span class="sxs-lookup"><span data-stu-id="1ecce-163">RichEdit</span></span>|<span data-ttu-id="1ecce-164">Document.</span><span class="sxs-lookup"><span data-stu-id="1ecce-164">Document.</span></span> <span data-ttu-id="1ecce-165">Consultez la remarque.</span><span class="sxs-lookup"><span data-stu-id="1ecce-165">See note.</span></span>|  
|<span data-ttu-id="1ecce-166">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="1ecce-166">RichEdit20A</span></span>|<span data-ttu-id="1ecce-167">Document</span><span class="sxs-lookup"><span data-stu-id="1ecce-167">Document</span></span>|  
|<span data-ttu-id="1ecce-168">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="1ecce-168">RichEdit20W</span></span>|<span data-ttu-id="1ecce-169">Document</span><span class="sxs-lookup"><span data-stu-id="1ecce-169">Document</span></span>|  
|<span data-ttu-id="1ecce-170">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="1ecce-170">RichEdit50W</span></span>|<span data-ttu-id="1ecce-171">Document</span><span class="sxs-lookup"><span data-stu-id="1ecce-171">Document</span></span>|  
|<span data-ttu-id="1ecce-172">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="1ecce-172">ScrollBar</span></span>|<span data-ttu-id="1ecce-173">Curseur</span><span class="sxs-lookup"><span data-stu-id="1ecce-173">Slider</span></span>|  
|<span data-ttu-id="1ecce-174">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="1ecce-174">msctls_trackbar32</span></span>|<span data-ttu-id="1ecce-175">Curseur</span><span class="sxs-lookup"><span data-stu-id="1ecce-175">Slider</span></span>|  
|<span data-ttu-id="1ecce-176">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="1ecce-176">msctls_updown32</span></span>|<span data-ttu-id="1ecce-177">Spinner</span><span class="sxs-lookup"><span data-stu-id="1ecce-177">Spinner</span></span>|  
|<span data-ttu-id="1ecce-178">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="1ecce-178">msctls_statusbar32</span></span>|<span data-ttu-id="1ecce-179">StatusBar</span><span class="sxs-lookup"><span data-stu-id="1ecce-179">StatusBar</span></span>|  
|<span data-ttu-id="1ecce-180">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="1ecce-180">SysTabControl32</span></span>|<span data-ttu-id="1ecce-181">Onglet</span><span class="sxs-lookup"><span data-stu-id="1ecce-181">Tab</span></span>|  
|<span data-ttu-id="1ecce-182">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="1ecce-182">SysTabControl32</span></span>|<span data-ttu-id="1ecce-183">TabItem</span><span class="sxs-lookup"><span data-stu-id="1ecce-183">TabItem</span></span>|  
|<span data-ttu-id="1ecce-184">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="1ecce-184">ToolbarWindow32</span></span>|<span data-ttu-id="1ecce-185">ToolBar</span><span class="sxs-lookup"><span data-stu-id="1ecce-185">ToolBar</span></span>|  
|<span data-ttu-id="1ecce-186">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="1ecce-186">ToolbarWindow32</span></span>|<span data-ttu-id="1ecce-187">MenuItem</span><span class="sxs-lookup"><span data-stu-id="1ecce-187">MenuItem</span></span>|  
|<span data-ttu-id="1ecce-188">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="1ecce-188">ToolbarWindow32</span></span>|<span data-ttu-id="1ecce-189">Bouton</span><span class="sxs-lookup"><span data-stu-id="1ecce-189">Button</span></span>|  
|<span data-ttu-id="1ecce-190">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="1ecce-190">ToolbarWindow32</span></span>|<span data-ttu-id="1ecce-191">CheckBox</span><span class="sxs-lookup"><span data-stu-id="1ecce-191">CheckBox</span></span>|  
|<span data-ttu-id="1ecce-192">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="1ecce-192">ToolbarWindow32</span></span>|<span data-ttu-id="1ecce-193">RadioButton</span><span class="sxs-lookup"><span data-stu-id="1ecce-193">RadioButton</span></span>|  
|<span data-ttu-id="1ecce-194">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="1ecce-194">ToolbarWindow32</span></span>|<span data-ttu-id="1ecce-195">Séparateur</span><span class="sxs-lookup"><span data-stu-id="1ecce-195">Separator</span></span>|  
|<span data-ttu-id="1ecce-196">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="1ecce-196">tooltips_class32</span></span>|<span data-ttu-id="1ecce-197">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="1ecce-197">ToolTip</span></span>|  
|<span data-ttu-id="1ecce-198">#32774</span><span class="sxs-lookup"><span data-stu-id="1ecce-198">#32774</span></span>|<span data-ttu-id="1ecce-199">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="1ecce-199">ToolTip</span></span>|  
|<span data-ttu-id="1ecce-200">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="1ecce-200">ReBarWindow32</span></span>|<span data-ttu-id="1ecce-201">Barre d'outils</span><span class="sxs-lookup"><span data-stu-id="1ecce-201">Toolbar</span></span>|  
|<span data-ttu-id="1ecce-202">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="1ecce-202">SysTreeView32</span></span>|<span data-ttu-id="1ecce-203">Arborescence</span><span class="sxs-lookup"><span data-stu-id="1ecce-203">Tree</span></span>|  
|<span data-ttu-id="1ecce-204">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="1ecce-204">SysTreeView32</span></span>|<span data-ttu-id="1ecce-205">TreeItem</span><span class="sxs-lookup"><span data-stu-id="1ecce-205">TreeItem</span></span>|  
  
 <span data-ttu-id="1ecce-206">**Remarque** Le contrôle RichEdit est pris en charge uniquement pour les versions fournies avec Windows Vista (dans RichEd20.dll version 3,1 et versions ultérieures, et MsftEdit.dll version 4,1 et versions ultérieures).</span><span class="sxs-lookup"><span data-stu-id="1ecce-206">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="1ecce-207">Les contrôles suivants ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="1ecce-207">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="1ecce-208">Nom de classe</span><span class="sxs-lookup"><span data-stu-id="1ecce-208">Class name</span></span>|<span data-ttu-id="1ecce-209">Type de contrôle</span><span class="sxs-lookup"><span data-stu-id="1ecce-209">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="1ecce-210">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="1ecce-210">SysAnimate32</span></span>|<span data-ttu-id="1ecce-211">Image</span><span class="sxs-lookup"><span data-stu-id="1ecce-211">Image</span></span>|  
|<span data-ttu-id="1ecce-212">SysPager</span><span class="sxs-lookup"><span data-stu-id="1ecce-212">SysPager</span></span>|<span data-ttu-id="1ecce-213">Spinner</span><span class="sxs-lookup"><span data-stu-id="1ecce-213">Spinner</span></span>|  
|<span data-ttu-id="1ecce-214">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="1ecce-214">SysDateTimePick32</span></span>|<span data-ttu-id="1ecce-215">Personnalisé</span><span class="sxs-lookup"><span data-stu-id="1ecce-215">Custom</span></span>|  
|<span data-ttu-id="1ecce-216">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="1ecce-216">SysMonthCal32</span></span>|<span data-ttu-id="1ecce-217">Calendrier</span><span class="sxs-lookup"><span data-stu-id="1ecce-217">Calendar</span></span>|  
|<span data-ttu-id="1ecce-218">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="1ecce-218">MS_WINNOTE</span></span>|<span data-ttu-id="1ecce-219">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="1ecce-219">Tooltip</span></span>|  
|<span data-ttu-id="1ecce-220">VBBubble</span><span class="sxs-lookup"><span data-stu-id="1ecce-220">VBBubble</span></span>|<span data-ttu-id="1ecce-221">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="1ecce-221">Tooltip</span></span>|  
|<span data-ttu-id="1ecce-222">ScrollBar (quand il est utilisé comme contrôle autonome)</span><span class="sxs-lookup"><span data-stu-id="1ecce-222">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="1ecce-223">Curseur</span><span class="sxs-lookup"><span data-stu-id="1ecce-223">Slider</span></span>|  
|<span data-ttu-id="1ecce-224">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="1ecce-224">SuperGrid</span></span>|<span data-ttu-id="1ecce-225">Personnalisé</span><span class="sxs-lookup"><span data-stu-id="1ecce-225">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>
## <a name="windows-forms-controls"></a><span data-ttu-id="1ecce-226">contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1ecce-226">Windows Forms Controls</span></span>  
 <span data-ttu-id="1ecce-227">Les contrôles Windows Forms sont exposés à [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] via des fournisseurs côté client dans UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="1ecce-227">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="1ecce-228">Cet assembly est inscrit automatiquement pour être utilisé avec les applications clientes UI Automation.</span><span class="sxs-lookup"><span data-stu-id="1ecce-228">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="1ecce-229">En général, les contrôles Windows Forms qui sont des wrappers managés pour les contrôles communs Win32 sont pris en charge par [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1ecce-229">Typically, Windows Forms controls that are managed wrappers for Win32 common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="1ecce-230">Les contrôles suivants sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="1ecce-230">The following controls are supported.</span></span>  
  
|<span data-ttu-id="1ecce-231">Nom de la classe</span><span class="sxs-lookup"><span data-stu-id="1ecce-231">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="1ecce-232">Bouton</span><span class="sxs-lookup"><span data-stu-id="1ecce-232">Button</span></span>|  
|<span data-ttu-id="1ecce-233">CheckBox</span><span class="sxs-lookup"><span data-stu-id="1ecce-233">CheckBox</span></span>|  
|<span data-ttu-id="1ecce-234">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="1ecce-234">CheckedListBox</span></span>|  
|<span data-ttu-id="1ecce-235">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="1ecce-235">ColorDialog</span></span>|  
|<span data-ttu-id="1ecce-236">ComboBox</span><span class="sxs-lookup"><span data-stu-id="1ecce-236">ComboBox</span></span>|  
|<span data-ttu-id="1ecce-237">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="1ecce-237">FolderBrowser</span></span>|  
|<span data-ttu-id="1ecce-238">FontDialog</span><span class="sxs-lookup"><span data-stu-id="1ecce-238">FontDialog</span></span>|  
|<span data-ttu-id="1ecce-239">GroupBox</span><span class="sxs-lookup"><span data-stu-id="1ecce-239">GroupBox</span></span>|  
|<span data-ttu-id="1ecce-240">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="1ecce-240">HscrollBar</span></span>|  
|<span data-ttu-id="1ecce-241">ImageList</span><span class="sxs-lookup"><span data-stu-id="1ecce-241">ImageList</span></span>|  
|<span data-ttu-id="1ecce-242">Étiquette</span><span class="sxs-lookup"><span data-stu-id="1ecce-242">Label</span></span>|  
|<span data-ttu-id="1ecce-243">ListBox</span><span class="sxs-lookup"><span data-stu-id="1ecce-243">ListBox</span></span>|  
|<span data-ttu-id="1ecce-244">Affichage de liste</span><span class="sxs-lookup"><span data-stu-id="1ecce-244">ListView</span></span>|  
|<span data-ttu-id="1ecce-245">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="1ecce-245">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="1ecce-246">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="1ecce-246">MonthCalendar</span></span>|  
|<span data-ttu-id="1ecce-247">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="1ecce-247">NotifyIcon</span></span>|  
|<span data-ttu-id="1ecce-248">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="1ecce-248">OpenFileDialog</span></span>|  
|<span data-ttu-id="1ecce-249">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="1ecce-249">PageSetupDialog</span></span>|  
|<span data-ttu-id="1ecce-250">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="1ecce-250">PrintDialog</span></span>|  
|<span data-ttu-id="1ecce-251">Barre de progression</span><span class="sxs-lookup"><span data-stu-id="1ecce-251">ProgressBar</span></span>|  
|<span data-ttu-id="1ecce-252">RadioButton</span><span class="sxs-lookup"><span data-stu-id="1ecce-252">RadioButton</span></span>|  
|<span data-ttu-id="1ecce-253">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="1ecce-253">RichTextBox</span></span>|  
|<span data-ttu-id="1ecce-254">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="1ecce-254">SaveFileDialog</span></span>|  
|<span data-ttu-id="1ecce-255">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="1ecce-255">ScrollableControl</span></span>|  
|<span data-ttu-id="1ecce-256">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="1ecce-256">SoundPlayer</span></span>|  
|<span data-ttu-id="1ecce-257">StatusBar</span><span class="sxs-lookup"><span data-stu-id="1ecce-257">StatusBar</span></span>|  
|<span data-ttu-id="1ecce-258">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="1ecce-258">TabControl/TabPage</span></span>|  
|<span data-ttu-id="1ecce-259">TextBox</span><span class="sxs-lookup"><span data-stu-id="1ecce-259">TextBox</span></span>|  
|<span data-ttu-id="1ecce-260">Minuterie</span><span class="sxs-lookup"><span data-stu-id="1ecce-260">Timer</span></span>|  
|<span data-ttu-id="1ecce-261">Barre d'outils</span><span class="sxs-lookup"><span data-stu-id="1ecce-261">Toolbar</span></span>|  
|<span data-ttu-id="1ecce-262">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="1ecce-262">ToolTip</span></span>|  
|<span data-ttu-id="1ecce-263">TrackBar</span><span class="sxs-lookup"><span data-stu-id="1ecce-263">TrackBar</span></span>|  
|<span data-ttu-id="1ecce-264">TreeView</span><span class="sxs-lookup"><span data-stu-id="1ecce-264">TreeView</span></span>|  
|<span data-ttu-id="1ecce-265">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="1ecce-265">VscrollBar</span></span>|  
|<span data-ttu-id="1ecce-266">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="1ecce-266">WebBrowser</span></span>|  
  
 <span data-ttu-id="1ecce-267">Les contrôles suivants sont exposés à [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] uniquement via leur prise en charge de Microsoft Active Accessibility.</span><span class="sxs-lookup"><span data-stu-id="1ecce-267">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="1ecce-268">Certaines fonctionnalités ne sont peut-être pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="1ecce-268">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="1ecce-269">Nom du contrôle</span><span class="sxs-lookup"><span data-stu-id="1ecce-269">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="1ecce-270">BindingSource</span><span class="sxs-lookup"><span data-stu-id="1ecce-270">BindingSource</span></span>|  
|<span data-ttu-id="1ecce-271">DataGrid</span><span class="sxs-lookup"><span data-stu-id="1ecce-271">DataGrid</span></span>|  
|<span data-ttu-id="1ecce-272">DataGridView</span><span class="sxs-lookup"><span data-stu-id="1ecce-272">DataGridView</span></span>|  
|<span data-ttu-id="1ecce-273">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="1ecce-273">DataNavigator</span></span>|  
|<span data-ttu-id="1ecce-274">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="1ecce-274">DomainUpDown</span></span>|  
|<span data-ttu-id="1ecce-275">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="1ecce-275">ErrorProvider</span></span>|  
|<span data-ttu-id="1ecce-276">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="1ecce-276">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="1ecce-277">Formulaire</span><span class="sxs-lookup"><span data-stu-id="1ecce-277">Form</span></span>|  
|<span data-ttu-id="1ecce-278">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="1ecce-278">LinkLabel</span></span>|  
|<span data-ttu-id="1ecce-279">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="1ecce-279">HelpProvider</span></span>|  
|<span data-ttu-id="1ecce-280">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="1ecce-280">MaskedTextBox</span></span>|  
|<span data-ttu-id="1ecce-281">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="1ecce-281">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="1ecce-282">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="1ecce-282">NumericUpDown</span></span>|  
|<span data-ttu-id="1ecce-283">Volet</span><span class="sxs-lookup"><span data-stu-id="1ecce-283">Panel</span></span>|  
|<span data-ttu-id="1ecce-284">PictureBox</span><span class="sxs-lookup"><span data-stu-id="1ecce-284">PictureBox</span></span>|  
|<span data-ttu-id="1ecce-285">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="1ecce-285">PrintDocument</span></span>|  
|<span data-ttu-id="1ecce-286">PrintPreviewControl</span><span class="sxs-lookup"><span data-stu-id="1ecce-286">PrintPreview-Control</span></span>|  
|<span data-ttu-id="1ecce-287">PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="1ecce-287">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="1ecce-288">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="1ecce-288">PropertyGrid</span></span>|  
|<span data-ttu-id="1ecce-289">UserControl</span><span class="sxs-lookup"><span data-stu-id="1ecce-289">UserControl</span></span>|  
|<span data-ttu-id="1ecce-290">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="1ecce-290">ToolStrip</span></span>|  
|<span data-ttu-id="1ecce-291">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="1ecce-291">TableLayoutPanel</span></span>|  
|<span data-ttu-id="1ecce-292">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="1ecce-292">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="1ecce-293">Séparateur</span><span class="sxs-lookup"><span data-stu-id="1ecce-293">Splitter</span></span>|  
|<span data-ttu-id="1ecce-294">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="1ecce-294">RaftingContainer</span></span>|  
|<span data-ttu-id="1ecce-295">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="1ecce-295">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1ecce-296">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ecce-296">See also</span></span>

- [<span data-ttu-id="1ecce-297">Types de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="1ecce-297">UI Automation Control Types</span></span>](ui-automation-control-types.md)
