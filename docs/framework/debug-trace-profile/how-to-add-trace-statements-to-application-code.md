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
ms.openlocfilehash: 4517da87603dcdd398d536cd9bf9e441430be375
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052737"
---
# <a name="how-to-add-trace-statements-to-application-code"></a>Procédure : Ajouter des instructions de trace dans le code d’une application
Les méthodes utilisées le plus souvent pour le suivi sont les méthodes permettant d’écrire la sortie dans des écouteurs : **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**et **Fail**. Ces méthodes peuvent être divisées en deux catégories : Les instructions **Write**, **WriteLine**et **Fail** émettent toutes la sortie sans condition, tandis que **WriteIf**, **WriteLineIf**et **Assert** testent une condition booléenne, et écrivent ou n’écrivent pas en fonction de la valeur de la condition. **WriteIf** et **WriteLineIf** émettent une sortie si la condition est `true` et **Assert** émet une sortie si la condition est `false`.  
  
 Quand vous concevez votre stratégie de débogage et de traçage, vous devez tenir compte de l'apparence souhaitée de la sortie. Si plusieurs instructions **Write** sont remplies avec des informations sans rapport, le journal créé est difficile à lire. D’un autre côté, si vous utilisez **WriteLine** pour placer des instructions connexes sur des lignes distinctes, il peut être difficile de déterminer les informations associées. En règle générale, utilisez plusieurs instructions **Write** si vous voulez combiner des informations provenant de plusieurs sources pour créer un message informatif unique et utilisez l’instruction **WriteLine** quand vous voulez créer un message unique et complet.  
  
### <a name="to-write-a-complete-line"></a>Pour écrire une ligne complète  
  
1. Appelez la méthode <xref:System.Diagnostics.Trace.WriteLine%2A> ou <xref:System.Diagnostics.Trace.WriteLineIf%2A>.  
  
     Un retour chariot est ajouté à la fin du message que cette méthode retourne, afin que le prochain message retourné par **Write**, **WriteIf**, **WriteLine** ou **WriteLineIf** commence à la ligne suivante :  
  
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
  
### <a name="to-write-a-partial-line"></a>Pour écrire une ligne partielle  
  
1. Appelez la méthode <xref:System.Diagnostics.Trace.Write%2A> ou <xref:System.Diagnostics.Trace.WriteIf%2A>.  
  
     Le prochain message émis par une instruction **Write**, **WriteIf**, **WriteLine** ou **WriteLineIf** commence sur la même ligne que le message émis par l’instruction **Write** ou **WriteIf** :  
  
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
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a>Pour vérifier que certaines conditions sont réunies avant ou après l'exécution d'une méthode  
  
1. Appelez la méthode <xref:System.Diagnostics.Trace.Assert%2A>.  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    > Vous pouvez utiliser **Assert** à la fois avec le suivi et le débogage. Cet exemple génère la pile des appels dans n’importe quel écouteur de la collection **Listeners**. Pour plus d’informations, consultez [Assertions dans du code managé](/visualstudio/debugger/assertions-in-managed-code) et <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>
- [Suivi et instrumentation d’applications](tracing-and-instrumenting-applications.md)
- [Guide pratique : Créer, initialiser et configurer des commutateurs de trace](how-to-create-initialize-and-configure-trace-switches.md)
- [Commutateurs de suivi](trace-switches.md)
- [Écouteurs de suivi](trace-listeners.md)
