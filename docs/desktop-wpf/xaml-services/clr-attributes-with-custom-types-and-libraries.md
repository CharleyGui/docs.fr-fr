---
title: Attributs CLR XAML pour les bibliothèques et types personnalisés
ms.date: 03/30/2017
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
ms.openlocfilehash: 5481d02e4d393312fa0f0dd13b45c54acc567e13
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071765"
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>Attributs CLR liés à XAML pour les types et bibliothèques personnalisés

Ce sujet décrit les attributs courants de l’heure d’exécution de langue (CLR) qui sont définis par .NET XAML Services. Il décrit également d’autres attributs CLR qui sont définis en .NET qui ont un scénario XAML-connexe pour l’application aux assemblages ou aux types. Attribuer des assemblages, des types ou des membres avec ces attributs CLR fournit des informations système de type XAML liées à vos types. L’information est fournie à tout consommateur XAML qui utilise .NET XAML Services pour le traitement du flux de nœudS XAML directement ou par l’intermédiaire des lecteurs dédiés XAML et écrivains XAML.

## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>Attributs CLR liés à XAML pour les types personnalisés et les membres personnalisés

L’utilisation d’attributs CLR implique que vous utilisez le CLR global pour définir vos types, sinon ces attributs ne sont pas disponibles. Si vous utilisez le CLR pour définir le support de type, alors le contexte de schéma XAML par défaut utilisé par les auteurs de .NET XAML Services XAML peuvent lire l’attribution CLR par la réflexion contre les assemblages de soutien.

Les sections suivantes décrivent les attributs liés à XAML que vous pouvez appliquer aux types personnalisés ou aux membres personnalisés. Chaque attribut CLR communique des informations pertinentes à un système de type XAML. Dans le chemin de charge, les informations attribuées aident soit le lecteur XAML à former un flux de nœudS XAML valide, soit elle aide l’auteur de XAML à produire un graphique d’objet valide. Dans le chemin d’enregistrement, l’information attribuée aide soit le lecteur XAML à former un flux valide de nœuds XAML qui reconstitue des informations système de type XAML ; ou il déclare des conseils de sérialisation ou des exigences pour l’écrivain XAML ou d’autres consommateurs XAML.

### <a name="ambientattribute"></a>AmbientAttribute

**Documentation de référence:**<xref:System.Windows.Markup.AmbientAttribute>

**S’applique à :** Membres de classe, de propriété ou `get` d’accesseur qui prennent en charge les propriétés attachables.

**Arguments:** Aucun

<xref:System.Windows.Markup.AmbientAttribute>indique que la propriété, ou toutes les propriétés qui prennent le type attribué, doivent être interprétées en vertu du concept de propriété ambiante dans XAML. Le concept de caractère ambiant renvoie à la façon dont les processeurs XAML déterminent les propriétaires de types des membres. Une propriété ambiante est une propriété où la valeur est censée être disponible dans le contexte du parseur lors de la création d’un graphique d’objet, mais où le lookup type-membre typique est suspendu pour l’ensemble immédiat de nœuds XAML en cours de création.

Le concept ambiant peut être appliqué aux membres attachables, <xref:System.AttributeTargets>qui ne sont pas représentés comme propriétés en termes de définition de l’attribution CLR . L’utilisation de l’attribution `get` de la méthode ne doit être appliquée que pour un accesseur qui prend en charge l’utilisation attachable pour XAML.

### <a name="constructorargumentattribute"></a>ConstructorArgumentAttribute

**Documentation de référence:**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>

**S’applique à :** Classe

**Arguments:** Une chaîne qui spécifie le nom de la propriété qui correspond à un seul argument constructeur.

<xref:System.Windows.Markup.ConstructorArgumentAttribute>précise qu’un objet peut être para initialisé à l’aide d’une syntaxe constructeur non sans paramètres, et qu’une propriété du nom spécifié fournit des informations de construction. Ces informations sont principalement destinées à la sérialisation XAML. Pour plus d’informations, consultez <xref:System.Windows.Markup.ConstructorArgumentAttribute>.

### <a name="contentpropertyattribute"></a>ContentPropertyAttribute

**Documentation de référence:**  <xref:System.Windows.Markup.ContentPropertyAttribute>

**S’applique à :** Classe

**Arguments:** Une chaîne qui spécifie le nom d’un membre du type attribué.

<xref:System.Windows.Markup.ContentPropertyAttribute>indique que la propriété telle que nommée par l’argument devrait servir de propriété de contenu XAML pour ce type. La définition de propriété de contenu XAML hérite de tous les types dérivés qui sont attribués au type définissant. Vous pouvez passer outre à la définition <xref:System.Windows.Markup.ContentPropertyAttribute> sur un type dérivé spécifique en appliquant sur le type dérivé spécifique.

Pour la propriété qui sert de propriété de contenu XAML, le marquage d’élément de propriété pour la propriété peut être omis dans l’utilisation de XAML. En règle générale, vous désignez les propriétés de contenu XAML qui favorisent une balisage XAML simplifiée pour vos modèles de contenu et de confinement. Étant donné qu’un seul membre peut être désigné comme propriété de contenu XAML, vous avez parfois des choix de conception à faire concernant laquelle de plusieurs propriétés de conteneurs d’un type devrait être désignée comme la propriété de contenu XAML. Les autres propriétés de conteneur doivent être utilisées avec des éléments de propriété explicites.

Dans le flux de nœuds XAML, les propriétés de contenu XAML produisent `StartMember` encore et `EndMember` les nœuds, en utilisant le nom de la propriété pour le <xref:System.Xaml.XamlMember>. Pour déterminer si un membre est la propriété <xref:System.Xaml.XamlType> de `StartObject` contenu XAML, <xref:System.Xaml.XamlType.ContentProperty%2A>examinez la valeur du poste et obtenez la valeur de .

### <a name="contentwrapperattribute"></a>ContentWrapperAttribute

**Documentation de référence:**  <xref:System.Windows.Markup.ContentWrapperAttribute>

**S’applique à :** Classe, en particulier les types de collecte.

**Arguments:** A <xref:System.Type> qui spécifie le type à utiliser comme type d’emballage de contenu pour le contenu étranger.

<xref:System.Windows.Markup.ContentWrapperAttribute>spécifie un ou plusieurs types sur le type de collecte associé qui seront utilisés pour envelopper le contenu étranger. Le contenu étranger désigne les cas où les contraintes du système de type sur le type de propriété de contenu ne saisissent pas tous les cas de contenu possibles que l’utilisation de XAML pour le type de propriétaire serait prise en charge. Par exemple, le support XAML pour le contenu d’un <xref:System.Collections.ObjectModel.Collection%601>type particulier peut prendre en charge les chaînes dans un générique fortement tapé . Les emballages de contenu sont utiles pour migrer les conventions de balisage préexistantes dans la conception de XAML de valeurs assignables pour les collections, telles que la migration de modèles de contenu liés au texte.

Pour spécifier plus d’un type d’emballage de contenu, appliquez l’attribut plusieurs fois.

### <a name="dependsonattribute"></a>DependsOnAttribute (en)

**Documentation de référence:**  <xref:System.Windows.Markup.DependsOnAttribute>

**S’applique à :** Propriété

**Arguments:** Une chaîne qui spécifie le nom d’un autre membre du type attribué.

<xref:System.Windows.Markup.DependsOnAttribute>indique que la propriété attribuée dépend de la valeur d’une autre propriété. L’application de cet attribut à une définition de propriété garantit que les propriétés dépendantes sont traitées en premier dans l’écriture d’objets XAML. Utilisations <xref:System.Windows.Markup.DependsOnAttribute> de spécifier les cas exceptionnels de propriétés sur les types où un ordre spécifique d’analyse doit être suivi pour la création d’objets valides.

Vous pouvez <xref:System.Windows.Markup.DependsOnAttribute> appliquer plusieurs cas à une définition de propriété.

### <a name="markupextensionreturntypeattribute"></a>MarkupExtensionReturnTypeAttribute

**Documentation de référence:**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>

**S’applique à :** Classe, qui devrait être <xref:System.Windows.Markup.MarkupExtension> un type dérivé.

**Arguments:** A <xref:System.Type> qui spécifie le type `ProvideValue` le plus <xref:System.Windows.Markup.MarkupExtension>précis à attendre à la suite de l’attribué .

Pour plus d’informations, voir [Extensions Markup pour XAML Aperçu](markup-extensions-overview.md).

### <a name="namescopepropertyattribute"></a>NomScopePropertyAttribute

**Documentation de référence:**  <xref:System.Windows.Markup.NameScopePropertyAttribute>

**S’applique à :** Classe

**Arguments:** Soutient deux formes d’attribution :

- Une chaîne qui spécifie le nom d’une propriété sur le type attribué.

- Une chaîne qui spécifie le <xref:System.Type> nom d’une propriété, et un pour le type qui définit la propriété nommée. Ce formulaire est destiné à spécifier un membre attachable comme propriété de namescope XAML.

<xref:System.Windows.Markup.NameScopePropertyAttribute>spécifie une propriété qui fournit la valeur XAML namescope pour la classe attribuée. La propriété XAML namescope devrait faire référence <xref:System.Windows.Markup.INameScope> à un objet qui implémente et détient le namescope XAML réel, son magasin, et son comportement.

### <a name="runtimenamepropertyattribute"></a>RuntimeNamePropertyAttribute RuntimeNamePropertyAttribute RuntimeNamePropertyAttribute Runtime

**Documentation de référence:**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>

**S’applique à :** Classe

**Arguments:** Une chaîne qui spécifie le nom de la propriété de nom de l’heure d’exécution sur le type attribué.

<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>signale une propriété du type attribué qui cartographie la directive XAML [x:Name](xname-directive.md). La propriété doit <xref:System.String> être de type et doit être lue/écriture.

La définition hérite de tous les types dérivés qui sont assignables au type définissant. Vous pouvez passer outre à la définition <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> sur un type dérivé spécifique en appliquant sur le type dérivé spécifique.

### <a name="trimsurroundingwhitespaceattribute"></a>TrimSurroundingWhitespaceAttribute

**Documentation de référence:**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>

**S’applique à :** Types

**Arguments:** Aucun.

<xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>s’applique à des types spécifiques qui peuvent apparaître comme des éléments pour <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>enfants dans un contenu significatif dans l’espace blanc (contenu détenu par une collection qui a ). <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>est principalement pertinent pour le chemin d’enregistrement, mais est disponible dans <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>le système de type XAML dans la trajectoire de charge en examinant . Pour plus d’informations, voir [traitement de l’espace blanc dans XAML](white-space-processing.md).

### <a name="typeconverterattribute"></a>TypeConverterAttribute

**Documentation de référence:**  <xref:System.ComponentModel.TypeConverterAttribute>

**S’applique à :** Catégorie, bien, méthode (le seul cas de `get` méthode valide XAML est un accesseur qui prend en charge un membre attachable).

**Arguments:** Le <xref:System.Type> de <xref:System.ComponentModel.TypeConverter>la .

<xref:System.ComponentModel.TypeConverterAttribute>dans un contexte XAML <xref:System.ComponentModel.TypeConverter>fait référence à une coutume . Cela <xref:System.ComponentModel.TypeConverter> fournit un comportement de conversion de type pour les types personnalisés, ou les membres de ce type.

Appliquez <xref:System.ComponentModel.TypeConverterAttribute> l’attribut à votre type, en référence à votre mise en œuvre de convertisseur de type. Vous pouvez définir des convertisseurs de type pour XAML sur les classes, les structures ou les interfaces. Vous n’avez pas besoin de fournir la conversion de type pour les énumérations, que la conversion est activée nativement.

Votre convertisseur de type devrait être en mesure de convertir à partir d’une chaîne qui est utilisée pour les attributs ou le texte d’initialisation en balisage, dans votre type de destination prévu. Pour plus d’informations, voir [TypeConverters et XAML](../../framework/wpf/advanced/typeconverters-and-xaml.md).

Plutôt que de s’appliquer à toutes les valeurs d’un type, un comportement de convertisseur de type pour XAML peut également être établi sur une propriété spécifique. Dans ce cas, <xref:System.ComponentModel.TypeConverterAttribute> vous appliquez à la définition `get` de `set` propriété (la définition extérieure, et non les définitions et définitions).

Un comportement de convertisseur de type pour l’utilisation XAML d’un membre joignable personnalisé peut être attribué en appliquant <xref:System.ComponentModel.TypeConverterAttribute> à l’accesseur `get` de méthode qui prend en charge l’utilisation de XAML.

Semblable <xref:System.ComponentModel.TypeConverter>à <xref:System.ComponentModel.TypeConverterAttribute> , existait en .NET avant l’existence de XAML, et le modèle de convertisseur de type servi à d’autres fins. Afin de référencer <xref:System.ComponentModel.TypeConverterAttribute>et d’utiliser, vous `using` devez <xref:System.ComponentModel>le qualifier pleinement ou fournir une déclaration pour . Inclure également l’assemblage du système dans votre projet.

### <a name="uidpropertyattribute"></a>UidPropertyAttribute UidPropertyAttribute

**Documentation de référence:**  <xref:System.Windows.Markup.UidPropertyAttribute>

**S’applique à :** Classe

**Arguments:** Une chaîne qui fait référence à la propriété concernée par son nom.

Indique la propriété CLR d’une classe qui alias la [directive x:Uid](xuid-directive.md).

### <a name="usableduringinitializationattribute"></a>UsableDuringInitialisationAttribute

**Documentation de référence:**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>

**S’applique à :** Classe

**Arguments:** Un Boolean. S’il est utilisé à l’objectif visé `true`par l’attribut, la valeur doit être définie à .

Indique si le type est construit de haut en bas pendant la création de graphique d’objet XAML. Il s’agit d’un concept avancé, qui est probablement étroitement lié à la définition de votre modèle de programmation. Pour plus d’informations, consultez <xref:System.Windows.Markup.UsableDuringInitializationAttribute>.

### <a name="valueserializerattribute"></a>ValueSerializerAttribute

**Documentation de référence:**  <xref:System.Windows.Markup.ValueSerializerAttribute>

**S’applique à :** Catégorie, bien, méthode (le seul cas de `get` méthode valide XAML est un accesseur qui prend en charge un membre attachable).

**Arguments:** A <xref:System.Type> qui spécifie la classe de support de sérialisation de valeur à utiliser lors de la sérialisation de toutes les propriétés du type attribué, ou de la propriété spécifique attribuée.

<xref:System.Windows.Markup.ValueSerializer>spécifie une classe de sérialisation <xref:System.ComponentModel.TypeConverter> de valeur qui exige plus d’état et de contexte qu’un. <xref:System.Windows.Markup.ValueSerializer>peut être associé à un membre <xref:System.Windows.Markup.ValueSerializerAttribute> attachable `get` en appliquant l’attribut sur la méthode d’accesseur statique pour le membre attachable. La sérialisation des valeurs s’applique également aux énumérations, interfaces et structures, mais pas aux délégués.

### <a name="whitespacesignificantcollectionattribute"></a>WhitespaceSignificantCollectionAttribute

**Documentation de référence:**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>

**S’applique à :** Classe, en particulier les types de collecte qui sont censés héberger du contenu mixte, où l’espace blanc autour des éléments de l’objet pourrait être important pour la représentation de l’interface utilisateur.

**Arguments:** Aucun.

<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>indique qu’un type de collecte doit être traité comme espace blanc significatif par un processeur XAML, ce qui influence la construction des nœuds de valeur du flux de nœuds XAML au sein de la collection. Pour plus d’informations, voir [traitement de l’espace blanc dans XAML](white-space-processing.md).

### <a name="xamldeferloadattribute"></a>XamlDeferLoadAttribute

**Documentation de référence:**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>

**S’applique à :** Classe, propri été.

**Arguments:** Prend en charge deux types de <xref:System.Type>formulaires d’attribution comme des chaînes, ou des types comme . Consultez <xref:System.Windows.Markup.XamlDeferLoadAttribute>.

Indique qu'une classe ou une propriété utilise le chargement différé pour XAML (par exemple, dans un comportement de modèle), et signale la classe qui active le comportement de report et son type de destination/contenu.

### <a name="xamlsetmarkupextensionattribute"></a>XamlSetMarkupExtensionAttribute

**Documentation de référence:**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>

**S’applique à :** Classe

**Arguments:** Nomme le rappel.

Indique qu’une classe peut utiliser une extension de balisage pour fournir une valeur pour une ou plusieurs de ses propriétés, et fait référence à un gestionnaire qu’un auteur XAML devrait appeler avant d’effectuer une opération de prolongation de balisage sur n’importe quelle propriété de la classe.

### <a name="xamlsettypeconverterattribute"></a>XamlSetTypeConverterAttribute

**Documentation de référence:**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>

**S’applique à :** Classe

**Arguments:** Nomme le rappel.

Indique qu’une classe peut utiliser un convertisseur de type pour fournir une valeur pour une ou plusieurs de ses propriétés, et fait référence à un gestionnaire qu’un auteur XAML devrait appeler avant d’effectuer une opération de convertisseur de type sur n’importe quelle propriété de la classe.

### <a name="xmllangpropertyattribute"></a>XmlLangPropertyAttribute XmlLangPropertyAttribute

**Documentation de référence:**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>

**S’applique à :** Classe

**Arguments:** Une chaîne qui spécifie le `xml:lang` nom de la propriété à alias sur le type attribué.

<xref:System.Windows.Markup.XmlLangPropertyAttribute>signale une propriété du type attribué `lang` qui trace à la directive XML. La propriété n’est <xref:System.String> pas nécessairement de type, mais doit être assignable à partir d’une chaîne (l’affectation peut être accomplie en associant un convertisseur de type avec le type de propriété ou avec la propriété spécifique). La propriété doit être lue/écrite.

Le scénario `xml:lang` de cartographie est de sorte qu’un modèle d’objet de durée de course a accès à des informations linguistiques spécifiées par XML sans traitement spécifique avec un XMLDOM.

La définition hérite de tous les types dérivés qui sont assignables au type définissant. Vous pouvez passer outre à la définition <xref:System.Windows.Markup.XmlLangPropertyAttribute> sur un type dérivé spécifique en appliquant sur le type dérivé spécifique, bien qu’il s’agit d’un scénario rare.

## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>Attributs CLR liés à XAML au niveau de l’Assemblée

Les sections suivantes décrivent les attributs liés à la XAML qui ne sont pas appliqués aux types ou aux définitions des membres, mais qui sont plutôt appliqués aux assemblages. Ces attributs sont pertinents à l’objectif global de définir une bibliothèque qui contient des types personnalisés à utiliser dans XAML. Certains des attributs n’influencent pas nécessairement directement le flux de nœuds XAML, mais sont transmis dans le flux de nœuds pour d’autres consommateurs à utiliser. Les consommateurs pour l’information comprennent des environnements de conception ou des processus de sérialisation qui ont besoin d’informations XAML namespace et les informations préfixes associées. Un contexte de schéma XAML (y compris le défaut .NET XAML Services) utilise également ces informations.

### <a name="xmlnscompatiblewithattribute"></a>XmlnsCompatibleWithAttribute

**Documentation de référence:**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>

**Arguments :**

- Une chaîne qui spécifie l’identifiant de l’espace de nom XAML pour subsume.

- Une chaîne qui spécifie l’identifiant de l’espace de nom XAML qui peut subsumer l’espace de nom XAML de l’argument précédent.

  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>spécifie qu’un espace de nom XAML peut être subsumé par un autre espace de nom XAML. En règle générale, l’espace de noms XAML inclus est indiqué dans un <xref:System.Windows.Markup.XmlnsDefinitionAttribute> précédemment défini. Cette technique peut être utilisée pour la version d’un vocabulaire XAML dans une bibliothèque et pour la rendre compatible avec le balisage précédemment défini par rapport au vocabulaire version antérieure.

### <a name="xmlnsdefinitionattribute"></a>XmlnsDefinitionAttribute

**Documentation de référence:**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>

**Arguments :**

- Une chaîne qui spécifie l’identifiant de l’espace de nom XAML à définir.

- Une chaîne qui nomme un espace de nom CLR. L’espace de nom CLR devrait définir les types publics dans votre assemblage, et au moins un des types d’espace nom CLR devrait être destiné à l’utilisation de XAML.

  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>spécifie une cartographie par assemblage entre un espace de nom XAML et un espace de nom CLR, qui est ensuite utilisé pour la résolution de type par un auteur d’objets XAML ou le contexte du schéma XAML.

  Plus d’un <xref:System.Windows.Markup.XmlnsDefinitionAttribute> peut être appliqué à une assemblée. Cela peut être fait pour n’importe quelle combinaison des raisons suivantes:

- La conception de la bibliothèque contient plusieurs espaces de noms CLR pour l’organisation logique de l’accès à l’API en temps d’exécution; cependant, vous voulez que tous les types dans ces espaces de nom soient XAML-utilisables en faisant référence au même espace de nom XAML. Dans ce cas, <xref:System.Windows.Markup.XmlnsDefinitionAttribute> vous appliquez <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> plusieurs attributs en utilisant la même valeur mais des valeurs différentes. <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> Ceci est particulièrement utile si vous définissez des cartes pour l’espace de nom XAML que votre cadre ou application a l’intention d’être l’espace de nom XAML par défaut dans l’utilisation commune.

- La conception de la bibliothèque contient plusieurs espaces de noms CLR, et vous voulez une séparation délibérée XAML namespace entre les utilisations de types dans ces espaces de noms CLR.

- Vous définissez un espace de nom CLR dans l’assemblage, et vous voulez qu’il soit accessible à travers plus d’un espace de nom XAML. Ce scénario se produit lorsque vous soutenez plusieurs vocabulaires avec la même base de code.

- Vous définissez le support linguistique XAML dans un ou plusieurs espaces de noms CLR. Dans ce cas, <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> la `http://schemas.microsoft.com/winfx/2006/xaml`valeur devrait être .

### <a name="xmlnsprefixattribute"></a>XmlnsPrefixAttribute

**Documentation de référence:**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>

**Arguments :**

- Une chaîne qui spécifie l’identifiant d’un espace de nom XAML.

- Une chaîne qui spécifie un préfixe recommandé.

  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>spécifie un préfixe recommandé à utiliser pour un espace de nom XAML. Le préfixe est utile lors de l’écriture d’éléments et d’attributs <xref:System.Xaml.XamlXmlWriter>dans un fichier XAML qui est sérialisé par .NET XAML Services , ou quand une bibliothèque XAML-mise en œuvre interagit avec un environnement de conception qui a XAML caractéristiques d’édition.

  Plus d’un <xref:System.Windows.Markup.XmlnsPrefixAttribute> peut être appliqué à une assemblée. Cela peut être fait pour n’importe quelle combinaison des raisons suivantes:

- Votre assemblage définit les types pour plus d’un espace de nom XAML. Dans ce cas, définissez différentes valeurs de préfixe pour chaque espace de nom XAML.

- Vous soutenez plusieurs vocabulaires, et vous utilisez différents préfixes pour chaque vocabulaire et l’espace de nom XAML.

- Vous définissez le support linguistique XAML dans l’assemblage et avez un <xref:System.Windows.Markup.XmlnsDefinitionAttribute> pour `http://schemas.microsoft.com/winfx/2006/xaml`. Dans ce cas, vous devez `x`généralement promouvoir le préfixe .

> [!NOTE]
> .NET XAML Services définit également l’attribut <xref:System.Windows.Markup.RootNamespaceAttribute>XAML- connexe . Cet attribut est un attribut de niveau d’assemblage pour le support du système de projet, et il n’est pas pertinent pour les types personnalisés XAML.

## <a name="see-also"></a>Voir aussi

- <xref:System.Attribute>
- [Définition de types personnalisés pour les utiliser avec les services XAML .NET](define-custom-types.md)
