---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
ms.openlocfilehash: 3b9a3703e49c3932f62fcfb6994c9028b074bbe8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594411"
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a>Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
La machine à états pour un enrôlement de coordinateur est passée à l'état Finished.  
  
## <a name="description"></a>Description  
 Suivi lorsque le gestionnaire de transactions local croit qu’un enrôlement de coordinateur supérieur a terminé le traitement 2PC. Le résultat peut être Committed, Aborted ou Forgotten. Suivi également lorsque le gestionnaire de transaction local vote ReadOnly pendant la préparation.  
  
## <a name="see-also"></a>Voir aussi

- [Suivi](index.md)
- [Utilisation du suivi pour résoudre les problèmes posés par votre application](using-tracing-to-troubleshoot-your-application.md)
- [Administration et diagnostics](../index.md)
