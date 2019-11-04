---
title: 'Comment : implémenter la notification des modifications de propriétés'
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
ms.openlocfilehash: 4f9ff49a443577e119b0c1079abbe23bd7ede4c4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459744"
---
# <a name="how-to-implement-property-change-notification"></a>Comment : implémenter la notification des modifications de propriétés
Pour prendre en charge la liaison <xref:System.Windows.Data.BindingMode.OneWay> ou <xref:System.Windows.Data.BindingMode.TwoWay> pour permettre à vos propriétés de cible de liaison de refléter automatiquement les modifications dynamiques de la source de liaison (par exemple, pour que le volet de visualisation soit mis à jour automatiquement lorsque l’utilisateur modifie un formulaire), votre classe doit fournissez les notifications de modification de propriété appropriées. Cet exemple montre comment créer une classe qui implémente <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
## <a name="example"></a>Exemple  
 Pour implémenter <xref:System.ComponentModel.INotifyPropertyChanged> vous devez déclarer l’événement <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> et créer la méthode `OnPropertyChanged`. Pour chaque propriété pour laquelle vous souhaitez modifier les notifications, vous devez ensuite appeler `OnPropertyChanged` chaque fois que la propriété est mise à jour.  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 Pour voir un exemple de la façon dont la classe `Person` peut être utilisée pour prendre en charge la liaison de <xref:System.Windows.Data.BindingMode.TwoWay>, consultez [contrôler le moment où le texte TextBox met à jour la source](how-to-control-when-the-textbox-text-updates-the-source.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble des sources de liaison](binding-sources-overview.md)
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
