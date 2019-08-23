---
title: 'Procédure : Contrôler quand le texte TextBox met à jour la source'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
ms.openlocfilehash: d1d624d7550a1135431b7fffc7450e3a510855a7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966450"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>Procédure : Contrôler quand le texte TextBox met à jour la source
Cette rubrique explique comment utiliser la <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriété pour contrôler le minutage des mises à jour de la source de liaison. La rubrique utilise le <xref:System.Windows.Controls.TextBox> contrôle comme exemple.  
  
## <a name="example"></a>Exemples  
 L’élément de langage <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> la propriété a la <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>valeur par défaut. Cela signifie que si une application a <xref:System.Windows.Controls.TextBox> un avec un lié aux <xref:System.Windows.Controls.TextBox>données.<xref:System.Windows.Controls.TextBox.Text%2A> , le texte que vous tapez dans le <xref:System.Windows.Controls.TextBox> ne met pas à jour la source <xref:System.Windows.Controls.TextBox> tant que le ne perd le focus (par exemple, lorsque <xref:System.Windows.Controls.TextBox>vous cliquez en dehors du).  
  
 Si vous souhaitez que la source soit mise à jour au fur et à <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> mesure que vous tapez <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, affectez la valeur à la de la liaison. Dans l’exemple suivant, les lignes de code en surbrillance `Text` indiquent que les propriétés <xref:System.Windows.Controls.TextBox> de et <xref:System.Windows.Controls.TextBlock> de sont liées à la même propriété source. La <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriété de la <xref:System.Windows.Controls.TextBox> liaison a la valeur <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  
  
 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]  
  
 En conséquence, le <xref:System.Windows.Controls.TextBlock> affiche le même texte (car la source change) lorsque l’utilisateur entre du texte dans le <xref:System.Windows.Controls.TextBox>, comme illustré dans la capture d’écran suivante de l’exemple:  
  
 ![Capture d’écran montrant une liaison de données simple.](./media/how-to-control-when-the-textbox-text-updates-the-source/data-binding-simple-binding-sample.png)  
  
 Si vous disposez d’une boîte de dialogue ou d’un formulaire modifiable par l’utilisateur et que vous souhaitez différer les mises à jour de la source jusqu’à ce que l’utilisateur ait fini <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> de modifier les champs et clique sur «OK», vous pouvez définir la valeur de vos liaisons sur <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, comme dans l’exemple suivant:  
  
 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 Lorsque vous affectez <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> la valeur <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>à, la valeur source change uniquement quand l’application appelle <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> la méthode. L’exemple suivant montre comment appeler <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> pour: `itemNameTextBox`  
  
 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
> Vous pouvez utiliser la même technique pour les propriétés d’autres contrôles, mais gardez à l’esprit que la plupart des autres <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriétés ont <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>la valeur par défaut. Pour plus d’informations, consultez <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> la page de propriétés.  
  
> [!NOTE]
> La <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriété traite les mises à jour de la source et ne concerne donc <xref:System.Windows.Data.BindingMode.TwoWay> que <xref:System.Windows.Data.BindingMode.OneWayToSource> les liaisons ou. Pour <xref:System.Windows.Data.BindingMode.TwoWay> que <xref:System.Windows.Data.BindingMode.OneWayToSource> les liaisons et fonctionnent, l’objet source doit fournir des notifications de modification de propriété. Vous pouvez consulter les exemples figurant dans cette rubrique pour plus d’informations. Vous pouvez également consulter la page [Implémenter la notification des modifications de propriétés](how-to-implement-property-change-notification.md).  
  
## <a name="see-also"></a>Voir aussi

- [Rubriques de guide pratique](data-binding-how-to-topics.md)
