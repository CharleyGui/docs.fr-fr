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
# <a name="how-to-create-and-use-assemblies-using-the-command-line-c"></a><span data-ttu-id="ea6d2-102">Procédure : Créer et utiliser des assemblys à l’aide de la ligne de commande (C#)</span><span class="sxs-lookup"><span data-stu-id="ea6d2-102">How to: Create and Use Assemblies Using the Command Line (C#)</span></span>
<span data-ttu-id="ea6d2-103">Un assembly, ou une bibliothèque de lien dynamique (DLL), est lié à votre programme au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ea6d2-103">An assembly, or a dynamic linking library (DLL), is linked to your program at run time.</span></span> <span data-ttu-id="ea6d2-104">Pour illustrer la génération et l’utilisation d’une DLL, considérez le scénario suivant :</span><span class="sxs-lookup"><span data-stu-id="ea6d2-104">To demonstrate building and using a DLL, consider the following scenario:</span></span>  
  
- <span data-ttu-id="ea6d2-105">`MathLibrary.DLL`: fichier bibliothèque qui contient les méthodes à appeler au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ea6d2-105">`MathLibrary.DLL`: The library file that contains the methods to be called at run time.</span></span> <span data-ttu-id="ea6d2-106">Dans cet exemple, la DLL contient deux méthodes, `Add` et `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="ea6d2-106">In this example, the DLL contains two methods, `Add` and `Multiply`.</span></span>  
  
- <span data-ttu-id="ea6d2-107">`Add`: fichier source qui contient la méthode `Add`.</span><span class="sxs-lookup"><span data-stu-id="ea6d2-107">`Add`: The source file that contains the method `Add`.</span></span> <span data-ttu-id="ea6d2-108">Il retourne la somme de ses paramètres.</span><span class="sxs-lookup"><span data-stu-id="ea6d2-108">It returns the sum of its parameters.</span></span> <span data-ttu-id="ea6d2-109">La classe `AddClass` qui contient la méthode `Add` est un membre de l’espace de noms `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="ea6d2-109">The class `AddClass` that contains the method `Add` is a member of the namespace `UtilityMethods`.</span></span>  
  
- <span data-ttu-id="ea6d2-110">`Mult`: code source qui contient la méthode `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="ea6d2-110">`Mult`: The source code that contains the method `Multiply`.</span></span> <span data-ttu-id="ea6d2-111">Il retourne le produit de ses paramètres.</span><span class="sxs-lookup"><span data-stu-id="ea6d2-111">It returns the product of its parameters.</span></span> <span data-ttu-id="ea6d2-112">La classe `MultiplyClass` qui contient la méthode `Multiply` est également un membre de l’espace de noms `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="ea6d2-112">The class `MultiplyClass` that contains the method `Multiply` is also a member of the namespace `UtilityMethods`.</span></span>  
  
- <span data-ttu-id="ea6d2-113">`TestCode`: fichier qui contient la méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="ea6d2-113">`TestCode`: The file that contains the `Main` method.</span></span> <span data-ttu-id="ea6d2-114">Il utilise les méthodes dans le fichier DLL pour calculer la somme et le produit des arguments d’exécution.</span><span class="sxs-lookup"><span data-stu-id="ea6d2-114">It uses the methods in the DLL file to calculate the sum and the product of the run-time arguments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea6d2-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="ea6d2-115">Example</span></span>  
  
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
  
 <span data-ttu-id="ea6d2-116">Ce fichier contient l’algorithme qui utilise les méthodes de la DLL, `Add` et `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="ea6d2-116">This file contains the algorithm that uses the DLL methods, `Add` and `Multiply`.</span></span> <span data-ttu-id="ea6d2-117">Il commence par analyser les arguments entrés à partir de la ligne de commande, `num1` et `num2`.</span><span class="sxs-lookup"><span data-stu-id="ea6d2-117">It starts with parsing the arguments entered from the command line, `num1` and `num2`.</span></span> <span data-ttu-id="ea6d2-118">Il calcule ensuite la somme en utilisant la méthode `Add` sur la classe `AddClass`, et le produit en utilisant la méthode `Multiply` sur la classe `MultiplyClass`.</span><span class="sxs-lookup"><span data-stu-id="ea6d2-118">Then it calculates the sum by using the `Add` method on the `AddClass` class, and the product by using the `Multiply` method on the `MultiplyClass` class.</span></span>  
  
 <span data-ttu-id="ea6d2-119">Notez que la directive `using` au début du fichier vous permet d’utiliser les noms de classes non qualifiés pour référencer les méthodes de la DLL au moment de la compilation, comme suit :</span><span class="sxs-lookup"><span data-stu-id="ea6d2-119">Notice that the `using` directive at the beginning of the file enables you to use the unqualified class names to reference the DLL methods at compile time, as follows:</span></span>  
  
```csharp  
MultiplyClass.Multiply(num1, num2);  
```  
  
 <span data-ttu-id="ea6d2-120">Sinon, vous devez utiliser les noms qualifiés complets, comme suit :</span><span class="sxs-lookup"><span data-stu-id="ea6d2-120">Otherwise, you have to use the fully qualified names, as follows:</span></span>  
  
```csharp  
UtilityMethods.MultiplyClass.Multiply(num1, num2);  
```  
  
## <a name="execution"></a><span data-ttu-id="ea6d2-121">Exécution</span><span class="sxs-lookup"><span data-stu-id="ea6d2-121">Execution</span></span>  
 <span data-ttu-id="ea6d2-122">Pour exécuter le programme, entrez le nom du fichier EXE, suivi de deux nombres, comme suit :</span><span class="sxs-lookup"><span data-stu-id="ea6d2-122">To run the program, enter the name of the EXE file, followed by two numbers, as follows:</span></span>  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ea6d2-123">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="ea6d2-123">Compiling the Code</span></span>  
 <span data-ttu-id="ea6d2-124">Pour générer le fichier `MathLibrary.DLL`, compilez les deux fichiers `Add` et `Mult` à l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="ea6d2-124">To build the file `MathLibrary.DLL`, compile the two files `Add` and `Mult` by using the following command line.</span></span>  
  
```csharp  
csc /target:library /out:MathLibrary.DLL Add.cs Mult.cs  
```  
  
 <span data-ttu-id="ea6d2-125">L’option du compilateur [/target:library](../../../../csharp/language-reference/compiler-options/target-library-compiler-option.md) indique au compilateur qu’il faut générer une DLL plutôt qu’un fichier EXE.</span><span class="sxs-lookup"><span data-stu-id="ea6d2-125">The [/target:library](../../../../csharp/language-reference/compiler-options/target-library-compiler-option.md) compiler option tells the compiler to output a DLL instead of an EXE file.</span></span> <span data-ttu-id="ea6d2-126">L’option du compilateur [/out](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) suivie d’un nom de fichier sert à spécifier le nom du fichier DLL.</span><span class="sxs-lookup"><span data-stu-id="ea6d2-126">The [/out](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) compiler option followed by a file name is used to specify the DLL file name.</span></span> <span data-ttu-id="ea6d2-127">Sinon, le compilateur utilise le premier fichier (`Add.cs`) comme nom de la DLL.</span><span class="sxs-lookup"><span data-stu-id="ea6d2-127">Otherwise, the compiler uses the first file (`Add.cs`) as the name of the DLL.</span></span>  
  
 <span data-ttu-id="ea6d2-128">Pour générer le fichier exécutable, `TestCode.exe`, utilisez la ligne de commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ea6d2-128">To build the executable file, `TestCode.exe`, use the following command line:</span></span>  
  
```csharp  
csc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.cs  
```  
  
 <span data-ttu-id="ea6d2-129">L’option du compilateur **/out** indique au compilateur qu’il faut générer un fichier EXE, et spécifie le nom du fichier de sortie (`TestCode.exe`).</span><span class="sxs-lookup"><span data-stu-id="ea6d2-129">The **/out** compiler option tells the compiler to output an EXE file and specifies the name of the output file (`TestCode.exe`).</span></span> <span data-ttu-id="ea6d2-130">Cette option du compilateur est facultative.</span><span class="sxs-lookup"><span data-stu-id="ea6d2-130">This compiler option is optional.</span></span> <span data-ttu-id="ea6d2-131">L’option du compilateur [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md) spécifie les fichiers DLL utilisés par ce programme.</span><span class="sxs-lookup"><span data-stu-id="ea6d2-131">The [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md) compiler option specifies the DLL file or files that this program uses.</span></span> <span data-ttu-id="ea6d2-132">Pour plus d’informations, consultez [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="ea6d2-132">For more information, see [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span></span>  
  
 <span data-ttu-id="ea6d2-133">Pour plus d’informations sur la génération à partir de la ligne de commande consultez [Génération à partir de la ligne de commande avec csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ea6d2-133">For more information about building from the command line, see [Command-line Building With csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea6d2-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea6d2-134">See also</span></span>

- [<span data-ttu-id="ea6d2-135">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="ea6d2-135">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="ea6d2-136">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="ea6d2-136">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
- [<span data-ttu-id="ea6d2-137">Création d’une classe pour contenir des fonctions DLL</span><span class="sxs-lookup"><span data-stu-id="ea6d2-137">Creating a Class to Hold DLL Functions</span></span>](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
