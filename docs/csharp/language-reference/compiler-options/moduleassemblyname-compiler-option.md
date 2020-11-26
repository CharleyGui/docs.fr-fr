---
description: -moduleassemblyname (Options du compilateur C#)
title: -moduleassemblyname (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
ms.openlocfilehash: 9131db17d767c76fe6a57f5d5353474153e0c269
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "91194087"
---
# <a name="-moduleassemblyname-c-compiler-option"></a><span data-ttu-id="758ac-103">-moduleassemblyname (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="758ac-103">-moduleassemblyname (C# Compiler Option)</span></span>

<span data-ttu-id="758ac-104">Spécifie un assembly dont les types non publics sont accessibles par un .netmodule.</span><span class="sxs-lookup"><span data-stu-id="758ac-104">Specifies an assembly whose non-public types a .netmodule can access.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="758ac-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="758ac-105">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="758ac-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="758ac-106">Arguments</span></span>  

 `assembly_name`  
 <span data-ttu-id="758ac-107">Nom de l’assembly dont les types non publics sont accessibles au fichier .netmodule.</span><span class="sxs-lookup"><span data-stu-id="758ac-107">The name of the assembly whose non-public types the .netmodule can access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="758ac-108">Notes</span><span class="sxs-lookup"><span data-stu-id="758ac-108">Remarks</span></span>  

 <span data-ttu-id="758ac-109">**-moduleassemblyname** doit être utilisée au moment de créer un fichier .netmodule et quand les conditions suivantes sont réunies :</span><span class="sxs-lookup"><span data-stu-id="758ac-109">**-moduleassemblyname** should be used when building a .netmodule, and where the following conditions are true:</span></span>  
  
- <span data-ttu-id="758ac-110">Le fichier .netmodule doit accéder à des types non publics dans un assembly existant.</span><span class="sxs-lookup"><span data-stu-id="758ac-110">The .netmodule needs access to non-public types in an existing assembly.</span></span>  
  
- <span data-ttu-id="758ac-111">Vous connaissez le nom de l’assembly dans lequel le fichier .netmodule sera généré.</span><span class="sxs-lookup"><span data-stu-id="758ac-111">You know the name of the assembly into which the .netmodule will be built.</span></span>  
  
- <span data-ttu-id="758ac-112">L’assembly existant a accordé un accès d’assembly friend à l’assembly dans lequel le fichier .netmodule sera généré.</span><span class="sxs-lookup"><span data-stu-id="758ac-112">The existing assembly has granted friend assembly access to the assembly into which the .netmodule will be built.</span></span>  
  
 <span data-ttu-id="758ac-113">Pour plus d’informations sur la création d’un fichier .netmodule, consultez [-target:module (Options du compilateur C#)](./target-module-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="758ac-113">For more information on building a .netmodule, see [-target:module (C# Compiler Options)](./target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="758ac-114">Pour plus d’informations sur les assemblys friend, consultez [Assemblys friend](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="758ac-114">For more information on friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
 <span data-ttu-id="758ac-115">Cette option n’est pas disponible dans l’environnement de développement ; elle l’est uniquement au moment de compiler à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="758ac-115">This option is not available from within the development environment; it is only available when compiling from the command line.</span></span>  
  
 <span data-ttu-id="758ac-116">Cette option de compilateur n’est pas disponible dans Visual Studio et ne peut pas être changée par programmation.</span><span class="sxs-lookup"><span data-stu-id="758ac-116">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="758ac-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="758ac-117">Example</span></span>  

 <span data-ttu-id="758ac-118">Cet exemple génère un assembly avec un type privé, ce qui octroie un accès d’assembly friend à un assembly appelé csman_an_assembly.</span><span class="sxs-lookup"><span data-stu-id="758ac-118">This sample builds an assembly with a private type, and that gives friend assembly access to an assembly called csman_an_assembly.</span></span>  
  
```csharp  
// moduleassemblyname_1.cs  
// compile with: -target:library  
using System;  
using System.Runtime.CompilerServices;  
  
[assembly:InternalsVisibleTo ("csman_an_assembly")]  
  
class An_Internal_Class
{  
    public void Test()
    {
        Console.WriteLine("An_Internal_Class.Test called");
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="758ac-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="758ac-119">Example</span></span>  

 <span data-ttu-id="758ac-120">Cet exemple génère un fichier .netmodule qui accède à un type non public dans l’assembly moduleassemblyname_1.dll.</span><span class="sxs-lookup"><span data-stu-id="758ac-120">This sample builds a .netmodule that accesses a non-public type in the assembly moduleassemblyname_1.dll.</span></span> <span data-ttu-id="758ac-121">En sachant que ce. netmodule sera intégré à un assembly appelé csman_an_assembly, nous pouvons spécifier **-moduleassemblyname**, ce qui permet au. netmodule d’accéder aux types non publics dans un assembly qui a accordé un accès d’assembly friend à csman_an_assembly.</span><span class="sxs-lookup"><span data-stu-id="758ac-121">By knowing that this .netmodule will be built into an assembly called csman_an_assembly, we can specify **-moduleassemblyname**, allowing the .netmodule to access non-public types in an assembly that has granted friend assembly access to csman_an_assembly.</span></span>  
  
```csharp  
// moduleassemblyname_2.cs  
// compile with: -moduleassemblyname:csman_an_assembly -target:module -reference:moduleassemblyname_1.dll  
class B {  
    public void Test() {  
        An_Internal_Class x = new An_Internal_Class();  
        x.Test();  
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="758ac-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="758ac-122">Example</span></span>  

 <span data-ttu-id="758ac-123">Cet exemple de code génère l’assembly csman_an_assembly en faisant référence à l’assembly et au fichier .netmodule générés précédemment.</span><span class="sxs-lookup"><span data-stu-id="758ac-123">This code sample builds the assembly csman_an_assembly, referencing the previously-built assembly and .netmodule.</span></span>  
  
```csharp  
// csman_an_assembly.cs  
// compile with: -addmodule:moduleassemblyname_2.netmodule -reference:moduleassemblyname_1.dll  
class A {  
    public static void Main() {  
        B bb = new B();  
        bb.Test();  
    }  
}  
```  
  
<span data-ttu-id="758ac-124">**An_Internal_Class.Test called**</span><span class="sxs-lookup"><span data-stu-id="758ac-124">**An_Internal_Class.Test called**</span></span>

## <a name="see-also"></a><span data-ttu-id="758ac-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="758ac-125">See also</span></span>

- [<span data-ttu-id="758ac-126">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="758ac-126">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="758ac-127">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="758ac-127">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
