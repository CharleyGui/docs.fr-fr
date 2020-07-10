---
title: "Comment : implémenter un formulaire qui utilise une opération d'arrière-plan"
description: Découvrez comment implémenter un Windows Form qui utilise une opération d’arrière-plan afin qu’une opération puisse continuer à s’exécuter pendant qu’une autre opération continue.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- background threads
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9f483f93-1613-4be1-a021-b4934e9c78f3
ms.openlocfilehash: 23bf4bc02fbf998d92dfce6d84e4e337cbefe7d9
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174521"
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a>Comment : implémenter un formulaire qui utilise une opération d'arrière-plan
L'exemple de programme suivant crée un formulaire qui calcule les nombres de Fibonacci. Le calcul s'exécute sur un thread distinct du thread d'interface utilisateur, pour que l'interface utilisateur continue de s'exécuter sans délai lors du calcul.  
  
 Cette tâche est très bien prise en charge dans Visual Studio.  
  
 Consultez également [Procédure pas à pas : implémentation d’un formulaire qui utilise une opération d’arrière-plan](walkthrough-implementing-a-form-that-uses-a-background-operation.md).  
  
## <a name="example"></a>Exemple  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- Références aux assemblys System, System.Drawing et System.Windows.Forms.  
  
## <a name="robust-programming"></a>Programmation fiable  
  
> [!CAUTION]
> Quand vous utilisez le multithreading, vous vous exposez potentiellement à des bogues très sérieux et complexes. Consultez les [Meilleures pratiques pour le threading managé](../../../standard/threading/managed-threading-best-practices.md) avant d’implémenter une solution qui utilise le multithreading.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [Vue d’ensemble du modèle asynchrone basé sur des événements](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Meilleures pratiques pour le threading managé](../../../standard/threading/managed-threading-best-practices.md)
