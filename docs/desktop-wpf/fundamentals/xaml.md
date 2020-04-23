---
title: Vue d’ensemble du langage XAML
description: Découvrez comment la langue XAML est structurée et implémentée par Windows Presentation Foundation (WPF) pour .NET Core.
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
# <a name="xaml-overview-in-wpf"></a>Vue d’ensemble XAML dans WPF

Cet article décrit les caractéristiques de la langue XAML et démontre comment vous pouvez utiliser XAML pour écrire windows Presentation Foundation (WPF) applications. Cet article décrit spécifiquement XAML tel qu’implémenté par WPF. XAML lui-même est un concept linguistique plus large que WPF.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="what-is-xaml"></a>Qu’est-ce que XAML

XAML est un langage de balisage déclaratif. Appliquée au modèle de programmation .NET Core, XAML simplifie la création d’une interface utilisateur pour une application .NET Core. Vous pouvez créer des éléments d’interface utilisateur visibles dans le balisage déclaratif XAML, puis séparer la définition d’interface utilisateur de la logique de l’exécution du temps en utilisant des fichiers de code-derrière qui sont joints à la balisage par des définitions partielles de classe. XAML représente directement l’instanciation d’objets dans un ensemble spécifique de types de stockage définis dans des assemblys. C’est ce qui le différencie de la plupart des autres langages de balisage, qui sont en général des langages interprétés sans un lien aussi direct à un système de type de stockage. XAML permet un flux de travail où des parties distinctes peuvent travailler sur l’interface utilisateur et la logique d’une application, en utilisant des outils potentiellement différents.

Représentés sous forme de texte, les fichiers XAML sont des fichiers XML qui ont généralement l’extension `.xaml`. Les fichiers peuvent être encodés par un encodage XML, même si UTF-8 est l’encodage classique.

L’exemple suivant montre comment vous pouvez créer un bouton dans le cadre d’une interface utilisateur. Cet exemple est destiné à vous donner une saveur de la façon dont XAML représente les métaphores courantes de programmation d’interface utilisateur (ce n’est pas un échantillon complet).

[!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]

## <a name="xaml-syntax-in-brief"></a>Syntaxe XAML en bref

Les sections suivantes expliquent les bases de la syntaxe XAML et donnent un court exemple de balisage. Ces sections ne visent pas à fournir des informations complètes sur toutes les formes de syntaxe, telles que représentées dans le système de types de stockage. Pour plus d’informations sur les spécificités de la syntaxe XAML, voir [XAML Syntax In Detail](../../framework/wpf/advanced/xaml-syntax-in-detail.md).

Une grande partie du matériel dans les prochaines sections sera élémentaire pour vous si vous avez une familiarité antérieure avec la langue XML. C’est une conséquence d’un des principes de base de la conception du langage XAML. La langue XAML définit ses propres concepts, mais ces concepts fonctionnent dans la langue XML et la forme de balisage.

### <a name="xaml-object-elements"></a>Éléments d’objets XAML

Un élément objet déclare généralement une instance d’un type. Ce type est défini dans les assemblages référencés par la technologie qui utilise XAML comme langue.

La syntaxe d’un élément objet commence toujours par un signe « inférieur à » (`<`). Le nom du type dans lequel vous souhaitez créer une instance suit. (Le nom peut inclure un préfixe, un concept qui sera expliqué plus tard.) Après cela, vous pouvez déclarer d’option des attributs sur l’élément objet. Pour compléter l’étiquette de l’élément`>`objet, terminez avec un support d’angle de fermeture (). Vous pouvez plutôt utiliser un formulaire d’auto-fermeture qui n’a pas de contenu,`/>`en complétant l’étiquette avec une barre oblique avant et le support d’angle de fermeture dans la succession ( ). Par exemple, regardez à nouveau l’extrait de balisage déjà montré.

[!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]

Deux éléments objet sont spécifiés : `<StackPanel>` (avec du contenu et suivi d’une balise de fermeture) et `<Button .../>` (avec plusieurs attributs et la forme de fermeture automatique). Les éléments `StackPanel` `Button` d’objet et chaque carte au nom d’une classe qui est définie par WPF et fait partie des assemblages WPF. Lorsque vous spécifiez une balise d’élément objet, vous créez une instruction pour le traitement XAML pour créer une nouvelle instance du type sous-jacent. Chaque instance est créée en appelant le constructeur sans paramètres du type sous-jacent lors de l’analyse et du chargement de la XAML.

### <a name="attribute-syntax-properties"></a>Attribuer la syntaxe (propriétés)

Les propriétés d’un objet peuvent souvent être exprimées en tant qu’attributs de l’élément objet. La syntaxe d’attribut nomme la propriété de l’objet qui est réglée, suivie par l’opérateur d’affectation (MD). La valeur d’un attribut est toujours spécifiée sous la forme d’une chaîne comprise entre guillemets.

La syntaxe d’attribut est la syntaxe de définition de propriétés la plus simple et la plus intuitive pour les développeurs ayant déjà utilisé des langages de balisage. Par exemple, le balisage suivant crée un bouton qui se compose d’un texte en rouge et d’un arrière-plan bleu, en plus du texte d’affichage spécifié comme `Content`.

[!code-xaml[XAMLOvwSupport#BlueRedButton](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbutton)]

### <a name="property-element-syntax"></a>Syntaxe des éléments de la propriété

Pour certaines propriétés d’un élément objet, la syntaxe d’attribut n’est pas possible parce que l’objet ou les informations nécessaires pour fournir la valeur de propriété ne peuvent pas être correctement exprimés dans les guillemets et les restrictions de chaîne de la syntaxe d’attribut. Pour ces cas particuliers, vous pouvez utiliser une autre syntaxe appelée syntaxe des éléments de propriété.

La syntaxe pour l’étiquette de démarrage de l’élément de propriété est `<TypeName.PropertyName>`. En général, le contenu de cette balise est un élément objet du type que la propriété prend comme valeur. Après avoir spécifiant le contenu, vous devez fermer l’élément de propriété avec une étiquette de fin. La syntaxe pour `</TypeName.PropertyName>`l’étiquette de fin est .

Si une syntaxe d’attribut est possible, son utilisation est généralement plus pratique et permet un balisage plus compact, mais il s’agit souvent d’une simple question de style et non d’une restriction technique. L’exemple suivant montre les mêmes propriétés définies comme dans l’exemple de la syntaxe d’attribut précédent, mais cette fois-ci la syntaxe des éléments de propriété est utilisée pour toutes les propriétés de `Button`.

[!code-xaml[XAMLOvwSupport#BlueRedButtonPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbuttonpe)]

### <a name="collection-syntax"></a>Syntaxe de collection

Le langage XAML offre quelques optimisations qui permettent une meilleure lecture des balises. Par exemple, si une propriété particulière utilise un type de collection, les éléments que vous déclarez dans le balisage en tant qu’éléments enfants dans cette valeur de propriété deviennent partie intégrante de la collection. Dans ce cas, une collection d’éléments objet enfants est la valeur définie pour la propriété de collection.

L’exemple suivant montre la syntaxe de collecte pour définir les valeurs de la <xref:System.Windows.Media.GradientBrush.GradientStops%2A> propriété.

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

XAML spécifie une caractéristique linguistique par laquelle une classe peut désigner exactement l’une de ses propriétés comme propriété de _contenu_ XAML. Les éléments enfants de cet élément objet sont utilisés pour définir la valeur de cette propriété de contenu. En d’autres termes, pour la propriété de contenu uniquement, vous pouvez omettre un élément de propriété lors de la définition de cette propriété dans le balisage XAML et produire une métaphore parent/enfant plus visible dans le balisage.

Par exemple, <xref:System.Windows.Controls.Border> spécifie <xref:System.Windows.Controls.Decorator.Child%2A>une propriété de _contenu_ de . Les deux <xref:System.Windows.Controls.Border> éléments suivants sont traités à l’identique. Le premier tire parti de la syntaxe de la propriété de contenu et omet l’élément de propriété `Border.Child`. Le deuxième affiche `Border.Child` explicitement.

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

En tant que règle du langage XAML, la valeur d’une propriété de contenu XAML doit figurer soit entièrement avant soit entièrement après tous les autres éléments de propriété sur cet élément objet. Par exemple, la majoration suivante ne se compile pas.

```xaml
<Button>I am a
  <Button.Background>Blue</Button.Background>
  blue button</Button>
```

Pour plus d’informations sur les spécificités de la syntaxe XAML, voir [XAML Syntax In Detail](../../framework/wpf/advanced/xaml-syntax-in-detail.md).

### <a name="text-content"></a>Contenu texte

Un petit nombre d’éléments XAML peuvent traiter directement du texte comme étant leur contenu. Pour ce faire, un des cas suivants doit se vérifier :

- La classe doit déclarer une propriété de contenu, et que la propriété de <xref:System.Object>contenu doit être d’un type attribué à une chaîne (le type pourrait être ). Par exemple, <xref:System.Windows.Controls.ContentControl> <xref:System.Windows.Controls.ContentControl.Content%2A> toute utilisation comme propriété <xref:System.Object>de contenu et il est <xref:System.Windows.Controls.ContentControl> de <xref:System.Windows.Controls.Button>type `<Button>Hello</Button>`, et cela prend en charge l’utilisation suivante sur un tel: .

- Le type doit déclarer un convertisseur de type, auquel cas le contenu de texte est utilisé comme texte d’initialisation pour ce convertisseur de type. Par exemple, `<Brush>Blue</Brush>` convertit la `Blue` valeur de contenu en pinceau. Ce cas est moins courant dans la pratique.

- Le type doit être une primitive de langage XAML connue.

### <a name="content-properties-and-collection-syntax-combined"></a>Propriétés de contenu et syntaxe de collecte combinées

Prenons cet exemple.

```xaml
<StackPanel>
  <Button>First Button</Button>
  <Button>Second Button</Button>
</StackPanel>
```

Ici, <xref:System.Windows.Controls.Button> chacun est un <xref:System.Windows.Controls.StackPanel>élément enfant de . Il s’agit d’un balisage simple et intuitif qui omet deux balises pour deux raisons différentes.

- **Omitted StackPanel.Children élément de propriété:** <xref:System.Windows.Controls.StackPanel> dérive de <xref:System.Windows.Controls.Panel>. <xref:System.Windows.Controls.Panel>définit <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> comme sa propriété de contenu XAML.

- **Élément d’objet UIElementCollection omis :** La <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> propriété prend <xref:System.Windows.Controls.UIElementCollection>le type <xref:System.Collections.IList>, qui met en œuvre . L’étiquette d’élément de la collection peut être omise, basée <xref:System.Collections.IList>sur les règles XAML pour le traitement des collections telles que . (Dans ce <xref:System.Windows.Controls.UIElementCollection> cas, en fait, ne peut pas être instantanée parce qu’il n’expose pas un constructeur sans paramètres, et c’est pourquoi l’élément <xref:System.Windows.Controls.UIElementCollection> objet est montré commenté).

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

### <a name="attribute-syntax-events"></a>Attribuer la syntaxe (événements)

La syntaxe des attributs peut également servir pour les membres qui sont des événements plutôt que des propriétés. Dans ce cas, le nom de l’attribut est le nom de l’événement. Dans l’implémentation WPF d’événements pour XAML, la valeur de l’attribut est le nom d’un gestionnaire qui implémente le délégué de l’événement. Par exemple, la balisage suivante <xref:System.Windows.Controls.Primitives.ButtonBase.Click> assigne <xref:System.Windows.Controls.Button> un gestionnaire pour l’événement à un majoré créé dans le balisage :

[!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]

Il existe plus d’événements et de code XAML dans WPF que cet exemple de syntaxe des attributs. Par exemple, vous vous demandez peut-être ce que le `ClickHandler` référencé ici représente et comment il est défini. Cela sera expliqué dans la section événements à venir [et XAML code-derrière](#events-and-xaml-code-behind) de cet article.

## <a name="case-and-white-space-in-xaml"></a>Cas et espace blanc dans XAML

En général, XAML est sensible aux cas. Aux fins de la résolution des types de support, WPF XAML est sensible aux cas par les mêmes règles que le CLR est sensible aux cas. Les éléments objet, les éléments de propriété et les noms d’attribut doivent tous être spécifiés en respectant la casse quand leurs noms sont comparés au type sous-jacent dans l’assembly ou à un membre d’un type. Les mots-clés en langue XAML et les primitifs sont également sensibles aux cas. Les valeurs ne sont pas toujours sensibles aux cas. Pour les valeurs, le respect de la casse varie selon le comportement du convertisseur de type associé à la propriété qui prend la valeur ou le type de valeur de la propriété. Par exemple, les <xref:System.Boolean> propriétés qui `true` `True` prennent le type peuvent prendre l’une ou l’autre ou <xref:System.Boolean> comme valeurs équivalentes, mais seulement parce que la conversion native de type de parser WPF XAML pour la chaîne permet déjà ces équivalents.

Les processeurs et sérialisateurs WPF XAML ignoreront ou laisseront tomber tous les espaces blancs non significatifs, et normaliseront tout espace blanc important. Ceci est compatible avec les recommandations par défaut de comportement de l’espace blanc de la spécification XAML. Ce comportement n’est de conséquence que lorsque vous spécifiez des chaînes dans les propriétés de contenu XAML. En termes simples, XAML convertit l’espace, l’alimentation en ligne et les caractères d’onglets en espaces, puis préserve un espace s’il est trouvé à chaque extrémité d’une chaîne contigu. L’explication complète de la manipulation de l’espace blanc XAML n’est pas couverte dans cet article. Pour plus d’informations, voir [traitement de l’espace blanc dans XAML](../xaml-services/white-space-processing.md).

## <a name="markup-extensions"></a>Extensions de balisage

Les extensions de balisage forment un concept de langage XAML. Lorsqu’elles sont utilisées pour fournir la valeur d’une syntaxe d’attributs, les accolades (`{` et `}`) indiquent une extension de balisage. Cette utilisation ordonne au traitement XAML de se soustraire au traitement général des valeurs d’attribut, soit en tant que chaîne littérale, soit en tant que valeur convertible en chaîne.

Les extensions de balisage les plus [`Binding`](../../framework/wpf/advanced/binding-markup-extension.md)courantes utilisées dans la programmation [`StaticResource`](../../framework/wpf/advanced/staticresource-markup-extension.md) d’applications WPF sont , utilisées pour les expressions de liaison de données, et les références de ressources et [`DynamicResource`](../../framework/wpf/advanced/dynamicresource-markup-extension.md). Grâce aux extensions de balisage, vous pouvez utiliser la syntaxe d’attributs pour fournir des valeurs aux propriétés, même si en général cette propriété ne prend pas en charge cette syntaxe. Les extensions de balisage utilisent souvent des types d’expression intermédiaire pour activer des fonctionnalités telles que le report de valeurs ou le référencement d’autres objets qui ne sont présents qu’à l’heure d’exécution.

Par exemple, la balisage suivante <xref:System.Windows.FrameworkElement.Style%2A> définit la valeur de la propriété à l’aide de la syntaxe d’attribut. La <xref:System.Windows.FrameworkElement.Style%2A> propriété prend un <xref:System.Windows.Style> exemple de la classe, qui par défaut ne pouvait pas être instantanée par une chaîne de syntaxe d’attribut. Mais dans ce cas, l’attribut fait `StaticResource`référence à une extension de balisage particulière, . Lorsque cette extension de balisage est traitée, elle retourne une référence à un style qui a été instancié précédemment en tant que ressource indexée dans un dictionnaire de ressources.

[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources)]
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources2](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources2)]
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources3](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources3)]

Pour obtenir la liste de référence de toutes les extensions de balisage XAML spécifiquement implémentées dans WPF, consultez [Extensions XAML WPF](../../framework/wpf/advanced/wpf-xaml-extensions.md). Pour une liste de référence des extensions de balisage qui sont définies par System.Xaml et sont plus largement disponibles pour .NET Core XAML implémentations, voir [XAML Namespace (x:) Caractéristiques linguistiques](../xaml-services/namespace-language-features.md). Pour plus d’informations sur les concepts d’extension de balisage, consultez [Extensions de balisage et XAML WPF](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).

## <a name="type-converters"></a>Convertisseurs de type

La section [Syntaxe XAML en bref](#xaml-syntax-in-brief) indique que la valeur d’attribut doit pouvoir être définie par une chaîne. La manipulation de base et native de la façon dont les cordes <xref:System.String> sont converties en d’autres types <xref:System.DateTime> <xref:System.Uri>d’objets ou de valeurs primitives est basée sur le type lui-même, en plus du traitement indigène pour certains types tels que ou . Mais de nombreux types de WPF ou les membres de ces types étendent le comportement de traitement de l’attribut de chaîne de base de telle sorte que les cas de types d’objets plus complexes peuvent être spécifiés comme des chaînes et des attributs.

La <xref:System.Windows.Thickness> structure est un exemple d’un type qui a une conversion de type activée pour les utilisations XAML. <xref:System.Windows.Thickness>indique des mesures dans un rectangle imbriqué et <xref:System.Windows.FrameworkElement.Margin%2A>est utilisé comme valeur pour des propriétés telles que . En plaçant un convertisseur de type <xref:System.Windows.Thickness> <xref:System.Windows.Thickness> sur , toutes les propriétés qui utilisent un sont plus faciles à spécifier dans XAML parce qu’ils peuvent être spécifiés comme attributs. L’exemple suivant utilise une conversion type et attribue <xref:System.Windows.FrameworkElement.Margin%2A>la syntaxe pour fournir une valeur pour un :

[!code-xaml[XAMLOvwSupport#MarginTCE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#margintce)]

L’exemple précédent de syntaxe d’attribut est équivalent <xref:System.Windows.FrameworkElement.Margin%2A> à l’exemple plus verbeux <xref:System.Windows.Thickness> de syntaxe suivant, où le est plutôt placé par la syntaxe d’élément de propriété contenant un élément d’objet. Les quatre propriétés clés sont <xref:System.Windows.Thickness> définies comme attributs sur la nouvelle instance :

[!code-xaml[XAMLOvwSupport#MarginVerbose](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#marginverbose)]

> [!NOTE]
> Il existe également un nombre limité d’objets où la conversion de type est la seule façon publique de définir une propriété à ce type sans impliquer une sous-classe, parce que le type lui-même n’a pas un constructeur sans paramètres. par exemple <xref:System.Windows.Input.Cursor>.

Pour plus d’informations sur la conversion de type, voir [TypeConverters et XAML](../../framework/wpf/advanced/typeconverters-and-xaml.md).

## <a name="xaml-root-elements-and-xaml-namespaces"></a>Éléments racines XAML et espaces de nom XAML

Un fichier XAML doit n’avoir qu’un seul élément racine, afin d’être à la fois un fichier XML bien formé et un fichier XAML valide. Pour les scénarios WPF typiques, vous utilisez un élément racine qui a <xref:System.Windows.Window> une <xref:System.Windows.Controls.Page> signification importante <xref:System.Windows.ResourceDictionary> dans le modèle <xref:System.Windows.Application> d’application WPF (par exemple, ou pour une page, pour un dictionnaire externe, ou pour la définition de l’application). L’exemple suivant montre l’élément racine d’un fichier XAML typique <xref:System.Windows.Controls.Page>pour une page WPF, avec l’élément racine de .

[!code-xaml[XAMLOvwSupport#RootOnly](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly)]
[!code-xaml[XAMLOvwSupport#RootOnly2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly2)]

L’élément racine contient également les attributs `xmlns` et `xmlns:x`. Ces attributs indiquent à un processeur XAML les espaces de noms XAML contenant les définitions de types pour les types de stockage qui vont être référencés en tant qu’éléments par le balisage. L’attribut `xmlns` indique explicitement l’espace de noms XAML par défaut. Dans l’espace de noms XAML par défaut, les éléments objet dans le balisage peuvent être spécifiés sans préfixe. Pour la plupart des scénarios d’applications WPF, et pour presque tous les exemples donnés dans les sections WPF `http://schemas.microsoft.com/winfx/2006/xaml/presentation`du SDK, l’espace de nom XAML par défaut est cartographié sur l’espace de nom WPF . L’attribut `xmlns:x` indique un espace de noms XAML supplémentaire qui mappe l’espace de noms du langage XAML `http://schemas.microsoft.com/winfx/2006/xaml`.

Cette utilisation de `xmlns` pour définir une étendue de l’utilisation et le mappage d’une portée de nom est conforme à la spécification XML 1.0. Les portées de nom XAML se distinguent des portées de nom XML uniquement parce qu’elles renseignent aussi sur la façon dont les éléments de la portée de nom sont stockés par les types lors d’une résolution de type et d’une analyse du code XAML.

Les `xmlns` attributs ne sont strictement nécessaires que sur l’élément racine de chaque fichier XAML. Les définitions `xmlns` s’appliquent à tous les éléments descendants de l’élément racine (ce comportement est encore une fois conforme à la spécification XML 1.0 pour `xmlns`), tandis que les attributs `xmlns` sont également autorisés sur d’autres éléments situés sous la racine et s’appliquent à tous les éléments descendants de l’élément de définition. Toutefois, si vous définissez/redéfinissez fréquemment les espaces de noms XAML, le style de balisage XAML peut devenir difficile à lire.

La mise en œuvre de son processeur XAML par le WPF comprend une infrastructure qui est au sens des assemblages de base du WPF. Les assemblages de base WPF sont connus pour contenir les types qui prennent en charge les cartes WPF à l’espace de nom XAML par défaut. Cette option est activée par le biais de la configuration faisant partie du fichier de build de votre projet et des systèmes de projet et de build WPF. Par conséquent, déclarer l’espace de nom `xmlns` XAML par défaut comme par défaut est tout ce qui est nécessaire afin de référencer les éléments XAML qui proviennent d’assemblages WPF.

### <a name="the-x-prefix"></a>Le x: préfixe

Dans l’exemple d’élément racine précédent, le préfixe `x:` a été utilisé pour mapper l’espace de noms XAML `http://schemas.microsoft.com/winfx/2006/xaml`, qui est l’espace de noms XAML dédié prenant en charge les constructions du langage XAML. Ce `x:` préfixe est utilisé pour cartographier cet espace de nom XAML dans les modèles de projets, par exemple et en documentation tout au long de ce SDK. L’espace de nom XAML pour la langue XAML contient plusieurs constructions de programmation que vous utiliserez fréquemment dans votre XAML. Voici une liste de constructions de programmation avec le préfixe `x:` parmi les plus courantes que vous allez utiliser :

- [x:Key](../xaml-services/xkey-directive.md): Définit une clé unique <xref:System.Windows.ResourceDictionary> pour chaque ressource dans un (ou des concepts de dictionnaire similaires dans d’autres cadres). `x:Key`représentera probablement 90 pour `x:` cent des utilisations que vous verrez dans le balisage d’une application WPF typique.

- [x:Classe](../xaml-services/xclass-directive.md): Specifie l’espace de nom CLR et le nom de classe pour la classe qui fournit un code-behind pour une page XAML. Vous devez disposer d’une telle classe pour prendre en charge le code-behind selon le modèle de programmation WPF, et c’est la raison pour laquelle vous voyez presque toujours `x:` mappé, même s’il n’ y a aucune ressource.

- [x:Name](../xaml-services/xname-directive.md) : spécifie un nom d’objet d’exécution pour l’instance qui existe dans le code d’exécution après le traitement d’un élément objet. En général, vous êtes amené à utiliser fréquemment une propriété équivalente définie par WPF pour [x:Name](../xaml-services/xname-directive.md). Ces propriétés cartographient spécifiquement une propriété de support CLR et sont donc plus pratiques pour la programmation d’applications, où vous utilisez fréquemment le code de temps d’exécution pour trouver les éléments nommés de XAML initialisé. La propriété la <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>plus commune est . Vous pouvez toujours utiliser [x:Nom](../xaml-services/xname-directive.md) lorsque la <xref:System.Windows.FrameworkElement.Name%2A> propriété équivalente au niveau cadre WPF n’est pas prise en charge dans un type particulier. Ce cas se présente dans certains scénarios d’animation.

- [x:Static](../xaml-services/xstatic-markup-extension.md) : active une référence qui retourne une valeur statique qui, sinon, n’est pas une propriété compatible XAML.

- [x:Type](../xaml-services/xtype-markup-extension.md): Construit <xref:System.Type> une référence basée sur un nom de type. Ceci est utilisé pour spécifier les attributs <xref:System.Type>qui prennent , tels <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>que , bien que souvent la propriété a native chaîne à<xref:System.Type> conversion de telle sorte que [l’utilisation x:Type](../xaml-services/xtype-markup-extension.md) extension de balisage est facultative.

Il existe d’autres constructions de programmation dans l’espace de noms XAML à préfixe `x:` qui ne sont pas aussi courantes. Pour plus d’informations, consultez [Fonctionnalités de langage pour les espaces de noms XAML (x:)](../xaml-services/namespace-language-features.md).

## <a name="custom-prefixes-and-custom-types-in-xaml"></a>Préfixes personnalisés et types personnalisés dans XAML

Pour vos propres assemblages personnalisés, ou pour les assemblages en dehors du noyau WPF de **PresentationCore** `xmlns` , **PresentationFramework** et **WindowsBase**, vous pouvez spécifier l’assemblage dans le cadre d’une cartographie personnalisée. Vous pouvez ensuite référencer des types depuis cet assembly dans votre XAML à partir du moment où le type voulu est correctement implémenté pour prendre en charge les utilisations XAML que vous essayez.

Ce qui suit est un exemple de base de la façon dont les préfixes personnalisés fonctionnent dans le balisage XAML. Le préfixe `custom` est défini dans l’étiquette de l’élément racine, et cartographié à un assemblage spécifique qui est emballé et disponible avec l’application. Cet assembly contient un type `NumericUpDown`, qui est implémenté pour prendre en charge l’utilisation générale de XAML ainsi que l’utilisation d’un héritage de classe, autorisant son insertion à ce stade dans un modèle de contenu XAML WPF. Une instance de ce contrôle `NumericUpDown` est déclaré comme élément objet en utilisant le préfixe afin qu’un analyseur XAML identifie quel espace de noms XAML contient le type et par conséquent l’emplacement de l’assembly de stockage contenant la définition de type.

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

Pour plus d’informations sur la façon dont les espaces de noms XML et les espaces nominaux de code dans les assemblages sont liés, voir [XAML Namespaces et Namespace Mapping pour WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).

## <a name="events-and-xaml-code-behind"></a>Événements et XAML en retard

La plupart des applications WPF se composent à la fois de balisage XAML et de code-derrière. Dans un projet, le XAML `.xaml` est écrit sous forme de fichier, et une langue CLR comme Microsoft Visual Basic ou C est utilisée pour écrire un fichier de code.derrière. Lors de la compilation du balisage d’un fichier XAML comme partie intégrante des modèles de programmation et d’application WPF, l’emplacement du fichier code-behind XAML pour un fichier XAML est identifié en spécifiant un espace de noms et une classe en tant qu’attribut `x:Class` de l’élément racine du XAML.

Jusqu’ici dans les exemples étudiés, vous avez vu plusieurs boutons, mais aucun d’eux n’avait encore de comportement logique qui lui était associé. Le mécanisme principal de niveau d’application pour ajouter un comportement pour un élément d’objet est d’utiliser un événement existant de la classe d’éléments, et d’écrire un gestionnaire spécifique pour cet événement qui est invoqué lorsque cet événement est soulevé au moment de la course. Le nom de l’événement et celui du gestionnaire à utiliser sont spécifiés dans le balisage, tandis que le code qui implémente le gestionnaire est défini dans le fichier code-behind.

[!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]

[!code-csharp[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml.cs#buttonwithcodebehindhandler)]
[!code-vb[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#buttonwithcodebehindhandler)]

Notez que le fichier code-behind utilise l’espace de noms CLR `ExampleNamespace` et déclare `ExamplePage` comme une classe partielle dans cet espace de noms. Cela correspond à la valeur d’attribut `x:Class` de `ExampleNamespace`.`ExamplePage` qui a été fournie dans la racine de la balise. Le compilateur de balisage WPF crée une classe partielle pour tout fichier XAML compilé, en dérivant une classe à partir du type d’élément racine. Lorsque vous fournissez un code-derrière qui définit également la même classe partielle, le code résultant est combiné dans le même espace de nom et la classe de l’application compilée.

Pour plus d’informations sur les exigences de la programmation de code-derrière dans WPF, voir [Code-behind, Event Handler, et Partial Class Requirements dans WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md#code-behind-event-handler-and-partial-class-requirements-in-wpf).

Si vous ne souhaitez pas créer de fichier code-behind distinct, vous pouvez également incorporer votre code dans un fichier XAML. Toutefois, le code incorporé est une technique moins flexible qui présente des limitations importantes. Pour plus d’informaiton, voir [Code-Behind et XAML dans WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).

### <a name="routed-events"></a>Événements routés

Une caractéristique particulière de l’événement qui est fondamentale pour WPF est un événement acheminé. Les événements routés permettent à un élément de gérer un événement déclenché par un élément différent, tant que ces éléments sont connectés via une relation d’arborescence. Lorsque vous spécifiez la gestion des événements avec un attribut XAML, vous pouvez écouter et géré l’événement routé sur n’importe quel élément, notamment les éléments qui ne listent pas cet événement particulier dans la table des membres de la classe. Pour cela, vous devez qualifier l’attribut de nom d’événement avec le nom de la classe propriétaire. Par exemple, `StackPanel` le parent `StackPanel`  /  `Button` dans l’exemple en cours pourrait <xref:System.Windows.Controls.Primitives.ButtonBase.Click> enregistrer un gestionnaire `Button.Click` pour `StackPanel` l’événement du bouton élément enfant en spécifiant l’attribut sur l’élément objet, avec votre nom de gestionnaire comme valeur d’attribut. Pour plus d’informations, voir [Aperçu des événements acheminés](../../framework/wpf/advanced/routed-events-overview.md).

## <a name="xaml-named-elements"></a>XAML nommé éléments

Par défaut, l’instance d’objet qui est créée par le traitement d’un élément objet XAML dans un graphique d’objet n’a pas d’identificateur unique ni de référence d’objet. En revanche, si vous appelez un constructeur dans le code, vous utilisez presque toujours le résultat du constructeur pour définir une variable sur l’instance construite, afin de pouvoir référencer l’instance ultérieurement dans votre code. Pour fournir un accès standardisé aux objets créés via une définition de balise, XAML définit l’[attribut x:Name](../xaml-services/xname-directive.md). Vous pouvez définir la valeur de l’attribut `x:Name` sur n’importe quel élément objet. Dans votre code-behind, l’identificateur que vous choisissez équivaut à une variable d’instance qui fait référence à l’instance construite. À tous égards, les éléments nommés fonctionnent comme s’il s’agissait d’instances d’objets (les références nominatifs de cette instance), et votre code-derrière peut faire référence aux éléments nommés pour gérer les interactions en temps d’exécution au sein de l’application. Ce lien entre les instances et les variables est accompli par le compilateur de <xref:System.Windows.Markup.IComponentConnector.InitializeComponent%2A> balisage WPF XAML, et plus précisément impliquer des fonctionnalités et des modèles tels que cela ne sera pas discuté en détail dans cet article.

Les éléments XAML de niveau <xref:System.Windows.FrameworkElement.Name%2A> cadre WPF héritent d’une propriété, ce qui équivaut à l’attribut défini `x:Name` XAML. Certaines autres classes fournissent également des équivalents de niveau propriété pour `x:Name`, qui est aussi généralement défini en tant que propriété `Name`. En règle générale, si vous ne trouvez pas une propriété `Name` dans la table des membres pour votre élément/type choisi, utilisez `x:Name` à la place. Les `x:Name` valeurs fourniront un identifiant à un élément XAML qui peut être utilisé à l’heure de pointe, soit par des sous-systèmes spécifiques ou par des méthodes d’utilité telles que <xref:System.Windows.FrameworkElement.FindName%2A>.

L’exemple <xref:System.Windows.FrameworkElement.Name%2A> suivant <xref:System.Windows.Controls.StackPanel> s’inse place sur un élément. Ensuite, un gestionnaire <xref:System.Windows.Controls.Button> sur <xref:System.Windows.Controls.StackPanel> un <xref:System.Windows.Controls.StackPanel> intérieur qui `buttonContainer` fait <xref:System.Windows.FrameworkElement.Name%2A>référence à travers sa référence d’instance tel qu’établi par .

[!code-xaml[XAMLOvwSupport#NamedE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede)]
[!code-xaml[XAMLOvwSupport#NamedE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede2)]

[!code-csharp[XAMLOvwSupport#NameCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml.cs#namecode)]
[!code-vb[XAMLOvwSupport#NameCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#namecode)]

Tout comme une variable, le nom XAML d’une instance est régi par un concept de portée afin que les noms puissent être appliqués pour être uniques dans une certaine étendue qui est prévisible. La balisage principal qui définit une page désigne une portée de nom XAML unique, avec pour élément racine de cette page, les limites de portée de nom XAML. Cependant, d’autres sources de balisage peuvent interagir avec une page à l’heure d’exécution, tels que les styles ou les modèles dans les styles, et ces sources de balisage ont souvent leurs propres namescopes XAML qui ne se connectent pas nécessairement avec le namescope XAML de la page. Pour plus `x:Name` d’informations sur et XAML namescopes, voir <xref:System.Windows.FrameworkElement.Name%2A>, [x:Name Directive](../xaml-services/xname-directive.md), ou [WPF XAML Namescopes](../../framework/wpf/advanced/wpf-xaml-namescopes.md).

## <a name="attached-properties-and-attached-events"></a>Propriétés ci-jointes et événements attachés

Le langage XAML comporte une fonctionnalité de langage qui permet à certaines propriétés ou événements d’être spécifiés sur n’importe quel élément, et cela même si la propriété ou l’événement existe dans les définitions de type pour l’élément sur lequel il est défini. La version des propriétés de cette fonctionnalité est appelée une propriété jointe, et la version des événements, un événement attaché. D’un point de vue conceptuel, vous pouvez considérer les propriétés jointes et les événements attachés comme des membres globaux pouvant être définis sur n’importe quelle instance d’élément ou d’objet XAML. Toutefois, cet élément/cette classe ou une infrastructure plus importante doit prendre en charge une banque de propriétés de stockage pour les valeurs attachées.

Les propriétés jointes en XAML sont généralement utilisées dans la syntaxe d’attributs. Dans la syntaxe d’attribut, `ownerType.propertyName`vous spécifiez une propriété attachée sous la forme .

Superficiellement, cela ressemble à une utilisation d’élément de propriété, mais dans ce cas, le `ownerType` vous spécifiez est toujours un type différent de l’élément objet où la propriété ci-jointe est définie. `ownerType`est le type qui fournit les méthodes d’accesseur qui sont nécessaires par un processeur XAML afin d’obtenir ou de définir la valeur de propriété ci-jointe.

Le scénario le plus courant pour les propriétés jointes consiste à permettre aux éléments enfants de signaler une valeur de propriété à leur élément parent.

L’exemple suivant <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> illustre la propriété ci-jointe. La <xref:System.Windows.Controls.DockPanel> classe définit les <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> accesseurs pour et possède donc la propriété ci-jointe. La <xref:System.Windows.Controls.DockPanel> classe comprend également la logique qui itère ses éléments enfant <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>et vérifie spécifiquement chaque élément pour une valeur définie de . Si une valeur est trouvée, cette valeur est utilisée au cours de la disposition pour positionner les éléments enfants. L’utilisation <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> de la propriété ci-jointe et de cette <xref:System.Windows.Controls.DockPanel> capacité de positionnement est en fait le scénario motivant pour la classe.

[!code-xaml[XAMLOvwSupport#DockAP](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#dockap)]

Dans WPF, la plupart ou la totalité des propriétés ci-jointes sont également mises en œuvre comme propriétés de dépendance. Pour plus d’informations, consultez [Vue d’ensemble des propriétés jointes](../../framework/wpf/advanced/attached-properties-overview.md).

Les événements ci-joints utilisent une forme similaire `ownerType.eventName` de syntaxe d’attribut. À l’instar des événements non attachés, la valeur d’attribut d’un événement attaché en XAML spécifie le nom de la méthode de gestionnaire qui est appelée lorsque l’événement est géré sur l’élément. Les utilisations d’événements attachés en XAML WPF sont moins courantes. Pour plus d’informations, consultez [Vue d’ensemble des événements attachés](../../framework/wpf/advanced/attached-events-overview.md).

## <a name="base-types-and-xaml"></a>Types de base et XAML

Sous-jacent WPF XAML et son espace de nom XAML est une collection de types qui correspondent à des objets CLR en plus des éléments de balisage pour XAML. Cela étant, toutes les classes ne peuvent pas être mappées aux éléments. Les classes abstraites, telles que <xref:System.Windows.Controls.Primitives.ButtonBase>, et certaines classes de base non abstraites, sont utilisées pour l’héritage dans le modèle d’objets CLR. Les classes de base, y compris abstraites, sont toujours importantes pour le développement en XAML, car chacun des éléments XAML concrets hérite de membres provenant d’une classe de base dans sa hiérarchie. Ces membres incluent souvent des propriétés qui peuvent être définies en tant qu’attributs sur l’élément, ou comme événements qui peuvent être gérés. <xref:System.Windows.FrameworkElement>est la classe d’assurance-chômage de base en béton de WPF au niveau du cadre WPF. Lors de la conception de l’interface utilisateur, vous utiliserez diverses classes <xref:System.Windows.FrameworkElement>de forme, de panneau, de décorateur ou de contrôle, qui dérivent toutes de . Une classe de <xref:System.Windows.FrameworkContentElement>base connexe, , prend en charge les éléments axés sur les documents <xref:System.Windows.FrameworkElement>qui fonctionnent bien pour une présentation de mise en page de flux, en utilisant des API qui reflètent délibérément les API dans . La combinaison d’attributs au niveau de l’élément et d’un modèle d’objet CLR vous fournit un ensemble de propriétés communes qui sont définies sur la plupart des éléments XAML en béton, quel que soit l’élément XAML spécifique et son type sous-jacent.

## <a name="xaml-security"></a>Sécurité XAML

Le XAML est un langage de balisage qui représente directement l’instanciation d’objets et leur exécution. Ainsi, les éléments créés en XAML ont la même capacité d’interagir avec les ressources système (accès réseau, e/s de système de fichiers, par exemple) que le code généré équivalent. XAML chargé dans une application de confiance a le même accès aux ressources du système que l’application d’hébergement ne.

### <a name="code-access-security-cas-in-wpf"></a>Code Access Security (CAS) dans WPF

**Cette section ne s’applique qu’au cadre .NET. WPF pour .NET Core ne prend pas en charge LE TAS. Pour plus d’informations, voir [les différences de sécurité d’accès](../migration/differences-from-net-framework.md#code-access-security)au code .**

WPF pour .NET Framework prend en charge la sécurité d’accès au Code (CAS). Cela signifie que le contenu WPF en cours d’exécution dans la zone Internet a réduit les autorisations d’exécution. "Loose XAML" (pages de XAML non compilée interprétée au moment de la charge par un spectateur XAML) et XBAP sont généralement exécutés dans cette zone Internet et utilisent le même ensemble d’autorisation. Toutefois, le XAML chargé dans une application d’un niveau de confiance totale dispose du même accès aux ressources système que l’application d’hébergement. Pour plus d’informations, consultez [Sécurité de confiance partielle de WPF](../../framework/wpf/wpf-partial-trust-security.md).

## <a name="loading-xaml-from-code"></a>Chargement de XAML à partir du code

Vous utilisez XAML pour définir l’ensemble de l’interface utilisateur, mais il est parfois également judicieux de ne définir qu’une partie de l’interface utilisateur en XAML. Vous pouvez vous servir de cette fonctionnalité pour activer la personnalisation partielle, un stockage local des informations, et utiliser XAML pour fournir un objet métier ou une variété de scénarios possibles. La clé de ces <xref:System.Windows.Markup.XamlReader> scénarios est <xref:System.Windows.Markup.XamlReader.Load%2A> la classe et sa méthode. L’entrée est un fichier XAML, et la sortie un objet représentant l’intégralité de l’arborescence d’exécution des objets qui a été créée à partir de ce balisage. Vous pouvez ensuite insérer l’objet pour être une propriété d’un autre objet qui existe déjà dans l’application. Tant que la propriété est une propriété appropriée dans le modèle de contenu qui a des capacités d’affichage éventuelles et qui informera le moteur d’exécution que le nouveau contenu a été ajouté dans l’application, vous pouvez modifier le contenu d’une application en cours d’exécution facilement en chargeant dans XAML. Pour .NET Framework, cette capacité n’est généralement disponible que dans les applications en pleine confiance, en raison des implications évidentes en matière de sécurité du chargement des fichiers dans les applications au fur et à mesure qu’elles s’exécutent.

## <a name="see-also"></a>Voir aussi

- [Syntaxe XAML en détail](../../framework/wpf/advanced/xaml-syntax-in-detail.md)
- [XAML et classes personnalisées pour WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [Espace de noms XAML (x:) Fonctionnalités de langage](../xaml-services/namespace-language-features.md)
- [Extensions XAML WPF](../../framework/wpf/advanced/wpf-xaml-extensions.md)
- [Vue d'ensemble des éléments de base](../../framework/wpf/advanced/base-elements-overview.md)
- [Arborescences dans WPF](../../framework/wpf/advanced/trees-in-wpf.md)
