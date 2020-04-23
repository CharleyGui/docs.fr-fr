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
ms.openlocfilehash: fb9ee6807135f17fd9e0c799533bba28b369ebe2
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072024"
---
# <a name="xstatic-markup-extension"></a>x:Static, extension de balisage

Mentionne toute entité de code de valeur nominale statique qui est définie d’une manière conforme à la spécification linguistique commune (CLS). La propriété statique qui est référencée peut être utilisée pour fournir la valeur d’une propriété dans XAML.

## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML

```xaml
<object property="{x:Static prefix:typeName.staticMemberName}" .../>
```

## <a name="xaml-values"></a>Valeurs XAML

| | |
|-|-|
|`prefix`|facultatif. Un préfixe qui fait référence à un espace de nom XAML cartographié et non par défaut. `prefix`est montré explicitement dans l’utilisation parce que vous faites rarement référence aux propriétés statiques qui proviennent d’un espace de nom XAML par défaut. Consultez la section Notes.|
|`typeName`|Obligatoire. Le nom du type qui définit le membre statique désiré.|
|`staticMemberName`|Obligatoire. Le nom du membre de valeur statique souhaité (une constante, une propriété statique, un champ ou une valeur de recensement).|

## <a name="remarks"></a>Notes

L’entité de code référencée doit être l’une des suivantes :

- Une constante
- Une propriété statique
- Un champ
- Une valeur d’énumération

Spécifier toute autre entité de code, telle qu’une propriété non indiquée, provoque une erreur de compilation-temps si le XAML est compilé, ou une exception XAML de temps de charge.

Vous pouvez `x:Static` faire des références à des champs statiques ou des propriétés qui ne sont pas dans l’espace de nom XAML par défaut pour le document XAML actuel; cependant, cela nécessite une cartographie préfixe. Les espaces de noms XAML sont presque toujours définis sur l’élément racine du document XAML.

Les opérations de recherche pour les propriétés statiques peuvent être effectuées par .NET XAML Services et ses lecteurs XAML et les écrivains XAML, quand ils sont en cours d’exécution avec le contexte de schéma XAML par défaut. Ce contexte de schéma XAML peut utiliser la réflexion CLR pour fournir les valeurs statiques nécessaires pour la construction de graphiques d’objets. Le `typeName` nom que vous spécifiez est en fait un nom de type XAML, pas un nom de type CLR, bien que ce sont essentiellement le même nom lors de l’utilisation du contexte par défaut de schéma XAML ou lors de l’utilisation de tous les cadres existants à base de CLR XAML-mise en œuvre.

Faites preuve de `x:Static` prudence lorsque vous faites des références qui ne sont pas directement le type de valeur d’une propriété. Dans la séquence de traitement XAML, les valeurs fournies à partir d’une extension de balisage n’invoquent pas la conversion de valeur supplémentaire. Cela est vrai `x:Static` même si votre référence crée une chaîne de texte, et une conversion de valeur pour les valeurs d’attribut basée sur la chaîne de texte se produit généralement soit pour ce membre spécifique ou pour les valeurs membres du type de retour.

La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage. Le jeton de chaîne fourni après la chaîne d’identificateur `x:Static` est assigné en tant que valeur <xref:System.Windows.Markup.StaticExtension.Member%2A> de la classe d’extension <xref:System.Windows.Markup.StaticExtension> sous-jacente.

Il y a deux autres utilisations de XAML qui sont techniquement possibles. Cependant, ces utilisations sont moins fréquentes parce qu’elles sont inutilement verbeuses :

01. Syntaxe d’élément d’objet.

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

02. Attribuer la syntaxe avec la propriété explicite du membre pour la chaîne d’initialisation.

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

Dans la mise en œuvre de .NET XAML <xref:System.Windows.Markup.StaticExtension> Services, le traitement de cette extension de balisage est défini par la classe.

`x:Static` est une extension de balisage. Toutes les extensions de balisage dans XAML utilisent la `{` syntaxe d’attribut, `}` qui est la convention par laquelle un processeur XAML reconnaît qu’une extension de balisage doit fournir une valeur. Pour plus d’informations sur les extensions de balisage, consultez [Markup Extensions for XAML Overview](markup-extensions-overview.md).

## <a name="wpf-usage-notes"></a>Remarques sur l'utilisation de WPF

L’espace de nom XAML par défaut que vous utilisez pour la programmation WPF ne contient pas de nombreuses `{x:Static}` propriétés statiques utiles, et la plupart des propriétés statiques utiles ont pris en charge tels que les convertisseurs de type qui facilitent l’utilisation sans avoir besoin . Pour les propriétés statiques, vous devez cartographier un préfixe pour un espace de nom XAML si l’un des éléments suivants est vrai :

- Vous faites référence à un type qui existe dans WPF mais ne fait pas`http://schemas.microsoft.com/winfx/2006/xaml/presentation`partie de l’espace de nom XAML par défaut pour WPF ( ). Il s’agit d’un scénario assez commun pour l’utilisation `x:Static`. Par exemple, vous `x:Static` pouvez utiliser une référence avec une <xref:System> cartographie XAML namespace à l’espace de <xref:System.Environment> nom CLR et l’assemblage mscorlib afin de référencer les propriétés statiques de la classe.

- Vous faites référence à un type d’assemblage personnalisé.

- Vous faites référence à un type qui existe dans un assemblage WPF, mais ce type est dans un espace de nom CLR qui n’a pas été cartographié pour faire partie de l’espace de nom par défaut WPF XAML. La cartographie des espaces de noms CLR dans l’espace de nom XAML par défaut pour WPF est effectuée par définition dans les différents assemblages WPF (pour plus d’informations sur ce concept, voir [XAML Namespaces et Namespace Mapping pour WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)). Les espaces de noms CLR non cartographiés peuvent exister si cet espace de nom CLR est <xref:System.Windows.Threading>composé principalement de définitions de classe qui ne sont généralement pas destinées à XAML, telles que .

Pour plus d’informations sur la façon d’utiliser les préfixes et les espaces de noms XAML pour WPF, voir [XAML Namespaces et Namespace Mapping pour WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).

## <a name="see-also"></a>Voir aussi

- [x:Type, extension de balisage](xtype-markup-extension.md)
- [Types migrés de WPF vers System.Xaml](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
