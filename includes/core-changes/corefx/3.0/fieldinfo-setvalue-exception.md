---
ms.openlocfilehash: 9f8a790718fbb9d685bb8959808338dc1766bf2c
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021656"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a>FieldInfo. SetValue lève une exception pour les champs statiques, en initialisation seule

À compter de .NET Core 3,0, une exception est levée lorsque vous tentez de définir une valeur sur un <xref:System.Reflection.FieldAttributes.InitOnly> champ statique, <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>en appelant.

#### <a name="change-description"></a>Description de la modification

Dans .NET Framework et les versions de .NET Core antérieures à 3,0, vous pouviez définir la valeur d’un champ statique qui est constante après qu’il a été initialisé ([ReadOnly en C#](~/docs/csharp/language-reference/keywords/readonly.md)) <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>en appelant. Toutefois, la définition de ce type de champ de cette façon a entraîné un comportement imprévisible basé sur le Framework cible et les paramètres d’optimisation.

Dans .NET Core 3,0 et versions ultérieures, lorsque vous <xref:System.Reflection.FieldInfo.SetValue%2A> appelez sur un champ <xref:System.Reflection.FieldAttributes.InitOnly> statique, une <xref:System.FieldAccessException?displayProperty=nameWithType> exception est levée.

> [!TIP]
> Un <xref:System.Reflection.FieldAttributes.InitOnly> champ est un champ qui ne peut être défini qu’au moment où il est déclaré ou dans le constructeur pour la classe conteneur. En d’autres termes, elle est constante une fois qu’elle a été initialisée.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Initialisez les <xref:System.Reflection.FieldAttributes.InitOnly> champs statiques dans un constructeur statique. Cela s’applique à la fois aux types dynamiques et non dynamiques.

Vous pouvez également supprimer l' <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> attribut du champ, puis appeler. <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
