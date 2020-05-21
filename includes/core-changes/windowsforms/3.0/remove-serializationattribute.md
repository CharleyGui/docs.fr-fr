---
ms.openlocfilehash: b35e99b1516c3236d07153cf0b69dae55a4bff7d
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721468"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a>SerializableAttribute supprimé de certains types de Windows Forms

<xref:System.SerializableAttribute>A été supprimé de certains Windows Forms des classes qui n’ont aucun scénario de sérialisation binaire connu.

#### <a name="change-description"></a>Description de la modification

Les types suivants sont décorés avec le <xref:System.SerializableAttribute> dans .NET Framework, mais l’attribut a été supprimé dans .net Core :

- `System.InvariantComparer`
- <xref:System.ComponentModel.Design.ExceptionCollection?displayProperty=nameWithType>
- <xref:System.ComponentModel.Design.Serialization.CodeDomSerializerException?displayProperty=nameWithType>
- `System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService.CodeDomSerializationStore`
- <xref:System.Drawing.Design.ToolboxItem?displayProperty=nameWithType>
- `System.Resources.ResXNullRef`
- `System.Resources.ResXDataNode`
- `System.Resources.ResXFileRef`
- <xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>
- `System.Windows.Forms.NativeMethods.MSOCRINFOSTRUCT`
- `System.Windows.Forms.NativeMethods.MSG`

Historiquement, ce mécanisme de sérialisation avait des préoccupations graves en matière de maintenance et de sécurité. La gestion `SerializableAttribute` de sur les types signifie que ces types doivent être testés pour les modifications de sérialisation de version à version et les modifications potentielles de sérialisation de Framework à Framework. Cela complique l’évolution de ces types et peut s’avérer coûteux à gérer. Ces types n’ont aucun scénario de sérialisation binaire connu, ce qui réduit l’impact de la suppression de l’attribut.

Pour plus d’informations, consultez [sérialisation binaire](~/docs/standard/serialization/binary-serialization.md).

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 9

#### <a name="recommended-action"></a>Action recommandée

Mettez à jour le code qui peut dépendre de ces types qui sont marqués comme sérialisables.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- Aucune

<!--

#### Affected APIs

- Not detectable via API analysis

-->
