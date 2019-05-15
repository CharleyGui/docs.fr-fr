---
title: 'Procédure : Créer et utiliser des assemblys à l’aide de la ligne de commande (C#)'
ms.date: 07/20/2015
ms.assetid: 408ddce3-89e3-4e12-8353-34a49beeb72b
ms.openlocfilehash: 76243034b4291142efa5ac78c21f65333e1378e2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599869"
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-c"></a>Procédure : Créer et utiliser des assemblys à l’aide de la ligne de commande (C#)
Un assembly, ou une bibliothèque de lien dynamique (DLL), est lié à votre programme au moment de l’exécution. Pour illustrer la génération et l’utilisation d’une DLL, considérez le scénario suivant :  
  
- `MathLibrary.DLL`: fichier bibliothèque qui contient les méthodes à appeler au moment de l’exécution. Dans cet exemple, la DLL contient deux méthodes, `Add` et `Multiply`.  
  
- `Add`: fichier source qui contient la méthode `Add`. Il retourne la somme de ses paramètres. La classe `AddClass` qui contient la méthode `Add` est un membre de l’espace de noms `UtilityMethods`.  
  
- `Mult`: code source qui contient la méthode `Multiply`. Il retourne le produit de ses paramètres. La classe `MultiplyClass` qui contient la méthode `Multiply` est également un membre de l’espace de noms `UtilityMethods`.  
  
- `TestCode`: fichier qui contient la méthode `Main`. Il utilise les méthodes dans le fichier DLL pour calculer la somme et le produit des arguments d’exécution.  
  
## <a name="example"></a>Exemple  
  
```csharp  
// File: Add.cs   
namespace UtilityMethods  
{  
    public class AddClass   
    {  
        public static long Add(long i, long j)   
        {   
            return (i + j);  
        }  
    }  
}  
```  
  
```csharp  
// File: Mult.cs  
namespace UtilityMethods   
{  
    public class MultiplyClass  
    {  
        public static long Multiply(long x, long y)   
        {  
            return (x * y);   
        }  
    }  
}  
```  
  
```csharp  
// File: TestCode.cs  
  
using UtilityMethods;  
  
class TestCode  
{  
    static void Main(string[] args)   
    {  
        System.Console.WriteLine("Calling methods from MathLibrary.DLL:");  
  
        if (args.Length != 2)  
        {  
            System.Console.WriteLine("Usage: TestCode <num1> <num2>");  
            return;  
        }  
  
        long num1 = long.Parse(args[0]);  
        long num2 = long.Parse(args[1]);  
  
        long sum = AddClass.Add(num1, num2);  
        long product = MultiplyClass.Multiply(num1, num2);  
  
        System.Console.WriteLine("{0} + {1} = {2}", num1, num2, sum);  
        System.Console.WriteLine("{0} * {1} = {2}", num1, num2, product);  
    }  
}  
/* Output (assuming 1234 and 5678 are entered as command-line arguments):  
    Calling methods from MathLibrary.DLL:  
    1234 + 5678 = 6912  
    1234 * 5678 = 7006652          
*/  
```  
  
 Ce fichier contient l’algorithme qui utilise les méthodes de la DLL, `Add` et `Multiply`. Il commence par analyser les arguments entrés à partir de la ligne de commande, `num1` et `num2`. Il calcule ensuite la somme en utilisant la méthode `Add` sur la classe `AddClass`, et le produit en utilisant la méthode `Multiply` sur la classe `MultiplyClass`.  
  
 Notez que la directive `using` au début du fichier vous permet d’utiliser les noms de classes non qualifiés pour référencer les méthodes de la DLL au moment de la compilation, comme suit :  
  
```csharp  
MultiplyClass.Multiply(num1, num2);  
```  
  
 Sinon, vous devez utiliser les noms qualifiés complets, comme suit :  
  
```csharp  
UtilityMethods.MultiplyClass.Multiply(num1, num2);  
```  
  
## <a name="execution"></a>Exécution  
 Pour exécuter le programme, entrez le nom du fichier EXE, suivi de deux nombres, comme suit :  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Pour générer le fichier `MathLibrary.DLL`, compilez les deux fichiers `Add` et `Mult` à l’aide de la ligne de commande.  
  
```csharp  
csc /target:library /out:MathLibrary.DLL Add.cs Mult.cs  
```  
  
 L’option du compilateur [/target:library](../../../../csharp/language-reference/compiler-options/target-library-compiler-option.md) indique au compilateur qu’il faut générer une DLL plutôt qu’un fichier EXE. L’option du compilateur [/out](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) suivie d’un nom de fichier sert à spécifier le nom du fichier DLL. Sinon, le compilateur utilise le premier fichier (`Add.cs`) comme nom de la DLL.  
  
 Pour générer le fichier exécutable, `TestCode.exe`, utilisez la ligne de commande suivante :  
  
```csharp  
csc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.cs  
```  
  
 L’option du compilateur **/out** indique au compilateur qu’il faut générer un fichier EXE, et spécifie le nom du fichier de sortie (`TestCode.exe`). Cette option du compilateur est facultative. L’option du compilateur [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md) spécifie les fichiers DLL utilisés par ce programme. Pour plus d’informations, consultez [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md).  
  
 Pour plus d’informations sur la génération à partir de la ligne de commande consultez [Génération à partir de la ligne de commande avec csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../../../../csharp/programming-guide/index.md)
- [Assemblys dans .NET](../../../../standard/assembly/index.md)
- [Création d’une classe pour contenir des fonctions DLL](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
