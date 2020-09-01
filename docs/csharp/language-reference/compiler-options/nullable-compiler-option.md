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
ms.openlocfilehash: f9c6c204d2563865f741c6ddb4644eb56f956c12
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125044"
---
# <a name="-nullable-c-compiler-options"></a>-Nullable (options du compilateur C#)

L’option **-Nullable** vous permet de spécifier le contexte Nullable souhaité.

## <a name="syntax"></a>Syntaxe

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a>Arguments

`+` &#124; `-`  
Si `+` vous spécifiez, ou uniquement **null**,, le compilateur active le contexte Nullable. `-`Si vous spécifiez, qui est en vigueur si vous ne spécifiez pas **-Nullable**, désactive le contexte Nullable.

`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`  
Spécifie l’option de contexte Nullable. Semblable à `+` ou `-` , pour activer et désactiver, mais permet une plus grande granularité de la spécificité du contexte Nullable. L' `enable` argument, qui est en effet le même que si vous spécifiez **-Nullable**, active le contexte Nullable. La spécification de `disable` désactive le contexte Nullable. Lorsque vous fournissez l' `warnings` argument, **-Nullable : Warnings**, le contexte d’avertissement Nullable est activé. Lors de la spécification de l' `annotations` argument, **-Nullable : annotations**, le contexte d’annotation Nullable est activé.

## <a name="remarks"></a>Remarques

L’analyse de Flow permet de déduire la possibilité de valeur null des variables au sein du code exécutable. La possibilité de valeur null déduite d’une variable est indépendante de la possibilité de valeur null déclarée de la variable. Les appels de méthode sont analysés même s’ils sont omis conditionnellement. Par exemple, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> en mode release.

L’appel de méthodes annotées avec les attributs suivants affecte également l’analyse du workflow :

- Conditions préalables simples : <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> et <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute>
- Conditions postérieures simples : <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> et <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute>
- Conditions de publication conditionnelles : <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> et <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute>
- <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (par exemple, `DoesNotReturnIf(false)` pour <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ) et <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- Conditions de publication des membres : <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> et <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])>

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
- [Types références Nullables](../../nullable-references.md)
