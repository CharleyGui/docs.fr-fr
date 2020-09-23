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
ms.openlocfilehash: d6708ee13963aaae43a73b159032f64f0fffac10
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072208"
---
# <a name="main-procedure-in-visual-basic"></a><span data-ttu-id="84b9a-102">Procédure Main dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="84b9a-102">Main Procedure in Visual Basic</span></span>

<span data-ttu-id="84b9a-103">Chaque Visual Basic application doit contenir une procédure appelée `Main` .</span><span class="sxs-lookup"><span data-stu-id="84b9a-103">Every Visual Basic application must contain a procedure called `Main`.</span></span> <span data-ttu-id="84b9a-104">Cette procédure sert de point de départ et de contrôle global pour votre application.</span><span class="sxs-lookup"><span data-stu-id="84b9a-104">This procedure serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="84b9a-105">Le .NET Framework appelle votre `Main` procédure lorsqu’il a chargé votre application et qu’il est prêt à lui transmettre le contrôle.</span><span class="sxs-lookup"><span data-stu-id="84b9a-105">The .NET Framework calls your `Main` procedure when it has loaded your application and is ready to pass control to it.</span></span> <span data-ttu-id="84b9a-106">À moins que vous ne soyez en train de créer une application Windows Forms, vous devez écrire la `Main` procédure pour les applications qui s’exécutent de manière autonome.</span><span class="sxs-lookup"><span data-stu-id="84b9a-106">Unless you are creating a Windows Forms application, you must write the `Main` procedure for applications that run on their own.</span></span>

 <span data-ttu-id="84b9a-107">`Main` contient le code qui s’exécute en premier.</span><span class="sxs-lookup"><span data-stu-id="84b9a-107">`Main` contains the code that runs first.</span></span> <span data-ttu-id="84b9a-108">Dans `Main` , vous pouvez déterminer le formulaire à charger en premier au démarrage du programme, savoir si une copie de votre application est déjà en cours d’exécution sur le système, établir un ensemble de variables pour votre application ou ouvrir une base de données dont l’application a besoin.</span><span class="sxs-lookup"><span data-stu-id="84b9a-108">In `Main`, you can determine which form is to be loaded first when the program starts, find out if a copy of your application is already running on the system, establish a set of variables for your application, or open a database that the application requires.</span></span>

## <a name="requirements-for-the-main-procedure"></a><span data-ttu-id="84b9a-109">Conditions requises pour la procédure main</span><span class="sxs-lookup"><span data-stu-id="84b9a-109">Requirements for the Main Procedure</span></span>

 <span data-ttu-id="84b9a-110">Un fichier qui s’exécute seul (généralement avec l’extension. exe) doit contenir une `Main` procédure.</span><span class="sxs-lookup"><span data-stu-id="84b9a-110">A file that runs on its own (usually with extension .exe) must contain a `Main` procedure.</span></span> <span data-ttu-id="84b9a-111">Une bibliothèque (par exemple, avec l’extension. dll) n’est pas exécutée de manière autonome et ne nécessite pas de `Main` procédure.</span><span class="sxs-lookup"><span data-stu-id="84b9a-111">A library (for example with extension .dll) does not run on its own and does not require a `Main` procedure.</span></span> <span data-ttu-id="84b9a-112">La configuration requise pour les différents types de projets que vous pouvez créer est la suivante :</span><span class="sxs-lookup"><span data-stu-id="84b9a-112">The requirements for the different types of projects you can create are as follows:</span></span>

- <span data-ttu-id="84b9a-113">Les applications console s’exécutent de manière autonome et vous devez fournir au moins une `Main` procédure.</span><span class="sxs-lookup"><span data-stu-id="84b9a-113">Console applications run on their own, and you must supply at least one `Main` procedure.</span></span>

- <span data-ttu-id="84b9a-114">Windows Forms applications s’exécutent de manière autonome.</span><span class="sxs-lookup"><span data-stu-id="84b9a-114">Windows Forms applications run on their own.</span></span> <span data-ttu-id="84b9a-115">Toutefois, le compilateur Visual Basic génère automatiquement une `Main` procédure dans une telle application, et vous n’avez pas besoin d’en écrire un.</span><span class="sxs-lookup"><span data-stu-id="84b9a-115">However, the Visual Basic compiler automatically generates a `Main` procedure in such an application, and you do not need to write one.</span></span>

- <span data-ttu-id="84b9a-116">Les bibliothèques de classes ne nécessitent pas de `Main` procédure.</span><span class="sxs-lookup"><span data-stu-id="84b9a-116">Class libraries do not require a `Main` procedure.</span></span> <span data-ttu-id="84b9a-117">Celles-ci incluent les bibliothèques de contrôles Windows et les bibliothèques de contrôles Web.</span><span class="sxs-lookup"><span data-stu-id="84b9a-117">These include Windows Control Libraries and Web Control Libraries.</span></span> <span data-ttu-id="84b9a-118">Les applications Web sont déployées en tant que bibliothèques de classes.</span><span class="sxs-lookup"><span data-stu-id="84b9a-118">Web applications are deployed as class libraries.</span></span>

## <a name="declaring-the-main-procedure"></a><span data-ttu-id="84b9a-119">Déclaration de la procédure main</span><span class="sxs-lookup"><span data-stu-id="84b9a-119">Declaring the Main Procedure</span></span>

 <span data-ttu-id="84b9a-120">Il existe quatre façons de déclarer la `Main` procédure.</span><span class="sxs-lookup"><span data-stu-id="84b9a-120">There are four ways to declare the `Main` procedure.</span></span> <span data-ttu-id="84b9a-121">Elle peut accepter ou non des arguments, et elle peut retourner une valeur ou non.</span><span class="sxs-lookup"><span data-stu-id="84b9a-121">It can take arguments or not, and it can return a value or not.</span></span>

> [!NOTE]
> <span data-ttu-id="84b9a-122">Si vous déclarez `Main` dans une classe, vous devez utiliser le `Shared` mot clé.</span><span class="sxs-lookup"><span data-stu-id="84b9a-122">If you declare `Main` in a class, you must use the `Shared` keyword.</span></span> <span data-ttu-id="84b9a-123">Dans un module, `Main` n’a pas besoin d’être `Shared` .</span><span class="sxs-lookup"><span data-stu-id="84b9a-123">In a module, `Main` does not need to be `Shared`.</span></span>

- <span data-ttu-id="84b9a-124">La méthode la plus simple consiste à déclarer une `Sub` procédure qui ne prend pas d’arguments ou ne retourne pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="84b9a-124">The simplest way is to declare a `Sub` procedure that does not take arguments or return a value.</span></span>

    ```vb
    Module mainModule
        Sub Main()
            MsgBox("The Main procedure is starting the application.")
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```

- <span data-ttu-id="84b9a-125">`Main` peut également retourner une `Integer` valeur, que le système d’exploitation utilise comme code de sortie pour votre programme.</span><span class="sxs-lookup"><span data-stu-id="84b9a-125">`Main` can also return an `Integer` value, which the operating system uses as the exit code for your program.</span></span> <span data-ttu-id="84b9a-126">D’autres programmes peuvent tester ce code en examinant la valeur Windows ERRORLEVEL.</span><span class="sxs-lookup"><span data-stu-id="84b9a-126">Other programs can test this code by examining the Windows ERRORLEVEL value.</span></span> <span data-ttu-id="84b9a-127">Pour retourner un code de sortie, vous devez déclarer `Main` comme une `Function` procédure au lieu d’une `Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="84b9a-127">To return an exit code, you must declare `Main` as a `Function` procedure instead of a `Sub` procedure.</span></span>

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

- <span data-ttu-id="84b9a-128">`Main` peut également prendre un `String` tableau en tant qu’argument.</span><span class="sxs-lookup"><span data-stu-id="84b9a-128">`Main` can also take a `String` array as an argument.</span></span> <span data-ttu-id="84b9a-129">Chaque chaîne du tableau contient l’un des arguments de ligne de commande utilisés pour appeler votre programme.</span><span class="sxs-lookup"><span data-stu-id="84b9a-129">Each string in the array contains one of the command-line arguments used to invoke your program.</span></span> <span data-ttu-id="84b9a-130">Vous pouvez effectuer différentes actions en fonction de leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="84b9a-130">You can take different actions depending on their values.</span></span>

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

- <span data-ttu-id="84b9a-131">Vous pouvez déclarer `Main` pour examiner les arguments de ligne de commande, mais ne pas retourner de code de sortie, comme suit.</span><span class="sxs-lookup"><span data-stu-id="84b9a-131">You can declare `Main` to examine the command-line arguments but not return an exit code, as follows.</span></span>

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
  
## <a name="see-also"></a><span data-ttu-id="84b9a-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84b9a-132">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>
- <xref:System.Array.Length%2A>
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="84b9a-133">Structure d'un programme Visual Basic</span><span class="sxs-lookup"><span data-stu-id="84b9a-133">Structure of a Visual Basic Program</span></span>](structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="84b9a-134">-main</span><span class="sxs-lookup"><span data-stu-id="84b9a-134">-main</span></span>](../../reference/command-line-compiler/main.md)
- [<span data-ttu-id="84b9a-135">Partagé</span><span class="sxs-lookup"><span data-stu-id="84b9a-135">Shared</span></span>](../../language-reference/modifiers/shared.md)
- [<span data-ttu-id="84b9a-136">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="84b9a-136">Sub Statement</span></span>](../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="84b9a-137">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="84b9a-137">Function Statement</span></span>](../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="84b9a-138">Integer (type de données)</span><span class="sxs-lookup"><span data-stu-id="84b9a-138">Integer Data Type</span></span>](../../language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="84b9a-139">String, type de données</span><span class="sxs-lookup"><span data-stu-id="84b9a-139">String Data Type</span></span>](../../language-reference/data-types/string-data-type.md)
