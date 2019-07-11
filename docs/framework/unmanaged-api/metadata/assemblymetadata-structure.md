---
title: ASSEMBLYMETADATA, structure
ms.date: 03/30/2017
api_name:
- ASSEMBLYMETADATA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ASSEMBLYMETADATA
helpviewer_keywords:
- ASSEMBLYMETADATA structure [.NET Framework metadata]
ms.assetid: 1af98e57-9145-4d35-bb78-77d1da7c91a5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a5039117c649943a1f05a91ecccf22eb4230e5e7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776380"
---
# <a name="assemblymetadata-structure"></a><span data-ttu-id="dec87-102">ASSEMBLYMETADATA, structure</span><span class="sxs-lookup"><span data-stu-id="dec87-102">ASSEMBLYMETADATA Structure</span></span>
<span data-ttu-id="dec87-103">Contient des informations sur l’assembly référencé, y compris sa version et son niveau de prise en charge des paramètres régionaux, des processeurs et systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="dec87-103">Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dec87-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dec87-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    USHORT  usMajorVersion;  
    USHORT  usMinorVersion;  
    USHORT  usBuildNumber;  
    USHORT  usRevisionNumber;  
    LPWSTR  szLocale;  
    ULONG   cbLocale;  
    DWORD*  rdwProcessor[];  
    ULONG   ulProcessor  
    OSINFO* rOS[];  
    ULONG   ulOS;  
} ASSEMBLYMETADATA;  
```  
  
## <a name="members"></a><span data-ttu-id="dec87-105">Membres</span><span class="sxs-lookup"><span data-stu-id="dec87-105">Members</span></span>  
  
|<span data-ttu-id="dec87-106">Membre</span><span class="sxs-lookup"><span data-stu-id="dec87-106">Member</span></span>|<span data-ttu-id="dec87-107">Description</span><span class="sxs-lookup"><span data-stu-id="dec87-107">Description</span></span>|  
|------------|-----------------|  
|`usMajorVersion`|<span data-ttu-id="dec87-108">Numéro de version principale de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="dec87-108">The major version number of the referenced assembly.</span></span> <span data-ttu-id="dec87-109">Cette valeur ne peut pas être égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="dec87-109">This value cannot be zero.</span></span> <span data-ttu-id="dec87-110">Si tous les bits de `usMajorVersion` sont définis, la version principale n’est pas spécifiée.</span><span class="sxs-lookup"><span data-stu-id="dec87-110">If all the bits of `usMajorVersion` are set, the major version is not specified.</span></span>|  
|`usMinorVersion`|<span data-ttu-id="dec87-111">Numéro de version secondaire de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="dec87-111">The minor version number of the referenced assembly.</span></span> <span data-ttu-id="dec87-112">Cette valeur ne peut pas être égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="dec87-112">This value cannot be zero.</span></span> <span data-ttu-id="dec87-113">Si tous les bits de `usMinorVersion` sont définis, la version secondaire n’est pas spécifiée.</span><span class="sxs-lookup"><span data-stu-id="dec87-113">If all the bits of `usMinorVersion` are set, the minor version is not specified.</span></span>|  
|`usBuildNumber`|<span data-ttu-id="dec87-114">Le numéro de build de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="dec87-114">The build number of the referenced assembly.</span></span> <span data-ttu-id="dec87-115">Cette valeur ne peut pas être égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="dec87-115">This value cannot be zero.</span></span> <span data-ttu-id="dec87-116">Si tous les bits de `usBuildNumber` sont définis, le numéro de build n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="dec87-116">If all the bits of `usBuildNumber` are set, the build number is not specified.</span></span>|  
|`usRevisionNumber`|<span data-ttu-id="dec87-117">Le numéro de révision de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="dec87-117">The revision number of the referenced assembly.</span></span> <span data-ttu-id="dec87-118">Cette valeur ne peut pas être égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="dec87-118">This value cannot be zero.</span></span> <span data-ttu-id="dec87-119">Si tous les bits de `usRevisionNumber` sont définis, le numéro de révision n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="dec87-119">If all the bits of `usRevisionNumber` are set, the revision number is not specified.</span></span>|  
|`szLocale`|<span data-ttu-id="dec87-120">Une liste de noms de paramètres régionaux conformément à la spécification RFC1766, séparée par des points-virgules, spécifiant les paramètres régionaux pris en charge par l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="dec87-120">A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly.</span></span> <span data-ttu-id="dec87-121">Une valeur null indique l’indépendance des paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="dec87-121">A null value indicates locale independence.</span></span> <span data-ttu-id="dec87-122">**Remarque :**  Dans le .NET Framework version 1.0, vous ne pouvez pas spécifier plusieurs paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="dec87-122">**Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.</span></span>|  
|`cbLocale`|<span data-ttu-id="dec87-123">La taille en caractères larges de `szLocale`.</span><span class="sxs-lookup"><span data-stu-id="dec87-123">The size in wide characters of `szLocale`.</span></span>|  
|`rdwProcessor`|<span data-ttu-id="dec87-124">Un tableau d’identificateurs, tel que défini dans Winnt.h, pour les types de processeurs qui sont pris en charge par l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="dec87-124">An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly.</span></span> <span data-ttu-id="dec87-125">Une valeur NULL indique l’indépendance des processeurs.</span><span class="sxs-lookup"><span data-stu-id="dec87-125">A NULL value indicates processor independence.</span></span>|  
|`ulProcessor`|<span data-ttu-id="dec87-126">La longueur de la `rdwProcessor` tableau.</span><span class="sxs-lookup"><span data-stu-id="dec87-126">The length of the `rdwProcessor` array.</span></span>|  
|`rOS`|<span data-ttu-id="dec87-127">Un tableau de [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instances spécifiant les systèmes d’exploitation pris en charge par l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="dec87-127">An array of [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly.</span></span> <span data-ttu-id="dec87-128">Une valeur NULL indique l’indépendance du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="dec87-128">A NULL value indicates operating-system independence.</span></span>|  
|`ulOS`|<span data-ttu-id="dec87-129">La longueur de la `rOS` tableau.</span><span class="sxs-lookup"><span data-stu-id="dec87-129">The length of the `rOS` array.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dec87-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="dec87-130">Requirements</span></span>  
 <span data-ttu-id="dec87-131">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dec87-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dec87-132">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dec87-132">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dec87-133">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dec87-133">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dec87-134">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dec87-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dec87-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dec87-135">See also</span></span>

- [<span data-ttu-id="dec87-136">Structures de métadonnées</span><span class="sxs-lookup"><span data-stu-id="dec87-136">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="dec87-137">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="dec87-137">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="dec87-138">OSINFO, structure</span><span class="sxs-lookup"><span data-stu-id="dec87-138">OSINFO Structure</span></span>](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
