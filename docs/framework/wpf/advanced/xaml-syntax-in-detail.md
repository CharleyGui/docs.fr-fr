---
title: Syntaxe XAML en détail
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
ms.openlocfilehash: dbff4bed59c8d1e861555676578b52528e2aebbe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186184"
---
# <a name="xaml-syntax-in-detail"></a>Syntaxe XAML en détail
Ce sujet définit les termes qui sont utilisés pour décrire les éléments de la syntaxe XAML. Ces termes sont fréquemment utilisés tout au long du reste de cette documentation, à la fois pour la documentation WPF spécifiquement et pour les autres cadres qui utilisent XAML ou les concepts XAML de base activés par le support linguistique XAML au niveau System.Xaml. Ce sujet s’étend sur la terminologie de base introduite dans le sujet [XAML Aperçu (WPF)](../../../desktop-wpf/fundamentals/xaml.md).  

<a name="the_xaml_language_specification"></a>
## <a name="the-xaml-language-specification"></a>La spécification linguistique XAML  
 La terminologie syntaxe XAML définie ici est également définie ou référencée dans la spécification de la langue XAML. XAML est une langue basée sur XML et suit ou élargit les règles structurelles XML. Une partie de la terminologie est partagée à partir ou est basée sur la terminologie couramment utilisée lors de la description de la langue XML ou le modèle d’objet de document XML.  
  
 Pour plus d’informations sur les spécifications linguistiques XAML, téléchargez [ \[MS-XAML\] ](https://download.microsoft.com/download/0/A/6/0A6F7755-9AF5-448B-907D-13985ACCF53E/[MS-XAML].pdf) à partir du Microsoft Download Center.  
  
<a name="xaml_and_clr"></a>
## <a name="xaml-and-clr"></a>XAML et CLR  
 XAML est un langage de balisage. L’heure courante de l’exécution de langue (CLR), comme l’implique son nom, permet l’exécution de l’exécution de l’exécution. XAML n’est pas en soi l’une des langues communes qui est directement consommée par le temps d’exécution CLR. Au lieu de cela, vous pouvez penser à XAML comme soutenant son propre système de type. Le système d’analyse XAML particulier qui est utilisé par WPF est construit sur le CLR et le système de type CLR. Les types XAML sont cartographiés sur les types CLR pour instantanér une représentation du temps d’exécution lorsque le XAML pour WPF est analysé. Pour cette raison, le reste de la discussion de la syntaxe dans ce document comprendra des références au système de type CLR, même si les discussions linguistiques équivalentes dans la spécification linguistique XAML ne le font pas. (Selon le niveau de spécification de langue XAML, les types XAML pourraient être cartographiés à tout autre système de type, qui n’a pas besoin d’être le CLR, mais qui nécessiterait la création et l’utilisation d’un analyseur XAML différent.)  
  
#### <a name="members-of-types-and-class-inheritance"></a>Membres de Types et De l’Héritage de classe  
 Propriétés et événements tels qu’ils [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] apparaissent en tant que membres XAML d’un type sont souvent hérités des types de base. Par exemple, considérez `<Button Background="Blue" .../>`cet exemple: . La <xref:System.Windows.Controls.Control.Background%2A> propriété n’est pas <xref:System.Windows.Controls.Button> une propriété immédiatement déclarée sur la classe, si vous devait examiner la définition de classe, les résultats de réflexion, ou la documentation. Au <xref:System.Windows.Controls.Control.Background%2A> lieu de cela, est hérité de la classe de base. <xref:System.Windows.Controls.Control>  
  
 Le comportement d’héritage de classe des [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] éléments XAML est un écart significatif d’une interprétation schéma-forcée de la balisage XML. L’héritage de classe peut devenir complexe, en particulier lorsque les classes intermédiaires de base sont abstraites, ou lorsque des interfaces sont impliquées. C’est l’une des raisons pour lesquelles l’ensemble d’éléments XAML et leurs attributs autorisés est difficile à représenter avec précision et complètement en utilisant les types de schémas qui sont généralement utilisés pour la programmation XML, tels que le format DTD ou XSD. Une autre raison est que l’extéabilité et les caractéristiques de cartographie de type de la langue XAML elle-même empêchent l’exhaustivité de toute représentation fixe des types et des membres autorisés.  
  
<a name="object_element_syntax"></a>
## <a name="object-element-syntax"></a>Syntaxe de l’élément objet  
 *La syntaxe d’élément d’objet* est la syntaxe de balisage XAML qui instantanéise une classe ou une structure CLR en déclarant un élément XML. Cette syntaxe ressemble à l’élément syntaxe d’autres langages de balisage tels que HTML. La syntaxe d’élément d’objet commence par un support d’angle gauche (),\<suivi immédiatement du nom de type de la classe ou de la structure en cours d’instantané. Zéro ou plusieurs espaces peuvent suivre le nom de type, et zéro ou plusieurs attributs peuvent également être déclarés sur l’élément objet, avec un ou plusieurs espaces séparant chaque nom d’attribut "valeur" paire. Enfin, l’un des éléments suivants doit être vrai :  
  
- L’élément et l’étiquette doivent être fermés par une barre oblique avant (/) suivie immédiatement d’un support d’angle droit (>).  
  
- L’étiquette d’ouverture doit être complétée par un support d’angle droit (>). D’autres éléments d’objets, éléments de propriété ou texte intérieur peuvent suivre l’étiquette d’ouverture. Exactement ce que le contenu peut être contenu ici est généralement limité par le modèle d’objet de l’élément. L’étiquette de fermeture équivalente pour l’élément objet doit également exister, dans la nidification et l’équilibre appropriés avec d’autres paires d’étiquettes d’ouverture et de fermeture.  
  
 XAML tel qu’implémenté par .NET a un ensemble de règles qui cartographient les éléments d’objets en types, attributs en propriétés ou événements, et XAML namespaces aux espaces de noms CLR plus l’assemblage. Pour WPF et .NET, les éléments d’objets XAML sont cartographiques pour les types .NET tels que définis dans les assemblages référencés, et la carte des attributs aux membres de ces types. Lorsque vous faites référence à un type CLR dans XAML, vous avez également accès aux membres hérités de ce type.  
  
 Par exemple, l’exemple suivant est la syntaxe d’élément objet qui instantanéise une nouvelle instance de la <xref:System.Windows.Controls.Button> classe, et précise également un <xref:System.Windows.FrameworkElement.Name%2A> attribut et une valeur pour cet attribut :  
  
 [!code-xaml[XAMLOvwSupport#SyntaxOE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxoe)]  
  
 L’exemple suivant est la syntaxe d’élément d’objet qui inclut également la syntaxe de propriété de contenu XAML. Le texte intérieur contenu dans sera <xref:System.Windows.Controls.TextBox> utilisé pour définir <xref:System.Windows.Controls.TextBox.Text%2A>la propriété de contenu XAML, .  
  
 [!code-xaml[XAMLOvwSupport#ThisIsATextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#thisisatextbox)]  
  
### <a name="content-models"></a>Modèles de contenu  
 Une classe peut prendre en charge une utilisation en tant qu’élément d’objet XAML en termes de syntaxe, mais cet élément ne fonctionnera correctement dans une application ou une page lorsqu’il est placé dans une position prévue d’un modèle de contenu global ou d’un arbre d’élément. Par exemple, <xref:System.Windows.Controls.MenuItem> un ne devrait généralement être <xref:System.Windows.Controls.Primitives.MenuBase> placé que <xref:System.Windows.Controls.Menu>comme un enfant d’une classe dérivée comme . Les modèles de contenu pour des éléments spécifiques sont documentés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans le cadre des remarques sur les pages de classe pour les contrôles et autres classes qui peuvent être utilisés comme éléments XAML.  
  
<a name="properties_of_object_elements"></a>
## <a name="properties-of-object-elements"></a>Propriétés des éléments d’objet  
 Les propriétés de XAML sont définies par une variété de syntaxes possibles. Quelle syntaxe peut être utilisée pour une propriété particulière variera, en fonction des caractéristiques du système de type sous-jacent de la propriété que vous définissez.  
  
 En définissant des valeurs de propriétés, vous ajoutez des fonctionnalités ou des caractéristiques aux objets tels qu’ils existent dans le graphique de l’objet temporel. L’état initial de l’objet créé à partir d’un élément d’objet est basé sur le comportement du constructeur sans paramètres. En règle générale, votre application utilisera autre chose qu’une instance par défaut complète de n’importe quel objet donné.  
  
<a name="attribute_syntax_properties"></a>
## <a name="attribute-syntax-properties"></a>Syntaxe d’attribut (Propriétés)  
 La syntaxe d’attribut est la syntaxe de balisage XAML qui établit une valeur pour une propriété en déclarant un attribut sur un élément d’objet existant. Le nom d’attribut doit correspondre au nom du membre CLR de la propriété de la classe qui soutient l’élément objet pertinent. Le nom d’attribut est suivi par un opérateur d’affectation (MD). La valeur d’attribut doit être une chaîne jointe dans les devis.  
  
> [!NOTE]
> Vous pouvez utiliser des citations alternées pour placer une marque de citation littérale dans un attribut. Par exemple, vous pouvez utiliser des citations simples comme un moyen de déclarer une chaîne qui contient un caractère de double devis en son sein. Que vous utilisiez des devis simples ou doubles, vous devez utiliser une paire assortie pour ouvrir et fermer la chaîne de valeur d’attribut. Il existe également des séquences d’évasion ou d’autres techniques disponibles pour travailler autour des restrictions de caractère imposées par une syntaxe XAML particulière. Voir [XML Character Entities et XAML](../../../desktop-wpf/xaml-services/xml-character-entities.md).  
  
 Pour être définie par la syntaxe d’attribut, une propriété doit être publique et doit être écrivante. La valeur de la propriété dans le système de type support doit être un type de valeur, ou doit être un type de référence qui peut être instantanée ou référencée par un processeur XAML lors de l’accès au type de sauvegarde pertinent.  
  
 Pour les événements WPF XAML, l’événement qui est référencé comme le nom d’attribut doit être public et avoir un délégué public.  
  
 La propriété ou l’événement doit être un membre de la classe ou de la structure qui est instantanée par l’élément d’objet contenant.  
  
### <a name="processing-of-attribute-values"></a>Traitement des valeurs d’attributs  
 La valeur de chaîne contenue dans les guillemets d’ouverture et de clôture est traitée par un processeur XAML. Pour les propriétés, le comportement de traitement par défaut est déterminé par le type de propriété SOUS-jacente CLR.  
  
 La valeur d’attribut est remplie par l’un des éléments suivants, en utilisant cet ordre de traitement :  
  
1. Si le processeur XAML rencontre une accolade bouclée, <xref:System.Windows.Markup.MarkupExtension>ou un élément d’objet qui dérive de , puis l’extension de balisage référencée est évaluée d’abord plutôt que de traiter la valeur comme une chaîne, et l’objet retourné par l’extension de balisage est utilisé comme la valeur. Dans de nombreux cas, l’objet retourné par une extension de balisage sera une référence à un objet existant, ou une expression qui reporte l’évaluation jusqu’au moment de l’exécution, et n’est pas un objet nouvellement instantané.  
  
2. Si la propriété est <xref:System.ComponentModel.TypeConverter>déclarée avec un attribut, ou le <xref:System.ComponentModel.TypeConverter>type de valeur de cette propriété est déclaré avec un attribué , la valeur de chaîne de l’attribut est soumise au convertisseur de type comme entrée de conversion, et le convertisseur retournera une nouvelle instance d’objet.  
  
3. S’il <xref:System.ComponentModel.TypeConverter>n’y a pas, une conversion directe au type de propriété est tentée. Ce niveau final est une conversion directe à la valeur parser-native entre les types primitifs de langue XAML, ou un contrôle pour les noms des constantes nommées dans un énumération (le parseur accède alors aux valeurs correspondantes).  
  
#### <a name="enumeration-attribute-values"></a>Valeurs d’attribut d’énumération  
 Les énumérations dans XAML sont traitées intrinsèquement par des analyseurs XAML, et les membres d’un recensement doivent être spécifiés en spécifiant le nom de chaîne de l’une des constantes nommées de l’énumération.  
  
 Pour les valeurs d’énumération non-flag, le comportement natif est de traiter la chaîne d’une valeur d’attribut et de la résoudre à l’une des valeurs d’énumération. Vous ne spécifiez pas l’énumération dans le format *Énumération*. *Valeur*, comme vous le faites dans le code. Au lieu de cela, vous spécifiez seulement *la valeur*, et *l’énumération* est déduite par le type de propriété que vous définissez. Si vous spécifiez un attribut dans *l’énumération*. Forme de *valeur,* il ne résoudra pas correctement.  
  
 Pour les énumérations dans le sens <xref:System.Enum.Parse%2A?displayProperty=nameWithType> du signal, le comportement est basé sur la méthode. Vous pouvez spécifier plusieurs valeurs pour un recensement du drapeau en séparant chaque valeur par une virgule. Cependant, vous ne pouvez pas combiner des valeurs d’énumération qui ne sont pas dans le sens du signalement. Par exemple, vous ne pouvez pas utiliser la <xref:System.Windows.Trigger> syntaxe virgule pour tenter de créer un qui agit sur de multiples conditions d’un recensement non enflammé :  
  
```xaml  
<!--This will not compile, because Visibility is not a flagwise enumeration.-->  
...  
<Trigger Property="Visibility" Value="Collapsed,Hidden">  
  <Setter ... />  
</Trigger>  
...  
```  
  
 Les énumérations flagwise qui prennent en charge les attributs qui sont définis dans XAML sont rares dans WPF. Cependant, l’un de <xref:System.Windows.Media.StyleSimulations>ces énumérations est . Vous pouvez, par exemple, utiliser la syntaxe d’attribut signalaire délimitée <xref:System.Windows.Documents.Glyphs> pour modifier l’exemple fourni dans les Remarques pour la classe; `StyleSimulations = "BoldSimulation"` pourrait `StyleSimulations = "BoldSimulation,ItalicSimulation"`devenir . <xref:System.Windows.Input.KeyBinding.Modifiers%2A?displayProperty=nameWithType>est une autre propriété où plus d’une valeur d’énumération peut être spécifiée. Cependant, cette propriété se trouve être <xref:System.Windows.Input.ModifierKeys> un cas spécial, parce que le recensement prend en charge son propre convertisseur de type. Le convertisseur de type pour modificateurs utilise un signe plus (en) comme délimitateur plutôt qu’une virgule (,). Cette conversion prend en charge la syntaxe plus traditionnelle pour représenter les combinaisons clés de la programmation Microsoft Windows, telles que "Ctrl-Alt".  
  
### <a name="properties-and-event-member-name-references"></a>Références de nom des propriétés et des membres de l’événement  
 Lorsque vous spécifiez un attribut, vous pouvez faire référence à toute propriété ou événement qui existe en tant que membre du type CLR que vous avez instantané pour l’élément objet contenant.  
  
 Ou, vous pouvez faire référence à une propriété jointe ou à un événement joint, indépendamment de l’élément objet contenant. (Les propriétés ci-jointes sont discutées dans une section à venir.)  
  
 Vous pouvez également nommer n’importe quel événement à partir de n’importe quel objet qui est accessible par l’espace nom par défaut en utilisant un *typeName*. nom partiellement qualifié de *l’événement;* cette syntaxe prend en charge l’attachement des gestionnaires pour les événements acheminés où le gestionnaire est destiné à gérer les événements de routage à partir d’éléments enfant, mais l’élément parent n’a pas aussi cet événement dans sa table des membres. Cette syntaxe ressemble à une syntaxe événement ci-jointe, mais l’événement ici n’est pas un véritable événement ci-joint. Au lieu de cela, vous faites référence à un événement avec un nom qualifié. Pour plus d’informations, voir [Aperçu des événements acheminés](routed-events-overview.md).  
  
 Pour certains scénarios, les noms de propriété sont parfois fournis comme la valeur d’un attribut, plutôt que le nom d’attribut. Ce nom de propriété peut également inclure des qualificatifs, tels que la propriété spécifiée dans le propriétaire de *formeType*. *dépendancePropertyName*. Ce scénario est courant lors de l’écriture de styles ou de modèles dans XAML. Les règles de traitement des noms de propriété fournies comme valeur d’attribut sont différentes, et sont régies par le type de propriété étant définie ou par les comportements de sous-systèmes WPF particuliers. Pour plus de détails, voir [Styling and Templating](../controls/styling-and-templating.md).  
  
 Une autre utilisation pour les noms de propriété est quand une valeur d’attribut décrit une relation propriété-propriété. Cette fonctionnalité est utilisée pour la liaison de données <xref:System.Windows.PropertyPath> et pour les cibles storyboard, et est activée par la classe et son convertisseur de type. Pour une description plus complète de la sémantique de recherche, voir [PropertyPath XAML Syntax](propertypath-xaml-syntax.md).  
  
<a name="property_element_syntax"></a>
## <a name="property-element-syntax"></a>Syntaxe des éléments de propriété  
 *La syntaxe d’élément de propriété* est une syntaxe qui diverge quelque peu des règles de base de syntaxe XML pour les éléments. Dans XML, la valeur d’un attribut est une chaîne de facto, la seule variante possible étant le format d’encodage des cordes qui est utilisé. Dans XAML, vous pouvez attribuer d’autres éléments d’objet pour être la valeur d’une propriété. Cette capacité est activée par la syntaxe de l’élément de propriété. Au lieu que la propriété soit spécifiée comme attribut dans l’étiquette d’élément, la propriété est spécifiée à l’aide d’une étiquette d’élément d’ouverture dans *elementTypeName*. *formulaire de propriétéName,* la valeur de la propriété est spécifiée à l’intérieur, puis l’élément de propriété est fermé.  
  
 Plus précisément, la syntaxe commence\<par un support d’angle gauche (), suivi immédiatement par le nom de type de la classe ou de la structure que la syntaxe d’élément de propriété est contenue dans. Elle est immédiatement suivie d’un seul point (.), puis du nom d’une propriété, puis d’un support d’angle droit (>). Comme pour la syntaxe d’attribut, cette propriété doit exister au sein des membres publics déclarés du type spécifié. La valeur à attribuer à la propriété est contenue dans l’élément propriété. Typiquement, la valeur est donnée comme un ou plusieurs éléments d’objet, parce que spécifier des objets comme valeurs est le scénario que la syntaxe d’élément de propriété est destinée à traiter. Enfin, une balise de clôture équivalente spécifiant le même *élémentTypeName*. *propriété La* combinaison de noms de propriété doit être fournie, dans la nidification et l’équilibre appropriés avec d’autres étiquettes d’élément.  
  
 Par exemple, ce qui suit est <xref:System.Windows.FrameworkElement.ContextMenu%2A> la <xref:System.Windows.Controls.Button>syntaxe d’élément de propriété pour la propriété d’un .  
  
 [!code-xaml[XAMLOvwSupport#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#contextmenu)]  
  
 La valeur dans un élément de propriété peut également être donnée comme texte intérieur, dans <xref:System.String>les cas où le type de propriété spécifié est un type de valeur primitive, tel que, ou un recensement où un nom est spécifié. Ces deux utilisations sont quelque peu rares, parce que chacun de ces cas pourrait également utiliser une syntaxe d’attribut plus simple. Un scénario pour remplir un élément de propriété avec une chaîne est pour les propriétés qui ne sont pas la propriété de contenu XAML, mais sont toujours utilisés pour la représentation du texte de l’interface utilisateur, et certains éléments de l’espace blanc tels que les filoires sont tenus d’apparaître dans ce texte d’interface utilisateur. La syntaxe d’attribut ne peut pas préserver les filoires, mais la syntaxe d’élément de propriété peut, tant que la conservation significative de l’espace blanc est active (pour plus de détails, voir [traitement de l’espace blanc dans XAML](../../../desktop-wpf/xaml-services/white-space-processing.md)). Un autre scénario est de sorte que [x:Uid Directive](../../../desktop-wpf/xaml-services/xuid-directive.md) peut être appliquée à l’élément de propriété et ainsi marquer la valeur à l’intérieur comme une valeur qui devrait être localisée dans la sortie WPF BAML ou par d’autres techniques.  
  
 Un élément de propriété n’est pas représenté dans l’arbre logique WPF. Un élément de propriété est juste une syntaxe particulière pour fixer une propriété, et n’est pas un élément qui a une instance ou un objet le soutenant. (Pour plus de détails sur le concept d’arbre logique, voir [Arbres dans WPF](trees-in-wpf.md).)  
  
 Pour les propriétés où la syntaxe d’attribut et d’élément de propriété sont soutenues, les deux syntaxes ont généralement le même résultat, bien que les subtilités telles que la manipulation de l’espace blanc puissent varier légèrement entre les syntaxes.  
  
<a name="collection_syntax"></a>
## <a name="collection-syntax"></a>Syntaxe des collections  
 La spécification XAML nécessite des implémentations de processeurS XAML pour identifier les propriétés où le type de valeur est une collection. La mise en œuvre générale du processeur XAML en .NET est basée sur le code géré et le CLR, et il identifie les types de collecte à travers l’un des éléments suivants:  
  
- Types d’outils <xref:System.Collections.IList>.  
  
- Types d’outils <xref:System.Collections.IDictionary>.  
  
- Type dérive <xref:System.Array> de (pour plus d’informations sur les tableaux dans XAML, voir [x:Array Markup Extension](../../../desktop-wpf/xaml-services/xarray-markup-extension.md).)  
  
 Si le type de propriété est une collection, alors le type de collecte déduit n’a pas besoin d’être spécifié dans la majoration comme un élément d’objet. Au lieu de cela, les éléments qui sont destinés à devenir les éléments de la collection sont spécifiés comme un ou plusieurs éléments enfant de l’élément de propriété. Chaque élément de ce type est évalué à un objet `Add` pendant le chargement et ajouté à la collection en appelant la méthode de la collection implicite. Par exemple, <xref:System.Windows.Style.Triggers%2A> la <xref:System.Windows.Style> propriété de <xref:System.Windows.TriggerCollection>prend le <xref:System.Collections.IList>type de collecte spécialisée , qui met en œuvre . Il n’est pas nécessaire <xref:System.Windows.TriggerCollection> d’instantanér un élément d’objet dans la balisage. Au lieu de cela, vous spécifiez un ou <xref:System.Windows.Trigger> plusieurs éléments comme éléments dans `Style.Triggers` l’élément de propriété, où <xref:System.Windows.Trigger> (ou une classe dérivée) est le type attendu comme le type d’élément pour le fortement tapé et implicite <xref:System.Windows.TriggerCollection>.  
  
 [!code-xaml[XAMLOvwSupport#SyntaxPECollection](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxpecollection)]  
  
 Une propriété peut être à la fois un type de collection et la propriété de contenu XAML pour ce type et les types dérivés, qui est discuté dans la section suivante de ce sujet.  
  
 Un élément de collecte implicite crée un membre dans la représentation logique des arbres, même s’il n’apparaît pas dans la majoration comme un élément. Habituellement, le constructeur du type parent effectue l’instantanéisation de la collection qui est l’une de ses propriétés, et la collection initialement vide devient une partie de l’arbre objet.  
  
> [!NOTE]
> La liste générique et<xref:System.Collections.Generic.IList%601> les <xref:System.Collections.Generic.IDictionary%602>interfaces de dictionnaire ( et ) ne sont pas prises en charge pour la détection de la collecte. Cependant, vous pouvez <xref:System.Collections.Generic.List%601> utiliser la classe comme une <xref:System.Collections.IList> classe <xref:System.Collections.Generic.Dictionary%602> de base, parce qu’elle implémente directement, ou comme classe de base, parce qu’elle implémente <xref:System.Collections.IDictionary> directement.  
  
 Dans les pages de référence .NET pour les types de collecte, cette syntaxe avec l’omission délibérée de l’élément objet pour une collection est parfois notée dans les sections syntaxe XAML comme Syntax de collection implicite.  
  
 À l’exception de l’élément racine, chaque élément d’objet dans un fichier XAML qui est imbriqué comme un élément enfant d’un autre élément est vraiment un élément qui est l’un ou les deux cas suivants: un membre d’une propriété de collecte implicite de son élément parent , ou un élément qui spécifie la valeur de la propriété de contenu XAML pour l’élément parent (les propriétés de contenu XAML seront discutées dans une section à venir). En d’autres termes, la relation entre les éléments parents et les éléments de l’enfant dans une page de balisage est en réalité un seul objet à la racine, et chaque élément d’objet sous la racine est soit une seule instance qui fournit une valeur de propriété du parent, ou l’un des éléments dans un qui est aussi une valeur de propriété de type collection du parent. Ce concept à racine unique est commun avec XML, et est souvent renforcé <xref:System.Windows.Markup.XamlReader.Load%2A>dans le comportement des API qui chargent XAML tels que .  
  
 L’exemple suivant est une syntaxe avec<xref:System.Windows.Media.GradientStopCollection>l’élément objet pour une collection ( ) spécifiée explicitement.  
  
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
  
 Notez qu’il n’est pas toujours possible de déclarer explicitement la collection. Par exemple, tenter <xref:System.Windows.TriggerCollection> de déclarer <xref:System.Windows.Style.Triggers%2A> explicitement dans l’exemple précédemment montré échouerait. Déclarer explicitement la collection exige que la classe de collecte <xref:System.Windows.TriggerCollection> doit prendre en charge un constructeur sans paramètres, et n’a pas de constructeur sans paramètres.  
  
<a name="xaml_content_properties"></a>
## <a name="xaml-content-properties"></a>Propriétés de contenu XAML  
 La syntaxe de contenu XAML est une syntaxe qui n’est activée que sur les classes qui spécifient le dans le <xref:System.Windows.Markup.ContentPropertyAttribute> cadre de leur déclaration de classe. Les <xref:System.Windows.Markup.ContentPropertyAttribute> références au nom de propriété qui est la propriété de contenu pour ce type d’élément (y compris les classes dérivées). Lorsqu’il est traité par un processeur XAML, tous les éléments pour enfants ou le texte intérieur qui se trouvent entre les balises d’ouverture et de fermeture de l’élément objet seront attribués pour être la valeur de la propriété de contenu XAML pour cet objet. Vous êtes autorisé à spécifier des éléments de propriété explicites pour la propriété de contenu, mais cette utilisation n’est généralement pas indiquée dans les sections syntaxes XAML dans la référence .NET. La technique explicite/verbeuse a une valeur occasionnelle pour la clarté de balisage ou comme une question de style de balisage, mais généralement l’intention d’une propriété de contenu est de rationaliser le balisage de sorte que les éléments qui sont intuitivement liés comme parent-enfant peuvent être imbriqués directement. Les étiquettes d’élément de propriété pour d’autres propriétés d’un élément ne sont pas assignées comme « contenu » par définition de langue XAML stricte ; ils sont traités précédemment dans l’ordonnance de traitement du parser XAML et ne sont pas considérés comme des « contenus ».  
  
### <a name="xaml-content-property-values-must-be-contiguous"></a>XAML Content Propriété Valeurs doivent être contigus  
 La valeur d’une propriété de contenu XAML doit être donnée soit entièrement avant ou entièrement après tout autre élément de propriété sur cet élément d’objet. Cela est vrai si la valeur d’une propriété de contenu XAML est spécifiée comme une chaîne, ou comme un ou plusieurs objets. Par exemple, la majoration suivante n’analyse pas :  
  
```xaml  
<Button>I am a
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 Ceci est illégal essentiellement parce que si cette syntaxe ont été rendues explicites en utilisant la syntaxe d’élément de propriété pour la propriété de contenu, alors la propriété de contenu serait réglée deux fois :  
  
```xaml  
<Button>  
  <Button.Content>I am a </Button.Content>  
  <Button.Background>Blue</Button.Background>  
  <Button.Content> blue button</Button.Content>  
</Button>  
```  
  
 Un exemple tout aussi illégal est celui où la propriété de contenu est une collection, et les éléments pour enfants sont entrecoupés d’éléments de propriété :  
  
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
 Afin d’accepter plus d’un seul élément d’objet comme contenu, le type de propriété de contenu doit être spécifiquement un type de collection. Semblable à la syntaxe d’élément de propriété pour les types de collection, un processeur XAML doit identifier les types qui sont des types de collecte. Si un élément a une propriété de contenu XAML et le type de la propriété de contenu XAML est une collection, alors le type de collecte implicite n’a pas besoin d’être spécifié dans la balisage comme un élément d’objet et la propriété de contenu XAML n’a pas besoin d’être spécifié comme une propriété Élément. Par conséquent, le modèle de contenu apparent dans la balisage peut maintenant avoir plus d’un élément enfant attribué comme le contenu. Ce qui suit est <xref:System.Windows.Controls.Panel> la syntaxe de contenu pour une classe dérivée. Toutes <xref:System.Windows.Controls.Panel> les classes dérivées établissent la <xref:System.Windows.Controls.Panel.Children%2A>propriété de contenu <xref:System.Windows.Controls.UIElementCollection>XAML à être , ce qui nécessite une valeur de type .  
  
 [!code-xaml[XAMLOvwSupport#SyntaxContent](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page5.xaml#syntaxcontent)]  
  
 Notez que ni <xref:System.Windows.Controls.Panel.Children%2A> l’élément de <xref:System.Windows.Controls.UIElementCollection> propriété ni l’élément pour le n’est requis dans la majoration. Il s’agit d’une caractéristique de conception de XAML de sorte que les éléments contenus de façon récursive qui définissent un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] sont plus intuitivement représentés comme un arbre d’éléments imbriqués avec des relations immédiates élément parent-enfant, sans intervenir étiquettes élément de propriété ou objets de collecte. En fait, <xref:System.Windows.Controls.UIElementCollection> ne peut pas être spécifié explicitement dans la balisage comme un élément d’objet, par conception. Parce que sa seule utilisation prévue <xref:System.Windows.Controls.UIElementCollection> est comme une collection implicite, n’expose pas un constructeur public sans paramètres et ne peut donc pas être instantanée comme un élément d’objet.  
  
### <a name="mixing-property-elements-and-object-elements-in-an-object-with-a-content-property"></a>Mélanger les éléments de propriété et les éléments d’objets dans un objet avec une propriété de contenu  
 La spécification XAML déclare qu’un processeur XAML peut appliquer les éléments d’objet qui sont utilisés pour remplir la propriété de contenu XAML dans un élément d’objet doit être contigu, et ne doit pas être mélangé. Cette restriction contre le mélange des éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de propriété et du contenu est appliquée par les processeurs XAML.  
  
 Vous pouvez avoir un élément d’objet enfant comme premier balisage immédiat dans un élément d’objet. Ensuite, vous pouvez introduire des éléments de propriété. Ou, vous pouvez spécifier un ou plusieurs éléments de propriété, puis le contenu, puis plus d’éléments de propriété. Mais une fois qu’un élément de propriété suit le contenu, vous ne pouvez pas introduire de contenu supplémentaire, vous ne pouvez ajouter que des éléments de propriété.  
  
 Cette exigence d’ordre d’élément de contenu/propriété ne s’applique pas au texte interne utilisé comme contenu. Cependant, il est toujours un bon style de balisage pour garder le texte intérieur contigu, parce que l’espace blanc significatif sera difficile à détecter visuellement dans le balisage si les éléments de propriété sont entrecoupés de texte intérieur.  
  
<a name="xaml_namespaces"></a>
## <a name="xaml-namespaces"></a>Espaces de noms XAML  
 Aucun des exemples syntaxes précédents n’a spécifié un espace de nom XAML autre que l’espace nom XAML par défaut. Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] les applications typiques, l’espace nom [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML par défaut est spécifié pour être l’espace de nom. Vous pouvez spécifier des espaces de nom XAML autres que l’espace nom XAML par défaut et toujours utiliser une syntaxe similaire. Mais alors, n’importe où où une classe est nommée qui n’est pas accessible dans l’espace de nom XAML par défaut, ce nom de classe doit être précédé avec le préfixe de l’espace de nom XAML tel que cartographié à l’espace de nom CLR correspondant. Par exemple, `<custom:Example/>` est la syntaxe d’élément `Example` d’objet pour instantanéiser une instance de la classe, où l’espace de `custom` nom CLR contenant cette classe (et peut-être les informations d’assemblage externe qui contient des types de support) a été précédemment cartographié au préfixe.  
  
 Pour plus d’informations sur les espaces de noms XAML, voir [XAML Namespaces et Namespace Mapping pour WPF XAML](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="markup_extensions"></a>
## <a name="markup-extensions"></a>Extensions de balisage  
 XAML définit une entité de programmation d’extension de balisage qui permet de s’échapper de la manipulation normale des valeurs d’attributs de chaîne ou des éléments d’objet par processeur XAML, et reporte le traitement à une classe de support. Le caractère qui identifie une extension de balisage à un processeur XAML lors de l’utilisation de la syntaxe d’attribut est l’accolade bouclée d’ouverture (EN), suivie par tout personnage autre qu’une accolade bouclée de fermeture (). La première chaîne suivant l’accolade bouclée d’ouverture doit faire référence à la classe qui fournit le comportement d’extension particulier, où la référence peut omettre le sous-corde "Extension" si cette sous-corde fait partie du vrai nom de classe. Par la suite, un seul espace peut apparaître, puis chaque personnage qui réussit est utilisé comme entrée par la mise en œuvre de l’extension, jusqu’à ce que l’accolade bouclée de fermeture soit rencontrée.  
  
 La mise en œuvre <xref:System.Windows.Markup.MarkupExtension> .NET XAML utilise la classe abstraite comme base pour toutes les extensions de balisage soutenues par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ainsi que d’autres cadres ou technologies. Les extensions de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] balisage qui implémentent spécifiquement sont souvent destinées à fournir un moyen de référencer d’autres objets existants, ou de faire des références différées à des objets qui seront évalués au moment de l’exécution. Par exemple, une simple liaison de données `{Binding}` WPF est réalisée en spécifiant l’extension de balisage au lieu de la valeur qu’une propriété particulière prendrait habituellement. Bon nombre des extensions de balisage WPF permettent une syntaxe d’attribut pour les propriétés où une syntaxe d’attribut ne serait pas autrement possible. Par exemple, <xref:System.Windows.Style> un objet est un type relativement complexe qui contient une série d’objets et de propriétés imbriqués. Les styles dans WPF sont généralement <xref:System.Windows.ResourceDictionary>définis comme une ressource dans un , puis référencé par l’une des deux extensions de balisage WPF qui demandent une ressource. L’extension de majoration reporte l’évaluation de la valeur de la <xref:System.Windows.FrameworkElement.Style%2A> propriété à <xref:System.Windows.Style>une recherche de ressources et permet de fournir la valeur de la propriété, en prenant le type, en syntaxe d’attribut comme dans l’exemple suivant :  
  
 `<Button Style="{StaticResource MyStyle}">My button</Button>`  
  
 Ici, `StaticResource` identifie <xref:System.Windows.StaticResourceExtension> la classe fournissant la mise en œuvre de l’extension de balisage. La chaîne `MyStyle` suivante est utilisée comme entrée <xref:System.Windows.StaticResourceExtension> pour le constructeur non par défaut, où <xref:System.Windows.ResourceKey>le paramètre tel qu’il est pris à partir de la chaîne d’extension déclare la demande . `MyStyle`devrait être la valeur [x:Key](../../../desktop-wpf/xaml-services/xkey-directive.md) d’un <xref:System.Windows.Style> défini comme une ressource. [L’utilisation de l’extension de markup De StaticResource](staticresource-markup-extension.md) demande que la ressource soit utilisée pour fournir la valeur de propriété par la <xref:System.Windows.Style> logique statique de recherche de ressources au moment de la charge.  
  
 Pour plus d’informations sur les extensions de balisage, consultez [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md). Pour une référence des extensions de balisage et d’autres fonctionnalités de programmation XAML activées dans la implémentation générale .NET XAML, voir [XAML Namespace (x:) Caractéristiques linguistiques](../../../desktop-wpf/xaml-services/namespace-language-features.md). Pour les extensions de balisage spécifiques au WPF, voir [extensions WPF XAML](wpf-xaml-extensions.md).  
  
<a name="attached_properties"></a>
## <a name="attached-properties"></a>Propriétés jointes  
 Les propriétés ci-jointes sont un concept de programmation introduit dans XAML où les propriétés peuvent être détenues et définies par un type particulier, mais définies comme attributs ou éléments de propriété sur n’importe quel élément. Le scénario principal pour lequel les propriétés ci-jointes sont destinées est de permettre aux éléments pour enfants d’une structure de balisage de signaler l’information à un élément parent sans exiger un modèle d’objet largement partagé sur tous les éléments. Inversement, les propriétés ci-jointes peuvent être utilisées par les éléments parentaux pour signaler l’information aux éléments de l’enfant. Pour plus d’informations sur le but des propriétés ci-jointes et comment créer vos propres propriétés ci-jointes, voir [Aperçu des propriétés ci-jointes](attached-properties-overview.md).  
  
 Les propriétés attachées utilisent une syntaxe qui ressemble superficiellement à la syntaxe d’élément de propriété, en ce que vous spécifiez également un *typeName*. *propertyName* combination. Il existe deux différences majeures :  
  
- Vous pouvez utiliser le *typeName*. *propriétéMène* combinaison même lors de la mise d’une propriété attachée par syntaxe attribut. Les propriétés jointes sont le seul cas où la qualification du nom de propriété est une exigence dans une syntaxe d’attribut.  
  
- Vous pouvez également utiliser la syntaxe d’élément de propriété pour les propriétés attachées. Toutefois, pour la syntaxe typique de l’élément de propriété, le *typeName* que vous spécifiez est l’élément objet qui contient l’élément de propriété. Si vous faites référence à une propriété attachée, alors le *typeName* est la classe qui définit la propriété ci-jointe, et non l’élément objet contenant.  
  
<a name="attached_events"></a>
## <a name="attached-events"></a>Événements attachés  
 Les événements ci-joints sont un autre concept de programmation introduit dans XAML où les événements peuvent être définis par un type spécifique, mais les gestionnaires peuvent être attachés sur n’importe quel élément d’objet. Dans la mise en œuvre WOF, souvent le type qui définit un événement ci-joint est un type statique qui définit un service, et parfois ces événements ci-joints sont exposés par un alias événement acheminé dans les types qui exposent le service. Les gestionnaires pour les événements ci-joints sont spécifiés par syntaxe d’attribut. Comme avec les événements ci-joints, la syntaxe d’attribut est étendue pour les événements attachés pour permettre un *typeName*. *eventName* utilisation, où *typeName* `Add` est `Remove` la classe qui fournit et les accesseurs de gestionnaire d’événements pour l’infrastructure d’événement ci-joint, et *eventName* est le nom de l’événement.  
  
<a name="anatomy_of_a_xaml_page_root_element"></a>
## <a name="anatomy-of-a-xaml-root-element"></a>Anatomie d’un élément racine XAML  
 Le tableau suivant montre un élément de racine XAML typique décomposé, montrant les attributs spécifiques d’un élément racine:  
  
|||  
|-|-|  
|`<Page`|Élément d’objet d’ouverture de l’élément racine|  
|`xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`|La par[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]défaut ( ) XAML namespace|  
|`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`|L’espace de nom XAML en langue XAML|  
|`x:Class="ExampleNamespace.ExampleCode"`|La déclaration de classe partielle qui relie la majoration à tout code-derrière défini pour la classe partielle|  
|`>`|Fin de l’élément objet pour la racine. L’objet n’est pas encore fermé parce que l’élément contient des éléments pour enfants|  
  
<a name="optional_and_nonrecommended_xaml_usages"></a>
## <a name="optional-and-nonrecommended-xaml-usages"></a>Utilisations XAML facultatives et non modifiées  
 Les sections suivantes décrivent les utilisations XAML qui sont techniquement prises en charge par les processeurs XAML, mais qui produisent la verbosité ou d’autres problèmes esthétiques qui interfèrent avec les fichiers XAML restant lisibles par l’homme lorsque vous développez des applications qui contiennent des sources XAML.  
  
### <a name="optional-property-element-usages"></a>Utilisations facultatives d’élément de propriété  
 Les utilisations facultatives d’élément de propriété incluent l’écriture explicite des propriétés de contenu d’élément que le processeur XAML considère implicite. <xref:System.Windows.Controls.Menu>Par exemple, lorsque vous déclarez le contenu d’un , vous pouvez choisir de déclarer explicitement la <xref:System.Windows.Controls.ItemsControl.Items%2A> collection de l’étiquette <xref:System.Windows.Controls.Menu> d’élément <xref:System.Windows.Controls.Menu> <xref:System.Windows.Controls.MenuItem> <xref:System.Windows.Controls.ItemsControl.Items%2A> `<Menu.Items>` de propriété, et de placer chacun <xref:System.Windows.Controls.MenuItem> à l’intérieur, `<Menu.Items>`plutôt que d’utiliser le comportement implicite processeur XAML que tous les éléments de l’enfant d’un doit être un et sont placés dans la collection. Parfois, les utilisations facultatives peuvent aider à clarifier visuellement la structure de l’objet tel que représenté dans la balisage. Ou parfois une utilisation explicite d’élément de propriété peut éviter la marge qui est techniquement fonctionnelle mais visuellement déroutante, telle que les extensions de balisage imbriquées dans une valeur d’attribut.  
  
### <a name="full-typenamemembername-qualified-attributes"></a>Type completName.memberName Qualified Attributes  
 Le *typeName*. *formulaire de nom* de membre pour un attribut fonctionne réellement plus universellement que juste le cas d’événement acheminé. Mais dans d’autres situations, cette forme est superflue et vous devriez l’éviter, ne serait-ce que pour des raisons de style de balisage et de lisibilité. Dans l’exemple suivant, chacune <xref:System.Windows.Controls.Control.Background%2A> des trois références à l’attribut est tout à fait équivalente :  
  
 [!code-xaml[XAMLOvwSupport#TypeNameProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenameprop)]  
  
 `Button.Background`fonctionne parce que la recherche <xref:System.Windows.Controls.Button> qualifiée pour<xref:System.Windows.Controls.Control.Background%2A> cette propriété sur <xref:System.Windows.Controls.Button> est réussie (a été héritée de contrôle) et est la classe de l’élément objet ou une classe de base. `Control.Background`fonctionne parce <xref:System.Windows.Controls.Control> que la <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Control> classe <xref:System.Windows.Controls.Button> définit réellement et est une classe de base.  
  
 Cependant, le *type suivantName*. *l’exemple* de formulaire de nom de membre ne fonctionne pas et est ainsi montré commenté :  
  
 [!code-xaml[XAMLOvwSupport#TypeNameBadProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenamebadprop)]  
  
 <xref:System.Windows.Controls.Label>est une autre <xref:System.Windows.Controls.Control>classe dérivée `Label.Background` de <xref:System.Windows.Controls.Label> , et si vous aviez spécifié dans un élément objet, cette utilisation aurait fonctionné. Cependant, <xref:System.Windows.Controls.Label> parce que n’est <xref:System.Windows.Controls.Button>pas la classe ou la classe `Label.Background` de base de , le comportement spécifié processeur XAML est de traiter alors comme une propriété attachée. `Label.Background`n’est pas une propriété attachée disponible, et cette utilisation échoue.  
  
### <a name="basetypenamemembername-property-elements"></a>baseTypeName.memberName Property Elements  
 D’une manière analogue à la façon dont le *typeName*. *formulaire de nom* de membre fonctionne pour la syntaxe d’attribut, une *baseTypeName*. *syntaxe membreName* fonctionne pour la syntaxe d’élément de propriété. Par exemple, la syntaxe suivante fonctionne :  
  
 [!code-xaml[XAMLOvwSupport#GoofyPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofype)]  
  
 En l’espèce, l’élément propriété a été donné, même `Control.Background` si l’élément de propriété était contenu dans `Button`.  
  
 Mais tout comme *typeName*. *formulaire de nom de membre* pour les attributs, *baseTypeName*. *memberName* est mauvais style dans la balisage, et vous devriez l’éviter.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Fonctionnalités de langage pour les espaces de noms XAML (x:)](../../../desktop-wpf/xaml-services/namespace-language-features.md)
- [Extensions XAML WPF](wpf-xaml-extensions.md)
- [Aperçu des propriétés de dépendance](dependency-properties-overview.md)
- [TypeConverters et XAML](typeconverters-and-xaml.md)
- [XAML et les classes personnalisées pour WPF](xaml-and-custom-classes-for-wpf.md)
