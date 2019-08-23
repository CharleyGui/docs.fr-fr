---
title: 'Procédure : Ajouter des instructions de trace dans le code d’une application'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework], conditional writes based on switches
- trace statements
- WriteLineIf method
- tracing [.NET Framework], adding trace statements
- Assert method, tracing code
- trace switches, conditional writes based on switches
- WriteIf method
ms.assetid: f3a93fa7-1717-467d-aaff-393e5c9828b4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 626e9823bbf7d379a21ae353a9189485259f3c42
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948010"
---
# <a name="how-to-add-trace-statements-to-application-code"></a><span data-ttu-id="fffa2-102">Procédure : Ajouter des instructions de trace dans le code d’une application</span><span class="sxs-lookup"><span data-stu-id="fffa2-102">How to: Add Trace Statements to Application Code</span></span>
<span data-ttu-id="fffa2-103">Les méthodes utilisées le plus souvent pour le suivi sont les méthodes permettant d’écrire la sortie dans des écouteurs: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**et **Fail**.</span><span class="sxs-lookup"><span data-stu-id="fffa2-103">The methods used most often for tracing are the methods for writing output to listeners: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**, and **Fail**.</span></span> <span data-ttu-id="fffa2-104">Ces méthodes peuvent être divisées en deux catégories: Les instructions **Write**, **WriteLine**et **Fail** émettent toutes la sortie sans condition, tandis que **WriteIf**, **WriteLineIf**et Assert testent une condition booléenne, et écrivent ou n’écrivent pas en fonction de la valeur de la condition.</span><span class="sxs-lookup"><span data-stu-id="fffa2-104">These methods can be divided into two categories: **Write**, **WriteLine**, and **Fail** all emit output unconditionally, whereas **WriteIf**, **WriteLineIf**, and **Assert** test a Boolean condition, and write or do not write based on the value of the condition.</span></span> <span data-ttu-id="fffa2-105">**WriteIf** et **WriteLineIf** émettent une sortie si la condition est `true` et **Assert** émet une sortie si la condition est `false`.</span><span class="sxs-lookup"><span data-stu-id="fffa2-105">**WriteIf** and **WriteLineIf** emit output if the condition is `true`, and **Assert** emits output if the condition is `false`.</span></span>  
  
 <span data-ttu-id="fffa2-106">Quand vous concevez votre stratégie de débogage et de traçage, vous devez tenir compte de l'apparence souhaitée de la sortie.</span><span class="sxs-lookup"><span data-stu-id="fffa2-106">When designing your tracing and debugging strategy, you should think about how you want the output to look.</span></span> <span data-ttu-id="fffa2-107">Si plusieurs instructions **Write** sont remplies avec des informations sans rapport, le journal créé est difficile à lire.</span><span class="sxs-lookup"><span data-stu-id="fffa2-107">Multiple **Write** statements filled with unrelated information will create a log that is difficult to read.</span></span> <span data-ttu-id="fffa2-108">D’un autre côté, si vous utilisez **WriteLine** pour placer des instructions connexes sur des lignes distinctes, il peut être difficile de déterminer les informations associées.</span><span class="sxs-lookup"><span data-stu-id="fffa2-108">On the other hand, using **WriteLine** to put related statements on separate lines may make it difficult to distinguish what information belongs together.</span></span> <span data-ttu-id="fffa2-109">En règle générale, utilisez plusieurs instructions **Write** si vous voulez combiner des informations provenant de plusieurs sources pour créer un message informatif unique et utilisez l’instruction **WriteLine** quand vous voulez créer un message unique et complet.</span><span class="sxs-lookup"><span data-stu-id="fffa2-109">In general, use multiple **Write** statements when you want to combine information from multiple sources to create a single informative message, and use the **WriteLine** statement when you want to create a single, complete message.</span></span>  
  
### <a name="to-write-a-complete-line"></a><span data-ttu-id="fffa2-110">Pour écrire une ligne complète</span><span class="sxs-lookup"><span data-stu-id="fffa2-110">To write a complete line</span></span>  
  
1. <span data-ttu-id="fffa2-111">Appelez la méthode <xref:System.Diagnostics.Trace.WriteLine%2A> ou <xref:System.Diagnostics.Trace.WriteLineIf%2A>.</span><span class="sxs-lookup"><span data-stu-id="fffa2-111">Call the <xref:System.Diagnostics.Trace.WriteLine%2A> or <xref:System.Diagnostics.Trace.WriteLineIf%2A> method.</span></span>  
  
     <span data-ttu-id="fffa2-112">Un retour chariot est ajouté à la fin du message que cette méthode retourne, afin que le prochain message retourné par **Write**, **WriteIf**, **WriteLine** ou **WriteLineIf** commence à la ligne suivante :</span><span class="sxs-lookup"><span data-stu-id="fffa2-112">A carriage return is appended to the end of the message this method returns, so that the next message returned by **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the following line:</span></span>  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteLine("Error in AppendData procedure.")  
    Trace.WriteLineIf(errorFlag, "Error in AppendData procedure.")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteLine ("Error in AppendData procedure.");  
    System.Diagnostics.Trace.WriteLineIf(errorFlag,   
       "Error in AppendData procedure.");  
    ```  
  
### <a name="to-write-a-partial-line"></a><span data-ttu-id="fffa2-113">Pour écrire une ligne partielle</span><span class="sxs-lookup"><span data-stu-id="fffa2-113">To write a partial line</span></span>  
  
1. <span data-ttu-id="fffa2-114">Appelez la méthode <xref:System.Diagnostics.Trace.Write%2A> ou <xref:System.Diagnostics.Trace.WriteIf%2A>.</span><span class="sxs-lookup"><span data-stu-id="fffa2-114">Call the <xref:System.Diagnostics.Trace.Write%2A> or <xref:System.Diagnostics.Trace.WriteIf%2A> method.</span></span>  
  
     <span data-ttu-id="fffa2-115">Le prochain message émis par une instruction **Write**, **WriteIf**, **WriteLine** ou **WriteLineIf** commence sur la même ligne que le message émis par l’instruction **Write** ou **WriteIf** :</span><span class="sxs-lookup"><span data-stu-id="fffa2-115">The next message put out by a **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the same line as the message put out by the **Write** or **WriteIf** statement:</span></span>  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteIf(errorFlag, "Error in AppendData procedure.")  
    Debug.WriteIf(errorFlag, "Transaction abandoned.")  
    Trace.Write("Invalid value for data request")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteIf(errorFlag,   
       "Error in AppendData procedure.");  
    System.Diagnostics.Debug.WriteIf(errorFlag, "Transaction abandoned.");  
    Trace.Write("Invalid value for data request");  
    ```  
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a><span data-ttu-id="fffa2-116">Pour vérifier que certaines conditions sont réunies avant ou après l'exécution d'une méthode</span><span class="sxs-lookup"><span data-stu-id="fffa2-116">To verify that certain conditions exist either before or after you execute a method</span></span>  
  
1. <span data-ttu-id="fffa2-117">Appelez la méthode <xref:System.Diagnostics.Trace.Assert%2A>.</span><span class="sxs-lookup"><span data-stu-id="fffa2-117">Call the <xref:System.Diagnostics.Trace.Assert%2A> method.</span></span>  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="fffa2-118">Vous pouvez utiliser **Assert** à la fois avec le suivi et le débogage.</span><span class="sxs-lookup"><span data-stu-id="fffa2-118">You can use **Assert** with both tracing and debugging.</span></span> <span data-ttu-id="fffa2-119">Cet exemple génère la pile des appels dans n’importe quel écouteur de la collection **Listeners**.</span><span class="sxs-lookup"><span data-stu-id="fffa2-119">This example outputs the call stack to any listener in the **Listeners** collection.</span></span> <span data-ttu-id="fffa2-120">Pour plus d’informations, consultez [Assertions dans du code managé](/visualstudio/debugger/assertions-in-managed-code) et <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fffa2-120">For more information, see [Assertions in Managed Code](/visualstudio/debugger/assertions-in-managed-code) and <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fffa2-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fffa2-121">See also</span></span>

- <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>
- [<span data-ttu-id="fffa2-122">Suivi et instrumentation d’applications</span><span class="sxs-lookup"><span data-stu-id="fffa2-122">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="fffa2-123">Guide pratique pour Créer, initialiser et configurer des commutateurs de trace</span><span class="sxs-lookup"><span data-stu-id="fffa2-123">How to: Create, Initialize and Configure Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="fffa2-124">Commutateurs de suivi</span><span class="sxs-lookup"><span data-stu-id="fffa2-124">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="fffa2-125">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="fffa2-125">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)
