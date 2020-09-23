---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: 9fb9287f9472d4b33eff4cb601aff5eed370b2c0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91065565"
---
# <a name="-moduleassemblyname"></a><span data-ttu-id="3c7d3-102">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="3c7d3-102">-moduleassemblyname</span></span>

<span data-ttu-id="3c7d3-103">Spécifie le nom de l’assembly dont ce module doit faire partie.</span><span class="sxs-lookup"><span data-stu-id="3c7d3-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c7d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c7d3-104">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="3c7d3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3c7d3-105">Arguments</span></span>  
  
|<span data-ttu-id="3c7d3-106">Terme</span><span class="sxs-lookup"><span data-stu-id="3c7d3-106">Term</span></span>|<span data-ttu-id="3c7d3-107">Définition</span><span class="sxs-lookup"><span data-stu-id="3c7d3-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="3c7d3-108">Nom de l'assembly dont ce module fera partie.</span><span class="sxs-lookup"><span data-stu-id="3c7d3-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c7d3-109">Notes</span><span class="sxs-lookup"><span data-stu-id="3c7d3-109">Remarks</span></span>  

 <span data-ttu-id="3c7d3-110">Le compilateur traite l' `-moduleassemblyname` option uniquement si l' `-target:module` option a été spécifiée.</span><span class="sxs-lookup"><span data-stu-id="3c7d3-110">The compiler processes the `-moduleassemblyname` option only if the `-target:module` option has been specified.</span></span> <span data-ttu-id="3c7d3-111">Le compilateur crée alors un module.</span><span class="sxs-lookup"><span data-stu-id="3c7d3-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="3c7d3-112">Le module créé par le compilateur est valide uniquement pour l’assembly spécifié avec l' `-moduleassemblyname` option.</span><span class="sxs-lookup"><span data-stu-id="3c7d3-112">The module created by the compiler is valid only for the assembly specified with the `-moduleassemblyname` option.</span></span> <span data-ttu-id="3c7d3-113">Si vous placez le module dans un assembly différent, des erreurs d’exécution se produisent.</span><span class="sxs-lookup"><span data-stu-id="3c7d3-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="3c7d3-114">L' `-moduleassemblyname` option est requise uniquement lorsque les conditions suivantes sont remplies :</span><span class="sxs-lookup"><span data-stu-id="3c7d3-114">The `-moduleassemblyname` option is needed only when the following are true:</span></span>  
  
- <span data-ttu-id="3c7d3-115">Un type de données dans le module a besoin d’accéder à un `Friend` type dans un assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="3c7d3-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
- <span data-ttu-id="3c7d3-116">L’assembly référencé a accordé un accès d’assembly friend à l’assembly dans lequel le module sera généré.</span><span class="sxs-lookup"><span data-stu-id="3c7d3-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="3c7d3-117">Pour plus d’informations sur la création d’un module, consultez [-target (Visual Basic)](target.md).</span><span class="sxs-lookup"><span data-stu-id="3c7d3-117">For more information about creating a module, see [-target (Visual Basic)](target.md).</span></span> <span data-ttu-id="3c7d3-118">Pour plus d’informations sur les assemblys friend, consultez [assemblys friend](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="3c7d3-118">For more information about friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3c7d3-119">L' `-moduleassemblyname` option n’est pas disponible dans l’environnement de développement Visual Studio ; elle est disponible uniquement quand vous compilez à partir d’une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="3c7d3-119">The `-moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c7d3-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c7d3-120">See also</span></span>

- [<span data-ttu-id="3c7d3-121">Comment : générer un assembly multifichier</span><span class="sxs-lookup"><span data-stu-id="3c7d3-121">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/build-multifile-assembly.md)
- [<span data-ttu-id="3c7d3-122">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3c7d3-122">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="3c7d3-123">-cible (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c7d3-123">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="3c7d3-124">-main</span><span class="sxs-lookup"><span data-stu-id="3c7d3-124">-main</span></span>](main.md)
- [<span data-ttu-id="3c7d3-125">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c7d3-125">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="3c7d3-126">-addmodule</span><span class="sxs-lookup"><span data-stu-id="3c7d3-126">-addmodule</span></span>](addmodule.md)
- [<span data-ttu-id="3c7d3-127">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="3c7d3-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="3c7d3-128">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="3c7d3-128">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="3c7d3-129">Assemblys friend</span><span class="sxs-lookup"><span data-stu-id="3c7d3-129">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
