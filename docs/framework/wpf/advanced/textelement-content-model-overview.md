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
ms.openlocfilehash: 21df7228f8dca884c5f36be23ae1aced7b31cc9a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942215"
---
# <a name="textelement-content-model-overview"></a>Vue d'ensemble du modèle de contenu de TextElement
Cette vue d’ensemble du modèle de contenu décrit le <xref:System.Windows.Documents.TextElement>contenu pris en charge pour un. La <xref:System.Windows.Documents.Paragraph> classe est un type de <xref:System.Windows.Documents.TextElement>. Un modèle de contenu décrit les objets/éléments qui peuvent être contenus dans d’autres. Cette vue d’ensemble résume le modèle de contenu utilisé pour les <xref:System.Windows.Documents.TextElement>objets dérivés de. Pour plus d’informations, consultez [vue d’ensemble des documents dynamiques](flow-document-overview.md).  

<a name="text_element_classes"></a>   
## <a name="content-model-diagram"></a>Diagramme d’un modèle de contenu  
 Le diagramme suivant résume le modèle de contenu pour les classes dérivées de <xref:System.Windows.Documents.TextElement> , ainsi que la manière dont les autres non- `TextElement` classes s’intègrent à ce modèle.  
  
 ![Schémas Schéma]de relation contenant-contenu Flow(./media/flow-content-schema.png "Flow_Content_Schema")  
  
 Comme vous pouvez le voir dans le diagramme précédent, les enfants autorisés pour un élément ne sont pas nécessairement déterminés par le fait qu’une classe <xref:System.Windows.Documents.Block> soit dérivée <xref:System.Windows.Documents.Inline> de la classe ou d’une classe. Par exemple, une <xref:System.Windows.Documents.Span> <xref:System.Windows.Documents.Inline>(classe dérivée) ne peut avoir <xref:System.Windows.Documents.Inline> que des éléments enfants, mais <xref:System.Windows.Documents.Figure> une (également <xref:System.Windows.Documents.Inline>une classe dérivée de) ne <xref:System.Windows.Documents.Block> peut avoir que des éléments enfants. Un diagramme est donc utile pour déterminer rapidement quel élément peut être contenu dans un autre. Par exemple, utilisons le diagramme pour déterminer comment construire le contenu dynamique d’un <xref:System.Windows.Controls.RichTextBox>.  
  
1. Un <xref:System.Windows.Controls.RichTextBox> doit contenir un <xref:System.Windows.Documents.FlowDocument> qui doit à son tour contenir <xref:System.Windows.Documents.Block>un objet dérivé de. Voici le segment correspondant extrait du diagramme précédent.  
  
     ![Schémas Règles]de relation contenant-contenu RichTextBox(./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     À ce stade, le balisage peut ressembler à ceci.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2. D’après le diagramme, vous avez le <xref:System.Windows.Documents.Block> choix <xref:System.Windows.Documents.Paragraph>entre <xref:System.Windows.Documents.List> <xref:System.Windows.Documents.Section> <xref:System.Windows.Documents.Table>plusieurs éléments,,,, et <xref:System.Windows.Documents.BlockUIContainer> (voir les classes dérivées de Block dans le diagramme précédent). Supposons que nous voulons un <xref:System.Windows.Documents.Table>. D’après le diagramme précédent, un <xref:System.Windows.Documents.Table> contient un <xref:System.Windows.Documents.TableRowGroup> élément <xref:System.Windows.Documents.TableRow> contenant des éléments qui <xref:System.Windows.Documents.TableCell> contiennent des éléments qui <xref:System.Windows.Documents.Block>contiennent un objet dérivé de. Voici le segment <xref:System.Windows.Documents.Table> correspondant pris dans le diagramme précédent.  
  
     ![Schémas Schéma&#47;enfant parent pour la]table(./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
     Voici le balisage correspondant.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3. Là encore, un ou <xref:System.Windows.Documents.Block> plusieurs éléments sont requis sous <xref:System.Windows.Documents.TableCell>un. Pour simplifier, insérons du texte dans la cellule. Nous pouvons le faire à l' <xref:System.Windows.Documents.Paragraph> aide d' <xref:System.Windows.Documents.Run> un avec un élément. Voici les segments correspondants du <xref:System.Windows.Documents.Paragraph> diagramme montrant qu’un peut accepter un <xref:System.Windows.Documents.Inline> élément et qu’un <xref:System.Windows.Documents.Run> (un <xref:System.Windows.Documents.Inline> élément) ne peut prendre que du texte brut.  
  
     ![Schémas Schéma&#47;enfant parent pour le]paragraphe(./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
     ![Schémas Schéma&#47;enfant parent pour Run](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 Voici le balisage de l’exemple complet.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## <a name="working-with-textelement-content-programmatically"></a>Utilisation du contenu de TextElement par programmation  
 Le contenu d’un <xref:System.Windows.Documents.TextElement> est constitué par des collections. par conséquent, la manipulation par programmation du contenu <xref:System.Windows.Documents.TextElement> des objets s’effectue en utilisant ces collections. Il existe trois collections différentes utilisées par <xref:System.Windows.Documents.TextElement> les classes dérivées de:  
  
- <xref:System.Windows.Documents.InlineCollection>: Représente une collection d'éléments <xref:System.Windows.Documents.Inline>. <xref:System.Windows.Documents.InlineCollection> définit le contenu enfant autorisé des éléments <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Span> et <xref:System.Windows.Controls.TextBlock>.  
  
- <xref:System.Windows.Documents.BlockCollection>: Représente une collection d'éléments <xref:System.Windows.Documents.Block>. <xref:System.Windows.Documents.BlockCollection> définit le contenu enfant autorisé des éléments <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.TableCell>, <xref:System.Windows.Documents.Floater> et <xref:System.Windows.Documents.Figure>.  
  
- <xref:System.Windows.Documents.ListItemCollection>: Élément de contenu de Flow qui représente un élément de contenu particulier dans un ordonné ou <xref:System.Windows.Documents.List>non ordonné.  
  
 Vous pouvez manipuler (ajouter ou supprimer des éléments) de ces collections en utilisant les propriétésrespectives des Inlines, des **blocs**et des **ListItems**. Les exemples suivants montrent comment manipuler le contenu d’une étendue à l’aide de la propriété Inlines.  
  
> [!NOTE]
> Table utilise plusieurs collections pour manipuler son contenu, mais ces collections ne sont pas abordées ici. Pour plus d’informations, consultez [vue d’ensemble des tables](table-overview.md).  
  
 L’exemple suivant crée un nouvel <xref:System.Windows.Documents.Span> objet, puis utilise la `Add` méthode pour ajouter deux séquences de texte <xref:System.Windows.Documents.Span>en tant qu’enfants de contenu du.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 L’exemple suivant crée un nouvel <xref:System.Windows.Documents.Run> élément et l’insère au début <xref:System.Windows.Documents.Span>de.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 L’exemple suivant supprime le dernier <xref:System.Windows.Documents.Inline> élément <xref:System.Windows.Documents.Span>de.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 L’exemple suivant efface tout le contenu (<xref:System.Windows.Documents.Inline> éléments) <xref:System.Windows.Documents.Span>de.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## <a name="types-that-share-this-content-model"></a>Types partageant ce modèle de contenu  
 Les types suivants héritent de <xref:System.Windows.Documents.TextElement> la classe et peuvent être utilisés pour afficher le contenu décrit dans cette vue d’ensemble.  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 Notez que cette liste comprend uniquement des types non abstraits distribués [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]avec le. Vous pouvez utiliser d’autres types qui héritent de <xref:System.Windows.Documents.TextElement>.  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## <a name="types-that-can-contain-textelement-objects"></a>Types pouvant contenir des objets TextElement  
 Consultez [modèle de contenu WPF](../controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Voir aussi

- [Manipuler un FlowDocument avec la propriété Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Manipuler des éléments de contenu dynamique avec la propriété Blocks](how-to-manipulate-flow-content-elements-through-the-blocks-property.md)
- [Manipuler un FlowDocument avec la propriété Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Manipuler les colonnes d’un tableau avec la propriété Columns](how-to-manipulate-table-columns-through-the-columns-property.md)
- [Manipuler les groupes de lignes d’un tableau avec la propriété RowGroups](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
