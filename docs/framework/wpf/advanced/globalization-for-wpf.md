---
title: Globalisation
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
ms.openlocfilehash: 95c0368889dfa4e69b5e40b32ea19ba845aa5c30
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747053"
---
# <a name="globalization-for-wpf"></a>Globalisation pour WPF
Cette rubrique présente les problèmes que vous devez prendre en compte lors de l’écriture d’applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pour le marché mondial. Les éléments de programmation de la globalisation sont définis dans .NET dans l’espace de noms <xref:System.Globalization>.

<a name="xaml_globalization"></a>
## <a name="xaml-globalization"></a>Globalisation XAML
 Extensible Application Markup Language (XAML) est basé sur XML et tire parti de la prise en charge de la globalisation définie dans la spécification XML. Les sections suivantes décrivent certaines fonctionnalités de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que vous devez connaître.

<a name="char_reference"></a>
### <a name="character-references"></a>Références de caractères
Une référence de caractère donne l’unité de code UTF16 du caractère Unicode particulier qu’elle représente, en notation décimale ou hexadécimale. L’exemple suivant montre une référence de caractère décimale pour la lettre majuscule du copte HORI, ou « Ϩ » :

```
&#1000;
```

L’exemple suivant montre une référence de caractère hexadécimale. Notez qu’il a un **x** devant le nombre hexadécimal.

```
&#x3E8;
```

<a name="encoding"></a>
### <a name="encoding"></a>Encodage
 L’encodage pris en charge par [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est ASCII, Unicode UTF-16 et UTF-8. L’instruction Encoding se trouve au début de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] document. Si aucun attribut d’encodage ni ordre d’octets n’existe, la valeur UTF-8 est affectée par défaut à l’analyseur. UTF-8 et UTF-16 sont les encodages par défaut. UTF-7 n’est pas pris en charge. L’exemple suivant montre comment spécifier un encodage UTF-8 dans un fichier [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

```xaml
?xml encoding="UTF-8"?
```

<a name="lang_attrib"></a>
### <a name="language-attribute"></a>Attribut de langue
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilise [XML : lang](../../../desktop-wpf/xaml-services/xml-language-handling.md) pour représenter l’attribut de langage d’un élément.  Pour tirer parti de la classe <xref:System.Globalization.CultureInfo>, la valeur de l’attribut Language doit être l’un des noms de culture prédéfinis par <xref:System.Globalization.CultureInfo>. [xml:lang](../../../desktop-wpf/xaml-services/xml-language-handling.md) peut être hérité dans l’arborescence d’éléments (par les règles XML, pas nécessairement à cause de l’héritage de propriétés de dépendance) et sa valeur par défaut est une chaîne vide s’il n’est pas assigné explicitement.

 L’attribut de langue est très utile pour spécifier des dialectes. Par exemple, le français présente des différences orthographiques, lexicales et phonologiques en fonction de la zone géographique dans laquelle il est utilisé : en France, au Québec, en Belgique ou en Suisse. En outre, le chinois, le japonais et le coréen partagent des points de code en Unicode, mais les formes idéographiques sont différentes et utilisent des polices totalement différentes.

 L’exemple de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] suivant utilise l’attribut `fr-CA` Language pour spécifier le français canadien.

```xaml
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>
```

<a name="unicode"></a>
### <a name="unicode"></a>Unicode
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] prend en charge toutes les fonctionnalités Unicode, y compris les substituts. Tant que le jeu de caractères peut être mappé au format Unicode, il est pris en charge. Par exemple, le jeu de caractères GB18030 comprend quelques caractères mappés aux extensions A et B et aux paires de substitution du chinois, du japonais et du coréen (CFK) ; par conséquent, il est totalement pris en charge. Une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] peut utiliser <xref:System.Globalization.StringInfo> pour manipuler des chaînes sans savoir s’ils ont des paires de substitution ou des caractères d’association.

<a name="design_intl_ui_with_xaml"></a>
## <a name="designing-an-international-user-interface-with-xaml"></a>Conception d’une interface utilisateur internationale avec le langage XAML
 Cette section décrit [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] fonctionnalités que vous devez prendre en compte lors de l’écriture d’une application.

<a name="intl_text"></a>
### <a name="international-text"></a>Texte international
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] intègre un traitement intégré pour tous les systèmes d’écriture Microsoft .NET Framework pris en charge.

 Les scripts suivants sont pris en charge :

- Arabe

- Bengali

- Dévanâgarî

- Cyrillique

- Grec

- Gujarati

- Gurmukhi

- Hébreu

- Scripts idéographiques

- Kannada

- Lao

- Latin

- Malayalam

- Mongol

- Odia

- Syriaque

- Tamoul

- Télougou

- Tana

- Thaï*

- Tibétain

 *Cette version prend en charge l’affichage et la modification de texte thaïlandais, mais pas la césure de mots.

 Les scripts suivants ne sont pas pris en charge :

- Khmer

- Hangûl (ancien coréen)

- Myanmar

- Cingalais

 Tous les moteurs de système d’écriture prennent en charge les polices OpenType. Les polices OpenType peuvent inclure les tableaux de disposition OpenType qui permettent aux créateurs de polices de concevoir de meilleures polices typographiques internationales et haut de gamme. Les tableaux de disposition des polices OpenType contiennent des informations sur les substitutions de glyphe, le positionnement des glyphes, la justification et le positionnement de la ligne de base, ce qui permet aux applications de traitement de texte d’améliorer la disposition du texte.

 Les polices OpenType permettent de gérer des jeux de glyphes volumineux à l’aide de l’encodage Unicode. Cet encodage est largement pris en charge au niveau international, comme les variantes de glyphes typographiques.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le rendu de texte est alimenté par la technologie de sous-pixel Microsoft ClearType, qui prend en charge l’indépendance de résolution. La lisibilité est ainsi considérablement améliorée et les documents haute qualité de style magazine peuvent être pris en charge pour tous les scripts.

<a name="intl_layout"></a>
### <a name="international-layout"></a>Disposition internationale
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] offre un moyen très pratique pour prendre en charge des dispositions horizontales, bidirectionnelles et verticales. Dans Presentation Framework, la propriété <xref:System.Windows.FrameworkElement.FlowDirection%2A> peut être utilisée pour définir la disposition. Les modèles de sens du déroulement sont les suivants :

- *LeftToRight* : disposition horizontale pour le latin, les langues d’Asie orientale, etc.

- *RightToLeft* : disposition bidirectionnelle pour l’arabe, l’hébreu, etc.

<a name="developing_localizable_apps"></a>
## <a name="developing-localizable-applications"></a>Développement d’applications localisables
 Quand vous écrivez une application destinée à être utilisée dans le monde entier, vous ne devez pas oublier que cette application doit être localisable. Les rubriques suivantes signalent certains éléments à prendre en compte.

<a name="mui"></a>
### <a name="multilingual-user-interface"></a>Interface utilisateur multilingue
 Les interfaces utilisateur multilingues (MUI) sont un support Microsoft permettant de basculer des interfaces utilisateur d’une langue à une autre. Une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise le modèle d’assembly pour prendre en charge MUI. Une application contient des assemblys indépendants de la langue ainsi que des assemblys de ressources satellites dépendants de la langue. Le point d’entrée est un .EXE managé dans l’assembly principal.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le chargeur de ressources tire parti du gestionnaire de ressources de l’infrastructure pour prendre en charge la recherche et le secours des ressources. Les assemblys satellites multilingues fonctionnent avec le même assembly principal. L’assembly de ressource chargé dépend de la <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> du thread actuel.

<a name="localizable_ui"></a>
### <a name="localizable-user-interface"></a>Interface utilisateur localisable
 les applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilisent [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pour définir leurs [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] permet aux développeurs de spécifier une hiérarchie d’objets avec un ensemble de propriétés et une logique. L’utilisation principale de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] consiste à développer des applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], mais elle peut être utilisée pour spécifier une hiérarchie d’objets common language runtime (CLR). La plupart des développeurs utilisent [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pour spécifier le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de leur application et utiliser un langage C# de programmation tel que pour réagir à l’interaction de l’utilisateur.

 Du point de vue de la ressource, un fichier de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] conçu pour décrire un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dépendant du langage est un élément de ressource et, par conséquent, son format de distribution final doit être localisable pour prendre en charge les langues internationales. Étant donné que [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ne peut pas gérer d’événements, de nombreuses applications [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] contiennent des blocs de code pour effectuer cette opération. Pour plus d’informations, consultez [vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md). Le code est supprimé et compilé en différents binaires lorsqu’un fichier [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est sous forme de jeton dans le formulaire BAML de XAML. Le formulaire BAML des fichiers, des images et d’autres types d’objets de ressources managées XAML est incorporé dans l’assembly des ressources satellites, pouvant être localisé dans d’autres langues, ou dans l’assembly principal, quand la localisation n’est pas nécessaire.

> [!NOTE]
> les applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prennent en charge toutes les ressources FrameworkCLR, y compris les tables de chaînes, les images, etc.

<a name="building_localizable_apps"></a>
### <a name="building-localizable-applications"></a>Génération d’applications localisables
 La localisation consiste à adapter un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] à différentes cultures. Pour rendre une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] localisable, les développeurs doivent générer toutes les ressources localisables dans un assembly de ressources. L’assembly de ressource est localisé dans différentes langues et le code-behind utilise l’API de gestion des ressources pour le chargement. L’un des fichiers requis pour une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est un fichier projet (. proj). Toutes les ressources que vous utilisez dans votre application doivent être comprises dans le fichier projet. Cette opération est illustrée dans l’exemple suivant, à partir d’un fichier .csproj.

```xml
<Resource Include="data\picture1.jpg"/>
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

 Pour utiliser une ressource dans votre application, instanciez un <xref:System.Resources.ResourceManager> et chargez la ressource que vous souhaitez utiliser. L'exemple suivant illustre la procédure à suivre pour réaliser cette opération.

 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

<a name="using_clickonce"></a>
## <a name="using-clickonce-with-localized-applications"></a>Utilisation de ClickOnce avec les applications localisées
 ClickOnce est une nouvelle technologie de déploiement Windows Forms qui sera livrée avec Visual Studio 2005. Cette technologie permet d’installer des applications et de mettre à niveau des applications web. Quand une application déployée avec ClickOnce est localisée, elle ne peut être affichée que sous la culture localisée. Par exemple, si une application déployée est localisée en japonais, elle ne peut être affichée que sur la version japonaise de Microsoft Windows, et non sur la version anglaise de Windows. Cela présente un problème, car il s’agit d’un scénario courant pour les utilisateurs japonais qui exécutent une version anglaise de Windows.

 La solution à ce problème consiste à définir l’attribut de secours de langue neutre. Un développeur d’applications peut également supprimer des ressources de l’assembly principal pour les placer dans un assembly satellite correspondant à une culture spécifique. Pour contrôler ce processus, utilisez le <xref:System.Resources.NeutralResourcesLanguageAttribute>. Le constructeur de la classe <xref:System.Resources.NeutralResourcesLanguageAttribute> a deux signatures, une qui prend un paramètre <xref:System.Resources.UltimateResourceFallbackLocation> pour spécifier l’emplacement où le <xref:System.Resources.ResourceManager> doit extraire les ressources de secours : assembly principal ou assembly satellite. L'exemple suivant montre comment utiliser l'attribut. Pour l’emplacement de secours ultime, le code amène l' <xref:System.Resources.ResourceManager> à rechercher les ressources dans le sous-répertoire « de » du répertoire de l’assembly en cours d’exécution.

```csharp
[assembly: NeutralResourcesLanguageAttribute(
    "de" , UltimateResourceFallbackLocation.Satellite)]
```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la globalisation et de la localisation WPF](wpf-globalization-and-localization-overview.md)
