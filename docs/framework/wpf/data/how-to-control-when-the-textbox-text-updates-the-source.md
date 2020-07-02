---
title: 'Comment : contrôler quand le texte TextBox met à jour la source'
description: Contrôler le minutage des mises à jour de la source de liaison à l’aide de la propriété UpdateSourceTrigger dans Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
ms.openlocfilehash: 8f6eb5beb0d14a951f6e6cf6eb81e130f5a3e194
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622781"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>Comment : contrôler quand le texte TextBox met à jour la source
Cette rubrique explique comment utiliser la <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriété pour contrôler le minutage des mises à jour de la source de liaison. La rubrique utilise le <xref:System.Windows.Controls.TextBox> contrôle comme exemple.

## <a name="example"></a>Exemple
 La <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> valeur par défaut de la propriété est <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> . Cela signifie que si une application a un <xref:System.Windows.Controls.TextBox> avec une propriété liée aux données <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> , le texte que vous tapez dans le <xref:System.Windows.Controls.TextBox> ne met pas à jour la source tant que le ne <xref:System.Windows.Controls.TextBox> perd le focus (par exemple, lorsque vous cliquez en dehors de <xref:System.Windows.Controls.TextBox> ).

 Si vous souhaitez que la source soit mise à jour au fur et à mesure que vous tapez, affectez la valeur <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> à la de la liaison <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> . Dans l’exemple suivant, les lignes de code en surbrillance indiquent que les `Text` Propriétés de <xref:System.Windows.Controls.TextBox> et de <xref:System.Windows.Controls.TextBlock> sont liées à la même propriété source. La <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriété de la <xref:System.Windows.Controls.TextBox> liaison a la valeur <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> .

 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]

 En conséquence, le <xref:System.Windows.Controls.TextBlock> affiche le même texte (car la source change) lorsque l’utilisateur entre du texte dans le <xref:System.Windows.Controls.TextBox> , comme illustré dans la capture d’écran suivante de l’exemple :

 ![Capture d’écran montrant une liaison de données simple.](./media/how-to-control-when-the-textbox-text-updates-the-source/data-binding-simple-binding-sample.png)

 Si vous disposez d’une boîte de dialogue ou d’un formulaire modifiable par l’utilisateur et que vous souhaitez différer les mises à jour de la source jusqu’à ce que l’utilisateur ait fini de modifier les champs et clique sur « OK », vous pouvez définir la <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valeur de vos liaisons sur <xref:System.Windows.Data.UpdateSourceTrigger.Explicit> , comme dans l’exemple suivant :

 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]

 Lorsque vous affectez la <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valeur à <xref:System.Windows.Data.UpdateSourceTrigger.Explicit> , la valeur source change uniquement quand l’application appelle la <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> méthode. L’exemple suivant montre comment appeler <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> pour `itemNameTextBox` :

 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]

> [!NOTE]
> Vous pouvez utiliser la même technique pour les propriétés d’autres contrôles, mais gardez à l’esprit que la plupart des autres propriétés ont la valeur par défaut <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> . Pour plus d’informations, consultez la <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> page de propriétés.

> [!NOTE]
> La <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriété traite les mises à jour de la source et ne concerne donc que les <xref:System.Windows.Data.BindingMode.TwoWay> <xref:System.Windows.Data.BindingMode.OneWayToSource> liaisons ou. Pour <xref:System.Windows.Data.BindingMode.TwoWay> que <xref:System.Windows.Data.BindingMode.OneWayToSource> les liaisons et fonctionnent, l’objet source doit fournir des notifications de modification de propriété. Vous pouvez consulter les exemples figurant dans cette rubrique pour plus d’informations. Vous pouvez également consulter la page [Implémenter la notification des modifications de propriétés](how-to-implement-property-change-notification.md).

## <a name="see-also"></a>Voir aussi

- [Rubriques de procédures](data-binding-how-to-topics.md)
