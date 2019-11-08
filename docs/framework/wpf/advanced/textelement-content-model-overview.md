---
title: Vue d'ensemble du modèle de contenu de TextElement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], flow documents
- TextElement content model [WPF]
- flow content elements [WPF], TextElement content model
ms.assetid: d0a7791c-b090-438c-812f-b9d009d83ee9
ms.openlocfilehash: acd67dd870c6912eddc368bf674804d98dba2db8
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740758"
---
# <a name="textelement-content-model-overview"></a>Vue d'ensemble du modèle de contenu de TextElement
Cette vue d’ensemble du modèle de contenu décrit le contenu pris en charge pour un <xref:System.Windows.Documents.TextElement>. La classe <xref:System.Windows.Documents.Paragraph> est un type de <xref:System.Windows.Documents.TextElement>. Un modèle de contenu décrit les objets/éléments qui peuvent être contenus dans d’autres. Cette vue d’ensemble résume le modèle de contenu utilisé pour les objets dérivés de <xref:System.Windows.Documents.TextElement>. Pour plus d’informations, consultez [vue d’ensemble des documents dynamiques](flow-document-overview.md).  

<a name="text_element_classes"></a>   
## <a name="content-model-diagram"></a>Diagramme d’un modèle de contenu  
 Le diagramme suivant résume le modèle de contenu pour les classes dérivées de <xref:System.Windows.Documents.TextElement>, ainsi que la façon dont d’autres classes non `TextElement` s’intègrent à ce modèle.  
  
 ![Diagramme : schéma de relation contenant-contenu de contenu dynamique](./media/flow-content-schema.png "Flow_Content_Schema")  
  
 Comme vous pouvez le voir dans le diagramme précédent, les enfants autorisés pour un élément ne sont pas nécessairement déterminés par le fait qu’une classe soit dérivée de la classe <xref:System.Windows.Documents.Block> ou d’une classe <xref:System.Windows.Documents.Inline>. Par exemple, une <xref:System.Windows.Documents.Span> (une classe dérivée de <xref:System.Windows.Documents.Inline>) peut uniquement avoir des éléments enfants <xref:System.Windows.Documents.Inline>, mais une <xref:System.Windows.Documents.Figure> (également une classe dérivée de <xref:System.Windows.Documents.Inline>) peut uniquement avoir des éléments enfants <xref:System.Windows.Documents.Block>. Un diagramme est donc utile pour déterminer rapidement quel élément peut être contenu dans un autre. Par exemple, utilisons le diagramme pour déterminer comment construire le contenu dynamique d’un <xref:System.Windows.Controls.RichTextBox>.  
  
1. Un <xref:System.Windows.Controls.RichTextBox> doit contenir un <xref:System.Windows.Documents.FlowDocument> qui doit à son tour contenir un objet dérivé de <xref:System.Windows.Documents.Block>. Voici le segment correspondant extrait du diagramme précédent.  
  
     ![Diagramme : règles de relation contenant-contenu RichTextBox](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     À ce stade, le balisage peut ressembler à ceci.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2. D’après le diagramme, vous avez le choix entre plusieurs éléments <xref:System.Windows.Documents.Block>, notamment <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.List>et <xref:System.Windows.Documents.BlockUIContainer> (voir les classes dérivées de Block dans le diagramme précédent). Supposons que nous voulons un <xref:System.Windows.Documents.Table>. D’après le diagramme précédent, un <xref:System.Windows.Documents.Table> contient un <xref:System.Windows.Documents.TableRowGroup> contenant des éléments <xref:System.Windows.Documents.TableRow>, qui contiennent des éléments <xref:System.Windows.Documents.TableCell> qui contiennent un objet dérivé de <xref:System.Windows.Documents.Block>. Voici le segment correspondant pour <xref:System.Windows.Documents.Table> extrait du diagramme précédent.  
  
     ![Diagramme : schéma&#47;enfant parent pour la table](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
     Voici le balisage correspondant.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3. Là encore, un ou plusieurs éléments <xref:System.Windows.Documents.Block> sont requis sous un <xref:System.Windows.Documents.TableCell>. Pour simplifier, insérons du texte dans la cellule. Nous pouvons le faire à l’aide d’un <xref:System.Windows.Documents.Paragraph> avec un élément <xref:System.Windows.Documents.Run>. Voici les segments correspondants du diagramme montrant qu’un <xref:System.Windows.Documents.Paragraph> peut prendre un élément <xref:System.Windows.Documents.Inline> et qu’un <xref:System.Windows.Documents.Run> (élément <xref:System.Windows.Documents.Inline>) ne peut prendre que du texte brut.  
  
     ![Diagramme : schéma&#47;enfant parent pour le paragraphe](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
     ![Diagramme : schéma&#47;enfant parent pour l’exécution](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 Voici le balisage de l’exemple complet.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## <a name="working-with-textelement-content-programmatically"></a>Utilisation du contenu de TextElement par programmation  
 Le contenu d’un <xref:System.Windows.Documents.TextElement> est constitué par des collections. par conséquent, la manipulation par programmation du contenu des objets <xref:System.Windows.Documents.TextElement> s’effectue en utilisant ces collections. Il existe trois collections différentes utilisées par les classes dérivées de <xref:System.Windows.Documents.TextElement> :  
  
- <xref:System.Windows.Documents.InlineCollection>: représente une collection d’éléments <xref:System.Windows.Documents.Inline>. <xref:System.Windows.Documents.InlineCollection> définit le contenu enfant autorisé des éléments <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Span> et <xref:System.Windows.Controls.TextBlock>.  
  
- <xref:System.Windows.Documents.BlockCollection>: représente une collection d’éléments <xref:System.Windows.Documents.Block>. <xref:System.Windows.Documents.BlockCollection> définit le contenu enfant autorisé des éléments <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.TableCell>, <xref:System.Windows.Documents.Floater> et <xref:System.Windows.Documents.Figure>.  
  
- <xref:System.Windows.Documents.ListItemCollection>: élément de contenu de Flow qui représente un élément de contenu particulier dans un <xref:System.Windows.Documents.List>ordonné ou non ordonné.  
  
 Vous pouvez manipuler (ajouter ou supprimer des éléments) de ces collections en utilisant les propriétés respectives des **Inlines**, des **blocs**et des **ListItems**. Les exemples suivants montrent comment manipuler le contenu d’une étendue à l’aide de la propriété **Inlines** .  
  
> [!NOTE]
> Table utilise plusieurs collections pour manipuler son contenu, mais ces collections ne sont pas abordées ici. Pour plus d’informations, consultez [vue d’ensemble des tables](table-overview.md).  
  
 L’exemple suivant crée un nouvel objet <xref:System.Windows.Documents.Span>, puis utilise la méthode `Add` pour ajouter deux séquences de texte en tant qu’enfants du contenu de l' <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 L’exemple suivant crée un nouvel élément <xref:System.Windows.Documents.Run> et l’insère au début du <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 L’exemple suivant supprime le dernier <xref:System.Windows.Documents.Inline> élément du <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 L’exemple suivant efface tout le contenu (<xref:System.Windows.Documents.Inline> éléments) du <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## <a name="types-that-share-this-content-model"></a>Types partageant ce modèle de contenu  
 Les types suivants héritent de la classe <xref:System.Windows.Documents.TextElement> et peuvent être utilisés pour afficher le contenu décrit dans cette vue d’ensemble.  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 Notez que cette liste comprend uniquement des types non abstraits distribués avec l’SDK Windows. Vous pouvez utiliser d’autres types qui héritent de <xref:System.Windows.Documents.TextElement>.  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## <a name="types-that-can-contain-textelement-objects"></a>Types pouvant contenir des objets TextElement  
 Consultez [modèle de contenu WPF](../controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Voir aussi

- [Manipuler un FlowDocument avec la propriété Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Manipuler des éléments de contenu dynamique avec la propriété Blocks](how-to-manipulate-flow-content-elements-through-the-blocks-property.md)
- [Manipuler un FlowDocument avec la propriété Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Manipuler les colonnes d’un tableau avec la propriété Columns](how-to-manipulate-table-columns-through-the-columns-property.md)
- [Manipuler les groupes de lignes d’un tableau avec la propriété RowGroups](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
