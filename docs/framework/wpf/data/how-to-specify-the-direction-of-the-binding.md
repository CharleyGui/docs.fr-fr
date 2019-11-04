---
title: 'Comment : spécifier le sens de la liaison'
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 8f7d843382ee3409047d7cf9549267d582883984
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459091"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a><span data-ttu-id="92a04-102">Comment : spécifier le sens de la liaison</span><span class="sxs-lookup"><span data-stu-id="92a04-102">How to: Specify the direction of the binding</span></span>

<span data-ttu-id="92a04-103">Cet exemple montre comment spécifier si la liaison met à jour uniquement la propriété de la cible de liaison (cible), uniquement la propriété de la source de liaison (source), ou bien à la fois la propriété cible et la propriété source.</span><span class="sxs-lookup"><span data-stu-id="92a04-103">This example shows how to specify whether the binding updates only the binding target (target) property, the binding source (source) property, or both the target property and the source property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92a04-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="92a04-104">Example</span></span>  
 <span data-ttu-id="92a04-105">Vous utilisez la propriété <xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType> pour spécifier le sens de la liaison.</span><span class="sxs-lookup"><span data-stu-id="92a04-105">You use the <xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType> property to specify the direction of the binding.</span></span> <span data-ttu-id="92a04-106">Les options disponibles pour les mises à jour de liaison sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="92a04-106">The following are the available options for binding updates:</span></span>  
  
- <span data-ttu-id="92a04-107"><xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType> met à jour la propriété ou la propriété cible chaque fois que la propriété cible ou la propriété source change.</span><span class="sxs-lookup"><span data-stu-id="92a04-107"><xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType> updates the target property or the property whenever either the target property or the source property changes.</span></span>  
  
- <span data-ttu-id="92a04-108"><xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType> met à jour la propriété cible uniquement lorsque la propriété source change.</span><span class="sxs-lookup"><span data-stu-id="92a04-108"><xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType> updates the target property only when the source property changes.</span></span>  
  
- <span data-ttu-id="92a04-109"><xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType> met à jour la propriété cible uniquement lorsque l’application démarre ou lorsque le <xref:System.Windows.FrameworkElement.DataContext%2A> subit une modification.</span><span class="sxs-lookup"><span data-stu-id="92a04-109"><xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType> updates the target property only when the application starts or when the <xref:System.Windows.FrameworkElement.DataContext%2A> undergoes a change.</span></span>  
  
- <span data-ttu-id="92a04-110"><xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType> met à jour la propriété source lorsque la propriété cible est modifiée.</span><span class="sxs-lookup"><span data-stu-id="92a04-110"><xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType> updates the source property when the target property changes.</span></span>  
  
- <span data-ttu-id="92a04-111"><xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType> entraîne l’utilisation de la valeur de <xref:System.Windows.Data.Binding.Mode%2A> par défaut de la propriété cible.</span><span class="sxs-lookup"><span data-stu-id="92a04-111"><xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType> causes the default <xref:System.Windows.Data.Binding.Mode%2A> value of target property to be used.</span></span>  
  
 <span data-ttu-id="92a04-112">Pour plus d’informations, consultez l’énumération <xref:System.Windows.Data.BindingMode>.</span><span class="sxs-lookup"><span data-stu-id="92a04-112">For more information, see the <xref:System.Windows.Data.BindingMode> enumeration.</span></span>  
  
 <span data-ttu-id="92a04-113">L'exemple suivant indique comment définir la propriété <xref:System.Windows.Data.Binding.Mode%2A>.</span><span class="sxs-lookup"><span data-stu-id="92a04-113">The following example shows how to set the <xref:System.Windows.Data.Binding.Mode%2A> property.</span></span>  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 <span data-ttu-id="92a04-114">Pour détecter les modifications de la source (applicables aux liaisons <xref:System.Windows.Data.BindingMode.OneWay> et <xref:System.Windows.Data.BindingMode.TwoWay>), la source doit implémenter un mécanisme de notification de modification de propriété approprié, tel que <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="92a04-114">To detect source changes (applicable to <xref:System.Windows.Data.BindingMode.OneWay> and <xref:System.Windows.Data.BindingMode.TwoWay> bindings), the source must implement a suitable property change notification mechanism such as <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span> <span data-ttu-id="92a04-115">Consultez [implémenter la notification de modification de propriété](how-to-implement-property-change-notification.md) pour obtenir un exemple d’implémentation de <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="92a04-115">See [Implement Property Change Notification](how-to-implement-property-change-notification.md) for an example of an <xref:System.ComponentModel.INotifyPropertyChanged> implementation.</span></span>  
  
 <span data-ttu-id="92a04-116">Pour les liaisons <xref:System.Windows.Data.BindingMode.TwoWay> ou <xref:System.Windows.Data.BindingMode.OneWayToSource>, vous pouvez contrôler le minutage des mises à jour de la source en définissant la propriété <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.</span><span class="sxs-lookup"><span data-stu-id="92a04-116">For <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings, you can control the timing of the source updates by setting the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property.</span></span> <span data-ttu-id="92a04-117">Pour plus d'informations, voir <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.</span><span class="sxs-lookup"><span data-stu-id="92a04-117">See <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92a04-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92a04-118">See also</span></span>

- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="92a04-119">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="92a04-119">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="92a04-120">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="92a04-120">How-to Topics</span></span>](data-binding-how-to-topics.md)
