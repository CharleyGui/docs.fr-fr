---
title: x:FieldModifier, directive
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 4e67a6dac49b8d6a7d316526f99a1519b08fd68b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554473"
---
# <a name="xfieldmodifier-directive"></a>x:FieldModifier, directive
Modifie le comportement de compilation XAML afin que les champs pour les références d’objets nommés soient définis avec <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> l’accès au lieu du <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> comportement par défaut.

## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML

```xaml
<object x:FieldModifier="Public".../>
```

## <a name="xaml-values"></a>Valeurs XAML

|||
|-|-|
|*Public*|La chaîne exacte que vous transmettez pour spécifier <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> et <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varie selon le langage de programmation code-behind utilisé. Consultez la section Notes.|

## <a name="dependencies"></a>Les dépendances

 Si une production XAML utilise `x:FieldModifier` n’importe où, l’élément racine de cette production XAML doit déclarer une [directive x :Class](xclass-directive.md).

## <a name="remarks"></a>Notes

`x:FieldModifier` ne s’applique pas à la déclaration du niveau d’accès général d’une classe ou de ses membres. Elle s’applique uniquement au comportement de traitement XAML lorsqu’un objet XAML particulier qui fait partie d’une production XAML est traité, et devient un objet potentiellement accessible dans le graphique d’objet d’une application. Par défaut, la référence de champ pour un tel objet est gardée privée, ce qui empêche les utilisateurs du contrôle de modifier directement le graphique d’objet. Au lieu de cela, les consommateurs de contrôle sont censés modifier le graphique d’objet à l’aide de modèles standard qui sont activés par les modèles de programmation, par exemple en obtenant la racine de la disposition, les collections d’éléments enfants, les propriétés publiques dédiées, et ainsi de suite.

La valeur de l' `x:FieldModifier` attribut varie en fonction du langage de programmation, et son objectif peut varier dans des frameworks spécifiques. La chaîne à utiliser dépend de la façon dont chaque langage implémente son <xref:System.CodeDom.Compiler.CodeDomProvider> et les convertisseurs de type qu’elle retourne pour définir les significations pour <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> et <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> , et si cette langue respecte la casse.

- Pour C#, la chaîne à passer à Designate <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> est `public` .

- Pour Microsoft Visual Basic .NET, la chaîne à transmettre à Designate <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> est `Public` .

- Pour C++/CLI, aucune cible n’existe actuellement pour XAML. par conséquent, la chaîne à passer est non définie.

Vous pouvez également spécifier <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> ( `internal` en C#, `Friend` dans Visual Basic), mais <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> la spécification est inhabituelle, car `NotPublic` le comportement est déjà la valeur par défaut.

<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> est le comportement par défaut, car il est peu fréquent que le code en dehors de l’assembly qui a compilé le XAML ait besoin d’accéder à un élément créé par XAML. L’architecture de la sécurité WPF et le comportement de compilation XAML ne déclarent pas les champs qui stockent des instances d’élément comme étant publics, sauf si vous définissez spécifiquement le `x:FieldModifier` pour autoriser l’accès public.

`x:FieldModifier` s’applique uniquement aux éléments avec une [directive x :Name](xname-directive.md) , car ce nom est utilisé pour référencer le champ une fois qu’il est public.

Par défaut, la classe partielle pour l’élément racine est publique ; Toutefois, vous pouvez le rendre non public à l’aide de la [directive x :ClassModifier](xclassmodifier-directive.md). La [directive x :ClassModifier](xclassmodifier-directive.md) affecte également le niveau d’accès de l’instance de la classe d’élément racine. Vous pouvez placer `x:Name` et `x:FieldModifier` sur l’élément racine, mais cela crée uniquement une copie de champ public de l’élément racine, avec le niveau d’accès de classe d’élément racine true toujours contrôlé par [la directive x :ClassModifier](xclassmodifier-directive.md).

## <a name="see-also"></a>Voir aussi

- [XAML et classes personnalisées pour WPF](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf)
- [Code-behind et XAML dans WPF](/dotnet/desktop/wpf/advanced/code-behind-and-xaml-in-wpf)
- [x:Name, directive](xname-directive.md)
- [Génération d’une application WPF (WPF)](/dotnet/desktop/wpf/app-development/building-a-wpf-application-wpf)
- [x:ClassModifier, directive](xclassmodifier-directive.md)
