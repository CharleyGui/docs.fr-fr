---
title: Collecter l’encre numérique
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ink [WPF], collecting
- InkCanvas element [WPF]
- properties [WPF], DrawingAttributes
- collecting digital ink [WPF]
- digital ink [WPF], collecting
- properties [WPF], DefaultDrawingAttributes
- DefaultDrawingAttributes property [WPF]
ms.assetid: 66a3129d-9577-43eb-acbd-56c147282016
ms.openlocfilehash: 813a5313a6fbf83c36cdbed1f64ce69a217ad788
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747026"
---
# <a name="collect-ink"></a>Collecter l’encre

La collecte d’encre numérique fait partie des principales fonctionnalités de la plateforme [Windows Presentation Foundation](../index.md). Cette rubrique décrit les méthodes de collecte d’encre dans Windows Presentation Foundation (WPF).

## <a name="prerequisites"></a>Composants requis

Pour utiliser les exemples suivants, vous devez d’abord installer Visual Studio et le SDK Windows. Vous devez également comprendre comment écrire des applications pour WPF. Pour plus d’informations sur la prise en main de WPF, consultez [procédure pas à pas : ma première application de bureau WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).

## <a name="use-the-inkcanvas-element"></a>Utiliser l’élément InkCanvas

L’élément <xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> offre le moyen le plus simple de collecter de l’encre dans WPF. Utilisez un élément <xref:System.Windows.Controls.InkCanvas> pour recevoir et afficher l’entrée manuscrite. Généralement, vous entrez de l’encre à l’aide d’un stylet qui interagit avec un digitaliseur pour produire des traits d’encre. En outre, vous pouvez utiliser une souris à la place du stylet. Les traits créés sont représentés en tant qu’objets <xref:System.Windows.Ink.Stroke>, et ils peuvent être manipulés à la fois par programmation et par entrée d’utilisateur. Le <xref:System.Windows.Controls.InkCanvas> permet aux utilisateurs de sélectionner, modifier ou supprimer un <xref:System.Windows.Ink.Stroke>existant.

À l’aide de XAML, vous pouvez configurer la collecte manuscrite aussi facilement que l’ajout d’un élément **InkCanvas** à votre arborescence. L’exemple suivant ajoute un <xref:System.Windows.Controls.InkCanvas> à un projet WPF par défaut créé dans Visual Studio :

[!code-xaml[DigitalInkTopics#6](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]

L’élément **InkCanvas** peut également contenir des éléments enfants, ce qui permet d’ajouter des fonctionnalités d’annotation manuscrite à presque n’importe quel type d’élément XAML. Par exemple, pour ajouter des fonctionnalités d’encrage à un élément de texte, il suffit d’en faire un enfant d’un <xref:System.Windows.Controls.InkCanvas>:

[!code-xaml[DigitalInkTopics#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]

L’ajout de la prise en charge pour le marquage d’une image avec de l’encre est tout aussi simple :

[!code-xaml[DigitalInkTopics#7](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]

### <a name="inkcollection-modes"></a>Modes InkCollection

Le <xref:System.Windows.Controls.InkCanvas> fournit la prise en charge de différents modes d’entrée par le biais de sa propriété <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>.

### <a name="manipulate-ink"></a>Manipuler l’encre

Le <xref:System.Windows.Controls.InkCanvas> prend en charge de nombreuses opérations de modification de l’encre. Par exemple, <xref:System.Windows.Controls.InkCanvas> prend en charge l’effacement du stylet, et aucun code supplémentaire n’est nécessaire pour ajouter la fonctionnalité à l’élément.

#### <a name="selection"></a>Sélection

La définition du mode de sélection est aussi simple que la définition de la propriété <xref:System.Windows.Controls.InkCanvasEditingMode> sur **Select**.

Le code suivant définit le mode d’édition en fonction de la valeur d’une <xref:System.Windows.Forms.CheckBox>:

[!code-csharp[DigitalInkTopics#8](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
[!code-vb[DigitalInkTopics#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]

#### <a name="drawingattributes"></a>DrawingAttributes

Utilisez la propriété <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> pour modifier l’apparence des traits d’encre. Par exemple, le membre <xref:System.Windows.Ink.DrawingAttributes.Color%2A> de <xref:System.Windows.Ink.DrawingAttributes> définit la couleur de la <xref:System.Windows.Ink.Stroke>rendue.

L’exemple suivant modifie la couleur des traits sélectionnés en rouge :

[!code-csharp[DigitalInkTopics#9](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
[!code-vb[DigitalInkTopics#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]

### <a name="defaultdrawingattributes"></a>DefaultDrawingAttributes

La propriété <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> permet d’accéder à des propriétés telles que la hauteur, la largeur et la couleur des traits à créer dans une <xref:System.Windows.Controls.InkCanvas>. Une fois que vous modifiez la <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, tous les nouveaux traits entrés dans le <xref:System.Windows.Controls.InkCanvas> sont rendus avec les nouvelles valeurs de propriété.

En plus de modifier le <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> dans le fichier code-behind, vous pouvez utiliser la syntaxe XAML pour spécifier les propriétés de <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>.

L’exemple suivant montre comment définir la propriété <xref:System.Windows.Ink.DrawingAttributes.Color%2A>. Pour utiliser ce code, créez un projet WPF appelé « HelloInkCanvas » dans Visual Studio. Remplacez le code du fichier *MainWindow. Xaml* par le code suivant :

[!code-xaml[HelloInkCanvas#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]

Ensuite, ajoutez les gestionnaires d’événements de bouton suivants au fichier code-behind, à l’intérieur de la classe MainWindow :

[!code-csharp[HelloInkCanvas#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]

Après avoir copié ce code, appuyez sur **F5** dans Visual Studio pour exécuter le programme dans le débogueur.

Notez que le <xref:System.Windows.Controls.StackPanel> place les boutons en haut du <xref:System.Windows.Controls.InkCanvas>. Si vous essayez d’utiliser de l’encre en haut des boutons, le <xref:System.Windows.Controls.InkCanvas> collecte et restitue l’encre derrière les boutons. Cela est dû au fait que les boutons sont frères de la <xref:System.Windows.Controls.InkCanvas>, par opposition aux enfants. De même, les boutons sont plus haut dans l’ordre de plan ; l’encre est donc restituée derrière eux.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Ink.DrawingAttributes>
- <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>
- <xref:System.Windows.Ink>
