---
title: 'Comment : implémenter la notification des modifications de propriétés'
description: Activez vos propriétés pour notifier automatiquement une source de liaison lorsque la valeur de propriété change dans Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- notifications of change [WPF]
- data binding [WPF], property change notifications
- change notifications [WPF]
- properties [WPF], change notifications
ms.assetid: 30b59d9e-8c3a-4349-aa82-4be837e841cf
ms.openlocfilehash: 6c298930b7b1f812e94ea6add8f53c67d3453530
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620779"
---
# <a name="how-to-implement-property-change-notification"></a>Comment : implémenter la notification des modifications de propriétés
Pour prendre en charge <xref:System.Windows.Data.BindingMode.OneWay> ou <xref:System.Windows.Data.BindingMode.TwoWay> lier pour permettre à vos propriétés de cible de liaison de refléter automatiquement les modifications dynamiques de la source de liaison (par exemple, pour que le volet de visualisation soit mis à jour automatiquement lorsque l’utilisateur modifie un formulaire), votre classe doit fournir les notifications de modification de propriété appropriées. Cet exemple montre comment créer une classe qui implémente <xref:System.ComponentModel.INotifyPropertyChanged> .  
  
## <a name="example"></a>Exemple  
 Pour implémenter <xref:System.ComponentModel.INotifyPropertyChanged> , vous devez déclarer l' <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> événement et créer la `OnPropertyChanged` méthode. Pour chaque propriété pour laquelle vous souhaitez modifier les notifications, vous devez ensuite appeler `OnPropertyChanged` chaque fois que la propriété est mise à jour.  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 Pour voir un exemple de la façon dont la `Person` classe peut être utilisée pour prendre en charge la <xref:System.Windows.Data.BindingMode.TwoWay> liaison, consultez [contrôler quand le texte TextBox met à jour la source](how-to-control-when-the-textbox-text-updates-the-source.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des sources de liaison](binding-sources-overview.md)
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Rubriques de procédures](data-binding-how-to-topics.md)
