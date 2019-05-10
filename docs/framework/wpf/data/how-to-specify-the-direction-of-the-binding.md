---
title: 'Procédure : Spécifier le sens de la liaison'
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 164fae937fc3935c7640a898c0c1908fd0a6b6b1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625326"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a>Procédure : Spécifier le sens de la liaison
Cet exemple montre comment spécifier si la liaison met à jour uniquement la propriété de la cible de liaison (cible), uniquement la propriété de la source de liaison (source), ou bien à la fois la propriété cible et la propriété source.  
  
## <a name="example"></a>Exemple  
 Vous utilisez le <xref:System.Windows.Data.Binding.Mode%2A> propriété pour spécifier la direction de la liaison. La liste d’énumération suivante affiche les options disponibles pour les mises à jour de la liaison :  
  
- <xref:System.Windows.Data.BindingMode.TwoWay> met à jour la propriété cible ou la propriété chaque fois que la propriété cible ou la propriété source change.  
  
- <xref:System.Windows.Data.BindingMode.OneWay> met à jour la propriété cible uniquement lorsque la propriété source change.  
  
- <xref:System.Windows.Data.BindingMode.OneTime> met à jour la propriété cible uniquement lorsque l’application démarre ou lorsque le <xref:System.Windows.FrameworkElement.DataContext%2A> subit une modification.  
  
- <xref:System.Windows.Data.BindingMode.OneWayToSource> Lorsque la propriété cible change, met à jour la propriété source.  
  
- <xref:System.Windows.Data.BindingMode.Default> provoque la valeur par défaut <xref:System.Windows.Data.Binding.Mode%2A> valeur de propriété cible à utiliser.  
  
 Pour plus d’informations, consultez l’énumération <xref:System.Windows.Data.BindingMode>.  
  
 L'exemple suivant indique comment définir la propriété <xref:System.Windows.Data.Binding.Mode%2A>.  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 Pour détecter des modifications de source (applicables à <xref:System.Windows.Data.BindingMode.OneWay> et <xref:System.Windows.Data.BindingMode.TwoWay> liaisons), la source doit implémenter un mécanisme de notification de modification de propriété approprié tel que <xref:System.ComponentModel.INotifyPropertyChanged>. Consultez [Notification de modification de propriété implémenter](how-to-implement-property-change-notification.md) pour obtenir un exemple d’un <xref:System.ComponentModel.INotifyPropertyChanged> implémentation.  
  
 Pour <xref:System.Windows.Data.BindingMode.TwoWay> ou <xref:System.Windows.Data.BindingMode.OneWayToSource> liaisons, vous pouvez contrôler le minutage des mises à jour des source en définissant le <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriété. Pour plus d'informations, voir <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Data.Binding>
- [Vue d’ensemble de la liaison de données](data-binding-overview.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
