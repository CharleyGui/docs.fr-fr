---
title: "Comment : créer un mode d'affichage personnalisé pour un ListView"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
ms.openlocfilehash: 3b9ca17bddcecb1895205fca76f0a489ecf25c4f
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243217"
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a>Comment : Créer un mode de vue personnalisé pour un ListView

Cet exemple montre comment <xref:System.Windows.Controls.ListView.View%2A> créer un <xref:System.Windows.Controls.ListView> mode personnalisé pour un contrôle.  
  
## <a name="example"></a>Exemple  
 Vous devez <xref:System.Windows.Controls.ViewBase> utiliser la classe lorsque vous <xref:System.Windows.Controls.ListView> créez une vue personnalisée pour le contrôle. L’exemple suivant montre `PlainView` un mode de <xref:System.Windows.Controls.ViewBase> vue appelé qui est dérivé de la classe.  
  
 [!code-csharp[ListViewCustomView#PlainView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 Pour appliquer un style à la <xref:System.Windows.Style> vue personnalisée, utilisez la classe. L’exemple suivant <xref:System.Windows.Style> définit `PlainView` un mode de vue pour le mode. Dans l’exemple précédent, ce style est <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> défini comme la `PlainView`valeur de la propriété qui est définie pour .  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 Pour définir la disposition des données dans <xref:System.Windows.DataTemplate> un mode de vue personnalisé, définissez un objet. L’exemple suivant <xref:System.Windows.DataTemplate> définit un qui peut être `PlainView` utilisé pour afficher les données en mode vue.  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 L’exemple suivant montre <xref:System.Windows.ResourceKey> comment `PlainView` définir un mode <xref:System.Windows.DataTemplate> de vue qui utilise celui qui est défini dans l’exemple précédent.  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 Un <xref:System.Windows.Controls.ListView> contrôle peut utiliser une vue <xref:System.Windows.Controls.ListView.View%2A> personnalisée si vous définissez la propriété à la clé de ressource. L’exemple suivant montre `PlainView` comment spécifier comme mode de vue pour un <xref:System.Windows.Controls.ListView>.  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 Pour l’échantillon complet, voir [ListView with Multiple Views (C)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp) ou [ListView with Multiple Views (Visual Basic)](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Rubriques de procédures](listview-how-to-topics.md)
- [Vue d’ensemble de ListView](listview-overview.md)
- [Vue d’ensemble de GridView](gridview-overview.md)
