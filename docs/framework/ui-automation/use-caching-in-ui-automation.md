---
title: Utiliser la mise en cache dans UI Automation
description: Découvrez comment utiliser la mise en cache dans UI Automation. Passez en revue les étapes permettant d’activer une requête de cache, de mettre en cache des propriétés AutomationElement et d’obtenir des modèles mis en cache.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- caching, UI Automation
- UI Automation, caching
ms.assetid: ec722dff-6009-4279-b86a-e18d3fa94ebf
ms.openlocfilehash: 8dff9db77e39dc66a16b6a7b395c76a3c768d48e
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924485"
---
# <a name="use-caching-in-ui-automation"></a>Utiliser la mise en cache dans UI Automation
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette section montre comment implémenter la mise en cache des propriétés <xref:System.Windows.Automation.AutomationElement> et des modèles de contrôle.  
  
### <a name="activate-a-cache-request"></a>Activer une requête de Cache  
  
1. Créer un <xref:System.Windows.Automation.CacheRequest>.  
  
2. Spécifiez les propriétés et les modèles à mettre en cache à l’aide de la méthode <xref:System.Windows.Automation.CacheRequest.Add%2A>.  
  
3. Spécifiez la portée de la mise en cache en définissant la propriété <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> .  
  
4. Spécifiez l’affichage de la sous-arborescence en définissant la propriété <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> .  
  
5. Affectez à la propriété <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> la valeur <xref:System.Windows.Automation.AutomationElementMode.None> si vous souhaitez augmenter l’efficacité en ne récupérant pas de référence complète aux objets. (Cela rend impossible la récupération des valeurs actuelles de ces objets.)  
  
6. Activez la requête à l’aide <xref:System.Windows.Automation.CacheRequest.Activate%2A> d’un `using` bloc ( `Using` dans Microsoft Visual Basic .net).  
  
 Après avoir obtenu des objets <xref:System.Windows.Automation.AutomationElement> ou vous être inscrit à des événements, désactivez la requête en utilisant <xref:System.Windows.Automation.CacheRequest.Pop%2A> (si <xref:System.Windows.Automation.CacheRequest.Push%2A> a été utilisé) ou en supprimant l’objet créé par <xref:System.Windows.Automation.CacheRequest.Activate%2A>. (Utilisez <xref:System.Windows.Automation.CacheRequest.Activate%2A> dans un `using` bloc ( `Using` dans Microsoft Visual Basic .net).  
  
### <a name="cache-automationelement-properties"></a>Mettre en cache des propriétés AutomationElement  
  
1. Lorsqu’un <xref:System.Windows.Automation.CacheRequest> est actif, obtenez des objets <xref:System.Windows.Automation.AutomationElement> en utilisant <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> ou <xref:System.Windows.Automation.AutomationElement.FindAll%2A>, ou obtenez un <xref:System.Windows.Automation.AutomationElement> comme source d’un événement pour lequel vous vous êtes inscrit lorsque le <xref:System.Windows.Automation.CacheRequest> était actif. (Vous pouvez également créer un cache en passant un <xref:System.Windows.Automation.CacheRequest> à GetUpdatedCache ou l’une des méthodes <xref:System.Windows.Automation.TreeWalker> .)  
  
2. Utilisez <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> ou récupérez une propriété de la propriété <xref:System.Windows.Automation.AutomationElement.Cached%2A> de l’ <xref:System.Windows.Automation.AutomationElement>.  
  
### <a name="obtain-cached-patterns-and-their-properties"></a>Obtenir des modèles mis en cache et leurs propriétés  
  
1. Lorsqu’un <xref:System.Windows.Automation.CacheRequest> est actif, obtenez des objets <xref:System.Windows.Automation.AutomationElement> en utilisant <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> ou <xref:System.Windows.Automation.AutomationElement.FindAll%2A>, ou obtenez un <xref:System.Windows.Automation.AutomationElement> comme source d’un événement pour lequel vous vous êtes inscrit lorsque le <xref:System.Windows.Automation.CacheRequest> était actif. (Vous pouvez également créer un cache en passant un <xref:System.Windows.Automation.CacheRequest> à GetUpdatedCache ou l’une des méthodes <xref:System.Windows.Automation.TreeWalker> .)  
  
2. Utilisez <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> ou <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> pour récupérer un modèle mis en cache.  
  
3. Récupérez les valeurs de propriété de la propriété `Cached` du modèle de contrôle.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant présente différents aspects de la mise en cache, en utilisant <xref:System.Windows.Automation.CacheRequest.Activate%2A> pour activer le <xref:System.Windows.Automation.CacheRequest>.  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant présente différents aspects de la mise en cache, en utilisant <xref:System.Windows.Automation.CacheRequest.Push%2A> pour activer le <xref:System.Windows.Automation.CacheRequest>. Excepté lorsque vous souhaitez imbriquer des requêtes de cache, il est préférable d’utiliser <xref:System.Windows.Automation.CacheRequest.Activate%2A>.  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a>Voir aussi

- [Mise en cache dans les clients UI Automation](caching-in-ui-automation-clients.md)
