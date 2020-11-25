---
ms.openlocfilehash: 02c9305a36f47dfaf0b1fa8d19b07cd2d34badae
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032021"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a>FieldInfo. SetValue lève une exception pour les champs statiques, en initialisation seule

À compter de .NET Core 3,0, une exception est levée lorsque vous tentez de définir une valeur sur un <xref:System.Reflection.FieldAttributes.InitOnly> champ statique, en appelant <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName> .

#### <a name="change-description"></a>Description de la modification

Dans .NET Framework et les versions de .NET Core antérieures à 3,0, vous pouviez définir la valeur d’un champ statique qui est constante après qu’il a été initialisé ([ReadOnly en C#](~/docs/csharp/language-reference/keywords/readonly.md)) en appelant <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName> . Toutefois, la définition de ce type de champ de cette façon a entraîné un comportement imprévisible basé sur le Framework cible et les paramètres d’optimisation.

Dans .NET Core 3,0 et versions ultérieures, lorsque vous appelez <xref:System.Reflection.FieldInfo.SetValue%2A> sur un champ statique, <xref:System.Reflection.FieldAttributes.InitOnly> une <xref:System.FieldAccessException?displayProperty=nameWithType> exception est levée.

> [!TIP]
> Un <xref:System.Reflection.FieldAttributes.InitOnly> champ est un champ qui ne peut être défini qu’au moment où il est déclaré ou dans le constructeur pour la classe conteneur. En d’autres termes, elle est constante une fois qu’elle a été initialisée.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Initialisez les champs statiques <xref:System.Reflection.FieldAttributes.InitOnly> dans un constructeur statique. Cela s’applique à la fois aux types dynamiques et non dynamiques.

Vous pouvez également supprimer l' <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> attribut du champ, puis appeler <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType> .

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
