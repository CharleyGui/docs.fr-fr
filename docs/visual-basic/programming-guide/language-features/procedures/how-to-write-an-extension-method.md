---
title: 'Procédure : Écrire une méthode d’extension (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 7a7a9d16d9f69071e9d1dacb0558f7ca92e1d21e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631032"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="4f1f4-102">Procédure : Écrire une méthode d’extension (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f1f4-102">How to: Write an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="4f1f4-103">Les méthodes d’extension vous permettent d’ajouter des méthodes à une classe existante.</span><span class="sxs-lookup"><span data-stu-id="4f1f4-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="4f1f4-104">La méthode d’extension peut être appelée comme s’il s’agissait d’une instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="4f1f4-104">The extension method can be called as if it were an instance of that class.</span></span>

### <a name="to-define-an-extension-method"></a><span data-ttu-id="4f1f4-105">Pour définir une méthode d’extension</span><span class="sxs-lookup"><span data-stu-id="4f1f4-105">To define an extension method</span></span>

1. <span data-ttu-id="4f1f4-106">Ouvrez une application de Visual Basic nouvelle ou existante dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4f1f4-106">Open a new or existing Visual Basic application in Visual Studio.</span></span>

2. <span data-ttu-id="4f1f4-107">En haut du fichier dans lequel vous souhaitez définir une méthode d’extension, incluez l’instruction d’importation suivante:</span><span class="sxs-lookup"><span data-stu-id="4f1f4-107">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. <span data-ttu-id="4f1f4-108">Dans un module de votre application nouvelle ou existante, commencez la définition de la méthode par l’attribut d’extension:</span><span class="sxs-lookup"><span data-stu-id="4f1f4-108">Within a module in your new or existing application, begin the method definition with the extension attribute:</span></span>

    ```vb
    <Extension()>
    ```

4. <span data-ttu-id="4f1f4-109">Déclarez votre méthode de manière ordinaire, sauf que le type du premier paramètre doit être le type de données que vous souhaitez étendre.</span><span class="sxs-lookup"><span data-stu-id="4f1f4-109">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>

    ```vb
    <Extension()>
    Public Sub SubName (ByVal para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a><span data-ttu-id="4f1f4-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="4f1f4-110">Example</span></span>
 <span data-ttu-id="4f1f4-111">L’exemple suivant déclare une méthode d’extension dans un `StringExtensions`module.</span><span class="sxs-lookup"><span data-stu-id="4f1f4-111">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="4f1f4-112">Un deuxième module, `Module1`, importe `StringExtensions` et appelle la méthode.</span><span class="sxs-lookup"><span data-stu-id="4f1f4-112">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="4f1f4-113">La méthode d’extension doit être dans la portée quand elle est appelée.</span><span class="sxs-lookup"><span data-stu-id="4f1f4-113">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="4f1f4-114">La méthode `PrintAndPunctuate` d’extension <xref:System.String> étend la classe avec une méthode qui affiche l’instance de chaîne suivie d’une chaîne de symboles de ponctuation envoyée en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="4f1f4-114">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>
  
```vb
' Declarations will typically be in a separate module.
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
        Console.WriteLine(aString & punc)
    End Sub

End Module
```

```vb
' Import the module that holds the extension method you want to use,
' and call it.

Imports ConsoleApplication2.StringExtensions

Module Module1
  
    Sub Main()
        Dim example = "Hello"
        example.PrintAndPunctuate("?")
        example.PrintAndPunctuate("!!!!")
    End Sub
    
End Module
```
  
 <span data-ttu-id="4f1f4-115">Notez que la méthode est définie avec deux paramètres et appelée avec un seul.</span><span class="sxs-lookup"><span data-stu-id="4f1f4-115">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="4f1f4-116">Le premier paramètre, `aString`, dans la définition de méthode est lié `example`à, l’instance `String` de qui appelle la méthode.</span><span class="sxs-lookup"><span data-stu-id="4f1f4-116">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="4f1f4-117">Voici la sortie de l’exemple :</span><span class="sxs-lookup"><span data-stu-id="4f1f4-117">The output of the example is as follows:</span></span>
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a><span data-ttu-id="4f1f4-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f1f4-118">See also</span></span>

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="4f1f4-119">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="4f1f4-119">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="4f1f4-120">Module (instruction)</span><span class="sxs-lookup"><span data-stu-id="4f1f4-120">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)
- [<span data-ttu-id="4f1f4-121">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="4f1f4-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="4f1f4-122">Étendue dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4f1f4-122">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
