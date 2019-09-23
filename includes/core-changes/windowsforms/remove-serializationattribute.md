---
ms.openlocfilehash: e9d76d5907e7d700fc57117ccb43f8c430c615b0
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181838"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a>SerializableAttribute supprimé de certains types de Windows Forms

<xref:System.SerializableAttribute> A été supprimé de certains Windows Forms des classes qui n’ont aucun scénario de sérialisation binaire connu.

#### <a name="change-description"></a>Modifier la description

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

Pour plus d'informations, consultez <https://docs.microsoft.com/en-us/dotnet/standard/serialization/binary-serialization>.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 9

#### <a name="recommended-action"></a>Action recommandée

Mettez à jour le code qui peut dépendre de ces types qui sont marqués comme sérialisables.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- Aucun.

<!-- 

### Affected APIs

- Not detectable via API analysis

-->