---
ms.openlocfilehash: 921baed7381fad363cc832c6b6af69068c2c8f43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802443"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a>L’arrière-plan de RibbonGroup est défini sur Transparent dans les versions localisées

|   |   |
|---|---|
|Détails|L’arrière-plan de <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> sur les versions localisées était toujours dessiné avec le pinceau Transparent, ce qui offrait une expérience assez pauvre de l’interface utilisateur. Ce point est résolu dans le correctif de .NET Framework 4.7 WPF par le biais d’une mise à jour des ressources localisées pour <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, qui à son tour garantit que le bon pinceau est sélectionné.|
|Suggestion|Mettre à niveau vers .NET Framework 4.7|
|Étendue|Edge|
|Version|4.6.2|
|Type|Runtime|
