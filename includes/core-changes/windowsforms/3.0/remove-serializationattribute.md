---
ms.openlocfilehash: d48ced9d0201a33f9149aba155ddd3d8bc04c93f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74643955"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a>SerializableAttribute supprimé de certains types de formulaires Windows

Le <xref:System.SerializableAttribute> a été supprimé de certaines classes de formulaires Windows qui n’ont pas de scénarios de sérialisation binaire connus.

#### <a name="change-description"></a>Description de la modification

Les types suivants sont <xref:System.SerializableAttribute> décorés avec le cadre en .NET, mais l’attribut a été supprimé dans .NET Core:

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

Historiquement, ce mécanisme de sérialisation a eu de graves problèmes de maintenance et de sécurité. Le `SerializableAttribute` maintien des types signifie que ces types doivent être testés pour les modifications de la sérialisation de la version à la version et les modifications potentiellement de sérialisation de cadre à cadre. Il est donc plus difficile de faire évoluer ces types et peut être coûteux à entretenir. Ces types n’ont pas de scénarios de sérialisation binaires connus, ce qui minimise l’impact de la suppression de l’attribut.

Pour plus d’informations, voir [la sérialisation binaire](~/docs/standard/serialization/binary-serialization.md).

#### <a name="version-introduced"></a>Version introduite

3.0 Aperçu 9

#### <a name="recommended-action"></a>Action recommandée

Mettez à jour tout code qui peut dépendre de ces types étant marqués comme sérialisables.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- None

<!--

### Affected APIs

- Not detectable via API analysis

-->
