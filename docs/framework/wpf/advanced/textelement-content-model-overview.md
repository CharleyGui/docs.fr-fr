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
ms.openlocfilehash: 1e1f67440377db95a5e0896b8fd31b1ab720b188
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64630651"
---
# <a name="textelement-content-model-overview"></a>Vue d'ensemble du modèle de contenu de TextElement
Cette vue d’ensemble du modèle de contenu décrit le contenu pris en charge pour un <xref:System.Windows.Documents.TextElement>. Le <xref:System.Windows.Documents.Paragraph> classe est un type de <xref:System.Windows.Documents.TextElement>. Un modèle de contenu décrit les objets/éléments qui peuvent être contenus dans d’autres. Cette vue d’ensemble résume le modèle de contenu utilisé pour les objets dérivés de <xref:System.Windows.Documents.TextElement>. Pour plus d’informations, consultez [vue d’ensemble du Document de flux](flow-document-overview.md).  

<a name="text_element_classes"></a>   
## <a name="content-model-diagram"></a>Diagramme d’un modèle de contenu  
 Le diagramme suivant récapitule le modèle de contenu pour les classes dérivées à partir de <xref:System.Windows.Documents.TextElement> , ainsi que comment d’autres non - `TextElement` classes adaptées à ce modèle.  
  
 ![Diagramme : Schéma de relation contenant-contenu de flux](./media/flow-content-schema.png "Flow_Content_Schema")  
  
 Comme le montre le diagramme précédent, les enfants autorisés pour un élément ne sont pas nécessairement déterminés par si une classe est dérivée de la <xref:System.Windows.Documents.Block> classe ou un <xref:System.Windows.Documents.Inline> classe. Par exemple, un <xref:System.Windows.Documents.Span> (un <xref:System.Windows.Documents.Inline>-classe dérivée) peut uniquement avoir <xref:System.Windows.Documents.Inline> éléments enfants, mais un <xref:System.Windows.Documents.Figure> (également une <xref:System.Windows.Documents.Inline>-classe dérivée) ne peut avoir <xref:System.Windows.Documents.Block> éléments enfants. Un diagramme est donc utile pour déterminer rapidement quel élément peut être contenu dans un autre. Par exemple, nous allons utiliser le diagramme pour déterminer comment construire le contenu dynamique d’un <xref:System.Windows.Controls.RichTextBox>.  
  
1. Un <xref:System.Windows.Controls.RichTextBox> doit contenir un <xref:System.Windows.Documents.FlowDocument> qui doit contenir un <xref:System.Windows.Documents.Block>-objet dérivé. Voici le segment correspondant extrait du diagramme précédent.  
  
     ![Diagramme : Règles de relation contenant-contenu RichTextBox](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     À ce stade, le balisage peut ressembler à ceci.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2. Après le diagramme, il y en a plusieurs <xref:System.Windows.Documents.Block> éléments, notamment <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.List>, et <xref:System.Windows.Documents.BlockUIContainer> (voir les classes dérivées de Block dans le diagramme précédent). Supposons que nous voulons un <xref:System.Windows.Documents.Table>. Le diagramme précédent, un <xref:System.Windows.Documents.Table> contient un <xref:System.Windows.Documents.TableRowGroup> contenant <xref:System.Windows.Documents.TableRow> éléments qui contiennent des <xref:System.Windows.Documents.TableCell> les éléments qui contiennent un <xref:System.Windows.Documents.Block>-objet dérivé. Voici le segment correspondant pour <xref:System.Windows.Documents.Table> extrait du diagramme précédent.  
  
     ![Diagramme : Parent&#47;schéma enfant pour Table](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
     Voici le balisage correspondant.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3. Là encore, un ou plusieurs <xref:System.Windows.Documents.Block> éléments sont requis sous un <xref:System.Windows.Documents.TableCell>. Pour simplifier, insérons du texte dans la cellule. Nous pouvons procéder à l’aide un <xref:System.Windows.Documents.Paragraph> avec un <xref:System.Windows.Documents.Run> élément. Les segments correspondants extraits du diagramme qui suit est un <xref:System.Windows.Documents.Paragraph> peut prendre un <xref:System.Windows.Documents.Inline> élément et qu’un <xref:System.Windows.Documents.Run> (un <xref:System.Windows.Documents.Inline> élément) peut contenir uniquement du texte brut.  
  
     ![Diagramme : Parent&#47;schéma enfant pour Paragraph](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
     ![Diagramme : Parent&#47;schéma enfant pour Run](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 Voici le balisage de l’exemple complet.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## <a name="working-with-textelement-content-programmatically"></a>Utilisation du contenu de TextElement par programmation  
 Le contenu d’un <xref:System.Windows.Documents.TextElement> est constitué par les collections et donc manipulation par programmation le contenu de <xref:System.Windows.Documents.TextElement> objets s’effectue à l’aide de ces collections. Il existe trois collections différentes utilisées par <xref:System.Windows.Documents.TextElement> -classes dérivées :  
  
- <xref:System.Windows.Documents.InlineCollection>: Représente une collection d'éléments <xref:System.Windows.Documents.Inline>. <xref:System.Windows.Documents.InlineCollection> définit le contenu enfant autorisé des éléments <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Span> et <xref:System.Windows.Controls.TextBlock>.  
  
- <xref:System.Windows.Documents.BlockCollection>: Représente une collection d'éléments <xref:System.Windows.Documents.Block>. <xref:System.Windows.Documents.BlockCollection> définit le contenu enfant autorisé des éléments <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.TableCell>, <xref:System.Windows.Documents.Floater> et <xref:System.Windows.Documents.Figure>.  
  
- <xref:System.Windows.Documents.ListItemCollection>: Un élément de contenu de flux qui représente un élément de contenu particulier dans une liste ordonnée ou non ordonnée <xref:System.Windows.Documents.List>.  
  
 Vous pouvez manipuler (ajouter ou supprimer des éléments) à partir de ces collections à l’aide des propriétés **Inlines**, **blocs**, et **ListItems**. Les exemples suivants montrent comment manipuler le contenu d’un Span à l’aide du **Inlines** propriété.  
  
> [!NOTE]
>  Table utilise plusieurs collections pour manipuler son contenu, mais ces collections ne sont pas abordées ici. Pour plus d’informations, consultez [vue d’ensemble de la Table](table-overview.md).  
  
 L’exemple suivant crée un nouveau <xref:System.Windows.Documents.Span> objet, puis utilise le `Add` méthode pour ajouter du texte deux s’exécute en tant que contenu enfant de le <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 L’exemple suivant crée un nouveau <xref:System.Windows.Documents.Run> élément et l’insère au début de la <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 L’exemple suivant supprime le dernier <xref:System.Windows.Documents.Inline> élément dans le <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 L’exemple suivant efface tout le contenu (<xref:System.Windows.Documents.Inline> éléments) à partir de la <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## <a name="types-that-share-this-content-model"></a>Types partageant ce modèle de contenu  
 Les types suivants héritent la <xref:System.Windows.Documents.TextElement> classe et peut être utilisé pour afficher le contenu décrit dans cette vue d’ensemble.  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 Notez que cette liste inclut uniquement les types non abstraits distribués avec le [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]. Vous pouvez utiliser d’autres types qui héritent de <xref:System.Windows.Documents.TextElement>.  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## <a name="types-that-can-contain-textelement-objects"></a>Types pouvant contenir des objets TextElement  
 Consultez [modèle de contenu WPF](../controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Voir aussi

- [Manipuler un FlowDocument avec la propriété Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Manipuler des éléments de contenu dynamique avec la propriété Blocks](how-to-manipulate-flow-content-elements-through-the-blocks-property.md)
- [Manipuler un FlowDocument avec la propriété Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Manipuler les colonnes d’un tableau avec la propriété Columns](how-to-manipulate-table-columns-through-the-columns-property.md)
- [Manipuler les groupes de lignes d’un tableau avec la propriété RowGroups](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
