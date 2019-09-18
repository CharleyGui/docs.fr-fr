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
ms.openlocfilehash: 5daff0567c1b1415fe994f6e39b4079cb2ab7346
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053820"
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier, directive
Modifie le comportement de compilation XAML `x:Class` lorsque est également fourni. Plus précisément, au lieu de créer `class` un partiel ayant `Public` un niveau d’accès (valeur par défaut) `x:Class` , le fourni est `NotPublic` créé avec un niveau d’accès. Ce comportement affecte le niveau d’accès de la classe dans les assemblys générés.  
  
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
  
## <a name="dependencies"></a>Dépendances  
 [x :Class](x-class-directive.md) doit également être fourni sur le même élément, et cet élément doit être l’élément racine d’une page. Pour plus d’informations, consultez [ \[la section\] MS-XAML 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="remarks"></a>Notes  
 La valeur de `x:ClassModifier` dans .NET Framework l’utilisation des services XAML varie en fonction du langage de programmation. La chaîne à utiliser dépend de la façon dont chaque langage implémente son <xref:System.CodeDom.Compiler.CodeDomProvider> et les convertisseurs de type qu’elle retourne pour définir les significations pour <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> et <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, et si cette langue respecte la casse.  
  
- Pour C#, la chaîne à passer à Designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> est `internal`.  
  
- Pour Microsoft Visual Basic .net, la chaîne à transmettre à Designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> est `Friend`.  
  
- Pour C++/CLI, il n’existe aucune cible prenant en charge la compilation XAML ; par conséquent, la valeur à passer n’est pas spécifiée.  
  
 Vous pouvez également spécifier <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` dans C#, `Public` dans Visual Basic); Toutefois, la <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> spécification de est rarement effectuée <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> , car est déjà le comportement par défaut.  
  
 D’autres valeurs avec des restrictions de niveau d’accès du code utilisateur `private` équivalentes, comme dans C#, `x:ClassModifier` ne sont pas pertinentes pour, car les références de classe imbriquée ne sont <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> pas prises en charge en XAML, et par conséquent, le modificateur a le même effet .  
  
## <a name="security-notes"></a>Notes de sécurité  
 Le niveau d’accès tel qu' `x:ClassModifier` il est déclaré dans est toujours soumis à une interprétation par des frameworks particuliers et leurs fonctionnalités. WPF offre des fonctionnalités permettant de charger et d' `x:ClassModifier` instancier des types où est `internal`, si cette classe est référencée à partir d’une ressource WPF par le biais d’une référence URI à en-tête pack. À la suite de ce cas et, éventuellement, d’autres personnes comme celles implémentées par d’autres infrastructures, `x:ClassModifier` ne comptez pas exclusivement sur pour bloquer toutes les tentatives d’instanciation possibles.  
  
## <a name="see-also"></a>Voir aussi

- [x:Class, directive](x-class-directive.md)
- [Code-behind et XAML dans WPF](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:FieldModifier, directive](x-fieldmodifier-directive.md)
- [Sécurité (WPF)](../wpf/security-wpf.md)
- [Types migrés de WPF vers System.Xaml](types-migrated-from-wpf-to-system-xaml.md)
