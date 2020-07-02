---
title: Vue d'ensemble des déclarations de liaison
description: Découvrez comment déclarer une liaison en XAML pour le développement de votre application dans Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- markup extensions [WPF]
- data binding [WPF], declarations
- object element syntax [WPF]
- binding data [WPF], declarations
- syntax [WPF], object elements
- binding declarations [WPF]
ms.assetid: b97fd626-4c0d-4761-872a-2bca5820da2c
ms.openlocfilehash: 8d4943de0cacb5fe0b5a0c37a5a68f15243ad528
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619635"
---
# <a name="binding-declarations-overview"></a>Vue d'ensemble des déclarations de liaison

Cette rubrique décrit les différentes façons dont vous pouvez déclarer une liaison.

<a name="Prereq"></a>

## <a name="prerequisites"></a>Prérequis

Avant de lire cette rubrique, il est important de vous familiariser avec le concept et l’utilisation des extensions de balisage. Pour plus d’informations sur les extensions de balisage, consultez [Extensions de balisage et XAML WPF](../advanced/markup-extensions-and-wpf-xaml.md).

Cette rubrique ne couvre pas les concepts de liaison de données. Pour une présentation des concepts de liaison de données, consultez la page [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md).

<a name="BindinginXAML"></a>

## <a name="declaring-a-binding-in-xaml"></a>Déclarer une liaison en XAML

Cette section explique comment déclarer une liaison en XAML.

<a name="MarkupExtensionSyntax"></a>

### <a name="markup-extension-usage"></a>Utilisation de l’extension de balisage

<xref:System.Windows.Data.Binding> est une extension de balisage. Lorsque vous utilisez l’extension de liaison pour déclarer une liaison, la déclaration se compose d’une série de clauses suivant le mot-clé `Binding` et séparées par des virgules (,). Les clauses dans la déclaration de liaison peuvent être dans n’importe quel ordre et il existe de nombreuses combinaisons possibles. Les clauses sont des paires *nom*- = *valeur* où *nom* est le nom de la <xref:System.Windows.Data.Binding> propriété et *valeur* est la valeur que vous définissez pour la propriété.

Lorsque vous créez des chaînes de déclaration de liaison dans le balisage, elles doivent être jointes à la propriété de dépendance spécifique d’un objet cible. L’exemple suivant montre comment lier la <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> propriété à l’aide de l’extension de liaison, en spécifiant les <xref:System.Windows.Data.Binding.Source%2A> <xref:System.Windows.Data.Binding.Path%2A> Propriétés et.

[!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#L37-L37)]

Vous pouvez spécifier la plupart des propriétés de la <xref:System.Windows.Data.Binding> classe de cette manière. Pour plus d’informations sur l’extension de liaison et pour obtenir la liste des <xref:System.Windows.Data.Binding> propriétés qui ne peuvent pas être définies à l’aide de l’extension de liaison, consultez vue d’ensemble de l' [extension de balisage Binding](../advanced/binding-markup-extension.md) .

<a name="ObjectElementSyntax"></a>

### <a name="object-element-syntax"></a>Syntaxe de l’élément objet

La syntaxe d’élément objet est une alternative à la création de la déclaration de liaison. Dans la plupart des cas, il n’existe pas d’avantage particulier à l’utilisation de l’extension de balisage ou de la syntaxe d’élément objet. Toutefois, dans le cas où l’extension de balisage ne prend pas en charge votre scénario, par exemple lorsque la valeur de propriété est d’un type hors chaîne pour lequel aucune conversion n’existe, vous devez utiliser la syntaxe d’élément objet.

Voici un exemple d’utilisation de la syntaxe d’élément objet et de l’extension de balisage :

[!code-xaml[BindConversionMarkup#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversionMarkup/CSharp/Page1.xaml#1)]

L’exemple lie la <xref:System.Windows.Controls.TextBlock.Foreground%2A> propriété en déclarant une liaison à l’aide de la syntaxe d’extension. La déclaration de liaison pour la <xref:System.Windows.Controls.TextBlock.Text%2A> propriété utilise la syntaxe d’élément objet.

Pour plus d’informations sur les différents termes, consultez [Syntaxe XAML en détail](../advanced/xaml-syntax-in-detail.md).

<a name="MBandPB"></a>

### <a name="multibinding-and-prioritybinding"></a>MultiBinding et PriorityBinding

<xref:System.Windows.Data.MultiBinding>et <xref:System.Windows.Data.PriorityBinding> ne prennent pas en charge la syntaxe d’extension XAML. Par conséquent, vous devez utiliser la syntaxe d’élément objet si vous déclarez un <xref:System.Windows.Data.MultiBinding> ou un <xref:System.Windows.Data.PriorityBinding> en XAML.

<a name="BindinginCode"></a>

## <a name="creating-a-binding-in-code"></a>Création d’une liaison dans le code

Une autre façon de spécifier une liaison consiste à définir des propriétés directement sur un <xref:System.Windows.Data.Binding> objet dans le code. L’exemple suivant montre comment créer un <xref:System.Windows.Data.Binding> objet et spécifier les propriétés dans le code.  Dans cet exemple, `TheConverter` est un objet qui implémente l' <xref:System.Windows.Data.IValueConverter> interface.

[!code-csharp[BindConversion#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#1)]
[!code-vb[BindConversion#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#1)]

Si l’objet que vous liez est un <xref:System.Windows.FrameworkElement> ou un <xref:System.Windows.FrameworkContentElement> , vous pouvez appeler la `SetBinding` méthode sur votre objet directement au lieu d’utiliser <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> . Pour un exemple, consultez [Créer une liaison dans du code](how-to-create-a-binding-in-code.md).

<a name="Path_Syntax"></a>

## <a name="binding-path-syntax"></a>Syntaxe de chemin de liaison

Utilisez la <xref:System.Windows.Data.Binding.Path%2A> propriété pour spécifier la valeur source que vous souhaitez lier :

- Dans le cas le plus simple, la <xref:System.Windows.Data.Binding.Path%2A> valeur de propriété est le nom de la propriété de l’objet source à utiliser pour la liaison, telle que `Path=PropertyName` .

- Les sous-propriétés d’une propriété peuvent être spécifiées à l’aide d’une syntaxe similaire à celle de C#. Par exemple, la clause `Path=ShoppingCart.Order` définit la liaison à la sous-propriété `Order` de l’objet ou la propriété `ShoppingCart`.

- Pour lier à une propriété jointe, placez des parenthèses autour de la propriété. Par exemple, pour effectuer une liaison à la propriété jointe <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> , la syntaxe est `Path=(DockPanel.Dock)` .

- Des indexeurs de propriété peuvent être spécifiés entre crochets après le nom de la propriété où l’indexeur est appliqué. Par exemple, la clause `Path=ShoppingCart[0]` définit la liaison à l’index qui correspond à la façon dont l’indexation interne de votre propriété gère la chaîne littérale « 0 ». Les indexeurs imbriqués sont également pris en charge.

- Les indexeurs et les sous-propriétés peuvent être combinés en une clause `Path` ; par exemple, `Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`

- À l’intérieur des indexeurs, vous pouvez avoir plusieurs paramètres d’indexeur séparés par des virgules (,). Le type de chaque paramètre peut être spécifié avec des parenthèses. Par exemple, vous pouvez avoir `Path="[(sys:Int32)42,(sys:Int32)24]"`, où `sys` est mappé à l’espace de noms `System`.

- Lorsque la source est une vue de collection, l’élément actuel peut être spécifié avec une barre oblique (/). Par exemple, la clause `Path=/` définit la liaison à l’élément actuel dans la vue. Lorsque la source est une collection, cette syntaxe spécifie l’élément actuel de la vue de collection par défaut.

- Les barres obliques et les noms de propriété peuvent être combinés pour parcourir les propriétés qui sont des collections. Par exemple, `Path=/Offices/ManagerName` spécifie l’élément actuel de la collection source, qui contient une propriété `Offices` qui est également une collection. Son élément actuel est un objet qui contient une propriété `ManagerName`.

- Éventuellement, un chemin d’accès ayant la valeur point (.) peut servir à lier à la source actuelle. Par exemple, `Text="{Binding}"` équivaut à `Text="{Binding Path=.}"`.

### <a name="escaping-mechanism"></a>Mécanisme d’échappement

- À l’intérieur des indexeurs ([]), l’accent circonflexe (^) échappe le caractère suivant.

- Si vous définissez <xref:System.Windows.Data.Binding.Path%2A> en XAML, vous devez également échapper (à l’aide d’entités XML) certains caractères qui sont spécifiques à la définition de langage XML :

  - Utilisez `&amp;` pour échapper le caractère « & ».

  - Utilisez `&gt;` pour échapper la balise de fin « > ».

- En outre, si vous décrivez la liaison entière dans un attribut à l’aide de la syntaxe d’extension de balisage, vous devrez échapper (avec la barre oblique inverse \\) les caractères qui sont spécifiques à l’analyseur d’extension de balisage [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] :

  - La barre oblique inverse (\\) est le caractère d’échappement lui-même.

  - Le signe égal (=) sépare le nom de la valeur de la propriété.

  - La virgule (,) sépare les propriétés.

  - L’accolade fermante (}) se place à la fin d’une extension de balisage.

<a name="Default"></a>

## <a name="default-behaviors"></a>Comportements par défaut

Le comportement par défaut est le suivant s’il n’est pas spécifié dans la déclaration.

- Un convertisseur de valeur par défaut est créé pour effectuer une conversion de type entre la valeur de source de liaison et la valeur de cible de liaison. Si une conversion ne peut pas être effectuée, le convertisseur par défaut retourne `null`.

- Si vous ne définissez pas <xref:System.Windows.Data.Binding.ConverterCulture%2A> , le moteur de liaison utilise la `Language` propriété de l’objet de cible de liaison. En XAML, cette valeur par défaut est « en-US » ou hérite de la valeur de l’élément racine (ou tout élément) de la page, s’il a été défini explicitement.

- Tant que la liaison possède déjà un contexte de données (par exemple, le contexte de données hérité provenant d’un élément parent), et qu’un élément ou une collection que ce contexte renvoie est approprié pour la liaison sans nécessiter de modification supplémentaire du chemin d’accès, une déclaration de liaison peut n’avoir aucune clause du tout : `{Binding}` il s’agit souvent de la manière dont une liaison est spécifiée pour les styles de données, où la liaison agit sur une collection. Pour plus d’informations, consultez la section « Objets entiers utilisés comme source de liaison » dans la [Vue d’ensemble des sources de liaison](binding-sources-overview.md).

- La valeur par défaut <xref:System.Windows.Data.Binding.Mode%2A> varie en fonction de la propriété de dépendance en cours de liaison. Vous pouvez toujours déclarer explicitement le mode de liaison pour garantir que votre liaison a le comportement souhaité. En général, les propriétés de contrôle modifiables par l’utilisateur, telles que <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> et, sont par défaut des liaisons bidirectionnelles <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=nameWithType> , tandis que la plupart des autres propriétés sont par défaut des liaisons unidirectionnelles.

- La valeur par défaut <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> varie <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> en fonction de la propriété de dépendance liée. La valeur par défaut de la plupart des propriétés de dépendance est <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, tandis que celle de la propriété <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> a comme valeur par défaut <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Rubriques de procédures](data-binding-how-to-topics.md)
- [Liaison de données](../advanced/optimizing-performance-data-binding.md)
- [PropertyPath, syntaxe XAML](../advanced/propertypath-xaml-syntax.md)
