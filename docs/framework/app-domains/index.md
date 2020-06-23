---
title: Programmation à l'aide de domaines d'application et d'assemblys
description: Familiarisez-vous avec la programmation avec les domaines d’application et les assemblys dans .NET. Consultez les liens vers des rubriques de procédures & des exemples sur la création de domaines d’application & assemblys.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
ms.openlocfilehash: 1c28fe0abeb279a1dbbc6dcf043c1780c72d79df
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903436"
---
# <a name="programming-with-application-domains-and-assemblies"></a><span data-ttu-id="1f5d8-104">Programmation à l'aide de domaines d'application et d'assemblys</span><span class="sxs-lookup"><span data-stu-id="1f5d8-104">Programming with Application Domains and Assemblies</span></span>

<span data-ttu-id="1f5d8-105">Les ordinateurs hôtes tels que Microsoft Internet Explorer, ASP.NET et le shell Windows chargent le Common Language Runtime dans un processus, créent un [domaine d’application](application-domains.md) dans ce processus, puis chargent et exécutent le code utilisateur dans ce domaine d’application lors de l’exécution d’une application .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1f5d8-105">Hosts such as Microsoft Internet Explorer, ASP.NET, and the Windows shell load the common language runtime into a process, create an [application domain](application-domains.md) in that process, and then load and execute user code in that application domain when running a .NET Framework application.</span></span> <span data-ttu-id="1f5d8-106">Dans la plupart des cas, vous n’avez pas à vous soucier de la création des domaines d’application et du chargement des assemblys dans ces domaines car l’hôte runtime effectue ces tâches.</span><span class="sxs-lookup"><span data-stu-id="1f5d8-106">In most cases, you do not have to worry about creating application domains and loading assemblies into them because the runtime host performs those tasks.</span></span>  
  
<span data-ttu-id="1f5d8-107">Toutefois, si vous créez une application qui hébergera le Common Language Runtime, créez des outils ou un code que vous souhaitez décharger par programmation, ou créez des composants enfichables pouvant être déchargés et rechargés à la volée, vous allez créer vos propres domaines d’application.</span><span class="sxs-lookup"><span data-stu-id="1f5d8-107">However, if you are creating an application that will host the common language runtime, creating tools or code you want to unload programmatically, or creating pluggable components that can be unloaded and reloaded on the fly, you will be creating your own application domains.</span></span> <span data-ttu-id="1f5d8-108">Même si vous ne créez aucun hôte de runtime, cette section fournit des informations importantes sur l’utilisation des domaines d’application et assemblys chargés dans ces domaines d’application.</span><span class="sxs-lookup"><span data-stu-id="1f5d8-108">Even if you are not creating a runtime host, this section provides important information on how to work with application domains and assemblies loaded in these application domains.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1f5d8-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="1f5d8-109">In This Section</span></span>  

[<span data-ttu-id="1f5d8-110">Rubriques Comment relatives aux domaines d'application et aux assemblys</span><span class="sxs-lookup"><span data-stu-id="1f5d8-110">Application Domains and Assemblies How-to Topics</span></span>](application-domains-and-assemblies-how-to-topics.md)  
<span data-ttu-id="1f5d8-111">Fournit des liens vers toutes les rubriques Guide pratique de la documentation conceptuelle pour la programmation avec des domaines d’application et des assemblys.</span><span class="sxs-lookup"><span data-stu-id="1f5d8-111">Provides links to all How-to topics found in the conceptual documentation for programming with application domains and assemblies.</span></span>  
  
[<span data-ttu-id="1f5d8-112">Utilisation des domaines d'application</span><span class="sxs-lookup"><span data-stu-id="1f5d8-112">Using Application Domains</span></span>](use.md)  
<span data-ttu-id="1f5d8-113">Fournit des exemples de création, de configuration et d’utilisation des domaines d’application.</span><span class="sxs-lookup"><span data-stu-id="1f5d8-113">Provides examples of creating, configuring, and using application domains.</span></span>  
  
[<span data-ttu-id="1f5d8-114">Programmation à l’aide d’assemblys</span><span class="sxs-lookup"><span data-stu-id="1f5d8-114">Programming with Assemblies</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="1f5d8-115">Décrit comment créer, signer et définir des attributs sur des assemblys.</span><span class="sxs-lookup"><span data-stu-id="1f5d8-115">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1f5d8-116">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="1f5d8-116">Related Sections</span></span>  

[<span data-ttu-id="1f5d8-117">Émission d’assemblys et de méthodes dynamiques</span><span class="sxs-lookup"><span data-stu-id="1f5d8-117">Emitting Dynamic Methods and Assemblies</span></span>](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
<span data-ttu-id="1f5d8-118">Décrit comment créer des assemblys dynamiques.</span><span class="sxs-lookup"><span data-stu-id="1f5d8-118">Describes how to create dynamic assemblies.</span></span>  
  
[<span data-ttu-id="1f5d8-119">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="1f5d8-119">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="1f5d8-120">Fournit une vue d'ensemble conceptuelle des assemblys.</span><span class="sxs-lookup"><span data-stu-id="1f5d8-120">Provides a conceptual overview of assemblies.</span></span>  
  
[<span data-ttu-id="1f5d8-121">Domaines d'application</span><span class="sxs-lookup"><span data-stu-id="1f5d8-121">Application Domains</span></span>](application-domains.md)  
<span data-ttu-id="1f5d8-122">Fournit une vue d'ensemble conceptuelle des domaines d'application.</span><span class="sxs-lookup"><span data-stu-id="1f5d8-122">Provides a conceptual overview of application domains.</span></span>  
  
[<span data-ttu-id="1f5d8-123">Vue d’ensemble de la réflexion</span><span class="sxs-lookup"><span data-stu-id="1f5d8-123">Reflection Overview</span></span>](../reflection-and-codedom/reflection.md)  
<span data-ttu-id="1f5d8-124">Explique comment utiliser la classe **Reflection** pour obtenir des informations sur un assembly.</span><span class="sxs-lookup"><span data-stu-id="1f5d8-124">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
