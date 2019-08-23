---
title: Réglage de votre application Async (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: 49e57d56c4df79cd9a3e8d5f76d6fc76ebdfa722
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958177"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a>Réglage de votre application Async (Visual Basic)
Vous pouvez ajouter de la précision et de la flexibilité à vos applications asynchrones en utilisant les méthodes et les propriétés qui sont mises à disposition par le type <xref:System.Threading.Tasks.Task>. Les rubriques de cette section présentent des exemples qui utilisent <xref:System.Threading.CancellationToken> et des méthodes `Task` importantes telles que <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.  
  
 En utilisant `WhenAny` et `WhenAll`, vous pouvez plus facilement démarrer plusieurs tâches et attendre leur achèvement en ne surveillant qu’une seule tâche.  
  
- `WhenAny` retourne une tâche qui se termine lorsque l’une des tâches d’une collection est terminée.  
  
     Pour obtenir des exemples `WhenAny`d’utilisation de, consultez [annuler les tâches asynchrones restantes après l’achèvement de l’opération (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)et [Démarrer plusieurs tâches Async et les traiter lorsqu’elles sont terminées (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
- `WhenAll` retourne une tâche qui se termine lorsque toutes les tâches d’une collection sont terminées.  
  
     Pour obtenir des informations supplémentaires et un exemple de code qui utilise `WhenAll`, consultez [Guide pratique pour Étendez la procédure pas à pas Async à l’aide de](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)Task. WhenAll (Visual Basic).  
  
 Cette section comprend les exemples suivants :  
  
- [Annuler une tâche asynchrone ou une liste de tâches (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).  
  
- [Annuler des tâches asynchrones après une période de temps (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
- [Annuler les tâches asynchrones restantes une fois l’opération terminée (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [Démarrer plusieurs tâches Async et les traiter à mesure qu’elles se terminent (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> Pour exécuter les exemples, Visual Studio version 2012 ou ultérieure et le .NET Framework version 4.5 ou ultérieure doivent être installés sur votre ordinateur.  
  
 Les projets créent une interface utilisateur qui contient un bouton permettant de démarrer le processus et un autre permettant de l’annuler, comme dans l’image suivante. Ces boutons se nomment `startButton` et `cancelButton`.  
  
 ![Fenêtre WPF avec bouton Annuler](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Boîte de dialogue avec bouton Démarrer et Arrêter")  
  
 Vous pouvez télécharger l’intégralité des projets WPF (Windows Presentation Foundation) à partir de la page [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (Exemple Async : Réglage précis de votre application).  
  
## <a name="see-also"></a>Voir aussi

- [Programmation asynchrone avec Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
