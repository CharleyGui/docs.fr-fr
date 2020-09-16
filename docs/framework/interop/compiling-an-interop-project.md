---
title: Compilation d'un projet d'interopérabilité
description: Examinez comment compiler un projet COM Interop, qui est compilé comme des projets managés s’ils font référence à un ou plusieurs assemblys contenant des types COM importés.
ms.date: 03/30/2017
helpviewer_keywords:
- interoperation with unmanaged code, compiling
- COM interop, compiling
- exposing COM components to .NET Framework
- compiling interop projects
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
ms.openlocfilehash: 1cf5bdbedd53227e812b0d2ed97778ab34a81444
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557095"
---
# <a name="compiling-an-interop-project"></a><span data-ttu-id="12409-103">Compilation d'un projet d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="12409-103">Compiling an Interop Project</span></span>

<span data-ttu-id="12409-104">Les projets de COM Interop qui référencent un ou plusieurs assemblys contenant des types COM importés sont compilés comme tout autre projet managé.</span><span class="sxs-lookup"><span data-stu-id="12409-104">COM interop projects that reference one or more assemblies containing imported COM types are compiled like any other managed project.</span></span> <span data-ttu-id="12409-105">Vous pouvez référencer des assemblys d’interopérabilité dans un environnement de développement tel que Visual Studio, ou vous pouvez les référencer quand vous utilisez un compilateur de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="12409-105">You can reference interop assemblies in a development environment such as Visual Studio, or you can reference them when you use a command-line compiler.</span></span> <span data-ttu-id="12409-106">Dans les deux cas, l’assembly d’interopérabilité doit figurer dans le même répertoire que les autres fichiers projet pour que la compilation réussisse.</span><span class="sxs-lookup"><span data-stu-id="12409-106">In either case, to compile properly, the interop assembly must be in the same directory as the other project files.</span></span>

 <span data-ttu-id="12409-107">Il existe deux façons de référencer des assemblys d’interopérabilité :</span><span class="sxs-lookup"><span data-stu-id="12409-107">There are two ways to reference interop assemblies:</span></span>

- <span data-ttu-id="12409-108">Types Interop incorporés : à partir de la .NET Framework 4 et de Visual Studio 2010, vous pouvez indiquer au compilateur d’incorporer les informations de type d’un assembly d’interopérabilité dans votre fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="12409-108">Embedded interop types: Beginning with the .NET Framework 4 and Visual Studio 2010, you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="12409-109">Il s’agit de la technique recommandée.</span><span class="sxs-lookup"><span data-stu-id="12409-109">This is the recommended technique.</span></span>

- <span data-ttu-id="12409-110">En déployant des assemblys d’interopérabilité : vous pouvez créer une référence standard à un assembly d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="12409-110">Deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="12409-111">Dans ce cas, l’assembly d’interopérabilité doit être déployé avec votre application.</span><span class="sxs-lookup"><span data-stu-id="12409-111">In this case, the interop assembly must be deployed with your application.</span></span>

 <span data-ttu-id="12409-112">Les différences entre ces deux techniques sont abordées de manière plus détaillée dans [Utilisation de types COM dans du code managé](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="12409-112">The differences between these two techniques are discussed in greater detail in [Using COM Types in Managed Code](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>

 <span data-ttu-id="12409-113">L’incorporation de types Interop à l’aide de Visual Studio est illustrée dans [procédure pas à pas : incorporation de types provenant d’assemblys managés dans Visual Studio](../../standard/assembly/embed-types-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="12409-113">Embedding interop types with Visual Studio is demonstrated in [Walkthrough: Embedding Types from Managed Assemblies in Visual Studio](../../standard/assembly/embed-types-visual-studio.md).</span></span>

 <span data-ttu-id="12409-114">Pour référencer un assembly d’interopérabilité à l’aide d’un compilateur de ligne de commande et incorporer des informations de type dans vos fichiers exécutables, utilisez les commutateurs [-Link (options du compilateur C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) ou [-Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) et spécifiez le nom de l’assembly d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="12409-114">To reference an interop assembly with a command-line compiler and embed type information in your executables, use the [-link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or the [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler switch and specify the name of the interop assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="12409-115">Les applications Visual C++ ne peuvent pas incorporer d’informations de type, mais elles peuvent interagir avec des applications ou des compléments qui le font.</span><span class="sxs-lookup"><span data-stu-id="12409-115">Visual C++ applications cannot embed type information, but they can interoperate with applications or add-ins that do.</span></span>

 <span data-ttu-id="12409-116">Pour compiler une application qui inclut un assembly PIA quand elle est déployée, utilisez le commutateur de compilateur **/reference** et spécifiez le nom de l’assembly d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="12409-116">To compile an application that includes a primary interop assembly when it is deployed, use the **/reference** compiler switch and specify the name of the interop assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="12409-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12409-117">See also</span></span>

- [<span data-ttu-id="12409-118">Exposition de composants COM au .NET Framework</span><span class="sxs-lookup"><span data-stu-id="12409-118">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="12409-119">Indépendance du langage et composants indépendants du langage</span><span class="sxs-lookup"><span data-stu-id="12409-119">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- <span data-ttu-id="12409-120">[Utiliser des types COM dans du code managé](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="12409-120">[Using COM Types in Managed Code](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span></span>
- [<span data-ttu-id="12409-121">Procédure pas à pas : incorporation de types provenant d’assemblys managés dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="12409-121">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio</span></span>](../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="12409-122">Importation d'une bibliothèque de types sous la forme d'un assembly</span><span class="sxs-lookup"><span data-stu-id="12409-122">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
