---
ms.openlocfilehash: 946096cb9510ca12bbd2cecd00099142308b072a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67856938"
---
### <a name="keytips-behavior-improved-in-wpf"></a>Amélioration du comportement des touches d’accès dans WPF

|   |   |
|---|---|
|Détails|Le comportement des touches d’accès a été modifié afin de correspondre au comportement de Microsoft Word et de l’Explorateur Windows. En vérifiant si l’état de la touche d’accès est activé ou non en cas de pression sur un <xref:System.Windows.Input.KeyEventArgs.SystemKey> (en particulier, <xref:System.Windows.Input.Key> ou <xref:System.Windows.Input.Key.F11>), WPF gère les touches KeyTip en conséquence. Les touches d’accès font maintenant disparaître un menu même quand il est ouvert par la souris.|
|Suggestion|N/A|
|Étendue|Edge|
|Version|4.7.2|
|Type|Runtime|
