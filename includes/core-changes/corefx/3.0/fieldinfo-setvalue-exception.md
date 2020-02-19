---
ms.openlocfilehash: dc733ee32184db5af59bb06e294cd73765977581
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449551"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a>FieldInfo. SetValue lève une exception pour les champs statiques, en initialisation seule

À compter de .NET Core 3,0, une exception est levée lorsque vous tentez de définir une valeur sur un champ statique, <xref:System.Reflection.FieldAttributes.InitOnly> en appelant <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.

#### <a name="change-description"></a>Modifier la description

Dans .NET Framework et les versions de .net Core antérieures à 3,0, vous pouviez définir la valeur d’un champ statique qui est constant après son initialisation ([ReadOnly en C# ](~/docs/csharp/language-reference/keywords/readonly.md)) en appelant <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>. Toutefois, la définition de ce type de champ de cette façon a entraîné un comportement imprévisible basé sur le Framework cible et les paramètres d’optimisation.

Dans .NET Core 3,0 et versions ultérieures, lorsque vous appelez <xref:System.Reflection.FieldInfo.SetValue%2A> sur un champ statique <xref:System.Reflection.FieldAttributes.InitOnly>, une exception <xref:System.FieldAccessException?displayProperty=nameWithType> est levée.

> [!TIP]
> Un champ <xref:System.Reflection.FieldAttributes.InitOnly> est un champ qui ne peut être défini qu’au moment où il est déclaré ou dans le constructeur pour la classe conteneur. En d’autres termes, elle est constante une fois qu’elle a été initialisée.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Initialisez les champs statiques <xref:System.Reflection.FieldAttributes.InitOnly> dans un constructeur statique. Cela s’applique à la fois aux types dynamiques et non dynamiques.

Vous pouvez également supprimer l’attribut <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> du champ, puis appeler <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>.

#### <a name="category"></a>Category

CoreFx

#### <a name="affected-apis"></a>API affectées

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
