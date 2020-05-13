---
title: 'Comment : afficher le contenu d’un assembly'
description: Vous pouvez utiliser le désassembleur IL pour afficher les attributs et les références d’un assembly à d’autres modules et assemblys.
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
ms.openlocfilehash: aed490459252466c6da06e5422b83b1bc20fb885
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380065"
---
# <a name="how-to-view-assembly-contents"></a>Comment : afficher le contenu d’un assembly

Vous pouvez utiliser [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) pour visualiser les informations de langage MSIL (Microsoft Intermediate Language) dans un fichier. Si le fichier examiné est un assembly, ces informations peuvent inclure les attributs et les références de l’assembly à d’autres modules et assemblys. Ces informations peuvent être utiles pour déterminer si un fichier est un assembly ou une partie d’un assembly et si le fichier a des références à d’autres modules ou assemblys.

Pour afficher le contenu d’un assembly à l’aide d' *Ildasm. exe*, entrez le nom de l' ** \< assembly Ildasm>** à l’invite de commandes. Par exemple, la commande suivante désassemble l’assembly *Hello. exe* .

```cmd
ildasm Hello.exe
```

Pour afficher les informations de manifeste d’assembly, double-cliquez sur l’icône de **manifeste** dans la fenêtre du désassembleur MSIL.

## <a name="example"></a>Exemple

L’exemple suivant démarre avec un programme « Hello World » de base. Après avoir compilé le programme, utilisez *Ildasm. exe* pour désassembler l’assembly *Hello. exe* et afficher le manifeste de l’assembly.

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

L’exécution de la commande *Ildasm. exe* sur l’assembly *Hello. exe* et le double-clic sur l’icône du **manifeste** dans la fenêtre du désassembleur MSIL génère la sortie suivante :

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

Le tableau suivant décrit chaque directive dans le manifeste de l’assembly de l’assembly *Hello. exe* utilisé dans l’exemple :

|Directive|Description|
|---------------|-----------------|
|**. assembly extern nom de l' \< assembly>**|Spécifie un autre assembly qui contient des éléments référencés par le module actuel (dans cet exemple, `mscorlib`).|
|**>de \< jeton. PublicKeyToken**|Spécifie le jeton de la clé réelle de l’assembly référencé.|
|**Numéro de \< version. ver>**|Spécifie le numéro de version de l’assembly référencé.|
|**. nom de l’assembly de l’assembly \<>**|Spécifie le nom de l’assembly.|
|**. valeur Int32 de l’algorithme de hachage \<>**|Spécifie l’algorithme de hachage utilisé.|
|**Numéro de \< version. ver>**|Spécifie le numéro de version de l’assembly.|
|**. nom de fichier. module \<>**|Spécifie le nom des modules qui composent l’assembly. Dans cet exemple, l’assembly se compose d’un seul fichier.|
|**valeur du sous-système \<>**|Spécifie l’environnement d’application nécessaire pour le programme. Dans cet exemple, la valeur 3 indique que cet exécutable est exécuté à partir d’une console.|
|**.corflags**|Actuellement un champ réservé dans les métadonnées.|

Un manifeste d’assembly peut contenir plusieurs directives différentes, en fonction du contenu de l’assembly. Pour obtenir une liste complète des directives du manifeste de l’assembly, consultez la documentation ECMA, en particulier « Partition II : Metadata Definition and Semantics » et « Partition III : CIL Instruction Set » :

- [Normes ECMA C# et Common Language Infrastructure](../components.md#applicable-standards)
- [Standard ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm)

## <a name="see-also"></a>Voir aussi

- [Domaines d’application et assemblys](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [Rubriques de procédures relatives aux domaines d’application et aux assemblys](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [Ildasm. exe (Désassembleur IL)](../../framework/tools/ildasm-exe-il-disassembler.md)
