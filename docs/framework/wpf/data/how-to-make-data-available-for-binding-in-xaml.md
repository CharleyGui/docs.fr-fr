---
title: 'Procédure : Rendre des données disponibles pour la liaison en XAML'
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 3487a160cc49ab6b779a20157668915c2da33900
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401496"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>Procédure : Rendre des données disponibles pour la liaison en XAML
Cette rubrique décrit les différentes façons dont vous pouvez rendre les données disponibles pour [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]la liaison dans, en fonction des besoins de votre application.  
  
## <a name="example"></a>Exemple  
 Si vous avez un objet Common Language Runtime (CLR) à partir duquel [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]vous souhaitez établir une liaison, vous pouvez rendre l’objet disponible pour la liaison pour le définir en tant que ressource et lui donner un. `x:Key` Dans l’exemple suivant, vous avez un `Person` objet avec une propriété de chaîne `PersonName`nommée. L' `Person` objet (dans la ligne affichée en surbrillance `<src>` qui contient l’élément) est défini dans `SDKSample`l’espace de noms appelé.  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Vous pouvez ensuite lier le <xref:System.Windows.Controls.TextBlock> contrôle à l’objet dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], comme le montre la ligne en surbrillance qui contient l' `<TextBlock>` élément. 
  
 Vous pouvez également utiliser la <xref:System.Windows.Data.ObjectDataProvider> classe, comme dans l’exemple suivant:  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 Vous définissez la liaison de la même façon, car la ligne mise en surbrillance qui contient l' `<TextBlock>` élément s’affiche.  
  
 Dans cet exemple, le résultat est le même: vous avez un <xref:System.Windows.Controls.TextBlock> avec le contenu `Joe`de texte. Toutefois, la <xref:System.Windows.Data.ObjectDataProvider> classe fournit des fonctionnalités telles que la possibilité de créer une liaison avec le résultat d’une méthode. Vous pouvez choisir d’utiliser la <xref:System.Windows.Data.ObjectDataProvider> classe si vous avez besoin des fonctionnalités qu’elle fournit.  
  
 Toutefois, si vous effectuez une liaison à un objet qui a déjà été créé, vous devez définir dans `DataContext` le code, comme dans l’exemple suivant.  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Pour accéder [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] aux données pour la liaison <xref:System.Windows.Data.XmlDataProvider> à l’aide de la classe, consultez [lier aux données XML à l’aide d’un XMLDataProvider et de requêtes XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md). Pour accéder [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] aux données pour la liaison <xref:System.Windows.Data.ObjectDataProvider> à l’aide de la classe, consultez les résultats de la [requête bind to XDocument, XElement ou LINQ for XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).  
  
 Pour plus d’informations sur les différentes façons de spécifier les données que vous liez, consultez [spécifier la source de liaison](how-to-specify-the-binding-source.md). Pour plus d’informations sur les types de données que vous pouvez lier ou sur la façon d’implémenter vos propres objets common language runtime (CLR) pour la liaison, consultez [vue d’ensemble des sources de liaison](binding-sources-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la liaison de données](data-binding-overview.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
