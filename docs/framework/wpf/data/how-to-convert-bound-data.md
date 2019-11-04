---
title: 'Comment : convertir des données liées'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
ms.openlocfilehash: f9ad390626092d481bf47f017f643a29302c1b29
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458859"
---
# <a name="how-to-convert-bound-data"></a>Comment : convertir des données liées
Cet exemple montre comment appliquer la conversion aux données utilisées dans les liaisons.  
  
 Pour convertir des données pendant une liaison, vous devez créer une classe qui implémente l’interface <xref:System.Windows.Data.IValueConverter>, qui comprend les méthodes <xref:System.Windows.Data.IValueConverter.Convert%2A> et <xref:System.Windows.Data.IValueConverter.ConvertBack%2A>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’implémentation d’un convertisseur de dates qui convertit la valeur de date passée afin qu’elle affiche uniquement l’année, le mois et le jour. Lors de l’implémentation de l’interface <xref:System.Windows.Data.IValueConverter>, il est recommandé de décorer l’implémentation avec un attribut <xref:System.Windows.Data.ValueConversionAttribute> pour indiquer aux outils de développement les types de données impliqués dans la conversion, comme dans l’exemple suivant :  
  
 [!code-csharp[DataBindingLab#18](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 Une fois que vous avez créé un convertisseur, vous pouvez l’ajouter en tant que ressource dans votre fichier [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Dans l’exemple suivant, *src* est mappé à l’espace de noms dans lequel *DateConverter* est défini.  
  
 [!code-xaml[DataBindingLab#15](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 Enfin, vous pouvez utiliser le convertisseur dans votre liaison à l’aide de la syntaxe suivante. Dans l’exemple suivant, le contenu de texte de l' <xref:System.Windows.Controls.TextBlock> est lié à *StartDate*, qui est une propriété d’une source de données externe.  
  
 [!code-xaml[DataBindingLab#17](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 Les ressources de style référencées dans l’exemple ci-dessus sont définies dans une section de ressource non présentée dans cette rubrique.  
  
## <a name="see-also"></a>Voir aussi

- [Implémenter la validation de la liaison](how-to-implement-binding-validation.md)
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
