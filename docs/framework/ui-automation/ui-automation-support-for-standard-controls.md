---
title: Prise en charge d'UI Automation pour les contrôles standard
description: Obtenir des informations sur la prise en charge d’UI Automation pour les contrôles standard dans les applications développées pour Windows Presentation Foundation (WPF), Win32 et Windows Forms.
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 0a5a0b61a6492d9efb62799fa610859b247cf26e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261070"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="c7a7e-103">Prise en charge d'UI Automation pour les contrôles standard</span><span class="sxs-lookup"><span data-stu-id="c7a7e-103">UI Automation Support for Standard Controls</span></span>

> [!NOTE]
> <span data-ttu-id="c7a7e-104">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="c7a7e-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="c7a7e-105">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="c7a7e-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="c7a7e-106">Cette rubrique contient des informations sur [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] la prise en charge des contrôles standard dans les applications développées pour les [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] frameworks, Win32 et Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c7a7e-106">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32, and Windows Forms frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>

## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="c7a7e-107">Contrôles Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="c7a7e-107">Windows Presentation Foundation Controls</span></span>  

 <span data-ttu-id="c7a7e-108">Tous les éléments du contrôle [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] qui fournissent des informations ou une prise en charge pour l’interaction utilisateur disposent d’une prise en charge native complète de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c7a7e-108">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="c7a7e-109">D’autres éléments, tels que les panneaux, ne sont pas visibles par [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c7a7e-109">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>

## <a name="win32-controls"></a><span data-ttu-id="c7a7e-110">Contrôles Win32</span><span class="sxs-lookup"><span data-stu-id="c7a7e-110">Win32 Controls</span></span>  

 <span data-ttu-id="c7a7e-111">La plupart des contrôles Win32 sont exposés à [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] via des fournisseurs côté client dans UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="c7a7e-111">Most Win32 controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="c7a7e-112">Cet assembly est inscrit automatiquement pour être utilisé avec les applications clientes UI Automation.</span><span class="sxs-lookup"><span data-stu-id="c7a7e-112">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="c7a7e-113">La prise en charge complète n’est fournie que pour les contrôles de la version 6 de *ComCtrl32.dll*.</span><span class="sxs-lookup"><span data-stu-id="c7a7e-113">Full support is provided only for controls from version 6 of *ComCtrl32.dll*.</span></span>  
  
 <span data-ttu-id="c7a7e-114">Les contrôles suivants sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="c7a7e-114">The following controls are supported.</span></span>  
  
|<span data-ttu-id="c7a7e-115">Nom de classe</span><span class="sxs-lookup"><span data-stu-id="c7a7e-115">Class name</span></span>|<span data-ttu-id="c7a7e-116">Type de contrôle</span><span class="sxs-lookup"><span data-stu-id="c7a7e-116">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="c7a7e-117">Button</span><span class="sxs-lookup"><span data-stu-id="c7a7e-117">Button</span></span>|<span data-ttu-id="c7a7e-118">Button</span><span class="sxs-lookup"><span data-stu-id="c7a7e-118">Button</span></span>|  
|<span data-ttu-id="c7a7e-119">Button</span><span class="sxs-lookup"><span data-stu-id="c7a7e-119">Button</span></span>|<span data-ttu-id="c7a7e-120">RadioButton</span><span class="sxs-lookup"><span data-stu-id="c7a7e-120">RadioButton</span></span>|  
|<span data-ttu-id="c7a7e-121">Bouton</span><span class="sxs-lookup"><span data-stu-id="c7a7e-121">Button</span></span>|<span data-ttu-id="c7a7e-122">Groupe</span><span class="sxs-lookup"><span data-stu-id="c7a7e-122">Group</span></span>|  
|<span data-ttu-id="c7a7e-123">Bouton</span><span class="sxs-lookup"><span data-stu-id="c7a7e-123">Button</span></span>|<span data-ttu-id="c7a7e-124">CheckBox</span><span class="sxs-lookup"><span data-stu-id="c7a7e-124">CheckBox</span></span>|  
|<span data-ttu-id="c7a7e-125">Bouton</span><span class="sxs-lookup"><span data-stu-id="c7a7e-125">Button</span></span>|<span data-ttu-id="c7a7e-126">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="c7a7e-126">Hyperlink</span></span>|  
|<span data-ttu-id="c7a7e-127">Bouton</span><span class="sxs-lookup"><span data-stu-id="c7a7e-127">Button</span></span>|<span data-ttu-id="c7a7e-128">SplitButton</span><span class="sxs-lookup"><span data-stu-id="c7a7e-128">SplitButton</span></span>|  
|<span data-ttu-id="c7a7e-129">Bouton</span><span class="sxs-lookup"><span data-stu-id="c7a7e-129">Button</span></span>|<span data-ttu-id="c7a7e-130">CheckBox</span><span class="sxs-lookup"><span data-stu-id="c7a7e-130">CheckBox</span></span>|  
|<span data-ttu-id="c7a7e-131">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="c7a7e-131">ComboBoxEx32</span></span>|<span data-ttu-id="c7a7e-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="c7a7e-132">ComboBox</span></span>|  
|<span data-ttu-id="c7a7e-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="c7a7e-133">ComboBox</span></span>|<span data-ttu-id="c7a7e-134">ComboBox</span><span class="sxs-lookup"><span data-stu-id="c7a7e-134">ComboBox</span></span>|  
|<span data-ttu-id="c7a7e-135">Modifier</span><span class="sxs-lookup"><span data-stu-id="c7a7e-135">Edit</span></span>|<span data-ttu-id="c7a7e-136">Document</span><span class="sxs-lookup"><span data-stu-id="c7a7e-136">Document</span></span>|  
|<span data-ttu-id="c7a7e-137">Modifier</span><span class="sxs-lookup"><span data-stu-id="c7a7e-137">Edit</span></span>|<span data-ttu-id="c7a7e-138">Modifier</span><span class="sxs-lookup"><span data-stu-id="c7a7e-138">Edit</span></span>|  
|<span data-ttu-id="c7a7e-139">SysLink</span><span class="sxs-lookup"><span data-stu-id="c7a7e-139">SysLink</span></span>|<span data-ttu-id="c7a7e-140">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="c7a7e-140">Hyperlink</span></span>|  
|<span data-ttu-id="c7a7e-141">statique</span><span class="sxs-lookup"><span data-stu-id="c7a7e-141">Static</span></span>|<span data-ttu-id="c7a7e-142">Texte</span><span class="sxs-lookup"><span data-stu-id="c7a7e-142">Text</span></span>|  
|<span data-ttu-id="c7a7e-143">statique</span><span class="sxs-lookup"><span data-stu-id="c7a7e-143">Static</span></span>|<span data-ttu-id="c7a7e-144">Image</span><span class="sxs-lookup"><span data-stu-id="c7a7e-144">Image</span></span>|  
|<span data-ttu-id="c7a7e-145">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="c7a7e-145">SysIPAddress32</span></span>|<span data-ttu-id="c7a7e-146">Custom</span><span class="sxs-lookup"><span data-stu-id="c7a7e-146">Custom</span></span>|  
|<span data-ttu-id="c7a7e-147">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="c7a7e-147">SysHeader32</span></span>|<span data-ttu-id="c7a7e-148">Header/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="c7a7e-148">Header/HeaderItem</span></span>|  
|<span data-ttu-id="c7a7e-149">SysListView32</span><span class="sxs-lookup"><span data-stu-id="c7a7e-149">SysListView32</span></span>|<span data-ttu-id="c7a7e-150">DataGrid</span><span class="sxs-lookup"><span data-stu-id="c7a7e-150">DataGrid</span></span>|  
|<span data-ttu-id="c7a7e-151">SysListView32</span><span class="sxs-lookup"><span data-stu-id="c7a7e-151">SysListView32</span></span>|<span data-ttu-id="c7a7e-152">List</span><span class="sxs-lookup"><span data-stu-id="c7a7e-152">List</span></span>|  
|<span data-ttu-id="c7a7e-153">ListBox</span><span class="sxs-lookup"><span data-stu-id="c7a7e-153">ListBox</span></span>|<span data-ttu-id="c7a7e-154">List</span><span class="sxs-lookup"><span data-stu-id="c7a7e-154">List</span></span>|  
|<span data-ttu-id="c7a7e-155">ListBox</span><span class="sxs-lookup"><span data-stu-id="c7a7e-155">ListBox</span></span>|<span data-ttu-id="c7a7e-156">ListItem</span><span class="sxs-lookup"><span data-stu-id="c7a7e-156">ListItem</span></span>|  
|<span data-ttu-id="c7a7e-157">#32768</span><span class="sxs-lookup"><span data-stu-id="c7a7e-157">#32768</span></span>|<span data-ttu-id="c7a7e-158">Menu</span><span class="sxs-lookup"><span data-stu-id="c7a7e-158">Menu</span></span>|  
|<span data-ttu-id="c7a7e-159">#32768</span><span class="sxs-lookup"><span data-stu-id="c7a7e-159">#32768</span></span>|<span data-ttu-id="c7a7e-160">MenuItem</span><span class="sxs-lookup"><span data-stu-id="c7a7e-160">MenuItem</span></span>|  
|<span data-ttu-id="c7a7e-161">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="c7a7e-161">msctls_progress32</span></span>|<span data-ttu-id="c7a7e-162">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="c7a7e-162">ProgressBar</span></span>|  
|<span data-ttu-id="c7a7e-163">RichEdit</span><span class="sxs-lookup"><span data-stu-id="c7a7e-163">RichEdit</span></span>|<span data-ttu-id="c7a7e-164">Document.</span><span class="sxs-lookup"><span data-stu-id="c7a7e-164">Document.</span></span> <span data-ttu-id="c7a7e-165">Consultez la remarque.</span><span class="sxs-lookup"><span data-stu-id="c7a7e-165">See note.</span></span>|  
|<span data-ttu-id="c7a7e-166">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="c7a7e-166">RichEdit20A</span></span>|<span data-ttu-id="c7a7e-167">Document</span><span class="sxs-lookup"><span data-stu-id="c7a7e-167">Document</span></span>|  
|<span data-ttu-id="c7a7e-168">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="c7a7e-168">RichEdit20W</span></span>|<span data-ttu-id="c7a7e-169">Document</span><span class="sxs-lookup"><span data-stu-id="c7a7e-169">Document</span></span>|  
|<span data-ttu-id="c7a7e-170">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="c7a7e-170">RichEdit50W</span></span>|<span data-ttu-id="c7a7e-171">Document</span><span class="sxs-lookup"><span data-stu-id="c7a7e-171">Document</span></span>|  
|<span data-ttu-id="c7a7e-172">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="c7a7e-172">ScrollBar</span></span>|<span data-ttu-id="c7a7e-173">Curseur</span><span class="sxs-lookup"><span data-stu-id="c7a7e-173">Slider</span></span>|  
|<span data-ttu-id="c7a7e-174">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="c7a7e-174">msctls_trackbar32</span></span>|<span data-ttu-id="c7a7e-175">Curseur</span><span class="sxs-lookup"><span data-stu-id="c7a7e-175">Slider</span></span>|  
|<span data-ttu-id="c7a7e-176">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="c7a7e-176">msctls_updown32</span></span>|<span data-ttu-id="c7a7e-177">Spinner</span><span class="sxs-lookup"><span data-stu-id="c7a7e-177">Spinner</span></span>|  
|<span data-ttu-id="c7a7e-178">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="c7a7e-178">msctls_statusbar32</span></span>|<span data-ttu-id="c7a7e-179">StatusBar</span><span class="sxs-lookup"><span data-stu-id="c7a7e-179">StatusBar</span></span>|  
|<span data-ttu-id="c7a7e-180">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="c7a7e-180">SysTabControl32</span></span>|<span data-ttu-id="c7a7e-181">Onglet</span><span class="sxs-lookup"><span data-stu-id="c7a7e-181">Tab</span></span>|  
|<span data-ttu-id="c7a7e-182">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="c7a7e-182">SysTabControl32</span></span>|<span data-ttu-id="c7a7e-183">TabItem</span><span class="sxs-lookup"><span data-stu-id="c7a7e-183">TabItem</span></span>|  
|<span data-ttu-id="c7a7e-184">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="c7a7e-184">ToolbarWindow32</span></span>|<span data-ttu-id="c7a7e-185">ToolBar</span><span class="sxs-lookup"><span data-stu-id="c7a7e-185">ToolBar</span></span>|  
|<span data-ttu-id="c7a7e-186">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="c7a7e-186">ToolbarWindow32</span></span>|<span data-ttu-id="c7a7e-187">MenuItem</span><span class="sxs-lookup"><span data-stu-id="c7a7e-187">MenuItem</span></span>|  
|<span data-ttu-id="c7a7e-188">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="c7a7e-188">ToolbarWindow32</span></span>|<span data-ttu-id="c7a7e-189">Bouton</span><span class="sxs-lookup"><span data-stu-id="c7a7e-189">Button</span></span>|  
|<span data-ttu-id="c7a7e-190">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="c7a7e-190">ToolbarWindow32</span></span>|<span data-ttu-id="c7a7e-191">CheckBox</span><span class="sxs-lookup"><span data-stu-id="c7a7e-191">CheckBox</span></span>|  
|<span data-ttu-id="c7a7e-192">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="c7a7e-192">ToolbarWindow32</span></span>|<span data-ttu-id="c7a7e-193">RadioButton</span><span class="sxs-lookup"><span data-stu-id="c7a7e-193">RadioButton</span></span>|  
|<span data-ttu-id="c7a7e-194">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="c7a7e-194">ToolbarWindow32</span></span>|<span data-ttu-id="c7a7e-195">Séparateur</span><span class="sxs-lookup"><span data-stu-id="c7a7e-195">Separator</span></span>|  
|<span data-ttu-id="c7a7e-196">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="c7a7e-196">tooltips_class32</span></span>|<span data-ttu-id="c7a7e-197">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="c7a7e-197">ToolTip</span></span>|  
|<span data-ttu-id="c7a7e-198">#32774</span><span class="sxs-lookup"><span data-stu-id="c7a7e-198">#32774</span></span>|<span data-ttu-id="c7a7e-199">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="c7a7e-199">ToolTip</span></span>|  
|<span data-ttu-id="c7a7e-200">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="c7a7e-200">ReBarWindow32</span></span>|<span data-ttu-id="c7a7e-201">Barre d'outils</span><span class="sxs-lookup"><span data-stu-id="c7a7e-201">Toolbar</span></span>|  
|<span data-ttu-id="c7a7e-202">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="c7a7e-202">SysTreeView32</span></span>|<span data-ttu-id="c7a7e-203">Arborescence</span><span class="sxs-lookup"><span data-stu-id="c7a7e-203">Tree</span></span>|  
|<span data-ttu-id="c7a7e-204">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="c7a7e-204">SysTreeView32</span></span>|<span data-ttu-id="c7a7e-205">TreeItem</span><span class="sxs-lookup"><span data-stu-id="c7a7e-205">TreeItem</span></span>|  
  
 <span data-ttu-id="c7a7e-206">**Remarque** Le contrôle RichEdit est pris en charge uniquement pour les versions fournies avec Windows Vista (dans RichEd20.dll version 3,1 et versions ultérieures, et MsftEdit.dll version 4,1 et versions ultérieures).</span><span class="sxs-lookup"><span data-stu-id="c7a7e-206">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="c7a7e-207">Les contrôles suivants ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="c7a7e-207">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="c7a7e-208">Nom de classe</span><span class="sxs-lookup"><span data-stu-id="c7a7e-208">Class name</span></span>|<span data-ttu-id="c7a7e-209">Type de contrôle</span><span class="sxs-lookup"><span data-stu-id="c7a7e-209">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="c7a7e-210">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="c7a7e-210">SysAnimate32</span></span>|<span data-ttu-id="c7a7e-211">Image</span><span class="sxs-lookup"><span data-stu-id="c7a7e-211">Image</span></span>|  
|<span data-ttu-id="c7a7e-212">SysPager</span><span class="sxs-lookup"><span data-stu-id="c7a7e-212">SysPager</span></span>|<span data-ttu-id="c7a7e-213">Spinner</span><span class="sxs-lookup"><span data-stu-id="c7a7e-213">Spinner</span></span>|  
|<span data-ttu-id="c7a7e-214">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="c7a7e-214">SysDateTimePick32</span></span>|<span data-ttu-id="c7a7e-215">Custom</span><span class="sxs-lookup"><span data-stu-id="c7a7e-215">Custom</span></span>|  
|<span data-ttu-id="c7a7e-216">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="c7a7e-216">SysMonthCal32</span></span>|<span data-ttu-id="c7a7e-217">Calendrier</span><span class="sxs-lookup"><span data-stu-id="c7a7e-217">Calendar</span></span>|  
|<span data-ttu-id="c7a7e-218">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="c7a7e-218">MS_WINNOTE</span></span>|<span data-ttu-id="c7a7e-219">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="c7a7e-219">Tooltip</span></span>|  
|<span data-ttu-id="c7a7e-220">VBBubble</span><span class="sxs-lookup"><span data-stu-id="c7a7e-220">VBBubble</span></span>|<span data-ttu-id="c7a7e-221">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="c7a7e-221">Tooltip</span></span>|  
|<span data-ttu-id="c7a7e-222">ScrollBar (quand il est utilisé comme contrôle autonome)</span><span class="sxs-lookup"><span data-stu-id="c7a7e-222">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="c7a7e-223">Curseur</span><span class="sxs-lookup"><span data-stu-id="c7a7e-223">Slider</span></span>|  
|<span data-ttu-id="c7a7e-224">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="c7a7e-224">SuperGrid</span></span>|<span data-ttu-id="c7a7e-225">Custom</span><span class="sxs-lookup"><span data-stu-id="c7a7e-225">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>

## <a name="windows-forms-controls"></a><span data-ttu-id="c7a7e-226">contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7a7e-226">Windows Forms Controls</span></span>  

 <span data-ttu-id="c7a7e-227">Les contrôles Windows Forms sont exposés à [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] via des fournisseurs côté client dans UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="c7a7e-227">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="c7a7e-228">Cet assembly est inscrit automatiquement pour être utilisé avec les applications clientes UI Automation.</span><span class="sxs-lookup"><span data-stu-id="c7a7e-228">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="c7a7e-229">En général, les contrôles Windows Forms qui sont des wrappers managés pour les contrôles communs Win32 sont pris en charge par [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c7a7e-229">Typically, Windows Forms controls that are managed wrappers for Win32 common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="c7a7e-230">Les contrôles suivants sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="c7a7e-230">The following controls are supported.</span></span>  
  
|<span data-ttu-id="c7a7e-231">Nom de la classe</span><span class="sxs-lookup"><span data-stu-id="c7a7e-231">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="c7a7e-232">Bouton</span><span class="sxs-lookup"><span data-stu-id="c7a7e-232">Button</span></span>|  
|<span data-ttu-id="c7a7e-233">CheckBox</span><span class="sxs-lookup"><span data-stu-id="c7a7e-233">CheckBox</span></span>|  
|<span data-ttu-id="c7a7e-234">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="c7a7e-234">CheckedListBox</span></span>|  
|<span data-ttu-id="c7a7e-235">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="c7a7e-235">ColorDialog</span></span>|  
|<span data-ttu-id="c7a7e-236">ComboBox</span><span class="sxs-lookup"><span data-stu-id="c7a7e-236">ComboBox</span></span>|  
|<span data-ttu-id="c7a7e-237">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="c7a7e-237">FolderBrowser</span></span>|  
|<span data-ttu-id="c7a7e-238">FontDialog</span><span class="sxs-lookup"><span data-stu-id="c7a7e-238">FontDialog</span></span>|  
|<span data-ttu-id="c7a7e-239">GroupBox</span><span class="sxs-lookup"><span data-stu-id="c7a7e-239">GroupBox</span></span>|  
|<span data-ttu-id="c7a7e-240">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="c7a7e-240">HscrollBar</span></span>|  
|<span data-ttu-id="c7a7e-241">ImageList</span><span class="sxs-lookup"><span data-stu-id="c7a7e-241">ImageList</span></span>|  
|<span data-ttu-id="c7a7e-242">Étiquette</span><span class="sxs-lookup"><span data-stu-id="c7a7e-242">Label</span></span>|  
|<span data-ttu-id="c7a7e-243">ListBox</span><span class="sxs-lookup"><span data-stu-id="c7a7e-243">ListBox</span></span>|  
|<span data-ttu-id="c7a7e-244">ListView</span><span class="sxs-lookup"><span data-stu-id="c7a7e-244">ListView</span></span>|  
|<span data-ttu-id="c7a7e-245">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="c7a7e-245">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="c7a7e-246">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="c7a7e-246">MonthCalendar</span></span>|  
|<span data-ttu-id="c7a7e-247">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="c7a7e-247">NotifyIcon</span></span>|  
|<span data-ttu-id="c7a7e-248">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="c7a7e-248">OpenFileDialog</span></span>|  
|<span data-ttu-id="c7a7e-249">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="c7a7e-249">PageSetupDialog</span></span>|  
|<span data-ttu-id="c7a7e-250">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="c7a7e-250">PrintDialog</span></span>|  
|<span data-ttu-id="c7a7e-251">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="c7a7e-251">ProgressBar</span></span>|  
|<span data-ttu-id="c7a7e-252">RadioButton</span><span class="sxs-lookup"><span data-stu-id="c7a7e-252">RadioButton</span></span>|  
|<span data-ttu-id="c7a7e-253">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="c7a7e-253">RichTextBox</span></span>|  
|<span data-ttu-id="c7a7e-254">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="c7a7e-254">SaveFileDialog</span></span>|  
|<span data-ttu-id="c7a7e-255">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="c7a7e-255">ScrollableControl</span></span>|  
|<span data-ttu-id="c7a7e-256">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="c7a7e-256">SoundPlayer</span></span>|  
|<span data-ttu-id="c7a7e-257">StatusBar</span><span class="sxs-lookup"><span data-stu-id="c7a7e-257">StatusBar</span></span>|  
|<span data-ttu-id="c7a7e-258">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="c7a7e-258">TabControl/TabPage</span></span>|  
|<span data-ttu-id="c7a7e-259">TextBox</span><span class="sxs-lookup"><span data-stu-id="c7a7e-259">TextBox</span></span>|  
|<span data-ttu-id="c7a7e-260">Minuteur</span><span class="sxs-lookup"><span data-stu-id="c7a7e-260">Timer</span></span>|  
|<span data-ttu-id="c7a7e-261">Barre d'outils</span><span class="sxs-lookup"><span data-stu-id="c7a7e-261">Toolbar</span></span>|  
|<span data-ttu-id="c7a7e-262">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="c7a7e-262">ToolTip</span></span>|  
|<span data-ttu-id="c7a7e-263">TrackBar</span><span class="sxs-lookup"><span data-stu-id="c7a7e-263">TrackBar</span></span>|  
|<span data-ttu-id="c7a7e-264">TreeView</span><span class="sxs-lookup"><span data-stu-id="c7a7e-264">TreeView</span></span>|  
|<span data-ttu-id="c7a7e-265">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="c7a7e-265">VscrollBar</span></span>|  
|<span data-ttu-id="c7a7e-266">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="c7a7e-266">WebBrowser</span></span>|  
  
 <span data-ttu-id="c7a7e-267">Les contrôles suivants sont exposés à [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] uniquement via leur prise en charge de Microsoft Active Accessibility.</span><span class="sxs-lookup"><span data-stu-id="c7a7e-267">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="c7a7e-268">Certaines fonctionnalités ne sont peut-être pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="c7a7e-268">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="c7a7e-269">Nom du contrôle</span><span class="sxs-lookup"><span data-stu-id="c7a7e-269">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="c7a7e-270">BindingSource</span><span class="sxs-lookup"><span data-stu-id="c7a7e-270">BindingSource</span></span>|  
|<span data-ttu-id="c7a7e-271">DataGrid</span><span class="sxs-lookup"><span data-stu-id="c7a7e-271">DataGrid</span></span>|  
|<span data-ttu-id="c7a7e-272">DataGridView</span><span class="sxs-lookup"><span data-stu-id="c7a7e-272">DataGridView</span></span>|  
|<span data-ttu-id="c7a7e-273">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="c7a7e-273">DataNavigator</span></span>|  
|<span data-ttu-id="c7a7e-274">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="c7a7e-274">DomainUpDown</span></span>|  
|<span data-ttu-id="c7a7e-275">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="c7a7e-275">ErrorProvider</span></span>|  
|<span data-ttu-id="c7a7e-276">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="c7a7e-276">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="c7a7e-277">Formulaire</span><span class="sxs-lookup"><span data-stu-id="c7a7e-277">Form</span></span>|  
|<span data-ttu-id="c7a7e-278">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="c7a7e-278">LinkLabel</span></span>|  
|<span data-ttu-id="c7a7e-279">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="c7a7e-279">HelpProvider</span></span>|  
|<span data-ttu-id="c7a7e-280">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="c7a7e-280">MaskedTextBox</span></span>|  
|<span data-ttu-id="c7a7e-281">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="c7a7e-281">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="c7a7e-282">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="c7a7e-282">NumericUpDown</span></span>|  
|<span data-ttu-id="c7a7e-283">Volet</span><span class="sxs-lookup"><span data-stu-id="c7a7e-283">Panel</span></span>|  
|<span data-ttu-id="c7a7e-284">PictureBox</span><span class="sxs-lookup"><span data-stu-id="c7a7e-284">PictureBox</span></span>|  
|<span data-ttu-id="c7a7e-285">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="c7a7e-285">PrintDocument</span></span>|  
|<span data-ttu-id="c7a7e-286">PrintPreviewControl</span><span class="sxs-lookup"><span data-stu-id="c7a7e-286">PrintPreview-Control</span></span>|  
|<span data-ttu-id="c7a7e-287">PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="c7a7e-287">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="c7a7e-288">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="c7a7e-288">PropertyGrid</span></span>|  
|<span data-ttu-id="c7a7e-289">UserControl</span><span class="sxs-lookup"><span data-stu-id="c7a7e-289">UserControl</span></span>|  
|<span data-ttu-id="c7a7e-290">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="c7a7e-290">ToolStrip</span></span>|  
|<span data-ttu-id="c7a7e-291">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="c7a7e-291">TableLayoutPanel</span></span>|  
|<span data-ttu-id="c7a7e-292">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="c7a7e-292">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="c7a7e-293">Séparateur</span><span class="sxs-lookup"><span data-stu-id="c7a7e-293">Splitter</span></span>|  
|<span data-ttu-id="c7a7e-294">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="c7a7e-294">RaftingContainer</span></span>|  
|<span data-ttu-id="c7a7e-295">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="c7a7e-295">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c7a7e-296">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7a7e-296">See also</span></span>

- [<span data-ttu-id="c7a7e-297">Types de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="c7a7e-297">UI Automation Control Types</span></span>](ui-automation-control-types.md)
