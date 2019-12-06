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
ms.openlocfilehash: a24277a4d5fbc4870157b6c8ba00ba71ba61e656
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837231"
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier, directive
Modifie le comportement de compilation XAML lorsque `x:Class` est également fourni. Plus précisément, au lieu de créer une `class` partielle ayant un niveau d’accès `Public` (valeur par défaut), la `x:Class` fournie est créée avec un niveau d’accès `NotPublic`. Ce comportement affecte le niveau d’accès de la classe dans les assemblys générés.  
  
## <a name="xaml-attribute-usage"></a>Utilisation des attributs XAML  
  
```xaml  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|*NotPublic*|La chaîne exacte à passer à spécifiez <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> contre <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varie selon le langage de programmation code-behind que vous utilisez. Consultez la section Notes.|  
  
## <a name="dependencies"></a>Dépendances  
 [x :Class](x-class-directive.md) doit également être fourni sur le même élément, et cet élément doit être l’élément racine d’une page. Pour plus d’informations, consultez [\[MS-XAML\] section 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
## <a name="remarks"></a>Notes  
 La valeur de `x:ClassModifier` dans .NET Framework l’utilisation des services XAML varie en fonction du langage de programmation. La chaîne à utiliser dépend de la façon dont chaque langage implémente son <xref:System.CodeDom.Compiler.CodeDomProvider> et des convertisseurs de type qu’elle retourne pour définir les significations pour <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> et <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, et si cette langue respecte la casse.  
  
- Pour C#, la chaîne à passer à la <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> de désignation est `internal`.  
  
- Pour Microsoft Visual Basic .NET, la chaîne à transmettre à la <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> Designate est `Friend`.  
  
- Pour C++/CLI, il n’existe aucune cible prenant en charge la compilation XAML ; par conséquent, la valeur à passer n’est pas spécifiée.  
  
 Vous pouvez également spécifier <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` dans C#, `Public` dans Visual Basic). Toutefois, la spécification de <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> est rarement effectuée, car <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> est déjà le comportement par défaut.  
  
 Les autres valeurs avec des restrictions de niveau d’accès de code utilisateur équivalentes C#, telles que `private` dans, ne sont pas pertinentes pour les `x:ClassModifier`, car les références de classe imbriquée ne sont pas prises en charge en XAML, et par conséquent, le modificateur <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> a le même effet.  
  
## <a name="security-notes"></a>Remarques relatives à la sécurité  
 Le niveau d’accès tel qu’il est déclaré dans `x:ClassModifier` est toujours soumis à une interprétation par des frameworks particuliers et leurs fonctionnalités. WPF comprend des fonctionnalités permettant de charger et d’instancier des types où `x:ClassModifier` est `internal`, si cette classe est référencée à partir d’une ressource WPF par le biais d’une référence URI à en-tête pack. À la suite de ce cas et, éventuellement, d’autres personnes comme celles implémentées par d’autres infrastructures, ne comptez pas exclusivement sur les `x:ClassModifier` pour bloquer toutes les tentatives d’instanciation possibles.  
  
## <a name="see-also"></a>Voir aussi

- [x:Class, directive](x-class-directive.md)
- [Code-behind et XAML dans WPF](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:FieldModifier, directive](x-fieldmodifier-directive.md)
- [Sécurité (WPF)](../wpf/security-wpf.md)
- [Types migrés de WPF vers System.Xaml](types-migrated-from-wpf-to-system-xaml.md)
