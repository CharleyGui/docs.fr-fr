---
title: Convertisseurs de types et extensions de balisage pour XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services
- XAML [XAML Services], value converters
- XAML [XAML Services], markup extension services
- value converters for XAML [XAML Services]
- XAML [XAML Services], service context
ms.assetid: db07a952-05ce-4aa4-b6f9-aac7397d0326
ms.openlocfilehash: 6d859f5f341eaf7c86573077ec56eab7b4cd7bb8
ms.sourcegitcommit: 90f0bee0e8a416e45c78fa3ad4c91ef00e5228d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66722554"
---
# <a name="type-converters-and-markup-extensions-for-xaml"></a>Convertisseurs de types et extensions de balisage pour XAML
Les convertisseurs de type et les extensions de balisage sont deux techniques que les systèmes de type XAML et les writers XAML utilisent pour générer des composants de graphique d'objets. Bien qu'ils partagent certaines caractéristiques, les convertisseurs de type et les extensions de balisage sont représentés différemment dans un flux de nœud XAML. Dans cet ensemble de documentation, les convertisseurs de type, les extensions de balisage et les constructions similaires sont parfois désignés collectivement sous le nom de « convertisseurs de valeurs ».  
  
<a name="value_converters"></a>   
## <a name="value-converters"></a>Convertisseurs de valeurs  
 En XAML, les convertisseurs de valeurs sont utilisés pour différents scénarios. La liste suivante présente les différents types de convertisseurs de valeur en XAML :  
  
- Convertisseur de type  
  
- Extension de balisage  
  
- Sérialiseur de valeur  
  
- Classe connexe ou classe de prise en charge qui fournit la logique pour une syntaxe de texte XAML  
  
<a name="type_converters"></a>   
## <a name="type-converters"></a>Convertisseurs de type  
 Dans la définition des services XAML .NET Framework, les convertisseurs de type sont des classes qui dérivent de la classe CLR <xref:System.ComponentModel.TypeConverter> . <xref:System.ComponentModel.TypeConverter> est une classe qui se trouvait dans le Microsoft .NET Framework antérieures à l’introduction de XAML. Son rôle initial était de prendre en charge les fenêtres de propriétés et les métaphores de modification de texte similaires pour les propriétés de l' [!INCLUDE[TLA2#tla_ide](../../../includes/tla2sharptla-ide-md.md)] . L’introduction de XAML dans le .NET Framework utilise <xref:System.ComponentModel.TypeConverter> pour convertir une syntaxe de texte (comme dans une valeur d’attribut ou un nœud de valeur XAML) en objet. <xref:System.ComponentModel.TypeConverter> peut également être utilisée pour sérialiser une valeur d’objet en syntaxe de texte. <xref:System.ComponentModel.TypeConverter> était également utilisée dans les implémentations XAML spécifiques à l’infrastructure précédentes dans Windows Presentation Foundation (WPF) et Windows Communication Foundation (WCF). Pour plus d’informations sur le <xref:System.ComponentModel.TypeConverter> en XAML, consultez [Type Converters for XAML Overview](type-converters-for-xaml-overview.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>Extensions de balisage  
 Dans l'implémentation des services XAML .NET Framework, les extensions de balisage sont des classes qui dérivent de la classe <xref:System.Windows.Markup.MarkupExtension> . Les extensions de balisage sont un concept qui, sous cette forme, provient du langage XAML. Vous pouvez considérer qu'une extension de balisage s'apparente à une séquence d'échappement extensible qui effectue des appels dans une classe de service pour fournir sa logique. Quant au balisage, les processeurs XAML reconnaissent universellement une extension de balisage par une séquence de texte qui commence par une accolade ouvrante ({) dans une chaîne de texte.  
  
 Les extensions de balisage diffèrent des convertisseurs de type. Les convertisseurs de type sont généralement associés à des types ou à des membres. Ils sont appelés lors de la création d'un graphique d'objets ou quand une sérialisation rencontre une syntaxe de texte associée à ces entités.  
  
 Les extensions de balisage sont associées à une seule classe de service de prise en charge, mais peuvent être appliquées pour toute valeur de membre. (Toutefois, vous pouvez implémenter votre extension de balisage pour limiter délibérément son utilisation à certains membres ou types de destination, à l'aide du contexte de service). Les extensions de balisage peuvent remplacer une association de convertisseurs de type. Ou vous pouvez les utiliser pour spécifier une valeur d'attribut pour les membres qui, sans cela, ne prendrait pas en charge une syntaxe de texte.  
  
 Pour plus d’informations sur le modèle d’implémentation d’extensions de balisage pour XAML, consultez [Markup Extensions for XAML Overview](markup-extensions-for-xaml-overview.md).  
  
> [!NOTE]
>  Les types <xref:System.Windows.Markup.MarkupExtension> et <xref:System.Windows.Markup.ValueSerializer> sont trouvent tous les deux dans l'espace de noms <xref:System.Windows.Markup> , et non dans l'espace de noms <xref:System.Xaml> . Cela ne signifie pas que ces types sont spécifiques aux technologies WPF ou Windows Forms qui remplissent normalement les espaces de noms CLR contenant la chaîne `Windows`. <xref:System.Windows.Markup.MarkupExtension> et <xref:System.Windows.Markup.ValueSerializer> se trouvent dans l'assembly System.Xaml et n'ont pas de dépendance d'infrastructure spécifique. Ces types existaient dans l’espace de noms CLR pour .NET Framework 3.0 et restent dans l’espace de noms CLR dans .NET Framework 4 afin d’éviter de rompre des références dans des projets WPF existants. Pour plus d'informations, consultez [Types Migrated from WPF to System.Xaml](types-migrated-from-wpf-to-system-xaml.md).  
  
<a name="value_serializers"></a>   
## <a name="value-serializers"></a>Sérialiseurs de valeur  
 Un <xref:System.Windows.Markup.ValueSerializer> est un convertisseur de type spécialisé qui est optimisé pour la conversion d'un objet en chaîne. Il est possible qu'un <xref:System.Windows.Markup.ValueSerializer> pour XAML n'implémente pas du tout la méthode `ConvertFrom` . Une implémentation de <xref:System.Windows.Markup.ValueSerializer> obtient des services d'une manière qui ressemble à une implémentation de <xref:System.ComponentModel.TypeConverter> . Les méthodes virtuelles fournissent un paramètre d'entrée `context` . Le paramètre `context` est de type <xref:System.Windows.Markup.IValueSerializerContext>, qui hérite de l'interface <xref:System.IServiceProvider> et a une méthode <xref:System.IServiceProvider.GetService%2A> .  
  
 Dans le système de type XAML et pour les implémentations de writer XAML utilisant un traitement des boucles de nœud XAML pour la sérialisation, un convertisseur de valeurs qui est associé à un type ou à un membre est signalé par sa propre propriété <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> . Pour les writers XAML qui effectuent la sérialisation, cela signifie que s'il existe une propriété <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> et une propriété <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> , le convertisseur de type doit être utilisé pour le chemin de chargement, et le sérialiseur de valeur doit être utilisé pour le chemin d'enregistrement. Si <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> existe mais que <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> a la valeur `null`, le convertisseur de type est également utilisé pour le chemin d'enregistrement.  
  
<a name="other_value_converters"></a>   
## <a name="other-value-converters"></a>Autres convertisseurs de valeurs  
 Un convertisseur de valeurs est extensible au-delà des modèles spécifiques d'un convertisseur de type ou d'une extension de balisage. Cependant, cette personnalisation nécessiterait également la redéfinition du système de type XAML tel que fourni par les services XAML .NET Framework. Le système de type XAML existant a des représentations et des systèmes de création de rapports pour les convertisseurs de type, les extensions de balisage et les sérialiseurs de valeurs, mais pas pour les formes personnalisées de conversion de valeurs. Si vous souhaitez créer des convertisseurs de valeurs personnalisés, utilisez le type <xref:System.Xaml.Schema.XamlValueConverter%601> .  
  
<a name="type_converters_and_markup_extensions_in_combination"></a>   
## <a name="type-converters-and-markup-extensions-in-combination"></a>Convertisseurs de type et extensions de balisage pour XAML  
 Les extensions de balisage et les convertisseurs de type sont utilisés pour des situations différentes en XAML. Bien que le contexte soit disponible pour les extensions de balisage, le comportement de la conversion de type des propriétés où une extension de balisage fournit une valeur n'est généralement pas vérifié dans les implémentations d'extension de balisage. En d'autres termes, même si une extension de balisage retourne une chaîne de texte comme sortie de `ProvideValue` , le comportement de la conversion de type sur cette chaîne tel qu'appliqué à une propriété ou à un type de valeur de propriété spécifique n'est pas appelé. En général, le but d'une extension de balisage est de traiter une chaîne et de retourner un objet sans qu'aucun convertisseur de type ne soit impliqué.  
  
<a name="service_context_for_a_value_converter"></a>   
## <a name="service-context-for-a-value-converter"></a>Contexte de service pour un convertisseur de valeurs  
 Lorsque vous implémentez un convertisseur de valeurs, vous devez souvent accéder à un contexte dans lequel le convertisseur de valeurs est appliqué. Ce contexte est appelé « contexte de service ». Le contexte de service peut inclure des informations telles que le contexte de schéma XAML actif, l'accès au système de mappage de type fourni par le contexte de schéma XAML et le writer d'objet XAML, etc. Pour plus d’informations sur les contextes de services disponibles pour un convertisseur de valeurs et pour savoir comment accéder aux services pouvant être fournis par un contexte de service, consultez [Contextes de services disponibles aux convertisseurs de types ou aux extensions de balisage](service-contexts-available-to-type-converters-and-markup-extensions.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [Vue d’ensemble des extensions de balisage pour XAML](markup-extensions-for-xaml-overview.md)
- [Vue d'ensemble des convertisseurs de types pour XAML](type-converters-for-xaml-overview.md)
- [Service Contexts Available to Type Converters and Markup Extensions](service-contexts-available-to-type-converters-and-markup-extensions.md)
