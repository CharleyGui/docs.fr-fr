---
title: Types migrés de WPF vers System.Xaml
ms.date: 03/30/2017
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
ms.openlocfilehash: 5aa2d8a39be47d9affb97c3b60e53c4722c63cce
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249801"
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>Types migrés de WPF à System.Xaml

Dans .NET Framework 3.5 et .NET Framework 3.0, Windows Presentation Foundation (WPF) et Windows Workflow Foundation ont inclus une implémentation linguistique XAML. La plupart des types publics qui fournissaient une extensibilité pour l'implémentation XAML WPF se trouvaient dans les assemblys WindowsBase, PresentationCore et PresentationFramework. De même, les types publics qui ont fourni l’extéabilité pour Windows Workflow Foundation XAML existaient dans l’assemblage System.Workflow.ComponentModel. Dans le cadre .NET 4, certains des types liés à XAML ont été migrés vers l’assemblage System.Xaml. Une mise en œuvre commune du Cadre .NET des services linguistiques XAML permet de nombreux scénarios d’extétabilité XAML qui ont été initialement définis par la mise en œuvre XAML d’un cadre spécifique, mais font maintenant partie de l’ensemble .NET Framework 4 XAML support linguistique. Cet article énumère les types qui ont été migrés et traite des questions liées à la migration.

## <a name="assemblies-and-namespaces"></a>Assemblys et espaces de noms

Dans .NET Framework 3.5 et .NET Framework 3.0, les types que WPF a mis en œuvre pour soutenir XAML étaient généralement dans l’espace nom. <xref:System.Windows.Markup> La plupart de ces types se trouvaient dans l'assembly WindowsBase.

Dans .NET Framework 4, <xref:System.Xaml> il y a un nouvel espace de nom et un nouvel assemblage System.Xaml. La plupart des types implémentés initialement pour XAML WPF sont maintenant fournis comme points ou services d'extensibilité pour les implémentations du langage XAML. En vue de les rendre disponibles pour des scénarios plus généraux, les types sont transférés de leur assembly WPF d'origine vers l'assembly System.Xaml. Cela permet aux scénarios d’extéabilité XAML sans avoir à inclure les assemblages d’autres cadres (tels que WPF et Windows Workflow Foundation).

En ce qui concerne les types migrés, ils restent pour la plupart dans l'espace de noms <xref:System.Windows.Markup> . Cela permettait en partie d'éviter d'interrompre le mappage des espaces de noms CLR dans les implémentations existantes par fichier. En conséquence, <xref:System.Windows.Markup> l’espace nom dans .NET Framework 4 contient un mélange de types de support linguistique XAML général (de l’assemblage System.Xaml) et les types qui sont spécifiques à la mise en œuvre WPF XAML (de WindowsBase et d’autres assemblages WPF). Tous les types migrés vers System.Xaml, mais se trouvant déjà dans un assembly WPF, prennent en charge le transfert des types dans la version 4 de l'assembly WPF.

### <a name="workflow-xaml-support-types"></a>Types de prise en charge XAML du flux de travail

Windows Workflow Foundation a également fourni des types de support XAML, et dans de nombreux cas, ceux-ci avaient des noms courts identiques à un équivalent WPF. Ce qui suit est une liste de Windows Workflow Foundation XAML types de support:

- <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>

- <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>

- <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>

Ces types de support existent toujours dans les assemblages de la Fondation Windows Workflow pour .NET Framework 4 et peuvent encore être utilisés pour des applications spécifiques de la Fondation Windows Workflow; cependant, ils ne doivent pas être référencés par des applications ou des cadres qui n’utilisent pas Windows Workflow Foundation.

## <a name="markupextension"></a>MarkupExtension

Dans le cadre .NET 3.5 et .NET Framework <xref:System.Windows.Markup.MarkupExtension> 3.0, la classe de WPF était dans l’assemblage WindowsBase. Une classe parallèle pour Windows <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>Workflow Foundation, , existait dans l’assemblage System.Workflow.ComponentModel. Dans le cadre .NET <xref:System.Windows.Markup.MarkupExtension> 4, la classe est migrée vers l’assemblage System.Xaml. Dans le cadre .NET <xref:System.Windows.Markup.MarkupExtension> 4, est destiné à tout scénario d’extéabilité XAML qui utilise .NET XAML Services, pas seulement pour ceux qui s’appuient sur des cadres spécifiques. Lorsque cela est possible, les infrastructures spécifiques ou le code utilisateur de l'infrastructure doivent également s'appuyer sur la classe <xref:System.Windows.Markup.MarkupExtension> pour l'extension XAML.

## <a name="markupextension-supporting-service-classes"></a>Classes de services de prise en charge MarkupExtension

.NET Framework 3.5 et .NET Framework 3.0 pour WPF ont fourni plusieurs services qui étaient disponibles pour <xref:System.Windows.Markup.MarkupExtension> les implémenteurs et <xref:System.ComponentModel.TypeConverter> les implémentations pour soutenir l’utilisation de type/propriété dans XAML. Ces services sont les suivants :

- <xref:System.Windows.Markup.IProvideValueTarget>

- <xref:System.Windows.Markup.IUriContext>

- <xref:System.Windows.Markup.IXamlTypeResolver>

> [!NOTE]
> Un autre service de .NET Framework 3.5 qui <xref:System.Windows.Markup.IReceiveMarkupExtension> est lié aux extensions de balisage est l’interface. <xref:System.Windows.Markup.IReceiveMarkupExtension>n’a pas été `[Obsolete]` migré et est marqué pour .NET Framework 4. Les scénarios qui utilisaient l'interface <xref:System.Windows.Markup.IReceiveMarkupExtension> doivent désormais utiliser les rappels avec attribut <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> . La classe<xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute> est également signalée comme `[Obsolete]`.

## <a name="xaml-language-features"></a>Fonctionnalités du langage XAML

Plusieurs fonctionnalités et composants du langage XAML pour WPF se trouvaient déjà dans l'assembly PresentationFramework. Ils ont été implémentés en tant que sous-classe <xref:System.Windows.Markup.MarkupExtension> pour exposer les utilisations des extensions de balisage en XAML dans le balisage XAML. Dans .NET Framework 4, ceux-ci existent dans l’assemblage System.Xaml de sorte que les projets qui n’incluent pas les assemblages WPF peuvent utiliser ces fonctionnalités de niveau de langue XAML. WPF utilise ces mêmes implémentations pour les applications .NET Framework 4. Comme avec d'autres situations répertoriées dans cette rubrique, les types de prise en charge se trouvent toujours dans l'espace de noms <xref:System.Windows.Markup> afin d'éviter d'endommager les références précédentes.

Le tableau suivant contient une liste des classes de prise en charge des fonctionnalités XAML définies dans System.Xaml.

|Fonctionnalité du langage XAML|Usage|
|---------------------------|-----------|
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|

Bien que System.Xaml ne dispose pas nécessairement de classes de prise en charge spécifiques, la logique générale en matière de traitement des fonctionnalités du langage XAML se trouve désormais dans System.Xaml, ainsi que dans ses lecteurs et writers XAML implémentés. Par exemple, `x:TypeArguments` est un attribut traité par les lecteurs et les writers XAML des implémentations System.Xaml. Il peut être signalé dans le flux de nœud XAML, gère le contexte de schéma XAML par défaut (basé sur CLR), a une représentation système de type XAML, etc. En conséquence, la documentation de référence pour toutes les fonctionnalités de niveau de langue XAML est un sous-topique pour [XAML Services](../../../desktop-wpf/xaml-services/index.md) dans le [Guide de bureau pour Windows Presentation Foundation (WPF)](../../../desktop-wpf/overview/index.md).

## <a name="valueserializer-and-supporting-classes"></a>ValueSerializer et classes de prise en charge

La classe <xref:System.Windows.Markup.ValueSerializer> prend en charge la conversion de type en chaîne, en particulier dans les cas de sérialisation XAML où la sérialisation peut nécessiter plusieurs modes ou nœuds dans la sortie. Dans .NET Framework 3.5 et .NET Framework <xref:System.Windows.Markup.ValueSerializer> 3.0, le WPF pour était dans l’assemblage WindowsBase. Dans le cadre .NET <xref:System.Windows.Markup.ValueSerializer> 4, la classe est dans System.Xaml et est destiné à tout scénario d’extéabilité XAML, pas seulement pour ceux qui s’appuient sur WPF. <xref:System.Windows.Markup.IValueSerializerContext> (service de prise en charge) et <xref:System.Windows.Markup.DateTimeValueSerializer> (sous-classe spécifique) sont également migrés vers System.Xaml.

## <a name="xaml-related-attributes"></a>Attributs XAML

XAML WPF incluait plusieurs attributs qui peuvent être appliqués aux types CLR pour indiquer certains éléments concernant leur comportement XAML. Ce qui suit est une liste des attributs qui existaient dans les assemblées WPF dans .NET Framework 3.5 et .NET Framework 3.0. Ces attributs sont migrés vers System.Xaml dans .NET Framework 4.

- <xref:System.Windows.Markup.AmbientAttribute>

- <xref:System.Windows.Markup.ContentPropertyAttribute>

- <xref:System.Windows.Markup.ContentWrapperAttribute>

- <xref:System.Windows.Markup.DependsOnAttribute>

- <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>

- <xref:System.Windows.Markup.NameScopePropertyAttribute>

- <xref:System.Windows.Markup.RootNamespaceAttribute>

- <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>

- <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>

- <xref:System.Windows.Markup.ValueSerializerAttribute>

- <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>

- <xref:System.Windows.Markup.XmlLangPropertyAttribute>

- <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>

- <xref:System.Windows.Markup.XmlnsDefinitionAttribute>

- <xref:System.Windows.Markup.XmlnsPrefixAttribute>

## <a name="miscellaneous-classes"></a>Classes diverses

L’interface <xref:System.Windows.Markup.IComponentConnector> existait dans WindowsBase dans .NET Framework 3.5 et .NET Framework 3.0, mais existe dans System.Xaml dans .NET Framework 4. <xref:System.Windows.Markup.IComponentConnector> est principalement conçu pour la prise en charge des outils et les compilateurs de balisage XAML.

L’interface <xref:System.Windows.Markup.INameScope> existait dans WindowsBase dans .NET Framework 3.5 et .NET Framework 3.0, mais existe dans System.Xaml dans .NET Framework 4. <xref:System.Windows.Markup.INameScope> définit les opérations de base pour une portée de nom XAML.

## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>Classes XAML portant les noms partagés qui se trouvent dans WPF et System.Xaml

Les classes suivantes existent à la fois dans les assemblages WPF et l’assemblage System.Xaml dans .NET Framework 4 :

`XamlReader`

`XamlWriter`

`XamlParseException`

L'implémentation WPF se trouve dans l'espace de noms <xref:System.Windows.Markup> et l'assembly PresentationFramework. L'implémentation System.Xaml se trouve dans l'espace de noms <xref:System.Xaml> . En général, si vous utilisez des types WPF ou dérivez de types WPF, vous devez utiliser les implémentations WPF de <xref:System.Windows.Markup.XamlReader> et <xref:System.Windows.Markup.XamlWriter> , et non les implémentations System.Xaml. Pour plus d'informations, consultez la section Notes dans <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> et <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>.

Si vous incluez des références aux assemblys WPF et System.Xaml, et si vous utilisez également des instructions `include` pour les espaces de noms <xref:System.Windows.Markup> et <xref:System.Xaml> , vous devrez peut-être qualifier pleinement les appels à ces API afin de résoudre les types sans ambiguïté.
