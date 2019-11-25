---
title: 'How to: View assembly contents'
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET Framework], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 72b02209d74b6b183af6c11d9bd037889ea08543
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347057"
---
# <a name="how-to-view-assembly-contents"></a>How to: View assembly contents

Vous pouvez utiliser [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) pour visualiser les informations de langage MSIL (Microsoft Intermediate Language) dans un fichier. If the file being examined is an assembly, this information can include the assembly's attributes and references to other modules and assemblies. This information can be helpful in determining whether a file is an assembly or part of an assembly and whether the file has references to other modules or assemblies.

To display the contents of an assembly using *Ildasm.exe*, enter **ildasm \<assembly name>** at a command prompt. For example, the following command disassembles the *Hello.exe* assembly.

```cmd
ildasm Hello.exe
```

To view assembly manifest information, double-click the **Manifest** icon in the MSIL Disassembler window.

## <a name="example"></a>Exemple

The following example starts with a basic "Hello World" program. After compiling the program, use *Ildasm.exe* to disassemble the *Hello.exe* assembly and view the assembly manifest.

```cpp
using namespace System;

class MainApp
{
public:
    static void Main()
    {
        Console::WriteLine("Hello World using C++/CLI!");
    }
};

int main()
{
    MainApp::Main();
}
```

```csharp
using System;

class MainApp
{
    public static void Main()
    {
        Console.WriteLine("Hello World using C#!");
    }
}
```

```vb
Class MainApp
    Public Shared Sub Main()
        Console.WriteLine("Hello World using Visual Basic!")
    End Sub
End Class
```

Running the command *ildasm.exe* on the *Hello.exe* assembly and double-clicking the **Manifest** icon in the MSIL Disassembler window produces the following output:

```output
// Metadata version: v4.0.30319
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 4:0:0:0
}
.assembly Hello
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .custom instance void [mscorlib]System.Runtime.CompilerServices.RuntimeCompatibilityAttribute::.ctor() = ( 01 00 01 00 54 02 16 57 72 61 70 4E 6F 6E 45 78   // ....T..WrapNonEx
                                                                                                             63 65 70 74 69 6F 6E 54 68 72 6F 77 73 01 )       // ceptionThrows.
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module Hello.exe
// MVID: {7C2770DB-1594-438D-BAE5-98764C39CCCA}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x00600000
```

The following table describes each directive in the assembly manifest of the *Hello.exe* assembly used in the example:

|Directive|Description|
|---------------|-----------------|
|**.assembly extern \<assembly name>**|Spécifie un autre assembly qui contient des éléments référencés par le module actuel (dans cet exemple, `mscorlib`).|
|**.publickeytoken \<token>**|Spécifie le jeton de la clé réelle de l’assembly référencé.|
|**.ver \<version number>**|Spécifie le numéro de version de l’assembly référencé.|
|**.assembly \<assembly name>**|Spécifie le nom de l’assembly.|
|**.hash algorithm \<int32 value>**|Spécifie l’algorithme de hachage utilisé.|
|**.ver \<version number>**|Spécifie le numéro de version de l’assembly.|
|**.module \<file name>**|Spécifie le nom des modules qui composent l’assembly. Dans cet exemple, l’assembly se compose d’un seul fichier.|
|**.subsystem \<value>**|Spécifie l’environnement d’application nécessaire pour le programme. Dans cet exemple, la valeur 3 indique que cet exécutable est exécuté à partir d’une console.|
|**.corflags**|Actuellement un champ réservé dans les métadonnées.|

Un manifeste d’assembly peut contenir plusieurs directives différentes, en fonction du contenu de l’assembly. For an extensive list of the directives in the assembly manifest, see the Ecma documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set":

- [ECMA C# and Common Language Infrastructure standards](/dotnet/standard/components#applicable-standards)
- [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm)

## <a name="see-also"></a>Voir aussi

- [Domaines d’application et assemblys](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [Application domains and assemblies how-to topics](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [Ildasm.exe (désassembleur IL)](../../framework/tools/ildasm-exe-il-disassembler.md)
