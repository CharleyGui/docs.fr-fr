---
title: Créer un style pour un contrôle
description: Apprenez à créer et à référencer un style de contrôle dans Windows Presentation Foundation et .NET Core.
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

Avec Windows Presentation Foundation (WPF), vous pouvez personnaliser l’apparence d’un contrôle existant avec votre propre style réutilisable. Les styles peuvent être appliqués globalement sur votre application, fenêtres et pages, ou directement sur les contrôles.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="create-a-style"></a>Créer un style

Vous pouvez penser <xref:System.Windows.Style> à un moyen commode d’appliquer un ensemble de valeurs de propriété à un ou plusieurs éléments. Vous pouvez utiliser un style sur <xref:System.Windows.FrameworkElement> n’importe quel élément qui dérive ou <xref:System.Windows.FrameworkContentElement> tel que un <xref:System.Windows.Window> ou un <xref:System.Windows.Controls.Button>.

La façon la plus courante de déclarer `Resources` un style est comme une ressource dans la section dans un fichier XAML. Parce que les styles sont des ressources, ils obéissent aux mêmes règles de portée qui s’appliquent à toutes les ressources. En d’autres termes, où vous déclarez qu’un style affecte l’endroit où le style peut être appliqué. Par exemple, si vous déclarez le style dans l’élément racine de votre fichier XAML de définition d’application, le style peut être utilisé n’importe où dans votre application.

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/App.xaml#AppResources)]

Si vous déclarez le style dans l’un des fichiers XAML de l’application, le style ne peut être utilisé que dans ce fichier XAML. Pour plus d’informations sur les règles de portée des ressources, consultez [Ressources XAML](xaml-resources-define.md).

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowSingleResource.xaml#WindowResources)]

Un style est `<Setter>` composé d’éléments pour enfants qui fixent des propriétés sur les éléments auxquels le style est appliqué. Dans l’exemple ci-dessus, notez `TextBlock` que le `TargetType` style est configuré pour s’appliquer aux types par l’attribut. Le style mettra <xref:System.Windows.Controls.Control.FontSize%2A> `15` le <xref:System.Windows.Controls.Control.FontWeight%2A> à `ExtraBold`et le à . Ajoutez `<Setter>` un pour chaque propriété les changements de style.

## <a name="apply-a-style-implicitly"></a>Appliquer un style implicitement

A <xref:System.Windows.Style> est un moyen pratique d’appliquer un ensemble de valeurs de propriété à plus d’un élément. Par exemple, tenez <xref:System.Windows.Controls.TextBlock> compte des éléments suivants et de leur par défaut dans une fenêtre.

[!code-xaml[TextBlocks](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetTextBlocks)]

![Capture d’écran d’échantillon de style](./media/styles-and-templates-overview/stylingintro-textblocksbefore.png "StylingIntro_TextBlocksBefore")

Vous pouvez modifier l’apparence par <xref:System.Windows.Controls.Control.FontSize%2A> défaut <xref:System.Windows.Controls.Control.FontFamily%2A>en <xref:System.Windows.Controls.TextBlock> définissant des propriétés, telles que et, sur chaque élément directement. Toutefois, si vous <xref:System.Windows.Controls.TextBlock> voulez que vos éléments partagent <xref:System.Windows.Style> certaines `Resources` propriétés, vous pouvez créer un dans la section de votre fichier XAML, comme indiqué ici.

[!code-xaml[DefaultTextBlockStyle](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetDefaultTextBlockStyle)]

Lorsque vous <xref:System.Windows.Style.TargetType%2A> définissez le <xref:System.Windows.Controls.TextBlock> style au type `x:Key` et ometez l’attribut, le style est appliqué à tous les <xref:System.Windows.Controls.TextBlock> éléments de portée au style, qui est généralement le fichier XAML lui-même.

Maintenant, <xref:System.Windows.Controls.TextBlock> les éléments apparaissent comme suit.

![Capture d’écran d’échantillon de style](./media/styles-and-templates-overview/stylingintro-textblocksbasestyle.png "StylingIntro_TextBlocksBaseStyle")

## <a name="apply-a-style-explicitly"></a>Appliquer un style explicitement

Si vous `x:Key` ajoutez un attribut avec valeur au style, le style <xref:System.Windows.Style.TargetType%2A>n’est plus implicitement appliqué à tous les éléments de . Seuls les éléments qui font explicitement référence au style auront le style appliqué à eux.

Voici le style de la section précédente, mais déclaré avec l’attribut. `x:Key`

[!code-xaml[ExplicitStyleDeclare](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleDeclare)]

Pour appliquer le style, définissez <xref:System.Windows.FrameworkElement.Style%2A> la `x:Key` propriété sur l’élément à la valeur, en utilisant une [extension de balisage StaticResource](../../framework/wpf/advanced/staticresource-markup-extension.md), comme indiqué ici.

[!code-xaml[ExplicitStyleReference](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleReference)]

Notez que <xref:System.Windows.Controls.TextBlock> le premier élément a le style appliqué à elle tandis que le deuxième élément TextBlock reste inchangé. Le style implicite de la section précédente a `x:Key` été changé en un style qui a déclaré l’attribut, ce qui signifie, le seul élément affecté par le style est celui qui a fait référence au style directement.

![Capture d’écran d’échantillon de style](./media/styles-and-templates-overview/create-a-style-explicit-textblock.png "créer un bloc de texte explicite de style")

Une fois qu’un style est appliqué, explicitement ou implicitement, il devient scellé et ne peut pas être changé. Si vous voulez changer un style qui a été appliqué, créez un nouveau style pour remplacer l’existant. Pour plus d'informations, consultez la propriété <xref:System.Windows.Style.IsSealed%2A>.

Vous pouvez créer un objet qui choisit un style à appliquer selon une logique personnalisée. Par exemple, voir l’exemple <xref:System.Windows.Controls.StyleSelector> fourni pour la classe.

## <a name="apply-a-style-programmatically"></a>Appliquer un style programmatiquement

Pour attribuer un style nommé à un élément programmatiquement, obtenir le style <xref:System.Windows.FrameworkElement.Style%2A> de la collecte des ressources et l’attribuer à la propriété de l’élément. Les éléments d’une collection <xref:System.Object>de ressources sont de type . Par conséquent, vous devez jeter <xref:System.Windows.Style?displayProperty=fullName> le style récupéré `Style` à un avant de l’attribuer à la propriété. Par exemple, le code suivant `TextBlock` définit `textblock1` le style `TitleText`d’un nommé au style défini .

[!code-csharp[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml.cs#SnippetSetStyleCode)]
[!code-vb[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/MainWindow.xaml.vb#SnippetSetStyleCode)]

## <a name="extend-a-style"></a>Étendre un style

Peut-être que <xref:System.Windows.Controls.TextBlock> vous voulez que vos deux <xref:System.Windows.Controls.Control.FontFamily%2A> éléments partagent <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>quelques valeurs de propriété, telles que le et le centré. Mais vous voulez aussi que le texte **My Pictures** ait quelques propriétés supplémentaires. Vous pouvez le faire en créant un nouveau style qui est basé sur le premier style, comme indiqué ici.

[!code-xaml[DefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

[!code-xaml[TextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

Ce `TextBlock` style est maintenant centré, utilise `Comic Sans MS` une `26`police avec une taille de <xref:System.Windows.Media.LinearGradientBrush> , et la couleur au premier plan mis à la montre dans l’exemple. Notez qu’il <xref:System.Windows.Controls.Control.FontSize%2A> l’emporte sur la valeur du style de base. S’il ya plus <xref:System.Windows.Setter> d’un pointant <xref:System.Windows.Style>vers `Setter` la même propriété dans un , le qui est déclaré dernier a préséance.

Ce qui suit <xref:System.Windows.Controls.TextBlock> montre à quoi ressemblent les éléments :

![TextBlocks mis en forme avec des styles](./media/styles-and-templates-overview/stylingintro-textblocks.png "StylingIntro_TextBlocks")

Ce `TitleText` style étend le style qui <xref:System.Windows.Controls.TextBlock> a été `BasedOn="{StaticResource {x:Type TextBlock}}"`créé pour le type, référencé avec . Vous pouvez également étendre un `x:Key` style `x:Key` qui a un en utilisant le du style. Par exemple, s’il `Header1` y avait un style nommé et `BasedOn="{StaticResource Header1}"`que vous vouliez étendre ce style, vous utiliseriez .

## <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>Relation de la propriété TargetType et l’attribut x:Key

Comme indiqué précédemment, <xref:System.Windows.Style.TargetType%2A> le `TextBlock` réglage de la `x:Key` propriété sans attribuer le <xref:System.Windows.Controls.TextBlock> style provoque l’application du style à tous les éléments. Dans ce cas, l’attribut `x:Key` a implicitement la valeur `{x:Type TextBlock}`. Cela signifie que si `x:Key` vous définissez `{x:Type TextBlock}`explicitement <xref:System.Windows.Style> la valeur à `TextBlock` autre chose que , l’est pas appliqué à tous les éléments automatiquement. Au lieu de cela, vous `x:Key` devez appliquer `TextBlock` le style (en utilisant la valeur) aux éléments explicitement. Si votre style est dans la section ressources `TargetType` et que vous ne définissez pas la propriété sur votre style, alors vous devez définir l’attribut. `x:Key`

En plus de fournir une `x:Key`valeur `TargetType` par défaut pour le , la propriété spécifie le type auquel les propriétés setter s’appliquent. Si vous ne spécifiez pas `TargetType`un <xref:System.Windows.Setter> , vous devez qualifier les `Property="ClassName.Property"`propriétés dans vos objets avec un nom de classe en utilisant la syntaxe . Par exemple, au `Property="FontSize"`lieu de <xref:System.Windows.Setter.Property%2A> `"TextBlock.FontSize"` définir, vous devez définir ou `"Control.FontSize"`.

Notez également que de nombreux contrôles WPF se composent d’une combinaison d’autres contrôles WPF. Si vous créez un style qui s’applique à tous les contrôles d’un type, vous pouvez obtenir des résultats inattendus. Par exemple, si vous créez <xref:System.Windows.Controls.TextBlock> un style <xref:System.Windows.Window>qui cible le `TextBlock` type dans un , `TextBlock` le style est appliqué à <xref:System.Windows.Controls.ListBox>tous les contrôles dans la fenêtre, même si le fait partie d’un autre contrôle, comme un .

## <a name="see-also"></a>Voir aussi

<!-- - [Create a style for a control](styles-templates-create-apply-template.md) -->
- [Aperçu des ressources XAML](xaml-resources-define.md)
- [Vue d’ensemble XAML (WPF & .NET Core)](xaml.md)
