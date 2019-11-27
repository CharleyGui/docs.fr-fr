---
title: Obtenir les propriétés d'éléments UI Automation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
ms.openlocfilehash: 1b82302ff89d2e8407871cbfba6c10e8322ac4e7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435497"
---
# <a name="get-ui-automation-element-properties"></a>Obtenir les propriétés d'éléments UI Automation
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique montre comment récupérer les propriétés d’un élément [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
### <a name="get-a-current-property-value"></a>Obtenir une valeur de propriété actuelle  
  
1. Obtenez le <xref:System.Windows.Automation.AutomationElement> dont vous souhaitez obtenir la propriété.  
  
2. Appelez <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>ou récupérez la structure de propriété <xref:System.Windows.Automation.AutomationElement.Current%2A> et récupérez la valeur de l’un de ses membres.  
  
### <a name="get-a-cached-property-value"></a>Obtenir une valeur de propriété mise en cache  
  
1. Obtenez le <xref:System.Windows.Automation.AutomationElement> dont vous souhaitez obtenir la propriété. La propriété doit avoir été spécifiée dans la <xref:System.Windows.Automation.CacheRequest>.  
  
2. Appelez <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>ou récupérez la structure de propriété <xref:System.Windows.Automation.AutomationElement.Cached%2A> et récupérez la valeur de l’un de ses membres.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre différentes façons de récupérer les propriétés actuelles d’un <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a>Voir aussi

- [UI Automation Properties for Clients](ui-automation-properties-for-clients.md)
- [Utiliser la mise en cache dans UI Automation](use-caching-in-ui-automation.md)
- [Caching in UI Automation Clients](caching-in-ui-automation-clients.md)
