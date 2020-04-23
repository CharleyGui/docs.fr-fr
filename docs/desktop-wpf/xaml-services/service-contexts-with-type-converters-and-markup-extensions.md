---
title: Contextes de services disponibles aux convertisseurs de types ou aux extensions de balisage
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services how-to
ms.assetid: b4dad00f-03da-4579-a4e9-d8d72d2ccbce
ms.openlocfilehash: 59c4385eb4df8c622be6164cdb0a1a911c445ca8
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071660"
---
# <a name="service-contexts-available-to-type-converters-and-markup-extensions"></a>Contextes de services disponibles aux convertisseurs de types ou aux extensions de balisage
Les auteurs des types qui prennent en charge les utilisations de convertisseurs de type et d'extensions de balisage doivent souvent disposer d'informations contextuelles concernant l'emplacement où une utilisation existe dans le balisage ou dans la structure de graphique d'objets environnante. Les informations peuvent être exigées afin que l'objet fourni soit correctement instancié ou que les références d'objets à des objets existants dans le graphique d'objets puissent être créées. Lors de l’utilisation de services .NET XAML, le contexte qui pourrait être nécessaire est exposé comme une série d’interfaces de service. Le code de prise en charge de convertisseur de type ou d'extension de balisage peut lancer une requête pour un service, à l'aide d'un contexte de fournisseur de services disponible et passé à partir de <xref:System.Xaml.XamlObjectWriter> ou des types associés. Le contexte de schéma XAML est directement disponible via un service de ce type. Cette rubrique décrit comment accéder aux contextes de service à partir d'une implémentation de convertisseur de valeurs et répertorie les services qui sont généralement disponibles et leurs rôles.

## <a name="obtaining-services"></a>Obtention de services

Lorsque vous implémentez un convertisseur de valeurs, vous devez souvent accéder à un certain type de contexte dans lequel le convertisseur de valeurs est appliqué. Ce contexte peut inclure des informations telles que le contexte actif du schéma XAML, l’accès au système de cartographie de type que le contexte du schéma XAML et l’auteur d’objets XAML fournissent, et ainsi de suite. Les services disponibles pour une implémentation d'extension de balisage ou de convertisseur de type sont communiqués via les paramètres de contexte qui font partie de la signature de chacune des méthodes virtuelles. Dans tous les cas, <xref:System.IServiceProvider> est implémenté dans le contexte et vous pouvez appeler <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType> pour demander un service.

## <a name="services-for-a-markup-extension"></a>Services pour une extension de balisage

<xref:System.Windows.Markup.MarkupExtension> dispose d'une seule méthode virtuelle, <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>. Le paramètre d'entrée `serviceProvider` décrit comment les services sont communiqués aux implémentations lorsque l'extension de balisage est appelée par un processeur XAML. Le pseudo-code suivant illustre comment une implémentation d'extension de balisage peut lancer une requête pour les services dans sa méthode <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>:

```csharp
public override object ProvideValue(IServiceProvider serviceProvider)
{
...
    // Get the IXamlTypeResolver from the service provider
    if (serviceProvider == null)
    {
        throw new ArgumentNullException("serviceProvider");
    }
    IXamlTypeResolver xamlTypeResolver = serviceProvider.GetService(typeof(IXamlTypeResolver)) as IXamlTypeResolver;
    if (xamlTypeResolver == null)
   {
        throw new ArgumentException("IXamlTypeResolver"));
    }
...
}
```

## <a name="services-for-a-type-converter"></a>Services pour un convertisseur de type

<xref:System.ComponentModel.TypeConverter> dispose de quatre méthodes virtuelles qui utilisent un contexte de service et qui prennent en charge des utilisations de code XAML. Chacune de ces méthodes passe un paramètre d'entrée `context` . Ce paramètre est de type <xref:System.ComponentModel.ITypeDescriptorContext>, mais cette interface hérite de l'élément <xref:System.IServiceProvider>; par conséquent, il existe une méthode <xref:System.IServiceProvider.GetService%2A> disponible pour les implémentations de convertisseur de type.

Le pseudo-code suivant illustre comment une implémentation de convertisseur de type pour les utilisations de code XAML peut lancer une requête pour les services dans l'une de ses substitutions, dans le cas présent, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>:

```csharp
public override object ConvertFrom(ITypeDescriptorContext typeDescriptorContext,
  CultureInfo cultureInfo,
  object source)
{
    IRootObjectProvider rootProvider = typeDescriptorContext.GetService(typeof(IRootObjectProvider)) as IRootObjectProvider;
    if (rootProvider != null && source is String)
    {
        //return something, else ...
    }
    throw GetConvertFromException(source);
}
```

## <a name="services-for-a-value-serializer"></a>Services pour un sérialiseur de valeur

Pour le contexte du sérialiseur de valeur, vous utilisez un type de fournisseur de services spécifique à la classe <xref:System.Windows.Markup.ValueSerializer> , <xref:System.Windows.Markup.IValueSerializerContext>. Ce contexte est passé aux substitutions des quatre méthodes virtuelles <xref:System.Windows.Markup.ValueSerializer> . Appelez <xref:System.IServiceProvider.GetService%2A> à partir du contexte pour obtenir des services.

## <a name="using-the-xaml-service-provider-contexts"></a>Utilisation de contextes de fournisseurs de services XAML

Le fournisseur <xref:System.IServiceProvider.GetService%2A> de services pour l’accès aux services XAML disponibles pour les extensions de balisage ou les convertisseurs de type est mis en œuvre en tant que classe interne, avec une exposition uniquement par l’interface et comment il est passé dans le contexte pertinent. Chaque fois qu’une opération de traitement XAML dans la définition par défaut .NET XAML Services de la trajectoire de charge ou de la voie d’enregistrement invoque l’extension de balisage pertinente ou les méthodes de conversion de type qui nécessitent un contexte de service, cet objet interne est passé. Selon le cas, le contexte de service du système fournit `MarkupExtensionContext` ou `TextSyntaxContext`, mais les informations de ces deux classes sont internes. Votre interaction avec ces classes est limitée à la demande de services à partir de celles-ci, via <xref:System.IServiceProvider.GetService%2A>.

## <a name="available-services-from-the-net-xaml-service-context"></a>Services disponibles à partir du contexte de service .NET XAML

.NET XAML Services définit les services pour les extensions de balisage, les convertisseurs de type, les sérialisateurs de valeur et potentiellement d’autres utilisations. Les sections suivantes décrivent chacun de ces services et fournissent de l'aide sur la manière dont le service peut être utilisé dans une implémentation.

### <a name="iserviceprovider"></a>IServiceProvider

**Documentation de référence**:<xref:System.IServiceProvider>

**Pertinent pour :** Fonctionnement de base d’une infrastructure basée sur <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType>le service en .NET afin que vous puissiez appeler .

### <a name="itypedescriptorcontext"></a>ITypeDescriptorContext

**Documentation de référence**:<xref:System.ComponentModel.ITypeDescriptorContext>

Dérive de <xref:System.IServiceProvider>. Cette classe représente le contexte dans les signatures <xref:System.ComponentModel.TypeConverter> ; <xref:System.ComponentModel.TypeConverter> est une classe qui existe depuis .NET Framework 1.0. Elle est antérieure à XAML et au scénario <xref:System.ComponentModel.TypeConverter> XAML pour la conversion de type de valeur de chaîne. Dans le contexte .NET XAML Services, les méthodes sont <xref:System.ComponentModel.TypeConverter> mises en œuvre explicitement. Le comportement de l'implémentation explicite indique aux appelants que l'API de <xref:System.ComponentModel.ITypeDescriptorContext> n'est pas appropriée pour les systèmes de type XAML, ni pour la lecture ou l'écriture d'objets à partir de XAML. <xref:System.ComponentModel.ITypeDescriptorContext.Container%2A>, <xref:System.ComponentModel.ITypeDescriptorContext.Instance%2A>et <xref:System.ComponentModel.ITypeDescriptorContext.PropertyDescriptor%2A> reviennent `null` généralement à partir de .NET XAML Services contextes.

### <a name="ivalueserializercontext"></a>IValueSerializerContext

**Documentation de référence**:<xref:System.Windows.Markup.IValueSerializerContext>

Dérive de <xref:System.ComponentModel.ITypeDescriptorContext> et repose également sur des implémentations explicites pour supprimer de fausses conséquences concernant le système de type XAML. Prend en charge les méthodes d'assistance de recherche statiques sur <xref:System.Windows.Markup.ValueSerializer>.

### <a name="ixamltyperesolver"></a>IXamlTypeResolver

**Documentation de référence**:<xref:System.Windows.Markup.IXamlTypeResolver>

**Défini par:** <xref:System.Windows.Markup> namespace, System.Xaml assemblage  

**S'applique aux éléments suivants :** scénarios de chemin de chargement et interaction avec le contexte de schéma XAML.

**API de service :**  <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>

Influence potentiellement le mappage de type de XAML à CLR, nécessaire lorsque le writer XAML crée un objet CLR dans un graphique d'objets. <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A> traite une chaîne potentiellement qualifiée par préfixe qui correspond à un nom de type XAML (<xref:System.Xaml.XamlType.Name%2A?displayProperty=nameWithType>), et retourne un CLR <xref:System.Type>. La résolution de types dépend en général fortement du contexte de schéma XAML. Seul le contexte de schéma XAML tient compte de considérations telles que les suivantes : quels assemblys sont chargés et lesquels d'entre eux peuvent ou doivent être accessibles pour la résolution de type.

### <a name="iuricontext"></a>IUriContext

**Documentation de référence**:<xref:System.Windows.Markup.IUriContext>

**Défini par:** <xref:System.Windows.Markup> namespace, System.Xaml assemblage  

**S'applique aux éléments suivants :** gestion du chemin de chargement et du chemin d'enregistrement des valeurs membres qui sont des URI ou des valeurs `x:Uri` .

**API de service :**  <xref:System.Windows.Markup.IUriContext.BaseUri%2A>

Ce service signale une racine d'URI globalement disponible, le cas échéant. La racine d'URI peut être utilisée pour résoudre des URI relatifs en URI absolus, ou inversement. Ce scénario s'applique principalement aux services d'application exposés par une infrastructure particulière, ou des fonctions d'une classe d'élément racine communément utilisée dans une infrastructure. L'URI de base peut être établi comme un paramètre de lecteur XAML, qui est ensuite passé au writer d'objet XAML et signalé par ce service.

### <a name="iambientprovider"></a>IAmbientProvider

**Documentation de référence**:<xref:System.Xaml.IAmbientProvider>

**Défini par:** <xref:System.Xaml> namespace, System.Xaml assemblage  

**S'applique aux éléments suivants :** gestion de chemin de chargement et différés ou optimisations de recherche de type.

**Service APIs:**  <xref:System.Xaml.IAmbientProvider.GetAllAmbientValues%2A>, trois autres.

Le concept d'ambiance dans XAML est une technique permettant de marquer un membre particulier d'un type comme ambiant. Un type peut également être ambiant afin que toutes les valeurs de propriétés qui contiennent une instance du type soient considérées comme des propriétés ambiantes. Les extensions de balisage ou les convertisseurs de type qui se trouvent plus loin dans le flux de nœud XAML et qui sont des descendants dans le graphique d'objets peuvent accéder à la propriété ambiante ou à l'instance de type lors du chargement, ou utiliser les connaissances de la structure ambiante lors de l'enregistrement. Cela peut affecter le degré de qualification requis pour résoudre des types pour d'autres services, comme pour <xref:System.Windows.Markup.IXamlTypeResolver> ou pour `x:Type`. Voir aussi <xref:System.Xaml.AmbientPropertyValue>.

### <a name="ixamlschemacontextprovider"></a>IXamlSchemaContextProvider

**Documentation de référence**:<xref:System.Xaml.IXamlSchemaContextProvider>

**Défini par:** <xref:System.Xaml> namespace, System.Xaml assemblage  

**S'applique aux éléments suivants :** chemin de chargement et toute opération qui doit résoudre un type XAML en type de stockage.

**API de service :**  <xref:System.Xaml.IXamlSchemaContextProvider.SchemaContext%2A>

Le contexte de schéma XAML est nécessaire pour toutes les opérations de chargement différé, car le même contexte de schéma doit agir sur la zone différée pour intégrer le contenu différé. Pour plus d’informations sur le rôle du contexte de schéma XAML, consultez [XAML Services](../../../api/index.md).

### <a name="irootobjectprovider"></a>IRootObjectProvider

**Documentation de référence**:<xref:System.Xaml.IRootObjectProvider>

**Défini par:** <xref:System.Xaml> namespace, System.Xaml assemblage  

**S'applique à l'élément suivant :** chemin de chargement.

**API de service :**  <xref:System.Xaml.IRootObjectProvider.RootObject%2A>

Ce service s'applique aux services d'application exposés par une infrastructure particulière, ou des fonctions d'une classe d'élément racine communément utilisée dans une infrastructure. Un scénario pour l'obtention de l'objet racine connecte le code-behind et la connexion d'événements. Par exemple, l'implémentation WPF de `x:Class` est utilisée pour la compilation de balisage et la connexion de tout attribut de gestionnaire d'événements se trouvant à n'importe quelle autre position dans le balisage XAML. Le point de connexion des classes partielles définies par le balisage et le code-behind pour la compilation du balisage se trouve au niveau de l'élément racine.

### <a name="ixamlnamespaceresolver"></a>IXamlNamespaceResolver

**Documentation de référence**:<xref:System.Xaml.IXamlNamespaceResolver>

**Défini par:** <xref:System.Xaml> namespace, System.Xaml assemblage  

**S'applique aux éléments suivants :** chemin de chargement, chemin d'enregistrement.

**API de service :** <xref:System.Xaml.IXamlNamespaceResolver.GetNamespace%2A> pour le chemin de chargement, <xref:System.Xaml.IXamlNamespaceResolver.GetNamespacePrefixes%2A> pour le chemin d’enregistrement.

<xref:System.Xaml.IXamlNamespaceResolver> est un service qui peut retourner un identificateur d'espace de noms XAML/URI en fonction de son préfixe, tel qu'il est mappé dans le balisage XAML d'origine.

### <a name="iprovidevaluetarget"></a>IProvideValueTarget

**Documentation de référence**:<xref:System.Windows.Markup.IProvideValueTarget>

**Défini par:** <xref:System.Windows.Markup> namespace, System.Xaml assemblage  

**S'applique aux éléments suivants :** chemin de chargement et chemin d'enregistrement.

**Service APIs:**<xref:System.Windows.Markup.IProvideValueTarget.TargetObject%2A>, <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A>.  

<xref:System.Windows.Markup.IProvideValueTarget> permet à un convertisseur de type ou à une extension de balisage d'obtenir le contexte concernant l'emplacement d'action lors du chargement. Les implémentations peuvent utiliser ce contexte pour invalider une utilisation. Par exemple, certaines des extensions de balisage de WPF telles que <xref:System.Windows.DynamicResourceExtension>utilisent une logique. Celle-ci vérifie la propriété <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A> pour s'assurer que l'extension est utilisée uniquement pour définir des propriétés de dépendance (ou une courte liste propriétés autres que celles de dépendance).

### <a name="ixamlnameresolver"></a>IXamlNameResolver

**Documentation de référence**:<xref:System.Xaml.IXamlNameResolver>

**Défini par:** <xref:System.Xaml> namespace, System.Xaml assemblage  

**Pertinent pour :** Définition du graphique d’objets de `x:Name` `x:Reference`direction de chargement, résolution d’objets identifiés par , , ou techniques spécifiques au cadre.

**API de Service :**  <xref:System.Xaml.IXamlNameResolver.Resolve%2A>; autres API pour les scénarios plus avancés tels que l'utilisation de références anticipées.

.NET XAML Services `x:Reference` mise en œuvre de la manipulation repose sur ce service. Les infrastructures ou les outils spécifiques qui prennent en charge l'infrastructure utilisent ce service pour la gestion de `x:Name` ou la gestion de propriétés équivalentes (<xref:System.Windows.Markup.RuntimeNamePropertyAttribute> attribué).

### <a name="idestinationtypeprovider"></a>IDestinationTypeProvider

**Documentation de référence**:<xref:System.Xaml.IDestinationTypeProvider>

**Défini par:** <xref:System.Xaml> namespace, System.Xaml assemblage  

**S'applique aux éléments suivants :** résolution de chemin de chargement d'informations indirectes de type CLR.

**API de service :** <xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>

Pour plus d’informations, consultez <xref:System.Xaml.IDestinationTypeProvider>.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [Vue d'ensemble des extensions de balisage pour XAML](markup-extensions-overview.md)
- [Vue d'ensemble des convertisseurs de types pour XAML](type-converters-overview.md)
