---
title: 'Comment : exécuter une opération en arrière-plan'
description: Découvrez comment utiliser la classe BackgroundWorker pour exécuter une opération de Windows Forms longue en arrière-plan.
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
ms.openlocfilehash: 6b2a97f5acf1e906dfe141aee62e99a4e50dca9f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621572"
---
# <a name="how-to-run-an-operation-in-the-background"></a><span data-ttu-id="168a8-103">Comment : exécuter une opération en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="168a8-103">How to: Run an Operation in the Background</span></span>
<span data-ttu-id="168a8-104">Si vous avez une opération qui prendra un certain temps et que vous ne souhaitez pas causer de retards dans votre interface utilisateur, vous pouvez utiliser la classe <xref:System.ComponentModel.BackgroundWorker> pour exécuter l'opération sur un autre thread.</span><span class="sxs-lookup"><span data-stu-id="168a8-104">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>  
  
 <span data-ttu-id="168a8-105">L'exemple de code suivant montre comment exécuter une longue opération en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="168a8-105">The following code example shows how to run a time-consuming operation in the background.</span></span> <span data-ttu-id="168a8-106">Le formulaire possède des boutons **Démarrer** et **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="168a8-106">The form has **Start** and **Cancel** buttons.</span></span> <span data-ttu-id="168a8-107">Cliquez sur le bouton **Démarrer** pour exécuter une opération asynchrone.</span><span class="sxs-lookup"><span data-stu-id="168a8-107">Click the **Start** button to run an asynchronous operation.</span></span> <span data-ttu-id="168a8-108">Cliquez sur le bouton **Annuler** pour arrêter une opération asynchrone en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="168a8-108">Click the **Cancel** button to stop a running asynchronous operation.</span></span> <span data-ttu-id="168a8-109">Le résultat de chaque opération est affiché dans un <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="168a8-109">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
 <span data-ttu-id="168a8-110">Cette tâche est très bien prise en charge dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="168a8-110">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="168a8-111">Consultez également l’article [Procédure pas à pas : exécution d’une opération en arrière-plan](walkthrough-running-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="168a8-111">Also see [Walkthrough: Running an Operation in the Background](walkthrough-running-an-operation-in-the-background.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="168a8-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="168a8-112">Example</span></span>  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="168a8-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="168a8-113">Compiling the Code</span></span>  
 <span data-ttu-id="168a8-114">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="168a8-114">This example requires:</span></span>  
  
- <span data-ttu-id="168a8-115">des références aux assemblys System, System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="168a8-115">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="168a8-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="168a8-116">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="168a8-117">Comment : implémenter un formulaire qui utilise une opération d'arrière-plan</span><span class="sxs-lookup"><span data-stu-id="168a8-117">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="168a8-118">Composant BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="168a8-118">BackgroundWorker Component</span></span>](backgroundworker-component.md)
