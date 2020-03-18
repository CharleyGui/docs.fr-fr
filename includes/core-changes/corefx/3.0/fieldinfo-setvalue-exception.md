---
ms.openlocfilehash: dc733ee32184db5af59bb06e294cd73765977581
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449551"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a>FieldInfo.SetValue jette l’exception pour les champs statiques et init-seulement

À partir de .NET Core 3.0, une exception est lancée <xref:System.Reflection.FieldAttributes.InitOnly> lorsque vous <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>essayez de définir une valeur sur un terrain statique en appelant .

#### <a name="change-description"></a>Description de la modification

Dans .NET Framework et les versions de .NET Core avant 3.0, vous pouvez définir la valeur d’un champ statique <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>qui est constant après qu’il est initialisé ( lire dans C ' )[en](~/docs/csharp/language-reference/keywords/readonly.md)appelant . Cependant, la définition d’un tel champ de cette façon a entraîné un comportement imprévisible basé sur le cadre cible et les paramètres d’optimisation.

Dans .NET Core 3.0 et les <xref:System.Reflection.FieldInfo.SetValue%2A> versions ultérieures, lorsque vous faites appel à un champ statique, <xref:System.Reflection.FieldAttributes.InitOnly> une <xref:System.FieldAccessException?displayProperty=nameWithType> exception est lancée.

> [!TIP]
> Un <xref:System.Reflection.FieldAttributes.InitOnly> champ est celui qui ne peut être fixé qu’au moment où il est déclaré ou dans le constructeur pour la classe contenant. En d’autres termes, il est constant après qu’il soit initialisé.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Initialiser les <xref:System.Reflection.FieldAttributes.InitOnly> champs statiques dans un constructeur statique. Cela s’applique à la fois aux types dynamiques et non dynamiques.

Alternativement, vous pouvez <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> supprimer l’attribut du <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>champ, puis appeler .

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
