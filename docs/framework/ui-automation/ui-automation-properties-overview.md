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
# <a name="ui-automation-properties-overview"></a>Vue d'ensemble des propriétés UI Automation
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Les fournisseurs UI Automation exposent des propriétés sur des éléments [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] . Ces propriétés permettent aux applications clientes UI Automation de découvrir des informations sur des parties de l’ [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], en particulier les contrôles (données statiques et dynamiques comprises).  
  
 Cette section offre une vue générale des propriétés [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] . Des informations plus spécifiques sont disponibles dans les rubriques suivantes :  
  
- [Propriétés UI Automation pour les clients](ui-automation-properties-for-clients.md)  
  
- [Implémentation de fournisseur UI Automation côté serveur](server-side-ui-automation-provider-implementation.md)  
  
<a name="Property_Identifiers"></a>
## <a name="property-identifiers"></a>Identificateurs de propriété  
 Chaque propriété est identifiée par un numéro et un nom. Les noms de propriétés sont utilisés uniquement pour le débogage et le diagnostic. Les fournisseurs utilisent les ID numériques pour identifier les demandes de propriété entrantes. Les applications clientes, toutefois, utilisent uniquement <xref:System.Windows.Automation.AutomationProperty>, qui encapsule le numéro et le nom, pour identifier les propriétés qu’elles souhaitent récupérer.  
  
 Les objets<xref:System.Windows.Automation.AutomationProperty> qui représentent des propriétés particulières sont disponibles sous forme de champs dans différentes classes. Pour des raisons de sécurité, les fournisseurs UI Automation obtiennent ces objets à partir d’un ensemble distinct de classes contenues dans Uiautomationtypes.dll.  
  
 Le tableau suivant classe les propriétés selon les classes qui contiennent les <xref:System.Windows.Automation.AutomationProperty> ID.  
  
|Types de propriétés|Les clients obtiennent les ID par le biais de|Les fournisseurs obtiennent les ID par le biais de|  
|-------------------------|--------------------------|----------------------------|  
|Propriétés communes à tous les éléments (consultez les tableaux suivants)|<xref:System.Windows.Automation.AutomationElement>|<xref:System.Windows.Automation.AutomationElementIdentifiers>|  
|Position d’une fenêtre d’ancrage|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.DockPatternIdentifiers>|  
|État d’un élément que vous pouvez développer et réduire|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers>|  
|Propriétés d’un élément dans une grille|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.GridItemPatternIdentifiers>|  
|Propriétés d’une grille|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.GridPatternIdentifiers>|  
|Affichage actuel pris en charge d’un élément disposant de plusieurs affichages|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers>|  
|Propriétés d’un élément se déplaçant dans une plage de valeurs, comme un curseur|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.RangeValuePatternIdentifiers>|  
|Propriétés d’une fenêtre de défilement|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.ScrollPatternIdentifiers>|  
|État et conteneur d’un élément pouvant être sélectionné, comme dans une liste|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers>|  
|Propriétés d’un contrôle contenant des éléments de sélection|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.SelectionPatternIdentifiers>|  
|En-têtes de ligne et de colonne d’un élément dans une table|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.TableItemPatternIdentifiers>|  
|En-têtes de ligne et de colonne et orientation d’une table|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.TablePatternIdentifiers>|  
|État d’un contrôle de basculement|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.TogglePatternIdentifiers>|  
|Fonctionnalités d’un élément pouvant être déplacé, pivoté ou redimensionné|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.TransformPatternIdentifiers>|  
|Valeur et fonctionnalités de lecture/d’écriture d’un élément ayant une valeur|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.ValuePatternIdentifiers>|  
|Fonctionnalités et état d’une fenêtre|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.WindowPatternIdentifiers>|  
  
<a name="Properties_by_Category"></a>
## <a name="properties-by-category"></a>Propriétés par catégorie  
 Les tableaux suivants catégorisent les propriétés dont les ID sont trouvés dans <xref:System.Windows.Automation.AutomationElement> et <xref:System.Windows.Automation.AutomationElementIdentifiers> . Ces propriétés sont communes à tous les contrôles. Toutefois, certaines d’entre elles sont susceptibles d’être statiques pendant la durée de vie de l’application fournisseur. Les propriétés les plus dynamiques sont associées à des modèles de contrôle.  
  
 La colonne **Accès à la propriété** répertorie tous les autres accesseurs pour chaque propriété, en plus de <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> et <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>. Pour plus d’informations sur l’obtention des propriétés d’une application cliente, consultez [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).  
  
> [!NOTE]
> Pour obtenir des informations spécifiques sur chaque propriété, suivez le lien de la colonne **Accès à la propriété** .  
  
### <a name="display-characteristics"></a>Caractéristiques d’affichage  
  
|Identificateur de propriété|Accès à la propriété|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>|  
|<xref:System.Windows.Automation.AutomationElement.CultureProperty>|n/a|  
|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsOffscreen%2A>|  
|<xref:System.Windows.Automation.AutomationElement.OrientationProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Orientation%2A>|  
  
### <a name="element-type"></a>Type d'élément  
  
|Identificateur de propriété|Accès à la propriété|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsContentElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsControlElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LocalizedControlType%2A>|  
  
### <a name="identification"></a>Identification  
  
|Identificateur de propriété|Accès à la propriété|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClassNameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ClassName%2A>|  
|<xref:System.Windows.Automation.AutomationElement.FrameworkIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.FrameworkId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LabeledByProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LabeledBy%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ProcessIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ProcessId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.RuntimeIdProperty>|<xref:System.Windows.Automation.AutomationElement.GetRuntimeId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NativeWindowHandleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.NativeWindowHandle%2A>|  
  
### <a name="interaction"></a>Interaction  
  
|Identificateur de propriété|Accès à la propriété|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AcceleratorKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AccessKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>|<xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>|  
|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HasKeyboardFocus%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsEnabled%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsKeyboardFocusable%2A>|  
  
### <a name="support-for-patterns"></a>Prise en charge des modèles  
  
|Identificateur de propriété|Accès à la propriété|  
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
  
### <a name="miscellaneous"></a>Divers  
  
|Identificateur de propriété|Accès à la propriété|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsRequiredForFormProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsRequiredForForm%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsPassword%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemStatusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemStatus%2A>|  
  
<a name="Localization"></a>
## <a name="localization"></a>Localisation  
 Les fournisseurs[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] doivent présenter les propriétés suivantes dans la langue du système d’exploitation :  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
<a name="Properties_and_Events"></a>
## <a name="properties-and-events"></a>Propriétés et événements  
 Le concept des événements de modification de propriété est étroitement lié aux propriétés d’ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Pour les propriétés dynamiques, l’application cliente a besoin d’un moyen de savoir si une valeur de propriété a changé, afin de pouvoir mettre à jour son cache d’informations ou réagir aux nouvelles informations d’une autre manière.  
  
 Les fournisseurs déclenchent des événements quand l’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] est modifiée. Par exemple, si une case est cochée ou décochée, un événement de modification de propriété est déclenché par l’implémentation du modèle Toggle par le fournisseur. Les fournisseurs peuvent déclencher des événements de manière sélective, selon que les clients écoutent tous les événements ou seulement des événements spécifiques.  
  
 Toutes les modifications de propriété ne déclenchent pas nécessairement des événements. Cela dépend entièrement de l’implémentation du fournisseur UI Automation pour l’élément. Par exemple, les fournisseurs de proxys standard pour les zones de liste ne déclenchent pas d’événement quand la propriété <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> est modifiée. Dans ce cas, l’application doit plutôt écouter un <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>.  
  
 Les clients écoutent des événements en s’y abonnant. L’abonnement à des événements revient à créer des méthodes déléguées capables de gérer les événements et à passer ces méthodes à [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] avec les événements spécifiques qu’elles devront traiter. Pour les événements de modification de propriété en particulier, les clients doivent implémenter <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>.  
  
## <a name="see-also"></a>Voir aussi

- [Mise en cache dans les clients UI Automation](caching-in-ui-automation-clients.md)
- [Propriétés UI Automation pour les clients](ui-automation-properties-for-clients.md)
- [Implémentation de fournisseur UI Automation côté serveur](server-side-ui-automation-provider-implementation.md)
- [Rechercher un élément UI Automation basé sur une condition de propriété](find-a-ui-automation-element-based-on-a-property-condition.md)
- [Retourner les propriétés d'un fournisseur UI Automation](return-properties-from-a-ui-automation-provider.md)
- [Déclencher des événements à partir d'un fournisseur UI Automation](raise-events-from-a-ui-automation-provider.md)
