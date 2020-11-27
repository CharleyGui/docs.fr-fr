---
title: Global Assembly Cache
description: Comprendre le Global Assembly Cache, qui est un cache de code à l’ensemble de l’ordinateur où le common language runtime pour .NET est installé.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache)
- ACLs [.NET Framework]
- global assembly cache
- cache [.NET Framework], global assembly cache
- global assembly cache, about
- access control lists [.NET Framework]
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
ms.openlocfilehash: 57d18c01bd6261e8207d8ad3849a3a7da9a24b6c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96264606"
---
# <a name="global-assembly-cache"></a><span data-ttu-id="01696-103">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="01696-103">Global Assembly Cache</span></span>

<span data-ttu-id="01696-104">Sur chaque ordinateur où le Common Language Runtime est installé, il y a un cache de code machine appelé Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="01696-104">Each computer where the Common Language Runtime is installed has a machine-wide code cache called the Global Assembly Cache.</span></span> <span data-ttu-id="01696-105">Le Global Assembly Cache stocke des assemblys spécialement destinés à être partagés entre plusieurs applications sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="01696-105">The Global Assembly Cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span>  
  
 <span data-ttu-id="01696-106">Partagez des assemblys en les installant dans le Global Assembly Cache uniquement si cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="01696-106">You should share assemblies by installing them into the Global Assembly Cache only when you need to.</span></span> <span data-ttu-id="01696-107">En règle générale, vous devez maintenir les dépendances d’assembly privées et rechercher les assemblys dans le répertoire de l’application, sauf si le partage d’un assembly est explicitement requis.</span><span class="sxs-lookup"><span data-stu-id="01696-107">As a general guideline, keep assembly dependencies private, and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="01696-108">De plus, il n’est pas nécessaire d’installer des assemblys dans le Global Assembly Cache pour les rendre accessibles à COM Interop ou au code non managé.</span><span class="sxs-lookup"><span data-stu-id="01696-108">In addition, it is not necessary to install assemblies into the Global Assembly Cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01696-109">Dans certains scénarios, vous ne devez pas installer d’assembly dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="01696-109">There are scenarios where you explicitly do not want to install an assembly into the Global Assembly Cache.</span></span> <span data-ttu-id="01696-110">Si vous placez l’un des assemblys composant une application dans le Global Assembly Cache, vous ne pouvez plus répliquer ni installer l’application en utilisant la commande **xcopy** pour copier le répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="01696-110">If you place one of the assemblies that make up an application in the Global Assembly Cache, you can no longer replicate or install the application by using the **xcopy** command to copy the application directory.</span></span> <span data-ttu-id="01696-111">Vous devez également déplacer l’assembly dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="01696-111">You must move the assembly in the Global Assembly Cache as well.</span></span>  
  
 <span data-ttu-id="01696-112">Il existe deux manières de déployer un assembly dans le Global Assembly Cache :</span><span class="sxs-lookup"><span data-stu-id="01696-112">There are two ways to deploy an assembly into the Global Assembly Cache:</span></span>  
  
- <span data-ttu-id="01696-113">Utiliser un programme d’installation conçu pour fonctionner avec le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="01696-113">Use an installer designed to work with the Global Assembly Cache.</span></span> <span data-ttu-id="01696-114">Il s’agit de l’option par défaut d’installation des assemblys dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="01696-114">This is the preferred option for installing assemblies into the Global Assembly Cache.</span></span>  
  
- <span data-ttu-id="01696-115">Utiliser un outil de développement appelé [Outil Global Assembly Cache (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) fourni par le SDK Windows.</span><span class="sxs-lookup"><span data-stu-id="01696-115">Use a developer tool called the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md), provided by the Windows SDK.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="01696-116">Dans les scénarios de déploiement, utilisez Windows Installer pour installer des assemblys dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="01696-116">In deployment scenarios, use Windows Installer to install assemblies into the Global Assembly Cache.</span></span> <span data-ttu-id="01696-117">Utilisez l’outil Global Assembly Cache uniquement dans les scénarios de développement, car il ne propose pas de fonctionnalités de décompte des références d’assembly et d’autres fonctionnalités disponibles lors de l’utilisation de Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="01696-117">Use the Global Assembly Cache tool only in development scenarios, because it does not provide assembly reference counting and other features provided when using the Windows Installer.</span></span>  
  
 <span data-ttu-id="01696-118">À compter du .NET Framework 4, l’emplacement par défaut du Global Assembly Cache est **%windir%\Microsoft.NET\assembly**.</span><span class="sxs-lookup"><span data-stu-id="01696-118">Starting with the .NET Framework 4, the default location for the Global Assembly Cache is **%windir%\Microsoft.NET\assembly**.</span></span> <span data-ttu-id="01696-119">Dans les versions antérieures du .NET Framework, l’emplacement par défaut est **%windir%\assembly**.</span><span class="sxs-lookup"><span data-stu-id="01696-119">In earlier versions of the .NET Framework, the default location is **%windir%\assembly**.</span></span>  
  
 <span data-ttu-id="01696-120">Les administrateurs protègent souvent le répertoire systemroot en utilisant une liste de contrôle d’accès pour contrôler l’accès en écriture et en exécution.</span><span class="sxs-lookup"><span data-stu-id="01696-120">Administrators often protect the systemroot directory using an access control list (ACL) to control write and execute access.</span></span> <span data-ttu-id="01696-121">Le Global Assembly Cache étant installé dans un sous-répertoire du répertoire systemroot, il hérite de la liste ACL de ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="01696-121">Because the Global Assembly Cache is installed in a subdirectory of the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="01696-122">Il est recommandé que seuls les utilisateurs ayant des privilèges d’administrateur soient autorisés à supprimer des fichiers du Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="01696-122">It is recommended that only users with Administrator privileges be allowed to delete files from the Global Assembly Cache.</span></span>  
  
 <span data-ttu-id="01696-123">Les assemblys déployés dans le Global Assembly Cache doivent avoir un nom fort.</span><span class="sxs-lookup"><span data-stu-id="01696-123">Assemblies deployed in the Global Assembly Cache must have a strong name.</span></span> <span data-ttu-id="01696-124">Quand un assembly est ajouté au Global Assembly Cache, des contrôles d’intégrité sont effectués sur tous les fichiers qui composent l’assembly.</span><span class="sxs-lookup"><span data-stu-id="01696-124">When an assembly is added to the Global Assembly Cache, integrity checks are performed on all files that make up the assembly.</span></span> <span data-ttu-id="01696-125">Le cache effectue ces contrôles d’intégrité pour vérifier qu’aucun assembly n’a été falsifié, par exemple quand un fichier a changé mais que le manifeste ne reflète pas ce changement.</span><span class="sxs-lookup"><span data-stu-id="01696-125">The cache performs these integrity checks to ensure that an assembly has not been tampered with, for example, when a file has changed but the manifest does not reflect the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01696-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01696-126">See also</span></span>

- [<span data-ttu-id="01696-127">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="01696-127">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="01696-128">Utilisation d'assemblys et du Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="01696-128">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="01696-129">Assemblys avec nom fort</span><span class="sxs-lookup"><span data-stu-id="01696-129">Strong-Named Assemblies</span></span>](../../standard/assembly/strong-named.md)
