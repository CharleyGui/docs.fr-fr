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
# <a name="how-to-implement-property-change-notification"></a><span data-ttu-id="e5084-102">Comment : implémenter la notification des modifications de propriétés</span><span class="sxs-lookup"><span data-stu-id="e5084-102">How to: Implement Property Change Notification</span></span>
<span data-ttu-id="e5084-103">Pour prendre en charge la liaison <xref:System.Windows.Data.BindingMode.OneWay> ou <xref:System.Windows.Data.BindingMode.TwoWay> pour permettre à vos propriétés de cible de liaison de refléter automatiquement les modifications dynamiques de la source de liaison (par exemple, pour que le volet de visualisation soit mis à jour automatiquement lorsque l’utilisateur modifie un formulaire), votre classe doit fournissez les notifications de modification de propriété appropriées.</span><span class="sxs-lookup"><span data-stu-id="e5084-103">To support <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> binding to enable your binding target properties to automatically reflect the dynamic changes of the binding source (for example, to have the preview pane updated automatically when the user edits a form), your class needs to provide the proper property changed notifications.</span></span> <span data-ttu-id="e5084-104">Cet exemple montre comment créer une classe qui implémente <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="e5084-104">This example shows how to create a class that implements <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5084-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="e5084-105">Example</span></span>  
 <span data-ttu-id="e5084-106">Pour implémenter <xref:System.ComponentModel.INotifyPropertyChanged> vous devez déclarer l’événement <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> et créer la méthode `OnPropertyChanged`.</span><span class="sxs-lookup"><span data-stu-id="e5084-106">To implement <xref:System.ComponentModel.INotifyPropertyChanged> you need to declare the <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> event and create the `OnPropertyChanged` method.</span></span> <span data-ttu-id="e5084-107">Pour chaque propriété pour laquelle vous souhaitez modifier les notifications, vous devez ensuite appeler `OnPropertyChanged` chaque fois que la propriété est mise à jour.</span><span class="sxs-lookup"><span data-stu-id="e5084-107">Then for each property you want change notifications for, you call `OnPropertyChanged` whenever the property is updated.</span></span>  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 <span data-ttu-id="e5084-108">Pour voir un exemple de la façon dont la classe `Person` peut être utilisée pour prendre en charge la liaison de <xref:System.Windows.Data.BindingMode.TwoWay>, consultez [contrôler le moment où le texte TextBox met à jour la source](how-to-control-when-the-textbox-text-updates-the-source.md).</span><span class="sxs-lookup"><span data-stu-id="e5084-108">To see an example of how the `Person` class can be used to support <xref:System.Windows.Data.BindingMode.TwoWay> binding, see [Control When the TextBox Text Updates the Source](how-to-control-when-the-textbox-text-updates-the-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5084-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5084-109">See also</span></span>

- [<span data-ttu-id="e5084-110">Vue d'ensemble des sources de liaison</span><span class="sxs-lookup"><span data-stu-id="e5084-110">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="e5084-111">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="e5084-111">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="e5084-112">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="e5084-112">How-to Topics</span></span>](data-binding-how-to-topics.md)
