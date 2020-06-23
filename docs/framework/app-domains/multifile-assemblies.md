---
title: Assemblys multifichiers
description: Utilisez des assemblys multifichiers ciblant .NET à l’aide de compilateurs de ligne de commande ou de Visual Studio avec Visual C++. Un fichier de l’assembly doit contenir le manifeste de l’assembly.
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
ms.openlocfilehash: a5fb41b3b136a325e6b8658da521cba3176e929f
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104640"
---
# <a name="multifile-assemblies"></a><span data-ttu-id="98bc0-104">Assemblys multifichiers</span><span class="sxs-lookup"><span data-stu-id="98bc0-104">Multifile assemblies</span></span>

<span data-ttu-id="98bc0-105">Vous pouvez créer des assemblys multifichiers qui ciblent le .NET Framework à l’aide de compilateurs de ligne de commande ou de Visual Studio avec Visual C++.</span><span class="sxs-lookup"><span data-stu-id="98bc0-105">You can create multifile assemblies that target the .NET Framework using command-line compilers or Visual Studio with Visual C++.</span></span> <span data-ttu-id="98bc0-106">L’un des fichiers de l’assembly doit contenir le manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="98bc0-106">One file in the assembly must contain the assembly manifest.</span></span> <span data-ttu-id="98bc0-107">Un assembly qui démarre une application doit également contenir un point d’entrée, tel qu’une `Main` `WinMain` méthode ou.</span><span class="sxs-lookup"><span data-stu-id="98bc0-107">An assembly that starts an application must also contain an entry point, such as a `Main` or `WinMain` method.</span></span>

<span data-ttu-id="98bc0-108">Par exemple, supposons que vous avez une application qui contient deux modules de code, *client.cs* et *Stringer.cs*.</span><span class="sxs-lookup"><span data-stu-id="98bc0-108">For example, suppose you have an application that contains two code modules, *Client.cs* and *Stringer.cs*.</span></span> <span data-ttu-id="98bc0-109">*Stringer.cs* crée l' `myStringer` espace de noms qui est référencé par le code dans *client.cs*.</span><span class="sxs-lookup"><span data-stu-id="98bc0-109">*Stringer.cs* creates the `myStringer` namespace that is referenced by the code in *Client.cs*.</span></span> <span data-ttu-id="98bc0-110">*Client.cs* contient la `Main` méthode, qui est le point d’entrée de l’application.</span><span class="sxs-lookup"><span data-stu-id="98bc0-110">*Client.cs* contains the `Main` method, which is the application's entry point.</span></span> <span data-ttu-id="98bc0-111">Dans cet exemple, vous compilez les deux modules de code, puis créez un troisième fichier qui contient le manifeste d’assembly, qui lance l’application.</span><span class="sxs-lookup"><span data-stu-id="98bc0-111">In this example, you compile the two code modules, and then create a third file that contains the assembly manifest, which launches the application.</span></span> <span data-ttu-id="98bc0-112">Le manifeste de l’assembly fait référence aux modules *client* et *Stringer* .</span><span class="sxs-lookup"><span data-stu-id="98bc0-112">The assembly manifest references both the *Client* and *Stringer* modules.</span></span>

> [!NOTE]
> <span data-ttu-id="98bc0-113">Les assemblys multifichiers ne peuvent avoir qu’un seul point d’entrée, même si l’assembly a plusieurs modules de code.</span><span class="sxs-lookup"><span data-stu-id="98bc0-113">Multifile assemblies can have only one entry point, even if the assembly has multiple code modules.</span></span>

<span data-ttu-id="98bc0-114">Il est possible de créer un assembly multifichier pour plusieurs raisons :</span><span class="sxs-lookup"><span data-stu-id="98bc0-114">There are several reasons you might want to create a multifile assembly:</span></span>

- <span data-ttu-id="98bc0-115">Pour combiner des modules écrits dans différents langages.</span><span class="sxs-lookup"><span data-stu-id="98bc0-115">To combine modules written in different languages.</span></span> <span data-ttu-id="98bc0-116">Il s’agit de la raison la plus courante de créer un assembly multifichier.</span><span class="sxs-lookup"><span data-stu-id="98bc0-116">This is the most common reason for creating a multifile assembly.</span></span>

- <span data-ttu-id="98bc0-117">Pour optimiser le téléchargement d’une application en plaçant des types rarement utilisés dans un module qui n’est téléchargé que si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="98bc0-117">To optimize downloading an application by putting seldom-used types in a module that is downloaded only when needed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="98bc0-118">Si vous créez des applications destinées à être téléchargées à l’aide de la balise `<object>` avec Microsoft Internet Explorer, il est important de créer des assemblys multifichiers.</span><span class="sxs-lookup"><span data-stu-id="98bc0-118">If you are creating applications that will be downloaded using the `<object>` tag with Microsoft Internet Explorer, it is important that you create multifile assemblies.</span></span> <span data-ttu-id="98bc0-119">Dans ce scénario, vous créez un fichier distinct de vos modules de code, qui contient uniquement le manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="98bc0-119">In this scenario, you create a file separate from your code modules that contains only the assembly manifest.</span></span> <span data-ttu-id="98bc0-120">Internet Explorer télécharge d’abord le manifeste d’assembly, puis crée des threads de travail pour télécharger tout assembly ou module supplémentaire requis.</span><span class="sxs-lookup"><span data-stu-id="98bc0-120">Internet Explorer downloads the assembly manifest first, and then creates worker threads to download any additional modules or assemblies required.</span></span> <span data-ttu-id="98bc0-121">Pendant le téléchargement du fichier contenant le manifeste d’assembly, Internet Explorer ne répond pas aux entrées d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="98bc0-121">While the file containing the assembly manifest is being downloaded, Internet Explorer will be unresponsive to user input.</span></span> <span data-ttu-id="98bc0-122">La durée de non-réponse d’Internet Explorer est proportionnelle à la taille du fichier contenant le manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="98bc0-122">The smaller the file containing the assembly manifest, the less time Internet Explorer will be unresponsive.</span></span>

- <span data-ttu-id="98bc0-123">Pour combiner des modules de code écrits par plusieurs développeurs.</span><span class="sxs-lookup"><span data-stu-id="98bc0-123">To combine code modules written by several developers.</span></span> <span data-ttu-id="98bc0-124">Même si chaque développeur peut compiler chaque module de code dans un assembly, ceci peut forcer l’exposition publique de certains types qui ne sont pas exposés si tous les modules sont placés dans un assembly multifichier.</span><span class="sxs-lookup"><span data-stu-id="98bc0-124">Although each developer can compile each code module into an assembly, this can force some types to be exposed publicly that are not exposed if all modules are put into a multifile assembly.</span></span>

<span data-ttu-id="98bc0-125">Une fois que vous avez créé l’assembly, vous pouvez signer le fichier qui contient le manifeste de l’assembly, par conséquent l’assembly, ou vous pouvez attribuer un nom fort au fichier et à l’assembly et le placer dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="98bc0-125">Once you create the assembly, you can sign the file that contains the assembly manifest, and hence the assembly, or you can give the file and the assembly a strong name and put it in the global assembly cache.</span></span>

## <a name="see-also"></a><span data-ttu-id="98bc0-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98bc0-126">See also</span></span>

- [<span data-ttu-id="98bc0-127">Procédure : Générer un assembly multifichier</span><span class="sxs-lookup"><span data-stu-id="98bc0-127">How to: Build a multifile assembly</span></span>](build-multifile-assembly.md)
- [<span data-ttu-id="98bc0-128">Programmer avec des assemblys</span><span class="sxs-lookup"><span data-stu-id="98bc0-128">Program with assemblies</span></span>](../../standard/assembly/index.md)
