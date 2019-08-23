---
title: Types migrés de WPF vers System.Xaml
ms.date: 03/30/2017
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
ms.openlocfilehash: 943cdb2a21cbf2f95ef7fe2feefe6c0e71f57be4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939681"
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>Types migrés de WPF vers System.Xaml
Dans .NET Framework 3,5 et .NET Framework 3,0, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] et Windows Workflow Foundation inclus une implémentation du langage XAML. La plupart des types publics qui fournissaient une extensibilité pour l'implémentation XAML WPF se trouvaient dans les assemblys WindowsBase, PresentationCore et PresentationFramework. De même, les types publics qui fournissaient une extensibilité pour Windows Workflow Foundation XAML existaient dans l’assembly System. Workflow. ComponentModel. Dans le .NET Framework 4, certains des types XAML sont migrés vers l’assembly System. Xaml. Une implémentation courante de .NET Framework des services de langage XAML autorise de nombreux scénarios d’extensibilité XAML qui étaient initialement définis par l’implémentation XAML d’une infrastructure spécifique, mais qui font désormais partie de la prise en charge globale du langage XAML .NET Framework 4. Cette rubrique répertorie les types qui sont migrés et traite des problèmes relatifs à la migration.  
  
<a name="assemblies_and_namespaces"></a>   
## <a name="assemblies-and-namespaces"></a>Assemblys et espaces de noms  
 Dans .NET Framework 3,5 et .NET Framework 3,0, les types implémentés par WPF pour prendre en charge le langage <xref:System.Windows.Markup> XAML se trouvaient généralement dans l’espace de noms. La plupart de ces types se trouvaient dans l'assembly WindowsBase.  
  
 Dans .NET Framework 4, il existe un nouvel <xref:System.Xaml> espace de noms et un nouvel assembly System. Xaml. La plupart des types implémentés initialement pour XAML WPF sont maintenant fournis comme points ou services d'extensibilité pour les implémentations du langage XAML. En vue de les rendre disponibles pour des scénarios plus généraux, les types sont transférés de leur assembly WPF d'origine vers l'assembly System.Xaml. Cela permet des scénarios d’extensibilité XAML sans avoir à inclure les assemblys d’autres infrastructures (telles que WPF et Windows Workflow Foundation).  
  
 En ce qui concerne les types migrés, ils restent pour la plupart dans l'espace de noms <xref:System.Windows.Markup> . Cela permettait en partie d'éviter d'interrompre le mappage des espaces de noms CLR dans les implémentations existantes par fichier. Par conséquent, l' <xref:System.Windows.Markup> espace de noms dans .NET Framework 4 contient un mélange de types généraux de prise en charge du langage XAML (à partir de l’assembly System. Xaml) et de types spécifiques à l’implémentation XAML WPF (à partir de WindowsBase et d’autres assemblys WPF). Tous les types migrés vers System.Xaml, mais se trouvant déjà dans un assembly WPF, prennent en charge le transfert des types dans la version 4 de l'assembly WPF.  
  
### <a name="workflow-xaml-support-types"></a>Types de prise en charge XAML du flux de travail  
 Windows Workflow Foundation également fourni des types de prise en charge XAML, et dans de nombreux cas, ils avaient des noms courts identiques à un équivalent WPF. Voici une liste de Windows Workflow Foundation types de prise en charge XAML:  
  
- <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>  
  
 Ces types de prise en charge existent toujours dans les assemblys Windows Workflow Foundation pour .NET Framework 4 et peuvent toujours être utilisés pour des applications Windows Workflow Foundation spécifiques; Toutefois, ils ne doivent pas être référencés par des applications ou des infrastructures qui n’utilisent pas de Windows Workflow Foundation.  
  
<a name="markupextension"></a>   
## <a name="markupextension"></a>MarkupExtension  
 Dans les .NET Framework 3,5 et .NET Framework 3,0, la <xref:System.Windows.Markup.MarkupExtension> classe pour WPF était dans l’assembly WindowsBase. Une classe parallèle pour Windows Workflow Foundation, <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>, existait dans l’assembly System. Workflow. ComponentModel. Dans le .NET Framework 4, la <xref:System.Windows.Markup.MarkupExtension> classe est migrée vers l’assembly System. Xaml. Dans le .NET Framework 4, <xref:System.Windows.Markup.MarkupExtension> est destiné aux scénarios d’extensibilité XAML qui utilisent des services .NET Framework XAML, pas seulement pour ceux qui s’appuient sur des infrastructures spécifiques. Lorsque cela est possible, les infrastructures spécifiques ou le code utilisateur de l'infrastructure doivent également s'appuyer sur la classe <xref:System.Windows.Markup.MarkupExtension> pour l'extension XAML.  
  
<a name="markupextension_supporting_service_classes"></a>   
## <a name="markupextension-supporting-service-classes"></a>Classes de services de prise en charge MarkupExtension  
 .NET Framework 3,5 et .NET Framework 3,0 pour WPF fournissaient plusieurs services qui étaient disponibles <xref:System.Windows.Markup.MarkupExtension> pour les implémenteurs et les <xref:System.ComponentModel.TypeConverter> implémentations afin de prendre en charge l’utilisation des types/propriétés en XAML. Ces services sont les suivants :  
  
- <xref:System.Windows.Markup.IProvideValueTarget>  
  
- <xref:System.Windows.Markup.IUriContext>  
  
- <xref:System.Windows.Markup.IXamlTypeResolver>  
  
> [!NOTE]
> L' <xref:System.Windows.Markup.IReceiveMarkupExtension> interface est un autre service de .NET Framework 3,5 qui est lié aux extensions de balisage. <xref:System.Windows.Markup.IReceiveMarkupExtension>n’a pas été migrée et `[Obsolete]` est marqué pour .NET Framework 4. Les scénarios qui utilisaient l'interface <xref:System.Windows.Markup.IReceiveMarkupExtension> doivent désormais utiliser les rappels avec attribut <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> . La classe<xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute> est également signalée comme `[Obsolete]`.  
  
<a name="xaml_language_features"></a>   
## <a name="xaml-language-features"></a>Fonctionnalités du langage XAML  
 Plusieurs fonctionnalités et composants du langage XAML pour WPF se trouvaient déjà dans l'assembly PresentationFramework. Ils ont été implémentés en tant que sous-classe <xref:System.Windows.Markup.MarkupExtension> pour exposer les utilisations des extensions de balisage en XAML dans le balisage XAML. Dans .NET Framework 4, elles existent dans l’assembly System. Xaml afin que les projets qui n’incluent pas les assemblys WPF puissent utiliser ces fonctionnalités au niveau du langage XAML. WPF utilise ces mêmes implémentations pour les applications .NET Framework 4. Comme avec d'autres situations répertoriées dans cette rubrique, les types de prise en charge se trouvent toujours dans l'espace de noms <xref:System.Windows.Markup> afin d'éviter d'endommager les références précédentes.  
  
 Le tableau suivant contient une liste des classes de prise en charge des fonctionnalités XAML définies dans System.Xaml.  
  
|Fonctionnalité du langage XAML|Usage|  
|---------------------------|-----------|  
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|  
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|  
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|  
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|  
  
 Bien que System.Xaml ne dispose pas nécessairement de classes de prise en charge spécifiques, la logique générale en matière de traitement des fonctionnalités du langage XAML se trouve désormais dans System.Xaml, ainsi que dans ses lecteurs et writers XAML implémentés. Par exemple, `x:TypeArguments` est un attribut traité par les lecteurs et les writers XAML des implémentations System.Xaml. Il peut être signalé dans le flux de nœud XAML, gère le contexte de schéma XAML par défaut (basé sur CLR), a une représentation système de type XAML, etc. Par conséquent, la documentation de référence pour toutes les fonctionnalités au niveau du langage XAML constitue une sous-rubrique des [XAML Services](index.md) et de cette zone générale de l’ensemble de documentation .NET Framework, et ne fait donc pas partie de la documentation WPF comme sous-rubrique de la rubrique [Avancé (Windows Presentation Foundation)](../wpf/advanced/index.md) (comme c’est toujours le cas dans les ensembles de documentation 3.5).  
  
<a name="valueserializer_and_supporting_classes"></a>   
## <a name="valueserializer-and-supporting-classes"></a>ValueSerializer et classes de prise en charge  
 La classe <xref:System.Windows.Markup.ValueSerializer> prend en charge la conversion de type en chaîne, en particulier dans les cas de sérialisation XAML où la sérialisation peut nécessiter plusieurs modes ou nœuds dans la sortie. Dans .NET Framework 3,5 et .NET Framework 3,0, le <xref:System.Windows.Markup.ValueSerializer> pour WPF était dans l’assembly WindowsBase. Dans le .NET Framework 4, la <xref:System.Windows.Markup.ValueSerializer> classe se trouve dans System. xaml et est destinée aux scénarios d’extensibilité XAML, et pas uniquement à ceux qui s’appuient sur WPF. <xref:System.Windows.Markup.IValueSerializerContext> (service de prise en charge) et <xref:System.Windows.Markup.DateTimeValueSerializer> (sous-classe spécifique) sont également migrés vers System.Xaml.  
  
<a name="xamlrelated_attributes"></a>   
## <a name="xaml-related-attributes"></a>Attributs XAML  
 XAML WPF incluait plusieurs attributs qui peuvent être appliqués aux types CLR pour indiquer certains éléments concernant leur comportement XAML. La liste suivante répertorie les attributs qui existaient dans les assemblys WPF dans .NET Framework 3,5 et .NET Framework 3,0. Ces attributs sont migrés vers System. xaml dans .NET Framework 4.  
  
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
  
<a name="miscellaneous_classes"></a>   
## <a name="miscellaneous-classes"></a>Classes diverses  
 L' <xref:System.Windows.Markup.IComponentConnector> interface existait dans WindowsBase dans le .NET Framework 3,5 et .NET Framework 3,0, mais elle existe dans System. xaml dans .NET Framework 4. <xref:System.Windows.Markup.IComponentConnector> est principalement conçu pour la prise en charge des outils et les compilateurs de balisage XAML.  
  
 L' <xref:System.Windows.Markup.INameScope> interface existait dans WindowsBase dans le .NET Framework 3,5 et .NET Framework 3,0, mais elle existe dans System. xaml dans .NET Framework 4. <xref:System.Windows.Markup.INameScope> définit les opérations de base pour une portée de nom XAML.  
  
<a name="xamlrelated_classes_with_shared_names_that_exist_in_wpf_and_systemxaml"></a>   
## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>Classes XAML portant les noms partagés qui se trouvent dans WPF et System.Xaml  
 Les classes suivantes existent à la fois dans les assemblys WPF et dans l’assembly System. xaml dans le .NET Framework 4:  
  
 `XamlReader`  
  
 `XamlWriter`  
  
 `XamlParseException`  
  
 L'implémentation WPF se trouve dans l'espace de noms <xref:System.Windows.Markup> et l'assembly PresentationFramework. L'implémentation System.Xaml se trouve dans l'espace de noms <xref:System.Xaml> . En général, si vous utilisez des types WPF ou dérivez de types WPF, vous devez utiliser les implémentations WPF de <xref:System.Windows.Markup.XamlReader> et <xref:System.Windows.Markup.XamlWriter> , et non les implémentations System.Xaml. Pour plus d'informations, consultez la section Notes dans <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> et <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>.  
  
 Si vous incluez des références aux assemblys WPF et System.Xaml, et si vous utilisez également des instructions `include` pour les espaces de noms <xref:System.Windows.Markup> et <xref:System.Xaml> , vous devrez peut-être qualifier pleinement les appels à ces API afin de résoudre les types sans ambiguïté.  
  
## <a name="see-also"></a>Voir aussi

- [Services XAML](index.md)
