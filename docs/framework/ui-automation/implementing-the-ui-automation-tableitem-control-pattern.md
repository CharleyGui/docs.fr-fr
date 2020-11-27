---
title: Implémentation du modèle de contrôle TableItem d’UI Automation
description: Passez en revue les recommandations et les conventions pour implémenter le modèle de contrôle TableItem dans UI Automation. Connaître les membres requis pour l’interface ITableItemProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: 5e83f68772de3026fe8bcb265a11999e0b85a164
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265672"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a>Implémentation du modèle de contrôle TableItem d’UI Automation

> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique présente les conventions et recommandations à respecter pour implémenter <xref:System.Windows.Automation.Provider.ITableItemProvider>, notamment des informations sur les événements et les propriétés. Des liens vers des références supplémentaires sont répertoriés à la fin de la vue d'ensemble.  
  
 Le modèle de contrôle <xref:System.Windows.Automation.TableItemPattern> est utilisé pour prendre en charge les contrôles enfants des conteneurs qui implémentent <xref:System.Windows.Automation.Provider.ITableProvider>. Un accès aux fonctionnalités des cellules individuelles est fourni par l’implémentation simultanée obligatoire de <xref:System.Windows.Automation.Provider.IGridItemProvider>. Ce modèle de contrôle est analogue à <xref:System.Windows.Automation.Provider.IGridItemProvider>, à la différence que tout contrôle implémentant <xref:System.Windows.Automation.Provider.ITableItemProvider> doit exposer par programmation la relation entre la cellule individuelle et ses informations de ligne et de colonne. Pour obtenir des exemples de contrôles implémentant ce modèle de contrôle, consultez [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a>Conventions et directives d'implémentation  
  
- Pour obtenir des fonctionnalités d’élément de grille associées, consultez [implémentation du modèle de contrôle GridItem d’UI Automation](implementing-the-ui-automation-griditem-control-pattern.md).  
  
<a name="Required_Members_for_ITableItemProvider"></a>

## <a name="required-members-for-itableitemprovider"></a>Membres obligatoires pour ITableItemProvider  
  
|Membre obligatoire|Type de membre|Notes|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|Méthode|None|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|Méthode|None|  
  
 Ce modèle de contrôle n’est associé à aucune propriété ni à aucun événement.  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a>Exceptions  

 Ce modèle de contrôle n’est associé à aucune exception.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble des modèles de contrôle UI Automation](ui-automation-control-patterns-overview.md)
- [Prendre en charge des modèles de contrôle dans un fournisseur UI Automation](support-control-patterns-in-a-ui-automation-provider.md)
- [Modèles de contrôle UI Automation pour les clients](ui-automation-control-patterns-for-clients.md)
- [Implémentation du modèle de contrôle Table d’UI Automation](implementing-the-ui-automation-table-control-pattern.md)
- [Implémentation du modèle de contrôle GridItem d’UI Automation](implementing-the-ui-automation-griditem-control-pattern.md)
- [Vue d’ensemble de l’arborescence UI Automation](ui-automation-tree-overview.md)
- [Utiliser la mise en cache dans UI Automation](use-caching-in-ui-automation.md)
