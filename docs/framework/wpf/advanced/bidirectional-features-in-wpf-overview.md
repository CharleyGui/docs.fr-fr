---
title: Vue d'ensemble des fonctionnalités bidirectionnelles dans WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Span elements [WPF]
- bidirectional features [WPF]
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
ms.openlocfilehash: 2a599322ef955b9f702f8960f294f5d093ede74a
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834746"
---
# <a name="bidirectional-features-in-wpf-overview"></a>Vue d'ensemble des fonctionnalités bidirectionnelles dans WPF

Contrairement à toute autre plateforme de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] développement, possède de nombreuses fonctionnalités qui prennent en charge le développement rapide de contenu bidirectionnel, par exemple, les données de gauche à droite et de droite à gauche dans le même document. En même temps, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] crée une excellente expérience pour les utilisateurs qui nécessitent des fonctionnalités bidirectionnelles, telles que les utilisateurs en arabe et en Hébreu.

Les sections suivantes expliquent de nombreuses fonctionnalités bidirectionnelles, accompagnées d’exemples qui illustrent comment réaliser le meilleur affichage de contenu bidirectionnel. La plupart des exemples utilisent [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], bien que vous puissiez facilement appliquer les concepts C# à ou à Microsoft Visual Basic code.

<a name="FlowDirection"></a>

## <a name="flowdirection"></a>FlowDirection

La propriété de base qui définit le sens du déroulement du [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu dans <xref:System.Windows.FrameworkElement.FlowDirection%2A>une application est. Cette propriété peut être définie sur l’une des deux valeurs d' <xref:System.Windows.FlowDirection.LeftToRight> énumération, ou <xref:System.Windows.FlowDirection.RightToLeft>. La propriété est disponible pour tous [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] les éléments qui héritent de. <xref:System.Windows.FrameworkElement>

Les exemples suivants définissent le sens du <xref:System.Windows.Controls.TextBox> déroulement d’un élément.

**Sens de déroulement de gauche à droite**

[!code-xaml[LTRRTL#LTR](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]

**Sens de déroulement de droite à gauche**

[!code-xaml[LTRRTL#RTL](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]

Le graphique suivant montre le rendu généré par le code précédent.

![Graphique illustrant les différentes directions de Flow.](./media/bidirectional-features-in-wpf-overview/left-right-right-left.png)

Un élément dans une [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] arborescence <xref:System.Windows.FrameworkElement.FlowDirection%2A> hérite de de son conteneur. Dans l’exemple suivant, le <xref:System.Windows.Controls.TextBlock> est à l' <xref:System.Windows.Controls.Grid>intérieur d’un, qui réside dans <xref:System.Windows.Window>un. La définition <xref:System.Windows.Window> <xref:System.Windows.Controls.Grid> de pour le implique de le définir pour <xref:System.Windows.Controls.TextBlock>et. <xref:System.Windows.FrameworkElement.FlowDirection%2A>

L’exemple suivant illustre le <xref:System.Windows.FrameworkElement.FlowDirection%2A>paramétrage de.

[!code-xaml[FlowDirection#FlowDirection](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]

Le niveau <xref:System.Windows.Window> supérieur a un <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection>, donc tous les éléments qu’il contient héritent également <xref:System.Windows.FrameworkElement.FlowDirection%2A>du même. Pour qu’un élément substitue un spécifié <xref:System.Windows.FrameworkElement.FlowDirection%2A> , il doit ajouter une modification de direction explicite, telle <xref:System.Windows.Controls.TextBlock> que la seconde dans l’exemple <xref:System.Windows.FlowDirection.LeftToRight>précédent, qui devient. Si aucun <xref:System.Windows.FrameworkElement.FlowDirection%2A> n’est défini, la <xref:System.Windows.FlowDirection.LeftToRight> valeur par défaut s’applique.

Le graphique suivant montre la sortie de l’exemple précédent :

![Graphique illustrant le changement de sens du déroulement explicite.](./media/bidirectional-features-in-wpf-overview/explicit-direction-change.png)

<a name="FlowDocument"></a>

## <a name="flowdocument"></a>FlowDocument

De nombreuses plateformes de développement, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] telles que HTML et Java, fournissent une prise en charge spéciale pour le développement de contenu bidirectionnel. Les langages de balisage tels que HTML donnent aux rédacteurs de contenu le balisage nécessaire pour afficher du texte dans n’importe quel sens requis, par exemple la balise HTML 4,0, « dir » qui prend « RTL » ou « LTR » comme valeurs. Cette balise est similaire à <xref:System.Windows.FrameworkElement.FlowDirection%2A> la propriété, mais <xref:System.Windows.FrameworkElement.FlowDirection%2A> la propriété fonctionne de manière plus avancée pour mettre en page le contenu textuel et peut être utilisée pour du contenu autre que du texte.

Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], un <xref:System.Windows.Documents.FlowDocument> est un élément [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] polyvalent qui peut héberger une combinaison de texte, de tables, d’images et d’autres éléments. Les exemples des sections suivantes utilisent cet élément.

L’ajout de texte <xref:System.Windows.Documents.FlowDocument> à un peut être effectué de plusieurs façons. Un moyen simple de le faire consiste à utiliser <xref:System.Windows.Documents.Paragraph> un qui est un élément de niveau bloc utilisé pour regrouper du contenu tel que du texte. Pour ajouter du texte aux éléments inclus au niveau de la ligne <xref:System.Windows.Documents.Span> , <xref:System.Windows.Documents.Run>les exemples utilisent et. <xref:System.Windows.Documents.Span>est un élément de contenu de workflow au niveau de la ligne utilisé pour regrouper d’autres éléments <xref:System.Windows.Documents.Run> Inline, tandis qu’un est un élément de contenu de workflow de niveau Inline destiné à contenir une exécution de texte non mis en forme. Un <xref:System.Windows.Documents.Span> peut contenir plusieurs <xref:System.Windows.Documents.Run> éléments.

Le premier exemple de document contient un document qui a plusieurs noms de partage réseau ; par exemple `\\server1\folder\file.ext`,. Que ce lien réseau soit dans un document en arabe ou en anglais, vous souhaiterez toujours qu’il apparaisse de la même façon. Le graphique suivant illustre l’utilisation de l’élément span et montre le lien dans un <xref:System.Windows.FlowDirection.RightToLeft> document en arabe :

![Graphique illustrant l’utilisation de l’élément span.](./media/bidirectional-features-in-wpf-overview/flow-direction-span-element.png "FlowDocument")

Étant donné que le <xref:System.Windows.FlowDirection.RightToLeft>texte est, tous les caractères spéciaux, tels\\que «», séparent le texte dans l’ordre de droite à gauche. Cela a pour effet que le lien n’est pas affiché dans le bon ordre <xref:System.Windows.Documents.Run> <xref:System.Windows.FlowDirection.LeftToRight>. par conséquent, pour résoudre le problème, le texte doit être incorporé pour conserver un déplacement distinct. Au lieu d’avoir un <xref:System.Windows.Documents.Run> distinct pour chaque langue, un meilleur moyen de résoudre le problème consiste à incorporer le texte en anglais le moins fréquemment utilisé <xref:System.Windows.Documents.Span>dans un arabe plus grand.

Le graphique suivant illustre cela à l’aide de l’élément Run incorporé dans un élément span :

![Graphique illustrant l’élément Run incorporé dans un élément span.](./media/bidirectional-features-in-wpf-overview/embedded-span-element.png)

L’exemple suivant illustre l' <xref:System.Windows.Documents.Run> utilisation <xref:System.Windows.Documents.Span> d’éléments et dans des documents.

[!code-xaml[RunSpan#RunSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]

<a name="SpanElements"></a>

## <a name="span-elements"></a>Éléments Span

L' <xref:System.Windows.Documents.Span> élément fonctionne comme un séparateur de limites entre les textes avec des directions de Flow différentes.  Même <xref:System.Windows.Documents.Span> les éléments ayant le même sens de déroulement sont considérés comme ayant des portées bidirectionnelles différentes <xref:System.Windows.Documents.Span> , ce qui signifie que les éléments <xref:System.Windows.FlowDirection>sont ordonnés dans le du <xref:System.Windows.Documents.Span> conteneur, uniquement le contenu de l’élément suit le <xref:System.Windows.FlowDirection> <xref:System.Windows.Documents.Span>de.

Le graphique suivant montre le sens du déroulement de <xref:System.Windows.Controls.TextBlock> plusieurs éléments.

![Graphique illustrant des blocs de texte avec différents sens de déroulement.](./media/bidirectional-features-in-wpf-overview/flow-direction-text-blocks.png)

L’exemple suivant montre comment utiliser les <xref:System.Windows.Documents.Span> éléments et <xref:System.Windows.Documents.Run> pour produire les résultats affichés dans le graphique précédent.

[!code-xaml[Span#Span](~/samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]

Dans les <xref:System.Windows.Controls.TextBlock> éléments de l’exemple, les <xref:System.Windows.Documents.Span> éléments sont disposés en fonction du <xref:System.Windows.FlowDirection> de leurs parents, mais le texte dans chaque <xref:System.Windows.Documents.Span> élément est transmis en fonction de son <xref:System.Windows.FlowDirection>propre élément. Ceci s’applique au latin et à l’arabe ou à toute autre langue.

### <a name="adding-xmllang"></a>Ajout de xml:lang

Le graphique suivant montre un autre exemple qui utilise des nombres et des expressions arithmétiques, tels que `"200.0+21.4=221.4"`. Notez que seul <xref:System.Windows.FlowDirection> est défini.

![Graphique qui affiche les nombres en utilisant uniquement FlowDirection.](./media/bidirectional-features-in-wpf-overview/numbers-flow-right-left.png)

Les utilisateurs de cette application seront déçus par la sortie, même si <xref:System.Windows.FlowDirection> le est correct, les nombres ne sont pas mis en forme, car les nombres arabes doivent être mis en forme.

Les éléments XAML peuvent inclure [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] un attribut`xml:lang`() qui définit le langage de chaque élément. XAML prend également en [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] charge un principe `xml:lang` de langage selon lequel les valeurs appliquées aux éléments parents dans l’arborescence sont utilisées par les éléments enfants. Dans l’exemple précédent, comme un langage n’a pas été défini <xref:System.Windows.Documents.Run> pour l’élément ou l’un de ses éléments de niveau `xml:lang` supérieur, la valeur par `en-US` défaut a été utilisée, qui est pour XAML. L’algorithme de mise en [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] forme des nombres internes de sélectionne des nombres dans la langue correspondante, dans ce cas l’anglais. Pour que les chiffres arabes s’affichent correctement `xml:lang` , la valeur doit être définie.

Le graphique suivant montre l’exemple avec `xml:lang` ajouté.

![Graphique illustrant les nombres arabes qui s’ensuivent de droite à gauche.](./media/bidirectional-features-in-wpf-overview/arabic-numbers-flow-right-left.png)

L’exemple suivant ajoute `xml:lang` à l’application.

[!code-xaml[LangAttribute#LangAttribute](~/samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]

Sachez que de nombreuses langues ont `xml:lang` des valeurs différentes en fonction de la région ciblée, `"ar-SA"` par `"ar-EG"` exemple, et représentent deux variantes de l’arabe. Les exemples précédents montrent que vous devez définir `xml:lang` les valeurs et. <xref:System.Windows.FlowDirection>

<a name="FlowDirectionNontext"></a>

## <a name="flowdirection-with-non-text-elements"></a>FlowDirection avec des éléments autres que textuels

<xref:System.Windows.FlowDirection>définit non seulement la façon dont le texte est transmis dans un élément textuel, mais également le sens [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] du flux de presque tous les autres éléments. Le graphique suivant montre un <xref:System.Windows.Controls.ToolBar> qui utilise un horizontal <xref:System.Windows.Media.LinearGradientBrush> pour dessiner son arrière-plan avec un dégradé de gauche à droite.

![Graphique qui affiche une barre d’outils avec un dégradé de gauche à droite.](./media/bidirectional-features-in-wpf-overview/toolbar-left-right-gradient.png)

Après avoir défini <xref:System.Windows.FlowDirection> la <xref:System.Windows.FlowDirection.RightToLeft>valeur sur, <xref:System.Windows.Controls.ToolBar> les boutons sont disposés de droite à gauche, mais même le <xref:System.Windows.Media.LinearGradientBrush> réaligne ses décalages de droite à gauche.

Le graphique suivant montre le réalignement du <xref:System.Windows.Media.LinearGradientBrush>.

![Graphique qui affiche une barre d’outils avec un dégradé de droite à gauche.](./media/bidirectional-features-in-wpf-overview/toolbar-right-left-gradient.png)

L’exemple suivant dessine <xref:System.Windows.FlowDirection.RightToLeft>un <xref:System.Windows.Controls.ToolBar>. (Pour le dessiner de gauche à droite, supprimez l' <xref:System.Windows.FlowDirection> attribut sur le. <xref:System.Windows.Controls.ToolBar>

[!code-xaml[Gradient#Gradient](~/samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]

<a name="FlowDirectionExceptions"></a>

### <a name="flowdirection-exceptions"></a>Exceptions de FlowDirection

Il existe quelques cas où <xref:System.Windows.FlowDirection> ne se comporte pas comme prévu. Cette section décrit deux de ces exceptions.

**Image**

Un <xref:System.Windows.Controls.Image> représente un contrôle qui affiche une image. Dans [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] , il peut être utilisé avec <xref:System.Windows.Controls.Image.Source%2A> une propriété <xref:System.Windows.Controls.Image> qui définit [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] le du à afficher.

Contrairement <xref:System.Windows.FlowDirection> à [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] d’autres éléments <xref:System.Windows.Controls.Image> , un n’hérite pas de à partir du conteneur. Toutefois, si <xref:System.Windows.FlowDirection> est défini explicitement sur <xref:System.Windows.FlowDirection.RightToLeft>, un <xref:System.Windows.Controls.Image> est affiché retourné horizontalement. Cette implémentation est une fonctionnalité pratique pour les développeurs de contenu bidirectionnel, car dans certains cas, le fait de retourner l’image horizontalement produit l’effet recherché.

Le graphique suivant montre un retourné <xref:System.Windows.Controls.Image>.

![Graphique illustrant une image retournée.](./media/bidirectional-features-in-wpf-overview/flipped-image-example.png)

L’exemple suivant montre que <xref:System.Windows.Controls.Image> ne peut pas <xref:System.Windows.FlowDirection> hériter de l <xref:System.Windows.Controls.StackPanel> 'de la qui le contient.

> [!NOTE]
> Vous devez avoir un fichier nommé **ms_logo. jpg** sur votre pour exécuter cet exemple.

[!code-xaml[Image#Image](~/samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]

> [!NOTE]
> Les fichiers téléchargés sont inclus dans un fichier **ms_logo. jpg** . Le code suppose que le fichier .jpg n’est pas à l’intérieur de votre projet mais quelque part sur le lecteur C:\. Vous devez copier le fichier .jpg depuis les fichiers de projet vers votre lecteur C:\ ou modifier le code pour qu’il recherche le fichier à l’intérieur du projet. Pour ce faire, `Source="file://c:/ms_logo.jpg"` remplacez `Source="ms_logo.jpg"`par.

**Tracés**

En plus d’un <xref:System.Windows.Controls.Image>, un autre élément intéressant <xref:System.Windows.Shapes.Path>est. Un tracé est un objet qui peut dessiner une série de lignes et de courbes reliées. Il se comporte de manière similaire à <xref:System.Windows.Controls.Image> un en ce qui concerne son <xref:System.Windows.FlowDirection>; par exemple <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> , il s’agit d’un <xref:System.Windows.FlowDirection.LeftToRight> miroir horizontal de celui-ci. Toutefois, à la <xref:System.Windows.Controls.Image>différence <xref:System.Windows.Shapes.Path> d’un, <xref:System.Windows.FlowDirection> hérite de son du conteneur et il n’est pas nécessaire de le spécifier explicitement.

L’exemple suivant dessine une flèche simple à l’aide de 3 lignes. La première flèche hérite <xref:System.Windows.FlowDirection.RightToLeft> du sens <xref:System.Windows.Controls.StackPanel> du déroulement du afin que ses points de début et de fin soient mesurés à partir d’une racine sur le côté droit. La deuxième flèche qui a un explicite <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> démarre également sur le côté droit. Cependant, la troisième flèche a sa racine de début située sur le côté gauche. Pour plus d’informations sur le <xref:System.Windows.Media.LineGeometry> dessin <xref:System.Windows.Media.GeometryGroup>, consultez et.

[!code-xaml[Paths#Paths](~/samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]

Le graphique suivant montre la sortie de l’exemple précédent avec des flèches dessinées `Path` à l’aide de l’élément :

![Graphique illustrant les flèches dessinées à l’aide de l’élément Path.](./media/bidirectional-features-in-wpf-overview/arrows-drawn-path-element.png)

Les <xref:System.Windows.Controls.Image> méthodes <xref:System.Windows.Shapes.Path> <xref:System.Windows.FlowDirection>et sont deux exemples d’utilisation de. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] En regard de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] la disposition des éléments dans une direction spécifique au <xref:System.Windows.FlowDirection> sein d’un conteneur, peut être <xref:System.Windows.Controls.InkPresenter> utilisé avec des éléments tels que qui restituent <xref:System.Windows.Media.RadialGradientBrush>l’encre sur une surface, <xref:System.Windows.Media.LinearGradientBrush>,. Chaque fois que vous avez besoin d’un comportement de droite à gauche pour votre contenu qui imite le comportement de gauche à droite [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] , ou vice versa, fournit cette fonctionnalité.

<a name="NumberSubstitution"></a>

## <a name="number-substitution"></a>Substitution de nombres

Historiquement, Windows prend en charge la substitution de nombres en autorisant la représentation de différentes formes culturelles pour les mêmes chiffres tout en conservant le stockage interne de ces chiffres unifié parmi les différents paramètres régionaux, par exemple les nombres sont stockés dans leur valeurs hexadécimales bien connues, 0x40, 0x41 vers, mais affichées en fonction de la langue sélectionnée.

Cela a permis aux applications de traiter des valeurs numériques sans avoir besoin de les convertir d’une langue à une autre, par exemple, un [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)] utilisateur peut ouvrir une feuille de calcul dans une fenêtre arabe localisée et afficher les nombres en arabe, mais l’ouvrir dans un Version européenne de Windows et consultez la représentation européenne des mêmes nombres. Ceci est également nécessaire pour les autres symboles tels que les virgules et le symbole du pourcentage, car ils accompagnent habituellement des nombres dans le même document.

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] continue dans la même tradition et ajoute une prise en charge supplémentaire de cette fonctionnalité qui permet un meilleur contrôle de l’utilisateur sur quand et comment la substitution est utilisée. Bien que cette fonctionnalité soit conçue pour n’importe quelle langue, elle est particulièrement utile pour du contenu bidirectionnel, où la mise en forme des chiffres pour une langue spécifique est habituellement un défi pour les développeurs d’application du fait des différentes cultures dans lesquelles peut s’exécuter l’application.

La propriété de base contrôlant le fonctionnement de la [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] substitution de <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> nombres dans est la propriété de dépendance. La <xref:System.Windows.Media.NumberSubstitution> classe spécifie le mode d’affichage des nombres dans le texte. Elle a trois propriétés publiques qui définissent son comportement. Voici un résumé de chacune des propriétés :

**CultureSource :**

Cette propriété spécifie la manière dont est déterminée la culture pour les nombres. Elle prend l’une des <xref:System.Windows.Media.NumberCultureSource> trois valeurs d’énumération.

- Remplacer La culture des nombres est <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> celle de la propriété.

- financière La culture des nombres est la culture de la séquence de texte. Dans le balisage, il `xml:lang`s’agit de, `Language` ou de sa <xref:System.Windows.FrameworkContentElement.Language%2A>propriété alias (<xref:System.Windows.FrameworkElement.Language%2A> ou). Par ailleurs, il s’agit de la valeur par défaut <xref:System.Windows.FrameworkContentElement>pour les classes qui dérivent de. Ces classes incluent <xref:System.Windows.Documents.Paragraph?displayProperty=nameWithType>, <xref:System.Windows.Documents.Table?displayProperty=nameWithType>, <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType> et ainsi de suite.

- Utilisateur : La culture des nombres est la culture du thread actuel. Cette propriété est la valeur par défaut pour toutes les sous <xref:System.Windows.FrameworkElement> -classes <xref:System.Windows.Controls.Page>de <xref:System.Windows.Window> telles <xref:System.Windows.Controls.TextBlock>que et.

**CultureOverride** :

La <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> propriété est utilisée uniquement si la <xref:System.Windows.Media.NumberSubstitution.CultureSource%2A> propriété a la valeur <xref:System.Windows.Media.NumberCultureSource.Override> et est ignorée dans le cas contraire. Elle spécifie la culture pour les nombres. La valeur `null`, la valeur par défaut, est interprétée comme en-US.

**Substitution** :

Cette propriété spécifie le type de substitution de nombres à effectuer. Elle prend l’une des valeurs <xref:System.Windows.Media.NumberSubstitutionMethod> d’énumération suivantes :

- <xref:System.Windows.Media.NumberSubstitutionMethod.AsCulture>: La méthode de substitution est déterminée en fonction de la propriété de <xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=nameWithType> la culture des nombres. Il s'agit de la valeur par défaut.

- <xref:System.Windows.Media.NumberSubstitutionMethod.Context>: Si la culture du nombre est une culture arabe ou persan, elle spécifie que les chiffres dépendent du contexte.

- <xref:System.Windows.Media.NumberSubstitutionMethod.European>: Les nombres sont toujours rendus sous la forme de chiffres européens.

- <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>: Les nombres sont restitués à l’aide des chiffres nationaux pour la culture des nombres, comme <xref:System.Globalization.CultureInfo.NumberFormat%2A>spécifié par le de la culture.

- <xref:System.Windows.Media.NumberSubstitutionMethod.Traditional>: Les nombres sont rendus à l’aide des chiffres traditionnels pour la culture des nombres. Pour la plupart des cultures, il s’agit <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>de la même chose que. Toutefois, <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational> génère des chiffres latins pour certaines cultures arabes, alors que cette valeur génère des chiffres arabes pour toutes les cultures arabes.

Que signifient ces valeurs pour un développeur de contenu bidirectionnel ? Dans la plupart des cas, le développeur peut avoir besoin <xref:System.Windows.FlowDirection> uniquement de définir et la langue [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de chaque élément textuel `Language="ar-SA"` , par <xref:System.Windows.Media.NumberSubstitution> exemple, et la logique s’occupe de l’affichage des [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]nombres en fonction du correct. L’exemple suivant illustre l’utilisation des nombres arabes et anglais [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] dans une application exécutée dans une version arabe de Windows.

[!code-xaml[Numbers#Numbers](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]

L’illustration suivante montre la sortie de l’exemple précédent si vous exécutez dans une version arabe de Windows avec des nombres arabes et anglais affichés :

![Graphique qui affiche les nombres arabes et anglais.](./media/bidirectional-features-in-wpf-overview/arabic-english-numbers.png)

Le <xref:System.Windows.FlowDirection> a été important dans ce cas, car <xref:System.Windows.FlowDirection> la <xref:System.Windows.FlowDirection.LeftToRight> définition du à à la place aurait généré des chiffres européens. Les sections suivantes expliquent comment obtenir un affichage unifié des chiffres dans l’ensemble de votre document. Si cet exemple ne s’exécute pas sur une version arabe de Windows, tous les chiffres sont affichés en tant que chiffres européens.

**Définition des règles de substitution**

Dans une application réelle, il est possible que vous ayez besoin de définir la langue par programmation. Par exemple, vous souhaitez définir l' `xml:lang` attribut pour qu’il soit identique à celui utilisé par le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]système, ou peut-être modifier la langue en fonction de l’état de l’application.

Si vous souhaitez apporter des modifications en fonction de l’état de l’application, utilisez d’autres fonctionnalités fournies [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]par.

Tout d’abord, définissez le composant `NumberSubstitution.CultureSource="Text"`de l’application. L’utilisation de ce paramètre permet de s’assurer que les paramètres ne [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] proviennent pas du pour les éléments de texte qui ont « User » comme <xref:System.Windows.Controls.TextBlock>valeur par défaut, par exemple.

Exemple :

```xaml
<TextBlock
   Name="text1" NumberSubstitution.CultureSource="Text">
   1234+5679=6913
</TextBlock>
```

Dans le code C# correspondant, affectez `Language` à `"ar-SA"`la propriété, par exemple, la valeur.

```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");
```

Si vous devez définir la `Language` propriété sur la langue de l’interface utilisateur actuelle, utilisez le code suivant.

```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage(System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);
```

<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>représente la culture actuelle utilisée par le thread actuel au moment de l’exécution.

Votre exemple [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] final doit ressembler à l’exemple suivant.

[!code-xaml[Numbers2#Numbers2](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]

Votre exemple C# final doit ressembler à ce qui suit.

[!code-csharp[NumbersCSharp#NumbersCSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]

L’illustration suivante montre à quoi ressemble la fenêtre pour le langage de programmation et l’affichage des nombres arabes :

![Graphique qui affiche les nombres arabes.](./media/bidirectional-features-in-wpf-overview/displays-arabic-numbers.png)

**Utilisation de la propriété Substitution**

La manière dont fonctionne la substitution des [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nombres dans dépend de la langue de l’élément de texte <xref:System.Windows.FlowDirection>et de son. Si est <xref:System.Windows.FlowDirection> de gauche à droite, les chiffres européens sont rendus. Toutefois, si elle est précédée d’un texte en arabe ou si la langue est définie sur « <xref:System.Windows.FlowDirection> AR <xref:System.Windows.FlowDirection.RightToLeft>» et que est, les chiffres arabes sont rendus à la place.

Toutefois, dans certains cas, il se peut que vous souhaitiez créer une application unifiée, avec par exemple des chiffres européens pour tous les utilisateurs. Ou des chiffres arabes <xref:System.Windows.Documents.Table> dans les cellules avec <xref:System.Windows.Style>un spécifique. Pour ce faire, une méthode simple consiste à <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> utiliser la propriété.

Dans l’exemple suivant, la première <xref:System.Windows.Controls.TextBlock> n’a pas la <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> propriété définie, de sorte que l’algorithme affiche les chiffres arabes comme prévu. Toutefois, dans la <xref:System.Windows.Controls.TextBlock>seconde, la substitution est définie sur le remplacement de la substitution par défaut pour les nombres arabes, et les chiffres européens sont affichés.

[!code-xaml[Numbers3#Numbers3](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]
