---
title: 'Procédure : exécuter une opération en arrière-plan'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 5b56e2aa-dc05-444f-930c-2d7b23f9ad5b
ms.openlocfilehash: a27c6d83a6a132ed5a83031d469e2f527b730d49
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638368"
---
# <a name="how-to-run-an-operation-in-the-background"></a>Procédure : exécuter une opération en arrière-plan
Si vous avez une opération qui prendra un certain temps et que vous ne souhaitez pas causer de retards dans votre interface utilisateur, vous pouvez utiliser la classe <xref:System.ComponentModel.BackgroundWorker> pour exécuter l'opération sur un autre thread.  
  
 L'exemple de code suivant montre comment exécuter une longue opération en arrière-plan. Le formulaire possède des boutons **Démarrer** et **Annuler**. Cliquez sur le bouton **Démarrer** pour exécuter une opération asynchrone. Cliquez sur le bouton **Annuler** pour arrêter une opération asynchrone en cours d’exécution. Le résultat de chaque opération est affiché dans un <xref:System.Windows.Forms.MessageBox>.  
  
 Cette tâche est très bien prise en charge dans Visual Studio.  
  
 Consultez également [procédure pas à pas : Exécution d’une opération en arrière-plan](walkthrough-running-an-operation-in-the-background.md).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- des références aux assemblys System, System.Drawing et System.Windows.Forms.  
  
 Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande pour Visual Basic ou Visual c#, consultez [génération à partir de la ligne de commande](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [de ligne de commande avec csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Vous pouvez également créer cet exemple dans Visual Studio en collant le code dans un nouveau projet.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [Guide pratique pour implémenter un formulaire qui utilise une opération d’arrière-plan](how-to-implement-a-form-that-uses-a-background-operation.md)
- [Composant BackgroundWorker](backgroundworker-component.md)
