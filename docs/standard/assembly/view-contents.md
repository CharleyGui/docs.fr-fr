---
title: 'Comment : Afficher le contenu de l’assemblage'
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
ms.openlocfilehash: 179b240bb06a319ff71009e14323d5c8f2740e5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187384"
---
# <a name="how-to-view-assembly-contents"></a>Comment : Afficher le contenu de l’assemblage

Vous pouvez utiliser [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) pour visualiser les informations de langage MSIL (Microsoft Intermediate Language) dans un fichier. Si le fichier examiné est un assemblage, ces informations peuvent inclure les attributs et les références de l’assemblage à d’autres modules et assemblages. Ces informations peuvent être utiles pour déterminer si un fichier est un assemblage ou une partie d’un assemblage et si le fichier a des références à d’autres modules ou assemblages.

Pour afficher le contenu d’un assemblage à l’aide *d’Ildasm.exe*, entrez **le nom d’assemblage ildasm \<>** à une invite de commande. Par exemple, la commande suivante démonte l’assemblage *Hello.exe.*

```cmd
ildasm Hello.exe
```

Pour afficher les informations manifestes de l’assemblage, cliquez deux fois sur l’icône **Manifeste** dans la fenêtre du démontage MSIL.

## <a name="example"></a> Exemple

L’exemple suivant commence par un programme de base "Hello World". Après avoir compilé le programme, utilisez *Ildasm.exe* pour démonter l’assemblage *Hello.exe* et voir le manifeste de l’assemblage.

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

Exécution de la commande *ildasm.exe* sur *l’assemblage Hello.exe* et double-cliquer sur l’icône **Manifeste** dans la fenêtre de démontage MSIL produit la sortie suivante:

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

Le tableau suivant décrit chaque directive dans le manifeste d’assemblage de l’assemblée *Hello.exe* utilisée dans l’exemple :

|Directive|Description|
|---------------|-----------------|
|**.assembly nom \<d’assemblée extern>**|Spécifie un autre assembly qui contient des éléments référencés par le module actuel (dans cet exemple, `mscorlib`).|
|**>symbolique .publickeytoken \<**|Spécifie le jeton de la clé réelle de l’assembly référencé.|
|**numéro \<de version .ver>**|Spécifie le numéro de version de l’assembly référencé.|
|**.nom \<de l’assemblée>**|Spécifie le nom de l’assembly.|
|**.hash \<algorithme int32 valeur>**|Spécifie l’algorithme de hachage utilisé.|
|**numéro \<de version .ver>**|Spécifie le numéro de version de l’assembly.|
|**.module \<nom de fichier>**|Spécifie le nom des modules qui composent l’assembly. Dans cet exemple, l’assembly se compose d’un seul fichier.|
|**.sous-système \<de valeur>**|Spécifie l’environnement d’application nécessaire pour le programme. Dans cet exemple, la valeur 3 indique que cet exécutable est exécuté à partir d’une console.|
|**.corflags**|Actuellement un champ réservé dans les métadonnées.|

Un manifeste d’assembly peut contenir plusieurs directives différentes, en fonction du contenu de l’assembly. Pour une longue liste des directives de l’assemblée manifeste, voir la documentation Ecma, en particulier "Partition II: Metadata Definition and Semantics" et "Partition III: CIL Instruction Set":

- [ECMA C et Common Language Infrastructure standards](../components.md#applicable-standards)
- [Standard ECMA-335 - Infrastructure linguistique commune (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm)

## <a name="see-also"></a>Voir aussi

- [Domaines et assemblages d’applications](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [Domaines d’application et assemblages de sujets de comment vers le haut](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [Ildasm.exe (désassembleur IL)](../../framework/tools/ildasm-exe-il-disassembler.md)
