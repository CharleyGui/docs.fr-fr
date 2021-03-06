---
description: -Nullable (options du compilateur C#)
title: -Nullable (options du compilateur C#)
author: IEvangelist
ms.author: dapine
ms.date: 06/04/2020
f1_keywords:
- /nullable
helpviewer_keywords:
- nullable compiler option [C#]
- /nullable compiler option [C#]
- -nullable compiler option [C#]
ms.openlocfilehash: 68857d0cb4d0cd1177506e0b7ce897d2cfc3aa5b
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099222"
---
# <a name="-nullable-c-compiler-options"></a>-Nullable (options du compilateur C#)

L’option **-Nullable** vous permet de spécifier le contexte Nullable.

## <a name="syntax"></a>Syntaxe

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a>Arguments

`+` &#124; `-`  
Si `+` vous spécifiez, ou **-Nullable**, le compilateur active le contexte Nullable. `-`Si vous spécifiez, qui est en vigueur si vous ne spécifiez pas **-Nullable**, désactive le contexte Nullable.

`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`  
Spécifie l’option de contexte Nullable. Semblable à `+` ou `-` , pour activer et désactiver, mais permet une plus grande granularité de la spécificité du contexte Nullable. L' `enable` argument, qui est en effet le même que si vous spécifiez **-Nullable**, active le contexte Nullable. La spécification de `disable` désactive le contexte Nullable. Lorsque vous fournissez l' `warnings` argument, **-Nullable : Warnings**, le contexte d’avertissement Nullable est activé. Lors de la spécification de l' `annotations` argument, **-Nullable : annotations**, le contexte d’annotation Nullable est activé.

## <a name="remarks"></a>Notes

L’analyse de Flow permet de déduire la possibilité de valeur null des variables au sein du code exécutable. La possibilité de valeur null déduite d’une variable est indépendante de la possibilité de valeur null déclarée de la variable. Les appels de méthode sont analysés même lorsqu’ils sont omis de manière conditionnelle. Par exemple, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> en mode release.

L’appel de méthodes annotées avec les attributs suivants affecte également l’analyse du workflow :

- Conditions préalables simples : <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> et <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute>
- Conditions postérieures simples : <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> et <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute>
- Conditions de publication conditionnelles : <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> et <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute>
- <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (par exemple, `DoesNotReturnIf(false)` pour <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ) et <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- Conditions de publication des membres : <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> et <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])>

> [!IMPORTANT]
> Le contexte Nullable global ne s’applique pas aux fichiers de code générés. Indépendamment de ce paramètre, le contexte Nullable est *désactivé* pour tout fichier source marqué comme généré. Un fichier est marqué comme généré de quatre façons :
>
> 1. Dans le fichier. editorconfig, spécifiez `generated_code = true` dans une section qui s’applique à ce fichier.
> 1. Placez `<auto-generated>` ou `<auto-generated/>` dans un commentaire en haut du fichier. Il peut se trouver sur n’importe quelle ligne de ce commentaire, mais le bloc de commentaires doit être le premier élément du fichier.
> 1. Démarrer le nom de fichier avec *TemporaryGeneratedFile_*
> 1. Terminez le nom de fichier avec *. Designer.cs*, *. generated.cs*, *. g.cs* ou *. g.i.cs*.
>
> Les générateurs peuvent s’abonner à l’aide de la [`#nullable`](../preprocessor-directives/preprocessor-nullable.md) directive de préprocesseur.

### <a name="to-set-this-compiler-option-in-a-project"></a>Pour définir cette option du compilateur dans un projet

Modifiez le fichier *. csproj* pour ajouter la `<Nullable>` balise dans une `Project/PropertyGroup` hiérarchie :

```xml
<Project Sdk="...">

  <PropertyGroup>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

## <a name="see-also"></a>Voir aussi

- [Options du compilateur C#](./index.md)
- [`#nullable` directive de préprocesseur](../preprocessor-directives/preprocessor-nullable.md)
- [Types références Nullables](../../nullable-references.md)
