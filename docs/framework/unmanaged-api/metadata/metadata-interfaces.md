---
title: Interfaces de métadonnées
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
ms.openlocfilehash: 5d9b48df740668797a7c901219401e9ea304a8f8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672879"
---
# <a name="metadata-interfaces"></a><span data-ttu-id="e078e-102">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="e078e-102">Metadata Interfaces</span></span>

<span data-ttu-id="e078e-103">Cette section décrit les interfaces non managées qui donnent accès aux métadonnées exposées par les types, méthodes, champs, etc. du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e078e-103">This section describes the unmanaged interfaces that provide access to the metadata exposed by the .NET Framework types, methods, fields, and so on.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e078e-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="e078e-104">In This Section</span></span>  

 [<span data-ttu-id="e078e-105">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="e078e-105">ICeeGen Interface</span></span>](iceegen-interface.md)  
 <span data-ttu-id="e078e-106">Fournit des méthodes pour la compilation de code dynamique.</span><span class="sxs-lookup"><span data-stu-id="e078e-106">Provides methods for dynamic code compilation.</span></span>  
  
 [<span data-ttu-id="e078e-107">IHostFilter, interface</span><span class="sxs-lookup"><span data-stu-id="e078e-107">IHostFilter Interface</span></span>](ihostfilter-interface.md)  
 <span data-ttu-id="e078e-108">Fournit une méthode permettant à l'hôte du runtime de marquer des jetons de métadonnées à traiter.</span><span class="sxs-lookup"><span data-stu-id="e078e-108">Provides a method for the run-time host to mark metadata tokens for processing.</span></span>  
  
 [<span data-ttu-id="e078e-109">IMapToken, interface</span><span class="sxs-lookup"><span data-stu-id="e078e-109">IMapToken Interface</span></span>](imaptoken-interface.md)  
 <span data-ttu-id="e078e-110">Fournit des fonctionnalités de mappage entre des signatures de métadonnées importées et émises.</span><span class="sxs-lookup"><span data-stu-id="e078e-110">Provides mapping capabilities between imported and emitted metadata signatures.</span></span>  
  
 [<span data-ttu-id="e078e-111">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="e078e-111">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)  
 <span data-ttu-id="e078e-112">Fournit des méthodes qui prennent en charge le modèle d'autodescription utilisé par le Common Language Runtime (CLR) pour résoudre et consommer des ressources.</span><span class="sxs-lookup"><span data-stu-id="e078e-112">Provides methods that support the self-description model used by the common language runtime (CLR) to resolve and consume resources.</span></span>  
  
 [<span data-ttu-id="e078e-113">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="e078e-113">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)  
 <span data-ttu-id="e078e-114">Fournit des méthodes pour accéder au contenu d'un manifeste d'assembly et l'examiner.</span><span class="sxs-lookup"><span data-stu-id="e078e-114">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
 [<span data-ttu-id="e078e-115">IMetaDataConverter, interface</span><span class="sxs-lookup"><span data-stu-id="e078e-115">IMetaDataConverter Interface</span></span>](imetadataconverter-interface.md)  
 <span data-ttu-id="e078e-116">Fournit des méthodes pour mapper des bibliothèques de types à leurs signatures de métadonnées et effectuer la conversion entre les deux.</span><span class="sxs-lookup"><span data-stu-id="e078e-116">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
 [<span data-ttu-id="e078e-117">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="e078e-117">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)  
 <span data-ttu-id="e078e-118">`IMetaDataDispenser` est obsolète.</span><span class="sxs-lookup"><span data-stu-id="e078e-118">`IMetaDataDispenser` is obsolete.</span></span> <span data-ttu-id="e078e-119">Utilisez plutôt `IMetaDataDispenserEx`.</span><span class="sxs-lookup"><span data-stu-id="e078e-119">Use `IMetaDataDispenserEx` instead.</span></span>  
  
 [<span data-ttu-id="e078e-120">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="e078e-120">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)  
 <span data-ttu-id="e078e-121">Fournit des méthodes qui mappent des zones de mémoire pour créer ou modifier des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="e078e-121">Provides methods that map areas of memory for creating or modifying metadata.</span></span>  
  
 [<span data-ttu-id="e078e-122">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="e078e-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)  
 <span data-ttu-id="e078e-123">Fournit des méthodes pour créer, modifier et stocker les métadonnées sur l'assembly dans la portée actuellement définie.</span><span class="sxs-lookup"><span data-stu-id="e078e-123">Provides methods to create, modify and store metadata about the assembly in the currently defined scope.</span></span>  
  
 [<span data-ttu-id="e078e-124">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="e078e-124">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)  
 <span data-ttu-id="e078e-125">Fournit des méthodes pour définir et modifier les signatures de métadonnées de méthodes et de constructeurs avec les paramètres de type <xref:System.Type?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e078e-125">Provides methods for defining and modifying the metadata signatures of methods and constructors with parameters of type <xref:System.Type?displayProperty=nameWithType>.</span></span>  
  
 [<span data-ttu-id="e078e-126">IMetaDataError, interface</span><span class="sxs-lookup"><span data-stu-id="e078e-126">IMetaDataError Interface</span></span>](imetadataerror-interface.md)  
 <span data-ttu-id="e078e-127">Fournit un mécanisme de rappel pour signaler les erreurs pendant la résolution de la signature de métadonnées d'un assembly.</span><span class="sxs-lookup"><span data-stu-id="e078e-127">Provides a callback mechanism for reporting errors during the resolution of the metadata signature for an assembly.</span></span>  
  
 [<span data-ttu-id="e078e-128">IMetaDataFilter, interface</span><span class="sxs-lookup"><span data-stu-id="e078e-128">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)  
 <span data-ttu-id="e078e-129">Fournit des méthodes pour marquer et filtrer des jetons de métadonnées pour éviter de répéter des actions qui ont déjà été prises.</span><span class="sxs-lookup"><span data-stu-id="e078e-129">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
 [<span data-ttu-id="e078e-130">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="e078e-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)  
 <span data-ttu-id="e078e-131">Fournit des méthodes pour importer et manipuler des types provenant d'autres assemblys.</span><span class="sxs-lookup"><span data-stu-id="e078e-131">Provides methods for importing and manipulating types from other assemblies.</span></span>  
  
 [<span data-ttu-id="e078e-132">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="e078e-132">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)  
 <span data-ttu-id="e078e-133">Étend `IMetaDataImport` pour permettre d'utiliser des types génériques.</span><span class="sxs-lookup"><span data-stu-id="e078e-133">Extends `IMetaDataImport` to provide the capability of working with generic types.</span></span>  
  
 [<span data-ttu-id="e078e-134">IMetaDataInfo, interface</span><span class="sxs-lookup"><span data-stu-id="e078e-134">IMetaDataInfo Interface</span></span>](imetadatainfo-interface.md)  
 <span data-ttu-id="e078e-135">Fournit une méthode qui obtient des informations sur le mappage de métadonnées à partir d'un fichier sur disque dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="e078e-135">Provides a method that gets information about the mapping of metadata from an on-disk file into memory.</span></span>  
  
 [<span data-ttu-id="e078e-136">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="e078e-136">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)  
 <span data-ttu-id="e078e-137">Fournit des méthodes pour le stockage et la récupération d'informations de métadonnées dans des tables.</span><span class="sxs-lookup"><span data-stu-id="e078e-137">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
 [<span data-ttu-id="e078e-138">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="e078e-138">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)  
 <span data-ttu-id="e078e-139">Étend `IMetaDataTables` pour inclure des méthodes permettant d'utiliser des flux de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="e078e-139">Extends `IMetaDataTables` to include methods for working with metadata streams.</span></span>  
  
 [<span data-ttu-id="e078e-140">IMetaDataValidate, interface</span><span class="sxs-lookup"><span data-stu-id="e078e-140">IMetaDataValidate Interface</span></span>](imetadatavalidate-interface.md)  
 <span data-ttu-id="e078e-141">Fournit des méthodes à utiliser pour la validation des signatures de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="e078e-141">Provides methods to use for validation of metadata signatures.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e078e-142">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="e078e-142">Related Sections</span></span>  

 [<span data-ttu-id="e078e-143">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="e078e-143">Metadata Global Static Functions</span></span>](metadata-global-static-functions.md)  
  
 [<span data-ttu-id="e078e-144">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="e078e-144">Metadata Enumerations</span></span>](metadata-enumerations.md)  
  
 [<span data-ttu-id="e078e-145">Structures de métadonnées</span><span class="sxs-lookup"><span data-stu-id="e078e-145">Metadata Structures</span></span>](metadata-structures.md)  
  
 [<span data-ttu-id="e078e-146">Unions de métadonnées</span><span class="sxs-lookup"><span data-stu-id="e078e-146">Metadata Unions</span></span>](metadata-unions.md)
