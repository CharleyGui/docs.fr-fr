---
title: x:Static, extension de balisage
ms.date: 03/30/2017
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
ms.openlocfilehash: 9fa9e51e66af6df4d1a6b1ec94c5010651bbb21d
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401502"
---
# <a name="xstatic-markup-extension"></a>x:Static, extension de balisage
Fait référence à toute entité de code statique par valeur définie dans une méthode conforme à la Common Language Specification (CLS). La propriété statique référencée peut être utilisée pour fournir la valeur d’une propriété en XAML.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xaml  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
| | |  
|-|-|  
|`prefix`|facultatif. Préfixe qui fait référence à un espace de noms XAML mappé non défini par défaut. `prefix`s’affiche de manière explicite dans l’utilisation, car vous référencez rarement des propriétés statiques provenant d’un espace de noms XAML par défaut. Consultez la section Notes.|  
|`typeName`|Requis. Nom du type qui définit le membre statique souhaité.|  
|`staticMemberName`|Requis. Nom du membre de valeur statique souhaité (une constante, une propriété statique, un champ ou une valeur d’énumération).|  
  
## <a name="remarks"></a>Notes  

L’entité de code référencée doit être l’une des suivantes:  
  
- Une constante  
- Une propriété statique  
- Un champ  
- Valeur d’énumération

La spécification d’une autre entité de code, telle qu’une propriété non statique, provoque une erreur au moment de la compilation si le XAML est compilé par balisage, ou une exception d’analyse au moment du chargement XAML.  

Vous pouvez créer `x:Static` des références à des champs ou des propriétés statiques qui ne sont pas dans l’espace de noms XAML par défaut pour le document XAML actuel; Toutefois, cela nécessite un mappage de préfixe. Les espaces de noms XAML sont presque toujours définis sur l’élément racine du document XAML.  

Les opérations de recherche pour les propriétés statiques peuvent être effectuées par .NET Framework les services XAML et ses lecteurs et writers XAML, lorsqu’ils s’exécutent avec le contexte de schéma XAML par défaut. Ce contexte de schéma XAML peut utiliser la réflexion CLR pour fournir les valeurs statiques nécessaires pour la construction du graphique d’objets. Le `typeName` que vous spécifiez est en fait un nom de type XAML, et non un nom de type CLR, bien qu’il s’agisse d’un nom identique lors de l’utilisation du contexte de schéma XAML par défaut ou de l’utilisation de tous les frameworks d’implémentation XAML basés sur CLR existants.  

Soyez prudent lorsque vous faites `x:Static` des références qui ne sont pas directement le type de la valeur d’une propriété. Dans la séquence de traitement XAML, les valeurs fournies par une extension de balisage n’appellent pas la conversion de valeur supplémentaire. Cela est vrai même si votre `x:Static` référence crée une chaîne de texte, et une conversion de valeur pour les valeurs d’attribut basées sur une chaîne de texte se produit généralement pour ce membre spécifique ou pour toutes les valeurs de membre du type de retour.  

La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage. Le jeton de chaîne fourni après la chaîne d’identificateur `x:Static` est assigné en tant que valeur <xref:System.Windows.Markup.StaticExtension.Member%2A> de la classe d’extension <xref:System.Windows.Markup.StaticExtension> sous-jacente.  

Il existe deux autres utilisations de XAML qui sont techniquement possibles. Toutefois, ces utilisations sont moins courantes, car elles sont inutilement détaillées:  

1. Syntaxe d’élément objet.

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

2. Syntaxe d’attribut avec propriété de membre explicite pour la chaîne d’initialisation.

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

Dans l’implémentation des services XAML .NET Framework, la gestion de cette extension de balisage est <xref:System.Windows.Markup.StaticExtension> définie par la classe.  

`x:Static` est une extension de balisage. Toutes les extensions de balisage en `{` XAML `}` utilisent les caractères et dans leur syntaxe d’attribut, qui est la Convention selon laquelle un processeur XAML reconnaît qu’une extension de balisage doit fournir une valeur. Pour plus d’informations sur les extensions de balisage, consultez [Markup Extensions for XAML Overview](markup-extensions-for-xaml-overview.md).  
  
## <a name="wpf-usage-notes"></a>Remarques sur l’utilisation de WPF  
 L’espace de noms XAML par défaut que vous utilisez pour la programmation WPF ne contient pas de nombreuses propriétés statiques utiles, et la plupart des propriétés statiques utiles prennent en charge des convertisseurs de type qui facilitent l’utilisation sans nécessiter `{x:Static}` . Pour les propriétés statiques, vous devez mapper un préfixe pour un espace de noms XAML si l’une des conditions suivantes est vraie:  
  
- Vous référencez un type qui existe dans WPF, mais qui ne fait pas partie de l’espace de noms[!INCLUDE[TLA#tla_wpfxmlnsv1](../../../includes/tlasharptla-wpfxmlnsv1-md.md)]XAML par défaut pour WPF (). Il s’agit d’un scénario assez courant `x:Static`pour l’utilisation de. Par exemple, vous pouvez utiliser une `x:Static` référence avec un mappage d’espace de noms <xref:System> XAML à l’espace de noms CLR et à l’assembly mscorlib pour <xref:System.Environment> référencer les propriétés statiques de la classe.  
  
- Vous référencez un type à partir d’un assembly personnalisé.  
  
- Vous référencez un type qui existe dans un assembly WPF, mais ce type se trouve dans un espace de noms CLR qui n’a pas été mappé pour faire partie de l’espace de noms XAML par défaut WPF. Le mappage des espaces de noms CLR dans l’espace de noms XAML par défaut pour WPF est effectué par les définitions dans les différents assemblys WPF (pour plus d’informations sur ce concept, consultez [espaces de noms XAML et mappage d’espace de noms pour XAML WPF](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)). Les espaces de noms CLR non mappés peuvent exister si cet espace de noms CLR est composé principalement de définitions de classe qui ne sont généralement pas prévues <xref:System.Windows.Threading>pour XAML, telles que.  
  
 Pour plus d’informations sur l’utilisation des préfixes et des espaces de noms XAML pour WPF, consultez [espaces de noms XAML et mappage d’espace de noms pour XAML WPF](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
## <a name="see-also"></a>Voir aussi

- [x:Type, extension de balisage](x-type-markup-extension.md)
- [Types migrés de WPF vers System.Xaml](types-migrated-from-wpf-to-system-xaml.md)
