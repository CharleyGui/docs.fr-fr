---
title: "Comment : produire une valeur en fonction d'une liste d'éléments liés"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], MultiBinding
- Multibinding [WPF]
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
ms.openlocfilehash: da183a34eb85de54b1e3f54f8d14c09e25640165
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459697"
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a>Comment : produire une valeur en fonction d'une liste d'éléments liés
<xref:System.Windows.Data.MultiBinding> vous permet de lier une propriété de cible de liaison à une liste de propriétés sources, puis d’appliquer une logique pour produire une valeur avec les entrées données. Cet exemple montre comment utiliser <xref:System.Windows.Data.MultiBinding>.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, `NameListData` fait référence à une collection d’objets `PersonName`, qui sont des objets contenant deux propriétés, `firstName` et `lastName`. L’exemple suivant produit une <xref:System.Windows.Controls.TextBlock> qui affiche le prénom et le nom d’une personne avec le nom de famille en premier.  
  
 [!code-xaml[MultiBinding#Resources1](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 Pour comprendre comment est généré le format nom-prénom, jetons un œil à l’implémentation du `NameConverter` :  
  
 [!code-csharp[MultiBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 `NameConverter` implémente l'interface <xref:System.Windows.Data.IMultiValueConverter>. `NameConverter` prend les valeurs des liaisons individuelles et les stocke dans le tableau d’objets de valeurs. L’ordre dans lequel les éléments de <xref:System.Windows.Data.Binding> apparaissent sous l’élément <xref:System.Windows.Data.MultiBinding> est l’ordre dans lequel ces valeurs sont stockées dans le tableau. La valeur de l’attribut <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> est référencée par l’argument de paramètre de la méthode <xref:System.Windows.Data.MultiBinding.Converter%2A>, qui exécute un commutateur sur le paramètre pour déterminer comment mettre en forme le nom.  
  
## <a name="see-also"></a>Voir aussi

- [Convertir des données liées](how-to-convert-bound-data.md)
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
