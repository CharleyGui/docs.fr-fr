---
title: Réglage de votre application Async (C#)
description: Ces exemples C# utilisent CancellationToken et des méthodes de tâche importantes telles que Task. WhenAll et Task. WhenAny pour ajuster les applications Async.
ms.date: 07/20/2015
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
ms.openlocfilehash: 46457f889a78932e306d2bd21dca666625d744eb
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925317"
---
# <a name="fine-tuning-your-async-application-c"></a>Réglage de votre application Async (C#)
Vous pouvez ajouter de la précision et de la flexibilité à vos applications asynchrones en utilisant les méthodes et les propriétés qui sont mises à disposition par le type <xref:System.Threading.Tasks.Task>. Les rubriques de cette section présentent des exemples qui utilisent <xref:System.Threading.CancellationToken> et des méthodes `Task` importantes telles que <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.  
  
 En utilisant `WhenAny` et `WhenAll`, vous pouvez plus facilement démarrer plusieurs tâches et attendre leur achèvement en ne surveillant qu’une seule tâche.  
  
- `WhenAny` retourne une tâche qui se termine lorsque l’une des tâches d’une collection est terminée.  
  
     Pour obtenir des exemples qui utilisent `WhenAny`, consultez [Annuler les tâches asynchrones restantes quand l’une d’elles est terminée (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md) et [Démarrer plusieurs tâches Async et les traiter une fois terminées (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
- `WhenAll` retourne une tâche qui se termine lorsque toutes les tâches d’une collection sont terminées.  
  
     Pour plus d’informations et pour obtenir un exemple qui utilise `WhenAll` , consultez Guide pratique [pour étendre la procédure pas à pas Async à l’aide de Task. WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).
  
 Cette section comprend les exemples suivants :  
  
- [Annuler une tâche asynchrone ou une liste de tâches (C#)](./cancel-an-async-task-or-a-list-of-tasks.md).  
  
- [Annuler des tâches asynchrones après une période de temps (C#)](./cancel-async-tasks-after-a-period-of-time.md)  
  
- [Annuler les tâches asynchrones restantes quand l’une d’elles est terminée (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [Démarrer plusieurs tâches Async et les traiter une fois terminées (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> Pour exécuter les exemples, Visual Studio version 2012 ou ultérieure et le .NET Framework version 4.5 ou ultérieure doivent être installés sur votre ordinateur.  
  
 Les projets créent une interface utilisateur qui contient un bouton permettant de démarrer le processus et un autre permettant de l’annuler, comme dans l’image suivante. Ces boutons se nomment `startButton` et `cancelButton`.  
  
 ![Fenêtre WPF avec un bouton d'annulation](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Boîte de dialogue avec un bouton de démarrage et d’arrêt")  
  
 Téléchargez l’intégralité des projets Windows Presentation Foundation (WPF) à partir de la page [Exemple Async : réglage de votre application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
## <a name="see-also"></a>Voir aussi

- [Programmation asynchrone avec Async et Await (C#)](./index.md)
