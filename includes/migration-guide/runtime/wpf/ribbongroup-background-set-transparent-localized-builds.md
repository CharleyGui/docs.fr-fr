---
ms.openlocfilehash: d6405573e476ce18513938b500041adefbeeef1b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497881"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a>L’arrière-plan de RibbonGroup est défini sur Transparent dans les versions localisées

#### <a name="details"></a>Détails

L’arrière-plan de <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> sur les versions localisées était toujours dessiné avec le pinceau Transparent, ce qui offrait une expérience assez pauvre de l’interface utilisateur. Ce point est résolu dans le correctif de .NET Framework 4.7 WPF par le biais d’une mise à jour des ressources localisées pour <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName>, qui à son tour garantit que le bon pinceau est sélectionné.

#### <a name="suggestion"></a>Suggestion

Mettre à niveau vers .NET Framework 4.7

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.6.2|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
