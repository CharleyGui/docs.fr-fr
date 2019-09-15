---
title: Programmer avec des assemblys
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03babe701b46eab54a76094c4728af80e6d9911e
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973137"
---
# <a name="program-with-assemblies"></a><span data-ttu-id="6f22a-102">Programmer avec des assemblys</span><span class="sxs-lookup"><span data-stu-id="6f22a-102">Program with assemblies</span></span>
<span data-ttu-id="6f22a-103">Les assemblys sont les éléments de base du .NET Framework. Ils forment l’unité fondamentale de déploiement, de gestion de version, de réutilisation, de portée d’activation et des autorisations de sécurité.</span><span class="sxs-lookup"><span data-stu-id="6f22a-103">Assemblies are the building blocks of the .NET Framework; they form the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions.</span></span> <span data-ttu-id="6f22a-104">Un assembly fournit au Common Language Runtime les informations dont il a besoin pour connaître les implémentations de type.</span><span class="sxs-lookup"><span data-stu-id="6f22a-104">An assembly provides the common language runtime with the information it needs to be aware of type implementations.</span></span> <span data-ttu-id="6f22a-105">Il s’agit d’une collection de types et de ressources conçus pour opérer ensemble et former une unité logique de fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="6f22a-105">It is a collection of types and resources that are built to work together and form a logical unit of functionality.</span></span> <span data-ttu-id="6f22a-106">Pour le runtime, un type n'existe pas en dehors du contexte d'un assembly.</span><span class="sxs-lookup"><span data-stu-id="6f22a-106">To the runtime, a type does not exist outside the context of an assembly.</span></span>  
  
 <span data-ttu-id="6f22a-107">Cette section explique comment créer des modules, comment créer des assemblys à partir de modules, comment créer une paire de clés et signer un assembly avec un nom fort, et comment installer un assembly dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="6f22a-107">This section describes how to create modules, create assemblies from modules, create a key pair and sign an assembly with a strong name, and install an assembly into the global assembly cache.</span></span> <span data-ttu-id="6f22a-108">Elle décrit également comment utiliser le [désassembleur MSIL (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) pour afficher les informations de manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="6f22a-108">In addition, this section describes how to use the [MSIL Disassembler (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) to view assembly manifest information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f22a-109">À compter du .NET Framework version 2.0, le runtime ne charge pas un assembly qui a été compilé avec une version du .NET Framework dont le numéro de version est supérieur au runtime actuellement chargé.</span><span class="sxs-lookup"><span data-stu-id="6f22a-109">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="6f22a-110">Cela s’applique à la combinaison des composants majeurs et mineurs du numéro de version.</span><span class="sxs-lookup"><span data-stu-id="6f22a-110">This applies to the combination of the major and minor components of the version number.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6f22a-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="6f22a-111">In this section</span></span>  
 [<span data-ttu-id="6f22a-112">Créer des assemblys</span><span class="sxs-lookup"><span data-stu-id="6f22a-112">Create assemblies</span></span>](create.md)  
 <span data-ttu-id="6f22a-113">Fournit une vue d'ensemble des assemblys multifichiers et à fichier unique.</span><span class="sxs-lookup"><span data-stu-id="6f22a-113">Provides an overview of single-file and multifile assemblies.</span></span>  
  
 [<span data-ttu-id="6f22a-114">Noms d’assemblys</span><span class="sxs-lookup"><span data-stu-id="6f22a-114">Assembly names</span></span>](names.md)  
 <span data-ttu-id="6f22a-115">Fournit une vue d’ensemble de l’affectation de noms à des assemblys.</span><span class="sxs-lookup"><span data-stu-id="6f22a-115">Provides an overview of assembly naming.</span></span>  
  
 [<span data-ttu-id="6f22a-116">Guide pratique pour Déterminer le nom qualifié complet d’un assembly</span><span class="sxs-lookup"><span data-stu-id="6f22a-116">How to: Determine an assembly's fully qualified name</span></span>](find-fully-qualified-name.md)  
 <span data-ttu-id="6f22a-117">Décrit comment déterminer le nom complet d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="6f22a-117">Describes how to determine the fully qualified name of an assembly.</span></span>  
  
 [<span data-ttu-id="6f22a-118">Exécuter des applications intranet en confiance totale</span><span class="sxs-lookup"><span data-stu-id="6f22a-118">Run intranet applications in full trust</span></span>](../../framework/app-domains/running-intranet-applications-in-full-trust.md)  
 <span data-ttu-id="6f22a-119">Décrit comment spécifier la stratégie de sécurité héritée pour les assemblys de confiance totale sur un partage intranet.</span><span class="sxs-lookup"><span data-stu-id="6f22a-119">Describes how to specify legacy security policy for full-trust assemblies on an intranet share.</span></span>  
  
 [<span data-ttu-id="6f22a-120">Emplacement de l’assembly</span><span class="sxs-lookup"><span data-stu-id="6f22a-120">Assembly location</span></span>](location.md)  
 <span data-ttu-id="6f22a-121">Offre une vue d’ensemble de l’emplacement des assemblys.</span><span class="sxs-lookup"><span data-stu-id="6f22a-121">Provides an overview of where to locate assemblies.</span></span>  
  
 [<span data-ttu-id="6f22a-122">Guide pratique : Créer un assembly à fichier unique</span><span class="sxs-lookup"><span data-stu-id="6f22a-122">How to: Build a single-file assembly</span></span>](../../framework/app-domains/build-single-file-assembly.md)  
 <span data-ttu-id="6f22a-123">Décrit comment créer un assembly à fichier unique.</span><span class="sxs-lookup"><span data-stu-id="6f22a-123">Describes how to create a single-file assembly.</span></span>  
  
 [<span data-ttu-id="6f22a-124">Assemblys multifichiers</span><span class="sxs-lookup"><span data-stu-id="6f22a-124">Multifile assemblies</span></span>](../../framework/app-domains/multifile-assemblies.md)  
 <span data-ttu-id="6f22a-125">Décrit les raisons justifiant la création d’assemblys multifichiers.</span><span class="sxs-lookup"><span data-stu-id="6f22a-125">Describes reasons for creating multifile assemblies.</span></span>  
  
 [<span data-ttu-id="6f22a-126">Guide pratique pour Créer un assembly multifichier</span><span class="sxs-lookup"><span data-stu-id="6f22a-126">How to: Build a multifile assembly</span></span>](../../framework/app-domains/build-multifile-assembly.md)  
 <span data-ttu-id="6f22a-127">Décrit comment créer un assembly multifichier.</span><span class="sxs-lookup"><span data-stu-id="6f22a-127">Describes how to create a multifile assembly.</span></span>  
  
 [<span data-ttu-id="6f22a-128">Définir des attributs d’assembly</span><span class="sxs-lookup"><span data-stu-id="6f22a-128">Set assembly attributes</span></span>](set-attributes.md)  
 <span data-ttu-id="6f22a-129">Décrit les attributs d’assembly et comment les définir.</span><span class="sxs-lookup"><span data-stu-id="6f22a-129">Describes assembly attributes and how to set them.</span></span>  
  
 [<span data-ttu-id="6f22a-130">Créer et utiliser des assemblys avec nom fort</span><span class="sxs-lookup"><span data-stu-id="6f22a-130">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)  
 <span data-ttu-id="6f22a-131">Explique comment et pourquoi signer un assembly avec un nom fort. Inclut des procédures.</span><span class="sxs-lookup"><span data-stu-id="6f22a-131">Describes how and why you sign an assembly with a strong name, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="6f22a-132">Temporiser la signature d’un assembly</span><span class="sxs-lookup"><span data-stu-id="6f22a-132">Delay-sign an assembly</span></span>](delay-sign.md)  
 <span data-ttu-id="6f22a-133">Décrit comment différer la signature d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="6f22a-133">Describes how to delay-sign an assembly.</span></span>  
  
 [<span data-ttu-id="6f22a-134">Utiliser des assemblys et le Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="6f22a-134">Work with assemblies and the global assembly cache</span></span>](../../framework/app-domains/working-with-assemblies-and-the-gac.md)  
 <span data-ttu-id="6f22a-135">Explique comment et pourquoi ajouter des assemblys au Global Assembly Cache. Inclut des procédures.</span><span class="sxs-lookup"><span data-stu-id="6f22a-135">Describes how and why you add assemblies to the global assembly cache, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="6f22a-136">Guide pratique pour Afficher le contenu de l’assembly</span><span class="sxs-lookup"><span data-stu-id="6f22a-136">How to: View assembly contents</span></span>](view-contents.md)  
 <span data-ttu-id="6f22a-137">Décrit comment utiliser le désassembleur MSIL (Ildasm.exe) pour afficher le contenu d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="6f22a-137">Describes how to use the MSIL Disassembler (Ildasm.exe) to view assembly contents.</span></span>  
  
 [<span data-ttu-id="6f22a-138">Transfert de type dans le common language runtime</span><span class="sxs-lookup"><span data-stu-id="6f22a-138">Type forwarding in the common language runtime</span></span>](type-forwarding.md)  
 <span data-ttu-id="6f22a-139">Décrit comment utiliser le transfert de type pour déplacer un type dans un assembly différent sans interrompre les applications existantes.</span><span class="sxs-lookup"><span data-stu-id="6f22a-139">Describes how to use type forwarding to move a type into a different assembly without breaking existing applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6f22a-140">Référence</span><span class="sxs-lookup"><span data-stu-id="6f22a-140">Reference</span></span>  
 <xref:System.Reflection.Assembly>  
 <span data-ttu-id="6f22a-141">Classe .NET Framework qui représente un assembly.</span><span class="sxs-lookup"><span data-stu-id="6f22a-141">The .NET Framework class that represents an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6f22a-142">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="6f22a-142">Related sections</span></span>  
 [<span data-ttu-id="6f22a-143">Guide pratique pour Obtenir des informations sur les types et les membres à partir d’un assembly</span><span class="sxs-lookup"><span data-stu-id="6f22a-143">How to: Obtain type and member information from an assembly</span></span>](../../framework/reflection-and-codedom/get-type-member-information.md)  
 <span data-ttu-id="6f22a-144">Décrit comment obtenir par programmation des informations relatives au type et à d’autres éléments à partir d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="6f22a-144">Describes how to programmatically obtain type and other information from an assembly.</span></span>  
  
 [<span data-ttu-id="6f22a-145">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="6f22a-145">Assemblies in .NET</span></span>](index.md)  
 <span data-ttu-id="6f22a-146">Offre une vue d’ensemble conceptuelle des assemblys du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="6f22a-146">Provides a conceptual overview of common language runtime assemblies.</span></span>  
  
 [<span data-ttu-id="6f22a-147">Contrôle de version des assemblys</span><span class="sxs-lookup"><span data-stu-id="6f22a-147">Assembly versioning</span></span>](versioning.md)  
 <span data-ttu-id="6f22a-148">Offre une vue d’ensemble de la liaison d’assembly et des attributs <xref:System.Reflection.AssemblyVersionAttribute> et <xref:System.Reflection.AssemblyInformationalVersionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="6f22a-148">Provides an overview of assembly binding and of the <xref:System.Reflection.AssemblyVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes.</span></span>  
  
 [<span data-ttu-id="6f22a-149">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="6f22a-149">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="6f22a-150">Décrit comment le runtime détermine l’assembly à utiliser pour répondre à une demande de liaison.</span><span class="sxs-lookup"><span data-stu-id="6f22a-150">Describes how the runtime determines which assembly to use to fulfill a binding request.</span></span>  
  
 <span data-ttu-id="6f22a-151">[Réflexion](../../framework/reflection-and-codedom/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="6f22a-151">[Reflection](../../framework/reflection-and-codedom/reflection.md) </span></span>  
 <span data-ttu-id="6f22a-152">Explique comment utiliser la classe **Reflection** pour obtenir des informations sur un assembly.</span><span class="sxs-lookup"><span data-stu-id="6f22a-152">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
