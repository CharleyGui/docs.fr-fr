---
title: Interfaces de fusion
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework fusion]
- fusion interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], fusion
ms.assetid: e2cf98b7-40c1-4f74-86c7-8a76dd9da677
ms.openlocfilehash: 81c66825e69d9526abddfe06133426a2274ad08f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108192"
---
# <a name="fusion-interfaces"></a><span data-ttu-id="8758d-102">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="8758d-102">Fusion Interfaces</span></span>
<span data-ttu-id="8758d-103">Cette section décrit les interfaces non managées utilisées par l’API de fusion pour accéder aux propriétés des ressources d’une application et rechercher les versions appropriées de ces ressources pour l’application.</span><span class="sxs-lookup"><span data-stu-id="8758d-103">This section describes the unmanaged interfaces that the fusion API uses to access the properties of an application's resources and to locate the correct versions of those resources for the application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8758d-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8758d-104">In This Section</span></span>  
 [<span data-ttu-id="8758d-105">IAppIdAuthority, interface</span><span class="sxs-lookup"><span data-stu-id="8758d-105">IAppIdAuthority Interface</span></span>](iappidauthority-interface.md)  
 <span data-ttu-id="8758d-106">Fournit des méthodes qui génèrent et comparent des clés pour les identités et les références d’application.</span><span class="sxs-lookup"><span data-stu-id="8758d-106">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="8758d-107">IAssemblyCache, interface</span><span class="sxs-lookup"><span data-stu-id="8758d-107">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)  
 <span data-ttu-id="8758d-108">Fournit une représentation de l’Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="8758d-108">Provides a representation of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="8758d-109">IAssemblyCacheItem, interface</span><span class="sxs-lookup"><span data-stu-id="8758d-109">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)  
 <span data-ttu-id="8758d-110">Représente un assembly unique dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="8758d-110">Represents a single assembly in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="8758d-111">IAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="8758d-111">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)  
 <span data-ttu-id="8758d-112">Représente un énumérateur pour un tableau d’objets `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="8758d-112">Represents an enumerator for an array of `IAssemblyName` objects.</span></span>  
  
 [<span data-ttu-id="8758d-113">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="8758d-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)  
 <span data-ttu-id="8758d-114">Fournit des méthodes pour décrire et utiliser l’identité unique d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="8758d-114">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
 [<span data-ttu-id="8758d-115">IDefinitionAppId, interface</span><span class="sxs-lookup"><span data-stu-id="8758d-115">IDefinitionAppId Interface</span></span>](idefinitionappid-interface.md)  
 <span data-ttu-id="8758d-116">Représente un identificateur unique pour le code qui définit l’application dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="8758d-116">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="8758d-117">IDefinitionIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="8758d-117">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)  
 <span data-ttu-id="8758d-118">Représente la signature unique du code qui définit l’application dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="8758d-118">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="8758d-119">IEnumDefinitionIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="8758d-119">IEnumDefinitionIdentity Interface</span></span>](ienumdefinitionidentity-interface.md)  
 <span data-ttu-id="8758d-120">Sert d’énumérateur pour une collection d’objets `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="8758d-120">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
 [<span data-ttu-id="8758d-121">IEnumIDENTITY_ATTRIBUTE, interface</span><span class="sxs-lookup"><span data-stu-id="8758d-121">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)  
 <span data-ttu-id="8758d-122">Sert d’énumérateur pour les attributs de l’objet de code dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="8758d-122">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
 [<span data-ttu-id="8758d-123">IEnumReferenceIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="8758d-123">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)  
 <span data-ttu-id="8758d-124">Sert d’énumérateur pour une collection d’objets `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="8758d-124">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
 [<span data-ttu-id="8758d-125">IIdentityAuthority, interface</span><span class="sxs-lookup"><span data-stu-id="8758d-125">IIdentityAuthority Interface</span></span>](iidentityauthority-interface.md)  
 <span data-ttu-id="8758d-126">Gère les clés d’identité pour les objets de code.</span><span class="sxs-lookup"><span data-stu-id="8758d-126">Manages identity keys for code objects.</span></span>  
  
 [<span data-ttu-id="8758d-127">IInstallReferenceEnum, interface</span><span class="sxs-lookup"><span data-stu-id="8758d-127">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)  
 <span data-ttu-id="8758d-128">Représente un énumérateur pour les assemblys référencés installés dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="8758d-128">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="8758d-129">IInstallReferenceItem, interface</span><span class="sxs-lookup"><span data-stu-id="8758d-129">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)  
 <span data-ttu-id="8758d-130">Représente un élément installé dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="8758d-130">Represents an item installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="8758d-131">IReferenceAppId, interface</span><span class="sxs-lookup"><span data-stu-id="8758d-131">IReferenceAppId Interface</span></span>](ireferenceappid-interface.md)  
 <span data-ttu-id="8758d-132">Représente une référence à l’identificateur unique de l’application dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="8758d-132">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
 [<span data-ttu-id="8758d-133">IReferenceIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="8758d-133">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)  
 <span data-ttu-id="8758d-134">Représente une référence à la signature unique d’un objet de code.</span><span class="sxs-lookup"><span data-stu-id="8758d-134">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8758d-135">Reference</span><span class="sxs-lookup"><span data-stu-id="8758d-135">Reference</span></span>  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
## <a name="related-sections"></a><span data-ttu-id="8758d-136">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="8758d-136">Related Sections</span></span>  
 [<span data-ttu-id="8758d-137">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="8758d-137">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)  
  
 [<span data-ttu-id="8758d-138">Énumérations de fusion</span><span class="sxs-lookup"><span data-stu-id="8758d-138">Fusion Enumerations</span></span>](fusion-enumerations.md)  
  
 [<span data-ttu-id="8758d-139">Structures de fusion</span><span class="sxs-lookup"><span data-stu-id="8758d-139">Fusion Structures</span></span>](fusion-structures.md)
