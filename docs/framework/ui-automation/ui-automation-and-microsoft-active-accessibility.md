---
title: UI Automation et Microsoft Active Accessibility
ms.date: 03/30/2017
helpviewer_keywords:
- Active Accessibility
- UI Automation, Active Accessibility compared to
- UI Automation, Microsoft Active Accessibility
- Active Accessibility, UI Automation compared to
ms.assetid: 87bee662-0a3e-4232-a421-20e7a5968321
ms.openlocfilehash: 9a84c344ffabdaaa9d0aed68b05b7a4449776789
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179981"
---
# <a name="ui-automation-and-microsoft-active-accessibility"></a>UI Automation et Microsoft Active Accessibility
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Microsoft Active Accessibility était la solution antérieure pour rendre les applications accessibles. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]est le nouveau modèle d’accessibilité pour Microsoft Windows et vise à répondre aux besoins des produits de technologie d’assistance et des outils de test automatisés. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]offre de nombreuses améliorations par rapport à l’accessibilité active.  
  
 Ce sujet comprend les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] principales caractéristiques et explique comment ces caractéristiques diffèrent de l’accessibilité active.  
  
<a name="Programming_Languages_compare"></a>
## <a name="programming-languages"></a>Langages de programmation  
<Active Accessibility est basé sur le modèle d’objet composant (COM) avec prise en charge des doubles interfaces, et est donc programmable dans les langues de C/C, Microsoft Visual Basic 6.0 et scripting. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)](y compris la bibliothèque de fournisseurs côté client pour les contrôles standard) est écrit dans le code géré, et les applications client UI Automation sont plus facilement programmées à l’aide de C ou Visual Basic .NET. Les fournisseurs UI Automation, qui sont des implémentations d’interface, peuvent être écrits en code managé ou en C/C++.  
  
<a name="Support_in_Windows_Presentation_Foundation_"></a>
## <a name="support-in-windows-presentation-foundation"></a>Prise en charge dans Windows Presentation Foundation  
 Windows Presentation Foundation (WPF) est le nouveau modèle de création d’interfaces utilisateur. Les éléments du FMM ne contiennent pas de soutien autochtone pour l’accessibilité active; cependant, ils [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]appuient , ce qui comprend le soutien de transition pour les clients d’accessibilité active. Seuls les clients [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] spécialement conçus peuvent tirer pleinement parti des caractéristiques d’accessibilité de WPF, telles que le riche support pour le texte.  
  
<a name="Servers_and_Clients_compare"></a>
## <a name="servers-and-clients"></a>Serveurs et clients  
 Dans Active Accessibility, les serveurs et les clients communiquent `IAccessible`directement, en grande partie par la mise en œuvre du serveur de .  
  
 Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], un service principal se trouve entre le serveur (appelé fournisseur) et le client. Ce service appelle les interfaces implémentées par les fournisseurs et fournit des services supplémentaires tels que la génération d’identificateurs d’exécution uniques pour les éléments. Les applications clientes utilisent des fonctions de bibliothèque pour appeler le service [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
 Les fournisseurs d’automatisation de l’interface utilisateur peuvent fournir des informations aux clients d’accessibilité active, et les serveurs d’accessibilité active peuvent fournir des informations aux applications client UI Automation. Cependant, parce que l’accessibilité active [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]n’expose pas autant d’informations que, les deux modèles ne sont pas entièrement compatibles.  
  
<a name="UI_Elements_compare"></a>
## <a name="ui-elements"></a>Éléments de l'interface utilisateur  
 Active Accessibility [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] présente des `IAccessible` éléments soit comme une interface, soit comme identifiant pour enfants. Il est difficile de comparer deux pointeurs `IAccessible` pour déterminer s’ils font référence au même élément.  
  
 Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], chaque élément est représenté comme un objet <xref:System.Windows.Automation.AutomationElement> . La comparaison s’effectue à l’aide de l’opérateur d’égalité ou de la méthode <xref:System.Windows.Automation.AutomationElement.Equals%2A> , qui comparent tous les deux les identificateurs d’exécution uniques des éléments.  
  
<a name="Tree_Views_and_Navigation_compare"></a>
## <a name="tree-views-and-navigation"></a>Arborescences et navigation  
 À l’écran, les éléments d’ [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] peuvent être affichés sous forme d’arborescence. Le bureau correspond à la racine, les fenêtres d’application aux enfants immédiats et les éléments des applications à des descendants plus lointains.  
  
 Dans Active Accessibility, de nombreux éléments d’automatisation qui ne sont pas pertinents pour les utilisateurs finaux sont exposés dans l’arbre. Les applications clientes doivent examiner tous les éléments pour déterminer les éléments significatifs.  
  
 Les applications clientes UI Automation voient l’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] via une vue filtrée. La vue ne contient que les éléments intéressants : ceux qui apportent des informations à l’utilisateur ou qui permettent l’interaction. Des vues prédéfinies contenant uniquement les éléments de contrôle et uniquement les éléments de contenu sont disponibles. En outre, les applications peuvent définir des vues personnalisées. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] simplifie la tâche consistant à décrire l’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] à l’utilisateur et à aider l’utilisateur à interagir avec l’application.  
  
 La navigation entre les éléments, dans l’accessibilité active, est soit spatiale (par exemple, se déplaçant vers l’élément qui se trouve à gauche sur l’écran), logique (par exemple, passer à l’élément de menu suivant, ou l’élément suivant dans l’ordre d’onglet dans une boîte de dialogue), ou hiérarchique ( par exemple, déplacer le premier enfant dans un conteneur, ou de l’enfant à son parent). La navigation hiérarchique est compliquée par le fait que les éléments enfants ne sont pas toujours des objets qui implémentent `IAccessible`.  
  
 Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], tous les éléments d’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] sont des objets <xref:System.Windows.Automation.AutomationElement> qui prennent en charge les mêmes fonctionnalités de base. (Du point de vue du fournisseur, ce sont <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>des objets qui implémentent une interface héritée de .) La navigation est principalement hiérarchique : des parents aux enfants, et d’un frère ou d’un autre. (La navigation entre frères et sœurs a un élément logique, car elle peut suivre l’ordre de l’onglet.) Vous pouvez naviguer à partir de n’importe quel point de <xref:System.Windows.Automation.TreeWalker> départ, en utilisant n’importe quelle vue filtrée de l’arbre, en utilisant la classe. Vous pouvez également naviguer vers des enfants ou des descendants particuliers à l’aide de <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> et <xref:System.Windows.Automation.AutomationElement.FindAll%2A>. Par exemple, il est très simple de récupérer tous les éléments d’une boîte de dialogue qui prennent en charge un modèle de contrôle spécifié.  
  
 La [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] navigation est plus cohérente que dans l’accessibilité active. Certains éléments tels que les listes de décrochage et les fenêtres contextaulaient apparaissent deux fois dans l’arbre d’accessibilité active, et la navigation à partir d’eux peut avoir des résultats inattendus. Il est en fait impossible de mettre en œuvre correctement l’accessibilité active pour un contrôle des barres d’armature. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] permet la définition de l’état de parent et le repositionnement, afin qu’un élément puisse être placé n’importe où dans l’arborescence en dépit de la hiérarchie imposée par la propriété des fenêtres.  
  
<a name="Roles_and_Control_Types"></a>
## <a name="roles-and-control-types"></a>Rôles et types de contrôle  
 Active Accessibility `accRole` utilise`IAccessible::get_actRole`la propriété ( ) pour récupérer une [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]description du rôle de l’élément dans le , comme ROLE_SYSTEM_SLIDER ou ROLE_SYSTEM_MENUITEM. Le rôle d’un élément est l’indice principal pour connaître ses fonctionnalités disponibles. L’interaction avec un contrôle est réalisée à l’aide de méthodes fixes telles que `IAccessible::accSelect` et `IAccessible::accDoDefaultAction`. L’interaction entre l’application cliente et l’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] se limite à ce qui peut s’effectuer via `IAccessible`.  
  
 En revanche, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] découple en grande partie le type de contrôle de l’élément (décrit par la propriété <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> ) de ses fonctionnalités attendues. Les fonctionnalités sont déterminées par les modèles de contrôle pris en charge par le fournisseur via son implémentation d’interfaces spécialisées. Les modèles de contrôle peuvent être combinés pour décrire l’ensemble des fonctionnalités prises en charge par un élément [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] particulier. Certains fournisseurs sont tenus de prendre en charge un modèle de contrôle particulier. Par exemple, le fournisseur d’une case à cocher doit prendre en charge le modèle de contrôle Toggle. D’autres fournisseurs doivent prendre en charge un ou plusieurs éléments d’un ensemble de modèles de contrôle. Par exemple, un bouton doit prendre en charge Toggle ou Invoke. D’autres encore ne prennent en charge aucun modèle de contrôle du tout. Par exemple, un volet qui ne peut pas être déplacé, redimensionné ni ancré n’a pas de modèle de contrôle.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] prend en charge des contrôles personnalisés, identifiés par la propriété <xref:System.Windows.Automation.ControlType.Custom> et pouvant être décrits par la propriété <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> .  
  
 Le tableau suivant montre la cartographie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] des rôles d’accessibilité active aux types de contrôle.  
  
|Rôle d’accessibilité active|Type de contrôle[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|----------------------------------------------------------------------|----------------------------------------------------------------------------------------|  
|ROLE_SYSTEM_PUSHBUTTON|Bouton|  
|ROLE_SYSTEM_CLIENT|Calendrier|  
|ROLE_SYSTEM_CHECKBUTTON|Case à cocher|  
|ROLE_SYSTEM_COMBOBOX|Zone de liste modifiable|  
|ROLE_SYSTEM_CLIENT|Custom|  
|ROLE_SYSTEM_LIST|Grille de données|  
|ROLE_SYSTEM_LISTITEM|Élément de données|  
|ROLE_SYSTEM_DOCUMENT|Document|  
|ROLE_SYSTEM_TEXT|Modifier|  
|ROLE_SYSTEM_GROUPING|Groupe|  
|ROLE_SYSTEM_LIST|En-tête|  
|ROLE_SYSTEM_COLUMNHEADER|Élément d’en-tête|  
|ROLE_SYSTEM_LINK|Hyperlink|  
|ROLE_SYSTEM_GRAPHIC|Image|  
|ROLE_SYSTEM_LIST|List|  
|ROLE_SYSTEM_LISTITEM|Élément de liste|  
|ROLE_SYSTEM_MENUPOPUP|Menu|  
|ROLE_SYSTEM_MENUBAR|Barre de menus|  
|ROLE_SYSTEM_MENUITEM|Élément de menu|  
|ROLE_SYSTEM_PANE|Volet|  
|ROLE_SYSTEM_PROGRESSBAR|Barre de progression|  
|ROLE_SYSTEM_RADIOBUTTON|Case d’option|  
|ROLE_SYSTEM_SCROLLBAR|Barre de défilement|  
|ROLE_SYSTEM_SEPARATOR|Séparateur|  
|ROLE_SYSTEM_SLIDER|Curseur|  
|ROLE_SYSTEM_SPINBUTTON|Spinner|  
|ROLE_SYSTEM_SPLITBUTTON|Bouton Fractionner|  
|ROLE_SYSTEM_STATUSBAR|Barre d'état|  
|ROLE_SYSTEM_PAGETABLIST|Onglet|  
|ROLE_SYSTEM_PAGETAB|Élément d’onglet|  
|ROLE_SYSTEM_TABLE|Table de charge de travail|  
|ROLE_SYSTEM_STATICTEXT|Texte|  
|ROLE_SYSTEM_INDICATOR|Thumb|  
|ROLE_SYSTEM_TITLEBAR|Barre de titre|  
|ROLE_SYSTEM_TOOLBAR|Barre d’outils|  
|ROLE_SYSTEM_TOOLTIP|Info-bulle|  
|ROLE_SYSTEM_OUTLINE|Arborescence|  
|ROLE_SYSTEM_OUTLINEITEM|Élément d’arborescence|  
|ROLE_SYSTEM_WINDOW|Fenêtre|  
  
 Pour plus d’informations sur les différents types de contrôle, consultez [UI Automation Control Types](ui-automation-control-types.md).  
  
<a name="States_and_Properties"></a>
## <a name="states-and-properties"></a>États et propriétés  
 Dans Active Accessibility, les éléments prennent en charge un `accState`ensemble commun de propriétés, et certaines propriétés (comme ) doivent décrire des choses très différentes, selon le rôle de l’élément. Les serveurs doivent implémenter toutes les méthodes de `IAccessible` qui retournent une propriété, y compris celles qui ne sont pas pertinentes pour l’élément.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]définit beaucoup plus de propriétés, dont certaines correspondent aux états d’accessibilité active. Certaines sont communes à tous les éléments, tandis que d’autres sont spécifiques aux types de contrôle et aux motifs de contrôle. Les propriétés se distinguent par des identificateurs uniques et la plupart des propriétés peuvent être récupérées à l’aide d’une méthode unique, <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> ou <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>. De nombreuses propriétés sont également facilement récupérables à partir des accesseurs de propriété <xref:System.Windows.Automation.AutomationElement.Current%2A> et <xref:System.Windows.Automation.AutomationElement.Cached%2A> .  
  
 Un fournisseur UI Automation n’est pas tenu d’implémenter des propriétés non pertinentes et peut simplement retourner une valeur `null` pour toutes les propriétés qu’il ne prend pas en charge. Le service principal [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] peut également obtenir des propriétés auprès du fournisseur de fenêtres par défaut. Ces propriétés sont fusionnées avec les propriétés implémentées explicitement par le fournisseur.  
  
 Outre la prise en charge de nombreuses autres propriétés, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] fournit de meilleures performances en autorisant la récupération de plusieurs propriétés via un seul appel interprocessus.  
  
 Le tableau suivant montre la correspondance entre les propriétés dans les deux modèles.  
  
|Accesseur de propriété d’accessibilité active|ID de propriété[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Notes |  
|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|-------------|  
|`get_accKeyboardShortcut`|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty> ou <xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|Si les deux sont présents,`AccessKeyProperty` est prioritaire.|  
|`get_accName`|<xref:System.Windows.Automation.AutomationElement.NameProperty>||  
|`get_accRole`|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|Pour la correspondance entre les rôles et les types de contrôle, consultez le tableau précédent.|  
|`get_accValue`|<xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>|Valide uniquement pour les types de contrôle qui prennent en charge ValuePattern ou RangeValuePattern. Les valeurs RangeValue sont normalisées de 0 à 100 pour être cohérentes avec le comportement MSAA. Les éléments de valeur utilisent une chaîne.|  
|`get_accHelp`|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>||  
|`accLocation`|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>||  
|`get_accDescription`|Non pris en charge dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|`accDescription` n’avait pas de spécification claire dans MSAA ; les fournisseurs ont donc placé différentes informations dans cette propriété.|  
|`get_accHelpTopic`|Non pris en charge dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]||  
  
 Le tableau suivant [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] montre quelles propriétés correspondent aux constantes de l’état d’accessibilité active.  
  
|État d’accessibilité active|Propriété [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Déclenche un changement d’état ?|  
|-----------------------------------------------------------------------|------------------------------------------------------------------------------------|----------------------------|  
|STATE_SYSTEM_CHECKED|Pour une case à cocher, <xref:System.Windows.Automation.TogglePattern.ToggleStateProperty><br /><br /> Pour une case d’option, <xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|O|  
|STATE_SYSTEM_COLLAPSED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Collapsed>|O|  
|STATE_SYSTEM_EXPANDED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Expanded> ou <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>|O|  
|STATE_SYSTEM_FOCUSABLE|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|N|  
|STATE_SYSTEM_FOCUSED|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|N|  
|STATE_SYSTEM_HASPOPUP|<xref:System.Windows.Automation.ExpandCollapsePattern> pour des éléments de menu|N|  
|STATE_SYSTEM_INVISIBLE|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> = True et <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A> entraîne <xref:System.Windows.Automation.NoClickablePointException>|N|  
|STATE_SYSTEM_LINKED|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> =<br /><br /> <xref:System.Windows.Automation.ControlType.Hyperlink>|N|  
|STATE_SYSTEM_MIXED|<xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> = <xref:System.Windows.Automation.ToggleState.Indeterminate>|N|  
|STATE_SYSTEM_MOVEABLE|<xref:System.Windows.Automation.TransformPattern.CanMoveProperty>|N|  
|STATE_SYSTEM_MUTLISELECTABLE|<xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>|N|  
|STATE_SYSTEM_OFFSCREEN|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> = True|N|  
|STATE_SYSTEM_PROTECTED|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|N|  
|STATE_SYSTEM_READONLY|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty?displayProperty=nameWithType> et <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty?displayProperty=nameWithType>|N|  
|STATE_SYSTEM_SELECTABLE|<xref:System.Windows.Automation.SelectionItemPattern> est pris en charge|N|  
|STATE_SYSTEM_SELECTED|<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|N|  
|STATE_SYSTEM_SIZEABLE|<xref:System.Windows.Automation.TransformPattern.TransformPatternInformation.CanResize%2A>|N|  
|STATE_SYSTEM_UNAVAILABLE|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|O|  
  
 Les états suivants n’ont pas été mis en œuvre par la plupart des serveurs de contrôle d’accessibilité active ou n’ont pas d’équivalent dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
|État d’accessibilité active|Notes |  
|-----------------------------------------------------------------------|-------------|  
|STATE_SYSTEM_BUSY|Non disponible dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_DEFAULT|Non disponible dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ANIMATED|Non disponible dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_EXTSELECTABLE|Pas largement mis en œuvre par les serveurs d’accessibilité active|  
|STATE_SYSTEM_MARQUEED|Pas largement mis en œuvre par les serveurs d’accessibilité active|  
|STATE_SYSTEM_SELFVOICING|Pas largement mis en œuvre par les serveurs d’accessibilité active|  
|STATE_SYSTEM_TRAVERSED|Non disponible dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ALERT_HIGH|Pas largement mis en œuvre par les serveurs d’accessibilité active|  
|STATE_SYSTEM_ALERT_MEDIUM|Pas largement mis en œuvre par les serveurs d’accessibilité active|  
|STATE_SYSTEM_ALERT_LOW|Pas largement mis en œuvre par les serveurs d’accessibilité active|  
|STATE_SYSTEM_FLOATING|Pas largement mis en œuvre par les serveurs d’accessibilité active|  
|STATE_SYSTEM_HOTTRACKED|Non disponible dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_PRESSED|Non disponible dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
  
 Pour obtenir la liste complète des identificateurs de propriété [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , consultez [UI Automation Properties Overview](ui-automation-properties-overview.md).  
  
<a name="uiautomation_events_compare"></a>
## <a name="events"></a>Événements  
 Le mécanisme [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]d’événement dans , contrairement à celui dans Active Accessibility, ne repose pas sur le routage d’événements Windows (qui est étroitement lié avec des poignées de fenêtre) et ne nécessite pas l’application client pour configurer des crochets. Les abonnements aux événements peuvent être ajustés non seulement à des événements particuliers mais également à des parties spécifiques de l’arborescence. Les fournisseurs peuvent également ajuster leur déclenchement d’événements en assurant le suivi des événements qui sont écoutés.  
  
 Il est également plus facile pour les clients de récupérer les éléments qui déclenchent des événements, car ils sont passés directement au rappel d’événement. Les propriétés de l’élément sont automatiquement prérécupérées si une requête de cache était active quand le client s’est abonné à l’événement.  
  
 Le tableau suivant montre la correspondance des [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] WinEvents et événements d’accessibilité active.  
  
|WinEvent|Identificateur d’événement[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|--------------|--------------------------------------------------------------------------------------------|  
|EVENT_OBJECT_ACCELERATORCHANGE|Modification de la propriété<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|  
|EVENT_OBJECT_CONTENTSCROLLED|Modification de la propriété ou  sur les barres de défilement associées|  
|EVENT_OBJECT_CREATE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_DEFACTIONCHANGE|Pas d'équivalent|  
|EVENT_OBJECT_DESCRIPTIONCHANGE|Pas d’équivalent exact. Éventuelle modification de la propriété <xref:System.Windows.Automation.AutomationElement.HelpTextProperty> ou <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty>|  
|EVENT_OBJECT_DESTROY|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_FOCUS|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_OBJECT_HELPCHANGE|Modification de<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>|  
|EVENT_OBJECT_HIDE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_LOCATIONCHANGE|Modification de la propriété<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|  
|EVENT_OBJECT_NAMECHANGE|Modification de la propriété<xref:System.Windows.Automation.AutomationElement.NameProperty>|  
|EVENT_OBJECT_PARENTCHANGE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_REORDER|Pas toujours utilisé dans l’accessibilité active. Aucun événement directement correspondant n’est défini dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|EVENT_OBJECT_SELECTION|<xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>|  
|EVENT_OBJECT_SELECTIONADD|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent>|  
|EVENT_OBJECT_SELECTIONREMOVE|<xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent>|  
|EVENT_OBJECT_SELECTIONWITHIN|Pas d'équivalent|  
|EVENT_OBJECT_SHOW|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_STATECHANGE|Différents événements de modification de propriété|  
|EVENT_OBJECT_VALUECHANGE|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType> et <xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType> modifiés|  
|EVENT_SYSTEM_ALERT|Pas d'équivalent|  
|EVENT_SYSTEM_CAPTUREEND|Pas d'équivalent|  
|EVENT_SYSTEM_CAPTURESTART|Pas d'équivalent|  
|EVENT_SYSTEM_CONTEXTHELPEND|Pas d'équivalent|  
|EVENT_SYSTEM_CONTEXTHELPSTART|Pas d'équivalent|  
|EVENT_SYSTEM_DIALOGEND|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|  
|EVENT_SYSTEM_DIALOGSTART|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|  
|EVENT_SYSTEM_DRAGDROPEND|Pas d'équivalent|  
|EVENT_SYSTEM_DRAGDROPSTART|Pas d'équivalent|  
|EVENT_SYSTEM_FOREGROUND|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_SYSTEM_MENUEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MENUSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MINIMIZEEND|Modification de la propriété<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>|  
|EVENT_SYSTEM_MINIMIZESTART|Modification de la propriété<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>|  
|EVENT_SYSTEM_MOVESIZEEND|Modification de la propriété<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|  
|EVENT_SYSTEM_MOVESIZESTART|Modification de la propriété<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|  
|EVENT_SYSTEM_SCROLLINGEND|Modification de la propriété ou |  
|EVENT_SYSTEM_SCROLLINGSTART|Modification de la propriété ou |  
|EVENT_SYSTEM_SOUND|Pas d'équivalent|  
|EVENT_SYSTEM_SWITCHEND|Aucun équivalent, mais un événement <xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent> signale qu’une nouvelle application a reçu le focus|  
|EVENT_SYSTEM_SWITCHSTART|Pas d'équivalent|  
|Pas d'équivalent|Modification de la propriété<xref:System.Windows.Automation.MultipleViewPattern.CurrentViewProperty>|  
|Pas d'équivalent|Modification de la propriété<xref:System.Windows.Automation.ScrollPattern.HorizontallyScrollableProperty>|  
|Pas d'équivalent|Modification de la propriété<xref:System.Windows.Automation.ScrollPattern.VerticallyScrollableProperty>|  
|Pas d'équivalent|Modification de la propriété<xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty>|  
|Pas d'équivalent|Modification de la propriété<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>|  
|Pas d'équivalent|Modification de la propriété<xref:System.Windows.Automation.ScrollPattern.HorizontalViewSizeProperty>|  
|Pas d'équivalent|Modification de la propriété<xref:System.Windows.Automation.ScrollPattern.VerticalViewSizeProperty>|  
|Pas d'équivalent|Modification de la propriété<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty>|  
|Pas d'équivalent|Modification de la propriété<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>|  
|Pas d'équivalent|Événement<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent>|  
|Pas d'équivalent|<xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent>|  
  
<a name="Security_compare"></a>
## <a name="security"></a>Sécurité  
 Certains scénarios de personnalisation `IAccessible` nécessitent l’encapsulation d’un `IAccessible` de base et l’appel via celui-ci. Cela a des implications en matière de sécurité, car un composant avec un niveau de confiance partiel ne doit pas être un intermédiaire sur un chemin de code.  
  
 Le modèle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] supprime le besoin qu’ont les fournisseurs d’appeler via un autre code de fournisseur. Le service principal [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] effectue toutes les opérations d’agrégation nécessaires.  
  
## <a name="see-also"></a>Voir aussi

- [Principes fondamentaux de l’automatisation de l’interface utilisateur](index.md)
