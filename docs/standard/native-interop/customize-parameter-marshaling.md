---
title: Personnalisation du marshaling de paramètres - .NET
description: Découvrez comment personnaliser la façon dont .NET marshale vos paramètres en une représentation native.
ms.date: 01/18/2019
ms.openlocfilehash: 1999cad057875f15b283421f87f485c2e5ca2306
ms.sourcegitcommit: e7748001b1cee80ced691d8a76ca814c0b02dd9b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86374310"
---
# <a name="customizing-parameter-marshaling"></a>Personnalisation du marshaling de paramètres

Si le comportement de marshaling des paramètres par défaut du runtime .NET ne vous convient pas, vous pouvez utiliser l’attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> pour le personnaliser.

## <a name="customizing-string-parameters"></a>Personnaliser des paramètres de chaîne

.NET propose tout un éventail de formats pour le marshaling des chaînes. Ces méthodes sont divisées en deux sections distinctes : les chaînes de style C et les chaînes orientées Windows.

### <a name="c-style-strings"></a>Chaînes de style C

Chacun de ces formats transmet une chaîne se terminant par Null au code natif. Ils diffèrent par l’encodage de la chaîne native.

| Valeur `System.Runtime.InteropServices.UnmanagedType` | Encodage |
|------------------------------------------------------|----------|
| LPStr | ANSI |
| LPUTF8Str | UTF-8 |
| LPWStr | UTF-16 |
| LPTStr | UTF-16 |

Le format <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=nameWithType> est légèrement différent. Comme `LPWStr`, il marshale la chaîne en une chaîne de style C native encodée en UTF-16. Toutefois, la signature managée vous fait passer la chaîne en référence ; la signature native correspondante prend la chaîne en valeur. Cette distinction permet d’utiliser une API native qui prend une chaîne en valeur et la modifie sur place sans qu’il soit nécessaire d’utiliser de `StringBuilder`. Nous vous déconseillons d’utiliser manuellement ce format, dans la mesure où il risque de provoquer une confusion entre les signatures native et managée.

### <a name="windows-centric-string-formats"></a>Formats de chaînes orientées Windows

En interagissant avec des interfaces COM ou OLE, vous remarquerez sûrement que les fonctions natives prennent des chaînes comme arguments `BSTR`. Vous pouvez utiliser le type non managé <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> pour marshaler une chaîne comme `BSTR`.

Si vous communiquez avec des API WinRT, vous pouvez utiliser le format <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> pour marshaler une chaîne comme `HSTRING`.

## <a name="customizing-array-parameters"></a>Personnaliser des paramètres de tableau

.NET propose également plusieurs moyens de marshaler des paramètres de tableau. Si vous appelez une API qui accepte un tableau de style C, utilisez le type non managé <xref:System.Runtime.InteropServices.UnmanagedType.LPArray?displayProperty=nameWithType>. Si les valeurs du tableau exigent un marshaling personnalisé, vous pouvez pour cela utiliser le champ <xref:System.Runtime.InteropServices.MarshalAsAttribute.ArraySubType> sur l’attribut `[MarshalAs]`.

Si vous utilisez les API COM, vous devrez probablement marshaler vos paramètres de tableau comme `SAFEARRAY*`. Pour cela, vous pouvez utiliser le type non managé <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>. Le type par défaut des éléments de `SAFEARRAY` est présenté dans la table [Personnaliser des champs `object`](./customize-struct-marshaling.md#marshal-systemobject). Vous pouvez utiliser les champs <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> et <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> pour personnaliser précisément le type d’élément de `SAFEARRAY`.

## <a name="customizing-boolean-or-decimal-parameters"></a>Personnaliser des paramètres booléens ou décimaux

Pour plus d’informations sur le marshaling des paramètres booléens ou décimaux, consultez [Personnaliser le marshaling des structures](customize-struct-marshaling.md).

## <a name="customizing-object-parameters-windows-only"></a>Personnaliser des paramètres d’objet (Windows uniquement)

Sous Windows, le runtime .NET propose plusieurs moyens de marshaler des paramètres d’objet en code natif.

### <a name="marshaling-as-specific-com-interfaces"></a>Marshaling comme interfaces COM spécifiques

Si votre API accepte un pointeur vers un objet COM, vous pouvez utiliser l’un des formats `UnmanagedType` suivants sur un paramètre de type `object` pour indiquer à .NET de marshaler comme ces interfaces spécifiques :

- `IUnknown`
- `IDispatch`
- `IInspectable`

De plus, si votre type est marqué `[ComVisible(true)]` ou que vous marshalez le type `object`, vous pouvez utiliser le format <xref:System.Runtime.InteropServices.UnmanagedType.Interface?displayProperty=nameWithType> pour marshaler votre objet comme wrapper appelable COM pour la vue COM de votre type.

### <a name="marshaling-to-a-variant"></a>Marshaling vers un `VARIANT`

Si votre API native accepte une `VARIANT` Win32, vous pouvez utiliser le format <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> sur votre `object` paramètre pour marshaler vos objets comme `VARIANT`. Pour connaître les correspondances entre les types .NET et les types `VARIANT`, voir la documentation [Personnaliser les champs `object`](customize-struct-marshaling.md#marshal-systemobject).

### <a name="custom-marshalers"></a>Marshaleurs personnalisés

Si vous voulez projeter une interface COM native dans un autre type managé, vous pouvez utiliser le format `UnmanagedType.CustomMarshaler` et une implémentation <xref:System.Runtime.InteropServices.ICustomMarshaler> pour fournir votre propre code de marshaling personnalisé.
