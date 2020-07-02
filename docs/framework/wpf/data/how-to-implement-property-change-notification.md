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
# <a name="how-to-implement-property-change-notification"></a><span data-ttu-id="c5c7d-103">Comment : implémenter la notification des modifications de propriétés</span><span class="sxs-lookup"><span data-stu-id="c5c7d-103">How to: Implement Property Change Notification</span></span>
<span data-ttu-id="c5c7d-104">Pour prendre en charge <xref:System.Windows.Data.BindingMode.OneWay> ou <xref:System.Windows.Data.BindingMode.TwoWay> lier pour permettre à vos propriétés de cible de liaison de refléter automatiquement les modifications dynamiques de la source de liaison (par exemple, pour que le volet de visualisation soit mis à jour automatiquement lorsque l’utilisateur modifie un formulaire), votre classe doit fournir les notifications de modification de propriété appropriées.</span><span class="sxs-lookup"><span data-stu-id="c5c7d-104">To support <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> binding to enable your binding target properties to automatically reflect the dynamic changes of the binding source (for example, to have the preview pane updated automatically when the user edits a form), your class needs to provide the proper property changed notifications.</span></span> <span data-ttu-id="c5c7d-105">Cet exemple montre comment créer une classe qui implémente <xref:System.ComponentModel.INotifyPropertyChanged> .</span><span class="sxs-lookup"><span data-stu-id="c5c7d-105">This example shows how to create a class that implements <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5c7d-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="c5c7d-106">Example</span></span>  
 <span data-ttu-id="c5c7d-107">Pour implémenter <xref:System.ComponentModel.INotifyPropertyChanged> , vous devez déclarer l' <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> événement et créer la `OnPropertyChanged` méthode.</span><span class="sxs-lookup"><span data-stu-id="c5c7d-107">To implement <xref:System.ComponentModel.INotifyPropertyChanged> you need to declare the <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> event and create the `OnPropertyChanged` method.</span></span> <span data-ttu-id="c5c7d-108">Pour chaque propriété pour laquelle vous souhaitez modifier les notifications, vous devez ensuite appeler `OnPropertyChanged` chaque fois que la propriété est mise à jour.</span><span class="sxs-lookup"><span data-stu-id="c5c7d-108">Then for each property you want change notifications for, you call `OnPropertyChanged` whenever the property is updated.</span></span>  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 <span data-ttu-id="c5c7d-109">Pour voir un exemple de la façon dont la `Person` classe peut être utilisée pour prendre en charge la <xref:System.Windows.Data.BindingMode.TwoWay> liaison, consultez [contrôler quand le texte TextBox met à jour la source](how-to-control-when-the-textbox-text-updates-the-source.md).</span><span class="sxs-lookup"><span data-stu-id="c5c7d-109">To see an example of how the `Person` class can be used to support <xref:System.Windows.Data.BindingMode.TwoWay> binding, see [Control When the TextBox Text Updates the Source](how-to-control-when-the-textbox-text-updates-the-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5c7d-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5c7d-110">See also</span></span>

- [<span data-ttu-id="c5c7d-111">Vue d’ensemble des sources de liaison</span><span class="sxs-lookup"><span data-stu-id="c5c7d-111">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="c5c7d-112">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="c5c7d-112">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="c5c7d-113">Rubriques de procédures</span><span class="sxs-lookup"><span data-stu-id="c5c7d-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
