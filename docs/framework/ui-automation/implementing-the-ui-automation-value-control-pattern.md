---
title: Implémentation du modèle de contrôle Value d’UI Automation
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
ms.openlocfilehash: d8b05238b55369fca3df76cf309f5cf742685b41
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64603303"
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a>Implémentation du modèle de contrôle Value d’UI Automation
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour plus d’informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [Windows Automation API : UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique présente les conventions et recommandations à respecter pour implémenter <xref:System.Windows.Automation.Provider.IValueProvider>, notamment des informations sur les événements et les propriétés. Des liens vers des références supplémentaires sont répertoriés à la fin de la rubrique.  
  
 Le modèle de contrôle <xref:System.Windows.Automation.ValuePattern> est utilisé pour prendre en charge les contrôles qui ont une valeur intrinsèque ne couvrant pas de plage et qui peuvent être représentés sous forme de chaîne. Cette chaîne peut être modifiée, en fonction du contrôle et de ses paramètres. Pour obtenir des exemples de contrôles implémentant ce modèle, consultez [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Conventions et recommandations en matière d'implémentation  
 Quand vous implémentez le modèle de contrôle Value, notez les conventions et recommandations suivantes :  
  
- Les contrôles tels que <xref:System.Windows.Automation.ControlType.ListItem> et <xref:System.Windows.Automation.ControlType.TreeItem> doivent prendre en charge <xref:System.Windows.Automation.ValuePattern> si la valeur d’un des éléments est modifiable, indépendamment du mode d’édition actuel du contrôle. Le contrôle parent doit également prendre en charge <xref:System.Windows.Automation.ValuePattern> si les éléments enfants sont modifiables.  
  
 ![Élément de liste modifiable. ](../../../docs/framework/ui-automation/media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")  
Exemple d’élément de liste modifiable  
  
- Les contrôles d’édition sur une ligne prennent en charge l’accès par programmation à leur contenu en implémentant <xref:System.Windows.Automation.Provider.IValueProvider>. Toutefois, les contrôles d’édition multilignes n’implémentent pas <xref:System.Windows.Automation.Provider.IValueProvider>. Ils fournissent plutôt un accès à leur contenu en implémentant <xref:System.Windows.Automation.Provider.ITextProvider>.  
  
- Pour récupérer le contenu textuel d’un contrôle d’édition multiligne, le contrôle doit implémenter <xref:System.Windows.Automation.Provider.ITextProvider>. Toutefois, <xref:System.Windows.Automation.Provider.ITextProvider> ne prend pas en charge la définition de la valeur d’un contrôle.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider> ne prend pas en charge la récupération des informations de mise en forme ou des valeurs d’une sous-chaîne. Implémentez <xref:System.Windows.Automation.Provider.ITextProvider> dans ces scénarios.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider> doit être implémenté par des contrôles tels que le contrôle de sélection **Sélecteur de couleurs** de [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] (illustré ci-dessous), qui prend en charge le mappage de chaînes entre une valeur de couleur (par exemple, « jaune ») et une structure [!INCLUDE[TLA#tla_rgb](../../../includes/tlasharptla-rgb-md.md)] équivalente interne.  
  
 ![Sélecteur de couleurs avec jaune en surbrillance. ](../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Exemple de mappage d’une chaîne d’échantillons de couleurs  
  
- Un contrôle doit avoir <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> défini sur `true` et <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> défini sur `false` avant d’autoriser un appel à <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-ivalueprovider"></a>Membres obligatoires pour IValueProvider  
 Les propriétés et méthodes suivantes sont nécessaires à l'implémentation d' <xref:System.Windows.Automation.Provider.IValueProvider>.  
  
|Membres requis|Type de membre|Notes|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>|Propriété|None|  
|<xref:System.Windows.Automation.ValuePattern.ValueProperty>|Propriété|None|  
|<xref:System.Windows.Automation.ValuePattern.SetValue%2A>|Méthode|None|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceptions  
 Les fournisseurs doivent lever les exceptions suivantes.  
  
|Type d'exception|Condition|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -Si les informations de paramètres régionaux spécifiques sont passées à un contrôle dans un format incorrect, telle qu’une date au format incorrect.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -Si une nouvelle valeur ne peut pas être convertie à partir d’une chaîne dans un format reconnu par le contrôle.|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -Lorsqu’une tentative est effectuée pour manipuler un contrôle qui n’est pas activé.|  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des modèles de contrôle UI Automation](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Prendre en charge des modèles de contrôle dans un fournisseur UI Automation](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Modèles de contrôle UI Automation pour les clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Exemple de texte ValuePattern Insert](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [Présentation de l’arborescence UI Automation](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Utiliser la mise en cache dans UI Automation](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
