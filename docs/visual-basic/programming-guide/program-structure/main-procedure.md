---
title: Procédure principale
ms.date: 07/20/2015
f1_keywords:
- vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
ms.openlocfilehash: 61cd397b82b4bb9a8b24a1a7d30eaea68e37368f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347357"
---
# <a name="main-procedure-in-visual-basic"></a><span data-ttu-id="ddd12-102">Procédure Main dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ddd12-102">Main Procedure in Visual Basic</span></span>
<span data-ttu-id="ddd12-103">Every Visual Basic application must contain a procedure called `Main`.</span><span class="sxs-lookup"><span data-stu-id="ddd12-103">Every Visual Basic application must contain a procedure called `Main`.</span></span> <span data-ttu-id="ddd12-104">This procedure serves as the starting point and overall control for your application.</span><span class="sxs-lookup"><span data-stu-id="ddd12-104">This procedure serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="ddd12-105">The .NET Framework calls your `Main` procedure when it has loaded your application and is ready to pass control to it.</span><span class="sxs-lookup"><span data-stu-id="ddd12-105">The .NET Framework calls your `Main` procedure when it has loaded your application and is ready to pass control to it.</span></span> <span data-ttu-id="ddd12-106">Unless you are creating a Windows Forms application, you must write the `Main` procedure for applications that run on their own.</span><span class="sxs-lookup"><span data-stu-id="ddd12-106">Unless you are creating a Windows Forms application, you must write the `Main` procedure for applications that run on their own.</span></span>

 <span data-ttu-id="ddd12-107">`Main` contains the code that runs first.</span><span class="sxs-lookup"><span data-stu-id="ddd12-107">`Main` contains the code that runs first.</span></span> <span data-ttu-id="ddd12-108">In `Main`, you can determine which form is to be loaded first when the program starts, find out if a copy of your application is already running on the system, establish a set of variables for your application, or open a database that the application requires.</span><span class="sxs-lookup"><span data-stu-id="ddd12-108">In `Main`, you can determine which form is to be loaded first when the program starts, find out if a copy of your application is already running on the system, establish a set of variables for your application, or open a database that the application requires.</span></span>

## <a name="requirements-for-the-main-procedure"></a><span data-ttu-id="ddd12-109">Requirements for the Main Procedure</span><span class="sxs-lookup"><span data-stu-id="ddd12-109">Requirements for the Main Procedure</span></span>
 <span data-ttu-id="ddd12-110">A file that runs on its own (usually with extension .exe) must contain a `Main` procedure.</span><span class="sxs-lookup"><span data-stu-id="ddd12-110">A file that runs on its own (usually with extension .exe) must contain a `Main` procedure.</span></span> <span data-ttu-id="ddd12-111">A library (for example with extension .dll) does not run on its own and does not require a `Main` procedure.</span><span class="sxs-lookup"><span data-stu-id="ddd12-111">A library (for example with extension .dll) does not run on its own and does not require a `Main` procedure.</span></span> <span data-ttu-id="ddd12-112">The requirements for the different types of projects you can create are as follows:</span><span class="sxs-lookup"><span data-stu-id="ddd12-112">The requirements for the different types of projects you can create are as follows:</span></span>

- <span data-ttu-id="ddd12-113">Console applications run on their own, and you must supply at least one `Main` procedure.</span><span class="sxs-lookup"><span data-stu-id="ddd12-113">Console applications run on their own, and you must supply at least one `Main` procedure.</span></span>

- <span data-ttu-id="ddd12-114">Windows Forms applications run on their own.</span><span class="sxs-lookup"><span data-stu-id="ddd12-114">Windows Forms applications run on their own.</span></span> <span data-ttu-id="ddd12-115">However, the Visual Basic compiler automatically generates a `Main` procedure in such an application, and you do not need to write one.</span><span class="sxs-lookup"><span data-stu-id="ddd12-115">However, the Visual Basic compiler automatically generates a `Main` procedure in such an application, and you do not need to write one.</span></span>

- <span data-ttu-id="ddd12-116">Class libraries do not require a `Main` procedure.</span><span class="sxs-lookup"><span data-stu-id="ddd12-116">Class libraries do not require a `Main` procedure.</span></span> <span data-ttu-id="ddd12-117">These include Windows Control Libraries and Web Control Libraries.</span><span class="sxs-lookup"><span data-stu-id="ddd12-117">These include Windows Control Libraries and Web Control Libraries.</span></span> <span data-ttu-id="ddd12-118">Web applications are deployed as class libraries.</span><span class="sxs-lookup"><span data-stu-id="ddd12-118">Web applications are deployed as class libraries.</span></span>

## <a name="declaring-the-main-procedure"></a><span data-ttu-id="ddd12-119">Declaring the Main Procedure</span><span class="sxs-lookup"><span data-stu-id="ddd12-119">Declaring the Main Procedure</span></span>
 <span data-ttu-id="ddd12-120">There are four ways to declare the `Main` procedure.</span><span class="sxs-lookup"><span data-stu-id="ddd12-120">There are four ways to declare the `Main` procedure.</span></span> <span data-ttu-id="ddd12-121">It can take arguments or not, and it can return a value or not.</span><span class="sxs-lookup"><span data-stu-id="ddd12-121">It can take arguments or not, and it can return a value or not.</span></span>

> [!NOTE]
> <span data-ttu-id="ddd12-122">If you declare `Main` in a class, you must use the `Shared` keyword.</span><span class="sxs-lookup"><span data-stu-id="ddd12-122">If you declare `Main` in a class, you must use the `Shared` keyword.</span></span> <span data-ttu-id="ddd12-123">In a module, `Main` does not need to be `Shared`.</span><span class="sxs-lookup"><span data-stu-id="ddd12-123">In a module, `Main` does not need to be `Shared`.</span></span>

- <span data-ttu-id="ddd12-124">The simplest way is to declare a `Sub` procedure that does not take arguments or return a value.</span><span class="sxs-lookup"><span data-stu-id="ddd12-124">The simplest way is to declare a `Sub` procedure that does not take arguments or return a value.</span></span>

    ```vb
    Module mainModule
        Sub Main()
            MsgBox("The Main procedure is starting the application.")
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```

- <span data-ttu-id="ddd12-125">`Main` can also return an `Integer` value, which the operating system uses as the exit code for your program.</span><span class="sxs-lookup"><span data-stu-id="ddd12-125">`Main` can also return an `Integer` value, which the operating system uses as the exit code for your program.</span></span> <span data-ttu-id="ddd12-126">Other programs can test this code by examining the Windows ERRORLEVEL value.</span><span class="sxs-lookup"><span data-stu-id="ddd12-126">Other programs can test this code by examining the Windows ERRORLEVEL value.</span></span> <span data-ttu-id="ddd12-127">To return an exit code, you must declare `Main` as a `Function` procedure instead of a `Sub` procedure.</span><span class="sxs-lookup"><span data-stu-id="ddd12-127">To return an exit code, you must declare `Main` as a `Function` procedure instead of a `Sub` procedure.</span></span>

    ```vb
    Module mainModule
        Function Main() As Integer
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' Insert call to appropriate starting place in your code.
            ' On return, assign appropriate value to returnValue.
            ' 0 usually means successful completion.
            MsgBox("The application is terminating with error level " &
                 CStr(returnValue) & ".")
            Return returnValue
        End Function
    End Module
    ```

- <span data-ttu-id="ddd12-128">`Main` can also take a `String` array as an argument.</span><span class="sxs-lookup"><span data-stu-id="ddd12-128">`Main` can also take a `String` array as an argument.</span></span> <span data-ttu-id="ddd12-129">Each string in the array contains one of the command-line arguments used to invoke your program.</span><span class="sxs-lookup"><span data-stu-id="ddd12-129">Each string in the array contains one of the command-line arguments used to invoke your program.</span></span> <span data-ttu-id="ddd12-130">You can take different actions depending on their values.</span><span class="sxs-lookup"><span data-stu-id="ddd12-130">You can take different actions depending on their values.</span></span>

    ```vb
    Module mainModule
        Function Main(ByVal cmdArgs() As String) As Integer
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
            End If
            ' Insert call to appropriate starting place in your code.
            ' On return, assign appropriate value to returnValue.
            ' 0 usually means successful completion.
            MsgBox("The application is terminating with error level " &
                 CStr(returnValue) & ".")
            Return returnValue
        End Function
    End Module
    ```

- <span data-ttu-id="ddd12-131">You can declare `Main` to examine the command-line arguments but not return an exit code, as follows.</span><span class="sxs-lookup"><span data-stu-id="ddd12-131">You can declare `Main` to examine the command-line arguments but not return an exit code, as follows.</span></span>

    ```vb
    Module mainModule
        Sub Main(ByVal cmdArgs() As String)
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
            End If
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```
  
## <a name="see-also"></a><span data-ttu-id="ddd12-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ddd12-132">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>
- <xref:System.Array.Length%2A>
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="ddd12-133">Structure of a Visual Basic Program</span><span class="sxs-lookup"><span data-stu-id="ddd12-133">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="ddd12-134">-main</span><span class="sxs-lookup"><span data-stu-id="ddd12-134">-main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)
- [<span data-ttu-id="ddd12-135">Shared</span><span class="sxs-lookup"><span data-stu-id="ddd12-135">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="ddd12-136">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="ddd12-136">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="ddd12-137">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="ddd12-137">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="ddd12-138">Integer (type de données)</span><span class="sxs-lookup"><span data-stu-id="ddd12-138">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="ddd12-139">String (type de données)</span><span class="sxs-lookup"><span data-stu-id="ddd12-139">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
