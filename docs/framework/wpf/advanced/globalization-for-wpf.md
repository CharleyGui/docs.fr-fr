---
title: Globalisation pour WPF
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
ms.openlocfilehash: 46e7d9caf0bdf0be25a4ac76e96fe04d0e131ed1
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238574"
---
# <a name="globalization-for-wpf"></a>Globalisation pour WPF
Cette rubrique présente certains problèmes dont vous devez être conscient lors de l’écriture [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications pour le marché international. Les éléments de programmation de la globalisation sont définis dans [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] dans `System.Globalization`.

<a name="xaml_globalization"></a>
## <a name="xaml-globalization"></a>Globalisation XAML
 [!INCLUDE[TLA#tla_xaml#initcap](../../../../includes/tlasharptla-xamlsharpinitcap-md.md)] est basé sur [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] et tire parti de la prise en charge de la globalisation définie dans le [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] spécification. Les sections suivantes décrivent certaines [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fonctionnalités dont vous devez être conscient de.

<a name="char_reference"></a>
### <a name="character-references"></a>Références de caractères
Une référence de caractère donne l’unité de code UTF16 de particulier [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] représente, sous forme décimale ou hexadécimale de caractères. L’exemple suivant montre une référence de caractère décimale pour la LETTRE MAJUSCULE COPTE HORI, ou « Ϩ » :

```
&#1000;
```

L’exemple suivant montre une référence de caractère hexadécimale. Notez la présence d’un **x** devant le nombre hexadécimal.

```
&#x3E8;
```

<a name="encoding"></a>
### <a name="encoding"></a>Encodage
 L’encodage pris en charge par [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sont [!INCLUDE[TLA#tla_ascii](../../../../includes/tlasharptla-ascii-md.md)], [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] UTF-16 et UTF-8. L’instruction des encodages se trouve au début de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] document. Si aucun attribut d’encodage ni ordre d’octets n’existe, la valeur UTF-8 est affectée par défaut à l’analyseur. UTF-8 et UTF-16 sont les encodages par défaut. UTF-7 n’est pas pris en charge. L’exemple suivant montre comment spécifier un encodage UTF-8 dans un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier.

```
?xml encoding="UTF-8"?
```

<a name="lang_attrib"></a>
### <a name="language-attribute"></a>Attribut de langue
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilise [XML : lang](../../xaml-services/xml-lang-handling-in-xaml.md) pour représenter l’attribut de langue d’un élément.  Pour tirer parti de la <xref:System.Globalization.CultureInfo> (classe), la valeur d’attribut de langage doit être un des noms de cultures prédéfinis par <xref:System.Globalization.CultureInfo>. [xml:lang](../../xaml-services/xml-lang-handling-in-xaml.md) peut être hérité dans l’arborescence d’éléments (par les règles XML, pas nécessairement à cause de l’héritage de propriétés de dépendance) et sa valeur par défaut est une chaîne vide s’il n’est pas assigné explicitement.

 L’attribut de langue est très utile pour spécifier des dialectes. Par exemple, le français présente des différences orthographiques, lexicales et phonologiques en fonction de la zone géographique dans laquelle il est utilisé : en France, au Québec, en Belgique ou en Suisse. Chinois, japonais et coréen partagent également des points de code dans [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], mais les idéogrammes très différents et qu’ils utilisent des polices totalement différentes.

 Ce qui suit [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemple utilise le `fr-CA` attribut de langue pour spécifier le Français du Canada.

```xml
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>
```

<a name="unicode"></a>
### <a name="unicode"></a>Unicode
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] prend en charge tous les [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] fonctionnalités, dont les substituts. Tant que le jeu de caractères peut être mappé à [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], il est pris en charge. Par exemple, le jeu de caractères GB18030 comprend quelques caractères mappés aux extensions A et B et aux paires de substitution du chinois, du japonais et du coréen (CFK) ; par conséquent, il est totalement pris en charge. Un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application peut utiliser <xref:System.Globalization.StringInfo> pour manipuler des chaînes sans savoir si celles-ci contiennent des paires de substitution ou des caractères de non-espacement.

<a name="design_intl_ui_with_xaml"></a>
## <a name="designing-an-international-user-interface-with-xaml"></a>Conception d’une interface utilisateur internationale avec le langage XAML
 Cette section décrit [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] les fonctionnalités dont vous devez tenir compte lors de l’écriture d’une application.

<a name="intl_text"></a>
### <a name="international-text"></a>Texte international
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclut un traitement intégré pour l’écriture de Microsoft .NET Framework pris en charge tous les systèmes.

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

- Sinhala

 Système d’écriture moteurs prennent en charge [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] polices. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] polices peuvent inclure la [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] des tableaux de disposition qui permettent aux créateurs de polices de concevoir de meilleures polices typographiques internationales et haut de gamme. Le [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] tableaux de disposition de police contiennent des informations sur les substitutions de glyphe, positionnement de glyphes, justification et le positionnement de ligne de base, permettant aux applications de traitement de texte d’améliorer la disposition du texte.

 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] les polices permettent la gestion des glyphes volumineux définit à l’aide de [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] encodage. Cet encodage est largement pris en charge au niveau international, comme les variantes de glyphes typographiques.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rendu de texte est alimenté par [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] technologie de sous-pixel qui prend en charge l’indépendance de résolution. La lisibilité est ainsi considérablement améliorée et les documents haute qualité de style magazine peuvent être pris en charge pour tous les scripts.

<a name="intl_layout"></a>
### <a name="international-layout"></a>Disposition internationale
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] offre un moyen très pratique pour prendre en charge des dispositions horizontales, bidirectionnelles et verticales. Dans l’infrastructure de présentation la <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriété peut être utilisée pour définir la disposition. Les modèles de sens du déroulement sont les suivants :

- *LeftToRight* : disposition horizontale pour le latin, les langues d’Asie orientale, etc.

- *RightToLeft* : disposition bidirectionnelle pour l’arabe, l’hébreu, etc.

<a name="developing_localizable_apps"></a>
## <a name="developing-localizable-applications"></a>Développement d’applications localisables
 Quand vous écrivez une application destinée à être utilisée dans le monde entier, vous ne devez pas oublier que cette application doit être localisable. Les rubriques suivantes signalent certains éléments à prendre en compte.

<a name="mui"></a>
### <a name="multilingual-user-interface"></a>Interface utilisateur multilingue
 Interfaces MUI (Multilingual User) est un [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] prennent en charge pour le basculement de [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] d’une langue à l’autre. Un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application utilise le modèle assembly pour prendre en charge d’interface utilisateur multilingue. Une application contient des assemblys indépendants de la langue ainsi que des assemblys de ressources satellites dépendants de la langue. Le point d’entrée est un .EXE managé dans l’assembly principal.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] chargeur de ressource tire parti de la [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]du Gestionnaire de ressources pour prendre en charge la recherche de ressources et de secours. Les assemblys satellites multilingues fonctionnent avec le même assembly principal. L’assembly de ressources chargé dépend le <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> du thread actuel.

<a name="localizable_ui"></a>
### <a name="localizable-user-interface"></a>Interface utilisateur localisable
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] les applications utilisent [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pour définir leur [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] permet aux développeurs de spécifier une hiérarchie d’objets avec un ensemble de propriétés et une logique. La principale utilisation de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] consiste à développer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, mais il peut être utilisé pour spécifier une hiérarchie de n’importe quel [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objets. La plupart des développeurs [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pour spécifier l’application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] et utiliser un langage de programmation tel que c# pour réagir à une interaction utilisateur.

 À partir d’un point de vue des ressources, un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier conçu pour décrire un dépendant du langage [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] est un élément de ressource et par conséquent, son format de distribution final doit être localisable pour prendre en charge des langues internationales. Étant donné que [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ne peut pas gérer les événements de nombreux [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] applications contiennent des blocs de code pour ce faire. Pour plus d’informations, consultez [vue d’ensemble de XAML (WPF)](xaml-overview-wpf.md). Code est supprimé et compilé dans différents binaires quand un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier est tokenisé dans le formulaire BAML de XAML. Le formulaire BAML des fichiers, des images et d’autres types d’objets de ressources managées XAML est incorporé dans l’assembly des ressources satellites, pouvant être localisé dans d’autres langues, ou dans l’assembly principal, quand la localisation n’est pas nécessaire.

> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] les applications prennent en charge toutes les [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)] [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] ressources, y compris les tables de chaînes, images et ainsi de suite.

<a name="building_localizable_apps"></a>
### <a name="building-localizable-applications"></a>Génération d’applications localisables
 La localisation consiste à adapter un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] à différentes cultures. Pour rendre un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application localisable, les développeurs doivent générer toutes les ressources localisables dans un assembly de ressources. L’assembly de ressources est localisé dans différentes langues, et le code-behind utilise l’API de gestion des ressources à charger. Un des fichiers requis pour un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application est un fichier de projet (.proj). Toutes les ressources que vous utilisez dans votre application doivent être comprises dans le fichier projet. Cette opération est illustrée dans l’exemple suivant, à partir d’un fichier .csproj.

```xml
<Resource Include="data\picture1.jpg"/>
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

 Pour utiliser une ressource dans votre application instancier un <xref:System.Resources.ResourceManager> et chargez la ressource que vous souhaitez utiliser. L'exemple suivant illustre la procédure à suivre pour réaliser cette opération.

 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

<a name="using_clickonce"></a>
## <a name="using-clickonce-with-localized-applications"></a>Utilisation de ClickOnce avec les applications localisées
 ClickOnce est une nouvelle technologie de déploiement de Windows Forms qui sera fournie avec Visual Studio 2005. Cette technologie permet d’installer des applications et de mettre à niveau des applications web. Quand une application déployée avec ClickOnce est localisée, elle ne peut être affichée que sous la culture localisée. Par exemple, si une application déployée est localisée en japonais elle peut uniquement être affichée sous la version japonaise [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] pas sur Windows en anglais. Cela pose un problème, car il est fréquent que des utilisateurs japonais utilisent une version anglaise de Windows.

 La solution à ce problème consiste à définir l’attribut de secours de langue neutre. Un développeur d’applications peut également supprimer des ressources de l’assembly principal pour les placer dans un assembly satellite correspondant à une culture spécifique. Pour contrôler ce processus, utilisez le <xref:System.Resources.NeutralResourcesLanguageAttribute>. Le constructeur de la <xref:System.Resources.NeutralResourcesLanguageAttribute> classe a deux signatures, une fonction qui accepte un <xref:System.Resources.UltimateResourceFallbackLocation> paramètre pour spécifier l’emplacement où le <xref:System.Resources.ResourceManager> doit extraire les ressources de secours : assembly principal ou assembly satellite. L'exemple suivant montre comment utiliser l'attribut. Pour l’emplacement de secours ultime, le code génère la <xref:System.Resources.ResourceManager> pour rechercher les ressources dans le sous-répertoire « de » du répertoire de l’assembly en cours d’exécution.

```
[assembly: NeutralResourcesLanguageAttribute(
    "de" , UltimateResourceFallbackLocation.Satellite)]
```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la globalisation et de la localisation WPF](wpf-globalization-and-localization-overview.md)
