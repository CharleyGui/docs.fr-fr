---
title: 'Comment : créer une liaison simple'
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: faef59ed426059eb2d488d0584d3325c8d46d415
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453511"
---
# <a name="how-to-create-a-simple-binding"></a>Comment : créer une liaison simple
Cet exemple montre comment créer un <xref:System.Windows.Data.Binding>simple.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, vous avez un objet `Person` avec une propriété de chaîne nommée `PersonName`. L’objet `Person` est défini dans l’espace de noms appelé `SDKSample`.  
  
 La ligne surlignée qui contient l’élément `<src>` dans l’exemple suivant instancie l’objet `Person` avec une valeur de propriété `PersonName` de `Joe`. Cette opération s’effectue dans la section `Resources` et reçoit une `x:Key`.  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 La ligne surlignée qui contient l’élément `<TextBlock>` lie ensuite le contrôle <xref:System.Windows.Controls.TextBlock> à la propriété `PersonName`. Par conséquent, le <xref:System.Windows.Controls.TextBlock> apparaît avec la valeur « Joe ».  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
