---
title: Interopération avec du code non managé
ms.date: 01/17/2018
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
ms.openlocfilehash: 12183f390a5178f038c6dd2122a72a33e31ae0ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457970"
---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="c1f5b-102">Interopération avec du code non managé</span><span class="sxs-lookup"><span data-stu-id="c1f5b-102">Interoperating with unmanaged code</span></span>

<span data-ttu-id="c1f5b-103">Le .NET Framework assure l’interaction avec les composants COM, les services COM+, les bibliothèques de types externes et de nombreux services de systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="c1f5b-103">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="c1f5b-104">Les types de données, les signatures de méthode et les mécanismes de gestion des erreurs varient selon les modèles objet managés et non managés.</span><span class="sxs-lookup"><span data-stu-id="c1f5b-104">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="c1f5b-105">Pour simplifier l’interopérabilité entre les composants .NET Framework et le code non managé ainsi que pour faciliter la migration, le common language runtime dissimule à la fois aux clients et aux serveurs les différences entre ces modèles objet.</span><span class="sxs-lookup"><span data-stu-id="c1f5b-105">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>

<span data-ttu-id="c1f5b-106">Le code qui s’exécute sous le contrôle du runtime est appelé code managé.</span><span class="sxs-lookup"><span data-stu-id="c1f5b-106">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="c1f5b-107">Inversement, le code qui s’exécute en dehors du runtime est appelé code non managé.</span><span class="sxs-lookup"><span data-stu-id="c1f5b-107">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="c1f5b-108">Les composants COM, les interfaces ActiveX et les fonctions API Windows sont des exemples de code non managé.</span><span class="sxs-lookup"><span data-stu-id="c1f5b-108">COM components, ActiveX interfaces, and Windows API functions are examples of unmanaged code.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="c1f5b-109">Contenu de cette section</span><span class="sxs-lookup"><span data-stu-id="c1f5b-109">In this section</span></span>

[<span data-ttu-id="c1f5b-110">Exposition de composants COM au .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c1f5b-110">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)  
<span data-ttu-id="c1f5b-111">Explique comment utiliser des composants COM à partir d’applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c1f5b-111">Describes how to use COM components from .NET Framework applications.</span></span>

[<span data-ttu-id="c1f5b-112">Exposition de composants .NET Framework à COM</span><span class="sxs-lookup"><span data-stu-id="c1f5b-112">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
<span data-ttu-id="c1f5b-113">Explique comment utiliser des composants .NET Framework à partir d’applications COM.</span><span class="sxs-lookup"><span data-stu-id="c1f5b-113">Describes how to use .NET Framework components from COM applications.</span></span>

[<span data-ttu-id="c1f5b-114">Consommation de fonctions DLL non managées</span><span class="sxs-lookup"><span data-stu-id="c1f5b-114">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
<span data-ttu-id="c1f5b-115">Décrit comment appeler des fonctions DLL non managées à l’aide de l’appel de code non managé.</span><span class="sxs-lookup"><span data-stu-id="c1f5b-115">Describes how to call unmanaged DLL functions using platform invoke.</span></span>

[<span data-ttu-id="c1f5b-116">Marshaling d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="c1f5b-116">Interop Marshaling</span></span>](interop-marshaling.md)  
<span data-ttu-id="c1f5b-117">Décrit le marshaling de COM Interop et de l’appel de code non managé.</span><span class="sxs-lookup"><span data-stu-id="c1f5b-117">Describes marshaling for COM interop and platform invoke.</span></span>

[<span data-ttu-id="c1f5b-118">Guide pratique pour mapper des HRESULT et des exceptions</span><span class="sxs-lookup"><span data-stu-id="c1f5b-118">How to: Map HRESULTs and Exceptions</span></span>](how-to-map-hresults-and-exceptions.md)  
<span data-ttu-id="c1f5b-119">Décrit le mappage entre les exceptions et les valeurs HRESULT.</span><span class="sxs-lookup"><span data-stu-id="c1f5b-119">Describes the mapping between exceptions and HRESULTs.</span></span>

[<span data-ttu-id="c1f5b-120">Équivalence de type et types interop incorporés</span><span class="sxs-lookup"><span data-stu-id="c1f5b-120">Type Equivalence and Embedded Interop Types</span></span>](type-equivalence-and-embedded-interop-types.md)  
<span data-ttu-id="c1f5b-121">Décrit comment les informations de type pour les types COM sont incorporées dans les assemblys, et comment le common language runtime détermine l’équivalence des types COM incorporés.</span><span class="sxs-lookup"><span data-stu-id="c1f5b-121">Describes how type information for COM types is embedded in assemblies, and how the common language runtime determines the equivalence of embedded COM types.</span></span>

[<span data-ttu-id="c1f5b-122">Comment : générer des assemblys PIA à l'aide de Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="c1f5b-122">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
<span data-ttu-id="c1f5b-123">Décrit comment produire des assemblys PIA à l’aide de *Tlbimp.exe* (importateur de bibliothèques de types).</span><span class="sxs-lookup"><span data-stu-id="c1f5b-123">Describes how to produce primary interop assemblies using *Tlbimp.exe* (Type Library Importer).</span></span>

[<span data-ttu-id="c1f5b-124">Comment : enregistrer des assemblys PIA</span><span class="sxs-lookup"><span data-stu-id="c1f5b-124">How to: Register Primary Interop Assemblies</span></span>](how-to-register-primary-interop-assemblies.md)  
<span data-ttu-id="c1f5b-125">Décrit comment inscrire les assemblys PIA avant de les référencer dans vos projets.</span><span class="sxs-lookup"><span data-stu-id="c1f5b-125">Describes how to register the primary interop assemblies before you can reference them in your projects.</span></span>

[<span data-ttu-id="c1f5b-126">COM Interop sans inscription</span><span class="sxs-lookup"><span data-stu-id="c1f5b-126">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)  
<span data-ttu-id="c1f5b-127">Décrit comment COM Interop peut activer des composants sans utiliser le Registre Windows.</span><span class="sxs-lookup"><span data-stu-id="c1f5b-127">Describes how COM interop can activate components without using the Windows registry.</span></span>

[<span data-ttu-id="c1f5b-128">Comment : configurer les composants COM .NET Framework pour l'activation sans inscription</span><span class="sxs-lookup"><span data-stu-id="c1f5b-128">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](configure-net-framework-based-com-components-for-reg.md)  
<span data-ttu-id="c1f5b-129">Décrit comment créer un manifeste d’application, puis explique comment créer et incorporer un manifeste de composant.</span><span class="sxs-lookup"><span data-stu-id="c1f5b-129">Describes how to create an application manifest and how to create and embed a component manifest.</span></span>

## <a name="related-sections"></a><span data-ttu-id="c1f5b-130">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="c1f5b-130">Related sections</span></span>

[<span data-ttu-id="c1f5b-131">Wrappers COM</span><span class="sxs-lookup"><span data-stu-id="c1f5b-131">COM Wrappers</span></span>](../../standard/native-interop/com-wrappers.md)  
<span data-ttu-id="c1f5b-132">Décrit les wrappers fournis par COM Interop.</span><span class="sxs-lookup"><span data-stu-id="c1f5b-132">Describes the wrappers provided by COM interop.</span></span>
