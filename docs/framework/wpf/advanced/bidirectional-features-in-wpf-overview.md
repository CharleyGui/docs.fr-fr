---
title: Vue d’ensemble des fonctionnalités bidirectionnelles
ms.date: 03/30/2017
helpviewer_keywords:
- Span elements [WPF]
- bidirectional features [WPF]
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
ms.openlocfilehash: 17167b1afa5037998d9ea8ed679a66c89babe242
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741630"
---
# <a name="bidirectional-features-in-wpf-overview"></a>Vue d'ensemble des fonctionnalités bidirectionnelles dans WPF

Contrairement à toute autre plateforme de développement, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] possède de nombreuses fonctionnalités qui prennent en charge le développement rapide de contenu bidirectionnel, par exemple, des données mixtes de gauche à droite et de droite à gauche dans le même document. En même temps, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] crée une excellente expérience pour les utilisateurs qui nécessitent des fonctionnalités bidirectionnelles, telles que les utilisateurs en arabe et en Hébreu.

Les sections suivantes expliquent de nombreuses fonctionnalités bidirectionnelles, accompagnées d’exemples qui illustrent comment réaliser le meilleur affichage de contenu bidirectionnel. La plupart des exemples utilisent XAML, bien que vous puissiez facilement appliquer les concepts C# à ou à Microsoft Visual Basic code.

<a name="FlowDirection"></a>

## <a name="flowdirection"></a>FlowDirection

La propriété de base qui définit le sens du déroulement du contenu dans une [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application est <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Cette propriété peut être définie sur l’une des deux valeurs d’énumération, <xref:System.Windows.FlowDirection.LeftToRight> ou <xref:System.Windows.FlowDirection.RightToLeft>. La propriété est disponible pour tous les éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui héritent de <xref:System.Windows.FrameworkElement>.

Les exemples suivants définissent le sens du déroulement d’un élément <xref:System.Windows.Controls.TextBox>.

**Sens de déroulement de gauche à droite**

[!code-xaml[LTRRTL#LTR](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]

**Sens de déroulement de droite à gauche**

[!code-xaml[LTRRTL#RTL](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]

Le graphique suivant montre le rendu généré par le code précédent.

![Graphique illustrant les différentes directions de Flow.](./media/bidirectional-features-in-wpf-overview/left-right-right-left.png)

Un élément dans une arborescence [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] hérite de la <xref:System.Windows.FrameworkElement.FlowDirection%2A> de son conteneur. Dans l’exemple suivant, le <xref:System.Windows.Controls.TextBlock> se trouve à l’intérieur d’un <xref:System.Windows.Controls.Grid>, qui réside dans un <xref:System.Windows.Window>. La définition de la <xref:System.Windows.FrameworkElement.FlowDirection%2A> pour le <xref:System.Windows.Window> implique de la définir pour le <xref:System.Windows.Controls.Grid> et le <xref:System.Windows.Controls.TextBlock> également.

L’exemple suivant illustre la définition de <xref:System.Windows.FrameworkElement.FlowDirection%2A>.

[!code-xaml[FlowDirection#FlowDirection](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]

Le <xref:System.Windows.Window> de niveau supérieur a un <xref:System.Windows.FlowDirection><xref:System.Windows.FlowDirection.RightToLeft>, donc tous les éléments qu’il contient héritent également du même <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Pour qu’un élément substitue un <xref:System.Windows.FrameworkElement.FlowDirection%2A> spécifié, il doit ajouter une modification de direction explicite, telle que la deuxième <xref:System.Windows.Controls.TextBlock> de l’exemple précédent, qui devient <xref:System.Windows.FlowDirection.LeftToRight>. Quand aucun <xref:System.Windows.FrameworkElement.FlowDirection%2A> n’est défini, le <xref:System.Windows.FlowDirection.LeftToRight> par défaut s’applique.

Le graphique suivant montre la sortie de l’exemple précédent :

![Graphique illustrant le changement de sens du déroulement explicite.](./media/bidirectional-features-in-wpf-overview/explicit-direction-change.png)

<a name="FlowDocument"></a>

## <a name="flowdocument"></a>FlowDocument

De nombreuses plateformes de développement, telles que HTML, Win32 et Java, fournissent une prise en charge spéciale pour le développement de contenu bidirectionnel. Les langages de balisage tels que HTML donnent aux rédacteurs de contenu le balisage nécessaire pour afficher du texte dans n’importe quel sens requis, par exemple la balise HTML 4,0, « dir » qui prend « RTL » ou « LTR » comme valeurs. Cette balise est similaire à la propriété <xref:System.Windows.FrameworkElement.FlowDirection%2A>, mais la propriété <xref:System.Windows.FrameworkElement.FlowDirection%2A> fonctionne de manière plus avancée pour mettre en page du contenu textuel et peut être utilisée pour du contenu autre que du texte.

Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], un <xref:System.Windows.Documents.FlowDocument> est un élément [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] polyvalent qui peut héberger une combinaison de texte, de tables, d’images et d’autres éléments. Les exemples des sections suivantes utilisent cet élément.

L’ajout de texte à un <xref:System.Windows.Documents.FlowDocument> peut être effectué de plusieurs façons. Un moyen simple de le faire consiste à utiliser un <xref:System.Windows.Documents.Paragraph> qui est un élément de niveau bloc utilisé pour regrouper du contenu tel que du texte. Pour ajouter du texte aux éléments inclus au niveau de la ligne, les exemples utilisent <xref:System.Windows.Documents.Span> et <xref:System.Windows.Documents.Run>. <xref:System.Windows.Documents.Span> est un élément de contenu de workflow au niveau de la ligne utilisé pour regrouper d’autres éléments Inline, tandis qu’un <xref:System.Windows.Documents.Run> est un élément de contenu de workflow au niveau de la ligne destiné à contenir une exécution de texte non mis en forme. Un <xref:System.Windows.Documents.Span> peut contenir plusieurs éléments <xref:System.Windows.Documents.Run>.

Le premier exemple de document contient un document qui a plusieurs noms de partage réseau ; par exemple `\\server1\folder\file.ext`. Que ce lien réseau soit dans un document en arabe ou en anglais, vous souhaiterez toujours qu’il apparaisse de la même façon. Le graphique suivant illustre l’utilisation de l’élément span et montre le lien dans un document <xref:System.Windows.FlowDirection.RightToLeft> arabe :

![Graphique illustrant l’utilisation de l’élément span.](./media/bidirectional-features-in-wpf-overview/flow-direction-span-element.png "FlowDocument")

Étant donné que le texte est <xref:System.Windows.FlowDirection.RightToLeft>, tous les caractères spéciaux, tels que «\\», séparent le texte dans l’ordre de droite à gauche. En conséquence, le lien n’est pas affiché dans le bon ordre. par conséquent, pour résoudre le problème, le texte doit être incorporé pour conserver un <xref:System.Windows.FlowDirection.LeftToRight>de <xref:System.Windows.Documents.Run> fluide distinct. Au lieu d’avoir une <xref:System.Windows.Documents.Run> distincte pour chaque langue, un meilleur moyen de résoudre le problème consiste à incorporer le texte en anglais le moins fréquemment utilisé dans une <xref:System.Windows.Documents.Span>arabe plus grande.

Le graphique suivant illustre cela à l’aide de l’élément Run incorporé dans un élément span :

![Graphique illustrant l’élément Run incorporé dans un élément span.](./media/bidirectional-features-in-wpf-overview/embedded-span-element.png)

L’exemple suivant illustre l’utilisation d’éléments <xref:System.Windows.Documents.Run> et <xref:System.Windows.Documents.Span> dans des documents.

[!code-xaml[RunSpan#RunSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]

<a name="SpanElements"></a>

## <a name="span-elements"></a>Éléments Span

L’élément <xref:System.Windows.Documents.Span> fonctionne comme un séparateur de limites entre les textes avec des directions de Flow différentes.  Même <xref:System.Windows.Documents.Span> éléments ayant le même sens de déroulement sont considérés comme ayant des portées bidirectionnelles différentes, ce qui signifie que les éléments <xref:System.Windows.Documents.Span> sont classés dans le <xref:System.Windows.FlowDirection>du conteneur, seul le contenu de l’élément <xref:System.Windows.Documents.Span> suit le <xref:System.Windows.FlowDirection> de l' <xref:System.Windows.Documents.Span>.

Le graphique suivant montre le sens du déroulement de plusieurs éléments <xref:System.Windows.Controls.TextBlock>.

![Graphique illustrant des blocs de texte avec différents sens de déroulement.](./media/bidirectional-features-in-wpf-overview/flow-direction-text-blocks.png)

L’exemple suivant montre comment utiliser les éléments <xref:System.Windows.Documents.Span> et <xref:System.Windows.Documents.Run> pour produire les résultats affichés dans le graphique précédent.

[!code-xaml[Span#Span](~/samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]

Dans les éléments <xref:System.Windows.Controls.TextBlock> de l’exemple, les éléments <xref:System.Windows.Documents.Span> sont disposés en fonction de la <xref:System.Windows.FlowDirection> de leurs parents, mais le texte contenu dans chaque <xref:System.Windows.Documents.Span> élément est transmis en fonction de sa propre <xref:System.Windows.FlowDirection>. Ceci s’applique au latin et à l’arabe ou à toute autre langue.

### <a name="adding-xmllang"></a>Ajout de xml:lang

Le graphique suivant montre un autre exemple qui utilise des nombres et des expressions arithmétiques, comme `"200.0+21.4=221.4"`. Notez que seul le <xref:System.Windows.FlowDirection> est défini.

![Graphique qui affiche les nombres en utilisant uniquement FlowDirection.](./media/bidirectional-features-in-wpf-overview/numbers-flow-right-left.png)

Les utilisateurs de cette application seront déçus par la sortie, même si le <xref:System.Windows.FlowDirection> est correct, les nombres ne sont pas mis en forme, car les nombres arabes doivent être mis en forme.

Les éléments XAML peuvent inclure un attribut XML (`xml:lang`) qui définit le langage de chaque élément. XAML prend également en charge un principe de langage XML par lequel `xml:lang` valeurs appliquées aux éléments parents dans l’arborescence sont utilisées par les éléments enfants. Dans l’exemple précédent, comme un langage n’a pas été défini pour l’élément <xref:System.Windows.Documents.Run> ou l’un de ses éléments de niveau supérieur, le `xml:lang` par défaut a été utilisé, ce qui est `en-US` pour XAML. L’algorithme de mise en forme des nombres internes de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sélectionne les nombres dans la langue correspondante, dans ce cas l’anglais. Pour que les nombres arabes s’affichent correctement `xml:lang` doit être défini.

Le graphique suivant montre l’exemple avec `xml:lang` ajoutée.

![Graphique illustrant les nombres arabes qui s’ensuivent de droite à gauche.](./media/bidirectional-features-in-wpf-overview/arabic-numbers-flow-right-left.png)

L’exemple suivant ajoute `xml:lang` à l’application.

[!code-xaml[LangAttribute#LangAttribute](~/samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]

Sachez que de nombreuses langues ont des valeurs de `xml:lang` différentes en fonction de la région ciblée, par exemple, `"ar-SA"` et `"ar-EG"` représentent deux variantes de l’arabe. Les exemples précédents montrent que vous devez définir à la fois les valeurs `xml:lang` et <xref:System.Windows.FlowDirection>.

<a name="FlowDirectionNontext"></a>

## <a name="flowdirection-with-non-text-elements"></a>FlowDirection avec des éléments autres que textuels

<xref:System.Windows.FlowDirection> définit non seulement la façon dont le texte est transmis dans un élément textuel, mais également le sens du flux de presque tous les autres éléments [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. L’illustration suivante montre une <xref:System.Windows.Controls.ToolBar> qui utilise un <xref:System.Windows.Media.LinearGradientBrush> horizontal pour dessiner son arrière-plan avec un dégradé de gauche à droite.

![Graphique qui affiche une barre d’outils avec un dégradé de gauche à droite.](./media/bidirectional-features-in-wpf-overview/toolbar-left-right-gradient.png)

Après avoir défini la <xref:System.Windows.FlowDirection> sur <xref:System.Windows.FlowDirection.RightToLeft>, les boutons <xref:System.Windows.Controls.ToolBar> sont disposés de droite à gauche, mais même le <xref:System.Windows.Media.LinearGradientBrush> réaligne ses décalages de droite à gauche.

Le graphique suivant montre le réalignement de la <xref:System.Windows.Media.LinearGradientBrush>.

![Graphique qui affiche une barre d’outils avec un dégradé de droite à gauche.](./media/bidirectional-features-in-wpf-overview/toolbar-right-left-gradient.png)

L’exemple suivant dessine une <xref:System.Windows.Controls.ToolBar><xref:System.Windows.FlowDirection.RightToLeft>. (Pour le dessiner de gauche à droite, supprimez l’attribut <xref:System.Windows.FlowDirection> sur le <xref:System.Windows.Controls.ToolBar>.

[!code-xaml[Gradient#Gradient](~/samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]

<a name="FlowDirectionExceptions"></a>

### <a name="flowdirection-exceptions"></a>Exceptions de FlowDirection

Dans certains cas, <xref:System.Windows.FlowDirection> ne se comporte pas comme prévu. Cette section décrit deux de ces exceptions.

**Image**

Un <xref:System.Windows.Controls.Image> représente un contrôle qui affiche une image. En XAML, il peut être utilisé avec une propriété <xref:System.Windows.Controls.Image.Source%2A> qui définit l’URI (Uniform Resource Identifier) de l' <xref:System.Windows.Controls.Image> à afficher.

Contrairement à d’autres éléments de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], un <xref:System.Windows.Controls.Image> n’hérite pas des <xref:System.Windows.FlowDirection> du conteneur. Toutefois, si la <xref:System.Windows.FlowDirection> est définie explicitement sur <xref:System.Windows.FlowDirection.RightToLeft>, un <xref:System.Windows.Controls.Image> s’affiche retourné horizontalement. Cette implémentation est une fonctionnalité pratique pour les développeurs de contenu bidirectionnel, car dans certains cas, le fait de retourner l’image horizontalement produit l’effet recherché.

Le graphique suivant illustre une <xref:System.Windows.Controls.Image>retournée.

![Graphique illustrant une image retournée.](./media/bidirectional-features-in-wpf-overview/flipped-image-example.png)

L’exemple suivant montre que le <xref:System.Windows.Controls.Image> ne peut pas hériter de la <xref:System.Windows.FlowDirection> du <xref:System.Windows.Controls.StackPanel> qui le contient.

> [!NOTE]
> Vous devez disposer d’un fichier nommé **ms_logo. jpg** sur votre pour exécuter cet exemple.

[!code-xaml[Image#Image](~/samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]

> [!NOTE]
> Les fichiers à télécharger sont un fichier **ms_logo. jpg** . Le code suppose que le fichier .jpg n’est pas à l’intérieur de votre projet mais quelque part sur le lecteur C:\. Vous devez copier le fichier .jpg depuis les fichiers de projet vers votre lecteur C:\ ou modifier le code pour qu’il recherche le fichier à l’intérieur du projet. Pour ce faire, `Source="file://c:/ms_logo.jpg"` `Source="ms_logo.jpg"`.

**Tracés**

En plus d’un <xref:System.Windows.Controls.Image>, un autre élément intéressant est <xref:System.Windows.Shapes.Path>. Un tracé est un objet qui peut dessiner une série de lignes et de courbes reliées. Il se comporte de manière similaire à une <xref:System.Windows.Controls.Image> concernant son <xref:System.Windows.FlowDirection>; par exemple, son <xref:System.Windows.FlowDirection.RightToLeft><xref:System.Windows.FlowDirection> est un miroir horizontal de son <xref:System.Windows.FlowDirection.LeftToRight>. Toutefois, contrairement à un <xref:System.Windows.Controls.Image>, <xref:System.Windows.Shapes.Path> hérite de son <xref:System.Windows.FlowDirection> du conteneur et il n’est pas nécessaire de le spécifier explicitement.

L’exemple suivant dessine une flèche simple à l’aide de 3 lignes. La première flèche hérite de l' <xref:System.Windows.FlowDirection.RightToLeft> sens du déroulement du <xref:System.Windows.Controls.StackPanel> afin que ses points de début et de fin soient mesurés à partir d’une racine sur le côté droit. La deuxième flèche qui a un <xref:System.Windows.FlowDirection.RightToLeft>explicite <xref:System.Windows.FlowDirection> démarre également sur le côté droit. Cependant, la troisième flèche a sa racine de début située sur le côté gauche. Pour plus d’informations sur le dessin, consultez <xref:System.Windows.Media.LineGeometry> et <xref:System.Windows.Media.GeometryGroup>.

[!code-xaml[Paths#Paths](~/samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]

Le graphique suivant montre la sortie de l’exemple précédent avec des flèches dessinées à l’aide de l’élément `Path` :

![Graphique illustrant les flèches dessinées à l’aide de l’élément Path.](./media/bidirectional-features-in-wpf-overview/arrows-drawn-path-element.png)

Les <xref:System.Windows.Controls.Image> et <xref:System.Windows.Shapes.Path> sont deux exemples de la manière dont [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] utilise les <xref:System.Windows.FlowDirection>. À côté de la disposition des éléments de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dans une direction spécifique au sein d’un conteneur, <xref:System.Windows.FlowDirection> peut être utilisé avec des éléments tels que <xref:System.Windows.Controls.InkPresenter> qui restituent l’encre sur une surface, <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>. Chaque fois que vous avez besoin d’un comportement de droite à gauche pour votre contenu qui imite le comportement de gauche à droite, ou vice versa, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit cette fonctionnalité.

<a name="NumberSubstitution"></a>

## <a name="number-substitution"></a>Substitution de nombres

Historiquement, Windows prend en charge la substitution de nombres en autorisant la représentation de différentes formes culturelles pour les mêmes chiffres tout en conservant le stockage interne de ces chiffres unifié parmi les différents paramètres régionaux, par exemple les nombres sont stockés dans leur valeurs hexadécimales bien connues, 0x40, 0x41 vers, mais affichées en fonction de la langue sélectionnée.

Cela a permis aux applications de traiter des valeurs numériques sans avoir besoin de les convertir d’une langue à une autre, par exemple, un utilisateur peut ouvrir une feuille de calcul Microsoft Excel dans une fenêtre arabe localisée et afficher les nombres en arabe, mais l’ouvrir dans un Version européenne de Windows et consultez la représentation européenne des mêmes nombres. Ceci est également nécessaire pour les autres symboles tels que les virgules et le symbole du pourcentage, car ils accompagnent habituellement des nombres dans le même document.

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] continue dans la même tradition et ajoute une prise en charge supplémentaire de cette fonctionnalité qui permet un meilleur contrôle de l’utilisateur sur quand et comment la substitution est utilisée. Bien que cette fonctionnalité soit conçue pour n’importe quelle langue, elle est particulièrement utile pour du contenu bidirectionnel, où la mise en forme des chiffres pour une langue spécifique est habituellement un défi pour les développeurs d’application du fait des différentes cultures dans lesquelles peut s’exécuter l’application.

La propriété de base contrôlant le fonctionnement de la substitution de nombres dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] est la <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> propriété de dépendance. La classe <xref:System.Windows.Media.NumberSubstitution> spécifie comment les nombres doivent être affichés dans le texte. Elle a trois propriétés publiques qui définissent son comportement. Voici un résumé de chacune des propriétés :

**CultureSource :**

Cette propriété spécifie la manière dont est déterminée la culture pour les nombres. Elle prend l’une des trois <xref:System.Windows.Media.NumberCultureSource> valeurs d’énumération.

- Override : la culture des nombres est celle de <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> propriété.

- Text : la culture pour les nombres est la culture de l’exécution de texte. Dans le balisage, il s’agit de `xml:lang`ou de sa propriété alias `Language` (<xref:System.Windows.FrameworkElement.Language%2A> ou <xref:System.Windows.FrameworkContentElement.Language%2A>). Par ailleurs, il s’agit de la valeur par défaut pour les classes dérivant de <xref:System.Windows.FrameworkContentElement>. Ces classes incluent <xref:System.Windows.Documents.Paragraph?displayProperty=nameWithType>, <xref:System.Windows.Documents.Table?displayProperty=nameWithType>, <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType> et ainsi de suite.

- User : la culture pour les nombres est la culture du thread actuel. Cette propriété est la valeur par défaut pour toutes les sous-classes de <xref:System.Windows.FrameworkElement> comme <xref:System.Windows.Controls.Page>, <xref:System.Windows.Window> et <xref:System.Windows.Controls.TextBlock>.

**CultureOverride** :

La propriété <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> est utilisée uniquement si la propriété <xref:System.Windows.Media.NumberSubstitution.CultureSource%2A> a la valeur <xref:System.Windows.Media.NumberCultureSource.Override> et est ignorée dans le cas contraire. Elle spécifie la culture pour les nombres. La valeur `null`, la valeur par défaut, est interprétée comme en-US.

**Substitution** :

Cette propriété spécifie le type de substitution de nombres à effectuer. Elle prend l’une des valeurs d’énumération <xref:System.Windows.Media.NumberSubstitutionMethod> suivantes :

- <xref:System.Windows.Media.NumberSubstitutionMethod.AsCulture>: la méthode de substitution est déterminée en fonction de la propriété de <xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=nameWithType> de la culture des nombres. Il s'agit de la valeur par défaut.

- <xref:System.Windows.Media.NumberSubstitutionMethod.Context>: si la culture du nombre est une culture arabe ou persan, elle spécifie que les chiffres dépendent du contexte.

- <xref:System.Windows.Media.NumberSubstitutionMethod.European>: les nombres sont toujours rendus en tant que chiffres européens.

- <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>: les nombres sont restitués à l’aide des chiffres nationaux pour la culture des nombres, comme spécifié par la <xref:System.Globalization.CultureInfo.NumberFormat%2A>de la culture.

- <xref:System.Windows.Media.NumberSubstitutionMethod.Traditional>: les nombres sont restitués à l’aide des chiffres traditionnels pour la culture des nombres. Pour la plupart des cultures, il s’agit de la même chose que <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>. Toutefois, <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational> produit des chiffres latins pour certaines cultures arabes, alors que cette valeur génère des chiffres arabes pour toutes les cultures arabes.

Que signifient ces valeurs pour un développeur de contenu bidirectionnel ? Dans la plupart des cas, le développeur peut avoir besoin uniquement de définir <xref:System.Windows.FlowDirection> et le langage de chaque élément de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de texte, par exemple `Language="ar-SA"` et la logique de <xref:System.Windows.Media.NumberSubstitution> prend soin d’afficher les nombres en fonction de la [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]correcte. L’exemple suivant illustre l’utilisation des nombres arabes et anglais dans une application [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] s’exécutant dans une version arabe de Windows.

[!code-xaml[Numbers#Numbers](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]

L’illustration suivante montre la sortie de l’exemple précédent si vous exécutez dans une version arabe de Windows avec des nombres arabes et anglais affichés :

![Graphique qui affiche les nombres arabes et anglais.](./media/bidirectional-features-in-wpf-overview/arabic-english-numbers.png)

Le <xref:System.Windows.FlowDirection> était important dans ce cas car la définition de la <xref:System.Windows.FlowDirection> sur <xref:System.Windows.FlowDirection.LeftToRight> aurait généré des chiffres européens. Les sections suivantes expliquent comment obtenir un affichage unifié des chiffres dans l’ensemble de votre document. Si cet exemple ne s’exécute pas sur une version arabe de Windows, tous les chiffres sont affichés en tant que chiffres européens.

**Définition des règles de substitution**

Dans une application réelle, il est possible que vous ayez besoin de définir la langue par programmation. Par exemple, vous souhaitez affecter à l’attribut `xml:lang` la même valeur que celle utilisée par le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]du système, ou peut-être modifier la langue en fonction de l’état de l’application.

Si vous souhaitez apporter des modifications en fonction de l’état de l’application, utilisez d’autres fonctionnalités fournies par [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].

Tout d’abord, définissez le `NumberSubstitution.CultureSource="Text"`du composant d’application. L’utilisation de ce paramètre permet de s’assurer que les paramètres ne proviennent pas de la [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pour les éléments de texte qui ont « User » comme valeur par défaut, comme <xref:System.Windows.Controls.TextBlock>.

Par exemple :

```xaml
<TextBlock
   Name="text1" NumberSubstitution.CultureSource="Text">
   1234+5679=6913
</TextBlock>
```

Dans le code C# correspondant, définissez la propriété `Language`, par exemple sur `"ar-SA"`.

```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");
```

Si vous devez définir la propriété `Language` sur la langue de l’interface utilisateur actuelle, utilisez le code suivant.

```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage(System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);
```

<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> représente la culture actuelle utilisée par le thread actuel au moment de l’exécution.

Votre exemple de code XAML final doit ressembler à l’exemple suivant.

[!code-xaml[Numbers2#Numbers2](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]

Votre exemple C# final doit ressembler à ce qui suit.

[!code-csharp[NumbersCSharp#NumbersCSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]

L’illustration suivante montre à quoi ressemble la fenêtre pour le langage de programmation et l’affichage des nombres arabes :

![Graphique qui affiche les nombres arabes.](./media/bidirectional-features-in-wpf-overview/displays-arabic-numbers.png)

**Utilisation de la propriété Substitution**

Le fonctionnement de la substitution de nombres dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] dépend de la langue de l’élément de texte et de ses <xref:System.Windows.FlowDirection>. Si le <xref:System.Windows.FlowDirection> est de gauche à droite, les chiffres européens sont rendus. Toutefois, s’il est précédé d’un texte en arabe ou si la langue est définie sur « AR » et que le <xref:System.Windows.FlowDirection> est <xref:System.Windows.FlowDirection.RightToLeft>, les chiffres arabes sont rendus à la place.

Toutefois, dans certains cas, il se peut que vous souhaitiez créer une application unifiée, avec par exemple des chiffres européens pour tous les utilisateurs. Ou des chiffres arabes dans <xref:System.Windows.Documents.Table> cellules avec un <xref:System.Windows.Style>spécifique. Pour ce faire, une méthode simple consiste à utiliser la propriété <xref:System.Windows.Media.NumberSubstitution.Substitution%2A>.

Dans l’exemple suivant, la première <xref:System.Windows.Controls.TextBlock> n’a pas la propriété <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> définie, de sorte que l’algorithme affiche les chiffres arabes comme prévu. Toutefois, dans la deuxième <xref:System.Windows.Controls.TextBlock>, la substitution est définie sur le remplacement de la substitution par défaut pour les nombres arabes, et les chiffres européens sont affichés.

[!code-xaml[Numbers3#Numbers3](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]
