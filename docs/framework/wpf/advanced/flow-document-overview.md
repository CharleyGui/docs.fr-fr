---
title: Vue d'ensemble des documents dynamiques
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'documents [WPF], flow documents [WPF], , '
- ', '
- flow documents [WPF]
ms.assetid: ef236a50-d44f-43c8-ba7c-82b0c733c0b7
ms.openlocfilehash: 1dcba034dd934cb0e103cd131fcaa2088e2f93d3
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856145"
---
# <a name="flow-document-overview"></a>Vue d'ensemble des documents dynamiques

Les documents dynamiques sont conçus pour optimiser l’affichage et la lisibilité. Au lieu d’avoir une disposition prédéfinie, ces documents dynamiques ajustent et refluent dynamiquement leur contenu en fonction des variables d’exécution telles que la taille de la fenêtre, la résolution de l’appareil et les préférences facultatives de l’utilisateur. En outre, les documents dynamiques offrent des fonctionnalités de document avancées, telles que la pagination et les colonnes. Cette rubrique fournit une vue d’ensemble des documents dynamiques et explique comment les créer.

<a name="what_is_a_flow_document"></a>

## <a name="what-is-a-flow-document"></a>Description d’un document dynamique

Un document dynamique est conçu pour « redisposer le contenu » en fonction de la taille de la fenêtre, de la résolution de l’appareil et d’autres variables d’environnement. En outre, les documents dynamiques possèdent plusieurs fonctionnalités intégrées, notamment la recherche, les modes d’affichage qui optimisent la lisibilité et la possibilité de changer la taille et l’apparence des polices. Les documents dynamiques sont utilisés surtout quand la facilité de lecture est le scénario principal de consommation des documents. À l’inverse, les documents fixes sont conçus pour avoir une présentation statique. Ces documents sont utiles quand le contenu source doit être fidèlement respecté. Pour plus d’informations sur les différents types de documents [, consultez documents dans WPF](documents-in-wpf.md) .

L’illustration suivante montre un exemple de document dynamique affiché dans des fenêtres de différentes tailles. Chaque fois que la zone d’affichage change, le contenu est redisposé pour utiliser de façon optimale l’espace disponible.

![Redisposition du contenu du document dynamique](./media/edocs-flowdocument.png "eDocs_FlowDocument")

Comme illustré dans l’image ci-dessus, le contenu dynamique peut comprendre plusieurs composants, notamment des paragraphes, des listes, des images et bien plus encore. Ces composants correspondent à des éléments dans le balisage et à des objets dans le code procédural. Nous allons passer en revue ces classes plus en détail dans la section [classes liées au Flow](#flow_related_classes) de cette vue d’ensemble. Pour le moment, voici un exemple de code simple qui crée un document dynamique constitué d’un paragraphe avec du texte en gras et une liste.

[!code-xaml[FlowOvwSnippets_snip#SimpleFlowExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SimpleFlowExample.xaml#simpleflowexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SimpleFlowExample.cs#simpleflowcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SimpleFlowExample.vb#simpleflowcodeonlyexamplewholepage)]

Cet extrait de code est illustré ci-dessous.

![Capture d’écran Exemple]de(./media/flow-ovw-first-example.png "Flow_Ovw_First_Example") de FlowDocument rendu

Dans cet exemple, le <xref:System.Windows.Controls.FlowDocumentReader> contrôle est utilisé pour héberger le contenu dynamique. Pour plus d’informations sur les contrôles d’hébergement de contenu dynamique, consultez [types de documents dynamiques](#flow_document_types) . <xref:System.Windows.Documents.Paragraph>les éléments,, <xref:System.Windows.Documents.Bold> et sont utilisés pour contrôler la mise en forme du contenu, en fonction de leur ordre dans le balisage. <xref:System.Windows.Documents.List> <xref:System.Windows.Documents.ListItem> Par exemple, l' <xref:System.Windows.Documents.Bold> élément s’étend uniquement à une partie du texte du paragraphe ; par conséquent, seule cette partie du texte est en gras. Si vous avez déjà utilisé le langage HTML, cela doit vous sembler familier.

Comme indiqué dans l’illustration ci-dessus, plusieurs fonctionnalités sont intégrées aux documents dynamiques :

- Rechercher : Permet à l’utilisateur d’effectuer une recherche en texte intégral d’un document entier.

- Mode d’affichage : L’utilisateur peut sélectionner son mode d’affichage préféré, y compris un mode d’affichage de page unique (page par page), un mode d’affichage à deux pages à la fois (format de livre) et un mode d’affichage de défilement continu (sans fin).  Pour plus d’informations sur ces modes d’affichage <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>, consultez.

- Contrôles de navigation entre les pages : Si le mode d’affichage du document utilise des pages, les contrôles de navigation entre les pages incluent un bouton pour accéder à la page suivante (flèche bas) ou la page précédente (flèche vers le haut), ainsi que des indicateurs pour le numéro de page actuel et le nombre total de pages. Vous pouvez aussi faire défiler les pages à l’aide des touches de direction du clavier.

- Zoom : Les contrôles de zoom permettent à l’utilisateur d’augmenter ou de diminuer le niveau de zoom en cliquant respectivement sur les boutons plus ou moins. Les contrôles de zoom incluent également un curseur pour ajuster le niveau de zoom. Pour plus d'informations, consultez <xref:System.Windows.Controls.FlowDocumentReader.Zoom%2A>.

Ces fonctionnalités peuvent être modifiées selon le contrôle utilisé pour héberger le contenu dynamique. La section suivante décrit les différents contrôles.

<a name="flow_document_types"></a>

## <a name="flow-document-types"></a>Types de documents dynamiques

L’affichage et l’apparence du contenu des documents dynamiques dépendent de l’objet utilisé pour héberger le contenu dynamique. Quatre contrôles prennent en charge l’affichage du contenu dynamique : <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.RichTextBox>et <xref:System.Windows.Controls.FlowDocumentScrollViewer>. Ces contrôles sont brièvement décrits ci-dessous.

> [!NOTE]
> <xref:System.Windows.Documents.FlowDocument>est requis pour héberger directement le contenu dynamique, donc tous ces contrôles d’affichage <xref:System.Windows.Documents.FlowDocument> consomment un pour activer l’hébergement du contenu dynamique.

### <a name="flowdocumentreader"></a>FlowDocumentReader

<xref:System.Windows.Controls.FlowDocumentReader>inclut des fonctionnalités qui permettent à l’utilisateur de choisir dynamiquement entre différents modes d’affichage, y compris un mode d’affichage d’une seule page (page par page), un mode d’affichage à deux pages à un moment donné (format de lecture du livre) et un mode d’affichage de défilement continu (sans fin). Pour plus d’informations sur ces modes d’affichage <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>, consultez. Si vous n’avez pas besoin de basculer dynamiquement entre les différents modes d' <xref:System.Windows.Controls.FlowDocumentPageViewer> affichage <xref:System.Windows.Controls.FlowDocumentScrollViewer> , et de fournir des visionneuses de contenu de circulation plus légères qui sont fixes dans un mode d’affichage particulier.

### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer et FlowDocumentScrollViewer

<xref:System.Windows.Controls.FlowDocumentPageViewer>affiche le contenu en mode page par page, tandis que <xref:System.Windows.Controls.FlowDocumentScrollViewer> affiche le contenu en mode de défilement continu. <xref:System.Windows.Controls.FlowDocumentPageViewer> Et<xref:System.Windows.Controls.FlowDocumentScrollViewer> sont résolus en un mode d’affichage particulier. Comparez <xref:System.Windows.Controls.FlowDocumentReader>à, qui comprend des fonctionnalités qui permettent à l’utilisateur de choisir dynamiquement entre plusieurs modes d’affichage ( <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> comme fourni par l’énumération), au détriment d’une <xref:System.Windows.Controls.FlowDocumentPageViewer> plus <xref:System.Windows.Controls.FlowDocumentScrollViewer>grande quantité de ressources que ou.

Par défaut, une barre de défilement verticale est toujours affichée et une barre de défilement horizontale apparaît si nécessaire. L’interface utilisateur par <xref:System.Windows.Controls.FlowDocumentScrollViewer> défaut pour n’inclut pas de barre d’outils <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> ; Toutefois, la propriété peut être utilisée pour activer une barre d’outils intégrée.

### <a name="richtextbox"></a>RichTextBox

Vous utilisez une <xref:System.Windows.Controls.RichTextBox> lorsque vous souhaitez autoriser l’utilisateur à modifier le contenu dynamique. Par exemple, si vous souhaitez créer un éditeur qui permettait à un utilisateur de manipuler des éléments tels que des tableaux, des mises en forme en italique et en <xref:System.Windows.Controls.RichTextBox>gras, etc., vous devez utiliser un. Pour plus d’informations, consultez [vue d’ensemble de RichTextBox](../controls/richtextbox-overview.md) .

> [!NOTE]
> Le contenu dynamique à <xref:System.Windows.Controls.RichTextBox> l’intérieur d’un ne se comporte pas exactement comme le contenu de Flow contenu dans d’autres contrôles. Par exemple, il n’y a pas de <xref:System.Windows.Controls.RichTextBox> colonnes dans un et, par conséquent, aucun comportement de redimensionnement automatique. En outre, les fonctionnalités généralement intégrées du contenu dynamique, telles que la recherche, le mode d’affichage, la navigation entre les pages <xref:System.Windows.Controls.RichTextBox>et le zoom, ne sont pas disponibles dans un.

<a name="creating_flow_content"></a>

## <a name="creating-flow-content"></a>Création de contenu dynamique

Le contenu dynamique peut être complexe, constitué de différents éléments, notamment du texte, des images, <xref:System.Windows.UIElement> des tables et même des classes dérivées telles que des contrôles. Pour comprendre comment créer du contenu dynamique complexe, les points suivants sont essentiels :

- **Classes liées au Flow**: Chaque classe utilisée dans le contenu dynamique a un objectif spécifique. En outre, la relation hiérarchique entre les classes vous permet de comprendre comment elles sont utilisées. Par exemple, les classes dérivées <xref:System.Windows.Documents.Block> de la classe sont utilisées pour contenir d’autres objets, <xref:System.Windows.Documents.Inline> tandis que les classes dérivées de contiennent des objets affichés.

- **Schéma de contenu**: Un document dynamique peut nécessiter un nombre important d’éléments imbriqués. Le schéma du contenu indique les relations parent/enfant possibles entre les éléments.

Les sections suivantes décrivent en détail chacun des points ci-dessus.

<a name="flow_related_classes"></a>

## <a name="flow-related-classes"></a>Classes liées au contenu dynamique

Le diagramme ci-dessous contient les objets les plus souvent utilisés avec du contenu dynamique :

![Schémas Hiérarchie]de classe d’élément de contenu de Flow(./media/flow-class-hierarchy.png "Flow_Class_Hierarchy")

Pour faciliter la gestion du contenu dynamique, il existe deux catégories principales :

1. **Classes dérivées de Block**: Également appelé « éléments de contenu de bloc » ou simplement « éléments de bloc ». Les éléments qui héritent de peuvent être utilisés pour regrouper des éléments sous un parent commun ou pour appliquer des <xref:System.Windows.Documents.Block> attributs communs à un groupe.

2. **Classes dérivées de Inline**: Également appelé « éléments de contenu Inline » ou simplement « éléments Inline ». Les éléments qui héritent de <xref:System.Windows.Documents.Inline> sont contenus dans un élément de bloc ou un autre élément inline. Les éléments Inline sont souvent utilisés comme conteneur direct du contenu restitué à l’écran. Par exemple, un <xref:System.Windows.Documents.Paragraph> (élément Block) peut contenir un <xref:System.Windows.Documents.Run> (élément <xref:System.Windows.Documents.Run> Inline), mais contient en fait le texte qui est affiché à l’écran.

Chaque classe de ces deux catégories est brièvement décrite ci-dessous.

### <a name="block-derived-classes"></a>Classes dérivées de Block

**Paragraph**

<xref:System.Windows.Documents.Paragraph>est généralement utilisé pour regrouper du contenu dans un paragraphe. L’utilisation la plus courante et la plus simple de Paragraph consiste à créer un paragraphe de texte.

[!code-xaml[FlowOvwSnippets_snip#ParagraphExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ParagraphExample.xaml#paragraphexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ParagraphExample.cs#paragraphcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ParagraphExample.vb#paragraphcodeonlyexamplewholepage)]

Toutefois, vous pouvez également contenir d’autres éléments dérivés de Inline comme vous le verrez ci-dessous.

**Section**

<xref:System.Windows.Documents.Section>est utilisé uniquement pour contenir d' <xref:System.Windows.Documents.Block>autres éléments dérivés de. Il n’applique aucune mise en forme par défaut aux éléments qu’il contient. Toutefois, les valeurs de propriété définies sur <xref:System.Windows.Documents.Section> un s’appliquent à ses éléments enfants. Une section vous permet également d’itérer par programmation dans sa collection enfant. <xref:System.Windows.Documents.Section>est utilisé de la même façon que la \<balise div > en html.

Dans l’exemple ci-dessous, trois paragraphes sont définis <xref:System.Windows.Documents.Section>sous un. La section a une <xref:System.Windows.Documents.TextElement.Background%2A> valeur de propriété rouge, donc la couleur d’arrière-plan des paragraphes est également rouge.

[!code-xaml[FlowOvwSnippets_snip#SectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SectionExample.xaml#sectionexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SectionExample.cs#sectioncodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SectionExample.vb#sectioncodeonlyexamplewholepage)]

**BlockUIContainer**

<xref:System.Windows.Documents.BlockUIContainer>permet <xref:System.Windows.UIElement> aux éléments (c’est-à-dire a <xref:System.Windows.Controls.Button>) d’être incorporés dans le contenu de fluide dérivé du bloc. <xref:System.Windows.Documents.InlineUIContainer>(voir ci-dessous) est utilisé <xref:System.Windows.UIElement> pour incorporer des éléments dans le contenu de fluide dérivé de Inline. <xref:System.Windows.Documents.BlockUIContainer>et <xref:System.Windows.Documents.InlineUIContainer> sont importants, car il n’existe pas d’autre moyen <xref:System.Windows.UIElement> d’utiliser un dans le contenu dynamique, sauf s’il est contenu dans l’un de ces deux éléments.

L’exemple suivant montre comment utiliser l’élément <xref:System.Windows.Documents.BlockUIContainer> pour héberger <xref:System.Windows.UIElement> des objets dans le contenu dynamique.

[!code-xaml[SpanSnippets#_BlockUIXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml#_blockuixaml)]

L’illustration suivante montre le rendu de cet exemple :

![Capture d’écran montrant un UIElement incorporé dans le contenu dynamique.](./media/flow-document-overview/embedded-blockuicontainer.png)

**List**

<xref:System.Windows.Documents.List>est utilisé pour créer une liste à puces ou une liste numérique. Affectez <xref:System.Windows.Documents.List.MarkerStyle%2A> à la propriété <xref:System.Windows.TextMarkerStyle> une valeur d’énumération pour déterminer le style de la liste. L’exemple ci-dessous montre comment créer une liste simple.

[!code-xaml[FlowOvwSnippets_snip#ListExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ListExample.xaml#listexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ListExample.cs#listcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ListExample.vb#listcodeonlyexamplewholepage)]

> [!NOTE]
> <xref:System.Windows.Documents.List>est le seul élément de Flow qui utilise <xref:System.Windows.Documents.ListItemCollection> le pour gérer les éléments enfants.

**Table**

<xref:System.Windows.Documents.Table>est utilisé pour créer une table. <xref:System.Windows.Documents.Table>est similaire à l' <xref:System.Windows.Controls.Grid> élément, mais il a davantage de fonctionnalités et, par conséquent, nécessite une plus grande surcharge de ressources. Étant <xref:System.Windows.Controls.Grid> donné que <xref:System.Windows.UIElement>est un, il ne peut pas être utilisé dans le contenu de fluide <xref:System.Windows.Documents.BlockUIContainer> , <xref:System.Windows.Documents.InlineUIContainer>sauf s’il est contenu dans un ou. Pour plus d’informations <xref:System.Windows.Documents.Table>sur, consultez [vue d’ensemble des tables](table-overview.md).

### <a name="inline-derived-classes"></a>Classes dérivées d’Inline

**Exécuter**

<xref:System.Windows.Documents.Run>est utilisé pour contenir du texte non mis en forme. Vous pouvez vous <xref:System.Windows.Documents.Run> attendre à ce que les objets soient largement utilisés dans le contenu dynamique. Toutefois, dans le balisage, <xref:System.Windows.Documents.Run> les éléments ne doivent pas obligatoirement être utilisés explicitement. <xref:System.Windows.Documents.Run>doit être utilisé lors de la création ou de la manipulation de documents de workflow à l’aide de code. Par exemple, dans le balisage ci-dessous <xref:System.Windows.Documents.Paragraph> , la <xref:System.Windows.Documents.Run> première spécifie l’élément explicitement alors que le deuxième ne le fait pas. Les deux paragraphes génèrent le même résultat.

[!code-xaml[FlowOvwSnippets_snip#RunExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/RunSnippetsExample.xaml#runexample1)]

> [!NOTE]
> À partir du .NET Framework 4, la <xref:System.Windows.Documents.Run.Text%2A> propriété de l' <xref:System.Windows.Documents.Run> objet est une propriété de dépendance. Vous pouvez lier la <xref:System.Windows.Documents.Run.Text%2A> propriété à une source de données, telle qu' <xref:System.Windows.Controls.TextBlock>un. La <xref:System.Windows.Documents.Run.Text%2A> propriété prend entièrement en charge la liaison unidirectionnelle. La <xref:System.Windows.Documents.Run.Text%2A> propriété prend également en charge la liaison bidirectionnelle <xref:System.Windows.Controls.RichTextBox>, à l’exception de. Pour obtenir un exemple, consultez <xref:System.Windows.Documents.Run.Text%2A?displayProperty=nameWithType>.

**Span**

<xref:System.Windows.Documents.Span>regroupe d’autres éléments de contenu Inline. Aucun rendu inhérent n’est appliqué au contenu dans <xref:System.Windows.Documents.Span> un élément. Toutefois, <xref:System.Windows.Documents.Span> <xref:System.Windows.Documents.Italic> les éléments qui héritent <xref:System.Windows.Documents.Hyperlink>de <xref:System.Windows.Documents.Bold>incluant, <xref:System.Windows.Documents.Underline> et appliquent la mise en forme au texte.

Voici un exemple de <xref:System.Windows.Documents.Span> qui est utilisé pour contenir du contenu Inline, notamment du texte, un <xref:System.Windows.Documents.Bold> élément et <xref:System.Windows.Controls.Button>un.

[!code-xaml[FlowOvwSnippets_snip#SpanExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SpanExample.xaml#spanexamplewholepage)]

La capture d’écran suivante montre le rendu de cet exemple.

![Capture d’écran Exemple]d’étendue rendue(./media/flow-spanexample.gif "Flow_SpanExample")

**InlineUIContainer**

<xref:System.Windows.Documents.InlineUIContainer>active <xref:System.Windows.UIElement> les éléments (par exemple, un <xref:System.Windows.Controls.Button>contrôle comme) à incorporer <xref:System.Windows.Documents.Inline> dans un élément de contenu. Cet élément est l’équivalent inline de <xref:System.Windows.Documents.BlockUIContainer> décrit ci-dessus. Vous trouverez ci-dessous un <xref:System.Windows.Documents.InlineUIContainer> exemple qui utilise <xref:System.Windows.Controls.Button> pour insérer une inline dans un <xref:System.Windows.Documents.Paragraph>.

[!code-xaml[FlowOvwSnippets_snip#InlineUIContainerExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/InlineUIContainerExample.xaml#inlineuicontainerexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/InlineUIContainerExample.cs#inlineuicontainercodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/InlineUIContainerExample.vb#inlineuicontainercodeonlyexamplewholepage)]

> [!NOTE]
> <xref:System.Windows.Documents.InlineUIContainer>n’a pas besoin d’être utilisé explicitement dans le balisage. Si vous l’omettez, un <xref:System.Windows.Documents.InlineUIContainer> est créé quand le code est compilé.

**Figure et Floater**

<xref:System.Windows.Documents.Figure>et <xref:System.Windows.Documents.Floater> sont utilisés pour incorporer du contenu dans des documents dynamiques avec des propriétés de positionnement qui peuvent être personnalisées indépendamment du contenu principal. <xref:System.Windows.Documents.Figure>les <xref:System.Windows.Documents.Floater> éléments ou sont souvent utilisés pour mettre en surbrillance ou accentuer des parties de contenu, pour héberger des images de prise en charge ou d’autres contenus au sein du contenu de contenu principal, ou pour injecter du contenu étroitement lié, tel que des publications.

L’exemple suivant montre comment incorporer un <xref:System.Windows.Documents.Figure> dans un paragraphe de texte.

[!code-xaml[FlowOvwSnippets_snip#FigureExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/FigureExample.xaml#figureexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/FigureExample.cs#figurecodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/FigureExample.vb#figurecodeonlyexamplewholepage)]

L’illustration suivante montre le rendu de cet exemple.

![Capture d’écran Exemple]de figure(./media/flow-ovw-figure-example.png "Flow_Ovw_Figure_Example")

<xref:System.Windows.Documents.Figure>et <xref:System.Windows.Documents.Floater> diffèrent de plusieurs façons et sont utilisés pour différents scénarios.

**Figure :**

- Peut être positionné : Vous pouvez définir ses ancres horizontale et verticale pour l’ancrer par rapport à la page, au contenu, à la colonne ou au paragraphe. Vous pouvez également utiliser ses <xref:System.Windows.Documents.Figure.HorizontalOffset%2A> propriétés <xref:System.Windows.Documents.Figure.VerticalOffset%2A> et pour spécifier des décalages arbitraires.

- Dimensionnable sur plusieurs colonnes : Vous pouvez définir <xref:System.Windows.Documents.Figure> la hauteur et la largeur en multiples de la hauteur ou de la largeur de la page, du contenu ou de la colonne. Notez que, dans les deux premiers cas, les multiples supérieurs à 1 ne sont pas autorisés. Par exemple, vous pouvez définir la largeur d’un <xref:System.Windows.Documents.Figure> sur « 0,5 page » ou « 0,25 content » ou « 2 Column ». Vous pouvez également définir des valeurs en pixels absolues pour la hauteur et la largeur.

- Ne pagine pas : Si le contenu à l' <xref:System.Windows.Documents.Figure> intérieur d’un ne tient <xref:System.Windows.Documents.Figure>pas dans le, il affiche le contenu qui est ajusté et le reste du contenu est perdu

**Floater :**

- Non positionnable : cet élément s’affiche dans l’espace disponible, quel qu’il soit. Vous ne pouvez pas définir le décalage ou <xref:System.Windows.Documents.Floater>ancrer un.

- Ne peut pas être dimensionné à plusieurs colonnes : Par défaut, <xref:System.Windows.Documents.Floater> les tailles sont représentées dans une colonne. Elle possède une <xref:System.Windows.Documents.Floater.Width%2A> propriété qui peut être définie sur une valeur en pixels absolue, mais si cette valeur est supérieure à une largeur de colonne, elle est ignorée et le floater est dimensionné au niveau d’une colonne. Vous pouvez la redimensionner sur moins d’une colonne en définissant la largeur en pixels correcte, mais le dimensionnement n’est pas relatif à la colonne, donc « colonne <xref:System.Windows.Documents.Floater> 0.5 » n’est pas une expression valide pour la largeur. <xref:System.Windows.Documents.Floater>n’a pas de propriété Height et sa hauteur ne peut pas être définie, sa hauteur dépend du contenu

- <xref:System.Windows.Documents.Floater>pagine Si son contenu à la largeur spécifiée s’étend à plus de 1 hauteur de colonne, le floater s’interrompt et pagine sur la colonne suivante, la page suivante, etc.

 <xref:System.Windows.Documents.Figure>est un emplacement idéal pour placer du contenu autonome dans lequel vous souhaitez contrôler la taille et le positionnement, et êtes sûr que le contenu sera adapté à la taille spécifiée. <xref:System.Windows.Documents.Floater>est un bon endroit pour placer un contenu plus libre qui circule comme le contenu de la page principale, mais qui en est séparé.

**LineBreak**

<xref:System.Windows.Documents.LineBreak>provoque l’apparition d’un saut de ligne dans le contenu dynamique. L'exemple suivant montre l'utilisation de <xref:System.Windows.Documents.LineBreak>.

[!code-xaml[FlowOvwSnippets_snip#LineBreakExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/LineBreakExample.xaml#linebreakexamplewholepage)]

La capture d’écran suivante montre le rendu de cet exemple.

![Capture d’écran Exemple]de LineBreak(./media/flow-ovw-linebreakexample.png "Flow_Ovw_LineBreakExample")

### <a name="flow-collection-elements"></a>Éléments de collection de flux

Dans la plupart des exemples ci-dessus <xref:System.Windows.Documents.BlockCollection> , <xref:System.Windows.Documents.InlineCollection> les et sont utilisés pour construire du contenu dynamique par programmation. Par exemple, pour ajouter des éléments à <xref:System.Windows.Documents.Paragraph>un, vous pouvez utiliser la syntaxe suivante :

```csharp
myParagraph.Inlines.Add(new Run("Some text"));
```

Cela ajoute un <xref:System.Windows.Documents.Run> <xref:System.Windows.Documents.InlineCollection> au du <xref:System.Windows.Documents.Paragraph>.  Il s’agit du même que celui <xref:System.Windows.Documents.Run> trouvé implicite <xref:System.Windows.Documents.Paragraph> dans un dans le balisage :

```xml
<Paragraph>
Some Text
</Paragraph>
```

En guise d’exemple d' <xref:System.Windows.Documents.BlockCollection>utilisation du, l’exemple suivant crée <xref:System.Windows.Documents.Section> un nouveau, puis utilise la <xref:System.Windows.Documents.Section> méthode **Add** pour ajouter <xref:System.Windows.Documents.Paragraph> un nouveau au contenu.

[!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
[!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]

En plus d’ajouter des éléments à une collection de flux, vous pouvez aussi en supprimer.  L’exemple suivant supprime le dernier <xref:System.Windows.Documents.Inline> élément <xref:System.Windows.Documents.Span>de.

[!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
[!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]

L’exemple suivant efface tout le contenu (<xref:System.Windows.Documents.Inline> éléments) <xref:System.Windows.Documents.Span>de.

[!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
[!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]

Quand vous utilisez du contenu dynamique par programmation, vous employez certainement très souvent ces collections.

Le fait qu’un élément de <xref:System.Windows.Documents.InlineCollection> Flow utilise un (Inline <xref:System.Windows.Documents.BlockCollection> ) ou un (bloc) pour contenir ses éléments enfants dépend du type d’éléments<xref:System.Windows.Documents.Block> enfants <xref:System.Windows.Documents.Inline>(ou) qui peuvent être contenus par le parent. Les règles relatives à la relation contenant-contenu pour les éléments de contenu dynamique sont résumées dans le schéma du contenu présenté à la section suivante.

> [!NOTE]
> Un troisième type de collection est utilisé avec le <xref:System.Windows.Documents.ListItemCollection>contenu dynamique, mais cette collection est utilisée uniquement avec un. <xref:System.Windows.Documents.List> En outre, plusieurs collections sont utilisées avec <xref:System.Windows.Documents.Table>. Pour plus d’informations, consultez [vue d’ensemble des tables](table-overview.md) .

<a name="content_schema"></a>

## <a name="content-schema"></a>Schéma du contenu

Étant donné le nombre d’éléments de contenu dynamique, il est parfois difficile de savoir quel type d’éléments enfants peut être contenu dans un élément. Le diagramme suivant récapitule les règles relatives à la relation contenant-contenu pour les éléments de contenu dynamique. Les flèches représentent les relations parent/enfant possibles.

![Schémas Schéma]de relation contenant-contenu Flow(./media/flow-content-schema.png "Flow_Content_Schema")

Comme vous pouvez le voir dans le diagramme ci-dessus, les enfants autorisés pour un élément ne sont pas nécessairement déterminés par <xref:System.Windows.Documents.Block> le fait qu' <xref:System.Windows.Documents.Inline> il s’agisse d’un élément ou d’un élément. Par exemple, un <xref:System.Windows.Documents.Span> (un <xref:System.Windows.Documents.Inline> élément) ne peut avoir <xref:System.Windows.Documents.Inline> que des éléments enfants <xref:System.Windows.Documents.Figure> tandis qu' <xref:System.Windows.Documents.Inline> un (également un élément <xref:System.Windows.Documents.Block> ) ne peut avoir que des éléments enfants. Un diagramme est donc utile pour déterminer rapidement quel élément peut être contenu dans un autre. Par exemple, utilisons le diagramme pour déterminer comment construire le contenu dynamique d’un <xref:System.Windows.Controls.RichTextBox>.

**1.** Un <xref:System.Windows.Controls.RichTextBox> doit contenir un <xref:System.Windows.Documents.FlowDocument> qui doit à son tour contenir <xref:System.Windows.Documents.Block>un objet dérivé de. Voici le segment correspondant extrait du diagramme ci-dessus.

![Schémas Règles]de relation contenant-contenu RichTextBox(./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")

À ce stade, le balisage peut ressembler à ceci.

[!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]

**2.** D’après le diagramme, vous avez le <xref:System.Windows.Documents.Block> choix <xref:System.Windows.Documents.Paragraph>entre <xref:System.Windows.Documents.List> <xref:System.Windows.Documents.Section> <xref:System.Windows.Documents.Table>plusieurs éléments,,,, et <xref:System.Windows.Documents.BlockUIContainer> (voir les classes dérivées de Block ci-dessus). Supposons que nous voulons un <xref:System.Windows.Documents.Table>. D’après le diagramme ci-dessus <xref:System.Windows.Documents.Table> , un <xref:System.Windows.Documents.TableRowGroup> contient <xref:System.Windows.Documents.TableRow> un élément contenant des <xref:System.Windows.Documents.TableCell> éléments qui contiennent des <xref:System.Windows.Documents.Block>éléments qui contiennent un objet dérivé de. Voici le segment <xref:System.Windows.Documents.Table> correspondant pris dans le diagramme ci-dessus.

![Schémas Schéma&#47;enfant parent pour la]table(./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")

Le balisage correspondant est indiqué ci-dessous.

[!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]

**3.** Là encore, un ou <xref:System.Windows.Documents.Block> plusieurs éléments sont requis sous <xref:System.Windows.Documents.TableCell>un. Pour simplifier, insérons du texte dans la cellule. Nous pouvons le faire à l' <xref:System.Windows.Documents.Paragraph> aide d' <xref:System.Windows.Documents.Run> un avec un élément. Voici les segments correspondants du <xref:System.Windows.Documents.Paragraph> diagramme montrant qu’un peut accepter un <xref:System.Windows.Documents.Inline> élément et qu’un <xref:System.Windows.Documents.Run> (un <xref:System.Windows.Documents.Inline> élément) ne peut prendre que du texte brut.

![Schémas Schéma&#47;enfant parent pour le]paragraphe(./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")

![Schémas Schéma&#47;enfant parent pour Run](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")

Le balisage de l’exemple complet est indiqué ci-dessous.

[!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]

<a name="customizing_text"></a>

## <a name="customizing-text"></a>Personnalisation du texte

Généralement, le texte est le type de contenu le plus fréquent dans un document dynamique. Même si les objets décrits ci-dessus permettent de contrôler la plupart des aspects concernant la restitution du texte, il existe d’autres méthodes, décrites dans cette section, destinées à personnaliser le texte.

### <a name="text-decorations"></a>Ornements de texte

Les ornements de texte vous permettent d’appliquer au texte les effets suivants : souligné, ligne au-dessus, ligne de base et barré (consultez les images ci-dessous). Ces décorations sont ajoutées à l' <xref:System.Windows.Documents.Inline.TextDecorations%2A> aide de la propriété qui est exposée par plusieurs <xref:System.Windows.Documents.Inline>objets, <xref:System.Windows.Controls.TextBlock>notamment, <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Documents.Paragraph>, et.

L'exemple suivant montre comment définir la propriété <xref:System.Windows.Documents.Paragraph.TextDecorations%2A> d'un <xref:System.Windows.Documents.Paragraph>.

[!code-xaml[InlineSnippets#_Paragraph_TextDecXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml#_paragraph_textdecxaml)]

[!code-csharp[InlineSnippets#_Paragraph_TextDec](~/samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml.cs#_paragraph_textdec)]
[!code-vb[InlineSnippets#_Paragraph_TextDec](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InlineSnippets/visualbasic/window1.xaml.vb#_paragraph_textdec)]

La figure suivante montre le rendu de cet exemple.

![Capture d’écran Texte avec effet]barré par défaut(./media/inline-textdec-strike.png "Inline_TextDec_Strike")

Les figures suivantes illustrent la façon dont **les ornements** de **ligne**et de ligne de **base**sont affichés respectivement.

![Capture d’écran Superline TextDecorator](./media/inline-textdec-over.png "Inline_TextDec_Over")

![Capture d’écran Effet de ligne de base]par défaut sur le texte(./media/inline-textdec-base.png "Inline_TextDec_Base")

![Capture d’écran Texte avec effet]de soulignement par défaut(./media/inline-textdec-under.png "Inline_TextDec_Under")

### <a name="typography"></a>Typographie

La <xref:System.Windows.Documents.TextElement.Typography%2A> propriété est exposée par la plupart des contenus liés <xref:System.Windows.Documents.TextElement>au Flow <xref:System.Windows.Controls.TextBlock>, notamment <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Documents.FlowDocument>, et. Cette propriété est utilisée pour contrôler les caractéristiques/variations typographiques de texte (en d’autres termes, petites ou grandes majuscules, exposants et indices, etc).

L’exemple suivant montre comment définir l' <xref:System.Windows.Documents.TextElement.Typography%2A> attribut à l’aide <xref:System.Windows.Documents.Paragraph> de comme exemple d’élément.

[!code-xaml[TextElementSnippets#_TextElement_TypogXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]

La figure suivante montre le rendu de cet exemple.

![Capture d’écran Texte avec des](./media/textelement-typog.png "TextElement_Typog") de typographie modifiés

Par contraste, l’illustration suivante montre comment s’affiche un exemple similaire avec des propriétés typographiques par défaut.

![Capture d’écran Texte avec des](./media/textelement-typog-default.png "TextElement_Typog_Default") de typographie modifiés

L’exemple suivant montre comment définir la <xref:System.Windows.Controls.TextBox.Typography%2A> propriété par programmation.

[!code-csharp[TextElementSnippets#_TextElement_Typog](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
[!code-vb[TextElementSnippets#_TextElement_Typog](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]

Pour plus d’informations sur la typographie, consultez [typographie dans WPF](typography-in-wpf.md) .

## <a name="see-also"></a>Voir aussi

- [Text](optimizing-performance-text.md)
- [Typographie dans WPF](typography-in-wpf.md)
- [Rubriques de guide pratique](flow-content-elements-how-to-topics.md)
- [Vue d'ensemble du modèle de contenu de TextElement](textelement-content-model-overview.md)
- [Vue d’ensemble de RichTextBox](../controls/richtextbox-overview.md)
- [Documents dans WPF](documents-in-wpf.md)
- [Vue d’ensemble de Table](table-overview.md)
- [Vue d’ensemble des annotations](annotations-overview.md)
