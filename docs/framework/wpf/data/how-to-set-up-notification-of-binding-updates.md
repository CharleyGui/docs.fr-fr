---
title: 'Comment : configurer la notification de mises à jour de liaisons'
ms.date: 03/30/2017
helpviewer_keywords:
- notifications [WPF], binding updates
- data binding [WPF], notification of binding updates
- binding [WPF], updates [WPF], notifications of
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
ms.openlocfilehash: dfa0f9264247f7585c1743e40fd980906556efd0
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454949"
---
# <a name="how-to-set-up-notification-of-binding-updates"></a><span data-ttu-id="a399a-102">Comment : configurer la notification de mises à jour de liaisons</span><span class="sxs-lookup"><span data-stu-id="a399a-102">How to: Set Up Notification of Binding Updates</span></span>
<span data-ttu-id="a399a-103">Cet exemple montre comment configurer l’envoi d’une notification lorsque la propriété de la cible de liaison (cible) ou de la source de liaison (source) d’une liaison a été mise à jour.</span><span class="sxs-lookup"><span data-stu-id="a399a-103">This example shows how to set up to be notified when the binding target (target) or the binding source (source) property of a binding has been updated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a399a-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="a399a-104">Example</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="a399a-105">déclenche un événement de mise à jour des données chaque fois que la source ou la cible de liaison a été mise à jour.</span><span class="sxs-lookup"><span data-stu-id="a399a-105">raises a data update event each time that the binding source or target has been updated.</span></span> <span data-ttu-id="a399a-106">En interne, cet événement est utilisé pour informer l’[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] qu’elle doit se mettre à jour, car les données liées ont changé.</span><span class="sxs-lookup"><span data-stu-id="a399a-106">Internally, this event is used to inform the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] that it should update, because the bound data has changed.</span></span> <span data-ttu-id="a399a-107">Notez que pour que ces événements fonctionnent, et que pour que la liaison unidirectionnelle ou bidirectionnelle fonctionne correctement, vous devez implémenter votre classe de données à l’aide de l’interface <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="a399a-107">Note that for these events to work, and also for one-way or two-way binding to work properly, you need to implement your data class using the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="a399a-108">Pour plus d’informations, consultez [Implémenter la notification des modifications de propriétés](how-to-implement-property-change-notification.md).</span><span class="sxs-lookup"><span data-stu-id="a399a-108">For more information, see [Implement Property Change Notification](how-to-implement-property-change-notification.md).</span></span>  
  
 <span data-ttu-id="a399a-109">Définissez la propriété <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> ou <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> (ou les deux) sur `true` dans la liaison.</span><span class="sxs-lookup"><span data-stu-id="a399a-109">Set the <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> or <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> property (or both) to `true` in the binding.</span></span> <span data-ttu-id="a399a-110">Le gestionnaire que vous fournissez pour écouter cet événement doit être directement attaché à l’élément sur lequel vous souhaitez être informé des modifications, ou au contexte de données global si vous souhaitez savoir que quelque chose dans le contexte a changé.</span><span class="sxs-lookup"><span data-stu-id="a399a-110">The handler you provide to listen for this event must be attached directly to the element where you want to be informed of changes, or to the overall data context if you want to be aware that anything in the context has changed.</span></span>  
  
 <span data-ttu-id="a399a-111">Voici un exemple qui montre comment configurer la notification lorsqu’une propriété cible a été mise à jour.</span><span class="sxs-lookup"><span data-stu-id="a399a-111">Here is an example that shows how to set up for notification when a target property has been updated.</span></span>  
  
 [!code-xaml[DirectionalBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 <span data-ttu-id="a399a-112">Vous pouvez ensuite affecter un gestionnaire basé sur le délégué EventHandler\<T >, *OnTargetUpdated* dans cet exemple, pour gérer l’événement :</span><span class="sxs-lookup"><span data-stu-id="a399a-112">You can then assign a handler based on the EventHandler\<T> delegate, *OnTargetUpdated* in this example, to handle the event:</span></span>  
  
 [!code-csharp[DirectionalBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 <span data-ttu-id="a399a-113">Les paramètres de l’événement peuvent être utilisés pour déterminer les détails de la propriété qui ont changé (par exemple, le type ou l’élément spécifique si le même gestionnaire est attaché à plusieurs éléments), ce qui peut être utile si plusieurs propriétés sont liées sur un seul élément.</span><span class="sxs-lookup"><span data-stu-id="a399a-113">Parameters of the event can be used to determine details about the property that changed (such as the type or the specific element if the same handler is attached to more than one element), which can be useful if there are multiple bound properties on a single element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a399a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a399a-114">See also</span></span>

- [<span data-ttu-id="a399a-115">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="a399a-115">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="a399a-116">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="a399a-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
