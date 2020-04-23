---
title: Assemblys multifichiers
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
ms.openlocfilehash: 2a70e45d50763cf99c55cf08600c3c816b4043b7
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644217"
---
# <a name="multifile-assemblies"></a><span data-ttu-id="e6778-102">Assemblys multifichiers</span><span class="sxs-lookup"><span data-stu-id="e6778-102">Multifile assemblies</span></span>

<span data-ttu-id="e6778-103">Vous pouvez créer des assemblys multifichiers qui ciblent le .NET Framework à l’aide de compilateurs de ligne de commande ou de Visual Studio avec Visual C++.</span><span class="sxs-lookup"><span data-stu-id="e6778-103">You can create multifile assemblies that target the .NET Framework using command-line compilers or Visual Studio with Visual C++.</span></span> <span data-ttu-id="e6778-104">L’un des fichiers de l’assembly doit contenir le manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="e6778-104">One file in the assembly must contain the assembly manifest.</span></span> <span data-ttu-id="e6778-105">Un assembly qui démarre une application doit également contenir un point d’entrée, tel `Main` qu' `WinMain` une méthode ou.</span><span class="sxs-lookup"><span data-stu-id="e6778-105">An assembly that starts an application must also contain an entry point, such as a `Main` or `WinMain` method.</span></span>

<span data-ttu-id="e6778-106">Par exemple, supposons que vous avez une application qui contient deux modules de code, *client.cs* et *Stringer.cs*.</span><span class="sxs-lookup"><span data-stu-id="e6778-106">For example, suppose you have an application that contains two code modules, *Client.cs* and *Stringer.cs*.</span></span> <span data-ttu-id="e6778-107">*Stringer.cs* crée l' `myStringer` espace de noms qui est référencé par le code dans *client.cs*.</span><span class="sxs-lookup"><span data-stu-id="e6778-107">*Stringer.cs* creates the `myStringer` namespace that is referenced by the code in *Client.cs*.</span></span> <span data-ttu-id="e6778-108">*Client.cs* contient la `Main` méthode, qui est le point d’entrée de l’application.</span><span class="sxs-lookup"><span data-stu-id="e6778-108">*Client.cs* contains the `Main` method, which is the application's entry point.</span></span> <span data-ttu-id="e6778-109">Dans cet exemple, vous compilez les deux modules de code, puis créez un troisième fichier qui contient le manifeste d’assembly, qui lance l’application.</span><span class="sxs-lookup"><span data-stu-id="e6778-109">In this example, you compile the two code modules, and then create a third file that contains the assembly manifest, which launches the application.</span></span> <span data-ttu-id="e6778-110">Le manifeste de l’assembly fait référence aux modules *client* et *Stringer* .</span><span class="sxs-lookup"><span data-stu-id="e6778-110">The assembly manifest references both the *Client* and *Stringer* modules.</span></span>

> [!NOTE]
> <span data-ttu-id="e6778-111">Les assemblys multifichiers ne peuvent avoir qu’un seul point d’entrée, même si l’assembly a plusieurs modules de code.</span><span class="sxs-lookup"><span data-stu-id="e6778-111">Multifile assemblies can have only one entry point, even if the assembly has multiple code modules.</span></span>

<span data-ttu-id="e6778-112">Il est possible de créer un assembly multifichier pour plusieurs raisons :</span><span class="sxs-lookup"><span data-stu-id="e6778-112">There are several reasons you might want to create a multifile assembly:</span></span>

- <span data-ttu-id="e6778-113">Pour combiner des modules écrits dans différents langages.</span><span class="sxs-lookup"><span data-stu-id="e6778-113">To combine modules written in different languages.</span></span> <span data-ttu-id="e6778-114">Il s’agit de la raison la plus courante de créer un assembly multifichier.</span><span class="sxs-lookup"><span data-stu-id="e6778-114">This is the most common reason for creating a multifile assembly.</span></span>

- <span data-ttu-id="e6778-115">Pour optimiser le téléchargement d’une application en plaçant des types rarement utilisés dans un module qui n’est téléchargé que si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="e6778-115">To optimize downloading an application by putting seldom-used types in a module that is downloaded only when needed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e6778-116">Si vous créez des applications destinées à être téléchargées à l’aide de la balise `<object>` avec Microsoft Internet Explorer, il est important de créer des assemblys multifichiers.</span><span class="sxs-lookup"><span data-stu-id="e6778-116">If you are creating applications that will be downloaded using the `<object>` tag with Microsoft Internet Explorer, it is important that you create multifile assemblies.</span></span> <span data-ttu-id="e6778-117">Dans ce scénario, vous créez un fichier distinct de vos modules de code, qui contient uniquement le manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="e6778-117">In this scenario, you create a file separate from your code modules that contains only the assembly manifest.</span></span> <span data-ttu-id="e6778-118">Internet Explorer télécharge d’abord le manifeste d’assembly, puis crée des threads de travail pour télécharger tout assembly ou module supplémentaire requis.</span><span class="sxs-lookup"><span data-stu-id="e6778-118">Internet Explorer downloads the assembly manifest first, and then creates worker threads to download any additional modules or assemblies required.</span></span> <span data-ttu-id="e6778-119">Pendant le téléchargement du fichier contenant le manifeste d’assembly, Internet Explorer ne répond pas aux entrées d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e6778-119">While the file containing the assembly manifest is being downloaded, Internet Explorer will be unresponsive to user input.</span></span> <span data-ttu-id="e6778-120">La durée de non-réponse d’Internet Explorer est proportionnelle à la taille du fichier contenant le manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="e6778-120">The smaller the file containing the assembly manifest, the less time Internet Explorer will be unresponsive.</span></span>

- <span data-ttu-id="e6778-121">Pour combiner des modules de code écrits par plusieurs développeurs.</span><span class="sxs-lookup"><span data-stu-id="e6778-121">To combine code modules written by several developers.</span></span> <span data-ttu-id="e6778-122">Même si chaque développeur peut compiler chaque module de code dans un assembly, ceci peut forcer l’exposition publique de certains types qui ne sont pas exposés si tous les modules sont placés dans un assembly multifichier.</span><span class="sxs-lookup"><span data-stu-id="e6778-122">Although each developer can compile each code module into an assembly, this can force some types to be exposed publicly that are not exposed if all modules are put into a multifile assembly.</span></span>

<span data-ttu-id="e6778-123">Une fois que vous avez créé l’assembly, vous pouvez signer le fichier qui contient le manifeste de l’assembly, par conséquent l’assembly, ou vous pouvez attribuer un nom fort au fichier et à l’assembly et le placer dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="e6778-123">Once you create the assembly, you can sign the file that contains the assembly manifest, and hence the assembly, or you can give the file and the assembly a strong name and put it in the global assembly cache.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6778-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6778-124">See also</span></span>

- [<span data-ttu-id="e6778-125">Comment : générer un assembly multifichier</span><span class="sxs-lookup"><span data-stu-id="e6778-125">How to: Build a multifile assembly</span></span>](build-multifile-assembly.md)
- [<span data-ttu-id="e6778-126">Programmer avec des assemblys</span><span class="sxs-lookup"><span data-stu-id="e6778-126">Program with assemblies</span></span>](../../standard/assembly/index.md)
