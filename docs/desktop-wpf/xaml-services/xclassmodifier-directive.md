---
title: x:ClassModifier, directive
ms.date: 03/30/2017
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
ms.openlocfilehash: 436204774c2d59b43a77865c666aed702f7681db
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072031"
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier, directive
Modifie le comportement de `x:Class` compilation XAML lorsqu’il est également fourni. Plus précisément, au `class` lieu de `Public` créer une partie qui `x:Class` a un `NotPublic` niveau d’accès (la valeur par défaut), le fourni est créé avec un niveau d’accès. Ce comportement affecte le niveau d’accès pour la classe dans les assemblages générés.

## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML

```xaml
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">
   ...
</object>
```

## <a name="xaml-values"></a>Valeurs XAML

|||
|-|-|
|*NonPublic*|La chaîne exacte à <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> passer <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> pour spécifier par rapport varie, selon le langage de programmation codé-derrière que vous utilisez. Consultez la section Notes.|

## <a name="dependencies"></a>Les dépendances

[x : La classe](xclass-directive.md) doit également être fournie sur le même élément, et cet élément doit être l’élément racine d’une page. Pour plus d’informations, voir [ \[MS-XAML\] Section 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

## <a name="remarks"></a>Notes

La valeur `x:ClassModifier` de l’utilisation de services .NET XAML varie selon le langage de programmation. La chaîne à utiliser dépend de <xref:System.CodeDom.Compiler.CodeDomProvider> la façon dont chaque langue implémente <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>son et le type de convertisseurs qu’elle retourne pour définir les significations et, <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> et si cette langue est sensible aux cas.

- Pour C, la corde à <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> passer `internal`pour désigner est .

- Pour Microsoft Visual Basic .NET, la <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> chaîne `Friend`à passer pour désigner est .

- Pour le CMD/CLI, il n’existe aucune cible qui appuie la compilation de XAML; par conséquent, la valeur de passage n’est pas précisée.

Vous pouvez <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> également`public` spécifier (en C, `Public` dans Visual Basic); cependant, la <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> spécifier est <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> rarement fait parce que c’est déjà le comportement par défaut.

D’autres valeurs assorties de restrictions `private` équivalentes au niveau du `x:ClassModifier` code utilisateur, comme dans le C, ne <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> sont pas pertinentes parce que les références de classe imbriquées ne sont pas prises en charge dans XAML, et par conséquent, le modificateur a le même effet.

## <a name="security-notes"></a>Remarques relatives à la sécurité

Le niveau d’accès tel qu’il est déclaré est `x:ClassModifier` toujours soumis à l’interprétation par des cadres particuliers et leurs capacités. WPF inclut les capacités de chargement et d’instantanéis types où `x:ClassModifier` est, `internal`si cette classe est référencée à partir d’une ressource WPF par le biais d’une référence URI pack. En conséquence de cette affaire et potentiellement d’autres comme elle `x:ClassModifier` mise en œuvre par d’autres cadres, ne comptent pas exclusivement sur pour bloquer toutes les tentatives d’instantanéisation possibles.

## <a name="see-also"></a>Voir aussi

- [x:Class, directive](xclass-directive.md)
- [Code-behind et XAML dans WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:FieldModifier, directive](xfieldmodifier-directive.md)
- [Sécurité (WPF)](../../framework/wpf/security-wpf.md)
- [Types migrés de WPF vers System.Xaml](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
