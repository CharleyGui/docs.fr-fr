---
title: 'Comment : rendre des données disponibles pour la liaison en XAML'
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 97e878e4932ca9122bf27f76c32d1a56e69f253a
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740609"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>Comment : rendre des données disponibles pour la liaison en XAML
Cette rubrique décrit les différentes façons dont vous pouvez rendre les données disponibles pour la liaison dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], selon les besoins de votre application.  
  
## <a name="example"></a>Exemple  
 Si vous souhaitez lier un objet common language runtime (CLR) à partir de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez rendre l’objet disponible pour la liaison pour le définir en tant que ressource et lui donner un `x:Key`. Dans l’exemple suivant, vous avez un objet `Person` avec une propriété de chaîne nommée `PersonName`. L’objet `Person` (dans la ligne affichée en surbrillance qui contient l’élément `<src>`) est défini dans l’espace de noms appelé `SDKSample`.  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Vous pouvez ensuite lier le contrôle <xref:System.Windows.Controls.TextBlock> à l’objet dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], comme le montre la ligne mise en surbrillance qui contient l’élément `<TextBlock>`. 
  
 Vous pouvez également utiliser la classe <xref:System.Windows.Data.ObjectDataProvider>, comme dans l’exemple suivant :  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 Vous définissez la liaison de la même façon, car la ligne mise en surbrillance qui contient l’élément `<TextBlock>` s’affiche.  
  
 Dans cet exemple, le résultat est le même : vous avez un <xref:System.Windows.Controls.TextBlock> avec le contenu de texte `Joe`. Toutefois, la classe <xref:System.Windows.Data.ObjectDataProvider> fournit des fonctionnalités telles que la possibilité d’effectuer une liaison au résultat d’une méthode. Vous pouvez choisir d’utiliser la classe <xref:System.Windows.Data.ObjectDataProvider> si vous avez besoin des fonctionnalités qu’elle fournit.  
  
 Toutefois, si vous effectuez une liaison à un objet qui a déjà été créé, vous devez définir la `DataContext` dans le code, comme dans l’exemple suivant.  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Pour accéder aux données XML à des fins de liaison à l’aide de la classe <xref:System.Windows.Data.XmlDataProvider>, consultez [lier à des données XML à l’aide d’un XMLDataProvider et de requêtes XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md). Pour accéder aux données XML pour la liaison à l’aide de la classe <xref:System.Windows.Data.ObjectDataProvider>, consultez [lier aux résultats de requête de type XDocument, XElement ou LINQ for XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).  
  
 Pour plus d’informations sur les différentes façons de spécifier les données que vous liez, consultez [spécifier la source de liaison](how-to-specify-the-binding-source.md). Pour plus d’informations sur les types de données que vous pouvez lier ou sur la façon d’implémenter vos propres objets common language runtime (CLR) pour la liaison, consultez [vue d’ensemble des sources de liaison](binding-sources-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
