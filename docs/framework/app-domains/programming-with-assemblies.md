---
title: Programmation à l'aide d'assemblys
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f427e2260fb26be7db0a29c47f38a3cb32dd34e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921434"
---
# <a name="programming-with-assemblies"></a><span data-ttu-id="b74b0-102">Programmation à l'aide d'assemblys</span><span class="sxs-lookup"><span data-stu-id="b74b0-102">Programming with Assemblies</span></span>
<span data-ttu-id="b74b0-103">Les assemblys sont les éléments de base du .NET Framework. Ils forment l’unité fondamentale de déploiement, de gestion de version, de réutilisation, de portée d’activation et des autorisations de sécurité.</span><span class="sxs-lookup"><span data-stu-id="b74b0-103">Assemblies are the building blocks of the .NET Framework; they form the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions.</span></span> <span data-ttu-id="b74b0-104">Un assembly fournit au Common Language Runtime les informations dont il a besoin pour connaître les implémentations de type.</span><span class="sxs-lookup"><span data-stu-id="b74b0-104">An assembly provides the common language runtime with the information it needs to be aware of type implementations.</span></span> <span data-ttu-id="b74b0-105">Il s’agit d’une collection de types et de ressources conçus pour opérer ensemble et former une unité logique de fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="b74b0-105">It is a collection of types and resources that are built to work together and form a logical unit of functionality.</span></span> <span data-ttu-id="b74b0-106">Pour le runtime, un type n'existe pas en dehors du contexte d'un assembly.</span><span class="sxs-lookup"><span data-stu-id="b74b0-106">To the runtime, a type does not exist outside the context of an assembly.</span></span>  
  
 <span data-ttu-id="b74b0-107">Cette section explique comment créer des modules, comment créer des assemblys à partir de modules, comment créer une paire de clés et signer un assembly avec un nom fort, et comment installer un assembly dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="b74b0-107">This section describes how to create modules, create assemblies from modules, create a key pair and sign an assembly with a strong name, and install an assembly into the global assembly cache.</span></span> <span data-ttu-id="b74b0-108">Elle décrit également comment utiliser le [désassembleur MSIL (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) pour afficher les informations de manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="b74b0-108">In addition, this section describes how to use the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view assembly manifest information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b74b0-109">À compter du .NET Framework version 2.0, le runtime ne charge pas un assembly qui a été compilé avec une version du .NET Framework dont le numéro de version est supérieur au runtime actuellement chargé.</span><span class="sxs-lookup"><span data-stu-id="b74b0-109">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="b74b0-110">Cela s’applique à la combinaison des composants majeurs et mineurs du numéro de version.</span><span class="sxs-lookup"><span data-stu-id="b74b0-110">This applies to the combination of the major and minor components of the version number.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b74b0-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b74b0-111">In This Section</span></span>  
 [<span data-ttu-id="b74b0-112">Création d’assemblys</span><span class="sxs-lookup"><span data-stu-id="b74b0-112">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 <span data-ttu-id="b74b0-113">Fournit une vue d'ensemble des assemblys multifichiers et à fichier unique.</span><span class="sxs-lookup"><span data-stu-id="b74b0-113">Provides an overview of single-file and multifile assemblies.</span></span>  
  
 [<span data-ttu-id="b74b0-114">Noms d’assemblys</span><span class="sxs-lookup"><span data-stu-id="b74b0-114">Assembly Names</span></span>](../../../docs/framework/app-domains/assembly-names.md)  
 <span data-ttu-id="b74b0-115">Fournit une vue d’ensemble de l’affectation de noms à des assemblys.</span><span class="sxs-lookup"><span data-stu-id="b74b0-115">Provides an overview of assembly naming.</span></span>  
  
 [<span data-ttu-id="b74b0-116">Guide pratique pour déterminer le nom qualifié complet d’un assembly</span><span class="sxs-lookup"><span data-stu-id="b74b0-116">How to: Determine an Assembly's Fully Qualified Name</span></span>](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 <span data-ttu-id="b74b0-117">Décrit comment déterminer le nom complet d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="b74b0-117">Describes how to determine the fully qualified name of an assembly.</span></span>  
  
 [<span data-ttu-id="b74b0-118">Exécution d'applications intranet de confiance totale</span><span class="sxs-lookup"><span data-stu-id="b74b0-118">Running Intranet Applications in Full Trust</span></span>](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 <span data-ttu-id="b74b0-119">Décrit comment spécifier la stratégie de sécurité héritée pour les assemblys de confiance totale sur un partage intranet.</span><span class="sxs-lookup"><span data-stu-id="b74b0-119">Describes how to specify legacy security policy for full-trust assemblies on an intranet share.</span></span>  
  
 [<span data-ttu-id="b74b0-120">Emplacement de l'assembly</span><span class="sxs-lookup"><span data-stu-id="b74b0-120">Assembly Location</span></span>](../../../docs/framework/app-domains/assembly-location.md)  
 <span data-ttu-id="b74b0-121">Offre une vue d’ensemble de l’emplacement des assemblys.</span><span class="sxs-lookup"><span data-stu-id="b74b0-121">Provides an overview of where to locate assemblies.</span></span>  
  
 [<span data-ttu-id="b74b0-122">Guide pratique pour générer un assembly à fichier unique</span><span class="sxs-lookup"><span data-stu-id="b74b0-122">How to: Build a Single-File Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 <span data-ttu-id="b74b0-123">Décrit comment créer un assembly à fichier unique.</span><span class="sxs-lookup"><span data-stu-id="b74b0-123">Describes how to create a single-file assembly.</span></span>  
  
 [<span data-ttu-id="b74b0-124">Assemblys multifichiers</span><span class="sxs-lookup"><span data-stu-id="b74b0-124">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)  
 <span data-ttu-id="b74b0-125">Décrit les raisons justifiant la création d’assemblys multifichiers.</span><span class="sxs-lookup"><span data-stu-id="b74b0-125">Describes reasons for creating multifile assemblies.</span></span>  
  
 [<span data-ttu-id="b74b0-126">Guide pratique pour générer un assembly multifichier</span><span class="sxs-lookup"><span data-stu-id="b74b0-126">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 <span data-ttu-id="b74b0-127">Décrit comment créer un assembly multifichier.</span><span class="sxs-lookup"><span data-stu-id="b74b0-127">Describes how to create a multifile assembly.</span></span>  
  
 [<span data-ttu-id="b74b0-128">Définition des attributs d’assembly</span><span class="sxs-lookup"><span data-stu-id="b74b0-128">Setting Assembly Attributes</span></span>](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 <span data-ttu-id="b74b0-129">Décrit les attributs d’assembly et comment les définir.</span><span class="sxs-lookup"><span data-stu-id="b74b0-129">Describes assembly attributes and how to set them.</span></span>  
  
 [<span data-ttu-id="b74b0-130">Création et utilisation d’assemblys avec nom fort</span><span class="sxs-lookup"><span data-stu-id="b74b0-130">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 <span data-ttu-id="b74b0-131">Explique comment et pourquoi signer un assembly avec un nom fort. Inclut des procédures.</span><span class="sxs-lookup"><span data-stu-id="b74b0-131">Describes how and why you sign an assembly with a strong name, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="b74b0-132">Temporisation de signature d'un assembly</span><span class="sxs-lookup"><span data-stu-id="b74b0-132">Delay Signing an Assembly</span></span>](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 <span data-ttu-id="b74b0-133">Décrit comment différer la signature d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="b74b0-133">Describes how to delay-sign an assembly.</span></span>  
  
 [<span data-ttu-id="b74b0-134">Utilisation d’assemblys et du Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="b74b0-134">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 <span data-ttu-id="b74b0-135">Explique comment et pourquoi ajouter des assemblys au Global Assembly Cache. Inclut des procédures.</span><span class="sxs-lookup"><span data-stu-id="b74b0-135">Describes how and why you add assemblies to the global assembly cache, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="b74b0-136">Guide pratique pour afficher le contenu d’un assembly</span><span class="sxs-lookup"><span data-stu-id="b74b0-136">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 <span data-ttu-id="b74b0-137">Décrit comment utiliser le désassembleur MSIL (Ildasm.exe) pour afficher le contenu d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="b74b0-137">Describes how to use the MSIL Disassembler (Ildasm.exe) to view assembly contents.</span></span>  
  
 [<span data-ttu-id="b74b0-138">Transfert de type dans le Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="b74b0-138">Type Forwarding in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 <span data-ttu-id="b74b0-139">Décrit comment utiliser le transfert de type pour déplacer un type dans un assembly différent sans interrompre les applications existantes.</span><span class="sxs-lookup"><span data-stu-id="b74b0-139">Describes how to use type forwarding to move a type into a different assembly without breaking existing applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b74b0-140">Référence</span><span class="sxs-lookup"><span data-stu-id="b74b0-140">Reference</span></span>  
 <xref:System.Reflection.Assembly>  
 <span data-ttu-id="b74b0-141">Classe .NET Framework qui représente un assembly.</span><span class="sxs-lookup"><span data-stu-id="b74b0-141">The .NET Framework class that represents an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b74b0-142">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="b74b0-142">Related Sections</span></span>  
 [<span data-ttu-id="b74b0-143">Guide pratique pour obtenir des informations relatives au type et aux membres à partir d’un assembly</span><span class="sxs-lookup"><span data-stu-id="b74b0-143">How to: Obtain Type and Member Information from an Assembly</span></span>](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 <span data-ttu-id="b74b0-144">Décrit comment obtenir par programmation des informations relatives au type et à d’autres éléments à partir d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="b74b0-144">Describes how to programmatically obtain type and other information from an assembly.</span></span>  
  
 [<span data-ttu-id="b74b0-145">Assemblys dans le Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="b74b0-145">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="b74b0-146">Offre une vue d’ensemble conceptuelle des assemblys du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="b74b0-146">Provides a conceptual overview of common language runtime assemblies.</span></span>  
  
 [<span data-ttu-id="b74b0-147">Contrôle de version des assemblys</span><span class="sxs-lookup"><span data-stu-id="b74b0-147">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)  
 <span data-ttu-id="b74b0-148">Offre une vue d’ensemble de la liaison d’assembly et des attributs <xref:System.Reflection.AssemblyVersionAttribute> et <xref:System.Reflection.AssemblyInformationalVersionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b74b0-148">Provides an overview of assembly binding and of the <xref:System.Reflection.AssemblyVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes.</span></span>  
  
 [<span data-ttu-id="b74b0-149">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="b74b0-149">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="b74b0-150">Décrit comment le runtime détermine l’assembly à utiliser pour répondre à une demande de liaison.</span><span class="sxs-lookup"><span data-stu-id="b74b0-150">Describes how the runtime determines which assembly to use to fulfill a binding request.</span></span>  
  
 [<span data-ttu-id="b74b0-151">Réflexion</span><span class="sxs-lookup"><span data-stu-id="b74b0-151">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="b74b0-152">Explique comment utiliser la classe **Reflection** pour obtenir des informations sur un assembly.</span><span class="sxs-lookup"><span data-stu-id="b74b0-152">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
