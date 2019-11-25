---
title: 'Comment : contrôler quand le texte TextBox met à jour la source'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
ms.openlocfilehash: b211eb67e3bac95f74255935a39cc0d6aec61531
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974788"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>Comment : contrôler quand le texte TextBox met à jour la source
Cette rubrique explique comment utiliser la propriété <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> pour contrôler le minutage des mises à jour de la source de liaison. La rubrique utilise le contrôle <xref:System.Windows.Controls.TextBox> à titre d’exemple.

## <a name="example"></a>Exemple
 La propriété <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> a une valeur de <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> par défaut de <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. Cela signifie que si une application a une <xref:System.Windows.Controls.TextBox> avec une propriété <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> liée aux données, le texte que vous tapez dans la <xref:System.Windows.Controls.TextBox> ne met pas à jour la source tant que le <xref:System.Windows.Controls.TextBox> n’a pas perdu le focus (par exemple, lorsque vous cliquez en dehors de la <xref:System.Windows.Controls.TextBox>).

 Si vous souhaitez que la source soit mise à jour au fur et à mesure que vous tapez, définissez la <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> de la liaison sur <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>. Dans l’exemple suivant, les lignes de code en surbrillance montrent que les propriétés `Text` des <xref:System.Windows.Controls.TextBox> et des <xref:System.Windows.Controls.TextBlock> sont liées à la même propriété source. La propriété <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> de la liaison <xref:System.Windows.Controls.TextBox> a la valeur <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.

 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]

 Par conséquent, le <xref:System.Windows.Controls.TextBlock> affiche le même texte (car la source change) lorsque l’utilisateur entre du texte dans la <xref:System.Windows.Controls.TextBox>, comme illustré dans la capture d’écran suivante de l’exemple :

 ![Capture d’écran montrant une liaison de données simple.](./media/how-to-control-when-the-textbox-text-updates-the-source/data-binding-simple-binding-sample.png)

 Si vous avez une boîte de dialogue ou un formulaire modifiable par l’utilisateur et que vous souhaitez différer les mises à jour de la source jusqu’à ce que l’utilisateur ait fini de modifier les champs et clique sur « OK », vous pouvez définir la <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valeur de vos liaisons sur <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, comme dans l’exemple suivant :

 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]

 Lorsque vous affectez la valeur <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>à la <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>, la valeur source change uniquement quand l’application appelle la méthode <xref:System.Windows.Data.BindingExpression.UpdateSource%2A>. L’exemple suivant montre comment appeler <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> pour `itemNameTextBox`:

 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]

> [!NOTE]
> Vous pouvez utiliser la même technique pour les propriétés d’autres contrôles, mais gardez à l’esprit que la plupart des autres propriétés ont une valeur de <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> par défaut de <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>. Pour plus d’informations, consultez la page de propriétés <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.

> [!NOTE]
> La propriété <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> concerne les mises à jour de la source et n’est donc pertinente que pour les liaisons <xref:System.Windows.Data.BindingMode.TwoWay> ou <xref:System.Windows.Data.BindingMode.OneWayToSource>. Pour que les liaisons <xref:System.Windows.Data.BindingMode.TwoWay> et <xref:System.Windows.Data.BindingMode.OneWayToSource> fonctionnent, l’objet source doit fournir des notifications de modification de propriété. Vous pouvez consulter les exemples figurant dans cette rubrique pour plus d’informations. Vous pouvez également consulter la page [Implémenter la notification des modifications de propriétés](how-to-implement-property-change-notification.md).

## <a name="see-also"></a>Voir aussi

- [Rubriques de guide pratique](data-binding-how-to-topics.md)
