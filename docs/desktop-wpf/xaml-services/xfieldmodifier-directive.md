---
title: x:FieldModifier, directive
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 3e104b4c464d545e048f29901701c1c3dbb68229
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071527"
---
# <a name="xfieldmodifier-directive"></a>x:FieldModifier, directive
Modifie le comportement de compilation XAML de sorte <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> que les <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> champs pour les références d’objets nommés sont définis avec l’accès au lieu du comportement par défaut.

## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML

```xaml
<object x:FieldModifier="Public".../>
```

## <a name="xaml-values"></a>Valeurs XAML

|||
|-|-|
|*Public*|La chaîne exacte que <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> vous <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> passez pour spécifier par rapport varie, selon le langage de programmation codé-derrière qui est utilisé. Consultez la section Notes.|

## <a name="dependencies"></a>Les dépendances

 Si une production XAML utilise `x:FieldModifier` n’importe où, l’élément racine de cette production XAML doit déclarer une directive [x:Class](xclass-directive.md).

## <a name="remarks"></a>Notes

`x:FieldModifier`n’est pas pertinent pour déclarer le niveau d’accès général d’une classe ou de ses membres. Il n’est pertinent que pour le comportement de traitement XAML lorsqu’un objet XAML particulier qui fait partie d’une production XAML est traité, et devient un objet qui est potentiellement accessible dans le graphique d’objet d’une application. Par défaut, la référence de champ pour un tel objet est gardée privée, ce qui empêche les consommateurs de contrôler de modifier directement le graphique de l’objet. Au lieu de cela, les consommateurs de contrôle sont censés modifier le graphique de l’objet en utilisant des modèles standard qui sont activés par des modèles de programmation, tels que par l’obtention de la racine de mise en page, les collections d’éléments pour enfants, les propriétés publiques dédiées, et ainsi de suite.

La valeur `x:FieldModifier` de l’attribut varie selon le langage de programmation, et son but peut varier dans des cadres spécifiques. La chaîne à utiliser dépend de <xref:System.CodeDom.Compiler.CodeDomProvider> la façon dont chaque langue implémente <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>son et le type de convertisseurs qu’elle retourne pour définir les significations et, <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> et si cette langue est sensible aux cas.

- Pour C, la corde à <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> passer `public`pour désigner est .

- Pour Microsoft Visual Basic .NET, la <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> chaîne `Public`à passer pour désigner est .

- Pour le CMD/CLI, il n’existe actuellement aucune cible pour XAML; par conséquent, la ficelle à passer est indéfinie.

Vous pouvez <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> également`internal` spécifier (en `Friend` C, <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> dans `NotPublic` Visual Basic) mais spécifier est inhabituel parce que le comportement est déjà la valeur par défaut.

<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>est le comportement par défaut parce qu’il est peu fréquent que le code en dehors de l’assemblage qui a compilé le XAML a besoin d’accéder à un élément créé par XAML. L’architecture de sécurité WPF ainsi que le comportement de compilation XAML `x:FieldModifier` ne déclareront pas les champs qui stockent les instances d’éléments comme publics, sauf si vous définissez spécifiquement le pour permettre l’accès du public.

`x:FieldModifier`n’est pertinent que pour les éléments avec une [directive x:Name](xname-directive.md) parce que ce nom est utilisé pour faire référence au champ après qu’il soit public.

Par défaut, la classe partielle de l’élément racine est publique; cependant, vous pouvez le rendre non public en utilisant la [directive x:ClassModifier](xclassmodifier-directive.md). La [directive x:ClassModifier](xclassmodifier-directive.md) affecte également le niveau d’accès de l’instance de la classe des éléments racinaires. Vous pouvez `x:Name` mettre `x:FieldModifier` à la fois et sur l’élément racine, mais cela ne fait qu’une copie publique de champ de l’élément racine, avec le véritable niveau d’accès de classe d’élément racine encore contrôlé par [x:ClassModifier directive](xclassmodifier-directive.md).

## <a name="see-also"></a>Voir aussi

- [XAML et classes personnalisées pour WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [Code-behind et XAML dans WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:Name, directive](xname-directive.md)
- [Construction d’une demande WPF (WPF)](../../framework/wpf/app-development/building-a-wpf-application-wpf.md)
- [x:ClassModifier, directive](xclassmodifier-directive.md)
