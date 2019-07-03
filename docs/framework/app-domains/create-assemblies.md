---
title: Création d'assemblys
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e544976b0b801b08af238b2aeb36b5611154379
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832900"
---
# <a name="creating-assemblies"></a><span data-ttu-id="30c2b-102">Création d'assemblys</span><span class="sxs-lookup"><span data-stu-id="30c2b-102">Creating Assemblies</span></span>

<span data-ttu-id="30c2b-103">Vous pouvez créer des assemblys monofichiers ou multifichiers à l’aide d’un IDE, comme Visual Studio, ou des compilateurs et des outils fournis par le kit de développement logiciel (SDK) Windows.</span><span class="sxs-lookup"><span data-stu-id="30c2b-103">You can create single-file or multifile assemblies using an IDE, such as Visual Studio, or the compilers and tools provided by the Windows Software Development Kit (SDK).</span></span> <span data-ttu-id="30c2b-104">L’assembly le plus simple est un fichier unique qui a un nom simple et qui est chargé dans un seul domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="30c2b-104">The simplest assembly is a single file that has a simple name and is loaded into a single application domain.</span></span> <span data-ttu-id="30c2b-105">Cet assembly ne peut pas être référencé par d’autres assemblys en dehors du répertoire de l’application et n’est pas soumis à la vérification de la version.</span><span class="sxs-lookup"><span data-stu-id="30c2b-105">This assembly cannot be referenced by other assemblies outside the application directory and does not undergo version checking.</span></span> <span data-ttu-id="30c2b-106">Pour désinstaller l’application constituée de l’assembly, vous supprimez simplement le répertoire où il se trouve.</span><span class="sxs-lookup"><span data-stu-id="30c2b-106">To uninstall the application made up of the assembly, you simply delete the directory where it resides.</span></span> <span data-ttu-id="30c2b-107">Pour de nombreux développeurs, un assembly avec ces fonctionnalités est tout ce qui est nécessaire pour déployer une application.</span><span class="sxs-lookup"><span data-stu-id="30c2b-107">For many developers, an assembly with these features is all that is needed to deploy an application.</span></span>

<span data-ttu-id="30c2b-108">Vous pouvez créer un assembly multifichier à partir de plusieurs modules de code et fichiers de ressources.</span><span class="sxs-lookup"><span data-stu-id="30c2b-108">You can create a multifile assembly from several code modules and resource files.</span></span> <span data-ttu-id="30c2b-109">Vous pouvez également créer un assembly qui peut être partagé par plusieurs applications.</span><span class="sxs-lookup"><span data-stu-id="30c2b-109">You can also create an assembly that can be shared by multiple applications.</span></span> <span data-ttu-id="30c2b-110">Un assembly partagé doit avoir un nom fort et peut être déployé dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="30c2b-110">A shared assembly must have a strong name and can be deployed in the global assembly cache.</span></span>

<span data-ttu-id="30c2b-111">Vous disposez de plusieurs options quand vous regroupez des modules de code et des ressources dans des assemblys, en fonction des facteurs suivants :</span><span class="sxs-lookup"><span data-stu-id="30c2b-111">You have several options when grouping code modules and resources into assemblies, depending on the following factors:</span></span>

- <span data-ttu-id="30c2b-112">Gestion de version</span><span class="sxs-lookup"><span data-stu-id="30c2b-112">Versioning</span></span>

     <span data-ttu-id="30c2b-113">Regroupez les modules qui doivent avoir les mêmes informations de version.</span><span class="sxs-lookup"><span data-stu-id="30c2b-113">Group modules that should have the same version information.</span></span>

- <span data-ttu-id="30c2b-114">Déploiement</span><span class="sxs-lookup"><span data-stu-id="30c2b-114">Deployment</span></span>

     <span data-ttu-id="30c2b-115">Regroupez les modules de code et les ressources qui prennent en charge votre modèle de déploiement.</span><span class="sxs-lookup"><span data-stu-id="30c2b-115">Group code modules and resources that support your model of deployment.</span></span>

- <span data-ttu-id="30c2b-116">Réutilisation</span><span class="sxs-lookup"><span data-stu-id="30c2b-116">Reuse</span></span>

     <span data-ttu-id="30c2b-117">Regroupez les modules s’ils peuvent être logiquement utilisés ensemble dans le même but.</span><span class="sxs-lookup"><span data-stu-id="30c2b-117">Group modules if they can be logically used together for some purpose.</span></span> <span data-ttu-id="30c2b-118">Par exemple, un assembly constitué de types et de classes peu utilisés pour la maintenance du programme peut être placé dans le même assembly.</span><span class="sxs-lookup"><span data-stu-id="30c2b-118">For example, an assembly consisting of types and classes used infrequently for program maintenance can be put in the same assembly.</span></span> <span data-ttu-id="30c2b-119">En outre, les types que vous prévoyez de partager avec plusieurs applications doivent être regroupés dans un assembly, et celui-ci doit être signé avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="30c2b-119">In addition, types that you intend to share with multiple applications should be grouped into an assembly and the assembly should be signed with a strong name.</span></span>

- <span data-ttu-id="30c2b-120">Sécurité</span><span class="sxs-lookup"><span data-stu-id="30c2b-120">Security</span></span>

     <span data-ttu-id="30c2b-121">Regroupez les modules contenant des types qui nécessitent les mêmes autorisations de sécurité.</span><span class="sxs-lookup"><span data-stu-id="30c2b-121">Group modules containing types that require the same security permissions.</span></span>

- <span data-ttu-id="30c2b-122">Portée</span><span class="sxs-lookup"><span data-stu-id="30c2b-122">Scoping</span></span>

     <span data-ttu-id="30c2b-123">Regroupez les modules contenant des types dont la visibilité doit être limitée au même assembly.</span><span class="sxs-lookup"><span data-stu-id="30c2b-123">Group modules containing types whose visibility should be restricted to the same assembly.</span></span>

<span data-ttu-id="30c2b-124">Des considérations particulières sont à prendre en compte quand des assemblys du common language runtime sont rendus disponibles pour des applications COM non managées.</span><span class="sxs-lookup"><span data-stu-id="30c2b-124">Special considerations must be made when making common language runtime assemblies available to unmanaged COM applications.</span></span> <span data-ttu-id="30c2b-125">Pour plus d’informations sur l’utilisation de code non managé, consultez [Exposition de composants .NET Framework à COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).</span><span class="sxs-lookup"><span data-stu-id="30c2b-125">For more information about working with unmanaged code, see [Exposing .NET Framework Components to COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="30c2b-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30c2b-126">See also</span></span>

- [<span data-ttu-id="30c2b-127">Programmation à l’aide d’assemblys</span><span class="sxs-lookup"><span data-stu-id="30c2b-127">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="30c2b-128">Contrôle de version des assemblys</span><span class="sxs-lookup"><span data-stu-id="30c2b-128">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)
- [<span data-ttu-id="30c2b-129">Guide pratique pour générer un assembly à fichier unique</span><span class="sxs-lookup"><span data-stu-id="30c2b-129">How to: Build a Single-File Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)
- [<span data-ttu-id="30c2b-130">Guide pratique pour générer un assembly multifichier</span><span class="sxs-lookup"><span data-stu-id="30c2b-130">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [<span data-ttu-id="30c2b-131">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="30c2b-131">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="30c2b-132">Assemblys multifichiers</span><span class="sxs-lookup"><span data-stu-id="30c2b-132">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)
