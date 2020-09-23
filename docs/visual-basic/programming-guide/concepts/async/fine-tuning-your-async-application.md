---
title: Réglage de votre application Async
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: 6ad4f9a526e0497029ff8ddc3e93637a4f9acb00
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075432"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a>Ajuster une application Async (Visual Basic)

Vous pouvez ajouter de la précision et de la flexibilité à vos applications asynchrones en utilisant les méthodes et les propriétés qui sont mises à disposition par le type <xref:System.Threading.Tasks.Task>. Les rubriques de cette section présentent des exemples qui utilisent <xref:System.Threading.CancellationToken> et des méthodes `Task` importantes telles que <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.  
  
 En utilisant `WhenAny` et `WhenAll`, vous pouvez plus facilement démarrer plusieurs tâches et attendre leur achèvement en ne surveillant qu’une seule tâche.  
  
- `WhenAny` retourne une tâche qui se termine lorsque l’une des tâches d’une collection est terminée.  
  
     Pour obtenir des exemples d’utilisation de `WhenAny` , consultez  [annuler les tâches asynchrones restantes après l’achèvement de l’opération (Visual Basic)](cancel-remaining-async-tasks-after-one-is-complete.md)et [Démarrer plusieurs tâches Async et les traiter lorsqu’elles sont terminées (Visual Basic)](start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
- `WhenAll` retourne une tâche qui se termine lorsque toutes les tâches d’une collection sont terminées.  
  
     Pour plus d’informations et pour obtenir un exemple qui utilise `WhenAll` , consultez [Comment : étendre la procédure pas à pas Async à l’aide de Task. WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Cette section comprend les exemples suivants :  
  
- [Annuler une tâche asynchrone ou une liste de tâches (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md).  
  
- [Annuler des tâches Asynch après une période spécifique (Visual Basic)](cancel-async-tasks-after-a-period-of-time.md)  
  
- [Annuler les tâches Asynch restantes lorsque l’une d’elles est terminée (Visual Basic)](cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [Démarrer plusieurs tâches Asynch et les traiter une fois terminées (Visual Basic)](start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> Pour exécuter les exemples, Visual Studio version 2012 ou ultérieure et le .NET Framework version 4.5 ou ultérieure doivent être installés sur votre ordinateur.  
  
 Les projets créent une interface utilisateur qui contient un bouton permettant de démarrer le processus et un autre permettant de l’annuler, comme dans l’image suivante. Ces boutons se nomment `startButton` et `cancelButton`.  
  
 ![Fenêtre WPF avec un bouton d'annulation](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Boîte de dialogue avec un bouton de démarrage et d’arrêt")  
  
 Téléchargez l’intégralité des projets Windows Presentation Foundation (WPF) à partir de la page [Exemple Async : réglage de votre application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
## <a name="see-also"></a>Voir aussi

- [Programmation asynchrone avec Async et Await (Visual Basic)](index.md)
