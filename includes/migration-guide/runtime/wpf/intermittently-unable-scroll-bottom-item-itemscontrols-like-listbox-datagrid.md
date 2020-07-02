---
ms.openlocfilehash: b92dc8a1c48e83846c3d9a1d86e66629f31b7722
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622019"
---
### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a>Impossibilité intermittente de faire défiler jusqu’à l’élément du bas dans les ItemsControls (comme ListBox et DataGrid) lors de l’utilisation de DataTemplates personnalisés

#### <a name="details"></a>Détails

Dans certains cas, un bogue du .NET Framework 4.5 empêche le défilement des ItemsControls (comme <xref:System.Windows.Controls.ListBox?displayProperty=fullName>, <xref:System.Windows.Controls.ComboBox?displayProperty=fullName>, <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>, etc.) jusqu’au dernier élément quand vous utilisez des DataTemplates personnalisés. Si le défilement est tenté une deuxième fois (après avoir fait défiler jusqu’en haut), il fonctionnera.

#### <a name="suggestion"></a>Suggestion

Étant donné que ce problème a été résolu dans le .NET Framework 4.5.2, vous pouvez également mettre à niveau votre version du .NET Framework. Vous pouvez également faire glisser les barres de défilement jusqu’au dernier élément de la collection, mais aurez peut-être à recommencer l’opération une deuxième fois pour y arriver.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,5|
|Type|Runtime|
