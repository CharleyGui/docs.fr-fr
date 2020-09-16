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
ms.openlocfilehash: 73732a06029cca3a4c6c6d82762d5263c5b8c955
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544815"
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier, directive
Modifie le comportement de compilation XAML lorsque `x:Class` est également fourni. Plus précisément, au lieu de créer un partiel `class` ayant un `Public` niveau d’accès (valeur par défaut), le fourni `x:Class` est créé avec un `NotPublic` niveau d’accès. Ce comportement affecte le niveau d’accès de la classe dans les assemblys générés.

## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML

```xaml
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">
   ...
</object>
```

## <a name="xaml-values"></a>Valeurs XAML

|||
|-|-|
|*NotPublic*|La chaîne exacte à passer pour spécifier <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> et <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varie selon le langage de programmation code-behind que vous utilisez. Consultez la section Notes.|

## <a name="dependencies"></a>Les dépendances

[x :Class](xclass-directive.md) doit également être fourni sur le même élément, et cet élément doit être l’élément racine d’une page. Pour plus d’informations, consultez la [ \[ section MS-XAML \] 4.3.1.8](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

## <a name="remarks"></a>Notes

La valeur de `x:ClassModifier` dans l’utilisation des services XAML .net varie en fonction du langage de programmation. La chaîne à utiliser dépend de la façon dont chaque langage implémente son <xref:System.CodeDom.Compiler.CodeDomProvider> et les convertisseurs de type qu’elle retourne pour définir les significations pour <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> et <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> , et si cette langue respecte la casse.

- Pour C#, la chaîne à passer à Designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> est `internal` .

- Pour Microsoft Visual Basic .NET, la chaîne à transmettre à Designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> est `Friend` .

- Pour C++/CLI, il n’existe aucune cible prenant en charge la compilation XAML ; par conséquent, la valeur à passer n’est pas spécifiée.

Vous pouvez également spécifier <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> ( `public` en C#, `Public` dans Visual Basic); Toutefois, la spécification de <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> est rarement effectuée, car <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> est déjà le comportement par défaut.

D’autres valeurs avec des restrictions de niveau d’accès de code utilisateur équivalentes, comme `private` en C#, ne sont pas pertinentes pour, `x:ClassModifier` car les références de classe imbriquée ne sont pas prises en charge en XAML, et par conséquent, le <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modificateur a le même effet.

## <a name="security-notes"></a>Remarques relatives à la sécurité

Le niveau d’accès tel qu’il est déclaré dans `x:ClassModifier` est toujours soumis à une interprétation par des frameworks particuliers et leurs fonctionnalités. WPF offre des fonctionnalités permettant de charger et d’instancier des types où `x:ClassModifier` est `internal` , si cette classe est référencée à partir d’une ressource WPF par le biais d’une référence URI à en-tête pack. À la suite de ce cas et, éventuellement, d’autres personnes comme celles implémentées par d’autres infrastructures, ne comptez pas exclusivement sur `x:ClassModifier` pour bloquer toutes les tentatives d’instanciation possibles.

## <a name="see-also"></a>Voir aussi

- [x:Class, directive](xclass-directive.md)
- [Code-behind et XAML dans WPF](/dotnet/desktop/wpf/advanced/code-behind-and-xaml-in-wpf)
- [x:FieldModifier, directive](xfieldmodifier-directive.md)
- [Sécurité (WPF)](/dotnet/desktop/wpf/security-wpf)
- [Types migrés de WPF vers System.Xaml](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
