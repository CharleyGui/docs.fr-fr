---
title: Vue d'ensemble des propriétés UI Automation
description: Consultez une vue d’ensemble générale des propriétés de Microsoft UI Automation. En savoir plus sur les identificateurs de propriété, les propriétés par catégorie, la localisation, les propriétés et les événements.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, properties
- properties, UI Automation
ms.assetid: a6c31d7b-b33e-49b3-b5c1-31a345f9b7c8
ms.openlocfilehash: 17d780c059530be8c91890302ea4066de2d4aa73
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163204"
---
# <a name="ui-automation-properties-overview"></a><span data-ttu-id="74739-104">Vue d'ensemble des propriétés UI Automation</span><span class="sxs-lookup"><span data-stu-id="74739-104">UI Automation Properties Overview</span></span>
> [!NOTE]
> <span data-ttu-id="74739-105">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="74739-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="74739-106">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="74739-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="74739-107">Les fournisseurs UI Automation exposent des propriétés sur des éléments [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="74739-107">UI Automation providers expose properties on [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements.</span></span> <span data-ttu-id="74739-108">Ces propriétés permettent aux applications clientes UI Automation de découvrir des informations sur des parties de l’ [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], en particulier les contrôles (données statiques et dynamiques comprises).</span><span class="sxs-lookup"><span data-stu-id="74739-108">These properties enable UI Automation client applications to discover information about pieces of the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], especially controls, including both static and dynamic data.</span></span>  
  
 <span data-ttu-id="74739-109">Cette section offre une vue générale des propriétés [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="74739-109">This section gives a broad overview of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] properties.</span></span> <span data-ttu-id="74739-110">Des informations plus spécifiques sont disponibles dans les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="74739-110">More specific information is given in the following topics:</span></span>  
  
- [<span data-ttu-id="74739-111">Propriétés UI Automation pour les clients</span><span class="sxs-lookup"><span data-stu-id="74739-111">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)  
  
- [<span data-ttu-id="74739-112">Implémentation de fournisseur UI Automation côté serveur</span><span class="sxs-lookup"><span data-stu-id="74739-112">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)  
  
<a name="Property_Identifiers"></a>
## <a name="property-identifiers"></a><span data-ttu-id="74739-113">Identificateurs de propriété</span><span class="sxs-lookup"><span data-stu-id="74739-113">Property Identifiers</span></span>  
 <span data-ttu-id="74739-114">Chaque propriété est identifiée par un numéro et un nom.</span><span class="sxs-lookup"><span data-stu-id="74739-114">Every property is identified by a number and a name.</span></span> <span data-ttu-id="74739-115">Les noms de propriétés sont utilisés uniquement pour le débogage et le diagnostic.</span><span class="sxs-lookup"><span data-stu-id="74739-115">The names of properties are used only for debugging and diagnosis.</span></span> <span data-ttu-id="74739-116">Les fournisseurs utilisent les ID numériques pour identifier les demandes de propriété entrantes.</span><span class="sxs-lookup"><span data-stu-id="74739-116">Providers use the numeric IDs to identify incoming property requests.</span></span> <span data-ttu-id="74739-117">Les applications clientes, toutefois, utilisent uniquement <xref:System.Windows.Automation.AutomationProperty>, qui encapsule le numéro et le nom, pour identifier les propriétés qu’elles souhaitent récupérer.</span><span class="sxs-lookup"><span data-stu-id="74739-117">Client applications, however, only use <xref:System.Windows.Automation.AutomationProperty>, which encapsulates the number and name, to identify properties they wish to retrieve.</span></span>  
  
 <span data-ttu-id="74739-118">Les objets<xref:System.Windows.Automation.AutomationProperty> qui représentent des propriétés particulières sont disponibles sous forme de champs dans différentes classes.</span><span class="sxs-lookup"><span data-stu-id="74739-118"><xref:System.Windows.Automation.AutomationProperty> objects representing particular properties are available as fields in various classes.</span></span> <span data-ttu-id="74739-119">Pour des raisons de sécurité, les fournisseurs UI Automation obtiennent ces objets à partir d’un ensemble distinct de classes contenues dans Uiautomationtypes.dll.</span><span class="sxs-lookup"><span data-stu-id="74739-119">For security reasons, UI Automation providers obtain these objects from a separate set of classes that are contained in Uiautomationtypes.dll.</span></span>  
  
 <span data-ttu-id="74739-120">Le tableau suivant classe les propriétés selon les classes qui contiennent les <xref:System.Windows.Automation.AutomationProperty> ID.</span><span class="sxs-lookup"><span data-stu-id="74739-120">The following table categorizes properties by the classes that contain the <xref:System.Windows.Automation.AutomationProperty>IDs.</span></span>  
  
|<span data-ttu-id="74739-121">Types de propriétés</span><span class="sxs-lookup"><span data-stu-id="74739-121">Kinds of properties</span></span>|<span data-ttu-id="74739-122">Les clients obtiennent les ID par le biais de</span><span class="sxs-lookup"><span data-stu-id="74739-122">Clients get IDs from</span></span>|<span data-ttu-id="74739-123">Les fournisseurs obtiennent les ID par le biais de</span><span class="sxs-lookup"><span data-stu-id="74739-123">Providers get IDs from</span></span>|  
|-------------------------|--------------------------|----------------------------|  
|<span data-ttu-id="74739-124">Propriétés communes à tous les éléments (consultez les tableaux suivants)</span><span class="sxs-lookup"><span data-stu-id="74739-124">Properties common to all elements (see following tables)</span></span>|<xref:System.Windows.Automation.AutomationElement>|<xref:System.Windows.Automation.AutomationElementIdentifiers>|  
|<span data-ttu-id="74739-125">Position d’une fenêtre d’ancrage</span><span class="sxs-lookup"><span data-stu-id="74739-125">Position of a docking window</span></span>|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.DockPatternIdentifiers>|  
|<span data-ttu-id="74739-126">État d’un élément que vous pouvez développer et réduire</span><span class="sxs-lookup"><span data-stu-id="74739-126">State of an element that can expand and collapse</span></span>|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers>|  
|<span data-ttu-id="74739-127">Propriétés d’un élément dans une grille</span><span class="sxs-lookup"><span data-stu-id="74739-127">Properties of an item in a grid</span></span>|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.GridItemPatternIdentifiers>|  
|<span data-ttu-id="74739-128">Propriétés d’une grille</span><span class="sxs-lookup"><span data-stu-id="74739-128">Properties of a grid</span></span>|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.GridPatternIdentifiers>|  
|<span data-ttu-id="74739-129">Affichage actuel pris en charge d’un élément disposant de plusieurs affichages</span><span class="sxs-lookup"><span data-stu-id="74739-129">Current and supported view of an element that has multiple views</span></span>|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers>|  
|<span data-ttu-id="74739-130">Propriétés d’un élément se déplaçant dans une plage de valeurs, comme un curseur</span><span class="sxs-lookup"><span data-stu-id="74739-130">Properties of an element that moves over a range of values, such as a slider</span></span>|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.RangeValuePatternIdentifiers>|  
|<span data-ttu-id="74739-131">Propriétés d’une fenêtre de défilement</span><span class="sxs-lookup"><span data-stu-id="74739-131">Properties of a scrolling window</span></span>|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.ScrollPatternIdentifiers>|  
|<span data-ttu-id="74739-132">État et conteneur d’un élément pouvant être sélectionné, comme dans une liste</span><span class="sxs-lookup"><span data-stu-id="74739-132">Status and container of an item that can be selected, as in a list</span></span>|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers>|  
|<span data-ttu-id="74739-133">Propriétés d’un contrôle contenant des éléments de sélection</span><span class="sxs-lookup"><span data-stu-id="74739-133">Properties of a control that contains selection items</span></span>|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.SelectionPatternIdentifiers>|  
|<span data-ttu-id="74739-134">En-têtes de ligne et de colonne d’un élément dans une table</span><span class="sxs-lookup"><span data-stu-id="74739-134">Column and row headers of an item in a table</span></span>|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.TableItemPatternIdentifiers>|  
|<span data-ttu-id="74739-135">En-têtes de ligne et de colonne et orientation d’une table</span><span class="sxs-lookup"><span data-stu-id="74739-135">Column and row headers, and orientation, of a table</span></span>|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.TablePatternIdentifiers>|  
|<span data-ttu-id="74739-136">État d’un contrôle de basculement</span><span class="sxs-lookup"><span data-stu-id="74739-136">State of a toggle control</span></span>|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.TogglePatternIdentifiers>|  
|<span data-ttu-id="74739-137">Fonctionnalités d’un élément pouvant être déplacé, pivoté ou redimensionné</span><span class="sxs-lookup"><span data-stu-id="74739-137">Capabilities of an element that can be moved, rotated, or resized</span></span>|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.TransformPatternIdentifiers>|  
|<span data-ttu-id="74739-138">Valeur et fonctionnalités de lecture/d’écriture d’un élément ayant une valeur</span><span class="sxs-lookup"><span data-stu-id="74739-138">Value and read/write capabilities of an element that has a value</span></span>|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.ValuePatternIdentifiers>|  
|<span data-ttu-id="74739-139">Fonctionnalités et état d’une fenêtre</span><span class="sxs-lookup"><span data-stu-id="74739-139">Capabilities and state of a window</span></span>|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.WindowPatternIdentifiers>|  
  
<a name="Properties_by_Category"></a>
## <a name="properties-by-category"></a><span data-ttu-id="74739-140">Propriétés par catégorie</span><span class="sxs-lookup"><span data-stu-id="74739-140">Properties by Category</span></span>  
 <span data-ttu-id="74739-141">Les tableaux suivants catégorisent les propriétés dont les ID sont trouvés dans <xref:System.Windows.Automation.AutomationElement> et <xref:System.Windows.Automation.AutomationElementIdentifiers> .</span><span class="sxs-lookup"><span data-stu-id="74739-141">The following tables categorize the properties whose IDs are found in <xref:System.Windows.Automation.AutomationElement> and <xref:System.Windows.Automation.AutomationElementIdentifiers>.</span></span> <span data-ttu-id="74739-142">Ces propriétés sont communes à tous les contrôles.</span><span class="sxs-lookup"><span data-stu-id="74739-142">These properties are common to all controls.</span></span> <span data-ttu-id="74739-143">Toutefois, certaines d’entre elles sont susceptibles d’être statiques pendant la durée de vie de l’application fournisseur. Les propriétés les plus dynamiques sont associées à des modèles de contrôle.</span><span class="sxs-lookup"><span data-stu-id="74739-143">All but a few of them are likely to be static over the lifetime of the provider application; most dynamic properties are associated with control patterns.</span></span>  
  
 <span data-ttu-id="74739-144">La colonne **Accès à la propriété** répertorie tous les autres accesseurs pour chaque propriété, en plus de <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> et <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="74739-144">The **Property Access** column lists any other accessors for each property, in addition to <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> and <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>.</span></span> <span data-ttu-id="74739-145">Pour plus d’informations sur l’obtention des propriétés d’une application cliente, consultez [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).</span><span class="sxs-lookup"><span data-stu-id="74739-145">For more information on getting properties in a client application, see [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74739-146">Pour obtenir des informations spécifiques sur chaque propriété, suivez le lien de la colonne **Accès à la propriété** .</span><span class="sxs-lookup"><span data-stu-id="74739-146">For specific information about each property, follow the link in the **Property Access** column.</span></span>  
  
### <a name="display-characteristics"></a><span data-ttu-id="74739-147">Caractéristiques d’affichage</span><span class="sxs-lookup"><span data-stu-id="74739-147">Display Characteristics</span></span>  
  
|<span data-ttu-id="74739-148">Identificateur de propriété</span><span class="sxs-lookup"><span data-stu-id="74739-148">Property identifier</span></span>|<span data-ttu-id="74739-149">Accès à la propriété</span><span class="sxs-lookup"><span data-stu-id="74739-149">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>|  
|<xref:System.Windows.Automation.AutomationElement.CultureProperty>|<span data-ttu-id="74739-150">n/a</span><span class="sxs-lookup"><span data-stu-id="74739-150">n/a</span></span>|  
|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsOffscreen%2A>|  
|<xref:System.Windows.Automation.AutomationElement.OrientationProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Orientation%2A>|  
  
### <a name="element-type"></a><span data-ttu-id="74739-151">Type d'élément</span><span class="sxs-lookup"><span data-stu-id="74739-151">Element Type</span></span>  
  
|<span data-ttu-id="74739-152">Identificateur de propriété</span><span class="sxs-lookup"><span data-stu-id="74739-152">Property identifier</span></span>|<span data-ttu-id="74739-153">Accès à la propriété</span><span class="sxs-lookup"><span data-stu-id="74739-153">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsContentElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsControlElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LocalizedControlType%2A>|  
  
### <a name="identification"></a><span data-ttu-id="74739-154">Identification</span><span class="sxs-lookup"><span data-stu-id="74739-154">Identification</span></span>  
  
|<span data-ttu-id="74739-155">Identificateur de propriété</span><span class="sxs-lookup"><span data-stu-id="74739-155">Property identifier</span></span>|<span data-ttu-id="74739-156">Accès à la propriété</span><span class="sxs-lookup"><span data-stu-id="74739-156">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClassNameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ClassName%2A>|  
|<xref:System.Windows.Automation.AutomationElement.FrameworkIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.FrameworkId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LabeledByProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LabeledBy%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ProcessIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ProcessId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.RuntimeIdProperty>|<xref:System.Windows.Automation.AutomationElement.GetRuntimeId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NativeWindowHandleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.NativeWindowHandle%2A>|  
  
### <a name="interaction"></a><span data-ttu-id="74739-157">Interaction</span><span class="sxs-lookup"><span data-stu-id="74739-157">Interaction</span></span>  
  
|<span data-ttu-id="74739-158">Identificateur de propriété</span><span class="sxs-lookup"><span data-stu-id="74739-158">Property identifier</span></span>|<span data-ttu-id="74739-159">Accès à la propriété</span><span class="sxs-lookup"><span data-stu-id="74739-159">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AcceleratorKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AccessKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>|<xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>|  
|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HasKeyboardFocus%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsEnabled%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsKeyboardFocusable%2A>|  
  
### <a name="support-for-patterns"></a><span data-ttu-id="74739-160">Prise en charge des modèles</span><span class="sxs-lookup"><span data-stu-id="74739-160">Support for Patterns</span></span>  
  
|<span data-ttu-id="74739-161">Identificateur de propriété</span><span class="sxs-lookup"><span data-stu-id="74739-161">Property identifier</span></span>|<span data-ttu-id="74739-162">Accès à la propriété</span><span class="sxs-lookup"><span data-stu-id="74739-162">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsExpandCollapsePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsGridItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsGridPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsInvokePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsMultipleViewPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsRangeValuePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsScrollItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsScrollPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsSelectionItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsSelectionPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTableItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTablePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTogglePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTransformPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsValuePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsWindowPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
  
### <a name="miscellaneous"></a><span data-ttu-id="74739-163">Divers</span><span class="sxs-lookup"><span data-stu-id="74739-163">Miscellaneous</span></span>  
  
|<span data-ttu-id="74739-164">Identificateur de propriété</span><span class="sxs-lookup"><span data-stu-id="74739-164">Property identifier</span></span>|<span data-ttu-id="74739-165">Accès à la propriété</span><span class="sxs-lookup"><span data-stu-id="74739-165">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsRequiredForFormProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsRequiredForForm%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsPassword%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemStatusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemStatus%2A>|  
  
<a name="Localization"></a>
## <a name="localization"></a><span data-ttu-id="74739-166">Localisation</span><span class="sxs-lookup"><span data-stu-id="74739-166">Localization</span></span>  
 <span data-ttu-id="74739-167">Les fournisseurs[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] doivent présenter les propriétés suivantes dans la langue du système d’exploitation :</span><span class="sxs-lookup"><span data-stu-id="74739-167">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] providers should present the following properties in the language of the operating system:</span></span>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
<a name="Properties_and_Events"></a>
## <a name="properties-and-events"></a><span data-ttu-id="74739-168">Propriétés et événements</span><span class="sxs-lookup"><span data-stu-id="74739-168">Properties and Events</span></span>  
 <span data-ttu-id="74739-169">Le concept des événements de modification de propriété est étroitement lié aux propriétés d’ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="74739-169">Closely tied in with the properties in [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is the concept of property-changed events.</span></span> <span data-ttu-id="74739-170">Pour les propriétés dynamiques, l’application cliente a besoin d’un moyen de savoir si une valeur de propriété a changé, afin de pouvoir mettre à jour son cache d’informations ou réagir aux nouvelles informations d’une autre manière.</span><span class="sxs-lookup"><span data-stu-id="74739-170">For dynamic properties, the client application needs a way to know that a property value has changed, so that it can update its cache of information or react to the new information in some other way.</span></span>  
  
 <span data-ttu-id="74739-171">Les fournisseurs déclenchent des événements quand l’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] est modifiée.</span><span class="sxs-lookup"><span data-stu-id="74739-171">Providers raise events when something in the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] changes.</span></span> <span data-ttu-id="74739-172">Par exemple, si une case est cochée ou décochée, un événement de modification de propriété est déclenché par l’implémentation du modèle Toggle par le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="74739-172">For example, if a check box is selected or cleared, a property-changed event is raised by the provider's implementation of the Toggle pattern.</span></span> <span data-ttu-id="74739-173">Les fournisseurs peuvent déclencher des événements de manière sélective, selon que les clients écoutent tous les événements ou seulement des événements spécifiques.</span><span class="sxs-lookup"><span data-stu-id="74739-173">Providers can raise events selectively, depending on whether any clients are listening for events, or listening for specific events.</span></span>  
  
 <span data-ttu-id="74739-174">Toutes les modifications de propriété ne déclenchent pas nécessairement des événements. Cela dépend entièrement de l’implémentation du fournisseur UI Automation pour l’élément.</span><span class="sxs-lookup"><span data-stu-id="74739-174">Not all property changes raise events; that is entirely up to the implementation of the UI Automation provider for the element.</span></span> <span data-ttu-id="74739-175">Par exemple, les fournisseurs de proxys standard pour les zones de liste ne déclenchent pas d’événement quand la propriété <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> est modifiée.</span><span class="sxs-lookup"><span data-stu-id="74739-175">For example, the standard proxy providers for list boxes do not raise an event when the <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> changes.</span></span> <span data-ttu-id="74739-176">Dans ce cas, l’application doit plutôt écouter un <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>.</span><span class="sxs-lookup"><span data-stu-id="74739-176">In this case, the application instead must listen for an <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>.</span></span>  
  
 <span data-ttu-id="74739-177">Les clients écoutent des événements en s’y abonnant.</span><span class="sxs-lookup"><span data-stu-id="74739-177">Clients listen for events by subscribing to them.</span></span> <span data-ttu-id="74739-178">L’abonnement à des événements revient à créer des méthodes déléguées capables de gérer les événements et à passer ces méthodes à [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] avec les événements spécifiques qu’elles devront traiter.</span><span class="sxs-lookup"><span data-stu-id="74739-178">Subscribing to events means creating delegate methods that can handle the events, and then passing the methods to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] along with the specific events that will be dealt with in those methods.</span></span> <span data-ttu-id="74739-179">Pour les événements de modification de propriété en particulier, les clients doivent implémenter <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="74739-179">For property-changed events in particular, clients must implement <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74739-180">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74739-180">See also</span></span>

- [<span data-ttu-id="74739-181">Mise en cache dans les clients UI Automation</span><span class="sxs-lookup"><span data-stu-id="74739-181">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
- [<span data-ttu-id="74739-182">Propriétés UI Automation pour les clients</span><span class="sxs-lookup"><span data-stu-id="74739-182">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)
- [<span data-ttu-id="74739-183">Implémentation de fournisseur UI Automation côté serveur</span><span class="sxs-lookup"><span data-stu-id="74739-183">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
- [<span data-ttu-id="74739-184">Rechercher un élément UI Automation basé sur une condition de propriété</span><span class="sxs-lookup"><span data-stu-id="74739-184">Find a UI Automation Element Based on a Property Condition</span></span>](find-a-ui-automation-element-based-on-a-property-condition.md)
- [<span data-ttu-id="74739-185">Retourner les propriétés d'un fournisseur UI Automation</span><span class="sxs-lookup"><span data-stu-id="74739-185">Return Properties from a UI Automation Provider</span></span>](return-properties-from-a-ui-automation-provider.md)
- [<span data-ttu-id="74739-186">Déclencher des événements à partir d'un fournisseur UI Automation</span><span class="sxs-lookup"><span data-stu-id="74739-186">Raise Events from a UI Automation Provider</span></span>](raise-events-from-a-ui-automation-provider.md)
