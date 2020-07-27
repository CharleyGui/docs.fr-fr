---
title: Implémentation du modèle de contrôle GridItem d’UI Automation
description: Connaître les recommandations et les conventions permettant d’implémenter le modèle de contrôle GridItemPattern pour les éléments de grille dans UI Automation. Consultez les membres requis pour IGridItemProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: e0a0c616f3f0cf9bc091e4fbb496d71ab8550bd3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165823"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a>Implémentation du modèle de contrôle GridItem d’UI Automation
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique présente les conventions et recommandations à respecter pour implémenter <xref:System.Windows.Automation.Provider.IGridItemProvider>, notamment des informations sur les propriétés. Des liens vers des références supplémentaires sont répertoriés à la fin de la vue d'ensemble.  
  
 Le modèle de contrôle <xref:System.Windows.Automation.GridItemPattern> est utilisé pour prendre en charge les contrôles enfants individuels des conteneurs qui implémentent <xref:System.Windows.Automation.Provider.IGridProvider>. Pour obtenir des exemples de contrôles implémentant ce modèle de contrôle, consultez [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Conventions et directives d'implémentation  
 Quand vous implémentez <xref:System.Windows.Automation.Provider.IGridProvider>, notez les conventions et recommandations suivantes :  
  
- Les coordonnées de grille ont une base zéro et la cellule supérieure gauche possède les coordonnées (0, 0).  
  
- Les cellules fusionnées signalent leurs propriétés <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> et <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> en fonction de leur cellule d’ancrage sous-jacente, comme défini par le fournisseur UI Automation. En règle générale, il s’agit de la ligne la plus haute ou de la colonne la plus à gauche.  
  
- <xref:System.Windows.Automation.Provider.IGridItemProvider> ne fournit pas de manipulation active de la grille telle que la fusion ou le fractionnement des cellules.  
  
- Les contrôles qui implémentent <xref:System.Windows.Automation.Provider.IGridItemProvider> peuvent généralement être parcourus (c’est-à-dire qu’un client UI Automation peut se déplacer vers les contrôles adjacents) à l’aide du clavier.  
  
<a name="Required_Members_for_IGridItemProvider"></a>
## <a name="required-members-for-igriditemprovider"></a>Membres obligatoires pour IGridItemProvider  
 Les propriétés et méthodes suivantes sont nécessaires à l'implémentation d' <xref:System.Windows.Automation.Provider.IGridItemProvider>.  
  
|Membres nécessaires|Type de membre|Notes|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|Propriété|None|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|Propriété|None|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|Propriété|None|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|Propriété|None|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|Propriété|None|  
  
 Ce modèle de contrôle n’est associé à aucune méthode ou aucun événement.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Exceptions  
 Ce modèle de contrôle n’est associé à aucune exception.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble des modèles de contrôle UI Automation](ui-automation-control-patterns-overview.md)
- [Prendre en charge des modèles de contrôle dans un fournisseur UI Automation](support-control-patterns-in-a-ui-automation-provider.md)
- [Modèles de contrôle UI Automation pour les clients](ui-automation-control-patterns-for-clients.md)
- [Implémentation du modèle de contrôle Grid d’UI Automation](implementing-the-ui-automation-grid-control-pattern.md)
- [Vue d’ensemble de l’arborescence UI Automation](ui-automation-tree-overview.md)
- [Utiliser la mise en cache dans UI Automation](use-caching-in-ui-automation.md)
