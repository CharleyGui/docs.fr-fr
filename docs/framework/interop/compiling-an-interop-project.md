---
title: Compilation d'un projet d'interopérabilité
ms.date: 03/30/2017
helpviewer_keywords:
- interoperation with unmanaged code, compiling
- COM interop, compiling
- exposing COM components to .NET Framework
- compiling interop projects
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4369ce9c9ce82ecdbf11d76f3b043778b8374d8b
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489757"
---
# <a name="compiling-an-interop-project"></a><span data-ttu-id="e121d-102">Compilation d'un projet d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="e121d-102">Compiling an Interop Project</span></span>

<span data-ttu-id="e121d-103">Les projets de COM Interop qui référencent un ou plusieurs assemblys contenant des types COM importés sont compilés comme tout autre projet managé.</span><span class="sxs-lookup"><span data-stu-id="e121d-103">COM interop projects that reference one or more assemblies containing imported COM types are compiled like any other managed project.</span></span> <span data-ttu-id="e121d-104">Vous pouvez référencer des assemblys d’interopérabilité dans un environnement de développement tel que Visual Studio, ou vous pouvez les référencer quand vous utilisez un compilateur de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="e121d-104">You can reference interop assemblies in a development environment such as Visual Studio, or you can reference them when you use a command-line compiler.</span></span> <span data-ttu-id="e121d-105">Dans les deux cas, l’assembly d’interopérabilité doit figurer dans le même répertoire que les autres fichiers projet pour que la compilation réussisse.</span><span class="sxs-lookup"><span data-stu-id="e121d-105">In either case, to compile properly, the interop assembly must be in the same directory as the other project files.</span></span>

 <span data-ttu-id="e121d-106">Il existe deux façons de référencer des assemblys d’interopérabilité :</span><span class="sxs-lookup"><span data-stu-id="e121d-106">There are two ways to reference interop assemblies:</span></span>

- <span data-ttu-id="e121d-107">En utilisant des types interop incorporés : Depuis .NET Framework 4 et Visual Studio 2010, vous pouvez indiquer au compilateur d’incorporer les informations de type à partir d’un assembly d’interopérabilité dans votre fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="e121d-107">Embedded interop types: Beginning with the .NET Framework 4 and Visual Studio 2010, you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="e121d-108">Il s'agit de la technique recommandée.</span><span class="sxs-lookup"><span data-stu-id="e121d-108">This is the recommended technique.</span></span>

- <span data-ttu-id="e121d-109">En déployant des assemblys d’interopérabilité : vous pouvez créer une référence standard à un assembly d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="e121d-109">Deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="e121d-110">Dans ce cas, l’assembly d’interopérabilité doit être déployé avec votre application.</span><span class="sxs-lookup"><span data-stu-id="e121d-110">In this case, the interop assembly must be deployed with your application.</span></span>

 <span data-ttu-id="e121d-111">Les différences entre ces deux techniques sont abordées de manière plus détaillée dans [Utilisation de types COM dans du code managé](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e121d-111">The differences between these two techniques are discussed in greater detail in [Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>

 <span data-ttu-id="e121d-112">L’incorporation des types interop avec Visual Studio est illustrée dans [Procédure pas à pas : Incorporation de types provenant d’assemblys managés dans Visual Studio (C#)](/docs/csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md) et [Procédure pas à pas : Incorporation de types provenant d’assemblys managés dans Visual Studio (Visual Basic)](/docs/visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="e121d-112">Embedding interop types with Visual Studio is demonstrated in [Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)](/docs/csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), and [Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)](/docs/visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md).</span></span>

 <span data-ttu-id="e121d-113">Pour référencer un assembly d’interopérabilité avec un compilateur de ligne de commande et pour incorporer des informations de type dans vos fichiers exécutables, utilisez le commutateur de compilateur [/link (Options du compilateur C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) ou [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) et spécifiez le nom de l’assembly d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="e121d-113">To reference an interop assembly with a command-line compiler and embed type information in your executables, use the [/link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or the [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler switch and specify the name of the interop assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="e121d-114">Les applications Visual C++ ne peuvent pas incorporer d’informations de type, mais elles peuvent interagir avec des applications ou des compléments qui le font.</span><span class="sxs-lookup"><span data-stu-id="e121d-114">Visual C++ applications cannot embed type information, but they can interoperate with applications or add-ins that do.</span></span>

 <span data-ttu-id="e121d-115">Pour compiler une application qui inclut un assembly PIA quand elle est déployée, utilisez le commutateur de compilateur **/reference** et spécifiez le nom de l’assembly d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="e121d-115">To compile an application that includes a primary interop assembly when it is deployed, use the **/reference** compiler switch and specify the name of the interop assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="e121d-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e121d-116">See also</span></span>

- [<span data-ttu-id="e121d-117">Exposition de composants COM au .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e121d-117">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="e121d-118">Indépendance du langage et composants indépendants du langage</span><span class="sxs-lookup"><span data-stu-id="e121d-118">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- <span data-ttu-id="e121d-119">[Utilisation de types COM dans du code managé](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e121d-119">[Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span></span>
- [<span data-ttu-id="e121d-120">Procédure pas à pas : Incorporation de types provenant d’assemblys managés dans Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="e121d-120">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>](/docs/csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)
- [<span data-ttu-id="e121d-121">Procédure pas à pas : Incorporation de types provenant d’assemblys managés dans Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e121d-121">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>](/docs/visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [<span data-ttu-id="e121d-122">Importation d'une bibliothèque de types sous la forme d'un assembly</span><span class="sxs-lookup"><span data-stu-id="e121d-122">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
