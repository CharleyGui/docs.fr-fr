---
title: 'Procédure : Spécifier le sens de la liaison'
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 023cd42ad5fb321e7ffa65f08673cb4145f49af4
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817908"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a>Procédure : Spécifier le sens de la liaison

Cet exemple montre comment spécifier si la liaison met à jour uniquement la propriété de la cible de liaison (cible), uniquement la propriété de la source de liaison (source), ou bien à la fois la propriété cible et la propriété source.  
  
## <a name="example"></a>Exemples  
 Vous utilisez la <xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType> propriété pour spécifier le sens de la liaison. Les options disponibles pour les mises à jour de liaison sont les suivantes:  
  
- <xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType>met à jour la propriété ou la propriété cible chaque fois que la propriété cible ou la propriété source change.  
  
- <xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType>met à jour la propriété cible uniquement lorsque la propriété source change.  
  
- <xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType>met à jour la propriété cible uniquement lorsque l’application démarre ou lorsque le <xref:System.Windows.FrameworkElement.DataContext%2A> subit une modification.  
  
- <xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType>met à jour la propriété source lorsque la propriété cible est modifiée.  
  
- <xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType>entraîne l’utilisation <xref:System.Windows.Data.Binding.Mode%2A> de la valeur par défaut de la propriété cible.  
  
 Pour plus d’informations, consultez l’énumération <xref:System.Windows.Data.BindingMode>.  
  
 L'exemple suivant indique comment définir la propriété <xref:System.Windows.Data.Binding.Mode%2A>.  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 Pour détecter les modifications de la source <xref:System.Windows.Data.BindingMode.OneWay> ( <xref:System.Windows.Data.BindingMode.TwoWay> applicables aux liaisons et), la source doit implémenter un mécanisme de notification de <xref:System.ComponentModel.INotifyPropertyChanged>modification de propriété approprié, tel que. Pour obtenir un exemple d'implémentation <xref:System.ComponentModel.INotifyPropertyChanged>, consultez [implémenter la notification de modification de propriété](how-to-implement-property-change-notification.md).  
  
 Pour <xref:System.Windows.Data.BindingMode.TwoWay> les <xref:System.Windows.Data.BindingMode.OneWayToSource> liaisons ou, vous pouvez contrôler le minutage des mises à jour de la source en définissant la <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriété. Pour plus d'informations, voir <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Data.Binding>
- [Vue d’ensemble de la liaison de données](data-binding-overview.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
