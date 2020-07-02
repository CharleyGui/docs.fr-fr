---
ms.openlocfilehash: 06c699281c8890ac65be1d282b72b54774acc280
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620476"
---
### <a name="wpf-datatemplate-elements-are-now-visible-to-uia"></a>Les éléments DataTemplate WPF sont désormais détectés par UI Automation

#### <a name="details"></a>Détails

Avant, les éléments <xref:System.Windows.DataTemplate?displayProperty=fullName> étaient invisibles pour UI Automation. À compter de la version 4.5, UI Automation détecte ces éléments. C’est pratique dans de nombreux cas, mais peut compromettre les tests qui dépendent des arborescences UI Automation qui ne contiennent pas d’éléments <xref:System.Windows.DataTemplate?displayProperty=fullName>.

#### <a name="suggestion"></a>Suggestion

Les tests UI Automation pour cette application peuvent nécessiter des modifications pour prendre en compte l’arborescence UI Automation qui contient maintenant des éléments <xref:System.Windows.DataTemplate?displayProperty=fullName> qui étaient invisibles. Par exemple, les tests qui attendent des éléments contigus doivent maintenant s’attendre à ce que des éléments UIA, autrefois indétectables, se trouvent entre ces éléments. Autre exemple : Les tests qui reposent sur certains nombres ou index pour les éléments UIA peuvent nécessiter la modification de leurs valeurs.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Windows.DataTemplate.%23ctor></li><li><xref:System.Windows.DataTemplate.%23ctor(System.Object)></li></ul>|
