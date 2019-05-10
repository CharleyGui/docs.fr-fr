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
ms.openlocfilehash: 8f90f56a595fa175d5c48a929fc19ceb81ab0d63
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617104"
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier, directive
Modifie le comportement de compilation XAML lorsque `x:Class` est également fourni. Plus précisément, au lieu de la création d’un partiel `class` qui a un `Public` (la valeur par défaut), de niveau d’accès fourni `x:Class` est créé avec un `NotPublic` niveau d’accès. Ce comportement affecte le niveau d’accès pour la classe dans les assemblys générés.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|*NotPublic*|La chaîne exacte à passer pour spécifier <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> et <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varie selon le langage de programmation de code-behind que vous utilisez. Consultez la section Notes.|  
  
## <a name="dependencies"></a>Dépendances  
 [x : Class](x-class-directive.md) doit également être fourni dans le même élément, et cet élément doit être l’élément racine dans une page. Pour plus d’informations, consultez [ \[MS-XAML\] Section 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="remarks"></a>Notes  
 La valeur de `x:ClassModifier` dans les Services XAML .NET Framework, l’utilisation varie par langage de programmation. La chaîne à utiliser dépend de la façon dont chaque langage implémente son <xref:System.CodeDom.Compiler.CodeDomProvider> et les convertisseurs de type qu’il retourne pour définir les significations de <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> et <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, et si cette langue est sensible à la casse.  
  
- Pour c#, la chaîne à passer pour désigner <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> est `internal`.  
  
- Pour Microsoft Visual Basic .NET, la chaîne à passer pour désigner <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> est `Friend`.  
  
- Pour [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], qui prennent en charge compilation XAML n’existe aucune cible ; par conséquent, la valeur à passer n’est pas spécifiée.  
  
 Vous pouvez également spécifier <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` en c#, `Public` en Visual Basic) ; Toutefois, en spécifiant <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> est rarement car <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> est déjà le comportement par défaut.  
  
 Autres valeurs avec le code utilisateur équivalente-niveau d’accès restrictions, telles que `private` en c#, ne sont pas pertinentes pour `x:ClassModifier` , car les références de classe imbriquées ne sont pas pris en charge dans XAML et par conséquent, le <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modificateur a le même effet.  
  
## <a name="security-notes"></a>Notes de sécurité  
 Le niveau d’accès tel que déclaré dans `x:ClassModifier` est toujours soumis à l’interprétation par les infrastructures particulières et leurs fonctionnalités. WPF inclut des fonctions pour charger et instancier des types où `x:ClassModifier` est `internal`, si cette classe est référencée à partir d’une ressource WPF via une référence URI à en-tête pack. En raison de ce cas et potentiellement d’autres similaires implémentés par d’autres infrastructures, ne comptez pas exclusivement sur `x:ClassModifier` pour bloquer l’instanciation de toutes les tentatives.  
  
## <a name="see-also"></a>Voir aussi

- [x:Class, directive](x-class-directive.md)
- [Code-behind et XAML dans WPF](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:FieldModifier, directive](x-fieldmodifier-directive.md)
- [Sécurité (WPF)](../wpf/security-wpf.md)
- [Types migrés de WPF vers System.Xaml](types-migrated-from-wpf-to-system-xaml.md)
