---
title: Créer des assemblys
ms.date: 08/19/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
ms.openlocfilehash: 81fffb2b2e1d56d6068bf6f663a13fad6968a383
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73740509"
---
# <a name="create-assemblies"></a><span data-ttu-id="1da49-102">Créer des assemblys</span><span class="sxs-lookup"><span data-stu-id="1da49-102">Create assemblies</span></span>

<span data-ttu-id="1da49-103">Vous pouvez créer des assemblys monofichiers ou multifichiers à l’aide d’un IDE, comme Visual Studio, ou des compilateurs et des outils fournis par le SDK Windows.</span><span class="sxs-lookup"><span data-stu-id="1da49-103">You can create single-file or multifile assemblies using an IDE, such as Visual Studio, or the compilers and tools provided by the Windows SDK.</span></span> <span data-ttu-id="1da49-104">L’assembly le plus simple est un fichier unique qui a un nom simple et qui est chargé dans un seul domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="1da49-104">The simplest assembly is a single file that has a simple name and is loaded into a single application domain.</span></span> <span data-ttu-id="1da49-105">Cet assembly ne peut pas être référencé par d’autres assemblys en dehors du répertoire de l’application et n’est pas soumis à la vérification de la version.</span><span class="sxs-lookup"><span data-stu-id="1da49-105">This assembly cannot be referenced by other assemblies outside the application directory and does not undergo version checking.</span></span> <span data-ttu-id="1da49-106">Pour désinstaller l’application constituée de l’assembly, vous supprimez simplement le répertoire où il se trouve.</span><span class="sxs-lookup"><span data-stu-id="1da49-106">To uninstall the application made up of the assembly, you simply delete the directory where it resides.</span></span> <span data-ttu-id="1da49-107">Pour de nombreux développeurs, un assembly avec ces fonctionnalités est tout ce qui est nécessaire pour déployer une application.</span><span class="sxs-lookup"><span data-stu-id="1da49-107">For many developers, an assembly with these features is all that is needed to deploy an application.</span></span>

<span data-ttu-id="1da49-108">Vous pouvez créer un assembly multifichier à partir de plusieurs modules de code et fichiers de ressources.</span><span class="sxs-lookup"><span data-stu-id="1da49-108">You can create a multifile assembly from several code modules and resource files.</span></span> <span data-ttu-id="1da49-109">Vous pouvez également créer un assembly qui peut être partagé par plusieurs applications.</span><span class="sxs-lookup"><span data-stu-id="1da49-109">You can also create an assembly that can be shared by multiple applications.</span></span> <span data-ttu-id="1da49-110">Un assembly partagé doit avoir un nom fort et peut être déployé dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="1da49-110">A shared assembly must have a strong name and can be deployed in the global assembly cache.</span></span>

<span data-ttu-id="1da49-111">Vous disposez de plusieurs options quand vous regroupez des modules de code et des ressources dans des assemblys, en fonction des facteurs suivants :</span><span class="sxs-lookup"><span data-stu-id="1da49-111">You have several options when grouping code modules and resources into assemblies, depending on the following factors:</span></span>

- <span data-ttu-id="1da49-112">Contrôle de version</span><span class="sxs-lookup"><span data-stu-id="1da49-112">Versioning</span></span>

     <span data-ttu-id="1da49-113">Regroupez les modules qui doivent avoir les mêmes informations de version.</span><span class="sxs-lookup"><span data-stu-id="1da49-113">Group modules that should have the same version information.</span></span>

- <span data-ttu-id="1da49-114">Déploiement</span><span class="sxs-lookup"><span data-stu-id="1da49-114">Deployment</span></span>

     <span data-ttu-id="1da49-115">Regroupez les modules de code et les ressources qui prennent en charge votre modèle de déploiement.</span><span class="sxs-lookup"><span data-stu-id="1da49-115">Group code modules and resources that support your model of deployment.</span></span>

- <span data-ttu-id="1da49-116">Réutilisation</span><span class="sxs-lookup"><span data-stu-id="1da49-116">Reuse</span></span>

     <span data-ttu-id="1da49-117">Regroupez les modules s’ils peuvent être logiquement utilisés ensemble dans le même but.</span><span class="sxs-lookup"><span data-stu-id="1da49-117">Group modules if they can be logically used together for some purpose.</span></span> <span data-ttu-id="1da49-118">Par exemple, un assembly constitué de types et de classes peu utilisés pour la maintenance du programme peut être placé dans le même assembly.</span><span class="sxs-lookup"><span data-stu-id="1da49-118">For example, an assembly consisting of types and classes used infrequently for program maintenance can be put in the same assembly.</span></span> <span data-ttu-id="1da49-119">En outre, les types que vous prévoyez de partager avec plusieurs applications doivent être regroupés dans un assembly, et celui-ci doit être signé avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="1da49-119">In addition, types that you intend to share with multiple applications should be grouped into an assembly and the assembly should be signed with a strong name.</span></span>

- <span data-ttu-id="1da49-120">Sécurité</span><span class="sxs-lookup"><span data-stu-id="1da49-120">Security</span></span>

     <span data-ttu-id="1da49-121">Regroupez les modules contenant des types qui nécessitent les mêmes autorisations de sécurité.</span><span class="sxs-lookup"><span data-stu-id="1da49-121">Group modules containing types that require the same security permissions.</span></span>

- <span data-ttu-id="1da49-122">Scoping</span><span class="sxs-lookup"><span data-stu-id="1da49-122">Scoping</span></span>

     <span data-ttu-id="1da49-123">Regroupez les modules contenant des types dont la visibilité doit être limitée au même assembly.</span><span class="sxs-lookup"><span data-stu-id="1da49-123">Group modules containing types whose visibility should be restricted to the same assembly.</span></span>

<span data-ttu-id="1da49-124">Il y a des considérations particulières lorsque l’on peut mettre des assemblages de temps d’exécution de langage commun à la disposition des applications COM non gérées.</span><span class="sxs-lookup"><span data-stu-id="1da49-124">There are special considerations when making common language runtime assemblies available to unmanaged COM applications.</span></span> <span data-ttu-id="1da49-125">Pour plus d’informations sur le travail avec le code non-gestion, voir [Expose .NET Composants cadre à COM](../../framework/interop/exposing-dotnet-components-to-com.md).</span><span class="sxs-lookup"><span data-stu-id="1da49-125">For more information about working with unmanaged code, see [Expose .NET Framework components to COM](../../framework/interop/exposing-dotnet-components-to-com.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1da49-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1da49-126">See also</span></span>

- [<span data-ttu-id="1da49-127">Contrôle de version des assemblys</span><span class="sxs-lookup"><span data-stu-id="1da49-127">Assembly versioning</span></span>](versioning.md)
- [<span data-ttu-id="1da49-128">Comment : Construire un assemblage à un seul fichier</span><span class="sxs-lookup"><span data-stu-id="1da49-128">How to: Build a single-file assembly</span></span>](../../framework/app-domains/build-single-file-assembly.md)
- [<span data-ttu-id="1da49-129">Comment : Construire un assemblage multifils</span><span class="sxs-lookup"><span data-stu-id="1da49-129">How to: Build a multifile assembly</span></span>](../../framework/app-domains/build-multifile-assembly.md)
- [<span data-ttu-id="1da49-130">Comment le temps d’exécution localise les assemblages</span><span class="sxs-lookup"><span data-stu-id="1da49-130">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="1da49-131">Assemblys multifichiers</span><span class="sxs-lookup"><span data-stu-id="1da49-131">Multifile assemblies</span></span>](../../framework/app-domains/multifile-assemblies.md)
