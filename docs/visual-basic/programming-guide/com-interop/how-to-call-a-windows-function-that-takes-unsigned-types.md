---
title: 'Procédure : Appeler une fonction Windows qui prend des types non signés (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Windows functions [Visual Basic], calling
- unsigned data types [Visual Basic]
- UShort data type [Visual Basic], using
- functions [Visual Basic], calling Windows functions
- ULong data type [Visual Basic], using
- UInteger data type [Visual Basic], using
- data types [Visual Basic], using
- unsigned types [Visual Basic]
- data types [Visual Basic], unsigned
- data types [Visual Basic], numeric
- unsigned types [Visual Basic], using
ms.assetid: c2c0e712-8dc2-43b9-b4c6-345fbb02e7ce
ms.openlocfilehash: 97075fb6149ed8c0ce06318d0e5bb6f01b841f30
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053324"
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a><span data-ttu-id="35a85-102">Procédure : Appeler une fonction Windows qui prend des types non signés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35a85-102">How to: Call a Windows Function that Takes Unsigned Types (Visual Basic)</span></span>

<span data-ttu-id="35a85-103">Si vous utilisez une classe, un module ou une structure qui a des membres de types entiers non signés, vous pouvez accéder à ces membres avec Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="35a85-103">If you are consuming a class, module, or structure that has members of unsigned integer types, you can access these members with Visual Basic.</span></span>

## <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a><span data-ttu-id="35a85-104">Pour appeler une fonction Windows qui accepte un type non signé</span><span class="sxs-lookup"><span data-stu-id="35a85-104">To call a Windows function that takes an unsigned type</span></span>

1. <span data-ttu-id="35a85-105">Utilisez une [instruction DECLARE](../../../visual-basic/language-reference/statements/declare-statement.md) pour indiquer Visual Basic la bibliothèque qui contient la fonction, son nom dans cette bibliothèque, son ordre d’appel, et comment convertir des chaînes lors de son appel.</span><span class="sxs-lookup"><span data-stu-id="35a85-105">Use a [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) to tell Visual Basic which library holds the function, what its name is in that library, what its calling sequence is, and how to convert strings when calling it.</span></span>

2. <span data-ttu-id="35a85-106">Dans l' `Declare` instruction, utilisez `UInteger`, `ULong` `UShort`, ou`Byte` , selon le cas, pour chaque paramètre avec un type non signé.</span><span class="sxs-lookup"><span data-stu-id="35a85-106">In the `Declare` statement, use `UInteger`, `ULong`, `UShort`, or `Byte` as appropriate for each parameter with an unsigned type.</span></span>

3. <span data-ttu-id="35a85-107">Consultez la documentation de la fonction Windows que vous appelez pour rechercher les noms et les valeurs des constantes qu’elle utilise.</span><span class="sxs-lookup"><span data-stu-id="35a85-107">Consult the documentation for the Windows function you are calling to find the names and values of the constants it uses.</span></span> <span data-ttu-id="35a85-108">Un grand nombre d’entre eux sont définis dans le fichier WinUser. h.</span><span class="sxs-lookup"><span data-stu-id="35a85-108">Many of these are defined in the WinUser.h file.</span></span>

4. <span data-ttu-id="35a85-109">Déclarez les constantes nécessaires dans votre code.</span><span class="sxs-lookup"><span data-stu-id="35a85-109">Declare the necessary constants in your code.</span></span> <span data-ttu-id="35a85-110">De nombreuses constantes Windows sont des valeurs non signées de 32 bits, et vous devez `As UInteger`les déclarer.</span><span class="sxs-lookup"><span data-stu-id="35a85-110">Many Windows constants are 32-bit unsigned values, and you should declare these `As UInteger`.</span></span>

5. <span data-ttu-id="35a85-111">Appelez la fonction de manière normale.</span><span class="sxs-lookup"><span data-stu-id="35a85-111">Call the function in the normal way.</span></span> <span data-ttu-id="35a85-112">L’exemple suivant appelle la fonction `MessageBox`Windows, qui accepte un argument d’entier non signé.</span><span class="sxs-lookup"><span data-stu-id="35a85-112">The following example calls the Windows function `MessageBox`, which takes an unsigned integer argument.</span></span>

    ```vb
    Public Class windowsMessage
        Private Declare Auto Function mb Lib "user32.dll" Alias "MessageBox" (
            ByVal hWnd As Integer,
            ByVal lpText As String,
            ByVal lpCaption As String,
            ByVal uType As UInteger) As Integer
        Private Const MB_OK As UInteger = 0
        Private Const MB_ICONEXCLAMATION As UInteger = &H30
        Private Const IDOK As UInteger = 1
        Private Const IDCLOSE As UInteger = 8
        Private Const c As UInteger = MB_OK Or MB_ICONEXCLAMATION
        Public Function messageThroughWindows() As String
            Dim r As Integer = mb(0, "Click OK if you see this!",
                "Windows API call", c)
            Dim s As String = "Windows API MessageBox returned " &
                 CStr(r)& vbCrLf & "(IDOK = " & CStr(IDOK) &
                 ", IDCLOSE = " & CStr(IDCLOSE) & ")"
            Return s
        End Function
    End Class
    ```

     <span data-ttu-id="35a85-113">Vous pouvez tester la fonction `messageThroughWindows` avec le code suivant.</span><span class="sxs-lookup"><span data-stu-id="35a85-113">You can test the function `messageThroughWindows` with the following code.</span></span>

    ```vb
    Public Sub consumeWindowsMessage()
        Dim w As New windowsMessage
        w.messageThroughWindows()
    End Sub
    ```

    > [!CAUTION]
    > <span data-ttu-id="35a85-114">Les `UInteger`types `ULong`de données`UShort`, `SByte` , et ne font pas partie de l' [indépendance du langage et des composants indépendants du langage](../../../standard/language-independence-and-language-independent-components.md) (CLS). par conséquent, le code conforme CLS ne peut pas consommer un composant qui les utilise.</span><span class="sxs-lookup"><span data-stu-id="35a85-114">The `UInteger`, `ULong`, `UShort`, and `SByte` data types are not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot consume a component that uses them.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="35a85-115">Le fait d’appeler du code non managé, tel que l’interface de programmation d’applications (API) Windows, expose votre code à des risques de sécurité potentiels.</span><span class="sxs-lookup"><span data-stu-id="35a85-115">Making a call to unmanaged code, such as the Windows application programming interface (API), exposes your code to potential security risks.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="35a85-116">L’appel de l’API Windows requiert une autorisation de code non managé, qui peut affecter son exécution dans des situations de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="35a85-116">Calling the Windows API requires unmanaged code permission, which might affect its execution in partial-trust situations.</span></span> <span data-ttu-id="35a85-117">Pour plus d’informations, <xref:System.Security.Permissions.SecurityPermission> consultez et [autorisations d’accès du code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="35a85-117">For more information, see <xref:System.Security.Permissions.SecurityPermission> and [Code Access Permissions](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="35a85-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35a85-118">See also</span></span>

- [<span data-ttu-id="35a85-119">Types de données</span><span class="sxs-lookup"><span data-stu-id="35a85-119">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="35a85-120">Integer (type de données)</span><span class="sxs-lookup"><span data-stu-id="35a85-120">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="35a85-121">UInteger (type de données)</span><span class="sxs-lookup"><span data-stu-id="35a85-121">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)
- [<span data-ttu-id="35a85-122">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="35a85-122">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="35a85-123">Procédure pas à pas : Appel des API Windows</span><span class="sxs-lookup"><span data-stu-id="35a85-123">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
