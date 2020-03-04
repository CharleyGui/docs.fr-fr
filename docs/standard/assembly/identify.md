---
title: 'Comment : déterminer si un fichier est un assembly'
ms.date: 08/19/2019
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
dev_langs:
- csharp
- vb
ms.openlocfilehash: 1d66c0c166724f195a3cafd9bcbe3c7414c08ebb
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159505"
---
# <a name="how-to-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="afa6a-102">Comment : déterminer si un fichier est un assembly</span><span class="sxs-lookup"><span data-stu-id="afa6a-102">How to: Determine if a file is an assembly</span></span>

<span data-ttu-id="afa6a-103">Un fichier est un assembly si et seulement s’il est managé et s’il contient une entrée d’assembly dans ses métadonnées.</span><span class="sxs-lookup"><span data-stu-id="afa6a-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="afa6a-104">Pour plus d’informations sur les assemblys et les métadonnées, consultez manifeste de l' [assembly](manifest.md).</span><span class="sxs-lookup"><span data-stu-id="afa6a-104">For more information on assemblies and metadata, see [Assembly manifest](manifest.md).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="afa6a-105">Comment déterminer manuellement si un fichier est un assembly</span><span class="sxs-lookup"><span data-stu-id="afa6a-105">How to manually determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="afa6a-106">Démarrez [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="afa6a-106">Start the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2. <span data-ttu-id="afa6a-107">Chargez le fichier que vous voulez tester.</span><span class="sxs-lookup"><span data-stu-id="afa6a-107">Load the file you want to test.</span></span>  
  
3. <span data-ttu-id="afa6a-108">Si **ILDASM** indique que le fichier n’est pas un fichier exécutable portable (PE), alors il ne s’agit pas d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="afa6a-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="afa6a-109">Pour plus d’informations, consultez la rubrique [Comment : afficher le contenu d’un assembly](view-contents.md).</span><span class="sxs-lookup"><span data-stu-id="afa6a-109">For more information, see the topic [How to: View assembly contents](view-contents.md).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="afa6a-110">Comment déterminer par programmation si un fichier est un assembly</span><span class="sxs-lookup"><span data-stu-id="afa6a-110">How to programmatically determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="afa6a-111">Appelez la méthode <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> en passant le chemin complet et le nom du fichier que vous testez.</span><span class="sxs-lookup"><span data-stu-id="afa6a-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method, passing the full file path and name of the file you are testing.</span></span>  
  
2. <span data-ttu-id="afa6a-112">Si une exception <xref:System.BadImageFormatException> est levée, le fichier n’est pas un assembly.</span><span class="sxs-lookup"><span data-stu-id="afa6a-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afa6a-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="afa6a-113">Example</span></span>  
<span data-ttu-id="afa6a-114">Cet exemple teste une DLL pour voir s’il s’agit d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="afa6a-114">This example tests a DLL to see if it is an assembly.</span></span>  

```csharp
class TestAssembly  
{  
    static void Main()  
    {  
  
        try  
        {  
            System.Reflection.AssemblyName testAssembly =  
                System.Reflection.AssemblyName.GetAssemblyName(@"C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll");  
  
            System.Console.WriteLine("Yes, the file is an assembly.");  
        }  
  
        catch (System.IO.FileNotFoundException)  
        {  
            System.Console.WriteLine("The file cannot be found.");  
        }  
  
        catch (System.BadImageFormatException)  
        {  
            System.Console.WriteLine("The file is not an assembly.");  
        }  
  
        catch (System.IO.FileLoadException)  
        {  
            System.Console.WriteLine("The assembly has already been loaded.");  
        }  
    }  
}  
/* Output (with .NET Framework 3.5 installed):  
    Yes, the file is an assembly.  
*/  
```  

```vb  
Module Module1  
    Sub Main()  
        Try  
            Dim testAssembly As Reflection.AssemblyName =  
                                Reflection.AssemblyName.GetAssemblyName("C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll")  
            Console.WriteLine("Yes, the file is an Assembly.")  
        Catch ex As System.IO.FileNotFoundException  
            Console.WriteLine("The file cannot be found.")  
        Catch ex As System.BadImageFormatException  
            Console.WriteLine("The file is not an Assembly.")  
        Catch ex As System.IO.FileLoadException  
            Console.WriteLine("The Assembly has already been loaded.")  
        End Try  
        Console.ReadLine()  
    End Sub  
End Module  
' Output (with .NET Framework 3.5 installed):  
'        Yes, the file is an Assembly.  
```

<span data-ttu-id="afa6a-115">La méthode <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> charge le fichier de test, puis le libère une fois que les informations sont lues.</span><span class="sxs-lookup"><span data-stu-id="afa6a-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afa6a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afa6a-116">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="afa6a-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="afa6a-117">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="afa6a-118">Concepts de programmation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afa6a-118">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="afa6a-119">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="afa6a-119">Assemblies in .NET</span></span>](index.md)
