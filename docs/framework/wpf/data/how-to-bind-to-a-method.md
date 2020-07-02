---
title: 'Comment : effectuer une liaison à une méthode'
description: Suivez cet exemple pour savoir comment effectuer une liaison à la méthode d’un objet dans le Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding to methods using ObjectDataProvider
- binding [WPF], to methods
- methods [WPF], binding to
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
ms.openlocfilehash: 9501e6357203c21651e85f1d65059be1d70becf2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619596"
---
# <a name="how-to-bind-to-a-method"></a>Comment : effectuer une liaison à une méthode
L’exemple suivant montre comment effectuer une liaison à une méthode à l’aide de <xref:System.Windows.Data.ObjectDataProvider> .  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, `TemperatureScale` est une classe qui possède une méthode `ConvertTemp`, qui prend deux paramètres (`TempType)`, un de type `double` et l’autre de type `enum`) et convertit la valeur donnée d’une échelle de température à une autre. Dans l’exemple suivant, un <xref:System.Windows.Data.ObjectDataProvider> est utilisé pour instancier l' `TemperatureScale` objet. La méthode `ConvertTemp` est appelée avec deux paramètres spécifiés.  
  
 [!code-xaml[BindToMethod#WindowResources](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 Maintenant que la méthode est disponible en tant que ressource, vous pouvez effectuer la liaison à ses résultats. Dans l’exemple suivant, la <xref:System.Windows.Controls.TextBox.Text%2A> propriété de <xref:System.Windows.Controls.TextBox> et du <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> <xref:System.Windows.Controls.ComboBox> sont liées aux deux paramètres de la méthode. Cela permet aux utilisateurs de spécifier la température à convertir et l’échelle de température à partir de laquelle effectuer la conversion. Notez que <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> a la valeur `true` , car nous créons une liaison à la <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> propriété de l' <xref:System.Windows.Data.ObjectDataProvider> instance et non aux propriétés de l’objet encapsulé par <xref:System.Windows.Data.ObjectDataProvider> (l' `TemperatureScale` objet).  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A>Des dernières <xref:System.Windows.Controls.Label> mises à jour lorsque l’utilisateur modifie le contenu du <xref:System.Windows.Controls.TextBox> ou de la sélection de <xref:System.Windows.Controls.ComboBox> .  
  
 [!code-xaml[BindToMethod#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 Le convertisseur `DoubleToString` prend un double et le transforme en une chaîne dans la <xref:System.Windows.Data.IValueConverter.Convert%2A> direction (de la source de liaison à la cible de liaison, qui est la <xref:System.Windows.Controls.TextBox.Text%2A> propriété) et convertit un en `string` `double` dans la <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> direction.  
  
 Le `InvalidationCharacterRule` est un <xref:System.Windows.Controls.ValidationRule> qui vérifie les caractères non valides. Le modèle d’erreur par défaut, qui est une bordure rouge autour du <xref:System.Windows.Controls.TextBox> , apparaît pour avertir les utilisateurs lorsque la valeur d’entrée n’est pas une valeur double.  
  
## <a name="see-also"></a>Voir aussi

- [Rubriques de procédures](data-binding-how-to-topics.md)
- [Lier à une énumération](how-to-bind-to-an-enumeration.md)
