---
title: Globalisation pour WPF
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
ms.openlocfilehash: fd99d97d677ef588c3f7e2a178190377d72c74ce
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400639"
---
# <a name="globalization-for-wpf"></a>Globalisation pour WPF
Cette rubrique présente les problèmes que vous devez connaître lors de l' [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] écriture d’applications pour le marché mondial. Les éléments de programmation de la globalisation `System.Globalization`sont définis dans [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] dans.

<a name="xaml_globalization"></a>
## <a name="xaml-globalization"></a>Globalisation XAML
 [!INCLUDE[TLA#tla_xaml#initcap](../../../../includes/tlasharptla-xamlsharpinitcap-md.md)]est basé sur [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] et tire parti de la prise en charge de la [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] globalisation définie dans la spécification. Les sections suivantes décrivent [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] certaines fonctionnalités que vous devez connaître.

<a name="char_reference"></a>
### <a name="character-references"></a>Références de caractères
Une référence de caractère donne l’unité de code UTF16 du [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] caractère particulier qu’elle représente, en notation décimale ou hexadécimale. L’exemple suivant montre une référence de caractère décimale pour la lettre majuscule du copte HORI, ou «Ϩ»:

```
&#1000;
```

L’exemple suivant montre une référence de caractère hexadécimale. Notez qu’il a un **x** devant le nombre hexadécimal.

```
&#x3E8;
```

<a name="encoding"></a>
### <a name="encoding"></a>Encodage
 L’encodage pris [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] en charge par [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] est ASCII, UTF-16 et UTF-8. L’instruction Encoding se trouve au début du [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] document. Si aucun attribut d’encodage ni ordre d’octets n’existe, la valeur UTF-8 est affectée par défaut à l’analyseur. UTF-8 et UTF-16 sont les encodages par défaut. UTF-7 n’est pas pris en charge. L’exemple suivant montre comment spécifier un encodage UTF-8 dans un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier.

```
?xml encoding="UTF-8"?
```

<a name="lang_attrib"></a>
### <a name="language-attribute"></a>Attribut de langue
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]utilise [XML: lang](../../xaml-services/xml-lang-handling-in-xaml.md) pour représenter l’attribut de langage d’un élément.  Pour tirer parti de la <xref:System.Globalization.CultureInfo> classe, la valeur de l’attribut Language doit être l’un des noms de culture prédéfinis par. <xref:System.Globalization.CultureInfo> [xml:lang](../../xaml-services/xml-lang-handling-in-xaml.md) peut être hérité dans l’arborescence d’éléments (par les règles XML, pas nécessairement à cause de l’héritage de propriétés de dépendance) et sa valeur par défaut est une chaîne vide s’il n’est pas assigné explicitement.

 L’attribut de langue est très utile pour spécifier des dialectes. Par exemple, le français présente des différences orthographiques, lexicales et phonologiques en fonction de la zone géographique dans laquelle il est utilisé : en France, au Québec, en Belgique ou en Suisse. En outre, le chinois, le japonais et le coréen [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]partagent des points de code dans, mais les formes idéographiques sont différentes et utilisent des polices totalement différentes.

 L’exemple [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] suivant utilise l' `fr-CA` attribut Language pour spécifier le français canadien.

```xml
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>
```

<a name="unicode"></a>
### <a name="unicode"></a>Unicode
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]prend en [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] charge toutes les fonctionnalités, y compris les substituts. Tant que le jeu de caractères peut être mappé à [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], il est pris en charge. Par exemple, le jeu de caractères GB18030 comprend quelques caractères mappés aux extensions A et B et aux paires de substitution du chinois, du japonais et du coréen (CFK) ; par conséquent, il est totalement pris en charge. Une [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application peut utiliser <xref:System.Globalization.StringInfo> pour manipuler des chaînes sans savoir si elles ont des paires de substitution ou des caractères d’association.

<a name="design_intl_ui_with_xaml"></a>
## <a name="designing-an-international-user-interface-with-xaml"></a>Conception d’une interface utilisateur internationale avec le langage XAML
 Cette section décrit [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] les fonctionnalités que vous devez prendre en compte lors de l’écriture d’une application.

<a name="intl_text"></a>
### <a name="international-text"></a>Texte international
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]comprend le traitement intégré pour tous les systèmes d’écriture Microsoft .NET Framework pris en charge.

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

 Tous les moteurs de système d' [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] écriture prennent en charge les polices. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]les polices peuvent inclure [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] les tableaux de disposition qui permettent aux créateurs de polices de concevoir de meilleures polices typographiques internationales et haut de gamme. Les [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] tableaux de disposition des polices contiennent des informations sur les substitutions de glyphe, le positionnement des glyphes, la justification et le positionnement de la ligne de base, ce qui permet aux applications de traitement de texte d’améliorer la disposition du texte.

 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]les polices permettent de gérer des jeux de glyphes volumineux à l’aide [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] de l’encodage. Cet encodage est largement pris en charge au niveau international, comme les variantes de glyphes typographiques.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]le rendu du texte est [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] alimenté par une technologie de sous-pixel qui prend en charge l’indépendance de résolution. La lisibilité est ainsi considérablement améliorée et les documents haute qualité de style magazine peuvent être pris en charge pour tous les scripts.

<a name="intl_layout"></a>
### <a name="international-layout"></a>Disposition internationale
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] offre un moyen très pratique pour prendre en charge des dispositions horizontales, bidirectionnelles et verticales. Dans l’infrastructure de <xref:System.Windows.FrameworkElement.FlowDirection%2A> présentation, la propriété peut être utilisée pour définir la disposition. Les modèles de sens du déroulement sont les suivants :

- *LeftToRight* : disposition horizontale pour le latin, les langues d’Asie orientale, etc.

- *RightToLeft* : disposition bidirectionnelle pour l’arabe, l’hébreu, etc.

<a name="developing_localizable_apps"></a>
## <a name="developing-localizable-applications"></a>Développement d’applications localisables
 Quand vous écrivez une application destinée à être utilisée dans le monde entier, vous ne devez pas oublier que cette application doit être localisable. Les rubriques suivantes signalent certains éléments à prendre en compte.

<a name="mui"></a>
### <a name="multilingual-user-interface"></a>Interface utilisateur multilingue
 Les interfaces utilisateur multilingues (MUI) [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] sont une prise [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] en charge du passage d’une langue à une autre. Une [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application utilise le modèle d’assembly pour prendre en charge MUI. Une application contient des assemblys indépendants de la langue ainsi que des assemblys de ressources satellites dépendants de la langue. Le point d’entrée est un .EXE managé dans l’assembly principal.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]le chargeur de ressources tire parti du [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]gestionnaire de ressources de pour prendre en charge la recherche et la restauration des ressources. Les assemblys satellites multilingues fonctionnent avec le même assembly principal. L’assembly <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> de ressource qui est chargé dépend du du thread actuel.

<a name="localizable_ui"></a>
### <a name="localizable-user-interface"></a>Interface utilisateur localisable
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]les applications [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilisent pour définir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]leur. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] permet aux développeurs de spécifier une hiérarchie d’objets avec un ensemble de propriétés et une logique. L’utilisation principale de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est de développer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] des applications, mais elle peut être utilisée pour spécifier une hiérarchie d’objets Common Language Runtime (CLR). La plupart des [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] développeurs utilisent pour spécifier leur [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] application et utiliser un langage de programmation C# tel que pour réagir à l’interaction de l’utilisateur.

 Du point de vue de la ressource, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] un fichier conçu pour décrire un dépendant [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] du langage est un élément de ressource et, par conséquent, son format de distribution final doit être localisable pour prendre en charge les langues internationales. Étant [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] donné que ne peut [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pas gérer les événements, de nombreuses applications contiennent des blocs de code pour effectuer cette opération. Pour plus d’informations, consultez [vue d’ensemble du langage XAML (WPF)](xaml-overview-wpf.md). Le code est supprimé et compilé en différents binaires lorsqu’un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier est sous forme de jeton dans le formulaire BAML de XAML. Le formulaire BAML des fichiers, des images et d’autres types d’objets de ressources managées XAML est incorporé dans l’assembly des ressources satellites, pouvant être localisé dans d’autres langues, ou dans l’assembly principal, quand la localisation n’est pas nécessaire.

> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]les applications prennent en [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]charge toutes les ressources CLR, y compris les tables de chaînes, les images, etc.

<a name="building_localizable_apps"></a>
### <a name="building-localizable-applications"></a>Génération d’applications localisables
 La localisation consiste à adapter [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] une à différentes cultures. Pour rendre une [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application localisable, les développeurs doivent générer toutes les ressources localisables dans un assembly de ressources. L’assembly de ressource est localisé dans différentes langues et le code-behind utilise l’API de gestion des ressources pour le chargement. L’un des fichiers requis pour une [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application est un fichier projet (. proj). Toutes les ressources que vous utilisez dans votre application doivent être comprises dans le fichier projet. Cette opération est illustrée dans l’exemple suivant, à partir d’un fichier .csproj.

```xml
<Resource Include="data\picture1.jpg"/>
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

 Pour utiliser une ressource dans votre application, instanciez un <xref:System.Resources.ResourceManager> et chargez la ressource que vous souhaitez utiliser. L'exemple suivant illustre la procédure à suivre pour réaliser cette opération.

 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

<a name="using_clickonce"></a>
## <a name="using-clickonce-with-localized-applications"></a>Utilisation de ClickOnce avec les applications localisées
 ClickOnce est une nouvelle technologie de déploiement Windows Forms qui sera livrée avec Visual Studio 2005. Cette technologie permet d’installer des applications et de mettre à niveau des applications web. Quand une application déployée avec ClickOnce est localisée, elle ne peut être affichée que sous la culture localisée. Par exemple, si une application déployée est localisée en japonais, elle ne peut être affichée [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] que sur le japonais et non sur la version anglaise de Windows. Cela présente un problème, car il s’agit d’un scénario courant pour les utilisateurs japonais qui exécutent une version anglaise de Windows.

 La solution à ce problème consiste à définir l’attribut de secours de langue neutre. Un développeur d’applications peut également supprimer des ressources de l’assembly principal pour les placer dans un assembly satellite correspondant à une culture spécifique. Pour contrôler ce processus, utilisez <xref:System.Resources.NeutralResourcesLanguageAttribute>le. Le constructeur de la <xref:System.Resources.NeutralResourcesLanguageAttribute> classe a deux signatures, une qui prend un <xref:System.Resources.UltimateResourceFallbackLocation> paramètre pour <xref:System.Resources.ResourceManager> spécifier l’emplacement où doit extraire les ressources de secours: assembly principal ou assembly satellite. L'exemple suivant montre comment utiliser l'attribut. Pour l’emplacement de secours ultime, le code fait <xref:System.Resources.ResourceManager> en sorte que le recherche les ressources dans le sous-répertoire «de» du répertoire de l’assembly en cours d’exécution.

```
[assembly: NeutralResourcesLanguageAttribute(
    "de" , UltimateResourceFallbackLocation.Satellite)]
```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la globalisation et de la localisation WPF](wpf-globalization-and-localization-overview.md)
