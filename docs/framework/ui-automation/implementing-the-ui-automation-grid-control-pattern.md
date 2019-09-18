---
title: Implémentation du modèle de contrôle Grid d’UI Automation
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
ms.openlocfilehash: 222f79934b183b836f74575cdcc611588b41ce2a
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043446"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a>Implémentation du modèle de contrôle Grid d’UI Automation
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les informations les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]plus récentes [sur, consultez API Windows Automation: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique présente les conventions et directives à respecter pour implémenter <xref:System.Windows.Automation.Provider.IGridProvider>, notamment les informations sur les propriétés, les méthodes et les événements. Des liens vers des références supplémentaires sont répertoriés à la fin de la vue d'ensemble.  
  
 Le modèle de contrôle <xref:System.Windows.Automation.GridPattern> permet de prendre en charge les contrôles qui agissent comme des conteneurs pour une collection d’éléments enfants. Les enfants de cet élément doivent implémenter <xref:System.Windows.Automation.Provider.IGridItemProvider> et être organisés en un système de coordonnées logiques à deux dimensions, qui peut être parcouru par ligne et par colonne. Pour obtenir des exemples de contrôles implémentant ce modèle de contrôle, consultez [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Conventions et recommandations en matière d'implémentation  
 Quand vous implémentez le modèle de contrôle Grid, notez les conventions et recommandations suivantes :  
  
- Les coordonnées de grille sont de base zéro, les coordonnées de la cellule supérieure gauche (ou supérieure droite en fonction des paramètres régionaux) ayant pour coordonnées (0, 0).  
  
- Si une cellule est vide, un élément UI Automation doit être retourné pour permettre la prise en charge de la propriété <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> de cette cellule. Cela est possible quand la disposition des éléments enfants de la grille est semblable à celle d’un tableau non justifié (consultez l’exemple ci-dessous).  
  
 ![Affichage de l’Explorateur Windows avec mise en page irrégulière.](./media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")  
Exemple de contrôle Grid avec des coordonnées vides  
  
- Une grille avec un seul élément est nécessaire pour implémenter <xref:System.Windows.Automation.Provider.IGridProvider> , s’il est logiquement considéré comme une grille. Le nombre d’éléments enfants de la grille est immatériel.  
  
- Selon l’implémentation du fournisseur, les lignes et les colonnes masquées peuvent être chargées dans l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , et sont donc reflétées dans les propriétés <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> et <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> . Si les lignes et les colonnes masquées n’ont pas encore été chargées, elles ne doivent pas être comptabilisées.  
  
- <xref:System.Windows.Automation.Provider.IGridProvider> n’active pas la manipulation active d’une grille. <xref:System.Windows.Automation.Provider.ITransformProvider> doit être implémenté pour activer cette fonctionnalité.  
  
- Utilisez <xref:System.Windows.Automation.StructureChangedEventHandler> pour écouter les changements de structure ou de disposition apportés à la grille, par exemple quand des cellules sont ajoutées, supprimées ou fusionnées.  
  
- Utilisez <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> pour suivre le parcours des éléments ou des cellules d’une grille.  
  
<a name="Required_Members_for_IGridProvider"></a>   
## <a name="required-members-for-igridprovider"></a>Membres obligatoires pour IGridProvider  
 Les propriétés et méthodes suivantes sont nécessaires à l’implémentation de l’interface IGridProvider.  
  
|Membres requis|Type|Notes|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|Propriété|Aucun|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|Propriété|Aucun|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|Méthode|Aucune|  
  
 Ce modèle de contrôle n’est associé aucun événement.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceptions  
 Les fournisseurs doivent lever les exceptions suivantes.  
  
|Type d'exception|Condition|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> -Si la coordonnée de la ligne demandée <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> est supérieure à ou si la coordonnée de la colonne est supérieure <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>à.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> -Si l’une des coordonnées de la ligne ou de la colonne demandée est inférieure à zéro.|  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des modèles de contrôle UI Automation](ui-automation-control-patterns-overview.md)
- [Prendre en charge des modèles de contrôle dans un fournisseur UI Automation](support-control-patterns-in-a-ui-automation-provider.md)
- [Modèles de contrôle UI Automation pour les clients](ui-automation-control-patterns-for-clients.md)
- [Implémentation du modèle de contrôle GridItem d’UI Automation](implementing-the-ui-automation-griditem-control-pattern.md)
- [Présentation de l’arborescence UI Automation](ui-automation-tree-overview.md)
- [Utiliser la mise en cache dans UI Automation](use-caching-in-ui-automation.md)
