---
title: Syntaxe XAML en détail
description: Découvrez les termes utilisés pour décrire les éléments de la syntaxe XAML pour Windows Presentation Foundation et d’autres infrastructures qui utilisent XAML.
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- XAML [WPF], parsing of attributes
- parsing of attributes [WPF]
- XAML [WPF], markup extensions
- attached properties [WPF]
- tag syntax [XAML]
- markup extensions [WPF]
- XAML [WPF], object element syntax
- XAML [WPF], syntax terminology
- attached events [WPF]
- lookup semantics [WPF]
- XAML [WPF], attached events
- XAML [WPF], content syntax
- XAML [WPF], lookup semantics
- content syntax [WPF]
- object element syntax [WPF]
- syntax terminology [XAML]
- XAML [WPF], attached properties
- attributes [XAML], parsing
- XAML [WPF], tag syntax
- XAML [WPF], attribute syntax
- property element syntax [WPF]
- terminology [XAML]
- namespaces [WPF], XML
- attribute syntax [XAML]
- XAML [WPF], property element syntax
ms.assetid: 67cce290-ca26-4c41-a797-b68aabc45479
ms.openlocfilehash: 6ef217a646b14f02c0b812f6316ec84f26d4b660
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168338"
---
# <a name="xaml-syntax-in-detail"></a>Syntaxe XAML en détail
Cette rubrique définit les termes utilisés pour décrire les éléments de la syntaxe XAML. Ces termes sont fréquemment utilisés dans la suite de cette documentation, à la fois pour la documentation WPF et pour les autres infrastructures qui utilisent XAML ou les concepts XAML de base activés par la prise en charge du langage XAML au niveau de System. Xaml. Cette rubrique développe la terminologie de base présentée dans la rubrique [vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md).  

<a name="the_xaml_language_specification"></a>
## <a name="the-xaml-language-specification"></a>Spécification du langage XAML  
 La terminologie de syntaxe XAML définie ici est également définie ou référencée dans la spécification du langage XAML. XAML est un langage basé sur XML qui suit ou s’étend sur les règles de structure XML. Une partie de la terminologie est partagée à partir de ou basée sur la terminologie couramment utilisée pour décrire le langage XML ou le modèle d’objet de document XML.  
  
 Pour plus d’informations sur la spécification du langage XAML, téléchargez [ \[ MS \] -XAML](https://download.microsoft.com/download/0/A/6/0A6F7755-9AF5-448B-907D-13985ACCF53E/[MS-XAML].pdf) à partir du centre de téléchargement Microsoft.  
  
<a name="xaml_and_clr"></a>
## <a name="xaml-and-clr"></a>XAML et CLR  
 XAML est un langage de balisage. Le common language runtime (CLR), tel qu’il est impliqué par son nom, permet l’exécution de l’exécution. XAML n’est pas par lui-même l’un des langages couramment utilisés directement par le runtime CLR. Au lieu de cela, vous pouvez considérer XAML comme prenant en charge son propre système de type. Le système d’analyse XAML particulier utilisé par WPF est basé sur le CLR et le système de type CLR. Les types XAML sont mappés aux types CLR pour instancier une représentation au moment de l’exécution lorsque le XAML pour WPF est analysé. Pour cette raison, le reste de la syntaxe de ce document inclut des références au système de type CLR, même si les discussions de syntaxe équivalentes dans la spécification du langage XAML ne le font pas. (Selon le niveau de spécification du langage XAML, les types XAML peuvent être mappés à n’importe quel autre système de type, ce qui ne doit pas nécessairement être le CLR, mais cela nécessiterait la création et l’utilisation d’un autre analyseur XAML.)  
  
#### <a name="members-of-types-and-class-inheritance"></a>Membres de types et héritage de classe  
 Les propriétés et les événements tels qu’ils apparaissent en tant que membres XAML d’un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] type sont souvent hérités de types de base. Prenons l’exemple suivant : `<Button Background="Blue" .../>` . La <xref:System.Windows.Controls.Control.Background%2A> propriété n’est pas une propriété déclarée immédiatement sur la <xref:System.Windows.Controls.Button> classe, si vous devez examiner la définition de classe, les résultats de la réflexion ou la documentation. <xref:System.Windows.Controls.Control.Background%2A>À la place, est héritée de la classe de base <xref:System.Windows.Controls.Control> .  
  
 Le comportement d’héritage de classe des [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] éléments XAML est un comportement significatif par rapport à une interprétation du balisage XML appliquée par schéma. L’héritage de classe peut devenir complexe, en particulier lorsque les classes de base intermédiaires sont abstraites, ou lorsque les interfaces sont impliquées. C’est l’une des raisons pour lesquelles l’ensemble d’éléments XAML et leurs attributs autorisés sont difficiles à représenter de façon précise et complète à l’aide des types de schémas généralement utilisés pour la programmation XML, tels que les DTD ou le format XSD. Une autre raison est que les fonctionnalités d’extensibilité et de mappage de type du langage XAML lui-même empêchent l’exhaustivité de toute représentation fixe des types et des membres autorisés.  
  
<a name="object_element_syntax"></a>
## <a name="object-element-syntax"></a>Syntaxe de l’élément objet  
 La *syntaxe d’élément objet* est la syntaxe de balisage XAML qui instancie une structure ou une classe CLR en déclarant un élément XML. Cette syntaxe ressemble à la syntaxe d’élément d’autres langages de balisage tels que HTML. La syntaxe d’élément objet commence par un chevron gauche ( \< ), suivi immédiatement du nom de type de la classe ou de la structure en cours d’instanciation. Zéro, un ou plusieurs espaces peuvent être suivis du nom de type et zéro, un ou plusieurs attributs peuvent également être déclarés sur l’élément objet, avec un ou plusieurs espaces séparant chaque paire nom d’attribut = « valeur ». Enfin, l’une des conditions suivantes doit être remplie :  
  
- L’élément et la balise doivent être fermés par une barre oblique (/) suivie immédiatement d’un chevron droit (>).  
  
- La balise d’ouverture doit être terminée par un chevron droit (>). D’autres éléments objets, éléments de propriété ou texte interne peuvent suivre la balise d’ouverture. Exactement le contenu qui peut être contenu ici est généralement limité par le modèle objet de l’élément. La balise de fermeture équivalente pour l’élément Object doit également exister, dans une imbrication et un équilibre appropriés avec d’autres paires de balises d’ouverture et de fermeture.  
  
 XAML implémenté par .NET dispose d’un ensemble de règles qui mappent des éléments objet dans des types, des attributs dans des propriétés ou des événements, et des espaces de noms XAML à des espaces de noms CLR plus assembly. Pour WPF et .NET, les éléments objets XAML sont mappés aux types .NET tels qu’ils sont définis dans les assemblys référencés, et les attributs sont mappés aux membres de ces types. Quand vous référencez un type CLR en XAML, vous avez également accès aux membres hérités de ce type.  
  
 Par exemple, l’exemple suivant est une syntaxe d’élément objet qui instancie une nouvelle instance de la <xref:System.Windows.Controls.Button> classe et spécifie également un <xref:System.Windows.FrameworkElement.Name%2A> attribut et une valeur pour cet attribut :  
  
 [!code-xaml[XAMLOvwSupport#SyntaxOE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxoe)]  
  
 L’exemple suivant est une syntaxe d’élément objet qui comprend également la syntaxe de propriété de contenu XAML. Le texte interne contenu dans sera utilisé pour définir la <xref:System.Windows.Controls.TextBox> propriété de contenu XAML, <xref:System.Windows.Controls.TextBox.Text%2A> .  
  
 [!code-xaml[XAMLOvwSupport#ThisIsATextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#thisisatextbox)]  
  
### <a name="content-models"></a>Modèles de contenu  
 Une classe peut prendre en charge une utilisation en tant qu’élément objet XAML en termes de syntaxe, mais cet élément ne fonctionnera correctement que dans une application ou une page lorsqu’il sera placé dans une position attendue d’un modèle de contenu ou d’une arborescence d’éléments global. Par exemple, un <xref:System.Windows.Controls.MenuItem> doit généralement être placé en tant qu’enfant d’une <xref:System.Windows.Controls.Primitives.MenuBase> classe dérivée telle que <xref:System.Windows.Controls.Menu> . Les modèles de contenu pour des éléments spécifiques sont documentés dans le cadre des remarques sur les pages de classe pour les contrôles et d’autres [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] classes qui peuvent être utilisés comme éléments XAML.  
  
<a name="properties_of_object_elements"></a>
## <a name="properties-of-object-elements"></a>Propriétés des éléments Object  
 Les propriétés en XAML sont définies par une variété de syntaxes possibles. La syntaxe qui peut être utilisée pour une propriété particulière varie en fonction des caractéristiques du système de type sous-jacent de la propriété que vous définissez.  
  
 En définissant des valeurs de propriétés, vous ajoutez des fonctionnalités ou des caractéristiques à des objets tels qu’ils existent dans le graphique d’objets d’exécution. L’état initial de l’objet créé à partir d’un élément objet est basé sur le comportement de constructeur sans paramètre. En règle générale, votre application utilise un autre nom que l’instance par défaut complète d’un objet donné.  
  
<a name="attribute_syntax_properties"></a>
## <a name="attribute-syntax-properties"></a>Syntaxe d’attribut (Propriétés)  
 La syntaxe d’attribut est la syntaxe de balisage XAML qui définit une valeur pour une propriété en déclarant un attribut sur un élément objet existant. Le nom de l’attribut doit correspondre au nom de membre CLR de la propriété de la classe qui stocke l’élément objet approprié. Le nom de l’attribut est suivi d’un opérateur d’assignation (=). La valeur de l’attribut doit être une chaîne entre guillemets.  
  
> [!NOTE]
> Vous pouvez utiliser des guillemets de remplacement pour placer un guillemet littéral dans un attribut. Par exemple, vous pouvez utiliser des guillemets simples comme moyen de déclarer une chaîne qui contient un caractère de guillemet double dans celui-ci. Que vous utilisiez des guillemets simples ou doubles, vous devez utiliser une paire correspondante pour ouvrir et fermer la chaîne de valeur d’attribut. Il existe également des séquences d’échappement ou d’autres techniques permettant de contourner les restrictions de caractères imposées par toute syntaxe XAML particulière. Consultez [entités de caractères XML et XAML](../../../desktop-wpf/xaml-services/xml-character-entities.md).  
  
 Pour être défini par le biais de la syntaxe d’attribut, une propriété doit être publique et doit être accessible en écriture. La valeur de la propriété dans le système de type de stockage doit être un type valeur ou doit être un type référence qui peut être instancié ou référencé par un processeur XAML lors de l’accès au type de stockage approprié.  
  
 Pour les événements XAML WPF, l’événement référencé en tant que nom d’attribut doit être public et avoir un délégué public.  
  
 La propriété ou l’événement doit être un membre de la classe ou de la structure qui est instancié par l’élément objet conteneur.  
  
### <a name="processing-of-attribute-values"></a>Traitement des valeurs d’attribut  
 La valeur de chaîne contenue dans les guillemets ouvrants et fermants est traitée par un processeur XAML. Pour les propriétés, le comportement de traitement par défaut est déterminé par le type de la propriété CLR sous-jacente.  
  
 La valeur de l’attribut est remplie par l’un des éléments suivants, à l’aide de cet ordre de traitement :  
  
1. Si le processeur XAML rencontre une accolade, ou un élément objet qui dérive de <xref:System.Windows.Markup.MarkupExtension> , l’extension de balisage référencée est évaluée en premier au lieu de traiter la valeur comme une chaîne, et l’objet retourné par l’extension de balisage est utilisé comme valeur. Dans de nombreux cas, l’objet retourné par une extension de balisage sera une référence à un objet existant, ou une expression qui diffère l’évaluation jusqu’au moment de l’exécution et n’est pas un objet nouvellement instancié.  
  
2. Si la propriété est déclarée avec un <xref:System.ComponentModel.TypeConverter> attribute ou si le type de valeur de cette propriété est déclaré avec un <xref:System.ComponentModel.TypeConverter> attribut, la valeur de chaîne de l’attribut est soumise au convertisseur de type comme une entrée de conversion, et le convertisseur retourne une nouvelle instance d’objet.  
  
3. S’il n’y a pas de <xref:System.ComponentModel.TypeConverter> , une conversion directe vers le type de propriété est tentée. Ce dernier niveau est une conversion directe au niveau de l’analyseur-valeur native entre les types primitifs du langage XAML, ou une vérification des noms des constantes nommées dans une énumération (l’analyseur accède ensuite aux valeurs correspondantes).  
  
#### <a name="enumeration-attribute-values"></a>Valeurs d’attribut d’énumération  
 Les énumérations en XAML sont traitées intrinsèquement par les analyseurs XAML, et les membres d’une énumération doivent être spécifiés en spécifiant le nom de chaîne de l’une des constantes nommées de l’énumération.  
  
 Pour les valeurs d’énumération sans indicateur, le comportement natif consiste à traiter la chaîne d’une valeur d’attribut et à la résoudre en l’une des valeurs d’énumération. Vous ne spécifiez pas l’énumération dans l' *énumération*de format. *, Comme*vous le feriez dans le code. Au lieu de cela, vous spécifiez uniquement la *valeur*et l' *énumération* est déduite par le type de la propriété que vous définissez. Si vous spécifiez un attribut dans l' *énumération*. Format de *valeur* , elle ne sera pas résolue correctement.  
  
 Pour les énumérations d’indicateurs, le comportement est basé sur la <xref:System.Enum.Parse%2A?displayProperty=nameWithType> méthode. Vous pouvez spécifier plusieurs valeurs pour une énumération d’indicateurs en séparant chaque valeur par une virgule. Toutefois, vous ne pouvez pas combiner des valeurs d’énumération qui n’ont pas d’indicateurs. Par exemple, vous ne pouvez pas utiliser la syntaxe de virgule pour tenter de créer un <xref:System.Windows.Trigger> qui agit sur plusieurs conditions d’une énumération sans indicateur :  
  
```xaml  
<!--This will not compile, because Visibility is not a flagwise enumeration.-->  
...  
<Trigger Property="Visibility" Value="Collapsed,Hidden">  
  <Setter ... />  
</Trigger>  
...  
```  
  
 Les énumérations d’indicateurs qui prennent en charge les attributs définissables dans XAML sont rares dans WPF. Toutefois, une telle énumération est <xref:System.Windows.Media.StyleSimulations> . Par exemple, vous pouvez utiliser la syntaxe d’attribut avec indicateurs délimités par des virgules pour modifier l’exemple fourni dans les notes de la <xref:System.Windows.Documents.Glyphs> classe ; `StyleSimulations = "BoldSimulation"` peut devenir `StyleSimulations = "BoldSimulation,ItalicSimulation"` . <xref:System.Windows.Input.KeyBinding.Modifiers%2A?displayProperty=nameWithType>est une autre propriété où plusieurs valeurs d’énumération peuvent être spécifiées. Toutefois, cette propriété est un cas particulier, car l' <xref:System.Windows.Input.ModifierKeys> énumération prend en charge son propre convertisseur de type. Le convertisseur de type pour les modificateurs utilise un signe plus (+) comme délimiteur plutôt qu’une virgule (,). Cette conversion prend en charge la syntaxe plus traditionnelle pour représenter les combinaisons de touches dans la programmation Microsoft Windows, par exemple « Ctrl + Alt ».  
  
### <a name="properties-and-event-member-name-references"></a>Propriétés et références de nom de membre d’événement  
 Lorsque vous spécifiez un attribut, vous pouvez référencer toute propriété ou événement qui existe en tant que membre du type CLR que vous avez instancié pour l’élément objet conteneur.  
  
 Ou bien, vous pouvez référencer une propriété jointe ou un événement attaché, indépendamment de l’élément objet conteneur. (Les propriétés jointes sont présentées dans une section à venir.)  
  
 Vous pouvez également nommer tout événement à partir de n’importe quel objet accessible par le biais de l’espace de noms par défaut à l’aide d’un *TypeName*. nom qualifié partiel de l' *événement* ; Cette syntaxe prend en charge l’attachement de gestionnaires pour les événements routés où le gestionnaire est destiné à gérer le routage d’événements à partir d’éléments enfants, mais l’élément parent n’a pas également cet événement dans sa table de membres. Cette syntaxe ressemble à une syntaxe d’événement jointe, mais l’événement ici n’est pas un événement attaché réel. Au lieu de cela, vous référencez un événement avec un nom qualifié. Pour plus d’informations, consultez [vue d’ensemble des événements routés](routed-events-overview.md).  
  
 Dans certains scénarios, les noms de propriétés sont parfois fournis comme valeur d’un attribut, plutôt que le nom de l’attribut. Ce nom de propriété peut également inclure des qualificateurs, tels que la propriété spécifiée sous la forme *ownerType*. *dependencyPropertyName*. Ce scénario est courant lors de l’écriture de styles ou de modèles en XAML. Les règles de traitement pour les noms de propriété fournies en tant que valeur d’attribut sont différentes et sont régies par le type de la propriété qui est définie ou par les comportements de sous-systèmes WPF particuliers. Pour plus d’informations, consultez [style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
 Une autre utilisation pour les noms de propriété est lorsqu’une valeur d’attribut décrit une relation de propriété-propriété. Cette fonctionnalité est utilisée pour la liaison de données et pour les cibles de Storyboard, et est activée par la <xref:System.Windows.PropertyPath> classe et son convertisseur de type. Pour une description plus complète de la sémantique de recherche, consultez [syntaxe XAML PropertyPath](propertypath-xaml-syntax.md).  
  
<a name="property_element_syntax"></a>
## <a name="property-element-syntax"></a>Syntaxe des éléments de propriété  
 La *syntaxe d’élément de propriété* est une syntaxe qui diffère quelque peu des règles de syntaxe XML de base pour les éléments. Dans XML, la valeur d’un attribut est une chaîne de facto, la seule différence possible étant le format d’encodage de chaîne utilisé. En XAML, vous pouvez assigner d’autres éléments objet comme valeur d’une propriété. Cette fonctionnalité est activée par la syntaxe d’élément de propriété. Au lieu de spécifier la propriété en tant qu’attribut dans la balise d’élément, la propriété est spécifiée à l’aide d’une balise d’élément ouvrante dans *elementTypeName*. *PropertyName* , la valeur de la propriété est spécifiée dans, puis l’élément de propriété est fermé.  
  
 Plus précisément, la syntaxe commence par un chevron gauche ( \<), followed immediately by the type name of the class or structure that the property element syntax is contained within. This is followed immediately by a single dot (.), then by the name of a property, then by a right angle bracket (> ). Comme pour la syntaxe d’attribut, cette propriété doit exister dans les membres publics déclarés du type spécifié. La valeur à assigner à la propriété est contenue dans l’élément de propriété. En règle générale, la valeur est donnée sous la forme d’un ou plusieurs éléments Object, car la spécification d’objets en tant que valeurs est le scénario que la syntaxe des éléments de propriété est destinée à traiter. Enfin, une balise de fermeture équivalente spécifiant le même *elementTypeName*. la combinaison *PropertyName* doit être fournie, à des niveaux d’imbrication et d’équilibrage appropriés avec d’autres balises d’élément.  
  
 Par exemple, la syntaxe d’élément de propriété suivante est utilisée pour la <xref:System.Windows.FrameworkElement.ContextMenu%2A> propriété d’un <xref:System.Windows.Controls.Button> .  
  
 [!code-xaml[XAMLOvwSupport#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#contextmenu)]  
  
 La valeur dans un élément de propriété peut également être fournie en tant que texte interne, dans les cas où le type de propriété spécifié est un type valeur primitif, tel que <xref:System.String> , ou une énumération où un nom est spécifié. Ces deux utilisations sont un peu rares, car chacun de ces cas peut également utiliser une syntaxe d’attribut plus simple. Un scénario de remplissage d’un élément de propriété avec une chaîne est pour les propriétés qui ne sont pas la propriété de contenu XAML mais qui sont toujours utilisées pour la représentation du texte de l’interface utilisateur, et des éléments d’espace blanc particuliers tels que les sauts de ligne doivent apparaître dans le texte de l’interface utilisateur. La syntaxe d’attribut ne peut pas conserver les sauts de ligne, mais la syntaxe des éléments de propriété peut, tant que la conservation de l’espace blanc significatif est active (pour plus d’informations, consultez [traitement des espaces blancs en XAML](../../../desktop-wpf/xaml-services/white-space-processing.md)). Un autre scénario est de sorte que la [directive x :uid](../../../desktop-wpf/xaml-services/xuid-directive.md) puisse être appliquée à l’élément de propriété et marque donc la valeur dans comme une valeur qui doit être localisée dans la sortie BAML de WPF ou par d’autres techniques.  
  
 Un élément de propriété n’est pas représenté dans l’arborescence logique WPF. Un élément de propriété est simplement une syntaxe particulière pour la définition d’une propriété, et n’est pas un élément qui a une instance ou un objet qui le sauvegarde. (Pour plus d’informations sur le concept d’arborescence logique, consultez [arborescences dans WPF](trees-in-wpf.md).)  
  
 Pour les propriétés où la syntaxe des attributs et des éléments de propriété est prise en charge, les deux syntaxes ont généralement le même résultat, bien que les subtilités, telles que la gestion des espaces blancs, peuvent varier légèrement entre les syntaxes.  
  
<a name="collection_syntax"></a>
## <a name="collection-syntax"></a>Syntaxe des collections  
 La spécification XAML exige que les implémentations du processeur XAML identifient les propriétés où le type de valeur est une collection. L’implémentation générale du processeur XAML dans .NET est basée sur le code managé et le CLR, et elle identifie les types de collections par le biais de l’un des éléments suivants :  
  
- Le type implémente <xref:System.Collections.IList> .  
  
- Le type implémente <xref:System.Collections.IDictionary> .  
  
- Le type dérive de <xref:System.Array> (pour plus d’informations sur les tableaux en XAML, consultez [X :Array Markup Extension](../../../desktop-wpf/xaml-services/xarray-markup-extension.md).)  
  
 Si le type d’une propriété est une collection, le type de collection déduit n’a pas besoin d’être spécifié dans le balisage en tant qu’élément objet. Au lieu de cela, les éléments destinés à devenir les éléments de la collection sont spécifiés en tant qu’un ou plusieurs éléments enfants de l’élément de propriété. Chaque élément de ce type est évalué à un objet pendant le chargement et ajouté à la collection en appelant la `Add` méthode de la collection implicite. Par exemple, la <xref:System.Windows.Style.Triggers%2A> propriété de <xref:System.Windows.Style> prend le type de collection spécialisé <xref:System.Windows.TriggerCollection> , qui implémente <xref:System.Collections.IList> . Il n’est pas nécessaire d’instancier un <xref:System.Windows.TriggerCollection> élément objet dans le balisage. Au lieu de cela, vous spécifiez un ou plusieurs <xref:System.Windows.Trigger> éléments en tant qu’éléments dans l' `Style.Triggers` élément de propriété, où <xref:System.Windows.Trigger> (ou une classe dérivée) est le type attendu comme type d’élément pour le fortement typé et implicite <xref:System.Windows.TriggerCollection> .  
  
 [!code-xaml[XAMLOvwSupport#SyntaxPECollection](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxpecollection)]  
  
 Une propriété peut être à la fois un type de collection et la propriété de contenu XAML pour ce type et les types dérivés, qui est décrit dans la section suivante de cette rubrique.  
  
 Un élément de collection implicite crée un membre dans la représentation de l’arborescence logique, même s’il n’apparaît pas dans le balisage en tant qu’élément. En général, le constructeur du type parent exécute l’instanciation de la collection qui est l’une de ses propriétés, et la collection initialement vide devient partie intégrante de l’arborescence d’objets.  
  
> [!NOTE]
> Les interfaces de liste et de dictionnaire génériques ( <xref:System.Collections.Generic.IList%601> et <xref:System.Collections.Generic.IDictionary%602> ) ne sont pas prises en charge pour la détection de collection. Toutefois, vous pouvez utiliser la <xref:System.Collections.Generic.List%601> classe comme classe de base, car elle implémente <xref:System.Collections.IList> directement, ou <xref:System.Collections.Generic.Dictionary%602> en tant que classe de base, car elle implémente <xref:System.Collections.IDictionary> directement.  
  
 Dans les pages de référence .NET pour les types de collection, cette syntaxe avec l’omission délibérée de l’élément objet pour une collection est parfois notée dans les sections de syntaxe XAML comme syntaxe de collection implicite.  
  
 À l’exception de l’élément racine, chaque élément objet d’un fichier XAML qui est imbriqué en tant qu’élément enfant d’un autre élément est en fait un élément qui est l’un des cas suivants, ou les deux : un membre d’une propriété de collection implicite de son élément parent, ou un élément qui spécifie la valeur de la propriété de contenu XAML pour l’élément parent (les propriétés de contenu XAML seront abordées dans une section En d’autres termes, la relation entre les éléments parents et les éléments enfants d’une page de balisage est en fait un objet unique à la racine, et chaque élément objet sous la racine est une instance unique qui fournit une valeur de propriété du parent, ou l’un des éléments d’une collection qui est également une valeur de propriété de type collection du parent. Ce concept à racine unique est courant avec XML et est fréquemment renforcé dans le comportement des API qui chargent le code XAML, par exemple <xref:System.Windows.Markup.XamlReader.Load%2A> .  
  
 L’exemple suivant est une syntaxe avec l’élément objet pour une collection ( <xref:System.Windows.Media.GradientStopCollection> ) spécifiée explicitement.  
  
```xaml  
<LinearGradientBrush>  
  <LinearGradientBrush.GradientStops>  
    <GradientStopCollection>  
      <GradientStop Offset="0.0" Color="Red" />  
      <GradientStop Offset="1.0" Color="Blue" />  
    </GradientStopCollection>  
  </LinearGradientBrush.GradientStops>  
</LinearGradientBrush>  
```  
  
 Notez qu’il n’est pas toujours possible de déclarer explicitement la collection. Par exemple, toute tentative de Déclaration <xref:System.Windows.TriggerCollection> explicite dans l' <xref:System.Windows.Style.Triggers%2A> exemple précédent échoue. La déclaration explicite de la collection requiert que la classe de collection prenne en charge un constructeur sans paramètre et <xref:System.Windows.TriggerCollection> n’ait pas de constructeur sans paramètre.  
  
<a name="xaml_content_properties"></a>
## <a name="xaml-content-properties"></a>Propriétés de contenu XAML  
 La syntaxe de contenu XAML est une syntaxe qui est uniquement activée sur les classes qui spécifient le dans le cadre <xref:System.Windows.Markup.ContentPropertyAttribute> de leur déclaration de classe. Le <xref:System.Windows.Markup.ContentPropertyAttribute> référence le nom de la propriété qui est la propriété de contenu pour ce type d’élément (y compris les classes dérivées). En cas de traitement par un processeur XAML, tout élément enfant ou texte interne trouvé entre les balises d’ouverture et de fermeture de l’élément objet sera assigné comme valeur de la propriété de contenu XAML pour cet objet. Vous êtes autorisé à spécifier des éléments de propriété explicites pour la propriété de contenu, mais cette utilisation n’est généralement pas indiquée dans les sections de syntaxe XAML de la référence .NET. La technique explicite/détaillée a une valeur occasionnelle pour la clarté du balisage ou comme une question de style de balisage, mais en général l’intention d’une propriété de contenu est de rationaliser le balisage afin que les éléments qui sont liés intuitivement comme parent-enfant puissent être imbriqués directement. Les balises d’élément de propriété pour d’autres propriétés sur un élément ne sont pas assignées en tant que « contenu » par une définition de langage XAML stricte ; elles sont traitées précédemment dans l’ordre de traitement de l’analyseur XAML et ne sont pas considérées comme « contenu ».  
  
### <a name="xaml-content-property-values-must-be-contiguous"></a>Les valeurs de propriété de contenu XAML doivent être contiguës  
 La valeur d’une propriété de contenu XAML doit être fournie entièrement avant ou entièrement après tous les autres éléments de propriété sur cet élément objet. Cela est vrai si la valeur d’une propriété de contenu XAML est spécifiée en tant que chaîne ou en tant qu’un ou plusieurs objets. Par exemple, le balisage suivant n’analyse pas :  
  
```xaml  
<Button>I am a
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 Ce n’est pas non plus conforme, car si cette syntaxe a été rendue explicite à l’aide de la syntaxe d’élément de propriété pour la propriété de contenu, la propriété de contenu est définie deux fois :  
  
```xaml  
<Button>  
  <Button.Content>I am a </Button.Content>  
  <Button.Background>Blue</Button.Background>  
  <Button.Content> blue button</Button.Content>  
</Button>  
```  
  
 Un exemple similaire non conforme est si la propriété de contenu est une collection et si les éléments enfants sont intercalés avec les éléments de propriété :  
  
```xaml  
<StackPanel>  
  <Button>This example</Button>  
  <StackPanel.Resources>  
    <SolidColorBrush x:Key="BlueBrush" Color="Blue"/>  
  </StackPanel.Resources>  
  <Button>... is illegal XAML</Button>  
</StackPanel>  
```  
  
<a name="content_properties_and_collection_syntax_combined"></a>
## <a name="content-properties-and-collection-syntax-combined"></a>Combinaison des propriétés de contenu et de la syntaxe des collections  
 Pour accepter plus d’un élément objet en tant que contenu, le type de la propriété de contenu doit être spécifiquement un type de collection. Semblable à la syntaxe des éléments de propriété pour les types de collections, un processeur XAML doit identifier les types qui sont des types de collection. Si un élément a une propriété de contenu XAML et que le type de la propriété de contenu XAML est une collection, le type de collection implicite n’a pas besoin d’être spécifié dans le balisage en tant qu’élément objet et la propriété de contenu XAML n’a pas besoin d’être spécifiée en tant qu’élément de propriété. Par conséquent, le modèle de contenu apparent dans le balisage peut désormais avoir plusieurs éléments enfants assignés comme contenu. Voici la syntaxe de contenu pour une <xref:System.Windows.Controls.Panel> classe dérivée. Toutes les <xref:System.Windows.Controls.Panel> classes dérivées établissent la propriété de contenu XAML comme étant <xref:System.Windows.Controls.Panel.Children%2A> , ce qui requiert une valeur de type <xref:System.Windows.Controls.UIElementCollection> .  
  
 [!code-xaml[XAMLOvwSupport#SyntaxContent](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page5.xaml#syntaxcontent)]  
  
 Notez que ni l’élément de propriété <xref:System.Windows.Controls.Panel.Children%2A> ni l’élément <xref:System.Windows.Controls.UIElementCollection> n’est requis dans le balisage. Il s’agit d’une fonctionnalité de conception de XAML qui fait que les éléments contenus de manière récursive qui définissent un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] sont représentées de manière intuitive sous la forme d’une arborescence d’éléments imbriqués avec des relations d’élément parent-enfant immédiates, sans balises d’élément de propriété ou objets de collection. En fait, <xref:System.Windows.Controls.UIElementCollection> ne peut pas être spécifié explicitement dans le balisage en tant qu’élément objet, par conception. Comme sa seule utilisation prévue est la collection implicite, <xref:System.Windows.Controls.UIElementCollection> n’expose pas de constructeur sans paramètre public et, par conséquent, ne peut pas être instancié en tant qu’élément objet.  
  
### <a name="mixing-property-elements-and-object-elements-in-an-object-with-a-content-property"></a>Combinaison d’éléments de propriété et d’éléments objet dans un objet avec une propriété de contenu  
 La spécification XAML déclare qu’un processeur XAML peut appliquer que les éléments objets utilisés pour remplir la propriété de contenu XAML dans un élément objet doivent être contigus et ne doivent pas être mélangés. Cette restriction par rapport à la combinaison d’éléments de propriété et de contenu est appliquée par les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] processeurs XAML.  
  
 Vous pouvez avoir un élément objet enfant comme premier balisage immédiat dans un élément objet. Vous pouvez alors introduire des éléments de propriété. Ou bien, vous pouvez spécifier un ou plusieurs éléments de propriété, le contenu, puis d’autres éléments de propriété. Toutefois, une fois qu’un élément Property suit le contenu, vous ne pouvez pas introduire de contenu supplémentaire, mais vous pouvez uniquement ajouter des éléments de propriété.  
  
 Cette exigence relative à l’ordre des éléments de contenu/propriété ne s’applique pas au texte interne utilisé comme contenu. Toutefois, il s’agit toujours d’un bon style de balisage pour maintenir le texte interne contigu, car un espace blanc significatif sera difficile à détecter visuellement dans le balisage si des éléments de propriété sont intercalés avec du texte interne.  
  
<a name="xaml_namespaces"></a>
## <a name="xaml-namespaces"></a>Espaces de noms XAML  
 Aucun des exemples de syntaxe précédents n’a spécifié un espace de noms XAML autre que l’espace de noms XAML par défaut. Dans les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications classiques, l’espace de noms XAML par défaut est spécifié comme étant l' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] espace de noms. Vous pouvez spécifier des espaces de noms XAML autres que l’espace de noms XAML par défaut et toujours utiliser une syntaxe similaire. Toutefois, à tout endroit où une classe est nommée et qui n’est pas accessible dans l’espace de noms XAML par défaut, ce nom de classe doit être précédé du préfixe de l’espace de noms XAML mappé à l’espace de noms CLR correspondant. Par exemple, `<custom:Example/>` est une syntaxe d’élément objet pour instancier une instance de la `Example` classe, où l’espace de noms CLR contenant cette classe (et éventuellement les informations d’assembly externe qui contiennent des types de stockage) a été précédemment mappé au `custom` préfixe.  
  
 Pour plus d’informations sur les espaces de noms XAML, consultez [espaces de noms XAML et mappage d’espace de noms pour XAML WPF](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="markup_extensions"></a>
## <a name="markup-extensions"></a>Extensions de balisage  
 XAML définit une entité de programmation d’extension de balisage qui permet une séquence d’échappement de la gestion normale du processeur XAML des valeurs d’attribut de chaîne ou des éléments objet, et diffère le traitement à une classe de stockage. Le caractère qui identifie une extension de balisage sur un processeur XAML lors de l’utilisation de la syntaxe d’attribut est l’accolade ouvrante ({), suivie d’un caractère autre qu’une accolade fermante (}). La première chaîne qui suit l’accolade ouvrante doit référencer la classe qui fournit le comportement d’extension particulier, où la référence peut omettre la sous-chaîne « extension » si cette sous-chaîne fait partie du nom de la classe true. Par la suite, un seul espace peut apparaître, puis chaque caractère suivant est utilisé comme entrée par l’implémentation de l’extension, jusqu’à ce que l’accolade fermante soit rencontrée.  
  
 L’implémentation XAML .NET utilise la <xref:System.Windows.Markup.MarkupExtension> classe abstraite comme base pour toutes les extensions de balisage prises en charge par, ainsi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que d’autres infrastructures ou technologies. Les extensions de balisage qui [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implémentent spécifiquement sont souvent destinées à fournir un moyen de référencer d’autres objets existants, ou d’effectuer des références différées aux objets qui seront évalués au moment de l’exécution. Par exemple, une liaison de données WPF simple est effectuée en spécifiant l' `{Binding}` extension de balisage à la place de la valeur qu’une propriété particulière devrait normalement prendre. La plupart des extensions de balisage WPF activent une syntaxe d’attribut pour les propriétés où une syntaxe d’attribut n’est pas possible autrement. Par exemple, un <xref:System.Windows.Style> objet est un type relativement complexe qui contient une série imbriquée d’objets et de propriétés. Les styles dans WPF sont généralement définis en tant que ressource dans un <xref:System.Windows.ResourceDictionary> , puis référencés par l’intermédiaire de l’une des deux extensions de balisage WPF qui demandent une ressource. L’extension de balisage défère l’évaluation de la valeur de propriété à une recherche de ressource et permet de fournir la valeur de la <xref:System.Windows.FrameworkElement.Style%2A> propriété, en prenant le type <xref:System.Windows.Style> , dans la syntaxe d’attribut, comme dans l’exemple suivant :  
  
 `<Button Style="{StaticResource MyStyle}">My button</Button>`  
  
 Ici, `StaticResource` identifie la <xref:System.Windows.StaticResourceExtension> classe qui fournit l’implémentation de l’extension de balisage. La chaîne suivante `MyStyle` est utilisée comme entrée pour le constructeur non défini par défaut <xref:System.Windows.StaticResourceExtension> , où le paramètre pris dans la chaîne d’extension déclare le demandé <xref:System.Windows.ResourceKey> . `MyStyle`est supposé être la valeur [x :Key](../../../desktop-wpf/xaml-services/xkey-directive.md) d’un <xref:System.Windows.Style> défini en tant que ressource. L’utilisation de l' [extension de balisage StaticResource](staticresource-markup-extension.md) demande que la ressource soit utilisée pour fournir la valeur de la <xref:System.Windows.Style> propriété par le biais d’une logique de recherche de ressources statiques au moment du chargement.  
  
 Pour plus d’informations sur les extensions de balisage, consultez [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md). Pour obtenir une référence des extensions de balisage et d’autres fonctionnalités de programmation XAML activées dans l’implémentation .NET XAML générale, consultez [espace de noms XAML (x :) Fonctionnalités de langage](../../../desktop-wpf/xaml-services/namespace-language-features.md). Pour les extensions de balisage spécifiques à WPF, consultez [Extensions XAML WPF](wpf-xaml-extensions.md).  
  
<a name="attached_properties"></a>
## <a name="attached-properties"></a>Propriétés attachées  
 Les propriétés jointes sont un concept de programmation introduit dans XAML, selon lequel les propriétés peuvent être détenues et définies par un type particulier, mais définies comme des attributs ou des éléments de propriété sur tout élément. Le scénario principal auquel les propriétés jointes sont destinées consiste à permettre aux éléments enfants dans une structure de balisage de rapporter des informations à un élément parent sans avoir besoin d’un modèle d’objet largement partagé sur tous les éléments. À l’inverse, les propriétés jointes peuvent être utilisées par les éléments parents pour signaler des informations à des éléments enfants. Pour plus d’informations sur l’objectif des propriétés jointes et sur la création de vos propres propriétés jointes, consultez [vue d’ensemble des propriétés](attached-properties-overview.md)jointes.  
  
 Les propriétés jointes utilisent une syntaxe qui ressemble superficiellement à la syntaxe des éléments de propriété, en ce que vous spécifiez également un *TypeName*. combinaison de *NomPropriété* . Il existe deux différences majeures :  
  
- Vous pouvez utiliser le *TypeName*. combinaison de *NomPropriété* même lors de la définition d’une propriété jointe par le biais de la syntaxe d’attribut. Les propriétés jointes sont le seul cas où le fait de qualifier le nom de la propriété est une exigence dans une syntaxe d’attribut.  
  
- Vous pouvez également utiliser la syntaxe d’élément de propriété pour les propriétés jointes. Toutefois, pour la syntaxe d’élément de propriété typique, le *TypeName* que vous spécifiez est l’élément objet qui contient l’élément de propriété. Si vous faites référence à une propriété jointe, *TypeName* est la classe qui définit la propriété jointe, et non l’élément objet conteneur.  
  
<a name="attached_events"></a>
## <a name="attached-events"></a>Événements attachés  
 Les événements attachés sont un autre concept de programmation introduit en XAML, où les événements peuvent être définis par un type spécifique, mais les gestionnaires peuvent être attachés à n’importe quel élément objet. Dans l’implémentation WOF, souvent le type qui définit un événement attaché est un type statique qui définit un service, et parfois ces événements attachés sont exposés par un alias d’événement routé dans des types qui exposent le service. Les gestionnaires pour les événements attachés sont spécifiés par le biais de la syntaxe d’attribut. Comme pour les événements attachés, la syntaxe d’attribut est développée pour les événements attachés afin d’autoriser un *TypeName*. *EventName* usage, où *TypeName* est la classe qui fournit `Add` les `Remove` accesseurs du gestionnaire d’événements et de l’infrastructure des événements attachés, et *EventName* est le nom de l’événement.  
  
<a name="anatomy_of_a_xaml_page_root_element"></a>
## <a name="anatomy-of-a-xaml-root-element"></a>Anatomie d’un élément racine XAML  
 Le tableau suivant montre un élément racine XAML classique, qui affiche les attributs spécifiques d’un élément racine :  
  
|||  
|-|-|  
|`<Page`|Ouverture de l’élément objet de l’élément racine|  
|`xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`|Espace de noms XAML par défaut ( [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] )|  
|`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`|Espace de noms XAML du langage XAML|  
|`x:Class="ExampleNamespace.ExampleCode"`|Déclaration de classe partielle qui connecte le balisage à tout code-behind défini pour la classe partielle|  
|`>`|Fin de l’élément objet pour la racine. L’objet n’est pas encore fermé, car l’élément contient des éléments enfants|  
  
<a name="optional_and_nonrecommended_xaml_usages"></a>
## <a name="optional-and-nonrecommended-xaml-usages"></a>Utilisations de XAML facultatives et déconseillées  
 Les sections suivantes décrivent les utilisations XAML techniquement prises en charge par les processeurs XAML, mais qui produisent des commentaires ou d’autres problèmes esthétiques qui interfèrent avec les fichiers XAML qui restent explicites quand vous développez des applications qui contiennent des sources XAML.  
  
### <a name="optional-property-element-usages"></a>Utilisations facultatives des éléments de propriété  
 Les utilisations facultatives des éléments de propriété incluent l’écriture explicite de propriétés de contenu d’élément que le processeur XAML considère comme étant implicites. Par exemple, lorsque vous déclarez le contenu d’un <xref:System.Windows.Controls.Menu> , vous pouvez choisir de déclarer explicitement la <xref:System.Windows.Controls.ItemsControl.Items%2A> collection du <xref:System.Windows.Controls.Menu> en tant que `<Menu.Items>` balise d’élément de propriété, et de placer chacun <xref:System.Windows.Controls.MenuItem> dans `<Menu.Items>` , au lieu d’utiliser le comportement de processeur XAML implicite dont tous les éléments enfants d’un <xref:System.Windows.Controls.Menu> doivent être un <xref:System.Windows.Controls.MenuItem> et sont placés dans la <xref:System.Windows.Controls.ItemsControl.Items%2A> collection. Parfois, les utilisations facultatives peuvent aider à clarifier visuellement la structure de l’objet, comme représenté dans le balisage. Ou parfois, une utilisation d’élément de propriété explicite peut éviter le balisage techniquement fonctionnel mais visuellement confus, comme les extensions de balisage imbriquées dans une valeur d’attribut.  
  
### <a name="full-typenamemembername-qualified-attributes"></a>Attributs qualifiés typeName. memberName complets  
 *TypeName*. le formulaire *MemberName* d’un attribut fonctionne en fait plus universellement que le seul cas d’événement routé. Mais dans d’autres situations, la forme est superflue et vous devez l’éviter, si uniquement pour des raisons de style et de lisibilité du balisage. Dans l’exemple suivant, chacune des trois références à l' <xref:System.Windows.Controls.Control.Background%2A> attribut est complètement équivalente :  
  
 [!code-xaml[XAMLOvwSupport#TypeNameProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenameprop)]  
  
 `Button.Background`fonctionne, car la recherche qualifiée pour cette propriété sur <xref:System.Windows.Controls.Button> est réussie ( <xref:System.Windows.Controls.Control.Background%2A> a été héritée de Control) et <xref:System.Windows.Controls.Button> est la classe de l’élément objet ou d’une classe de base. `Control.Background`fonctionne parce que la <xref:System.Windows.Controls.Control> classe définit réellement <xref:System.Windows.Controls.Control.Background%2A> et qu' <xref:System.Windows.Controls.Control> il s’agit d’une <xref:System.Windows.Controls.Button> classe de base.  
  
 Toutefois, le *TypeName*suivant. l’exemple de formulaire *MemberName* ne fonctionne pas et est donc représenté par commenté :  
  
 [!code-xaml[XAMLOvwSupport#TypeNameBadProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenamebadprop)]  
  
 <xref:System.Windows.Controls.Label>est une autre classe dérivée de <xref:System.Windows.Controls.Control> , et si vous aviez spécifié `Label.Background` dans un <xref:System.Windows.Controls.Label> élément objet, cette utilisation aurait fonctionné. Toutefois, étant donné que <xref:System.Windows.Controls.Label> n’est pas la classe ou la classe de base de <xref:System.Windows.Controls.Button> , le comportement de processeur XAML spécifié doit ensuite être traité `Label.Background` comme une propriété jointe. `Label.Background`n’est pas une propriété jointe disponible, et cette utilisation échoue.  
  
### <a name="basetypenamemembername-property-elements"></a>baseTypeName. memberName, éléments de propriété  
 D’une manière analogue à la façon dont le *TypeName*. le formulaire *MemberName* fonctionne pour la syntaxe d’attribut, un *BaseTypeName*. la syntaxe *MemberName* fonctionne pour la syntaxe des éléments de propriété. Par exemple, la syntaxe suivante fonctionne :  
  
 [!code-xaml[XAMLOvwSupport#GoofyPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofype)]  
  
 Ici, l’élément Property a été donné comme `Control.Background` même si l’élément Property était contenu dans `Button` .  
  
 Mais tout comme *TypeName*. formulaire *MemberName* pour les attributs, *BaseTypeName*. *MemberName* est un style médiocre dans le balisage et vous devez l’éviter.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Espace de noms XAML (x:) Fonctionnalités de langage](../../../desktop-wpf/xaml-services/namespace-language-features.md)
- [Extensions XAML WPF](wpf-xaml-extensions.md)
- [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md)
- [TypeConverters et XAML](typeconverters-and-xaml.md)
- [XAML et classes personnalisées pour WPF](xaml-and-custom-classes-for-wpf.md)
