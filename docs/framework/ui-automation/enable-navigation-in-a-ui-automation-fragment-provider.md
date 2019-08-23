---
title: Activer la navigation dans un fournisseur de fragment UI Automation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, enabling navigation in provider
- navigation, enabling in UI Automation provider
ms.assetid: 3cb6092a-58c9-4ca0-84a5-0e54d5d00a0d
ms.openlocfilehash: 6410a0f8a991f1dc21a298972182ec630723f627
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932613"
---
# <a name="enable-navigation-in-a-ui-automation-fragment-provider"></a>Activer la navigation dans un fournisseur de fragment UI Automation
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les informations les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]plus récentes [sur, consultez API Windows Automation: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique contient un exemple de code qui montre comment activer la navigation dans un fournisseur UI Automation pour un élément situé dans un fragment.  
  
## <a name="example"></a>Exemples  
 L’exemple de code suivant implémente <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> pour un élément de liste situé dans une liste. L’élément parent est l’élément de zone de liste. Les éléments frères sont d’autres éléments de la collection de listes. La méthode retourne `null` (`Nothing` en Visual Basic) pour les directions non valides. Dans le cas présent, il s’agit de <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> et <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, car l’élément n’a pas d’enfants.  
  
 [!code-csharp[UIAFragmentProvider_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListItemFragment.cs#103)]
 [!code-vb[UIAFragmentProvider_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListItemFragment.vb#103)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des fournisseurs UI Automation](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [Implémentation de fournisseur UI Automation côté serveur](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
