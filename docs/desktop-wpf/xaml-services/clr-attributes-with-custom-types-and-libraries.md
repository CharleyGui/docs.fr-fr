---
title: Attributs CLR XAML pour les bibliothèques et types personnalisés
ms.date: 03/30/2017
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
ms.openlocfilehash: a4b8a58ea2c7d9de2b59ed78dc37e4ce1c434b79
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90535395"
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>Attributs CLR liés à XAML pour les bibliothèques et les types personnalisés

Cette rubrique décrit les attributs du common language runtime (CLR) définis par les services XAML .NET. Elle décrit également d’autres attributs CLR définis dans .NET qui ont un scénario XAML pour l’application vers des assemblys ou des types. L’attribution d’assemblys, de types ou de membres avec ces attributs CLR fournit des informations de système de type XAML relatives à vos types. Des informations sont fournies à tout consommateur XAML qui utilise les services XAML .NET pour traiter le flux de nœud XAML directement ou via les lecteurs et writers XAML dédiés.

## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>Attributs CLR liés à XAML pour les types personnalisés et les membres personnalisés

L’utilisation des attributs CLR implique que vous utilisez le CLR global pour définir vos types, sinon ces attributs ne sont pas disponibles. Si vous utilisez le CLR pour définir la sauvegarde de type, le contexte de schéma XAML par défaut utilisé par les writers XAML des services XAML .NET peut lire l’attribution CLR par le biais de la réflexion sur les assemblys de stockage.

Les sections suivantes décrivent les attributs XAML que vous pouvez appliquer aux types personnalisés ou aux membres personnalisés. Chaque attribut CLR communique des informations qui sont pertinentes pour un système de type XAML. Dans le chemin de chargement, les informations attribuées aident le lecteur XAML à former un flux de nœud XAML valide, ou il aide le writer XAML à produire un graphique d’objets valide. Dans le chemin d’enregistrement, les informations attribuées aident le lecteur XAML à former un flux de nœud XAML valide qui reconstitue les informations de système de type XAML ; ou il déclare des indications de sérialisation ou des spécifications pour le writer XAML ou d’autres consommateurs XAML.

### <a name="ambientattribute"></a>AmbientAttribute

**Documentation de référence :**<xref:System.Windows.Markup.AmbientAttribute>

**S’applique à :** Membres de classe, de propriété ou d' `get` accesseur qui prennent en charge les propriétés pouvant être attachées.

**Arguments :** None

<xref:System.Windows.Markup.AmbientAttribute> indique que la propriété, ou toutes les propriétés qui prennent le type avec attributs, doivent être interprétées sous le concept de propriété ambiante en XAML. Le concept de caractère ambiant renvoie à la façon dont les processeurs XAML déterminent les propriétaires de types des membres. Une propriété ambiante est une propriété où la valeur est supposée être disponible dans le contexte de l’analyseur lors de la création d’un graphique d’objet, mais où la recherche de membres de type standard est suspendue pour le jeu de nœuds XAML immédiat en cours de création.

Le concept ambiant peut être appliqué aux membres pouvant être attachés, qui ne sont pas représentés en tant que propriétés en ce qui concerne la façon dont l’attribution CLR est définie <xref:System.AttributeTargets> . L’utilisation de l’attribution de méthode doit être appliquée uniquement pour un `get` accesseur qui prend en charge l’utilisation pouvant être attachée pour XAML.

### <a name="constructorargumentattribute"></a>ConstructorArgumentAttribute

**Documentation de référence :**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>

**S’applique à :** Type

**Arguments :** Chaîne qui spécifie le nom de la propriété qui correspond à un argument de constructeur unique.

<xref:System.Windows.Markup.ConstructorArgumentAttribute> Spécifie qu’un objet peut être initialisé à l’aide d’une syntaxe de constructeur sans paramètre et qu’une propriété du nom spécifié fournit les informations de construction. Ces informations sont principalement destinées à la sérialisation XAML. Pour plus d'informations, consultez <xref:System.Windows.Markup.ConstructorArgumentAttribute>.

### <a name="contentpropertyattribute"></a>ContentPropertyAttribute

**Documentation de référence :**  <xref:System.Windows.Markup.ContentPropertyAttribute>

**S’applique à :** Type

**Arguments :** Chaîne qui spécifie le nom d’un membre du type avec attributs.

<xref:System.Windows.Markup.ContentPropertyAttribute> indique que la propriété telle que nommée par l’argument doit servir de propriété de contenu XAML pour ce type. La définition de propriété de contenu XAML hérite de tous les types dérivés qui peuvent être assignés au type de définition. Vous pouvez substituer la définition sur un type dérivé spécifique en appliquant <xref:System.Windows.Markup.ContentPropertyAttribute> sur le type dérivé spécifique.

Pour la propriété qui sert de propriété de contenu XAML, l’étiquetage des éléments de propriété de la propriété peut être omis dans l’utilisation de XAML. En règle générale, vous désignez les propriétés de contenu XAML qui favorisent une balise XAML rationalisée pour votre contenu et vos modèles de relation contenant-contenu. Étant donné qu’un seul membre peut être désigné comme la propriété de contenu XAML, vous avez parfois des choix de conception à faire concernant les propriétés de conteneur d’un type qui doivent être désignées comme propriété de contenu XAML. Les autres propriétés de conteneur doivent être utilisées avec des éléments de propriété explicites.

Dans le flux de nœud XAML, les propriétés de contenu XAML génèrent toujours des `StartMember` `EndMember` nœuds, en utilisant le nom de la propriété pour le <xref:System.Xaml.XamlMember> . Pour déterminer si un membre est la propriété de contenu XAML, examinez la <xref:System.Xaml.XamlType> valeur à partir de la `StartObject` position et obtenez la valeur de <xref:System.Xaml.XamlType.ContentProperty%2A> .

### <a name="contentwrapperattribute"></a>ContentWrapperAttribute

**Documentation de référence :**  <xref:System.Windows.Markup.ContentWrapperAttribute>

**S’applique à :** Classe, en particulier les types de collections.

**Arguments :** <xref:System.Type> Qui spécifie le type à utiliser comme type de wrapper de contenu pour le contenu étranger.

<xref:System.Windows.Markup.ContentWrapperAttribute> spécifie un ou plusieurs types sur le type de collection associé qui sera utilisé pour encapsuler le contenu étranger. Le contenu étranger fait référence aux cas où les contraintes de système de type sur le type de la propriété de contenu ne capturent pas tous les cas de contenu possibles que l’utilisation de XAML pour le type propriétaire prendrait en charge. Par exemple, la prise en charge XAML pour le contenu d’un type particulier peut prendre en charge les chaînes dans un générique fortement typé <xref:System.Collections.ObjectModel.Collection%601> . Les wrappers de contenu sont utiles pour la migration de conventions de balisage préexistantes en XAML pour la conception de valeurs assignables pour les collections, telles que la migration de modèles de contenu liés au texte.

Pour spécifier plusieurs types de wrappers de contenu, appliquez l’attribut plusieurs fois.

### <a name="dependsonattribute"></a>DependsOnAttribute

**Documentation de référence :**  <xref:System.Windows.Markup.DependsOnAttribute>

**S’applique à :** Propriété

**Arguments :** Chaîne qui spécifie le nom d’un autre membre du type avec attributs.

<xref:System.Windows.Markup.DependsOnAttribute> indique que la propriété avec attributs dépend de la valeur d’une autre propriété. L’application de cet attribut à une définition de propriété garantit que les propriétés dépendantes sont traitées en premier dans l’écriture d’objet XAML. Les utilisations de <xref:System.Windows.Markup.DependsOnAttribute> spécifient les cas exceptionnels des propriétés sur les types où un ordre spécifique d’analyse doit être suivi pour la création d’un objet valide.

Vous pouvez appliquer plusieurs <xref:System.Windows.Markup.DependsOnAttribute> cas à une définition de propriété.

### <a name="markupextensionreturntypeattribute"></a>MarkupExtensionReturnTypeAttribute

**Documentation de référence :**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>

**S’applique à :** Classe, qui est censée être un <xref:System.Windows.Markup.MarkupExtension> type dérivé.

**Arguments :** <xref:System.Type> Qui spécifie le type le plus précis attendu comme `ProvideValue` résultat de l’attribute <xref:System.Windows.Markup.MarkupExtension> .

Pour plus d’informations, consultez [vue d’ensemble des extensions de balisage pour XAML](markup-extensions-overview.md).

### <a name="namescopepropertyattribute"></a>NameScopePropertyAttribute

**Documentation de référence :**  <xref:System.Windows.Markup.NameScopePropertyAttribute>

**S’applique à :** Type

**Arguments :** Prend en charge deux formes d’attribution :

- Chaîne qui spécifie le nom d’une propriété sur le type avec attributs.

- Chaîne qui spécifie le nom d’une propriété, et <xref:System.Type> pour le type qui définit la propriété nommée. Ce formulaire est destiné à la spécification d’un membre pouvant être attaché en tant que propriété de portée de code XAML.

<xref:System.Windows.Markup.NameScopePropertyAttribute> spécifie une propriété qui fournit la valeur de la portée de code XAML pour la classe avec attributs. La propriété de portée de code XAML est supposée référencer un objet qui implémente <xref:System.Windows.Markup.INameScope> et contient la portée de code XAML réelle, son magasin et son comportement.

### <a name="runtimenamepropertyattribute"></a>RuntimeNamePropertyAttribute

**Documentation de référence :**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>

**S’applique à :** Type

**Arguments :** Chaîne qui spécifie le nom de la propriété de nom au moment de l’exécution sur le type avec attributs.

<xref:System.Windows.Markup.RuntimeNamePropertyAttribute> signale une propriété du type avec attributs qui est mappée à la [directive X :Name](xname-directive.md)XAML. La propriété doit être de type <xref:System.String> et doit être en lecture/écriture.

La définition hérite de tous les types dérivés qui peuvent être assignés au type de définition. Vous pouvez substituer la définition sur un type dérivé spécifique en appliquant <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> sur le type dérivé spécifique.

### <a name="trimsurroundingwhitespaceattribute"></a>TrimSurroundingWhitespaceAttribute

**Documentation de référence :**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>

**S’applique à :** Modes

**Arguments :** None.

<xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> est appliqué à des types spécifiques qui peuvent apparaître en tant qu’éléments enfants dans un contenu significatif d’espaces blancs (contenu détenu par une collection qui possède <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> ). <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> concerne principalement le chemin d’enregistrement, mais est disponible dans le système de type XAML dans le chemin de chargement en examinant <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType> . Pour plus d’informations, consultez traitement des espaces [blancs en XAML](white-space-processing.md).

### <a name="typeconverterattribute"></a>TypeConverterAttribute

**Documentation de référence :**  <xref:System.ComponentModel.TypeConverterAttribute>

**S’applique à :** La classe, la propriété, la méthode (le seul cas de méthode XAML valide est un `get` accesseur qui prend en charge un membre pouvant être attaché).

**Arguments :** <xref:System.Type> Du <xref:System.ComponentModel.TypeConverter> .

<xref:System.ComponentModel.TypeConverterAttribute> dans un contexte XAML, fait référence à un personnalisé <xref:System.ComponentModel.TypeConverter> . Cela <xref:System.ComponentModel.TypeConverter> fournit le comportement de conversion de type pour les types personnalisés, ou les membres de ce type.

Appliquez l' <xref:System.ComponentModel.TypeConverterAttribute> attribut à votre type, en référençant votre implémentation de convertisseur de type. Vous pouvez définir des convertisseurs de type pour XAML sur des classes, des structures ou des interfaces. Vous n’avez pas besoin de fournir la conversion de type pour les énumérations, cette conversion est activée en mode natif.

Votre convertisseur de type doit pouvoir effectuer une conversion à partir d’une chaîne utilisée pour les attributs ou le texte d’initialisation dans le balisage, dans le type de destination prévu. Pour plus d’informations, consultez [TypeConverters et XAML](/dotnet/desktop/wpf/advanced/typeconverters-and-xaml).

Plutôt que d’appliquer à toutes les valeurs d’un type, un comportement de convertisseur de type pour XAML peut également être établi sur une propriété spécifique. Dans ce cas, vous appliquez <xref:System.ComponentModel.TypeConverterAttribute> à la définition de propriété (la définition externe, pas les `get` définitions spécifiques et `set` ).

Un comportement de convertisseur de type pour l’utilisation XAML d’un membre pouvant être attaché personnalisé peut être assigné en appliquant <xref:System.ComponentModel.TypeConverterAttribute> à l' `get` accesseur de méthode qui prend en charge l’utilisation de XAML.

Semblable à <xref:System.ComponentModel.TypeConverter> , <xref:System.ComponentModel.TypeConverterAttribute> existait dans .net avant l’existence de XAML, et le modèle de convertisseur de type a servi à d’autres fins. Pour faire référence à et utiliser <xref:System.ComponentModel.TypeConverterAttribute> , vous devez le qualifier entièrement ou fournir une `using` instruction pour <xref:System.ComponentModel> . Incluez également l’assembly système dans votre projet.

### <a name="uidpropertyattribute"></a>UidPropertyAttribute

**Documentation de référence :**  <xref:System.Windows.Markup.UidPropertyAttribute>

**S’applique à :** Type

**Arguments :** Chaîne qui fait référence à la propriété appropriée par nom.

Indique la propriété CLR d’une classe qui est l’alias de la [directive x :uid](xuid-directive.md).

### <a name="usableduringinitializationattribute"></a>UsableDuringInitializationAttribute

**Documentation de référence :**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>

**S’applique à :** Type

**Arguments :** Valeur booléenne. S’il est utilisé pour le rôle prévu de l’attribut, la valeur doit être définie sur `true` .

Indique si le type est généré de haut en haut lors de la création d’un graphique d’objet XAML. Il s’agit d’un concept avancé, qui est probablement étroitement lié à la définition de votre modèle de programmation. Pour plus d'informations, consultez <xref:System.Windows.Markup.UsableDuringInitializationAttribute>.

### <a name="valueserializerattribute"></a>ValueSerializerAttribute

**Documentation de référence :**  <xref:System.Windows.Markup.ValueSerializerAttribute>

**S’applique à :** La classe, la propriété, la méthode (le seul cas de méthode XAML valide est un `get` accesseur qui prend en charge un membre pouvant être attaché).

**Arguments :** <xref:System.Type> Qui spécifie la classe de prise en charge du sérialiseur de valeurs à utiliser lors de la sérialisation de toutes les propriétés du type avec attributs, ou de la propriété avec attributs spécifique.

<xref:System.Windows.Markup.ValueSerializer> spécifie une classe de sérialisation de valeur qui requiert plus d’État et de contexte qu’un <xref:System.ComponentModel.TypeConverter> . <xref:System.Windows.Markup.ValueSerializer> peut être associé à un membre pouvant être attaché en appliquant l' <xref:System.Windows.Markup.ValueSerializerAttribute> attribut sur la `get` méthode d’accesseur statique pour le membre pouvant être attaché. La sérialisation de valeur est également applicable pour les énumérations, les interfaces et les structures, mais pas pour les délégués.

### <a name="whitespacesignificantcollectionattribute"></a>WhitespaceSignificantCollectionAttribute

**Documentation de référence :**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>

**S’applique à :** Classe, spécifiquement les types de collection supposés héberger du contenu mixte, où les espaces autour des éléments objets peuvent être significatifs pour la représentation de l’interface utilisateur.

**Arguments :** None.

<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> indique qu’un type de collection doit être traité comme un espace blanc significatif par un processeur XAML, ce qui a une incidence sur la construction des nœuds de valeur du flux de nœud XAML au sein de la collection. Pour plus d’informations, consultez traitement des espaces [blancs en XAML](white-space-processing.md).

### <a name="xamldeferloadattribute"></a>XamlDeferLoadAttribute

**Documentation de référence :**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>

**S’applique à :** Classe, propriété.

**Arguments :** Prend en charge deux types de formulaires d’attribution sous forme de chaînes ou de types sous la forme <xref:System.Type> . Consultez <xref:System.Windows.Markup.XamlDeferLoadAttribute>.

Indique qu'une classe ou une propriété utilise le chargement différé pour XAML (par exemple, dans un comportement de modèle), et signale la classe qui active le comportement de report et son type de destination/contenu.

### <a name="xamlsetmarkupextensionattribute"></a>XamlSetMarkupExtensionAttribute

**Documentation de référence :**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>

**S’applique à :** Type

**Arguments :** Nomme le rappel.

Indique qu’une classe peut utiliser une extension de balisage pour fournir une valeur à une ou plusieurs de ses propriétés, et référence un gestionnaire qu’un writer XAML doit appeler avant d’effectuer une opération de définition d’extension de balisage sur n’importe quelle propriété de la classe.

### <a name="xamlsettypeconverterattribute"></a>XamlSetTypeConverterAttribute

**Documentation de référence :**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>

**S’applique à :** Type

**Arguments :** Nomme le rappel.

Indique qu’une classe peut utiliser un convertisseur de type pour fournir une valeur pour une ou plusieurs de ses propriétés, et référence un gestionnaire qu’un writer XAML doit appeler avant d’effectuer une opération de définition de convertisseur de type sur n’importe quelle propriété de la classe.

### <a name="xmllangpropertyattribute"></a>XmlLangPropertyAttribute

**Documentation de référence :**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>

**S’applique à :** Type

**Arguments :** Chaîne qui spécifie le nom de la propriété avec lequel effectuer un alias `xml:lang` sur le type avec attributs.

<xref:System.Windows.Markup.XmlLangPropertyAttribute> signale une propriété du type avec attributs qui est mappée à la `lang` directive XML. La propriété n’est pas nécessairement de type <xref:System.String> , mais doit pouvoir être assignée à partir d’une chaîne (l’assignation peut être obtenue en associant un convertisseur de type au type de la propriété ou à la propriété spécifique). La propriété doit être en lecture/écriture.

Le scénario de mappage `xml:lang` permet à un modèle objet d’exécution d’accéder aux informations de langage spécifiées par XML sans traitement spécifique avec un XMLDOM.

La définition hérite de tous les types dérivés qui peuvent être assignés au type de définition. Vous pouvez substituer la définition sur un type dérivé spécifique en appliquant <xref:System.Windows.Markup.XmlLangPropertyAttribute> sur le type dérivé spécifique, bien qu’il s’agisse d’un scénario rare.

## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>Attributs CLR liés à XAML au niveau de l’assembly

Les sections suivantes décrivent les attributs XAML qui ne sont pas appliqués aux types ou aux définitions de membres, mais qui sont plutôt appliqués aux assemblys. Ces attributs sont pertinents pour l’objectif global de la définition d’une bibliothèque qui contient des types personnalisés à utiliser en XAML. Certains des attributs n’influencent pas nécessairement le flux de nœud XAML directement, mais sont transmis dans le flux de nœud à utiliser par les autres consommateurs. Les consommateurs des informations incluent des environnements de conception ou des processus de sérialisation qui nécessitent des informations d’espace de noms XAML et des informations de préfixe associées. Un contexte de schéma XAML (y compris la valeur par défaut des services XAML .NET) utilise également ces informations.

### <a name="xmlnscompatiblewithattribute"></a>XmlnsCompatibleWithAttribute

**Documentation de référence :**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>

**Arguments :**

- Chaîne qui spécifie l’identificateur de l’espace de noms XAML à englober.

- Chaîne qui spécifie l’identificateur de l’espace de noms XAML qui peut englober l’espace de noms XAML à partir de l’argument précédent.

  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute> Spécifie qu’un espace de noms XAML peut être inclus par un autre espace de noms XAML. En règle générale, l’espace de noms XAML inclus est indiqué dans un <xref:System.Windows.Markup.XmlnsDefinitionAttribute> précédemment défini. Cette technique peut être utilisée pour le contrôle de version d’un vocabulaire XAML dans une bibliothèque et pour le rendre compatible avec le balisage précédemment défini par rapport au vocabulaire avec version antérieure.

### <a name="xmlnsdefinitionattribute"></a>XmlnsDefinitionAttribute

**Documentation de référence :**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>

**Arguments :**

- Chaîne qui spécifie l’identificateur de l’espace de noms XAML à définir.

- Chaîne qui nomme un espace de noms CLR. L’espace de noms CLR doit définir des types publics dans votre assembly, et au moins l’un des types d’espaces de noms CLR doit être prévu pour l’utilisation de XAML.

  <xref:System.Windows.Markup.XmlnsDefinitionAttribute> spécifie un mappage par assembly entre un espace de noms XAML et un espace de noms CLR, qui est ensuite utilisé pour la résolution de type par un writer d’objet XAML ou un contexte de schéma XAML.

  Plusieurs <xref:System.Windows.Markup.XmlnsDefinitionAttribute> peuvent être appliqués à un assembly. Cette opération peut être effectuée pour n’importe quelle combinaison des raisons suivantes :

- La conception de la bibliothèque contient plusieurs espaces de noms CLR pour l’organisation logique de l’accès à l’API Runtime. Toutefois, vous souhaitez que tous les types de ces espaces de noms soient utilisables en XAML en référençant le même espace de noms XAML. Dans ce cas, vous appliquez plusieurs <xref:System.Windows.Markup.XmlnsDefinitionAttribute> attributs à l’aide de la même <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> valeur, mais des <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> valeurs différentes. Cela s’avère particulièrement utile si vous définissez des mappages pour l’espace de noms XAML que votre infrastructure ou application envisage d’être l’espace de noms XAML par défaut en utilisation courante.

- La conception de la bibliothèque contient plusieurs espaces de noms CLR et vous souhaitez une séparation délibérée des espaces de noms XAML entre les utilisations des types dans ces espaces de noms CLR.

- Vous définissez un espace de noms CLR dans l’assembly et vous souhaitez qu’il soit accessible par le biais de plusieurs espaces de noms XAML. Ce scénario se produit lorsque vous prenez en charge plusieurs vocabulaires avec le même code base.

- Vous définissez la prise en charge du langage XAML dans un ou plusieurs espaces de noms CLR. Dans ce cas, la <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> valeur doit être `http://schemas.microsoft.com/winfx/2006/xaml` .

### <a name="xmlnsprefixattribute"></a>XmlnsPrefixAttribute

**Documentation de référence :**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>

**Arguments :**

- Chaîne qui spécifie l’identificateur d’un espace de noms XAML.

- Chaîne qui spécifie un préfixe recommandé.

  <xref:System.Windows.Markup.XmlnsDefinitionAttribute> spécifie un préfixe recommandé à utiliser pour un espace de noms XAML. Le préfixe est utile lors de l’écriture d’éléments et d’attributs dans un fichier XAML qui est sérialisé par les services XAML .NET <xref:System.Xaml.XamlXmlWriter> , ou lorsqu’une bibliothèque d’implémentation XAML interagit avec un environnement de conception qui a des fonctionnalités d’édition XAML.

  Plusieurs <xref:System.Windows.Markup.XmlnsPrefixAttribute> peuvent être appliqués à un assembly. Cette opération peut être effectuée pour n’importe quelle combinaison des raisons suivantes :

- Votre assembly définit des types pour plusieurs espaces de noms XAML. Dans ce cas, définissez des valeurs de préfixe différentes pour chaque espace de noms XAML.

- Vous prenez en charge plusieurs vocabulaires, et vous utilisez différents préfixes pour chaque vocabulaire et espace de noms XAML.

- Vous définissez la prise en charge du langage XAML dans l’assembly et avez un <xref:System.Windows.Markup.XmlnsDefinitionAttribute> pour `http://schemas.microsoft.com/winfx/2006/xaml` . Dans ce cas, vous devez généralement promouvoir le préfixe `x` .

> [!NOTE]
> Les services XAML .NET définissent également l’attribut XAML <xref:System.Windows.Markup.RootNamespaceAttribute> . Cet attribut est un attribut de niveau assembly pour la prise en charge du système de projet, et il ne s’applique pas aux types personnalisés XAML.

## <a name="see-also"></a>Voir aussi

- <xref:System.Attribute>
- [Définition de types personnalisés pour les utiliser avec les services XAML .NET](define-custom-types.md)
