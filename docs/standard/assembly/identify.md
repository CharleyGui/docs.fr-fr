---
title: 'Comment : Déterminer si un fichier est un assemblage'
ms.date: 08/19/2019
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
dev_langs:
- csharp
- vb
ms.openlocfilehash: 1d66c0c166724f195a3cafd9bcbe3c7414c08ebb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159505"
---
# <a name="how-to-determine-if-a-file-is-an-assembly"></a>Comment : Déterminer si un fichier est un assemblage

Un fichier est un assembly si et seulement s’il est managé et s’il contient une entrée d’assembly dans ses métadonnées. Pour plus d’informations sur les assemblées et les métadonnées, voir [Assemblée manifeste](manifest.md).  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Comment déterminer manuellement si un fichier est un assembly  
  
1. Démarrez [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md).  
  
2. Chargez le fichier que vous souhaitez tester.  
  
3. Si **ILDASM** indique que le fichier n’est pas un fichier exécutable portable (PE), alors il ne s’agit pas d’un assembly. Pour plus d’informations, voir le sujet [Comment : Voir le contenu de l’assemblage](view-contents.md).  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Comment déterminer par programmation si un fichier est un assembly  
  
1. Appelez la méthode <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> en passant le chemin complet et le nom du fichier que vous testez.  
  
2. Si une exception <xref:System.BadImageFormatException> est levée, le fichier n’est pas un assembly.  
  
## <a name="example"></a> Exemple  
Cet exemple teste une DLL pour voir s’il s’agit d’un assembly.  

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

La méthode <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> charge le fichier de test, puis le libère une fois que les informations sont lues.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Reflection.AssemblyName>
- [Guide de programmation CMD](../../csharp/programming-guide/index.md)
- [Concepts de programmation (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Assemblys dans .NET](index.md)
