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
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a><span data-ttu-id="d9c25-103">Comment : implémenter un formulaire qui utilise une opération d'arrière-plan</span><span class="sxs-lookup"><span data-stu-id="d9c25-103">How to: Implement a Form That Uses a Background Operation</span></span>
<span data-ttu-id="d9c25-104">L'exemple de programme suivant crée un formulaire qui calcule les nombres de Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="d9c25-104">The following example program creates a form that calculates Fibonacci numbers.</span></span> <span data-ttu-id="d9c25-105">Le calcul s'exécute sur un thread distinct du thread d'interface utilisateur, pour que l'interface utilisateur continue de s'exécuter sans délai lors du calcul.</span><span class="sxs-lookup"><span data-stu-id="d9c25-105">The calculation runs on a thread that is separate from the user interface thread, so the user interface continues to run without delays as the calculation proceeds.</span></span>  
  
 <span data-ttu-id="d9c25-106">Cette tâche est très bien prise en charge dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d9c25-106">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="d9c25-107">Consultez également [Procédure pas à pas : implémentation d’un formulaire qui utilise une opération d’arrière-plan](walkthrough-implementing-a-form-that-uses-a-background-operation.md).</span><span class="sxs-lookup"><span data-stu-id="d9c25-107">Also see [Walkthrough: Implementing a Form That Uses a Background Operation](walkthrough-implementing-a-form-that-uses-a-background-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9c25-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="d9c25-108">Example</span></span>  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d9c25-109">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="d9c25-109">Compiling the Code</span></span>  
 <span data-ttu-id="d9c25-110">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="d9c25-110">This example requires:</span></span>  
  
- <span data-ttu-id="d9c25-111">Références aux assemblys System, System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="d9c25-111">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d9c25-112">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="d9c25-112">Robust Programming</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="d9c25-113">Quand vous utilisez le multithreading, vous vous exposez potentiellement à des bogues très sérieux et complexes.</span><span class="sxs-lookup"><span data-stu-id="d9c25-113">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="d9c25-114">Consultez les [Meilleures pratiques pour le threading managé](../../../standard/threading/managed-threading-best-practices.md) avant d’implémenter une solution qui utilise le multithreading.</span><span class="sxs-lookup"><span data-stu-id="d9c25-114">Consult the [Managed Threading Best Practices](../../../standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9c25-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9c25-115">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="d9c25-116">Vue d’ensemble du modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="d9c25-116">Event-based Asynchronous Pattern Overview</span></span>](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="d9c25-117">Meilleures pratiques pour le threading managé</span><span class="sxs-lookup"><span data-stu-id="d9c25-117">Managed Threading Best Practices</span></span>](../../../standard/threading/managed-threading-best-practices.md)
