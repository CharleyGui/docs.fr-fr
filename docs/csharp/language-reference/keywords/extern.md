---
title: extern, modificateur - Référence C#
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: c121d810e64b5fa27f105f814253c0752e028a95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713539"
---
# <a name="extern-c-reference"></a><span data-ttu-id="ecdda-102">extern (référence C#)</span><span class="sxs-lookup"><span data-stu-id="ecdda-102">extern (C# Reference)</span></span>

<span data-ttu-id="ecdda-103">Le modificateur `extern` permet de déclarer une méthode qui est implémentée en externe.</span><span class="sxs-lookup"><span data-stu-id="ecdda-103">The `extern` modifier is used to declare a method that is implemented externally.</span></span> <span data-ttu-id="ecdda-104">Le modificateur `extern` est souvent utilisé avec l'attribut `DllImport` lors de l'utilisation de services Interop à appeler dans du code non managé.</span><span class="sxs-lookup"><span data-stu-id="ecdda-104">A common use of the `extern` modifier is with the `DllImport` attribute when you are using Interop services to call into unmanaged code.</span></span> <span data-ttu-id="ecdda-105">Dans ce cas, la méthode doit également être déclarée comme `static`, comme indiqué dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="ecdda-105">In this case, the method must also be declared as `static`, as shown in the following example:</span></span>

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

<span data-ttu-id="ecdda-106">Le mot clé `extern` peut également définir un alias d'assembly externe, permettant ainsi de référencer différentes versions du même composant à partir d'un seul assembly.</span><span class="sxs-lookup"><span data-stu-id="ecdda-106">The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.</span></span> <span data-ttu-id="ecdda-107">Pour plus d’informations, consultez [extern alias](extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="ecdda-107">For more information, see [extern alias](extern-alias.md).</span></span>

<span data-ttu-id="ecdda-108">C’est une erreur d’utiliser conjointement les modificateurs [abstract](abstract.md) et `extern` pour modifier le même membre.</span><span class="sxs-lookup"><span data-stu-id="ecdda-108">It is an error to use the [abstract](abstract.md) and `extern` modifiers together to modify the same member.</span></span> <span data-ttu-id="ecdda-109">L'utilisation du modificateur `extern` signifie que la méthode est implémentée en dehors du code C#, tandis que l'utilisation du modificateur `abstract` signifie que l'implémentation de la méthode n'est pas effectuée dans la classe.</span><span class="sxs-lookup"><span data-stu-id="ecdda-109">Using the `extern` modifier means that the method is implemented outside the C# code, whereas using the `abstract` modifier means that the method implementation is not provided in the class.</span></span>

<span data-ttu-id="ecdda-110">L'utilisation du mot clé extern est plus restreinte dans C# que dans C++.</span><span class="sxs-lookup"><span data-stu-id="ecdda-110">The extern keyword has more limited uses in C# than in C++.</span></span> <span data-ttu-id="ecdda-111">Pour comparer son utilisation dans C# et C++, consultez : Utilisation d'extern pour spécifier la liaison dans le Guide de référence du langage C++.</span><span class="sxs-lookup"><span data-stu-id="ecdda-111">To compare the C# keyword with the C++ keyword, see Using extern to Specify Linkage in the C++ Language Reference.</span></span>

## <a name="example-1"></a><span data-ttu-id="ecdda-112">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="ecdda-112">Example 1</span></span>

<span data-ttu-id="ecdda-113">Dans cet exemple, le programme reçoit une chaîne provenant de l’utilisateur et l’affiche dans une boîte de message.</span><span class="sxs-lookup"><span data-stu-id="ecdda-113">In this example, the program receives a string from the user and displays it inside a message box.</span></span> <span data-ttu-id="ecdda-114">Le programme utilise la méthode `MessageBox` importée de la bibliothèque User32.dll.</span><span class="sxs-lookup"><span data-stu-id="ecdda-114">The program uses the `MessageBox` method imported from the User32.dll library.</span></span>

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a><span data-ttu-id="ecdda-115">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="ecdda-115">Example 2</span></span>

<span data-ttu-id="ecdda-116">Cet exemple illustre un programme C# qui fait appel à une bibliothèque C (une DLL native).</span><span class="sxs-lookup"><span data-stu-id="ecdda-116">This example illustrates a C# program that calls into a C library (a native DLL).</span></span>

1. <span data-ttu-id="ecdda-117">Créez le fichier C suivant et nommez-le `cmdll.c` :</span><span class="sxs-lookup"><span data-stu-id="ecdda-117">Create the following C file and name it `cmdll.c`:</span></span>

    ```c
    // cmdll.c
    // Compile with: -LD
    int __declspec(dllexport) SampleMethod(int i)
    {
      return i*10;
    }
    ```

2. <span data-ttu-id="ecdda-118">Ouvrez une fenêtre d’invite de commandes d’outils natifs Visual Studio x64 (ou x32) à partir du répertoire d’installation de Visual Studio et compilez le fichier `cmdll.c` en tapant **cl -LD cmdll.c** à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="ecdda-118">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cmdll.c` file by typing **cl -LD cmdll.c** at the command prompt.</span></span>

3. <span data-ttu-id="ecdda-119">Dans le même répertoire, créez le fichier C# suivant et nommez-le `cm.cs` :</span><span class="sxs-lookup"><span data-stu-id="ecdda-119">In the same directory, create the following C# file and name it `cm.cs`:</span></span>

    ```csharp
    // cm.cs
    using System;
    using System.Runtime.InteropServices;
    public class MainClass
    {
        [DllImport("Cmdll.dll")]
          public static extern int SampleMethod(int x);

        static void Main()
        {
            Console.WriteLine("SampleMethod() returns {0}.", SampleMethod(5));
        }
    }
    ```

4. <span data-ttu-id="ecdda-120">Ouvrez une fenêtre d'invite de commandes d'outils natifs Visual Studio x64 (ou x32) à partir du répertoire d'installation de Visual Studio et compilez le fichier `cm.cs` en tapant :</span><span class="sxs-lookup"><span data-stu-id="ecdda-120">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cm.cs` file by typing:</span></span>

    > <span data-ttu-id="ecdda-121">**csc cm.cs** (pour l’invite de commandes x64) —ou— **csc -platform:x86 cm.cs** (pour l’invite de commandes x32)</span><span class="sxs-lookup"><span data-stu-id="ecdda-121">**csc cm.cs** (for the x64 command prompt) —or— **csc -platform:x86 cm.cs** (for the x32 command prompt)</span></span>

    <span data-ttu-id="ecdda-122">Cette opération crée le fichier exécutable `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="ecdda-122">This will create the executable file `cm.exe`.</span></span>

5. <span data-ttu-id="ecdda-123">Exécutez `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="ecdda-123">Run `cm.exe`.</span></span> <span data-ttu-id="ecdda-124">La méthode `SampleMethod` passe la valeur 5 au fichier DLL, qui retourne la valeur multipliée par 10.</span><span class="sxs-lookup"><span data-stu-id="ecdda-124">The `SampleMethod` method passes the value 5 to the DLL file, which returns the value multiplied by 10.</span></span>  <span data-ttu-id="ecdda-125">Le programme génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="ecdda-125">The program produces the following output:</span></span>

    ```output
    SampleMethod() returns 50.
    ```

## <a name="c-language-specification"></a><span data-ttu-id="ecdda-126">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="ecdda-126">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ecdda-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ecdda-127">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>
- [<span data-ttu-id="ecdda-128">Référence C</span><span class="sxs-lookup"><span data-stu-id="ecdda-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ecdda-129">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="ecdda-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ecdda-130">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="ecdda-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ecdda-131">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="ecdda-131">Modifiers</span></span>](index.md)
