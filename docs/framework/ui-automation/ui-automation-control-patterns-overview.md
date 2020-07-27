---
title: Vue d'ensemble des modèles de contrôle UI Automation
description: Consultez une vue d’ensemble des modèles de contrôle UI Automation. Les modèles de contrôle vous permettent de catégoriser et d’exposer les fonctionnalités d’un contrôle, indépendamment du type ou de l’apparence.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns
- UI Automation, control patterns
ms.assetid: cc229b33-234b-469b-ad60-f0254f32d45d
ms.openlocfilehash: d0df24de4f8a877405dfecb6b0d245ff1caf0418
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163884"
---
# <a name="ui-automation-control-patterns-overview"></a>Vue d'ensemble des modèles de contrôle UI Automation
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette vue d’ensemble présente les modèles de contrôle [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] . Les modèles de contrôle permettent de catégoriser et d'exposer les fonctionnalités d'un contrôle, indépendamment du type de contrôle ou de l'apparence du contrôle.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] utilise des modèles de contrôle pour représenter les comportements de contrôle courants. Par exemple, vous utilisez le modèle de contrôle Invoke pour les contrôles qui peuvent être appelés (tels que les boutons) et le modèle de contrôle Scroll pour les contrôles qui disposent de barres de défilement (tels que les zones de liste, les affichages de liste ou les zones de liste modifiables). Étant donné que chaque modèle de contrôle représente une fonctionnalité distincte, il est possible de les combiner pour décrire l’ensemble complet de fonctionnalités prises en charge par un contrôle particulier.  
  
> [!NOTE]
> Les contrôles d’agrégat (générés avec des contrôles enfants qui fournissent l’ [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] pour les fonctionnalités exposées par le parent) doivent implémenter tous les modèles de contrôle normalement associés à chaque contrôle enfant. Il n’est pas nécessaire que ces mêmes modèles de contrôle soient, à leur tour, implémentés par les contrôles enfants.  
  
<a name="uiautomation_control_pattern_includes"></a>
## <a name="ui-automation-control-pattern-components"></a>Composants des modèles de contrôle UI Automation  
 Les modèles de contrôle prennent en charge les méthodes, les propriétés, les événements et les relations nécessaires pour définir une partie discrète des fonctionnalités disponibles dans un contrôle.  
  
- La relation entre un élément UI Automation et son parent, ses enfants et ses frères décrit la structure de l’élément dans l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
- Les méthodes permettent aux clients UI Automation de manipuler le contrôle.  
  
- Les propriétés et les événements fournissent des informations sur les fonctionnalités du modèle de contrôle, ainsi que des informations sur l’état du contrôle.  
  
 Les modèles de contrôle sont liés à [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] car les interfaces sont liées aux objets COM (Component Object Model). Dans COM, vous pouvez interroger un objet et lui demander quelles interfaces il prend en charge, puis vous servir de ces interfaces pour accéder aux fonctionnalités. Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], les clients UI Automation peuvent demander à un contrôle les modèles de contrôle qu’il prend en charge, puis interagir avec le contrôle via les propriétés, les méthodes, les événements et les structures exposées par les modèles de contrôle pris en charge. Par exemple, pour une zone d’édition multiligne, les fournisseurs UI Automation implémentent <xref:System.Windows.Automation.Provider.IScrollProvider>. Lorsqu’un client sait qu’un <xref:System.Windows.Automation.AutomationElement> prend en charge le modèle de contrôle <xref:System.Windows.Automation.ScrollPattern> , il peut utiliser les propriétés, les méthodes et les événements exposés par ce modèle de contrôle pour manipuler le contrôle ou accéder aux informations concernant le contrôle.  
  
<a name="uiautomation_control_pattern_client_provider"></a>
## <a name="ui-automation-providers-and-clients"></a>Fournisseurs et clients UI Automation  
 Les fournisseurs UI Automation implémentent des modèles de contrôle pour exposer le comportement approprié d’une partie spécifique des fonctionnalités prises en charge par le contrôle.  
  
 Les clients UI Automation accèdent aux méthodes et aux propriétés des classes de modèle de contrôle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] et les utilisent pour obtenir des informations sur l’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]ou pour manipuler l’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Ces classes de modèle de contrôle se trouvent dans l’espace de noms <xref:System.Windows.Automation> (par exemple, <xref:System.Windows.Automation.InvokePattern> et <xref:System.Windows.Automation.SelectionPattern>).  
  
 Les clients utilisent des <xref:System.Windows.Automation.AutomationElement> méthodes (telles que <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> ou <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> ) ou les accesseurs Common Language Runtime (CLR) pour accéder aux [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Propriétés sur un modèle. Chaque classe de modèle de contrôle a un membre de champ (par exemple, <xref:System.Windows.Automation.InvokePattern.Pattern?displayProperty=nameWithType> ou <xref:System.Windows.Automation.SelectionPattern.Pattern?displayProperty=nameWithType> ) qui identifie ce modèle de contrôle et peut être passé en tant que paramètre à <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> ou <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> pour récupérer ce modèle pour un <xref:System.Windows.Automation.AutomationElement> .  
  
<a name="uiautomation_control_patterns_dynamic"></a>
## <a name="dynamic-control-patterns"></a>Modèles de contrôle dynamique  
 Certains contrôles ne prennent pas toujours en charge le même ensemble de modèles de contrôle. Les modèles de contrôle sont considérés comme pris en charge lorsqu’ils sont disponibles pour un client UI Automation. Par exemple, une zone d’édition multiligne ne permet un défilement vertical que lorsqu’elle contient plus de lignes de texte que ne peut en afficher sa zone affichable. Le défilement est désactivé lorsque tout le texte peut s’afficher dans la zone prévue à cet effet. Pour cet exemple, le modèle de contrôle ScrollPattern est pris en charge de manière dynamique en fonction de l’état actuel du contrôle (la quantité de texte présente dans la zone d’édition).  
  
<a name="Control_Pattern_Classes_and_Interfaces"></a>
## <a name="control-pattern-classes-and-interfaces"></a>Interfaces et classes du modèle de contrôle  
 Le tableau suivant décrit les modèles de contrôle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Il répertorie également les classes utilisées par les clients UI Automation pour accéder aux modèles de contrôle, ainsi que les interfaces utilisées par les fournisseurs UI Automation pour les implémenter.  
  
|Classe du modèle de contrôle|Interface du fournisseur|Description|  
|---------------------------|------------------------|-----------------|  
|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.Provider.IDockProvider>|Utilisées pour les contrôles qui peuvent être ancrés dans un conteneur d’ancrage. Par exemple, les barres d’outils ou les palettes d’outils.|  
|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Utilisées pour les contrôles qui peuvent être développés ou réduits. Par exemple, les éléments de menu dans une application, comme le menu **Fichier** .|  
|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.Provider.IGridProvider>|Utilisées pour les contrôles qui prennent en charge des fonctionnalités de grille telles que le dimensionnement et le déplacement vers une cellule spécifiée. Par exemple, la vue grande icône dans l’Explorateur Windows ou les tableaux simples sans en-têtes dans Microsoft Word.|  
|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Utilisées pour les contrôles dont les grilles contiennent des cellules. Les cellules individuelles doivent prendre en charge le modèle GridItem. Par exemple, chaque cellule dans l’affichage détaillé de l’Explorateur Microsoft Windows.|  
|<xref:System.Windows.Automation.InvokePattern>|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Utilisées pour les contrôles qui peuvent être appelés, tel qu’un bouton.|  
|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Utilisées pour les contrôles qui peuvent basculer entre plusieurs représentations du même ensemble d’informations, de données ou d’enfants. Par exemple, un contrôle list view où les données sont disponibles en affichage Miniatures, Mosaïques, Icônes, Liste ou Détails.|  
|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Utilisées pour les contrôles disposant d’une plage de valeurs qui peut s’appliquer au contrôle. Par exemple, un contrôle spinner contenant des années peut avoir une plage comprise entre 1900 et 2010, alors qu’un autre contrôle spinner représentant des mois aura une plage comprise entre 1 et 12.|  
|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.Provider.IScrollProvider>|Utilisées pour les contrôles qui peuvent défiler. Par exemple, un contrôle disposant de barres de défilement qui sont actives lorsque la quantité d’informations est trop importante pour être affichée dans la zone affichable du contrôle.|  
|<xref:System.Windows.Automation.ScrollItemPattern>|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Utilisées pour les contrôles qui disposent d’éléments individuels dans une liste déroulante. Par exemple, un contrôle de liste qui dispose d’éléments individuels dans la liste déroulante, comme un contrôle zone de liste déroulante.|  
|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Utilisées pour les contrôles conteneur de sélection. Par exemple, les zones de liste et zones de liste modifiable.|  
|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Utilisées pour les éléments individuels dans les contrôles conteneur de sélection, tels que les zones de liste et zones de liste modifiables.|  
|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.Provider.ITableProvider>|Utilisées pour les contrôles qui disposent d’une grille ainsi que d’informations d’en-tête. Par exemple, les feuilles de calcul Microsoft Excel.|  
|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Utilisées pour les éléments d’une table.|  
|<xref:System.Windows.Automation.TextPattern>|<xref:System.Windows.Automation.Provider.ITextProvider>|Utilisées pour les contrôles d’édition et les documents qui exposent des informations textuelles.|  
|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.Provider.IToggleProvider>|Utilisées pour les contrôles dont l’état peut être activé et désactivé. Par exemple, les cases à cocher et les éléments de menu pouvant être activés.|  
|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.Provider.ITransformProvider>|Utilisées pour les contrôles qui peuvent être redimensionnés, déplacés et pivotés. Les utilisations courantes du modèle de contrôle Transform se font dans les concepteurs, les formulaires les éditeurs graphiques et les applications de dessin.|  
|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.Provider.IValueProvider>|Permet aux clients d’obtenir ou de définir une valeur sur des contrôles qui ne prennent pas en charge une plage de valeurs. Par exemple, un sélecteur de date et heure.|  
|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.Provider.IWindowProvider>|Expose des informations spécifiques aux fenêtres, concept fondamental du système d’exploitation Microsoft Windows. Les fenêtres d’application de niveau supérieur (Microsoft Word, Explorateur Microsoft Windows, etc.), les fenêtres enfants MDI et les boîtes de dialogue sont des exemples de contrôles qui sont des fenêtres.|  
  
## <a name="see-also"></a>Voir aussi

- [Modèles de contrôle UI Automation pour les clients](ui-automation-control-patterns-for-clients.md)
- [Mappage de modèle de contrôle pour les clients UI Automation](control-pattern-mapping-for-ui-automation-clients.md)
- [Vue d'ensemble d'UI Automation](ui-automation-overview.md)
- [Propriétés UI Automation pour les clients](ui-automation-properties-for-clients.md)
- [Événements UI Automation pour les clients](ui-automation-events-for-clients.md)
