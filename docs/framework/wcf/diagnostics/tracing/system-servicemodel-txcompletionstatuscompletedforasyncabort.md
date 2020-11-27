---
title: System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort
ms.date: 03/30/2017
ms.assetid: 155c3203-2e17-4709-b896-2254e22da45e
ms.openlocfilehash: f7b3ca5e049adbb773cb6a3054de0a1520300586
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96291737"
---
# <a name="systemservicemodeltxcompletionstatuscompletedforasyncabort"></a>System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort

La transaction spécifiée pour l’opération indiquée s’est terminée en raison d’un abandon asynchrone.  
  
## <a name="description"></a>Description  

 La transaction courante a été abandonnée car un autre participant a voté Abort, le délai a été dépassé et une autre erreur s’est produite à l’intérieur du participant d’une transaction.  
  
## <a name="troubleshooting"></a>Dépannage  

 Si cet abandon est inattendu, vérifiez tous les journaux système afin de déterminer la véritable raison de l'abandon.  
  
## <a name="see-also"></a>Voir aussi

- [Suivi](index.md)
- [Utilisation du suivi pour résoudre les problèmes posés par votre application](using-tracing-to-troubleshoot-your-application.md)
- [Administration et diagnostics](../index.md)
