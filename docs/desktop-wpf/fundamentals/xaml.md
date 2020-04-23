---
title: Vue d’ensemble du langage XAML
description: Découvrez comment le langage XAML est structuré et implémenté par Windows Presentation Foundation (WPF) pour .NET Core.
author: thraka
ms.date: 08/08/2019
ms.author: adegeo
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user interfaces [XAML]
- classes [XAML]
- root element [XAML]
- XAML [WPF], about XAML
- base classes [XAML]
- routed events [WPF]
- code-behind files [WPF], XAML
- collection properties [XAML]
- events [XAML]
- property element [XAML]
- content models [XAML]
- Extensible Application Markup Language (see XAML)
- attribute syntax [XAML]
ms.openlocfilehash: b0a9357b623fbde08731a5b1ddb8fee3a93824c2
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "82071786"
---
# <a name="xaml-overview-in-wpf"></a>Vue d’ensemble du langage XAML dans WPF

Cet article décrit les fonctionnalités du langage XAML et montre comment vous pouvez utiliser XAML pour écrire des applications Windows Presentation Foundation (WPF). Cet article décrit spécifiquement XAML implémenté par WPF. XAML lui-même est un plus grand concept de langage que WPF.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="what-is-xaml"></a>Qu’est-ce que XAML ?

XAML est un langage de balisage déclaratif. Comme appliqué au modèle de programmation .NET Core, le langage XAML simplifie la création d’une interface utilisateur pour une application .NET Core. Vous pouvez créer des éléments d’interface utilisateur visibles dans la balise XAML déclarative, puis séparer la définition de l’interface utilisateur de la logique d’exécution en utilisant des fichiers code-behind joints à la balise par le biais de définitions de classe partielles. XAML représente directement l’instanciation d’objets dans un ensemble spécifique de types de stockage définis dans des assemblys. C’est ce qui le différencie de la plupart des autres langages de balisage, qui sont en général des langages interprétés sans un lien aussi direct à un système de type de stockage. XAML active un workflow dans lequel des parties distinctes peuvent travailler sur l’interface utilisateur et la logique d’une application, à l’aide d’outils potentiellement différents.

Représentés sous forme de texte, les fichiers XAML sont des fichiers XML qui ont généralement l’extension `.xaml`. Les fichiers peuvent être encodés par un encodage XML, même si UTF-8 est l’encodage classique.

L’exemple suivant montre comment vous pouvez créer un bouton dans le cadre d’une interface utilisateur. Cet exemple est destiné à vous fournir une idée de la façon dont XAML représente les métaphores courantes de programmation d’interface utilisateur (il ne s’agit pas d’un exemple complet).

[!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]

## <a name="xaml-syntax-in-brief"></a>Syntaxe XAML en bref

Les sections suivantes expliquent les bases de la syntaxe XAML et donnent un court exemple de balisage. Ces sections ne visent pas à fournir des informations complètes sur toutes les formes de syntaxe, telles que représentées dans le système de types de stockage. Pour plus d’informations sur les spécificités de la syntaxe XAML, consultez [syntaxe XAML en détail](../../framework/wpf/advanced/xaml-syntax-in-detail.md).

La plupart des documents des sections suivantes vous seront élémentaires si vous connaissez déjà le langage XML. C’est une conséquence d’un des principes de base de la conception du langage XAML. Le langage XAML définit ses propres concepts, mais ces concepts fonctionnent dans le langage XML et le format de balisage.

### <a name="xaml-object-elements"></a>Éléments objet XAML

Un élément objet déclare généralement une instance d’un type. Ce type est défini dans les assemblys référencés par la technologie qui utilise XAML en tant que langage.

La syntaxe d’un élément objet commence toujours par un signe « inférieur à » (`<`). Le nom du type dans lequel vous souhaitez créer une instance suit. (Le nom peut inclure un préfixe, un concept qui sera expliqué plus tard). Après cela, vous pouvez éventuellement déclarer des attributs sur l’élément objet. Pour terminer la balise de l’élément objet, terminer par un chevron`>`fermant (). Vous pouvez utiliser à la place un formulaire de fermeture automatique qui n’a pas de contenu, en renseignant la balise avec une barre oblique et un crochet pointu`/>`fermant (). Par exemple, examinez à nouveau l’extrait de code de balisage illustré précédemment.

[!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]

Deux éléments objet sont spécifiés : `<StackPanel>` (avec du contenu et suivi d’une balise de fermeture) et `<Button .../>` (avec plusieurs attributs et la forme de fermeture automatique). Les éléments `StackPanel` objet et `Button` sont tous mappés au nom d’une classe qui est définie par WPF et fait partie des assemblys WPF. Quand vous spécifiez une balise d’élément objet, vous créez une instruction pour le traitement XAML afin de créer une nouvelle instance du type sous-jacent. Chaque instance est créée en appelant le constructeur sans paramètre du type sous-jacent lors de l’analyse et du chargement du code XAML.

### <a name="attribute-syntax-properties"></a>Syntaxe d’attribut (propriétés)

Les propriétés d’un objet peuvent souvent être exprimées en tant qu’attributs de l’élément objet. La syntaxe d’attribut nomme la propriété d’objet qui est définie, suivie de l’opérateur d’assignation (=). La valeur d’un attribut est toujours spécifiée sous la forme d’une chaîne comprise entre guillemets.

La syntaxe d’attribut est la syntaxe de définition de propriétés la plus simple et la plus intuitive pour les développeurs ayant déjà utilisé des langages de balisage. Par exemple, le balisage suivant crée un bouton qui se compose d’un texte en rouge et d’un arrière-plan bleu, en plus du texte d’affichage spécifié comme `Content`.

[!code-xaml[XAMLOvwSupport#BlueRedButton](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbutton)]

### <a name="property-element-syntax"></a>Syntaxe des éléments de la propriété

Pour certaines propriétés d’un élément objet, la syntaxe d’attribut n’est pas possible parce que l’objet ou les informations nécessaires pour fournir la valeur de propriété ne peuvent pas être correctement exprimés dans les guillemets et les restrictions de chaîne de la syntaxe d’attribut. Pour ces cas particuliers, vous pouvez utiliser une autre syntaxe appelée syntaxe des éléments de propriété.

La syntaxe de la balise de début de `<TypeName.PropertyName>`l’élément de propriété est. En règle générale, le contenu de cette balise est un élément objet du type que la propriété prend comme valeur. Après avoir spécifié le contenu, vous devez fermer l’élément de propriété à l’aide d’une balise de fin. La syntaxe de la balise de `</TypeName.PropertyName>`fin est.

Si une syntaxe d’attribut est possible, son utilisation est généralement plus pratique et permet un balisage plus compact, mais il s’agit souvent d’une simple question de style et non d’une restriction technique. L’exemple suivant montre les mêmes propriétés définies comme dans l’exemple de la syntaxe d’attribut précédent, mais cette fois-ci la syntaxe des éléments de propriété est utilisée pour toutes les propriétés de `Button`.

[!code-xaml[XAMLOvwSupport#BlueRedButtonPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbuttonpe)]

### <a name="collection-syntax"></a>Syntaxe de collection

Le langage XAML offre quelques optimisations qui permettent une meilleure lecture des balises. Par exemple, si une propriété particulière utilise un type de collection, les éléments que vous déclarez dans le balisage en tant qu’éléments enfants dans cette valeur de propriété deviennent partie intégrante de la collection. Dans ce cas, une collection d’éléments objet enfants est la valeur définie pour la propriété de collection.

L’exemple suivant illustre la syntaxe de collection pour la définition <xref:System.Windows.Media.GradientBrush.GradientStops%2A> des valeurs de la propriété.

```xaml
<LinearGradientBrush>
  <LinearGradientBrush.GradientStops>
    <!-- no explicit new GradientStopCollection, parser knows how to find or create -->
    <GradientStop Offset="0.0" Color="Red" />
    <GradientStop Offset="1.0" Color="Blue" />
  </LinearGradientBrush.GradientStops>
</LinearGradientBrush>
```

### <a name="xaml-content-properties"></a>Propriétés de contenu XAML

XAML spécifie une fonctionnalité de langage par laquelle une classe peut désigner exactement l’une de ses propriétés comme étant la propriété de _contenu_ XAML. Les éléments enfants de cet élément objet sont utilisés pour définir la valeur de cette propriété de contenu. En d’autres termes, pour la propriété de contenu uniquement, vous pouvez omettre un élément de propriété lors de la définition de cette propriété dans le balisage XAML et produire une métaphore parent/enfant plus visible dans le balisage.

Par exemple, <xref:System.Windows.Controls.Border> spécifie _content_ une propriété de <xref:System.Windows.Controls.Decorator.Child%2A>contenu de. Les deux <xref:System.Windows.Controls.Border> éléments suivants sont traités de la même façon. Le premier tire parti de la syntaxe de la propriété de contenu et omet l’élément de propriété `Border.Child`. Le deuxième affiche `Border.Child` explicitement.

```xaml
<Border>
  <TextBox Width="300"/>
</Border>
<!--explicit equivalent-->
<Border>
  <Border.Child>
    <TextBox Width="300"/>
  </Border.Child>
</Border>
```

En tant que règle du langage XAML, la valeur d’une propriété de contenu XAML doit figurer soit entièrement avant soit entièrement après tous les autres éléments de propriété sur cet élément objet. Par exemple, le balisage suivant n’est pas compilé.

```xaml
<Button>I am a
  <Button.Background>Blue</Button.Background>
  blue button</Button>
```

Pour plus d’informations sur les spécificités de la syntaxe XAML, consultez [syntaxe XAML en détail](../../framework/wpf/advanced/xaml-syntax-in-detail.md).

### <a name="text-content"></a>Contenu de texte

Un petit nombre d’éléments XAML peuvent traiter directement du texte comme étant leur contenu. Pour ce faire, un des cas suivants doit se vérifier :

- La classe doit déclarer une propriété de contenu, et cette propriété de contenu doit être d’un type assignable à une chaîne (le <xref:System.Object>type peut être). Par exemple, tout <xref:System.Windows.Controls.ContentControl> utilise <xref:System.Windows.Controls.ContentControl.Content%2A> comme propriété de contenu et est de type <xref:System.Object>, et cela prend en charge l’utilisation suivante <xref:System.Windows.Controls.ContentControl> sur un tel <xref:System.Windows.Controls.Button>que `<Button>Hello</Button>`:.

- Le type doit déclarer un convertisseur de type, auquel cas le contenu de texte est utilisé comme texte d’initialisation pour ce convertisseur de type. Par exemple, `<Brush>Blue</Brush>` convertit la valeur de `Blue` contenu de en pinceau. Ce cas est moins courant dans la pratique.

- Le type doit être une primitive de langage XAML connue.

### <a name="content-properties-and-collection-syntax-combined"></a>Propriétés de contenu et syntaxe de collection combinées

Prenons l’exemple suivant.

```xaml
<StackPanel>
  <Button>First Button</Button>
  <Button>Second Button</Button>
</StackPanel>
```

Ici, chaque <xref:System.Windows.Controls.Button> est un élément enfant de <xref:System.Windows.Controls.StackPanel>. Il s’agit d’un balisage simple et intuitif qui omet deux balises pour deux raisons différentes.

- **Élément de propriété StackPanel. Children omis :** <xref:System.Windows.Controls.StackPanel> dérive de <xref:System.Windows.Controls.Panel>. <xref:System.Windows.Controls.Panel>définit <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> en tant que propriété de contenu XAML.

- **Élément objet UIElementCollection omis :** La <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> propriété prend le type <xref:System.Windows.Controls.UIElementCollection>, qui implémente <xref:System.Collections.IList>. La balise d’élément de la collection peut être omise, en fonction des règles XAML pour le <xref:System.Collections.IList>traitement des collections telles que. (Dans ce cas, <xref:System.Windows.Controls.UIElementCollection> ne peut en fait pas être instancié, car il n’expose pas de constructeur sans paramètre, et <xref:System.Windows.Controls.UIElementCollection> c’est pourquoi l’élément objet est indiqué comme commenté).

```xaml
<StackPanel>
  <StackPanel.Children>
    <!--<UIElementCollection>-->
    <Button>First Button</Button>
    <Button>Second Button</Button>
    <!--</UIElementCollection>-->
  </StackPanel.Children>
</StackPanel>
```

### <a name="attribute-syntax-events"></a>Syntaxe d’attribut (événements)

La syntaxe des attributs peut également servir pour les membres qui sont des événements plutôt que des propriétés. Dans ce cas, le nom de l’attribut est le nom de l’événement. Dans l’implémentation WPF d’événements pour XAML, la valeur de l’attribut est le nom d’un gestionnaire qui implémente le délégué de l’événement. Par exemple, le balisage suivant assigne un gestionnaire pour <xref:System.Windows.Controls.Primitives.ButtonBase.Click> l’événement à <xref:System.Windows.Controls.Button> un créé dans le balisage :

[!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]

Il existe plus d’événements et de code XAML dans WPF que cet exemple de syntaxe des attributs. Par exemple, vous vous demandez peut-être ce que le `ClickHandler` référencé ici représente et comment il est défini. Cela sera expliqué dans la section [événements à venir et code-behind XAML](#events-and-xaml-code-behind) de cet article.

## <a name="case-and-white-space-in-xaml"></a>Cas et espace blanc en XAML

En général, le code XAML respecte la casse. À des fins de résolution des types de stockage, le XAML WPF respecte la casse par les mêmes règles que celles que le CLR respecte la casse. Les éléments objet, les éléments de propriété et les noms d’attribut doivent tous être spécifiés en respectant la casse quand leurs noms sont comparés au type sous-jacent dans l’assembly ou à un membre d’un type. Les primitives et les mots clés du langage XAML sont également sensibles à la casse. Les valeurs ne respectent pas toujours la casse. Pour les valeurs, le respect de la casse varie selon le comportement du convertisseur de type associé à la propriété qui prend la valeur ou le type de valeur de la propriété. Par exemple, les propriétés qui prennent <xref:System.Boolean> le type peuvent accepter `true` ou `True` comme valeurs équivalentes, mais uniquement parce que la conversion de type d’analyseur XAML WPF <xref:System.Boolean> native pour la chaîne en autorise déjà ces équivalents.

Les sérialiseurs et les processeurs XAML WPF ignorent ou suppriment tous les espaces blancs non significatifs, et normalisent tout espace blanc significatif. Cela est cohérent avec les recommandations de comportement par défaut en matière d’espace blanc de la spécification XAML. Ce comportement est uniquement la conséquence lorsque vous spécifiez des chaînes dans les propriétés de contenu XAML. Dans les termes les plus simples, XAML convertit les caractères espace, saut de ligne et tabulation en espaces, puis conserve un espace s’il est trouvé à l’une ou l’autre extrémité d’une chaîne contiguë. L’explication complète de la gestion des espaces blancs XAML n’est pas abordée dans cet article. Pour plus d’informations, consultez [traitement des espaces blancs en XAML](../xaml-services/white-space-processing.md).

## <a name="markup-extensions"></a>Extensions de balisage

Les extensions de balisage forment un concept de langage XAML. Lorsqu’elles sont utilisées pour fournir la valeur d’une syntaxe d’attributs, les accolades (`{` et `}`) indiquent une extension de balisage. Cette utilisation ordonne au traitement XAML de se soustraire au traitement général des valeurs d’attribut, soit en tant que chaîne littérale, soit en tant que valeur convertible en chaîne.

Les extensions de balisage les plus courantes utilisées dans la [`Binding`](../../framework/wpf/advanced/binding-markup-extension.md)programmation d’applications WPF sont, utilisées pour les expressions de [`StaticResource`](../../framework/wpf/advanced/staticresource-markup-extension.md) liaison [`DynamicResource`](../../framework/wpf/advanced/dynamicresource-markup-extension.md)de données, et les références de ressources et. Grâce aux extensions de balisage, vous pouvez utiliser la syntaxe d’attributs pour fournir des valeurs aux propriétés, même si en général cette propriété ne prend pas en charge cette syntaxe. Les extensions de balisage utilisent souvent des types d’expressions intermédiaires pour activer des fonctionnalités telles que le report de valeurs ou la référence à d’autres objets qui sont présents uniquement au moment de l’exécution.

Par exemple, le balisage suivant définit la valeur de <xref:System.Windows.FrameworkElement.Style%2A> la propriété à l’aide de la syntaxe d’attribut. La <xref:System.Windows.FrameworkElement.Style%2A> propriété prend une instance de la <xref:System.Windows.Style> classe, qui, par défaut, n’a pas pu être instanciée par une chaîne de syntaxe d’attribut. Mais dans ce cas, l’attribut fait référence à une extension de `StaticResource`balisage particulière,. Lorsque cette extension de balisage est traitée, elle retourne une référence à un style qui a été instancié précédemment en tant que ressource indexée dans un dictionnaire de ressources.

[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources)]
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources2](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources2)]
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources3](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources3)]

Pour obtenir la liste de référence de toutes les extensions de balisage XAML spécifiquement implémentées dans WPF, consultez [Extensions XAML WPF](../../framework/wpf/advanced/wpf-xaml-extensions.md). Pour obtenir une liste de références des extensions de balisage définies par System. xaml et qui sont plus largement disponibles pour les implémentations XAML .NET Core, consultez [espace de noms XAML (x :) Fonctionnalités de langage](../xaml-services/namespace-language-features.md). Pour plus d’informations sur les concepts d’extension de balisage, consultez [Extensions de balisage et XAML WPF](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).

## <a name="type-converters"></a>Convertisseurs de type

La section [Syntaxe XAML en bref](#xaml-syntax-in-brief) indique que la valeur d’attribut doit pouvoir être définie par une chaîne. La gestion native de base de la façon dont les chaînes sont converties en d’autres types d’objets <xref:System.String> ou valeurs primitives est basée sur le type lui-même, <xref:System.DateTime> en <xref:System.Uri>plus du traitement natif pour certains types tels que ou. Toutefois, de nombreux types ou membres WPF de ces types étendent le comportement de traitement des attributs de chaîne de base de telle sorte que des instances de types d’objets plus complexes peuvent être spécifiées en tant que chaînes et attributs.

La <xref:System.Windows.Thickness> structure est un exemple de type pour lequel une conversion de type est activée pour les utilisations XAML. <xref:System.Windows.Thickness>indique des mesures dans un rectangle imbriqué et est utilisé comme valeur pour les propriétés telles que <xref:System.Windows.FrameworkElement.Margin%2A>. En plaçant un convertisseur de type <xref:System.Windows.Thickness>sur, toutes les propriétés qui <xref:System.Windows.Thickness> utilisent un sont plus faciles à spécifier en XAML, car elles peuvent être spécifiées en tant qu’attributs. L’exemple suivant utilise une conversion de type et une syntaxe d’attribut pour fournir une <xref:System.Windows.FrameworkElement.Margin%2A>valeur pour un :

[!code-xaml[XAMLOvwSupport#MarginTCE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#margintce)]

L’exemple de syntaxe d’attribut précédent est équivalent à l’exemple de syntaxe plus détaillée suivant, <xref:System.Windows.FrameworkElement.Margin%2A> où est défini à la place via la syntaxe <xref:System.Windows.Thickness> d’élément de propriété contenant un élément objet. Les quatre propriétés de clé <xref:System.Windows.Thickness> de sont définies en tant qu’attributs sur la nouvelle instance :

[!code-xaml[XAMLOvwSupport#MarginVerbose](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#marginverbose)]

> [!NOTE]
> Il existe également un nombre limité d’objets où la conversion de type est la seule méthode publique pour définir une propriété sur ce type sans impliquer une sous-classe, parce que le type lui-même n’a pas de constructeur sans paramètre. par exemple <xref:System.Windows.Input.Cursor>.

Pour plus d’informations sur la conversion de type, consultez [TypeConverters et XAML](../../framework/wpf/advanced/typeconverters-and-xaml.md).

## <a name="xaml-root-elements-and-xaml-namespaces"></a>Éléments racines XAML et espaces de noms XAML

Un fichier XAML ne doit avoir qu’un seul élément racine, afin d’être à la fois un fichier XML bien formé et un fichier XAML valide. Pour les scénarios WPF classiques, vous utilisez un élément racine qui a une signification visible dans le modèle d’application WPF (par <xref:System.Windows.Window> exemple <xref:System.Windows.Controls.Page> , ou pour une <xref:System.Windows.ResourceDictionary> page, un dictionnaire externe ou <xref:System.Windows.Application> la définition d’application). L’exemple suivant montre l’élément racine d’un fichier XAML standard pour une page WPF, avec l’élément racine de <xref:System.Windows.Controls.Page>.

[!code-xaml[XAMLOvwSupport#RootOnly](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly)]
[!code-xaml[XAMLOvwSupport#RootOnly2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly2)]

L’élément racine contient également les attributs `xmlns` et `xmlns:x`. Ces attributs indiquent à un processeur XAML les espaces de noms XAML contenant les définitions de types pour les types de stockage qui vont être référencés en tant qu’éléments par le balisage. L’attribut `xmlns` indique explicitement l’espace de noms XAML par défaut. Dans l’espace de noms XAML par défaut, les éléments objet dans le balisage peuvent être spécifiés sans préfixe. Pour la plupart des scénarios d’application WPF, et pour presque tous les exemples fournis dans les sections WPF du kit de développement logiciel (SDK), l’espace de noms `http://schemas.microsoft.com/winfx/2006/xaml/presentation`XAML par défaut est mappé à l’espace de noms WPF. L’attribut `xmlns:x` indique un espace de noms XAML supplémentaire qui mappe l’espace de noms du langage XAML `http://schemas.microsoft.com/winfx/2006/xaml`.

Cette utilisation de `xmlns` pour définir une étendue de l’utilisation et le mappage d’une portée de nom est conforme à la spécification XML 1.0. Les portées de nom XAML se distinguent des portées de nom XML uniquement parce qu’elles renseignent aussi sur la façon dont les éléments de la portée de nom sont stockés par les types lors d’une résolution de type et d’une analyse du code XAML.

Les `xmlns` attributs ne sont strictement nécessaires que sur l’élément racine de chaque fichier XAML. Les définitions `xmlns` s’appliquent à tous les éléments descendants de l’élément racine (ce comportement est encore une fois conforme à la spécification XML 1.0 pour `xmlns`), tandis que les attributs `xmlns` sont également autorisés sur d’autres éléments situés sous la racine et s’appliquent à tous les éléments descendants de l’élément de définition. Toutefois, si vous définissez/redéfinissez fréquemment les espaces de noms XAML, le style de balisage XAML peut devenir difficile à lire.

L’implémentation WPF de son processeur XAML inclut une infrastructure qui a connaissance des assemblys principaux WPF. Les assemblys principaux WPF sont connus pour contenir les types qui prennent en charge les mappages WPF à l’espace de noms XAML par défaut. Cette option est activée par le biais de la configuration faisant partie du fichier de build de votre projet et des systèmes de projet et de build WPF. Par conséquent, la déclaration de l’espace de noms XAML `xmlns` par défaut est tout ce qui est nécessaire pour référencer des éléments XAML provenant d’assemblys WPF.

### <a name="the-x-prefix"></a>Le préfixe x :

Dans l’exemple d’élément racine précédent, le préfixe `x:` a été utilisé pour mapper l’espace de noms XAML `http://schemas.microsoft.com/winfx/2006/xaml`, qui est l’espace de noms XAML dédié prenant en charge les constructions du langage XAML. Ce `x:` préfixe est utilisé pour mapper cet espace de noms XAML dans les modèles pour les projets, dans les exemples et dans la documentation de ce kit de développement logiciel (SDK). L’espace de noms XAML du langage XAML contient plusieurs constructions de programmation que vous utiliserez fréquemment dans votre XAML. Voici une liste de constructions de programmation avec le préfixe `x:` parmi les plus courantes que vous allez utiliser :

- [x :Key](../xaml-services/xkey-directive.md): définit une clé unique pour chaque ressource dans un <xref:System.Windows.ResourceDictionary> (ou des concepts de dictionnaire similaires dans d’autres frameworks). `x:Key`prendra probablement en compte 90% des utilisations `x:` que vous verrez dans le balisage d’une application WPF typique.

- [x :Class](../xaml-services/xclass-directive.md): spécifie l’espace de noms CLR et le nom de classe pour la classe qui fournit le code-behind pour une page XAML. Vous devez disposer d’une telle classe pour prendre en charge le code-behind selon le modèle de programmation WPF, et c’est la raison pour laquelle vous voyez presque toujours `x:` mappé, même s’il n’ y a aucune ressource.

- [x:Name](../xaml-services/xname-directive.md) : spécifie un nom d’objet d’exécution pour l’instance qui existe dans le code d’exécution après le traitement d’un élément objet. En général, vous êtes amené à utiliser fréquemment une propriété équivalente définie par WPF pour [x:Name](../xaml-services/xname-directive.md). Ces propriétés sont mappées spécifiquement à une propriété de stockage CLR et sont donc plus pratiques pour la programmation d’applications, où vous utilisez fréquemment le code d’exécution pour rechercher les éléments nommés à partir du code XAML initialisé. La propriété de ce type est <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>la plus courante. Vous pouvez toujours utiliser [x :Name](../xaml-services/xname-directive.md) lorsque la propriété de niveau <xref:System.Windows.FrameworkElement.Name%2A> Framework WPF équivalente n’est pas prise en charge dans un type particulier. Ce cas se présente dans certains scénarios d’animation.

- [x:Static](../xaml-services/xstatic-markup-extension.md) : active une référence qui retourne une valeur statique qui, sinon, n’est pas une propriété compatible XAML.

- [x :type](../xaml-services/xtype-markup-extension.md): construit une <xref:System.Type> référence basée sur un nom de type. Cela permet de spécifier les attributs qui prennent <xref:System.Type>, par exemple <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>, bien que la propriété ait souvent une chaîne à<xref:System.Type> convertir native de telle sorte que l’utilisation d’une extension de balisage [x :type](../xaml-services/xtype-markup-extension.md) soit facultative.

Il existe d’autres constructions de programmation dans l’espace de noms XAML à préfixe `x:` qui ne sont pas aussi courantes. Pour plus d’informations, consultez [Fonctionnalités de langage pour les espaces de noms XAML (x:)](../xaml-services/namespace-language-features.md).

## <a name="custom-prefixes-and-custom-types-in-xaml"></a>Préfixes personnalisés et types personnalisés en XAML

Pour vos propres assemblys personnalisés, ou pour des assemblys en dehors du noyau WPF de **PresentationCore**, **PresentationFramework** et **WindowsBase**, vous pouvez spécifier l’assembly dans le `xmlns` cadre d’un mappage personnalisé. Vous pouvez ensuite référencer des types depuis cet assembly dans votre XAML à partir du moment où le type voulu est correctement implémenté pour prendre en charge les utilisations XAML que vous essayez.

Voici un exemple de base illustrant le fonctionnement des préfixes personnalisés dans le balisage XAML. Le préfixe `custom` est défini dans la balise d’élément racine et est mappé à un assembly spécifique qui est empaqueté et disponible avec l’application. Cet assembly contient un type `NumericUpDown`, qui est implémenté pour prendre en charge l’utilisation générale de XAML ainsi que l’utilisation d’un héritage de classe, autorisant son insertion à ce stade dans un modèle de contenu XAML WPF. Une instance de ce contrôle `NumericUpDown` est déclaré comme élément objet en utilisant le préfixe afin qu’un analyseur XAML identifie quel espace de noms XAML contient le type et par conséquent l’emplacement de l’assembly de stockage contenant la définition de type.

```xaml
<Page
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:custom="clr-namespace:NumericUpDownCustomControl;assembly=CustomLibrary"
    >
  <StackPanel Name="LayoutRoot">
    <custom:NumericUpDown Name="numericCtrl1" Width="100" Height="60"/>
...
  </StackPanel>
</Page>
```

Pour plus d’informations sur les types personnalisés en XAML, consultez [XAML et les classes personnalisées pour WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).

Pour plus d’informations sur la façon dont les espaces de noms XML et les espaces de noms de code dans les assemblys sont liés, consultez [espaces de noms XAML et mappage d’espace de noms pour XAML WPF](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).

## <a name="events-and-xaml-code-behind"></a>Événements et code-behind XAML

La plupart des applications WPF se composent à la fois du balisage XAML et du code-behind. Dans un projet, le code XAML est écrit sous `.xaml` la forme d’un fichier, et un langage CLR tel que Microsoft Visual Basic ou C# est utilisé pour écrire un fichier code-behind. Lors de la compilation du balisage d’un fichier XAML comme partie intégrante des modèles de programmation et d’application WPF, l’emplacement du fichier code-behind XAML pour un fichier XAML est identifié en spécifiant un espace de noms et une classe en tant qu’attribut `x:Class` de l’élément racine du XAML.

Jusqu’ici dans les exemples étudiés, vous avez vu plusieurs boutons, mais aucun d’eux n’avait encore de comportement logique qui lui était associé. Le mécanisme principal au niveau de l’application pour ajouter un comportement pour un élément objet consiste à utiliser un événement existant de la classe d’éléments et à écrire un gestionnaire spécifique pour cet événement qui est appelé quand cet événement est déclenché au moment de l’exécution. Le nom de l’événement et celui du gestionnaire à utiliser sont spécifiés dans le balisage, tandis que le code qui implémente le gestionnaire est défini dans le fichier code-behind.

[!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]

[!code-csharp[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml.cs#buttonwithcodebehindhandler)]
[!code-vb[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#buttonwithcodebehindhandler)]

Notez que le fichier code-behind utilise l’espace de noms CLR `ExampleNamespace` et déclare `ExamplePage` comme une classe partielle dans cet espace de noms. Cela correspond à la valeur d’attribut `x:Class` de `ExampleNamespace`.`ExamplePage` qui a été fournie dans la racine de la balise. Le compilateur de balisage WPF crée une classe partielle pour tout fichier XAML compilé, en dérivant une classe à partir du type d’élément racine. Quand vous fournissez du code-behind qui définit également la même classe partielle, le code résultant est combiné dans le même espace de noms et la même classe de l’application compilée.

Pour plus d’informations sur la configuration requise pour la programmation code-behind dans WPF, consultez [code-behind, gestionnaire d’événements et exigences de classe partielle dans WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md#code-behind-event-handler-and-partial-class-requirements-in-wpf).

Si vous ne souhaitez pas créer de fichier code-behind distinct, vous pouvez également incorporer votre code dans un fichier XAML. Toutefois, le code incorporé est une technique moins flexible qui présente des limitations importantes. Pour plus d’informations, consultez [code-behind et XAML dans WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).

### <a name="routed-events"></a>Événements routés

Une fonctionnalité d’événement particulière qui est fondamentale pour WPF est un événement routé. Les événements routés permettent à un élément de gérer un événement déclenché par un élément différent, tant que ces éléments sont connectés via une relation d’arborescence. Lorsque vous spécifiez la gestion des événements avec un attribut XAML, vous pouvez écouter et géré l’événement routé sur n’importe quel élément, notamment les éléments qui ne listent pas cet événement particulier dans la table des membres de la classe. Pour cela, vous devez qualifier l’attribut de nom d’événement avec le nom de la classe propriétaire. Par exemple, le parent `StackPanel` de l’exemple `StackPanel`  /  `Button` en cours peut inscrire un gestionnaire pour l’événement du bouton <xref:System.Windows.Controls.Primitives.ButtonBase.Click> d’élément enfant en spécifiant `Button.Click` l' `StackPanel` attribut sur l’élément objet, avec le nom de votre gestionnaire comme valeur d’attribut. Pour plus d’informations, consultez [vue d’ensemble des événements routés](../../framework/wpf/advanced/routed-events-overview.md).

## <a name="xaml-named-elements"></a>Éléments nommés XAML

Par défaut, l’instance d’objet qui est créée par le traitement d’un élément objet XAML dans un graphique d’objet n’a pas d’identificateur unique ni de référence d’objet. En revanche, si vous appelez un constructeur dans le code, vous utilisez presque toujours le résultat du constructeur pour définir une variable sur l’instance construite, afin de pouvoir référencer l’instance ultérieurement dans votre code. Pour fournir un accès standardisé aux objets créés via une définition de balise, XAML définit l’[attribut x:Name](../xaml-services/xname-directive.md). Vous pouvez définir la valeur de l’attribut `x:Name` sur n’importe quel élément objet. Dans votre code-behind, l’identificateur que vous choisissez équivaut à une variable d’instance qui fait référence à l’instance construite. À tous égards, les éléments nommés fonctionnent comme s’il s’agissait d’instances d’objet (le nom fait référence à cette instance) et votre code-behind peut référencer les éléments nommés pour gérer les interactions au moment de l’exécution au sein de l’application. Cette connexion entre les instances et les variables est accomplie par le compilateur de balisage XAML WPF et implique plus spécifiquement des <xref:System.Windows.Markup.IComponentConnector.InitializeComponent%2A> fonctionnalités et des modèles tels que qui ne seront pas abordés en détail dans cet article.

Les éléments XAML au niveau de l’infrastructure <xref:System.Windows.FrameworkElement.Name%2A> WPF héritent d’une propriété, qui est `x:Name` équivalente à l’attribut XAML défini. Certaines autres classes fournissent également des équivalents de niveau propriété pour `x:Name`, qui est aussi généralement défini en tant que propriété `Name`. En règle générale, si vous ne trouvez pas une propriété `Name` dans la table des membres pour votre élément/type choisi, utilisez `x:Name` à la place. Les `x:Name` valeurs fournissent un identificateur à un élément XAML qui peut être utilisé au moment de l’exécution, soit par des sous-systèmes spécifiques, soit par des méthodes utilitaires <xref:System.Windows.FrameworkElement.FindName%2A>telles que.

L’exemple suivant définit <xref:System.Windows.FrameworkElement.Name%2A> sur un <xref:System.Windows.Controls.StackPanel> élément. Ensuite, un gestionnaire sur un <xref:System.Windows.Controls.Button> dans qui <xref:System.Windows.Controls.StackPanel> référence le <xref:System.Windows.Controls.StackPanel> par le biais de `buttonContainer` sa référence d' <xref:System.Windows.FrameworkElement.Name%2A>instance telle que définie par.

[!code-xaml[XAMLOvwSupport#NamedE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede)]
[!code-xaml[XAMLOvwSupport#NamedE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede2)]

[!code-csharp[XAMLOvwSupport#NameCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml.cs#namecode)]
[!code-vb[XAMLOvwSupport#NameCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#namecode)]

Tout comme une variable, le nom XAML d’une instance est régi par un concept de portée afin que les noms puissent être appliqués pour être uniques dans une certaine étendue qui est prévisible. La balisage principal qui définit une page désigne une portée de nom XAML unique, avec pour élément racine de cette page, les limites de portée de nom XAML. Toutefois, d’autres sources de balisage peuvent interagir avec une page au moment de l’exécution, telles que les styles ou les modèles dans les styles, et ces sources de balisage ont souvent leurs propres portées de code XAML qui ne se connectent pas nécessairement à la portée de code XAML de la page. Pour plus d’informations `x:Name` sur les portées de <xref:System.Windows.FrameworkElement.Name%2A>code XAML et, consultez, [directive x :Name](../xaml-services/xname-directive.md)ou portées de [code XAML WPF](../../framework/wpf/advanced/wpf-xaml-namescopes.md).

## <a name="attached-properties-and-attached-events"></a>Propriétés jointes et événements attachés

Le langage XAML comporte une fonctionnalité de langage qui permet à certaines propriétés ou événements d’être spécifiés sur n’importe quel élément, et cela même si la propriété ou l’événement existe dans les définitions de type pour l’élément sur lequel il est défini. La version des propriétés de cette fonctionnalité est appelée une propriété jointe, et la version des événements, un événement attaché. D’un point de vue conceptuel, vous pouvez considérer les propriétés jointes et les événements attachés comme des membres globaux pouvant être définis sur n’importe quelle instance d’élément ou d’objet XAML. Toutefois, cet élément/cette classe ou une infrastructure plus importante doit prendre en charge une banque de propriétés de stockage pour les valeurs attachées.

Les propriétés jointes en XAML sont généralement utilisées dans la syntaxe d’attributs. Dans la syntaxe d’attribut, vous spécifiez une propriété jointe dans le formulaire `ownerType.propertyName`.

En apparence, cela ressemble à une utilisation d’élément de propriété, mais dans ce `ownerType` cas, le que vous spécifiez est toujours un type différent de l’élément objet dans lequel la propriété jointe est définie. `ownerType`est le type qui fournit les méthodes d’accesseur requises par un processeur XAML pour obtenir ou définir la valeur de la propriété jointe.

Le scénario le plus courant pour les propriétés jointes consiste à permettre aux éléments enfants de signaler une valeur de propriété à leur élément parent.

L’exemple suivant illustre la <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> propriété jointe. La <xref:System.Windows.Controls.DockPanel> classe définit les accesseurs pour <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> et, par conséquent, possède la propriété jointe. La <xref:System.Windows.Controls.DockPanel> classe comprend également une logique qui itère ses éléments enfants et vérifie spécifiquement chaque élément pour une valeur définie de <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>. Si une valeur est trouvée, cette valeur est utilisée au cours de la disposition pour positionner les éléments enfants. L’utilisation de <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> la propriété jointe et de cette fonctionnalité de positionnement est en fait le scénario <xref:System.Windows.Controls.DockPanel> motivant pour la classe.

[!code-xaml[XAMLOvwSupport#DockAP](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#dockap)]

Dans WPF, la plupart ou toutes les propriétés jointes sont également implémentées en tant que propriétés de dépendance. Pour plus d’informations, consultez [Vue d’ensemble des propriétés jointes](../../framework/wpf/advanced/attached-properties-overview.md).

Les événements attachés utilisent `ownerType.eventName` une forme similaire de syntaxe d’attribut. À l’instar des événements non attachés, la valeur d’attribut d’un événement attaché en XAML spécifie le nom de la méthode de gestionnaire qui est appelée lorsque l’événement est géré sur l’élément. Les utilisations d’événements attachés en XAML WPF sont moins courantes. Pour plus d’informations, consultez [Vue d’ensemble des événements attachés](../../framework/wpf/advanced/attached-events-overview.md).

## <a name="base-types-and-xaml"></a>Types de base et XAML

Le XAML WPF sous-jacent et son espace de noms XAML sont une collection de types qui correspondent aux objets CLR en plus des éléments de balisage pour XAML. Cela étant, toutes les classes ne peuvent pas être mappées aux éléments. Les classes abstraites, <xref:System.Windows.Controls.Primitives.ButtonBase>telles que, et certaines classes de base non abstraites, sont utilisées pour l’héritage dans le modèle d’objets CLR. Les classes de base, y compris abstraites, sont toujours importantes pour le développement en XAML, car chacun des éléments XAML concrets hérite de membres provenant d’une classe de base dans sa hiérarchie. Ces membres incluent souvent des propriétés qui peuvent être définies en tant qu’attributs sur l’élément, ou comme événements qui peuvent être gérés. <xref:System.Windows.FrameworkElement>est la classe d’interface utilisateur de base concrète de WPF au niveau de l’infrastructure WPF. Lors de la conception de l’interface utilisateur, vous utiliserez différentes classes de formes, de volets, d' <xref:System.Windows.FrameworkElement>éléments décoratifs ou de contrôles, qui dérivent toutes de. Une classe de base connexe, <xref:System.Windows.FrameworkContentElement>, prend en charge les éléments orientés document qui fonctionnent bien pour une présentation de mise en page fluide, <xref:System.Windows.FrameworkElement>à l’aide d’API qui reflètent délibérément les API dans. La combinaison d’attributs au niveau de l’élément et d’un modèle objet CLR vous fournit un ensemble de propriétés communes qui peuvent être définies sur la plupart des éléments XAML concrets, quel que soit l’élément XAML spécifique et son type sous-jacent.

## <a name="xaml-security"></a>Sécurité XAML

Le XAML est un langage de balisage qui représente directement l’instanciation d’objets et leur exécution. Ainsi, les éléments créés en XAML ont la même capacité d’interagir avec les ressources système (accès réseau, e/s de système de fichiers, par exemple) que le code généré équivalent. Le code XAML chargé dans une application de confiance totale a le même accès aux ressources système que l’application d’hébergement.

### <a name="code-access-security-cas-in-wpf"></a>Sécurité d’accès du code (CAS) dans WPF

**Cette section s’applique uniquement aux .NET Framework. WPF pour .NET Core ne prend pas en charge les autorités de certification. Pour plus d’informations, consultez [différences de sécurité d’accès du code](../migration/differences-from-net-framework.md#code-access-security).**

WPF pour .NET Framework prend en charge la sécurité d’accès du code (CAS). Cela signifie que le contenu WPF s’exécutant dans la zone Internet a des autorisations d’exécution réduites. « XAML libre » (pages de code XAML non compilés interprétées au moment du chargement par une visionneuse XAML) et XBAP sont généralement exécutés dans cette zone Internet et utilisent le même jeu d’autorisations. Toutefois, le XAML chargé dans une application d’un niveau de confiance totale dispose du même accès aux ressources système que l’application d’hébergement. Pour plus d’informations, consultez [Sécurité de confiance partielle de WPF](../../framework/wpf/wpf-partial-trust-security.md).

## <a name="loading-xaml-from-code"></a>Charger XAML à partir du code

Vous utilisez XAML pour définir l’ensemble de l’interface utilisateur, mais il est parfois également judicieux de ne définir qu’une partie de l’interface utilisateur en XAML. Vous pouvez vous servir de cette fonctionnalité pour activer la personnalisation partielle, un stockage local des informations, et utiliser XAML pour fournir un objet métier ou une variété de scénarios possibles. La clé de ces scénarios est la <xref:System.Windows.Markup.XamlReader> classe et sa <xref:System.Windows.Markup.XamlReader.Load%2A> méthode. L’entrée est un fichier XAML, et la sortie un objet représentant l’intégralité de l’arborescence d’exécution des objets qui a été créée à partir de ce balisage. Vous pouvez ensuite insérer l’objet pour qu’il s’agit d’une propriété d’un autre objet qui existe déjà dans l’application. Tant que la propriété est une propriété appropriée dans le modèle de contenu qui a des fonctionnalités d’affichage, et qui notifie le moteur d’exécution qu’un nouveau contenu a été ajouté à l’application, vous pouvez facilement modifier le contenu d’une application en cours d’exécution en chargeant en XAML. Par .NET Framework, cette fonctionnalité est généralement uniquement disponible dans les applications de confiance totale, en raison des implications évidentes en matière de sécurité du chargement de fichiers dans des applications lorsqu’elles s’exécutent.

## <a name="see-also"></a>Voir aussi

- [Syntaxe XAML en détail](../../framework/wpf/advanced/xaml-syntax-in-detail.md)
- [XAML et classes personnalisées pour WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [Espace de noms XAML (x:) Fonctionnalités de langage](../xaml-services/namespace-language-features.md)
- [Extensions XAML WPF](../../framework/wpf/advanced/wpf-xaml-extensions.md)
- [Vue d'ensemble des éléments de base](../../framework/wpf/advanced/base-elements-overview.md)
- [Arborescences dans WPF](../../framework/wpf/advanced/trees-in-wpf.md)
