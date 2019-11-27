---
title: Vue d'ensemble des types de contrôle UI Automation
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: ec2dd3635f09144985df278be1d53ead675d3080
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442626"
---
# <a name="ui-automation-control-types-overview"></a><span data-ttu-id="41d2e-102">Vue d'ensemble des types de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="41d2e-102">UI Automation Control Types Overview</span></span>
> [!NOTE]
> <span data-ttu-id="41d2e-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="41d2e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="41d2e-104">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="41d2e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="41d2e-105">Les types de contrôle[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] sont des identificateurs connus qui peuvent être utilisés pour indiquer le type de contrôle que représente un élément particulier, tel qu’une zone de liste modifiable ou un bouton.</span><span class="sxs-lookup"><span data-stu-id="41d2e-105">[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] control types are well-known identifiers that can be used to indicate what kind of control a particular element represents, such as a combo box or a button.</span></span>  
  
 <span data-ttu-id="41d2e-106">Avoir un identificateur connu permet aux périphériques de technologie d'assistance de déterminer plus facilement les types de contrôles disponibles dans l' [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] et de savoir comment interagir avec les contrôles.</span><span class="sxs-lookup"><span data-stu-id="41d2e-106">Having a well-known identifier makes it easier for assistive technology devices to determine what types of controls are available in the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] and how to interact with the controls.</span></span>  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a><span data-ttu-id="41d2e-107">Conditions requises pour le type de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="41d2e-107">UI Automation Control Type Requisites</span></span>  
 <span data-ttu-id="41d2e-108">Les types de contrôles[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] fournissent un jeu de conditions que les fournisseurs doivent satisfaire.</span><span class="sxs-lookup"><span data-stu-id="41d2e-108">[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] control types provide a set of conditions that providers must meet.</span></span> <span data-ttu-id="41d2e-109">Quand ces conditions sont remplies, le contrôle peut utiliser le nom du type de contrôle spécifique.</span><span class="sxs-lookup"><span data-stu-id="41d2e-109">When these conditions are met, the control can use the specific control type name.</span></span> <span data-ttu-id="41d2e-110">Chaque type de contrôle présente des conditions pour les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="41d2e-110">Each control type has conditions for the following:</span></span>  
  
- <span data-ttu-id="41d2e-111">Modèles de contrôle[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ; quels modèles de contrôle doivent être pris en charge, lesquels sont facultatifs et lesquels ne doivent pas être pris en charge par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="41d2e-111">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] control patterns—which control patterns must be supported, which control patterns are optional, and which control patterns must not be supported by the control.</span></span>  
  
- <span data-ttu-id="41d2e-112">Valeurs de propriété[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ; quelles valeurs de propriété sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="41d2e-112">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] property values—which property values are supported.</span></span>  
  
- <span data-ttu-id="41d2e-113">Arborescence[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ; l'arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nécessaire pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="41d2e-113">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure—the required [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure for the control.</span></span>  
  
 <span data-ttu-id="41d2e-114">Quand un contrôle satisfait les conditions d'un type de contrôle particulier, la valeur de propriété <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> indique ce type de contrôle.</span><span class="sxs-lookup"><span data-stu-id="41d2e-114">When a control meets the conditions for a particular control type, the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> property value will indicate that control type.</span></span>  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a><span data-ttu-id="41d2e-115">Types de contrôle UI Automation actuels</span><span class="sxs-lookup"><span data-stu-id="41d2e-115">Current UI Automation Control Types</span></span>  
 <span data-ttu-id="41d2e-116">La liste suivante contient les différents types de contrôle [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] actuels :</span><span class="sxs-lookup"><span data-stu-id="41d2e-116">The following list contains the current set of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] control types:</span></span>  
  
- [<span data-ttu-id="41d2e-117">Prise en charge d’UI Automation pour le type de contrôle Button</span><span class="sxs-lookup"><span data-stu-id="41d2e-117">UI Automation Support for the Button Control Type</span></span>](ui-automation-support-for-the-button-control-type.md)  
  
- [<span data-ttu-id="41d2e-118">Prise en charge d’UI Automation pour le type de contrôle Calendar</span><span class="sxs-lookup"><span data-stu-id="41d2e-118">UI Automation Support for the Calendar Control Type</span></span>](ui-automation-support-for-the-calendar-control-type.md)  
  
- [<span data-ttu-id="41d2e-119">Prise en charge d’UI Automation pour le type de contrôle CheckBox</span><span class="sxs-lookup"><span data-stu-id="41d2e-119">UI Automation Support for the CheckBox Control Type</span></span>](ui-automation-support-for-the-checkbox-control-type.md)  
  
- [<span data-ttu-id="41d2e-120">Prise en charge d’UI Automation pour le type de contrôle ComboBox</span><span class="sxs-lookup"><span data-stu-id="41d2e-120">UI Automation Support for the ComboBox Control Type</span></span>](ui-automation-support-for-the-combobox-control-type.md)  
  
- [<span data-ttu-id="41d2e-121">Prise en charge d’UI Automation pour le type de contrôle DataGrid</span><span class="sxs-lookup"><span data-stu-id="41d2e-121">UI Automation Support for the DataGrid Control Type</span></span>](ui-automation-support-for-the-datagrid-control-type.md)  
  
- [<span data-ttu-id="41d2e-122">Prise en charge d’UI Automation pour le type de contrôle DataItem</span><span class="sxs-lookup"><span data-stu-id="41d2e-122">UI Automation Support for the DataItem Control Type</span></span>](ui-automation-support-for-the-dataitem-control-type.md)  
  
- [<span data-ttu-id="41d2e-123">Prise en charge d’UI Automation pour le type de contrôle Document</span><span class="sxs-lookup"><span data-stu-id="41d2e-123">UI Automation Support for the Document Control Type</span></span>](ui-automation-support-for-the-document-control-type.md)  
  
- [<span data-ttu-id="41d2e-124">Prise en charge d’UI Automation pour le type de contrôle Edit</span><span class="sxs-lookup"><span data-stu-id="41d2e-124">UI Automation Support for the Edit Control Type</span></span>](ui-automation-support-for-the-edit-control-type.md)  
  
- [<span data-ttu-id="41d2e-125">Prise en charge d’UI Automation pour le type de contrôle Group</span><span class="sxs-lookup"><span data-stu-id="41d2e-125">UI Automation Support for the Group Control Type</span></span>](ui-automation-support-for-the-group-control-type.md)  
  
- [<span data-ttu-id="41d2e-126">Prise en charge d’UI Automation pour le type de contrôle Header</span><span class="sxs-lookup"><span data-stu-id="41d2e-126">UI Automation Support for the Header Control Type</span></span>](ui-automation-support-for-the-header-control-type.md)  
  
- [<span data-ttu-id="41d2e-127">Prise en charge d’UI Automation pour le type de contrôle HeaderItem</span><span class="sxs-lookup"><span data-stu-id="41d2e-127">UI Automation Support for the HeaderItem Control Type</span></span>](ui-automation-support-for-the-headeritem-control-type.md)  
  
- [<span data-ttu-id="41d2e-128">Prise en charge d’UI Automation pour le type de contrôle Hyperlink</span><span class="sxs-lookup"><span data-stu-id="41d2e-128">UI Automation Support for the Hyperlink Control Type</span></span>](ui-automation-support-for-the-hyperlink-control-type.md)  
  
- [<span data-ttu-id="41d2e-129">Prise en charge d’UI Automation pour le type de contrôle Image</span><span class="sxs-lookup"><span data-stu-id="41d2e-129">UI Automation Support for the Image Control Type</span></span>](ui-automation-support-for-the-image-control-type.md)  
  
- [<span data-ttu-id="41d2e-130">Prise en charge d’UI Automation pour le type de contrôle List</span><span class="sxs-lookup"><span data-stu-id="41d2e-130">UI Automation Support for the List Control Type</span></span>](ui-automation-support-for-the-list-control-type.md)  
  
- [<span data-ttu-id="41d2e-131">Prise en charge d’UI Automation pour le type de contrôle ListItem</span><span class="sxs-lookup"><span data-stu-id="41d2e-131">UI Automation Support for the ListItem Control Type</span></span>](ui-automation-support-for-the-listitem-control-type.md)  
  
- [<span data-ttu-id="41d2e-132">Prise en charge d’UI Automation pour le type de contrôle Menu</span><span class="sxs-lookup"><span data-stu-id="41d2e-132">UI Automation Support for the Menu Control Type</span></span>](ui-automation-support-for-the-menu-control-type.md)  
  
- [<span data-ttu-id="41d2e-133">Prise en charge d’UI Automation pour le type de contrôle MenuBar</span><span class="sxs-lookup"><span data-stu-id="41d2e-133">UI Automation Support for the MenuBar Control Type</span></span>](ui-automation-support-for-the-menubar-control-type.md)  
  
- [<span data-ttu-id="41d2e-134">Prise en charge d’UI Automation pour le type de contrôle MenuItem</span><span class="sxs-lookup"><span data-stu-id="41d2e-134">UI Automation Support for the MenuItem Control Type</span></span>](ui-automation-support-for-the-menuitem-control-type.md)  
  
- [<span data-ttu-id="41d2e-135">Prise en charge d’UI Automation pour le type de contrôle Pane</span><span class="sxs-lookup"><span data-stu-id="41d2e-135">UI Automation Support for the Pane Control Type</span></span>](ui-automation-support-for-the-pane-control-type.md)  
  
- [<span data-ttu-id="41d2e-136">Prise en charge d’UI Automation pour le type de contrôle ProgressBar</span><span class="sxs-lookup"><span data-stu-id="41d2e-136">UI Automation Support for the ProgressBar Control Type</span></span>](ui-automation-support-for-the-progressbar-control-type.md)  
  
- [<span data-ttu-id="41d2e-137">Prise en charge d’UI Automation pour le type de contrôle RadioButton</span><span class="sxs-lookup"><span data-stu-id="41d2e-137">UI Automation Support for the RadioButton Control Type</span></span>](ui-automation-support-for-the-radiobutton-control-type.md)  
  
- [<span data-ttu-id="41d2e-138">Prise en charge d’UI Automation pour le type de contrôle ScrollBar</span><span class="sxs-lookup"><span data-stu-id="41d2e-138">UI Automation Support for the ScrollBar Control Type</span></span>](ui-automation-support-for-the-scrollbar-control-type.md)  
  
- [<span data-ttu-id="41d2e-139">Prise en charge d’UI Automation pour le type de contrôle Separator</span><span class="sxs-lookup"><span data-stu-id="41d2e-139">UI Automation Support for the Separator Control Type</span></span>](ui-automation-support-for-the-separator-control-type.md)  
  
- [<span data-ttu-id="41d2e-140">Prise en charge d’UI Automation pour le type de contrôle Slider</span><span class="sxs-lookup"><span data-stu-id="41d2e-140">UI Automation Support for the Slider Control Type</span></span>](ui-automation-support-for-the-slider-control-type.md)  
  
- [<span data-ttu-id="41d2e-141">Prise en charge d’UI Automation pour le type de contrôle Spinner</span><span class="sxs-lookup"><span data-stu-id="41d2e-141">UI Automation Support for the Spinner Control Type</span></span>](ui-automation-support-for-the-spinner-control-type.md)  
  
- [<span data-ttu-id="41d2e-142">Prise en charge d’UI Automation pour le type de contrôle SplitButton</span><span class="sxs-lookup"><span data-stu-id="41d2e-142">UI Automation Support for the SplitButton Control Type</span></span>](ui-automation-support-for-the-splitbutton-control-type.md)  
  
- [<span data-ttu-id="41d2e-143">Prise en charge d’UI Automation pour le type de contrôle StatusBar</span><span class="sxs-lookup"><span data-stu-id="41d2e-143">UI Automation Support for the StatusBar Control Type</span></span>](ui-automation-support-for-the-statusbar-control-type.md)  
  
- [<span data-ttu-id="41d2e-144">Prise en charge d’UI Automation pour le type de contrôle Tab</span><span class="sxs-lookup"><span data-stu-id="41d2e-144">UI Automation Support for the Tab Control Type</span></span>](ui-automation-support-for-the-tab-control-type.md)  
  
- [<span data-ttu-id="41d2e-145">Prise en charge d’UI Automation pour le type de contrôle TabItem</span><span class="sxs-lookup"><span data-stu-id="41d2e-145">UI Automation Support for the TabItem Control Type</span></span>](ui-automation-support-for-the-tabitem-control-type.md)  
  
- [<span data-ttu-id="41d2e-146">Prise en charge d’UI Automation pour le type de contrôle Table</span><span class="sxs-lookup"><span data-stu-id="41d2e-146">UI Automation Support for the Table Control Type</span></span>](ui-automation-support-for-the-table-control-type.md)  
  
- [<span data-ttu-id="41d2e-147">Prise en charge d’UI Automation pour le type de contrôle Text</span><span class="sxs-lookup"><span data-stu-id="41d2e-147">UI Automation Support for the Text Control Type</span></span>](ui-automation-support-for-the-text-control-type.md)  
  
- [<span data-ttu-id="41d2e-148">Prise en charge d’UI Automation pour le type de contrôle Thumb</span><span class="sxs-lookup"><span data-stu-id="41d2e-148">UI Automation Support for the Thumb Control Type</span></span>](ui-automation-support-for-the-thumb-control-type.md)  
  
- [<span data-ttu-id="41d2e-149">Prise en charge d’UI Automation pour le type de contrôle TitleBar</span><span class="sxs-lookup"><span data-stu-id="41d2e-149">UI Automation Support for the TitleBar Control Type</span></span>](ui-automation-support-for-the-titlebar-control-type.md)  
  
- [<span data-ttu-id="41d2e-150">Prise en charge d’UI Automation pour le type de contrôle ToolBar</span><span class="sxs-lookup"><span data-stu-id="41d2e-150">UI Automation Support for the ToolBar Control Type</span></span>](ui-automation-support-for-the-toolbar-control-type.md)  
  
- [<span data-ttu-id="41d2e-151">Prise en charge d’UI Automation pour le type de contrôle ToolTip</span><span class="sxs-lookup"><span data-stu-id="41d2e-151">UI Automation Support for the ToolTip Control Type</span></span>](ui-automation-support-for-the-tooltip-control-type.md)  
  
- [<span data-ttu-id="41d2e-152">Prise en charge d’UI Automation pour le type de contrôle Tree</span><span class="sxs-lookup"><span data-stu-id="41d2e-152">UI Automation Support for the Tree Control Type</span></span>](ui-automation-support-for-the-tree-control-type.md)  
  
- [<span data-ttu-id="41d2e-153">Prise en charge d’UI Automation pour le type de contrôle TreeItem</span><span class="sxs-lookup"><span data-stu-id="41d2e-153">UI Automation Support for the TreeItem Control Type</span></span>](ui-automation-support-for-the-treeitem-control-type.md)  
  
- [<span data-ttu-id="41d2e-154">Prise en charge d’UI Automation pour le type de contrôle Window</span><span class="sxs-lookup"><span data-stu-id="41d2e-154">UI Automation Support for the Window Control Type</span></span>](ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a><span data-ttu-id="41d2e-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41d2e-155">See also</span></span>

- <xref:System.Windows.Automation.ControlType>
