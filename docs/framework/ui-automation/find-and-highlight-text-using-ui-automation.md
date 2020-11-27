---
title: Rechercher et mettre un texte en surbrillance à l'aide d'UI Automation
description: Rechercher et mettre en surbrillance du texte à l’aide d’UI Automation. Un exemple recherche et met en surbrillance séquentiellement chaque occurrence d’une chaîne dans le contenu de contrôle de texte.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text, highlighting
- finding text
- text, finding
- UI automation, highlighting text
- UI automation, finding text
- highlighting text
ms.assetid: b77693f5-87bb-4b29-a297-05ff882e2044
ms.openlocfilehash: 7ae933bdf12c81e48371fa89ba5fc5cf5dd4731e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276462"
---
# <a name="find-and-highlight-text-using-ui-automation"></a>Rechercher et mettre un texte en surbrillance à l'aide d'UI Automation

> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique montre comment rechercher et mettre en surbrillance séquentiellement chaque occurrence d’une chaîne dans le contenu d’un contrôle de texte à l’aide de [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] .  
  
## <a name="example"></a> Exemple  

 L’exemple suivant obtient un <xref:System.Windows.Automation.TextPattern> objet à partir d’un contrôle de texte. Un <xref:System.Windows.Automation.Text.TextPatternRange> objet, représentant le contenu textuel du document entier, est ensuite créé à l’aide <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> de la propriété de ce <xref:System.Windows.Automation.TextPattern> . Deux <xref:System.Windows.Automation.Text.TextPatternRange> objets supplémentaires sont ensuite créés pour la fonctionnalité de recherche et de mise en surbrillance séquentielle.  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#SearchTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#searchtarget)]
[!code-vb[FindText#SearchTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#searchtarget)]  
  
## <a name="see-also"></a>Voir aussi

- [Rechercher et mettre un texte en surbrillance à l'aide d'UI Automation](find-and-highlight-text-using-ui-automation.md)
