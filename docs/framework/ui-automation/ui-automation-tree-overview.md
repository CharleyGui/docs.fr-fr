---
title: Vue d’ensemble de l’arborescence UI Automation
ms.date: 03/30/2017
helpviewer_keywords:
- automation tree
- UI Automation, tree
ms.assetid: 03b98058-bdb3-47a0-8ff7-45e6cdf67166
ms.openlocfilehash: a0b888e8ecc80e3739c583931a86da3cdb7242d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179454"
---
# <a name="ui-automation-tree-overview"></a>Vue d’ensemble de l’arborescence UI Automation
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Les produits de technologie d’assistance et les scripts de test parcourent l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pour recueillir des informations sur l’[!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] et ses éléments.  
  
 Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] l’arbre il ya<xref:System.Windows.Automation.AutomationElement.RootElement%2A>un élément racine ( ) qui représente le bureau actuel et dont les éléments de l’enfant représentent les fenêtres d’application. Chacun de ces éléments enfants peut contenir des éléments représentant des composants d’[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] tels que des menus, boutons, barres d’outils et zones de liste. Ces éléments peuvent à leur tour contenir des éléments tels que des éléments de liste.  
  
 L’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] n’est pas une structure fixe et est rarement visible dans son intégralité, car elle peut contenir des milliers d’éléments. Certains de ses composants sont créés à mesure des besoins et elle peut subir des modifications à mesure que des éléments sont ajoutés, déplacés ou supprimés.  
  
 Les fournisseurs UI Automation prennent en charge l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] en implémentant une navigation entre les éléments d’un fragment, qui est constitué d’une racine (généralement hébergée dans une fenêtre) et d’une sous-arborescence. Cependant, les fournisseurs ne sont pas concernés par la navigation d’un contrôle à un autre. Cela est géré par le noyau [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], à partir des informations issues des fournisseurs de fenêtre par défaut.  
  
<a name="uiautomation_tree_view"></a>
## <a name="views-of-the-automation-tree"></a>Affichages de l’arborescence Automation  
 L’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] peut être filtrée pour créer des affichages qui contiennent uniquement les objets <xref:System.Windows.Automation.AutomationElement> utiles à un client particulier. Cette approche permet aux clients de personnaliser la structure présentée via [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] en fonction de leurs besoins particuliers.  
  
 Le client peut personnaliser l’affichage de deux façons : par la portée et par le filtrage. La portée consiste à définir l’étendue de l’affichage à partir d’un élément de base. Par exemple, l’application peut rechercher uniquement les enfants directs du bureau ou tous les descendants d’une fenêtre de l’application. Le filtrage consiste à définir les types d’éléments qui doivent être inclus dans l’affichage.  
  
 Les fournisseurs UI Automation prennent en charge le filtrage moyennant la définition de propriétés sur les éléments, notamment les propriétés <xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty> et <xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propose trois affichages par défaut. Ces affichages sont définis en fonction du type de filtrage effectué ; l’étendue d’un affichage est définie par l’application. Par ailleurs, l’application peut appliquer d’autres filtres sur les propriétés, par exemple, pour inclure uniquement des contrôles activés dans un affichage de contrôle.  
  
<a name="uiautomation_raw_view"></a>
### <a name="raw-view"></a>Affichage brut  
 L’affichage brut de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] est l’arborescence complète des objets <xref:System.Windows.Automation.AutomationElement> dont le bureau est la racine. L’affichage brut suit étroitement la structure de programmation native d’une application et est de ce fait l’affichage le plus détaillé. C’est aussi la base sur laquelle reposent les autres affichages de l’arborescence. Parce que cette vue [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] dépend du cadre [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] sous-jacent, la vue brute d’un bouton aura une vue brute différente d’un bouton Win32.  
  
 L’affichage brut s’obtient en recherchant des éléments sans spécifier de propriétés ou en utilisant <xref:System.Windows.Automation.TreeWalker.RawViewWalker> pour parcourir l’arborescence.  
  
<a name="uiautomation_control_view"></a>
### <a name="control-view"></a>Affichage de contrôle  
 L’affichage de contrôle de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] permet au produit de technologie d’assistance de décrire plus facilement l’[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] à l’utilisateur final et aide ce dernier à interagir avec l’application, car il s’apparente de près à la structure de l’[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] perçue par un utilisateur final.  
  
 L’affichage de contrôle est un sous-ensemble de l’affichage brut. Il comprend tous les éléments d’[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] de l’affichage brut qu’un utilisateur final considérerait comme interactif ou qui contribuent à la structure logique du contrôle dans l’[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Parmi les éléments d’[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] qui contribuent à la structure logique de l’[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], mais qui ne sont pas eux-mêmes interactifs, il y a notamment les conteneurs d’éléments tels que les en-têtes, les barres d’outils, les menus et la barre d’état d’un affichage de liste. Les éléments non interactifs utilisés simplement à des fins de disposition ou de décoration n’apparaissent pas dans l’affichage de contrôle. Tel est le cas, par exemple, d’un volet servant uniquement à disposer les contrôles dans une boîte de dialogue mais qui ne contient lui-même aucune information. Les éléments non interactifs qui apparaissent dans l’affichage de contrôle sont des éléments graphiques associées aux informations et au texte statique d’une boîte de dialogue. Les éléments non interactifs qui sont inclus dans l’affichage de contrôle ne peuvent pas recevoir le focus clavier.  
  
 L’affichage de contrôle s’obtient en recherchant des éléments dont la propriété <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> a la valeur `true` ou en utilisant <xref:System.Windows.Automation.TreeWalker.ControlViewWalker> pour parcourir l’arborescence.  
  
<a name="uiautomation_content_view"></a>
### <a name="content-view"></a>Affichage de contenu  
 L’affichage du contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] est un sous-ensemble de l’affichage de contrôle. Il contient des éléments d’[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] qui communiquent les véritables informations d’une interface utilisateur, notamment les éléments d’[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] qui peuvent recevoir le focus clavier et du texte autre qu’une étiquette d’élément d’[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Par exemple, les valeurs contenues dans une zone de liste déroulante s’affichent dans l’affichage de contenu, car elles représentent les informations utilisées par un utilisateur final. Dans l’affichage de contenu, une zone de liste déroulante et une zone de liste sont toutes deux représentées sous forme de collection d’éléments [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] dans laquelle un ou éventuellement plusieurs éléments peuvent être sélectionnés. Le fait qu’il y en a un toujours d’ouvert et un qui peut être développé et réduit est sans importance dans l’affichage de contenu, car il est conçu pour afficher les données (ou le contenu) présentées à l’utilisateur.  
  
 L’affichage de contenu s’obtient en recherchant des éléments dont la propriété <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> a la valeur `true` ou en utilisant <xref:System.Windows.Automation.TreeWalker.ContentViewWalker> pour parcourir l’arborescence.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Automation.AutomationElement>
- [Vue d'ensemble d'UI Automation](ui-automation-overview.md)
