---
title: 'Procédure : inclure dans un wrapper des modèles EAP dans une tâche'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to wrap EAP patterns
ms.assetid: f11ed467-af2f-4504-8a2e-299a6c36d44e
ms.openlocfilehash: 339544ce9f0ee44097d1a60e0d2c2035d81f674d
ms.sourcegitcommit: 6d09ae36acba0b0e2ba47999f8f1a725795462a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92925361"
---
# <a name="how-to-wrap-eap-patterns-in-a-task"></a>Procédure : inclure dans un wrapper des modèles EAP dans une tâche
L’exemple suivant montre comment exposer une séquence arbitraire d’opérations EAP (modèle asynchrone basé sur des événements) comme une seule tâche à l’aide d’un <xref:System.Threading.Tasks.TaskCompletionSource%601>. L’exemple montre également comment utiliser un <xref:System.Threading.CancellationToken> pour appeler les méthodes d’annulation intégrées sur les objets <xref:System.Net.WebClient>.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a>Voir aussi

- [Bibliothèque parallèle de tâches et programmation asynchrone .NET traditionnelle](tpl-and-traditional-async-programming.md)
