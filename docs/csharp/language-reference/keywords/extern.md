---
description: extern, modificateur - Référence C#
title: extern, modificateur - Référence C#
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: 25eb5e6642d8b608bedcb4e9adadde4d84c2bae9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138967"
---
# <a name="extern-c-reference"></a>extern (référence C#)

Le modificateur `extern` permet de déclarer une méthode qui est implémentée en externe. Le modificateur `extern` est souvent utilisé avec l'attribut `DllImport` lors de l'utilisation de services Interop à appeler dans du code non managé. Dans ce cas, la méthode doit également être déclarée comme `static`, comme indiqué dans l'exemple suivant :

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

Le mot clé `extern` peut également définir un alias d'assembly externe, permettant ainsi de référencer différentes versions du même composant à partir d'un seul assembly. Pour plus d’informations, consultez [extern alias](extern-alias.md).

C’est une erreur d’utiliser conjointement les modificateurs [abstract](abstract.md) et `extern` pour modifier le même membre. L'utilisation du modificateur `extern` signifie que la méthode est implémentée en dehors du code C#, tandis que l'utilisation du modificateur `abstract` signifie que l'implémentation de la méthode n'est pas effectuée dans la classe.

L'utilisation du mot clé extern est plus restreinte dans C# que dans C++. Pour comparer son utilisation dans C# et C++, consultez : Utilisation d'extern pour spécifier la liaison dans le Guide de référence du langage C++.

## <a name="example-1"></a>Exemple 1

Dans cet exemple, le programme reçoit une chaîne provenant de l’utilisateur et l’affiche dans une boîte de message. Le programme utilise la méthode `MessageBox` importée de la bibliothèque User32.dll.

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a>Exemple 2

Cet exemple illustre un programme C# qui fait appel à une bibliothèque C (une DLL native).

1. Créez le fichier C suivant et nommez-le `cmdll.c` :

    ```c
    // cmdll.c
    // Compile with: -LD
    int __declspec(dllexport) SampleMethod(int i)
    {
      return i*10;
    }
    ```

2. Ouvrez une fenêtre d’invite de commandes d’outils natifs Visual Studio x64 (ou x32) à partir du répertoire d’installation de Visual Studio et compilez le fichier `cmdll.c` en tapant **cl -LD cmdll.c** à l’invite de commandes.

3. Dans le même répertoire, créez le fichier C# suivant et nommez-le `cm.cs` :

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

4. Ouvrez une fenêtre d'invite de commandes d'outils natifs Visual Studio x64 (ou x32) à partir du répertoire d'installation de Visual Studio et compilez le fichier `cm.cs` en tapant :

    > **csc cm.cs** (pour l’invite de commandes x64) —ou— **csc -platform:x86 cm.cs** (pour l’invite de commandes x32)

    Cette opération crée le fichier exécutable `cm.exe`.

5. Exécutez `cm.exe`. La méthode `SampleMethod` passe la valeur 5 au fichier DLL, qui retourne la valeur multipliée par 10.  Le programme génère la sortie suivante :

    ```output
    SampleMethod() returns 50.
    ```

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>
- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [Modificateurs](index.md)
