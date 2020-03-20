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
ms.openlocfilehash: 91e89dbf36024c31f4afcd9b6d956944baf13576
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174184"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>Comment : rendre des données disponibles pour la liaison en XAML
Ce sujet traite de différentes façons dont [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]vous pouvez rendre les données disponibles pour la liaison, en fonction des besoins de votre application.  
  
## <a name="example"></a> Exemple  
 Si vous avez un terme de langage commun (CLR) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]objet que vous souhaitez lier à partir de , une `x:Key`façon que vous pouvez rendre l’objet disponible pour la liaison est de le définir comme une ressource et lui donner un . Dans l’exemple suivant, `Person` vous avez un `PersonName`objet avec une propriété à cordes nommée . L’objet `Person` (dans la ligne `<src>` indiquée sur laquelle contient `SDKSample`l’élément) est défini dans l’espace nom appelé .  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Vous pouvez ensuite <xref:System.Windows.Controls.TextBlock> lier le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]contrôle à l’objet `<TextBlock>` en , comme le montre la ligne surlignée qui contient l’élément.
  
 Alternativement, vous pouvez <xref:System.Windows.Data.ObjectDataProvider> utiliser la classe, comme dans l’exemple suivant:  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 Vous définissez la liaison de la même `<TextBlock>` manière, comme le montre la ligne surlignée qui contient l’élément.  
  
 Dans cet exemple particulier, le résultat est <xref:System.Windows.Controls.TextBlock> le même `Joe`: vous avez un contenu texte avec. Cependant, <xref:System.Windows.Data.ObjectDataProvider> la classe fournit des fonctionnalités telles que la capacité de se lier au résultat d’une méthode. Vous pouvez choisir <xref:System.Windows.Data.ObjectDataProvider> d’utiliser la classe si vous avez besoin de la fonctionnalité qu’il fournit.  
  
 Toutefois, si vous êtes contraignant à un objet qui a `DataContext` déjà été créé, vous devez définir le code, comme dans l’exemple suivant.  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Pour accéder aux données XML pour la liaison à l’aide de la <xref:System.Windows.Data.XmlDataProvider> classe, voir Bind to [XML Data Using an XMLDataProvider et XPath Queries](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md). Pour accéder aux données XML pour la liaison à l’aide de la <xref:System.Windows.Data.ObjectDataProvider> classe, voir Bind to [XDocument, XElement ou LINQ pour les résultats de requête XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).  
  
 Pour plus d’informations sur de nombreuses façons dont vous pouvez spécifier les données que vous êtes contraignant, voir [Spécifier la source contraignante](how-to-specify-the-binding-source.md). Pour plus d’informations sur les types de données que vous pouvez lier à ou comment mettre en œuvre vos propres objets de temps d’exécution de langue commune (CLR) pour la liaison, voir [Binding Sources Overview](binding-sources-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- [Aperçu de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Sujets comment se passer](data-binding-how-to-topics.md)
