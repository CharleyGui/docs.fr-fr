---
title: Créer un style pour un contrôle
description: Découvrez comment créer et référencer un style de contrôle dans Windows Presentation Foundation et .NET Core.
author: thraka
ms.author: adegeo
ms.date: 09/12/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: 2956dbf93a1d34feca31d3ab10536f5089010189
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "82071268"
---
# <a name="create-a-style-for-a-control-in-wpf"></a>Créer un style pour un contrôle dans WPF

Avec Windows Presentation Foundation (WPF), vous pouvez personnaliser l’apparence d’un contrôle existant avec votre propre style réutilisable. Les styles peuvent être appliqués globalement à votre application, à vos fenêtres et à vos pages, ou directement à des contrôles.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="create-a-style"></a>Créer un style

Vous pouvez considérer <xref:System.Windows.Style> comme un moyen pratique d’appliquer un ensemble de valeurs de propriétés à un ou plusieurs éléments. Vous pouvez utiliser un style sur tout élément qui dérive de <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> tel qu’un <xref:System.Windows.Window> ou un <xref:System.Windows.Controls.Button>.

La méthode la plus courante pour déclarer un style est la ressource dans la `Resources` section d’un fichier XAML. Étant donné que les styles sont des ressources, ils obéissent aux mêmes règles de portée qui s’appliquent à toutes les ressources. En d’autres termes, lorsque vous déclarez un style affecte l’endroit où le style peut être appliqué. Par exemple, si vous déclarez le style dans l’élément racine de votre fichier XAML de définition d’application, le style peut être utilisé n’importe où dans votre application.

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/App.xaml#AppResources)]

Si vous déclarez le style dans l’un des fichiers XAML de l’application, le style peut être utilisé uniquement dans ce fichier XAML. Pour plus d’informations sur les règles de portée des ressources, consultez [Ressources XAML](xaml-resources-define.md).

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowSingleResource.xaml#WindowResources)]

Un style est constitué d’éléments `<Setter>` enfants qui définissent des propriétés sur les éléments auxquels le style est appliqué. Dans l’exemple ci-dessus, Notez que le style est défini pour `TextBlock` s’appliquer aux `TargetType` types via l’attribut. <xref:System.Windows.Controls.Control.FontSize%2A> Le style affecte `15` à et à <xref:System.Windows.Controls.Control.FontWeight%2A> `ExtraBold`la valeur. Ajoutez un `<Setter>` pour chaque propriété que le style change.

## <a name="apply-a-style-implicitly"></a>Appliquer un style de manière implicite

Un <xref:System.Windows.Style> est un moyen pratique d’appliquer un ensemble de valeurs de propriété à plusieurs éléments. Par exemple, considérez les <xref:System.Windows.Controls.TextBlock> éléments suivants et leur apparence par défaut dans une fenêtre.

[!code-xaml[TextBlocks](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetTextBlocks)]

![Capture d’écran de l’exemple de style](./media/styles-and-templates-overview/stylingintro-textblocksbefore.png "StylingIntro_TextBlocksBefore")

Vous pouvez modifier l’apparence par défaut en définissant des propriétés <xref:System.Windows.Controls.Control.FontSize%2A> , <xref:System.Windows.Controls.Control.FontFamily%2A>telles que et <xref:System.Windows.Controls.TextBlock> , sur chaque élément directement. Toutefois, si vous souhaitez que <xref:System.Windows.Controls.TextBlock> vos éléments partagent des propriétés, vous pouvez créer un <xref:System.Windows.Style> élément dans `Resources` la section de votre fichier XAML, comme indiqué ici.

[!code-xaml[DefaultTextBlockStyle](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetDefaultTextBlockStyle)]

Lorsque vous définissez le <xref:System.Windows.Style.TargetType%2A> de votre style sur le <xref:System.Windows.Controls.TextBlock> type et omettez l' `x:Key` attribut, le style est appliqué à tous les <xref:System.Windows.Controls.TextBlock> éléments dont la portée est limitée au style, qui est généralement le fichier XAML lui-même.

Maintenant, <xref:System.Windows.Controls.TextBlock> les éléments apparaissent comme suit.

![Capture d’écran de l’exemple de style](./media/styles-and-templates-overview/stylingintro-textblocksbasestyle.png "StylingIntro_TextBlocksBaseStyle")

## <a name="apply-a-style-explicitly"></a>Appliquer un style explicitement

Si vous ajoutez un `x:Key` attribut avec une valeur au style, le style n’est plus appliqué implicitement à tous les éléments <xref:System.Windows.Style.TargetType%2A>de. Seuls les éléments qui référencent explicitement le style auront le style appliqué.

Voici le style de la section précédente, mais déclaré avec l' `x:Key` attribut.

[!code-xaml[ExplicitStyleDeclare](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleDeclare)]

Pour appliquer le style, affectez <xref:System.Windows.FrameworkElement.Style%2A> à la propriété de l’élément `x:Key` la valeur, à l’aide d’une [extension de balisage StaticResource](../../framework/wpf/advanced/staticresource-markup-extension.md), comme indiqué ici.

[!code-xaml[ExplicitStyleReference](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleReference)]

Notez que le style <xref:System.Windows.Controls.TextBlock> est appliqué au premier élément alors que le deuxième élément TextBlock reste inchangé. Le style implicite de la section précédente a été remplacé par un style qui `x:Key` a déclaré l’attribut, ce qui signifie que le seul élément affecté par le style est celui qui a directement référencé le style.

![Capture d’écran de l’exemple de style](./media/styles-and-templates-overview/create-a-style-explicit-textblock.png "Create-a-style-Explicit-TextBlock")

Une fois qu’un style est appliqué, explicitement ou implicitement, il devient sealed et ne peut pas être modifié. Si vous souhaitez modifier un style qui a été appliqué, créez un nouveau style pour remplacer celui qui existe déjà. Pour plus d'informations, consultez la propriété <xref:System.Windows.Style.IsSealed%2A>.

Vous pouvez créer un objet qui choisit un style à appliquer selon une logique personnalisée. Pour obtenir un exemple, consultez l’exemple fourni pour <xref:System.Windows.Controls.StyleSelector> la classe.

## <a name="apply-a-style-programmatically"></a>Appliquer un style par programmation

Pour assigner un style nommé à un élément par programme, récupérez le style de la collection de ressources et assignez <xref:System.Windows.FrameworkElement.Style%2A> -le à la propriété de l’élément. Les éléments d’une collection de ressources sont de <xref:System.Object>type. Par conséquent, vous devez effectuer un cast du style <xref:System.Windows.Style?displayProperty=fullName> récupéré en un avant de l' `Style` assigner à la propriété. Par exemple, le code suivant définit le style d’un `TextBlock` nommé `textblock1` sur le style `TitleText`défini.

[!code-csharp[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml.cs#SnippetSetStyleCode)]
[!code-vb[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/MainWindow.xaml.vb#SnippetSetStyleCode)]

## <a name="extend-a-style"></a>Étendre un style

Peut-être souhaitez- <xref:System.Windows.Controls.TextBlock> vous que vos deux éléments partagent des valeurs de propriété <xref:System.Windows.Controls.Control.FontFamily%2A> , comme et <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>le centré. Mais vous souhaitez également que le texte **Mes images** ait des propriétés supplémentaires. Pour ce faire, vous pouvez créer un nouveau style basé sur le premier style, comme illustré ici.

[!code-xaml[DefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

[!code-xaml[TextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

Ce `TextBlock` style est maintenant centré, utilise une `Comic Sans MS` police avec une taille de `26`et la couleur de premier plan définie sur <xref:System.Windows.Media.LinearGradientBrush> le indiqué dans l’exemple. Notez qu’elle remplace la <xref:System.Windows.Controls.Control.FontSize%2A> valeur du style de base. Si plusieurs <xref:System.Windows.Setter> pointent vers la même propriété dans un <xref:System.Windows.Style>, la `Setter` dernière valeur déclarée est prioritaire.

L’exemple suivant montre à <xref:System.Windows.Controls.TextBlock> quoi ressemblent les éléments :

![TextBlocks mis en forme avec des styles](./media/styles-and-templates-overview/stylingintro-textblocks.png "StylingIntro_TextBlocks")

Ce `TitleText` style étend le style qui a été créé pour le <xref:System.Windows.Controls.TextBlock> type, référencé avec `BasedOn="{StaticResource {x:Type TextBlock}}"`. Vous pouvez également étendre un style qui a un `x:Key` à l’aide `x:Key` du du style. Par exemple, s’il existe un style nommé `Header1` et que vous souhaitez étendre ce style, vous devez utiliser `BasedOn="{StaticResource Header1}"`.

## <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>Relation entre la propriété TargetType et l’attribut x :Key

Comme indiqué précédemment, l’affectation <xref:System.Windows.Style.TargetType%2A> de la `TextBlock` valeur à la propriété sans affecter `x:Key` le style à entraîne l’application du style <xref:System.Windows.Controls.TextBlock> à tous les éléments. Dans ce cas, l’attribut `x:Key` a implicitement la valeur `{x:Type TextBlock}`. Cela signifie que si vous définissez explicitement la `x:Key` valeur sur autre chose que `{x:Type TextBlock}`, le <xref:System.Windows.Style> n’est pas appliqué `TextBlock` automatiquement à tous les éléments. Au lieu de cela, vous devez appliquer explicitement le style `x:Key` (en utilisant la `TextBlock` valeur) aux éléments. Si votre style se trouve dans la section ressources et que vous ne `TargetType` définissez pas la propriété sur votre style, vous devez `x:Key` définir l’attribut.

En plus de fournir une valeur par défaut pour `x:Key`, la `TargetType` propriété spécifie le type auquel les propriétés de l’accesseur Set s’appliquent. Si vous ne spécifiez `TargetType`pas de, vous devez qualifier les propriétés <xref:System.Windows.Setter> dans vos objets avec un nom de classe à `Property="ClassName.Property"`l’aide de la syntaxe. Par exemple, au lieu de `Property="FontSize"`définir, vous devez <xref:System.Windows.Setter.Property%2A> affecter `"TextBlock.FontSize"` à `"Control.FontSize"`la valeur ou à.

Notez également que de nombreux contrôles WPF se composent d’une combinaison d’autres contrôles WPF. Si vous créez un style qui s’applique à tous les contrôles d’un type, vous pouvez obtenir des résultats inattendus. Par exemple, si vous créez un style qui cible le <xref:System.Windows.Controls.TextBlock> type dans un <xref:System.Windows.Window>, le style est appliqué à tous `TextBlock` les contrôles de la fenêtre, même si `TextBlock` le fait partie d’un autre contrôle, tel <xref:System.Windows.Controls.ListBox>qu’un.

## <a name="see-also"></a>Voir aussi

<!-- - [Create a style for a control](styles-templates-create-apply-template.md) -->
- [Vue d’ensemble des ressources XAML](xaml-resources-define.md)
- [Vue d’ensemble du langage XAML (WPF & .NET Core)](xaml.md)
