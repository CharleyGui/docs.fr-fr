---
title: 'Comment : créer une liaison dans du code'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: 616487a16ebbe6e23fe067fb7ce72644aa3f919f
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458847"
---
# <a name="how-to-create-a-binding-in-code"></a>Comment : créer une liaison dans du code
Cet exemple montre comment créer et définir une <xref:System.Windows.Data.Binding> dans le code.  
  
## <a name="example"></a>Exemple  
 La classe <xref:System.Windows.FrameworkElement> et la classe <xref:System.Windows.FrameworkContentElement> exposent toutes deux une méthode `SetBinding`. Si vous liez un élément qui hérite de l’une de ces classes, vous pouvez appeler directement la méthode <xref:System.Windows.FrameworkElement.SetBinding%2A>.  
  
 L’exemple suivant crée une classe nommée, `MyData`, qui contient une propriété nommée `MyDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 L’exemple suivant montre comment créer un objet de liaison pour définir la source de la liaison.  L’exemple utilise <xref:System.Windows.FrameworkElement.SetBinding%2A> pour lier la propriété <xref:System.Windows.Controls.TextBlock.Text%2A> de `myText`, qui est un contrôle <xref:System.Windows.Controls.TextBlock>, à `MyDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Pour obtenir l’exemple de code complet, consultez [exemple de liaison de code uniquement](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).  
  
 Au lieu d’appeler <xref:System.Windows.FrameworkElement.SetBinding%2A>, vous pouvez utiliser la méthode statique <xref:System.Windows.Data.BindingOperations.SetBinding%2A> de la classe <xref:System.Windows.Data.BindingOperations>. L’exemple suivant appelle <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> au lieu de <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> pour lier `myText` à `myDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
