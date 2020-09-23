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
# <a name="main-procedure-in-visual-basic"></a>Procédure Main dans Visual Basic

Chaque Visual Basic application doit contenir une procédure appelée `Main` . Cette procédure sert de point de départ et de contrôle global pour votre application. Le .NET Framework appelle votre `Main` procédure lorsqu’il a chargé votre application et qu’il est prêt à lui transmettre le contrôle. À moins que vous ne soyez en train de créer une application Windows Forms, vous devez écrire la `Main` procédure pour les applications qui s’exécutent de manière autonome.

 `Main` contient le code qui s’exécute en premier. Dans `Main` , vous pouvez déterminer le formulaire à charger en premier au démarrage du programme, savoir si une copie de votre application est déjà en cours d’exécution sur le système, établir un ensemble de variables pour votre application ou ouvrir une base de données dont l’application a besoin.

## <a name="requirements-for-the-main-procedure"></a>Conditions requises pour la procédure main

 Un fichier qui s’exécute seul (généralement avec l’extension. exe) doit contenir une `Main` procédure. Une bibliothèque (par exemple, avec l’extension. dll) n’est pas exécutée de manière autonome et ne nécessite pas de `Main` procédure. La configuration requise pour les différents types de projets que vous pouvez créer est la suivante :

- Les applications console s’exécutent de manière autonome et vous devez fournir au moins une `Main` procédure.

- Windows Forms applications s’exécutent de manière autonome. Toutefois, le compilateur Visual Basic génère automatiquement une `Main` procédure dans une telle application, et vous n’avez pas besoin d’en écrire un.

- Les bibliothèques de classes ne nécessitent pas de `Main` procédure. Celles-ci incluent les bibliothèques de contrôles Windows et les bibliothèques de contrôles Web. Les applications Web sont déployées en tant que bibliothèques de classes.

## <a name="declaring-the-main-procedure"></a>Déclaration de la procédure main

 Il existe quatre façons de déclarer la `Main` procédure. Elle peut accepter ou non des arguments, et elle peut retourner une valeur ou non.

> [!NOTE]
> Si vous déclarez `Main` dans une classe, vous devez utiliser le `Shared` mot clé. Dans un module, `Main` n’a pas besoin d’être `Shared` .

- La méthode la plus simple consiste à déclarer une `Sub` procédure qui ne prend pas d’arguments ou ne retourne pas de valeur.

    ```vb
    Module mainModule
        Sub Main()
            MsgBox("The Main procedure is starting the application.")
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```

- `Main` peut également retourner une `Integer` valeur, que le système d’exploitation utilise comme code de sortie pour votre programme. D’autres programmes peuvent tester ce code en examinant la valeur Windows ERRORLEVEL. Pour retourner un code de sortie, vous devez déclarer `Main` comme une `Function` procédure au lieu d’une `Sub` procédure.

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

- `Main` peut également prendre un `String` tableau en tant qu’argument. Chaque chaîne du tableau contient l’un des arguments de ligne de commande utilisés pour appeler votre programme. Vous pouvez effectuer différentes actions en fonction de leurs valeurs.

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

- Vous pouvez déclarer `Main` pour examiner les arguments de ligne de commande, mais ne pas retourner de code de sortie, comme suit.

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
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>
- <xref:System.Array.Length%2A>
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [Structure d'un programme Visual Basic](structure-of-a-visual-basic-program.md)
- [-main](../../reference/command-line-compiler/main.md)
- [Partagé](../../language-reference/modifiers/shared.md)
- [Sub (instruction)](../../language-reference/statements/sub-statement.md)
- [Function (instruction)](../../language-reference/statements/function-statement.md)
- [Integer (type de données)](../../language-reference/data-types/integer-data-type.md)
- [String, type de données](../../language-reference/data-types/string-data-type.md)
