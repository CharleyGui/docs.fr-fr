---
ms.openlocfilehash: 9659068304eb208fd6a0a753273453bc669fbc56
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621275"
---
### <a name="keytips-behavior-improved-in-wpf"></a>Amélioration du comportement des touches d’accès dans WPF

#### <a name="details"></a>Détails

Le comportement des touches d’accès a été modifié afin de correspondre au comportement de Microsoft Word et de l’Explorateur Windows. En vérifiant si l’état de la touche d’accès est activé ou non en cas de pression sur un <xref:System.Windows.Input.KeyEventArgs.SystemKey> (en particulier, <xref:System.Windows.Input.Key> ou <xref:System.Windows.Input.Key.F11>), WPF gère les touches KeyTip en conséquence. Les touches d’accès font maintenant disparaître un menu même quand il est ouvert par la souris.

#### <a name="suggestion"></a>Suggestion

N/A

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.7.2|
|Type|Runtime|
