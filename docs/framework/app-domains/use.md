---
title: Utilisation des domaines d'application
description: Utilisez des domaines d’application, qui fournissent une unité d’isolation pour le common language runtime (CLR). Les domaines d’application sont créés et exécutés à l’intérieur d’un processus.
ms.date: 03/30/2017
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
ms.openlocfilehash: df2a63716904ebfc6ee163121a1f07e53aa07514
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105179"
---
# <a name="using-application-domains"></a><span data-ttu-id="a4463-104">Utilisation des domaines d'application</span><span class="sxs-lookup"><span data-stu-id="a4463-104">Using Application Domains</span></span>

<span data-ttu-id="a4463-105">Les domaines d’application fournissent une unité d’isolation pour le common language runtime.</span><span class="sxs-lookup"><span data-stu-id="a4463-105">Application domains provide a unit of isolation for the common language runtime.</span></span> <span data-ttu-id="a4463-106">Ils sont créés et exécutés dans un processus.</span><span class="sxs-lookup"><span data-stu-id="a4463-106">They are created and run inside a process.</span></span> <span data-ttu-id="a4463-107">Les domaines d’application sont généralement créés par un hôte de runtime, qui est une application responsable du chargement du runtime dans un processus et de l’exécution du code utilisateur dans un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="a4463-107">Application domains are usually created by a runtime host, which is an application responsible for loading the runtime into a process and executing user code within an application domain.</span></span> <span data-ttu-id="a4463-108">L’hôte de runtime crée un processus et un domaine d’application par défaut et exécute le code managé dans ce domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="a4463-108">The runtime host creates a process and a default application domain, and runs managed code inside it.</span></span> <span data-ttu-id="a4463-109">Les hôtes de runtime comprennent ASP.NET, Microsoft Internet Explorer et le shell Windows.</span><span class="sxs-lookup"><span data-stu-id="a4463-109">Runtime hosts include ASP.NET, Microsoft Internet Explorer, and the Windows shell.</span></span>  
  
<span data-ttu-id="a4463-110">Pour la plupart des applications, vous n’êtes pas obligé de créer votre propre domaine d’application ; l’hôte du runtime se charge de créer le domaine d’application dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="a4463-110">For most applications, you do not need to create your own application domain; the runtime host creates any necessary application domains for you.</span></span> <span data-ttu-id="a4463-111">Toutefois, vous pouvez créer et configurer des domaines d’application supplémentaires si votre application doit isoler du code ou utiliser et décharger des DLL.</span><span class="sxs-lookup"><span data-stu-id="a4463-111">However, you can create and configure additional application domains if your application needs to isolate code or to use and unload DLLs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a4463-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a4463-112">In This Section</span></span>  

[<span data-ttu-id="a4463-113">Procédure : créer un domaine d’application</span><span class="sxs-lookup"><span data-stu-id="a4463-113">How to: Create an Application Domain</span></span>](how-to-create-an-application-domain.md)  
<span data-ttu-id="a4463-114">Décrit comment créer un domaine d’application par programmation.</span><span class="sxs-lookup"><span data-stu-id="a4463-114">Describes how to programmatically create an application domain.</span></span>  
  
[<span data-ttu-id="a4463-115">Procédure : décharger un domaine d’application</span><span class="sxs-lookup"><span data-stu-id="a4463-115">How to: Unload an Application Domain</span></span>](how-to-unload-an-application-domain.md)  
<span data-ttu-id="a4463-116">Décrit comment décharger un domaine d’application par programmation.</span><span class="sxs-lookup"><span data-stu-id="a4463-116">Describes how to programmatically unload an application domain.</span></span>  
  
[<span data-ttu-id="a4463-117">Procédure : configurer un domaine d’application</span><span class="sxs-lookup"><span data-stu-id="a4463-117">How to: Configure an Application Domain</span></span>](how-to-configure-an-application-domain.md)  
<span data-ttu-id="a4463-118">Propose une introduction à la configuration d’un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="a4463-118">Provides an introduction to configuring an application domain.</span></span>  
  
[<span data-ttu-id="a4463-119">Récupération d'informations d'installation à partir d'un domaine d'application</span><span class="sxs-lookup"><span data-stu-id="a4463-119">Retrieving Setup Information from an Application Domain</span></span>](retrieve-setup-information.md)  
<span data-ttu-id="a4463-120">Décrit comment récupérer les informations de configuration d’un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="a4463-120">Describes how to retrieve setup information from an application domain.</span></span>  
  
[<span data-ttu-id="a4463-121">Procédure : charger des assemblys dans un domaine d’application</span><span class="sxs-lookup"><span data-stu-id="a4463-121">How to: Load Assemblies into an Application Domain</span></span>](how-to-load-assemblies-into-an-application-domain.md)  
<span data-ttu-id="a4463-122">Décrit comment charger un assembly dans un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="a4463-122">Describes how to load an assembly into an application domain.</span></span>  
  
[<span data-ttu-id="a4463-123">Guide pratique pour obtenir des informations relatives au type et aux membres à partir d'un assembly</span><span class="sxs-lookup"><span data-stu-id="a4463-123">How to: Obtain Type and Member Information from an Assembly</span></span>](../reflection-and-codedom/get-type-member-information.md)  
<span data-ttu-id="a4463-124">Décrit comment récupérer des informations sur un assembly.</span><span class="sxs-lookup"><span data-stu-id="a4463-124">Describes how to retrieve information about an assembly.</span></span>  
  
[<span data-ttu-id="a4463-125">Clichés instantanés d'assemblys</span><span class="sxs-lookup"><span data-stu-id="a4463-125">Shadow Copying Assemblies</span></span>](shadow-copy-assemblies.md)  
<span data-ttu-id="a4463-126">Décrit comment utiliser des clichés instantanés pour mettre à jour des assemblys pendant leur utilisation, et comment configurer des clichés instantanés.</span><span class="sxs-lookup"><span data-stu-id="a4463-126">Describes how shadow copying allows updates to assemblies while they are in use, and how to configure shadow copying.</span></span>  
  
[<span data-ttu-id="a4463-127">Procédure : recevoir des notifications des exceptions de première chance</span><span class="sxs-lookup"><span data-stu-id="a4463-127">How to: Receive First-Chance Exception Notifications</span></span>](how-to-receive-first-chance-exception-notifications.md)  
<span data-ttu-id="a4463-128">Explique comment recevoir une notification indiquant qu’une exception a été levée, avant que le common language runtime ne commence à rechercher des gestionnaires d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="a4463-128">Explains how you can receive a notification that an exception has been thrown, before the common language runtime has begun searching for exception handlers.</span></span>  
  
[<span data-ttu-id="a4463-129">Résoudre les chargements d'assemblys</span><span class="sxs-lookup"><span data-stu-id="a4463-129">Resolving Assembly Loads</span></span>](../../standard/assembly/resolve-loads.md)  
<span data-ttu-id="a4463-130">Offre des conseils sur l’utilisation de l’événement <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> pour résoudre les échecs de chargement de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="a4463-130">Provides guidance on using the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event to resolve assembly load failures.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a4463-131">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="a4463-131">Reference</span></span>  

<xref:System.AppDomain>  
<span data-ttu-id="a4463-132">Représente un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="a4463-132">Represents an application domain.</span></span> <span data-ttu-id="a4463-133">Fournit des méthodes pour la création et le contrôle des domaines d’application.</span><span class="sxs-lookup"><span data-stu-id="a4463-133">Provides methods for creating and controlling application domains.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a4463-134">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="a4463-134">Related Sections</span></span>  
[<span data-ttu-id="a4463-135">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="a4463-135">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="a4463-136">Fournit une vue d’ensemble des fonctions exécutées par les assemblys.</span><span class="sxs-lookup"><span data-stu-id="a4463-136">Provides an overview of the functions performed by assemblies.</span></span>  
  
[<span data-ttu-id="a4463-137">Programmation à l’aide d’assemblys</span><span class="sxs-lookup"><span data-stu-id="a4463-137">Programming with Assemblies</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="a4463-138">Décrit comment créer, signer et définir des attributs sur des assemblys.</span><span class="sxs-lookup"><span data-stu-id="a4463-138">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
[<span data-ttu-id="a4463-139">Émission d’assemblys et de méthodes dynamiques</span><span class="sxs-lookup"><span data-stu-id="a4463-139">Emitting Dynamic Methods and Assemblies</span></span>](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
<span data-ttu-id="a4463-140">Décrit comment créer des assemblys dynamiques.</span><span class="sxs-lookup"><span data-stu-id="a4463-140">Describes how to create dynamic assemblies.</span></span>  
  
[<span data-ttu-id="a4463-141">Domaines d'application</span><span class="sxs-lookup"><span data-stu-id="a4463-141">Application Domains</span></span>](application-domains.md)  
<span data-ttu-id="a4463-142">Fournit une vue d'ensemble conceptuelle des domaines d'application.</span><span class="sxs-lookup"><span data-stu-id="a4463-142">Provides a conceptual overview of application domains.</span></span>  
  
[<span data-ttu-id="a4463-143">Vue d’ensemble de la réflexion</span><span class="sxs-lookup"><span data-stu-id="a4463-143">Reflection Overview</span></span>](../reflection-and-codedom/reflection.md)  
<span data-ttu-id="a4463-144">Explique comment utiliser la classe **Reflection** pour obtenir des informations sur un assembly.</span><span class="sxs-lookup"><span data-stu-id="a4463-144">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
