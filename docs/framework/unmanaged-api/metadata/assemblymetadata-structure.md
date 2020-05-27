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
ms.openlocfilehash: 5c7211fc2523b70313a1e4d4d9d2da0dcecd1d32
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009429"
---
# <a name="assemblymetadata-structure"></a><span data-ttu-id="aada1-102">ASSEMBLYMETADATA, structure</span><span class="sxs-lookup"><span data-stu-id="aada1-102">ASSEMBLYMETADATA Structure</span></span>
<span data-ttu-id="aada1-103">Contient des informations sur l’assembly référencé, y compris sa version et son niveau de prise en charge pour les paramètres régionaux, les processeurs et les systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="aada1-103">Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aada1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aada1-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="aada1-105">Membres</span><span class="sxs-lookup"><span data-stu-id="aada1-105">Members</span></span>  
  
|<span data-ttu-id="aada1-106">Membre</span><span class="sxs-lookup"><span data-stu-id="aada1-106">Member</span></span>|<span data-ttu-id="aada1-107">Description</span><span class="sxs-lookup"><span data-stu-id="aada1-107">Description</span></span>|  
|------------|-----------------|  
|`usMajorVersion`|<span data-ttu-id="aada1-108">Numéro de version principale de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="aada1-108">The major version number of the referenced assembly.</span></span> <span data-ttu-id="aada1-109">Cette valeur ne peut pas être égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="aada1-109">This value cannot be zero.</span></span> <span data-ttu-id="aada1-110">Si tous les bits de `usMajorVersion` sont définis, la version principale n’est pas spécifiée.</span><span class="sxs-lookup"><span data-stu-id="aada1-110">If all the bits of `usMajorVersion` are set, the major version is not specified.</span></span>|  
|`usMinorVersion`|<span data-ttu-id="aada1-111">Numéro de version mineure de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="aada1-111">The minor version number of the referenced assembly.</span></span> <span data-ttu-id="aada1-112">Cette valeur ne peut pas être égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="aada1-112">This value cannot be zero.</span></span> <span data-ttu-id="aada1-113">Si tous les bits de `usMinorVersion` sont définis, la version mineure n’est pas spécifiée.</span><span class="sxs-lookup"><span data-stu-id="aada1-113">If all the bits of `usMinorVersion` are set, the minor version is not specified.</span></span>|  
|`usBuildNumber`|<span data-ttu-id="aada1-114">Numéro de build de l'assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="aada1-114">The build number of the referenced assembly.</span></span> <span data-ttu-id="aada1-115">Cette valeur ne peut pas être égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="aada1-115">This value cannot be zero.</span></span> <span data-ttu-id="aada1-116">Si tous les bits de `usBuildNumber` sont définis, le numéro de build n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="aada1-116">If all the bits of `usBuildNumber` are set, the build number is not specified.</span></span>|  
|`usRevisionNumber`|<span data-ttu-id="aada1-117">Numéro de révision de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="aada1-117">The revision number of the referenced assembly.</span></span> <span data-ttu-id="aada1-118">Cette valeur ne peut pas être égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="aada1-118">This value cannot be zero.</span></span> <span data-ttu-id="aada1-119">Si tous les bits de `usRevisionNumber` sont définis, le numéro de révision n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="aada1-119">If all the bits of `usRevisionNumber` are set, the revision number is not specified.</span></span>|  
|`szLocale`|<span data-ttu-id="aada1-120">Liste des noms de paramètres régionaux conformes à la spécification RFC1766, séparés par des points-virgules, en spécifiant les paramètres régionaux pris en charge par l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="aada1-120">A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly.</span></span> <span data-ttu-id="aada1-121">Une valeur null indique l’indépendance des paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="aada1-121">A null value indicates locale independence.</span></span> <span data-ttu-id="aada1-122">**Remarque :**  Dans le .NET Framework version 1,0, vous ne pouvez pas spécifier plusieurs paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="aada1-122">**Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.</span></span>|  
|`cbLocale`|<span data-ttu-id="aada1-123">Taille en caractères larges de `szLocale` .</span><span class="sxs-lookup"><span data-stu-id="aada1-123">The size in wide characters of `szLocale`.</span></span>|  
|`rdwProcessor`|<span data-ttu-id="aada1-124">Tableau d’identificateurs, tel que défini dans Winnt. h, pour les types de processeurs pris en charge par l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="aada1-124">An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly.</span></span> <span data-ttu-id="aada1-125">Une valeur NULL indique l’indépendance du processeur.</span><span class="sxs-lookup"><span data-stu-id="aada1-125">A NULL value indicates processor independence.</span></span>|  
|`ulProcessor`|<span data-ttu-id="aada1-126">Longueur du tableau `rdwProcessor`.</span><span class="sxs-lookup"><span data-stu-id="aada1-126">The length of the `rdwProcessor` array.</span></span>|  
|`rOS`|<span data-ttu-id="aada1-127">Tableau d’instances [OSInfo,](osinfo-structure.md) spécifiant les systèmes d’exploitation pris en charge par l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="aada1-127">An array of [OSINFO](osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly.</span></span> <span data-ttu-id="aada1-128">Une valeur NULL indique l’indépendance du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="aada1-128">A NULL value indicates operating-system independence.</span></span>|  
|`ulOS`|<span data-ttu-id="aada1-129">Longueur du tableau `rOS`.</span><span class="sxs-lookup"><span data-stu-id="aada1-129">The length of the `rOS` array.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aada1-130">Spécifications</span><span class="sxs-lookup"><span data-stu-id="aada1-130">Requirements</span></span>  
 <span data-ttu-id="aada1-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aada1-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aada1-132">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="aada1-132">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aada1-133">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="aada1-133">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aada1-134">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aada1-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aada1-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aada1-135">See also</span></span>

- [<span data-ttu-id="aada1-136">Structures de métadonnées</span><span class="sxs-lookup"><span data-stu-id="aada1-136">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="aada1-137">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="aada1-137">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="aada1-138">OSINFO, structure</span><span class="sxs-lookup"><span data-stu-id="aada1-138">OSINFO Structure</span></span>](osinfo-structure.md)
