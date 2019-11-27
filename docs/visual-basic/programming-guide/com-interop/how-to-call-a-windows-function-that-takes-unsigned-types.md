---
title: 'Comment : appeler une fonction Windows qui possède des types non signés'
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
ms.openlocfilehash: 790c680744e2100a40a7cea8b8cef80c68d586bb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348731"
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a>Comment : appeler une fonction Windows qui possède des types non signés (Visual Basic)

Si vous utilisez une classe, un module ou une structure qui a des membres de types entiers non signés, vous pouvez accéder à ces membres avec Visual Basic.

## <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a>Pour appeler une fonction Windows qui accepte un type non signé

1. Utilisez une [instruction DECLARE](../../../visual-basic/language-reference/statements/declare-statement.md) pour indiquer Visual Basic la bibliothèque qui contient la fonction, son nom dans cette bibliothèque, son ordre d’appel, et comment convertir des chaînes lors de son appel.

2. Dans l’instruction `Declare`, utilisez `UInteger`, `ULong`, `UShort`ou `Byte` comme il convient pour chaque paramètre avec un type non signé.

3. Consultez la documentation de la fonction Windows que vous appelez pour rechercher les noms et les valeurs des constantes qu’elle utilise. Un grand nombre d’entre eux sont définis dans le fichier WinUser. h.

4. Déclarez les constantes nécessaires dans votre code. De nombreuses constantes Windows sont des valeurs non signées de 32 bits, et vous devez déclarer ces `As UInteger`.

5. Appelez la fonction de manière normale. L’exemple suivant appelle la fonction Windows `MessageBox`, qui accepte un argument entier non signé.

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

     Vous pouvez tester la fonction `messageThroughWindows` à l’aide du code suivant.

    ```vb
    Public Sub consumeWindowsMessage()
        Dim w As New windowsMessage
        w.messageThroughWindows()
    End Sub
    ```

    > [!CAUTION]
    > Les types de données `UInteger`, `ULong`, `UShort`et `SByte` ne font pas partie de l' [indépendance du langage et des composants indépendants du langage](../../../standard/language-independence-and-language-independent-components.md) (CLS). par conséquent, le code conforme CLS ne peut pas consommer un composant qui les utilise.

    > [!IMPORTANT]
    > Le fait d’appeler du code non managé, tel que l’interface de programmation d’applications (API) Windows, expose votre code à des risques de sécurité potentiels.

    > [!IMPORTANT]
    > L’appel de l’API Windows requiert une autorisation de code non managé, qui peut affecter son exécution dans des situations de confiance partielle. Pour plus d’informations, consultez <xref:System.Security.Permissions.SecurityPermission> et [autorisations d’accès du code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).

## <a name="see-also"></a>Voir aussi

- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Integer (type de données)](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [UInteger (type de données)](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)
- [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Procédure pas à pas : appel des API Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
