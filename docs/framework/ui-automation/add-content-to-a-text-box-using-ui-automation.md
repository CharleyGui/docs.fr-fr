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
ms.openlocfilehash: 71385690c01d261b4ff1b495674bab377232e81d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447248"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a>Ajouter du contenu à une zone de texte à l'aide d'UI Automation
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique contient un exemple de code qui montre comment utiliser [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour insérer du texte dans une zone de texte sur une seule ligne. Une autre méthode est fournie pour les contrôles de texte enrichi et multilignes où [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] n’est pas applicable. À des fins de comparaison, l’exemple montre également comment utiliser des méthodes Win32 pour obtenir les mêmes résultats.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment parcourir une séquence de contrôles de texte dans une application cible. Chaque contrôle de texte est testé pour voir s’il est possible d’obtenir un objet <xref:System.Windows.Automation.ValuePattern> à l’aide de la méthode <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>. Si le contrôle de texte prend en charge <xref:System.Windows.Automation.ValuePattern>, la méthode <xref:System.Windows.Automation.ValuePattern.SetValue%2A> est utilisée pour insérer une chaîne définie par l’utilisateur dans le contrôle de texte. Dans le cas contraire, la méthode <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> est utilisée.  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a>Voir aussi

- [Exemple d’insertion de texte TextPattern](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))
