---
ms.openlocfilehash: d48ced9d0201a33f9149aba155ddd3d8bc04c93f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74643955"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a>SerializableAttribute supprimé de certains types de Windows Forms

<xref:System.SerializableAttribute> A été supprimé de certains Windows Forms des classes qui n’ont aucun scénario de sérialisation binaire connu.

#### <a name="change-description"></a>Description de la modification

Les types suivants sont décorés avec <xref:System.SerializableAttribute> le dans .NET Framework, mais l’attribut a été supprimé dans .net Core :

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

Historiquement, ce mécanisme de sérialisation avait des préoccupations graves en matière de maintenance et de sécurité. La `SerializableAttribute` gestion de sur les types signifie que ces types doivent être testés pour les modifications de sérialisation de version à version et les modifications potentielles de sérialisation de Framework à Framework. Cela complique l’évolution de ces types et peut s’avérer coûteux à gérer. Ces types n’ont aucun scénario de sérialisation binaire connu, ce qui réduit l’impact de la suppression de l’attribut.

Pour plus d’informations, consultez [sérialisation binaire](~/docs/standard/serialization/binary-serialization.md).

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 9

#### <a name="recommended-action"></a>Action recommandée

Mettez à jour le code qui peut dépendre de ces types qui sont marqués comme sérialisables.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- Aucun

<!--

### Affected APIs

- Not detectable via API analysis

-->
