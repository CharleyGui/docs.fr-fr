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
ms.openlocfilehash: 264a24646f7a3c3b5b20e94fa0ed98a1341f8273
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435762"
---
# <a name="enable-navigation-in-a-ui-automation-fragment-provider"></a>Activer la navigation dans un fournisseur de fragment UI Automation
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique contient un exemple de code qui montre comment activer la navigation dans un fournisseur UI Automation pour un élément situé dans un fragment.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant implémente <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> pour un élément de liste situé dans une liste. L’élément parent est l’élément de zone de liste. Les éléments frères sont d’autres éléments de la collection de listes. La méthode retourne `null` (`Nothing` en Visual Basic) pour les directions non valides. Dans le cas présent, il s’agit de <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> et <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, car l’élément n’a pas d’enfants.  
  
 [!code-csharp[UIAFragmentProvider_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListItemFragment.cs#103)]
 [!code-vb[UIAFragmentProvider_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListItemFragment.vb#103)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des fournisseurs UI Automation](ui-automation-providers-overview.md)
- [Implémentation de fournisseur UI Automation côté serveur](server-side-ui-automation-provider-implementation.md)
