---
title: Ajouter du contenu à une zone de texte à l'aide d'UI Automation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
ms.openlocfilehash: fdc52d0b94ce500b6560b60419d409f5cbd73b55
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932652"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a>Ajouter du contenu à une zone de texte à l'aide d'UI Automation
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les informations les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]plus récentes [sur, consultez API Windows Automation: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique contient un exemple de code qui montre comment [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] utiliser pour insérer du texte dans une zone de texte sur une seule ligne. Une autre méthode est fournie pour les contrôles de texte enrichi et multilignes où [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] n’est pas applicable. À des fins de comparaison, l’exemple montre également comment utiliser des méthodes Win32 pour obtenir les mêmes résultats.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment parcourir une séquence de contrôles de texte dans une application cible. Chaque contrôle de texte est testé pour voir si <xref:System.Windows.Automation.ValuePattern> un objet peut être obtenu à partir de <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> celui-ci à l’aide de la méthode. Si le contrôle de texte prend <xref:System.Windows.Automation.ValuePattern>en charge <xref:System.Windows.Automation.ValuePattern.SetValue%2A> , la méthode est utilisée pour insérer une chaîne définie par l’utilisateur dans le contrôle de texte. Dans le cas <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> contraire, la méthode est utilisée.  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a>Voir aussi

- [Exemple d’insertion de texte TextPattern](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))
