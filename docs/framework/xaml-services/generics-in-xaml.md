---
title: Génériques en XAML
ms.date: 03/30/2017
helpviewer_keywords:
- generics [XAML Services]
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
ms.openlocfilehash: 6ca7986513d1a6cbe160ca1a0af6699c323aac7e
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690640"
---
# <a name="generics-in-xaml"></a>Génériques en XAML
Les Services XAML .NET Framework tel qu’implémenté dans System.Xaml prend en charge l’utilisation des types CLR génériques. Cette prise en charge inclut la spécification des contraintes de génériques comme argument de type et l’application de la contrainte en appelant approprié `Add` méthode pour les cas de collection générique. Cette rubrique décrit les aspects de l’utilisation et référencement des types génériques en XAML.  
  
## <a name="xtypearguments"></a>x:TypeArguments  
 `x:TypeArguments` est une directive définie par le langage XAML. Lorsqu’il est utilisé en tant que membre d’un type XAML qui est sauvegardé par un type générique, `x:TypeArguments` passe contraindre des arguments du générique au constructeur de stockage de type. Pour la syntaxe de référence relative aux Services XAML du .NET Framework utilisent `x:TypeArguments`, qui inclut des exemples de syntaxe, consultez [x : TypeArguments Directive](x-typearguments-directive.md).  
  
 Étant donné que `x:TypeArguments` prend une chaîne, et a la sauvegarde de convertisseur de type, il est généralement déclaré dans l’utilisation XAML en tant qu’attribut.  
  
 Dans le flux de nœud XAML, les informations déclarées par `x:TypeArguments` peut être obtenu à partir de <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> à un `StartObject` position dans le flux de nœud. La valeur de retour de <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> est une liste de <xref:System.Xaml.XamlType> valeurs. Déterminer si un type XAML représente un type générique peut être effectuée en appelant <xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=nameWithType>.  
  
## <a name="rules-and-syntax-conventions-for-generics-in-xaml"></a>Règles et Conventions de syntaxe des génériques en XAML  
 Dans XAML, un type générique doit toujours être représenté comme contrainte générique ; un générique sans contrainte n’est jamais présent dans le système de type XAML ou un flux de nœud XAML et ne peut pas être représenté dans le balisage XAML. Un générique peut être référencé dans la syntaxe d’attribut XAML, dans les cas où il est une contrainte de type imbriqué d’un générique référencé par `x:TypeArguments`, ou pour les cas où `x:Type` fournit une référence de type CLR pour un type générique. Cela est pris en charge par le biais du <xref:System.Xaml.Schema.XamlTypeTypeConverter> classe définie par les Services XAML .NET Framework.  
  
 Le XAML activé en forme de la syntaxe d’attribut <xref:System.Xaml.Schema.XamlTypeTypeConverter> modifie le MSIL classique / convention de syntaxe CLR qui utilise des crochets pour les types et contraintes de génériques et substitue à la place des parenthèses pour le conteneur de contrainte. Pour obtenir un exemple, consultez [x : TypeArguments Directive](x-typearguments-directive.md).  
  
## <a name="generics-and-xaml-2009-features"></a>Génériques et les fonctionnalités de XAML 2009  
 Si vous utilisez XAML 2009 au lieu de mapper le CLR des types pour obtenir les types XAML pour les primitives de langage courantes de base, vous pouvez utiliser [types intégrés XAML 2009](built-in-types-for-common-xaml-language-primitives.md) en tant qu’éléments d’information dans `x:TypeArguments`. Par exemple, vous pouvez déclarer les éléments suivants (ne pas indiqués, les mappages de préfixe, mais `x` est l’espace de noms XAML de langage XAML pour XAML 2009) :  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
## <a name="generics-support-in-wpf-and-other-v35-frameworks"></a>Prise en charge des génériques dans WPF et d’autres infrastructures v3.5  
 Pour l’utilisation de XAML 2006 en ciblant spécifiquement WPF, [x : Class](x-class-directive.md) doit également être fourni dans le même élément que `x:TypeArguments`, et cet élément doit être l’élément racine dans un document XAML. L’élément racine doit mapper à un type générique au moins un argument de type. Par exemple, <xref:System.Windows.Navigation.PageFunction%601>.  
  
 Solutions de contournement possible pour prendre en charge des utilisations génériques incluent la définition d’une extension de balisage personnalisée qui peut retourner des types génériques, ou fournir un retour à la ligne définition qui dérive d’un type générique, mais aplanit la contrainte générique dans sa propre définition de classe de la classe.  
  
 Dans WPF et le ciblage de .NET Framework 4, vous pouvez utiliser les fonctionnalités XAML 2009 avec `x:TypeArguments`, mais uniquement pour XAML libre (XAML non compilé par balisage). Le code XAML compilé par balisage pour WPF et la forme BAML du code XAML ne prennent actuellement pas en charge les mots clés et les fonctionnalités XAML 2009.  
  
 Flux de travail personnalisés dans Windows Workflow Foundation pour .NET Framework 3.5 ne gèrent pas l’utilisation XAML générique.  
  
## <a name="see-also"></a>Voir aussi

- [x:TypeArguments, directive](x-typearguments-directive.md)
- [x:Class, directive](x-class-directive.md)
- [Types intégrés pour les primitives associées au langage XAML courant](built-in-types-for-common-xaml-language-primitives.md)
