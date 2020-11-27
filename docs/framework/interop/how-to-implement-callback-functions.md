---
title: 'Procédure : implémenter des fonctions de rappel'
description: Consultez Comment implémenter des fonctions de rappel. Dans cet exemple, une application managée, à l’aide de l’appel de code non managé, imprime la valeur de handle pour chaque fenêtre sur un ordinateur.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- callback function, implementing
ms.assetid: e55b3712-b9ea-4453-bd9a-ad5cfa2f6bfa
ms.openlocfilehash: 9fa1d3b3ece334e109584f38ba69b796dfe24491
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267050"
---
# <a name="how-to-implement-callback-functions"></a><span data-ttu-id="bfad9-104">Procédure : implémenter des fonctions de rappel</span><span class="sxs-lookup"><span data-stu-id="bfad9-104">How to: Implement Callback Functions</span></span>

<span data-ttu-id="bfad9-105">La procédure et l'exemple suivants montrent comment une application managée peut, à l'aide de l'appel de code non managé, imprimer la valeur de handle de chaque fenêtre sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="bfad9-105">The following procedure and example demonstrate how a managed application, using platform invoke, can print the handle value for each window on the local computer.</span></span> <span data-ttu-id="bfad9-106">En particulier, ils utilisent la fonction **EnumWindows** pour parcourir la liste des fenêtres et une fonction de rappel managée (nommée CallBack) pour imprimer la valeur du handle des fenêtres.</span><span class="sxs-lookup"><span data-stu-id="bfad9-106">Specifically, the procedure and example use the **EnumWindows** function to step through the list of windows and a managed callback function (named CallBack) to print the value of the window handle.</span></span>  
  
### <a name="to-implement-a-callback-function"></a><span data-ttu-id="bfad9-107">Pour implémenter une fonction de rappel</span><span class="sxs-lookup"><span data-stu-id="bfad9-107">To implement a callback function</span></span>  
  
1. <span data-ttu-id="bfad9-108">Examinez la signature de la fonction **EnumWindows** avant d’aller plus loin dans l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="bfad9-108">Look at the signature for the **EnumWindows** function before going further with the implementation.</span></span> <span data-ttu-id="bfad9-109">**EnumWindows** possède la signature suivante :</span><span class="sxs-lookup"><span data-stu-id="bfad9-109">**EnumWindows** has the following signature:</span></span>  
  
    ```cpp
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)
    ```
  
     <span data-ttu-id="bfad9-110">La présence de l’argument **lpEnumFunc** indique que cette fonction nécessite un rappel.</span><span class="sxs-lookup"><span data-stu-id="bfad9-110">One clue that this function requires a callback is the presence of the **lpEnumFunc** argument.</span></span> <span data-ttu-id="bfad9-111">Le préfixe **lp** (pointeur long) est couramment associé au suffixe **Func** dans le nom des arguments qui acceptent un pointeur vers une fonction de rappel.</span><span class="sxs-lookup"><span data-stu-id="bfad9-111">It is common to see the **lp** (long pointer) prefix combined with the **Func** suffix in the name of arguments that take a pointer to a callback function.</span></span> <span data-ttu-id="bfad9-112">Pour obtenir de la documentation sur les fonctions Win32, consultez le Kit de développement Microsoft Platform SDK.</span><span class="sxs-lookup"><span data-stu-id="bfad9-112">For documentation about Win32 functions, see the Microsoft Platform SDK.</span></span>  
  
2. <span data-ttu-id="bfad9-113">Créez la fonction de rappel managée.</span><span class="sxs-lookup"><span data-stu-id="bfad9-113">Create the managed callback function.</span></span> <span data-ttu-id="bfad9-114">L’exemple déclare un type délégué, appelé `CallBack`, qui accepte deux arguments (**hwnd** et **lparam**).</span><span class="sxs-lookup"><span data-stu-id="bfad9-114">The example declares a delegate type, called `CallBack`, which takes two arguments (**hwnd** and **lparam**).</span></span> <span data-ttu-id="bfad9-115">Le premier argument est un handle de la fenêtre, alors que le second est défini par l'application.</span><span class="sxs-lookup"><span data-stu-id="bfad9-115">The first argument is a handle to the window; the second argument is application-defined.</span></span> <span data-ttu-id="bfad9-116">Dans cette mise en production, les deux arguments doivent être des entiers.</span><span class="sxs-lookup"><span data-stu-id="bfad9-116">In this release, both arguments must be integers.</span></span>  
  
     <span data-ttu-id="bfad9-117">Les fonctions de rappel retournent généralement des valeurs différentes de zéro pour indiquer la réussite et zéro pour indiquer l'échec.</span><span class="sxs-lookup"><span data-stu-id="bfad9-117">Callback functions generally return nonzero values to indicate success and zero to indicate failure.</span></span> <span data-ttu-id="bfad9-118">Dans cet exemple, **true** est explicitement défini comme valeur de retour pour poursuivre l’énumération.</span><span class="sxs-lookup"><span data-stu-id="bfad9-118">This example explicitly sets the return value to **true** to continue the enumeration.</span></span>  
  
3. <span data-ttu-id="bfad9-119">Créez un délégué et passez-le en tant qu’argument à la fonction **EnumWindows**.</span><span class="sxs-lookup"><span data-stu-id="bfad9-119">Create a delegate and pass it as an argument to the **EnumWindows** function.</span></span> <span data-ttu-id="bfad9-120">L'appel de code non managé convertit automatiquement le délégué au format de rappel habituel.</span><span class="sxs-lookup"><span data-stu-id="bfad9-120">Platform invoke converts the delegate to a familiar callback format automatically.</span></span>  
  
4. <span data-ttu-id="bfad9-121">Assurez-vous que le garbage collector ne récupère pas le délégué avant que la fonction de rappel n’ait effectué sa tâche.</span><span class="sxs-lookup"><span data-stu-id="bfad9-121">Ensure that the garbage collector does not reclaim the delegate before the callback function completes its work.</span></span> <span data-ttu-id="bfad9-122">Quand vous transmettez un délégué en tant que paramètre ou un délégué contenu en tant que champ dans une structure, il n'est pas collecté pendant toute la durée de l'appel.</span><span class="sxs-lookup"><span data-stu-id="bfad9-122">When you pass a delegate as a parameter, or pass a delegate contained as a field in a structure, it remains uncollected for the duration of the call.</span></span> <span data-ttu-id="bfad9-123">Par conséquent, comme dans le cas de l'exemple d'énumération suivant, la fonction de rappel effectue sa tâche avant le retour d'appel et ne nécessite aucune action supplémentaire de la part de l'appelant managé.</span><span class="sxs-lookup"><span data-stu-id="bfad9-123">So, as is the case in the following enumeration example, the callback function completes its work before the call returns and requires no additional action by the managed caller.</span></span>  
  
     <span data-ttu-id="bfad9-124">Si, toutefois, la fonction de rappel peut être appelée après le retour d'appel, l'appelant managé doit prendre des mesures pour s’assurer que le délégué n'est pas collecté jusqu’à ce que la fonction de rappel termine sa tâche.</span><span class="sxs-lookup"><span data-stu-id="bfad9-124">If, however, the callback function can be invoked after the call returns, the managed caller must take steps to ensure that the delegate remains uncollected until the callback function finishes.</span></span> <span data-ttu-id="bfad9-125">Pour plus d’informations sur la façon d’empêcher l’opération de garbage collection, consultez [Marshaling d’interopérabilité](interop-marshaling.md) avec l’appel de code non managé.</span><span class="sxs-lookup"><span data-stu-id="bfad9-125">For detailed information about preventing garbage collection, see [Interop Marshaling](interop-marshaling.md) with Platform Invoke.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfad9-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="bfad9-126">Example</span></span>  
  
```vb  
Imports System  
Imports System.Runtime.InteropServices  
  
Public Delegate Function CallBack( _  
hwnd As Integer, lParam As Integer) As Boolean  
  
Public Class EnumReportApp  
  
    Declare Function EnumWindows Lib "user32" ( _  
       x As CallBack, y As Integer) As Integer  
  
    Public Shared Sub Main()  
        EnumWindows(AddressOf EnumReportApp.Report, 0)  
    End Sub 'Main  
  
    Public Shared Function Report(hwnd As Integer, lParam As Integer) _  
    As Boolean  
        Console.Write("Window handle is ")  
        Console.WriteLine(hwnd)  
        Return True  
    End Function 'Report  
End Class 'EnumReportApp  
```  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
public delegate bool CallBack(int hwnd, int lParam);  
  
public class EnumReportApp  
{  
    [DllImport("user32")]  
    public static extern int EnumWindows(CallBack x, int y);
  
    public static void Main()
    {  
        CallBack myCallBack = new CallBack(EnumReportApp.Report);  
        EnumWindows(myCallBack, 0);  
    }  
  
    public static bool Report(int hwnd, int lParam)  
    {
        Console.Write("Window handle is ");  
        Console.WriteLine(hwnd);  
        return true;  
    }  
}  
```  
  
```cpp  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
// A delegate type.  
delegate bool CallBack(int hwnd, int lParam);  
  
// Managed type with the method to call.  
ref class EnumReport  
{  
// Report the window handle.  
public:  
    [DllImport("user32")]  
    static int EnumWindows(CallBack^ x, int y);  
  
    static void Main()  
    {  
        EnumReport^ er = gcnew EnumReport;  
        CallBack^ myCallBack = gcnew CallBack(&EnumReport::Report);  
        EnumWindows(myCallBack, 0);  
    }  
  
    static bool Report(int hwnd, int lParam)  
    {  
       Console::Write(L"Window handle is ");  
       Console::WriteLine(hwnd);  
       return true;  
    }  
};  
  
int main()  
{  
    EnumReport::Main();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="bfad9-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bfad9-127">See also</span></span>

- [<span data-ttu-id="bfad9-128">Fonctions de rappel</span><span class="sxs-lookup"><span data-stu-id="bfad9-128">Callback Functions</span></span>](callback-functions.md)
- [<span data-ttu-id="bfad9-129">Appel à une fonction DLL</span><span class="sxs-lookup"><span data-stu-id="bfad9-129">Calling a DLL Function</span></span>](calling-a-dll-function.md)
