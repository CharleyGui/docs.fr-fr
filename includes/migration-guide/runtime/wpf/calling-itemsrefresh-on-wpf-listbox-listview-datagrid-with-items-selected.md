---
ms.openlocfilehash: 972601874d80d82ebae8b79779acfed82e5570cb
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497536"
---
### <a name="calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a>L’appel d’Items.Refresh dans un contrôle WPF ListBox, ListView ou DataGrid contenant des éléments sélectionnés peut provoquer l’apparition d’éléments en double.

#### <a name="details"></a>Détails

Dans le .NET Framework 4.5, si vous appelez ListBox.Items.Refresh à partir du code alors que des éléments sont sélectionnés dans une <xref:System.Windows.Controls.ListBox?displayProperty=fullName>, les éléments en question peuvent apparaître deux fois dans la liste. Un problème similaire se produit avec <xref:System.Windows.Controls.ListView?displayProperty=fullName> et <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>. Ce problème a été résolu dans le .NET Framework 4.6.

#### <a name="suggestion"></a>Suggestion

Pour contourner ce problème, vous pouvez désélectionner programmatiquement les éléments avant d’appeler <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=fullName>, puis les resélectionner une fois l’appel effectué. Étant donné que ce problème a été résolu dans le .NET Framework 4.6, vous pouvez également mettre à niveau votre version du .NET Framework.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Data.CollectionView.Refresh`

-->
