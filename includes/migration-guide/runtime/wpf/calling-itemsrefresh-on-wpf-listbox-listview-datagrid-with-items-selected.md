---
ms.openlocfilehash: 22c67c687f5581c181acc4aeab8910c4467fd424
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858837"
---
### <a name="calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a>L’appel d’Items.Refresh dans un contrôle WPF ListBox, ListView ou DataGrid contenant des éléments sélectionnés peut provoquer l’apparition d’éléments en double.

|   |   |
|---|---|
|Détails|Dans le .NET Framework 4.5, si vous appelez ListBox.Items.Refresh à partir du code alors que des éléments sont sélectionnés dans une <xref:System.Windows.Controls.ListBox?displayProperty=name>, les éléments en question peuvent apparaître deux fois dans la liste. Un problème similaire se produit avec <xref:System.Windows.Controls.ListView?displayProperty=name> et <xref:System.Windows.Controls.DataGrid?displayProperty=name>. Ce problème a été résolu dans le .NET Framework 4.6.|
|Suggestion|Ce problème peut être contourné en désélectionnant les éléments par programmation avant d’appeler <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=name>, puis en les resélectionnant une fois l’appel terminé. Étant donné que ce problème a été résolu dans le .NET Framework 4.6, vous pouvez également mettre à niveau votre version du .NET Framework.|
|Portée|Mineur|
|Version|4.5|
|Type|Runtime|
|API affectées|<ul><li><xref:System.Windows.Data.CollectionView.Refresh?displayProperty=nameWithType></li></ul>|

