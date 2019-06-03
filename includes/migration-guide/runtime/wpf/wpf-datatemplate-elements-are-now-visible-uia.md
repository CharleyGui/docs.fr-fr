---
ms.openlocfilehash: 51691ced3f05201f784ccdeffbc130e34748b7c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379662"
---
### <a name="wpf-datatemplate-elements-are-now-visible-to-uia"></a>Les éléments DataTemplate WPF sont désormais détectés par UI Automation

|   |   |
|---|---|
|Détails|Avant, les éléments <xref:System.Windows.DataTemplate?displayProperty=name> étaient invisibles pour UI Automation. À compter de la version 4.5, UI Automation détecte ces éléments. C’est pratique dans de nombreux cas, mais peut compromettre les tests qui dépendent des arborescences UI Automation qui ne contiennent pas d’éléments <xref:System.Windows.DataTemplate?displayProperty=name>.|
|Suggestion|Les tests UI Automation pour cette application peuvent nécessiter des modifications pour prendre en compte l’arborescence UI Automation qui contient maintenant des éléments <xref:System.Windows.DataTemplate?displayProperty=name> qui étaient invisibles. Par exemple, les tests qui attendent des éléments contigus doivent maintenant s’attendre à ce que des éléments UIA, autrefois indétectables, se trouvent entre ces éléments. Autre exemple : Les tests qui reposent sur certains nombres ou index pour les éléments UIA peuvent nécessiter la modification de leurs valeurs.|
|Portée|Microsoft Edge|
|Version|4.5|
|Type|Runtime|
|API affectées|<ul><li><xref:System.Windows.DataTemplate.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.DataTemplate.%23ctor(System.Object)?displayProperty=nameWithType></li></ul>|
