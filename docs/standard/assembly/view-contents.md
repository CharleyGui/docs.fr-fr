---
title: 'Comment : afficher le contenu d’un assembly'
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
ms.openlocfilehash: 0b5e306d55bf38c28e2a68172c2a035b56e8d0af
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140168"
---
# <a name="how-to-view-assembly-contents"></a><span data-ttu-id="df9f5-102">Comment : afficher le contenu d’un assembly</span><span class="sxs-lookup"><span data-stu-id="df9f5-102">How to: View assembly contents</span></span>

<span data-ttu-id="df9f5-103">Vous pouvez utiliser [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) pour visualiser les informations de langage MSIL (Microsoft Intermediate Language) dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="df9f5-103">You can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in a file.</span></span> <span data-ttu-id="df9f5-104">Si le fichier examiné est un assembly, ces informations peuvent inclure les attributs de l’assembly, ainsi que des références à d’autres modules et assemblys.</span><span class="sxs-lookup"><span data-stu-id="df9f5-104">If the file being examined is an assembly, this information can include the assembly's attributes, as well as references to other modules and assemblies.</span></span> <span data-ttu-id="df9f5-105">Ces informations peuvent être utiles pour déterminer si un fichier est un assembly ou fait partie d’un assembly, et s’il a des références à d’autres modules ou assemblys.</span><span class="sxs-lookup"><span data-stu-id="df9f5-105">This information can be helpful in determining whether a file is an assembly or part of an assembly, and whether the file has references to other modules or assemblies.</span></span>  
  
<span data-ttu-id="df9f5-106">Pour afficher le contenu d’un assembly à l’aide d' *Ildasm. exe*, tapez **Ildasm** \<nom de l' *assembly*> à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="df9f5-106">To display the contents of an assembly using *Ildasm.exe*, type **ildasm** \<*assembly name*> at a command prompt.</span></span> <span data-ttu-id="df9f5-107">Par exemple, la commande suivante désassemble l’assembly *Hello. exe* .</span><span class="sxs-lookup"><span data-stu-id="df9f5-107">For example, the following command disassembles the *Hello.exe* assembly.</span></span>  

```cmd
ildasm Hello.exe  
```  

<span data-ttu-id="df9f5-108">Pour afficher les informations de manifeste d’assembly, double-cliquez sur l’icône de **manifeste** dans la fenêtre du désassembleur MSIL.</span><span class="sxs-lookup"><span data-stu-id="df9f5-108">To view assembly manifest information, double-click the **Manifest** icon in the MSIL Disassembler window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df9f5-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="df9f5-109">Example</span></span>  

<span data-ttu-id="df9f5-110">L’exemple suivant démarre avec un programme « Hello World » de base.</span><span class="sxs-lookup"><span data-stu-id="df9f5-110">The following example starts with a basic "Hello World" program.</span></span> <span data-ttu-id="df9f5-111">Après avoir compilé le programme, utilisez *Ildasm. exe* pour désassembler l’assembly *Hello. exe* et afficher le manifeste de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="df9f5-111">After compiling the program, use *Ildasm.exe* to disassemble the *Hello.exe* assembly and view the assembly manifest.</span></span>  

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
Imports System

Class MainApp
    Public Shared Sub Main()
        Console.WriteLine("Hello World using Visual Basic!")
    End Sub
End Class
```

<span data-ttu-id="df9f5-112">L’exécution de la commande *Ildasm. exe* sur l’assembly *Hello. exe* et le double-clic sur l’icône du **manifeste** dans la fenêtre du désassembleur MSIL génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="df9f5-112">Running the command *ildasm.exe* on the *Hello.exe* assembly and double-clicking the **Manifest** icon in the MSIL Disassembler window produces the following output:</span></span>  

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
  
 <span data-ttu-id="df9f5-113">Le tableau suivant décrit chaque directive dans le manifeste d’assembly de l’assembly *Hello. exe* utilisé dans l’exemple.</span><span class="sxs-lookup"><span data-stu-id="df9f5-113">The following table describes each directive in the assembly manifest of the *Hello.exe* assembly used in the example.</span></span>  
  
|<span data-ttu-id="df9f5-114">Directive</span><span class="sxs-lookup"><span data-stu-id="df9f5-114">Directive</span></span>|<span data-ttu-id="df9f5-115">Description</span><span class="sxs-lookup"><span data-stu-id="df9f5-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="df9f5-116">**.assembly extern \<** *nom_assembly* **>**</span><span class="sxs-lookup"><span data-stu-id="df9f5-116">**.assembly extern \<** *assembly name* **>**</span></span>|<span data-ttu-id="df9f5-117">Spécifie un autre assembly qui contient des éléments référencés par le module actuel (dans cet exemple, `mscorlib`).</span><span class="sxs-lookup"><span data-stu-id="df9f5-117">Specifies another assembly that contains items referenced by the current module (in this example, `mscorlib`).</span></span>|  
|<span data-ttu-id="df9f5-118">**.publickeytoken \<** *jeton* **>**</span><span class="sxs-lookup"><span data-stu-id="df9f5-118">**.publickeytoken \<** *token* **>**</span></span>|<span data-ttu-id="df9f5-119">Spécifie le jeton de la clé réelle de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="df9f5-119">Specifies the token of the actual key of the referenced assembly.</span></span>|  
|<span data-ttu-id="df9f5-120">**.ver \<** *numéro_version* **>**</span><span class="sxs-lookup"><span data-stu-id="df9f5-120">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="df9f5-121">Spécifie le numéro de version de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="df9f5-121">Specifies the version number of the referenced assembly.</span></span>|  
|<span data-ttu-id="df9f5-122">**.assembly \<** *nom_assembly* **>**</span><span class="sxs-lookup"><span data-stu-id="df9f5-122">**.assembly \<** *assembly name* **>**</span></span>|<span data-ttu-id="df9f5-123">Spécifie le nom de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="df9f5-123">Specifies the assembly name.</span></span>|  
|<span data-ttu-id="df9f5-124">**.hash algorithm \<** *valeur_int32* **>**</span><span class="sxs-lookup"><span data-stu-id="df9f5-124">**.hash algorithm \<** *int32 value* **>**</span></span>|<span data-ttu-id="df9f5-125">Spécifie l’algorithme de hachage utilisé.</span><span class="sxs-lookup"><span data-stu-id="df9f5-125">Specifies the hash algorithm used.</span></span>|  
|<span data-ttu-id="df9f5-126">**.ver \<** *numéro_version* **>**</span><span class="sxs-lookup"><span data-stu-id="df9f5-126">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="df9f5-127">Spécifie le numéro de version de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="df9f5-127">Specifies the version number of the assembly.</span></span>|  
|<span data-ttu-id="df9f5-128">**.module \<** *nom_fichier* **>**</span><span class="sxs-lookup"><span data-stu-id="df9f5-128">**.module \<** *file name* **>**</span></span>|<span data-ttu-id="df9f5-129">Spécifie le nom des modules qui composent l’assembly.</span><span class="sxs-lookup"><span data-stu-id="df9f5-129">Specifies the name of the modules that make up the assembly.</span></span> <span data-ttu-id="df9f5-130">Dans cet exemple, l’assembly se compose d’un seul fichier.</span><span class="sxs-lookup"><span data-stu-id="df9f5-130">In this example, the assembly consists of only one file.</span></span>|  
|<span data-ttu-id="df9f5-131">**.subsystem \<** *valeur* **>**</span><span class="sxs-lookup"><span data-stu-id="df9f5-131">**.subsystem \<** *value* **>**</span></span>|<span data-ttu-id="df9f5-132">Spécifie l’environnement d’application nécessaire pour le programme.</span><span class="sxs-lookup"><span data-stu-id="df9f5-132">Specifies the application environment required for the program.</span></span> <span data-ttu-id="df9f5-133">Dans cet exemple, la valeur 3 indique que cet exécutable est exécuté à partir d’une console.</span><span class="sxs-lookup"><span data-stu-id="df9f5-133">In this example, the value 3 indicates that this executable is run from a console.</span></span>|  
|<span data-ttu-id="df9f5-134">**.corflags**</span><span class="sxs-lookup"><span data-stu-id="df9f5-134">**.corflags**</span></span>|<span data-ttu-id="df9f5-135">Actuellement un champ réservé dans les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="df9f5-135">Currently a reserved field in the metadata.</span></span>|  
  
 <span data-ttu-id="df9f5-136">Un manifeste d’assembly peut contenir plusieurs directives différentes, en fonction du contenu de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="df9f5-136">An assembly manifest can contain a number of different directives, depending on the contents of the assembly.</span></span> <span data-ttu-id="df9f5-137">Pour obtenir une liste complète des directives du manifeste de l’assembly, consultez la documentation ECMA, en particulier « Partition II : Metadata Definition and Semantics » et « Partition III : CIL Instruction Set ».</span><span class="sxs-lookup"><span data-stu-id="df9f5-137">For an extensive list of the directives in the assembly manifest, see the ECMA documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set."</span></span> <span data-ttu-id="df9f5-138">La documentation est disponible en ligne.</span><span class="sxs-lookup"><span data-stu-id="df9f5-138">The documentation is available online.</span></span> <span data-ttu-id="df9f5-139">Consultez [les C# normes ECMA et Common Language Infrastructure](https://go.microsoft.com/fwlink/?LinkID=99212) sur MSDN et [norme ECMA-335-Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) sur le site Web ECMA International.</span><span class="sxs-lookup"><span data-stu-id="df9f5-139">See [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the ECMA International website.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df9f5-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df9f5-140">See also</span></span>

- [<span data-ttu-id="df9f5-141">Domaines d’application et assemblys</span><span class="sxs-lookup"><span data-stu-id="df9f5-141">Application domains and assemblies</span></span>](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [<span data-ttu-id="df9f5-142">Rubriques de procédures relatives aux domaines d’application et aux assemblys</span><span class="sxs-lookup"><span data-stu-id="df9f5-142">Application domains and assemblies how-to topics</span></span>](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [<span data-ttu-id="df9f5-143">Ildasm.exe (désassembleur IL)</span><span class="sxs-lookup"><span data-stu-id="df9f5-143">Ildasm.exe (IL Disassembler)</span></span>](../../framework/tools/ildasm-exe-il-disassembler.md)
