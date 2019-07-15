---
ms.openlocfilehash: d7cf32eb369e2607ee540d7188cc680b9506c261
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67856938"
---
### <a name="keytips-behavior-improved-in-wpf"></a>Amélioration du comportement des touches d’accès dans WPF

|   |   |
|---|---|
|Détails|Le comportement des touches d’accès a été modifié afin de correspondre au comportement de Microsoft Word et de l’Explorateur Windows. En vérifiant si l’état de la touche d’accès est activé ou non en cas de pression sur un <xref:System.Windows.Input.KeyEventArgs.SystemKey> (en particulier, <xref:System.Windows.Input.Key> ou <xref:System.Windows.Input.Key.F11>), WPF gère les touches KeyTip en conséquence. Les touches d’accès font maintenant disparaître un menu même quand il est ouvert par la souris.|
|Suggestion|N/A|
|Portée|Microsoft Edge|
|Version|4.7.2|
|Type|Runtime|

