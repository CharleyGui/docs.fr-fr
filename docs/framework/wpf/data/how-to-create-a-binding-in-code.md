---
title: 'Comment : créer une liaison dans du code'
description: Apprenez à créer une liaison dans le code d’une application Windows Presentation Foundation en appelant directement la méthode SetBinding.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: aa2a29f4c1262d8ac54641b856c297b284b23a38
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165805"
---
# <a name="how-to-create-a-binding-in-code"></a>Comment : créer une liaison dans du code
Cet exemple montre comment créer et définir un <xref:System.Windows.Data.Binding> dans le code.  
  
## <a name="example"></a>Exemple  
 La <xref:System.Windows.FrameworkElement> classe et la <xref:System.Windows.FrameworkContentElement> classe exposent toutes deux une `SetBinding` méthode. Si vous liez un élément qui hérite de l’une de ces classes, vous pouvez appeler <xref:System.Windows.FrameworkElement.SetBinding%2A> directement la méthode.  
  
 L’exemple suivant crée une classe nommée, `MyData` , qui contient une propriété nommée `MyDataProperty` .  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 L’exemple suivant montre comment créer un objet de liaison pour définir la source de la liaison.  L’exemple utilise <xref:System.Windows.FrameworkElement.SetBinding%2A> pour lier la <xref:System.Windows.Controls.TextBlock.Text%2A> propriété de `myText` , qui est un <xref:System.Windows.Controls.TextBlock> contrôle, à `MyDataProperty` .  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Pour obtenir l’exemple de code complet, consultez [exemple de liaison de code uniquement](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).  
  
 Au lieu d’appeler <xref:System.Windows.FrameworkElement.SetBinding%2A> , vous pouvez utiliser la <xref:System.Windows.Data.BindingOperations.SetBinding%2A> méthode statique de la <xref:System.Windows.Data.BindingOperations> classe. L’exemple suivant appelle <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> au lieu de <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> pour effectuer une liaison `myText` à `myDataProperty` .  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Rubriques Comment](data-binding-how-to-topics.md)
