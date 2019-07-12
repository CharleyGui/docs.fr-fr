---
title: Prise en charge d'UI Automation pour les contrôles standard
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 641fc3f8dfca3ff6506354c076b98cc88073a1b7
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802119"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="11c38-102">Prise en charge d'UI Automation pour les contrôles standard</span><span class="sxs-lookup"><span data-stu-id="11c38-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="11c38-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="11c38-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="11c38-104">Pour plus d’informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [Windows Automation API : UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="11c38-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="11c38-105">Cette rubrique contient des informations sur la prise en charge d’ [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour les contrôles standard dans les applications développées pour les infrastructures [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]et [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="11c38-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="11c38-106">Contrôles Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="11c38-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="11c38-107">Tous les éléments du contrôle [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] qui fournissent des informations ou une prise en charge pour l’interaction utilisateur disposent d’une prise en charge native complète de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="11c38-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="11c38-108">D’autres éléments, tels que les panneaux, ne sont pas visibles par [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="11c38-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="11c38-109">Contrôles Win32</span><span class="sxs-lookup"><span data-stu-id="11c38-109">Win32 Controls</span></span>  
 <span data-ttu-id="11c38-110">La plupart des contrôles [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] sont exposés à [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] via des fournisseurs côté client dans UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="11c38-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="11c38-111">Cet assembly est inscrit automatiquement pour être utilisé avec les applications clientes UI Automation.</span><span class="sxs-lookup"><span data-stu-id="11c38-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="11c38-112">La prise en charge complète n’est fournie que pour les contrôles de la version 6 de ComCtrl32.dll (disponible avec [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] et les versions ultérieures).</span><span class="sxs-lookup"><span data-stu-id="11c38-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="11c38-113">Les contrôles suivants sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="11c38-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="11c38-114">Nom de classe</span><span class="sxs-lookup"><span data-stu-id="11c38-114">Class name</span></span>|<span data-ttu-id="11c38-115">Type de contrôle</span><span class="sxs-lookup"><span data-stu-id="11c38-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="11c38-116">Bouton</span><span class="sxs-lookup"><span data-stu-id="11c38-116">Button</span></span>|<span data-ttu-id="11c38-117">Bouton</span><span class="sxs-lookup"><span data-stu-id="11c38-117">Button</span></span>|  
|<span data-ttu-id="11c38-118">Bouton</span><span class="sxs-lookup"><span data-stu-id="11c38-118">Button</span></span>|<span data-ttu-id="11c38-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="11c38-119">RadioButton</span></span>|  
|<span data-ttu-id="11c38-120">Bouton</span><span class="sxs-lookup"><span data-stu-id="11c38-120">Button</span></span>|<span data-ttu-id="11c38-121">Regrouper</span><span class="sxs-lookup"><span data-stu-id="11c38-121">Group</span></span>|  
|<span data-ttu-id="11c38-122">Bouton</span><span class="sxs-lookup"><span data-stu-id="11c38-122">Button</span></span>|<span data-ttu-id="11c38-123">Case à cocher</span><span class="sxs-lookup"><span data-stu-id="11c38-123">CheckBox</span></span>|  
|<span data-ttu-id="11c38-124">Bouton</span><span class="sxs-lookup"><span data-stu-id="11c38-124">Button</span></span>|<span data-ttu-id="11c38-125">Lien hypertexte</span><span class="sxs-lookup"><span data-stu-id="11c38-125">Hyperlink</span></span>|  
|<span data-ttu-id="11c38-126">Bouton</span><span class="sxs-lookup"><span data-stu-id="11c38-126">Button</span></span>|<span data-ttu-id="11c38-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="11c38-127">SplitButton</span></span>|  
|<span data-ttu-id="11c38-128">Bouton</span><span class="sxs-lookup"><span data-stu-id="11c38-128">Button</span></span>|<span data-ttu-id="11c38-129">Case à cocher</span><span class="sxs-lookup"><span data-stu-id="11c38-129">CheckBox</span></span>|  
|<span data-ttu-id="11c38-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="11c38-130">ComboBoxEx32</span></span>|<span data-ttu-id="11c38-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="11c38-131">ComboBox</span></span>|  
|<span data-ttu-id="11c38-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="11c38-132">ComboBox</span></span>|<span data-ttu-id="11c38-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="11c38-133">ComboBox</span></span>|  
|<span data-ttu-id="11c38-134">Modifier</span><span class="sxs-lookup"><span data-stu-id="11c38-134">Edit</span></span>|<span data-ttu-id="11c38-135">Document</span><span class="sxs-lookup"><span data-stu-id="11c38-135">Document</span></span>|  
|<span data-ttu-id="11c38-136">Modifier</span><span class="sxs-lookup"><span data-stu-id="11c38-136">Edit</span></span>|<span data-ttu-id="11c38-137">Modifier</span><span class="sxs-lookup"><span data-stu-id="11c38-137">Edit</span></span>|  
|<span data-ttu-id="11c38-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="11c38-138">SysLink</span></span>|<span data-ttu-id="11c38-139">Lien hypertexte</span><span class="sxs-lookup"><span data-stu-id="11c38-139">Hyperlink</span></span>|  
|<span data-ttu-id="11c38-140">statique</span><span class="sxs-lookup"><span data-stu-id="11c38-140">Static</span></span>|<span data-ttu-id="11c38-141">Text</span><span class="sxs-lookup"><span data-stu-id="11c38-141">Text</span></span>|  
|<span data-ttu-id="11c38-142">Statique</span><span class="sxs-lookup"><span data-stu-id="11c38-142">Static</span></span>|<span data-ttu-id="11c38-143">Image</span><span class="sxs-lookup"><span data-stu-id="11c38-143">Image</span></span>|  
|<span data-ttu-id="11c38-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="11c38-144">SysIPAddress32</span></span>|<span data-ttu-id="11c38-145">Personnalisé</span><span class="sxs-lookup"><span data-stu-id="11c38-145">Custom</span></span>|  
|<span data-ttu-id="11c38-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="11c38-146">SysHeader32</span></span>|<span data-ttu-id="11c38-147">Header/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="11c38-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="11c38-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="11c38-148">SysListView32</span></span>|<span data-ttu-id="11c38-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="11c38-149">DataGrid</span></span>|  
|<span data-ttu-id="11c38-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="11c38-150">SysListView32</span></span>|<span data-ttu-id="11c38-151">Énumérer</span><span class="sxs-lookup"><span data-stu-id="11c38-151">List</span></span>|  
|<span data-ttu-id="11c38-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="11c38-152">ListBox</span></span>|<span data-ttu-id="11c38-153">Énumérer</span><span class="sxs-lookup"><span data-stu-id="11c38-153">List</span></span>|  
|<span data-ttu-id="11c38-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="11c38-154">ListBox</span></span>|<span data-ttu-id="11c38-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="11c38-155">ListItem</span></span>|  
|<span data-ttu-id="11c38-156">#32768</span><span class="sxs-lookup"><span data-stu-id="11c38-156">#32768</span></span>|<span data-ttu-id="11c38-157">Menu</span><span class="sxs-lookup"><span data-stu-id="11c38-157">Menu</span></span>|  
|<span data-ttu-id="11c38-158">#32768</span><span class="sxs-lookup"><span data-stu-id="11c38-158">#32768</span></span>|<span data-ttu-id="11c38-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="11c38-159">MenuItem</span></span>|  
|<span data-ttu-id="11c38-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="11c38-160">msctls_progress32</span></span>|<span data-ttu-id="11c38-161">Barre de progression</span><span class="sxs-lookup"><span data-stu-id="11c38-161">ProgressBar</span></span>|  
|<span data-ttu-id="11c38-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="11c38-162">RichEdit</span></span>|<span data-ttu-id="11c38-163">Document.</span><span class="sxs-lookup"><span data-stu-id="11c38-163">Document.</span></span> <span data-ttu-id="11c38-164">Consultez la remarque.</span><span class="sxs-lookup"><span data-stu-id="11c38-164">See note.</span></span>|  
|<span data-ttu-id="11c38-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="11c38-165">RichEdit20A</span></span>|<span data-ttu-id="11c38-166">Document</span><span class="sxs-lookup"><span data-stu-id="11c38-166">Document</span></span>|  
|<span data-ttu-id="11c38-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="11c38-167">RichEdit20W</span></span>|<span data-ttu-id="11c38-168">Document</span><span class="sxs-lookup"><span data-stu-id="11c38-168">Document</span></span>|  
|<span data-ttu-id="11c38-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="11c38-169">RichEdit50W</span></span>|<span data-ttu-id="11c38-170">Document</span><span class="sxs-lookup"><span data-stu-id="11c38-170">Document</span></span>|  
|<span data-ttu-id="11c38-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="11c38-171">ScrollBar</span></span>|<span data-ttu-id="11c38-172">Curseur</span><span class="sxs-lookup"><span data-stu-id="11c38-172">Slider</span></span>|  
|<span data-ttu-id="11c38-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="11c38-173">msctls_trackbar32</span></span>|<span data-ttu-id="11c38-174">Curseur</span><span class="sxs-lookup"><span data-stu-id="11c38-174">Slider</span></span>|  
|<span data-ttu-id="11c38-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="11c38-175">msctls_updown32</span></span>|<span data-ttu-id="11c38-176">Spinner</span><span class="sxs-lookup"><span data-stu-id="11c38-176">Spinner</span></span>|  
|<span data-ttu-id="11c38-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="11c38-177">msctls_statusbar32</span></span>|<span data-ttu-id="11c38-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="11c38-178">StatusBar</span></span>|  
|<span data-ttu-id="11c38-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="11c38-179">SysTabControl32</span></span>|<span data-ttu-id="11c38-180">Onglet</span><span class="sxs-lookup"><span data-stu-id="11c38-180">Tab</span></span>|  
|<span data-ttu-id="11c38-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="11c38-181">SysTabControl32</span></span>|<span data-ttu-id="11c38-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="11c38-182">TabItem</span></span>|  
|<span data-ttu-id="11c38-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="11c38-183">ToolbarWindow32</span></span>|<span data-ttu-id="11c38-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="11c38-184">ToolBar</span></span>|  
|<span data-ttu-id="11c38-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="11c38-185">ToolbarWindow32</span></span>|<span data-ttu-id="11c38-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="11c38-186">MenuItem</span></span>|  
|<span data-ttu-id="11c38-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="11c38-187">ToolbarWindow32</span></span>|<span data-ttu-id="11c38-188">Bouton</span><span class="sxs-lookup"><span data-stu-id="11c38-188">Button</span></span>|  
|<span data-ttu-id="11c38-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="11c38-189">ToolbarWindow32</span></span>|<span data-ttu-id="11c38-190">Case à cocher</span><span class="sxs-lookup"><span data-stu-id="11c38-190">CheckBox</span></span>|  
|<span data-ttu-id="11c38-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="11c38-191">ToolbarWindow32</span></span>|<span data-ttu-id="11c38-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="11c38-192">RadioButton</span></span>|  
|<span data-ttu-id="11c38-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="11c38-193">ToolbarWindow32</span></span>|<span data-ttu-id="11c38-194">Séparateur</span><span class="sxs-lookup"><span data-stu-id="11c38-194">Separator</span></span>|  
|<span data-ttu-id="11c38-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="11c38-195">tooltips_class32</span></span>|<span data-ttu-id="11c38-196">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="11c38-196">ToolTip</span></span>|  
|<span data-ttu-id="11c38-197">#32774</span><span class="sxs-lookup"><span data-stu-id="11c38-197">#32774</span></span>|<span data-ttu-id="11c38-198">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="11c38-198">ToolTip</span></span>|  
|<span data-ttu-id="11c38-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="11c38-199">ReBarWindow32</span></span>|<span data-ttu-id="11c38-200">ToolBar</span><span class="sxs-lookup"><span data-stu-id="11c38-200">Toolbar</span></span>|  
|<span data-ttu-id="11c38-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="11c38-201">SysTreeView32</span></span>|<span data-ttu-id="11c38-202">Arborescence</span><span class="sxs-lookup"><span data-stu-id="11c38-202">Tree</span></span>|  
|<span data-ttu-id="11c38-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="11c38-203">SysTreeView32</span></span>|<span data-ttu-id="11c38-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="11c38-204">TreeItem</span></span>|  
  
 <span data-ttu-id="11c38-205">**Remarque** Le contrôle RichEdit est pris en charge uniquement pour les versions fournies avec [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (dans RichEd20.dll version 3.1 et version ultérieure, ainsi que dans MsftEdit.dll version 4.1 et version ultérieure).</span><span class="sxs-lookup"><span data-stu-id="11c38-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="11c38-206">Les contrôles suivants ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="11c38-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="11c38-207">Nom de classe</span><span class="sxs-lookup"><span data-stu-id="11c38-207">Class name</span></span>|<span data-ttu-id="11c38-208">Type de contrôle</span><span class="sxs-lookup"><span data-stu-id="11c38-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="11c38-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="11c38-209">SysAnimate32</span></span>|<span data-ttu-id="11c38-210">Image</span><span class="sxs-lookup"><span data-stu-id="11c38-210">Image</span></span>|  
|<span data-ttu-id="11c38-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="11c38-211">SysPager</span></span>|<span data-ttu-id="11c38-212">Spinner</span><span class="sxs-lookup"><span data-stu-id="11c38-212">Spinner</span></span>|  
|<span data-ttu-id="11c38-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="11c38-213">SysDateTimePick32</span></span>|<span data-ttu-id="11c38-214">Personnalisé</span><span class="sxs-lookup"><span data-stu-id="11c38-214">Custom</span></span>|  
|<span data-ttu-id="11c38-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="11c38-215">SysMonthCal32</span></span>|<span data-ttu-id="11c38-216">Calendrier</span><span class="sxs-lookup"><span data-stu-id="11c38-216">Calendar</span></span>|  
|<span data-ttu-id="11c38-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="11c38-217">MS_WINNOTE</span></span>|<span data-ttu-id="11c38-218">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="11c38-218">Tooltip</span></span>|  
|<span data-ttu-id="11c38-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="11c38-219">VBBubble</span></span>|<span data-ttu-id="11c38-220">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="11c38-220">Tooltip</span></span>|  
|<span data-ttu-id="11c38-221">ScrollBar (quand il est utilisé comme contrôle autonome)</span><span class="sxs-lookup"><span data-stu-id="11c38-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="11c38-222">Curseur</span><span class="sxs-lookup"><span data-stu-id="11c38-222">Slider</span></span>|  
|<span data-ttu-id="11c38-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="11c38-223">SuperGrid</span></span>|<span data-ttu-id="11c38-224">Personnalisé</span><span class="sxs-lookup"><span data-stu-id="11c38-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="11c38-225">contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11c38-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="11c38-226">Contrôles Windows Forms sont exposés à [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] via des fournisseurs côté client dans UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="11c38-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="11c38-227">Cet assembly est inscrit automatiquement pour être utilisé avec les applications clientes UI Automation.</span><span class="sxs-lookup"><span data-stu-id="11c38-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="11c38-228">En règle générale, les contrôles Windows Forms qui sont des wrappers managés pour [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] contrôles communs sont pris en charge par [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="11c38-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="11c38-229">Les contrôles suivants sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="11c38-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="11c38-230">Nom de classe</span><span class="sxs-lookup"><span data-stu-id="11c38-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="11c38-231">Bouton</span><span class="sxs-lookup"><span data-stu-id="11c38-231">Button</span></span>|  
|<span data-ttu-id="11c38-232">Case à cocher</span><span class="sxs-lookup"><span data-stu-id="11c38-232">CheckBox</span></span>|  
|<span data-ttu-id="11c38-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="11c38-233">CheckedListBox</span></span>|  
|<span data-ttu-id="11c38-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="11c38-234">ColorDialog</span></span>|  
|<span data-ttu-id="11c38-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="11c38-235">ComboBox</span></span>|  
|<span data-ttu-id="11c38-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="11c38-236">FolderBrowser</span></span>|  
|<span data-ttu-id="11c38-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="11c38-237">FontDialog</span></span>|  
|<span data-ttu-id="11c38-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="11c38-238">GroupBox</span></span>|  
|<span data-ttu-id="11c38-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="11c38-239">HscrollBar</span></span>|  
|<span data-ttu-id="11c38-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="11c38-240">ImageList</span></span>|  
|<span data-ttu-id="11c38-241">Etiquette</span><span class="sxs-lookup"><span data-stu-id="11c38-241">Label</span></span>|  
|<span data-ttu-id="11c38-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="11c38-242">ListBox</span></span>|  
|<span data-ttu-id="11c38-243">Affichage de liste</span><span class="sxs-lookup"><span data-stu-id="11c38-243">ListView</span></span>|  
|<span data-ttu-id="11c38-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="11c38-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="11c38-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="11c38-245">MonthCalendar</span></span>|  
|<span data-ttu-id="11c38-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="11c38-246">NotifyIcon</span></span>|  
|<span data-ttu-id="11c38-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="11c38-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="11c38-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="11c38-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="11c38-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="11c38-249">PrintDialog</span></span>|  
|<span data-ttu-id="11c38-250">Barre de progression</span><span class="sxs-lookup"><span data-stu-id="11c38-250">ProgressBar</span></span>|  
|<span data-ttu-id="11c38-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="11c38-251">RadioButton</span></span>|  
|<span data-ttu-id="11c38-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="11c38-252">RichTextBox</span></span>|  
|<span data-ttu-id="11c38-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="11c38-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="11c38-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="11c38-254">ScrollableControl</span></span>|  
|<span data-ttu-id="11c38-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="11c38-255">SoundPlayer</span></span>|  
|<span data-ttu-id="11c38-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="11c38-256">StatusBar</span></span>|  
|<span data-ttu-id="11c38-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="11c38-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="11c38-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="11c38-258">TextBox</span></span>|  
|<span data-ttu-id="11c38-259">Minuterie</span><span class="sxs-lookup"><span data-stu-id="11c38-259">Timer</span></span>|  
|<span data-ttu-id="11c38-260">ToolBar</span><span class="sxs-lookup"><span data-stu-id="11c38-260">Toolbar</span></span>|  
|<span data-ttu-id="11c38-261">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="11c38-261">ToolTip</span></span>|  
|<span data-ttu-id="11c38-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="11c38-262">TrackBar</span></span>|  
|<span data-ttu-id="11c38-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="11c38-263">TreeView</span></span>|  
|<span data-ttu-id="11c38-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="11c38-264">VscrollBar</span></span>|  
|<span data-ttu-id="11c38-265">Navigateur web</span><span class="sxs-lookup"><span data-stu-id="11c38-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="11c38-266">Les contrôles suivants sont exposés à [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] uniquement par le biais de leur prise en charge pour Microsoft Active Accessibility.</span><span class="sxs-lookup"><span data-stu-id="11c38-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="11c38-267">Certaines fonctionnalités ne sont peut-être pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="11c38-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="11c38-268">Nom du contrôle</span><span class="sxs-lookup"><span data-stu-id="11c38-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="11c38-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="11c38-269">BindingSource</span></span>|  
|<span data-ttu-id="11c38-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="11c38-270">DataGrid</span></span>|  
|<span data-ttu-id="11c38-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="11c38-271">DataGridView</span></span>|  
|<span data-ttu-id="11c38-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="11c38-272">DataNavigator</span></span>|  
|<span data-ttu-id="11c38-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="11c38-273">DomainUpDown</span></span>|  
|<span data-ttu-id="11c38-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="11c38-274">ErrorProvider</span></span>|  
|<span data-ttu-id="11c38-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="11c38-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="11c38-276">Formulaire</span><span class="sxs-lookup"><span data-stu-id="11c38-276">Form</span></span>|  
|<span data-ttu-id="11c38-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="11c38-277">LinkLabel</span></span>|  
|<span data-ttu-id="11c38-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="11c38-278">HelpProvider</span></span>|  
|<span data-ttu-id="11c38-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="11c38-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="11c38-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="11c38-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="11c38-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="11c38-281">NumericUpDown</span></span>|  
|<span data-ttu-id="11c38-282">Volet</span><span class="sxs-lookup"><span data-stu-id="11c38-282">Panel</span></span>|  
|<span data-ttu-id="11c38-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="11c38-283">PictureBox</span></span>|  
|<span data-ttu-id="11c38-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="11c38-284">PrintDocument</span></span>|  
|<span data-ttu-id="11c38-285">PrintPreviewControl</span><span class="sxs-lookup"><span data-stu-id="11c38-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="11c38-286">PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="11c38-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="11c38-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="11c38-287">PropertyGrid</span></span>|  
|<span data-ttu-id="11c38-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="11c38-288">UserControl</span></span>|  
|<span data-ttu-id="11c38-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="11c38-289">ToolStrip</span></span>|  
|<span data-ttu-id="11c38-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="11c38-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="11c38-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="11c38-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="11c38-292">Séparateur</span><span class="sxs-lookup"><span data-stu-id="11c38-292">Splitter</span></span>|  
|<span data-ttu-id="11c38-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="11c38-293">RaftingContainer</span></span>|  
|<span data-ttu-id="11c38-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="11c38-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="11c38-295">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11c38-295">See also</span></span>

- [<span data-ttu-id="11c38-296">Types de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="11c38-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
