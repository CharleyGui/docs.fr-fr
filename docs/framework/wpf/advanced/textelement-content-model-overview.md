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
ms.openlocfilehash: ddb2613dc924424b5f4b9d90f06d44b45b7b5e77
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186902"
---
# <a name="textelement-content-model-overview"></a>Vue d'ensemble du modèle de contenu de TextElement
Cette vue d’ensemble du modèle <xref:System.Windows.Documents.TextElement>de contenu décrit le contenu pris en charge pour un . La <xref:System.Windows.Documents.Paragraph> classe est <xref:System.Windows.Documents.TextElement>un type de . Un modèle de contenu décrit les objets/éléments qui peuvent être contenus dans d’autres. Cette vue d’ensemble résume le <xref:System.Windows.Documents.TextElement>modèle de contenu utilisé pour les objets dérivés de . Pour plus d’informations, voir [Flow Document Overview](flow-document-overview.md).  

<a name="text_element_classes"></a>
## <a name="content-model-diagram"></a>Diagramme d’un modèle de contenu  
 Le diagramme suivant résume le modèle <xref:System.Windows.Documents.TextElement> de contenu pour les `TextElement` classes dérivées ainsi que la façon dont d’autres non-classes s’intègrent dans ce modèle.  
  
 ![Diagramme : schéma de relation contenant-contenu du flux](./media/flow-content-schema.png "Flow_Content_Schema")  
  
 Comme on peut le voir dans le diagramme précédent, les enfants autorisés pour <xref:System.Windows.Documents.Block> un <xref:System.Windows.Documents.Inline> élément ne sont pas nécessairement déterminés par la question de savoir si une classe est dérivée de la classe ou d’une classe. Par exemple, <xref:System.Windows.Documents.Span> une <xref:System.Windows.Documents.Inline>(classe dérivée) <xref:System.Windows.Documents.Inline> ne peut <xref:System.Windows.Documents.Figure> avoir que <xref:System.Windows.Documents.Inline>des éléments pour <xref:System.Windows.Documents.Block> enfants, mais une (également une classe dérivée) ne peut avoir que des éléments pour enfants. Un diagramme est donc utile pour déterminer rapidement quel élément peut être contenu dans un autre. À titre d’exemple, utilisons le diagramme pour déterminer comment <xref:System.Windows.Controls.RichTextBox>construire le contenu de flux d’un .  
  
1. Un <xref:System.Windows.Controls.RichTextBox> doit <xref:System.Windows.Documents.FlowDocument> contenir un qui <xref:System.Windows.Documents.Block>à son tour doit contenir un objet dérivé. Voici le segment correspondant extrait du diagramme précédent.  
  
     ![Diagramme : règles de relation contenant-contenu RichtextBox](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     À ce stade, le balisage peut ressembler à ceci.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2. Selon le diagramme, il <xref:System.Windows.Documents.Block> ya plusieurs <xref:System.Windows.Documents.Paragraph>éléments <xref:System.Windows.Documents.Section> <xref:System.Windows.Documents.Table>à <xref:System.Windows.Documents.List>choisir, y compris , , , et <xref:System.Windows.Documents.BlockUIContainer> (voir les classes dérivées du bloc dans le diagramme précédent). Disons que nous voulons <xref:System.Windows.Documents.Table>un . Selon le diagramme précédent, <xref:System.Windows.Documents.TableRowGroup> un <xref:System.Windows.Documents.TableRow> contient un <xref:System.Windows.Documents.TableCell> <xref:System.Windows.Documents.Block> <xref:System.Windows.Documents.Table> élément contenant, qui contiennent des éléments qui contiennent un objet dérivé. Ce qui suit est <xref:System.Windows.Documents.Table> le segment correspondant pour prise à partir du diagramme précédent.  
  
     ![Diagramme : Parent&#47;schéma enfant pour la table](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
     Voici le balisage correspondant.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3. Encore une fois, un ou plusieurs <xref:System.Windows.Documents.Block> éléments sont nécessaires sous un <xref:System.Windows.Documents.TableCell>. Pour simplifier, insérons du texte dans la cellule. Nous pouvons le <xref:System.Windows.Documents.Paragraph> faire <xref:System.Windows.Documents.Run> en utilisant un avec un élément. Ce qui suit est les segments <xref:System.Windows.Documents.Paragraph> correspondants <xref:System.Windows.Documents.Inline> du diagramme <xref:System.Windows.Documents.Run> montrant <xref:System.Windows.Documents.Inline> qu’un peut prendre un élément et qu’un (un élément) ne peut prendre que du texte simple.  
  
     ![Diagramme : Parent&#47;schéma d’enfant pour le paragraphe](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
     ![Diagramme : Parent&#47;schéma d’enfant pour la course](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 Voici le balisage de l’exemple complet.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>
## <a name="working-with-textelement-content-programmatically"></a>Utilisation du contenu de TextElement par programmation  
 Le contenu <xref:System.Windows.Documents.TextElement> d’a est composé de collections et donc <xref:System.Windows.Documents.TextElement> la manipulation programmatique du contenu des objets se fait en travaillant avec ces collections. Il existe trois collections <xref:System.Windows.Documents.TextElement> différentes utilisées par les classes dérivées :  
  
- <xref:System.Windows.Documents.InlineCollection>: Représente une <xref:System.Windows.Documents.Inline> collection d’éléments. <xref:System.Windows.Documents.InlineCollection> définit le contenu enfant autorisé des éléments <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Span> et <xref:System.Windows.Controls.TextBlock>.  
  
- <xref:System.Windows.Documents.BlockCollection>: Représente une <xref:System.Windows.Documents.Block> collection d’éléments. <xref:System.Windows.Documents.BlockCollection> définit le contenu enfant autorisé des éléments <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.TableCell>, <xref:System.Windows.Documents.Floater> et <xref:System.Windows.Documents.Figure>.  
  
- <xref:System.Windows.Documents.ListItemCollection>: Un élément de contenu de flux qui représente un <xref:System.Windows.Documents.List>élément de contenu particulier dans un ordre ordonné ou non ordonné .  
  
 Vous pouvez manipuler (ajouter ou supprimer des éléments) de ces collections en utilisant les propriétés **respectives d’Inlines**, **Blocks**, et **ListItems**. Les exemples suivants montrent comment manipuler le contenu d’une Span à l’aide de la propriété **Inlines.**  
  
> [!NOTE]
> Table utilise plusieurs collections pour manipuler son contenu, mais ces collections ne sont pas abordées ici. Pour plus d’informations, voir [Aperçu du tableau](table-overview.md).  
  
 L’exemple suivant <xref:System.Windows.Documents.Span> crée un nouvel `Add` objet, puis utilise la méthode <xref:System.Windows.Documents.Span>pour ajouter deux textes fonctionne comme des enfants de contenu de la .  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 L’exemple suivant <xref:System.Windows.Documents.Run> crée un nouvel élément et <xref:System.Windows.Documents.Span>l’insère au début de la .  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 L’exemple suivant supprime <xref:System.Windows.Documents.Inline> le <xref:System.Windows.Documents.Span>dernier élément dans le .  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 L’exemple suivant efface tout<xref:System.Windows.Documents.Inline> le contenu <xref:System.Windows.Documents.Span>(éléments) de la .  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>
## <a name="types-that-share-this-content-model"></a>Types partageant ce modèle de contenu  
 Les types suivants <xref:System.Windows.Documents.TextElement> héritent de la classe et peuvent être utilisés pour afficher le contenu décrit dans cette vue d’ensemble.  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 Notez que cette liste ne comprend que les types de nonabstract distribués avec le SDK Windows. Vous pouvez utiliser d’autres types qui héritent de <xref:System.Windows.Documents.TextElement>.  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>
## <a name="types-that-can-contain-textelement-objects"></a>Types pouvant contenir des objets TextElement  
 Voir [WPF Content Model](../controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Voir aussi

- [Manipuler un FlowDocument avec la propriété Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Manipuler des éléments de contenu dynamique avec la propriété Blocks](how-to-manipulate-flow-content-elements-through-the-blocks-property.md)
- [Manipuler un FlowDocument avec la propriété Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Manipuler les colonnes d’un tableau avec la propriété Columns](how-to-manipulate-table-columns-through-the-columns-property.md)
- [Manipuler les groupes de lignes d’un tableau avec la propriété RowGroups](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
