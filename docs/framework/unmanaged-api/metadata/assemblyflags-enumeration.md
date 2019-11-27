---
title: Énumération AssemblyFlags
ms.date: 03/30/2017
api_name:
- AssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyFlags
helpviewer_keywords:
- AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type:
- apiref
ms.openlocfilehash: ffb5953c843a338b4548253457a0c3b1ca0c20f5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444301"
---
# <a name="assemblyflags-enumeration"></a><span data-ttu-id="76c01-102">Énumération AssemblyFlags</span><span class="sxs-lookup"><span data-stu-id="76c01-102">AssemblyFlags Enumeration</span></span>
<span data-ttu-id="76c01-103">Contient des valeurs qui décrivent les fonctionnalités d’exécution d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="76c01-103">Contains values that describe run-time features of an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76c01-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76c01-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="76c01-105">Membres</span><span class="sxs-lookup"><span data-stu-id="76c01-105">Members</span></span>  
  
|<span data-ttu-id="76c01-106">Membre</span><span class="sxs-lookup"><span data-stu-id="76c01-106">Member</span></span>|<span data-ttu-id="76c01-107">Description</span><span class="sxs-lookup"><span data-stu-id="76c01-107">Description</span></span>|  
|------------|-----------------|  
|`afImplicitExportedTypes`|<span data-ttu-id="76c01-108">Spécifie que les définitions de type exporté sont implicites dans les fichiers qui composent l’assembly.</span><span class="sxs-lookup"><span data-stu-id="76c01-108">Specifies that exported type definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="76c01-109">Dans les versions 1,0 et 1,1 de .NET Framework, cette valeur est toujours supposée être définie.</span><span class="sxs-lookup"><span data-stu-id="76c01-109">In the .NET Framework versions 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afImplicitResources`|<span data-ttu-id="76c01-110">Spécifie que les définitions de ressource sont implicites dans les fichiers qui composent l’assembly.</span><span class="sxs-lookup"><span data-stu-id="76c01-110">Specifies that resource definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="76c01-111">Dans les .NET Framework 1,0 et 1,1, cette valeur est toujours supposée être définie.</span><span class="sxs-lookup"><span data-stu-id="76c01-111">In the .NET Framework 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afNonSideBySideAppDomain`|<span data-ttu-id="76c01-112">Spécifie que l’assembly ne peut pas s’exécuter avec d’autres versions si elles s’exécutent dans le même domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="76c01-112">Specifies that the assembly cannot execute with other versions if they are running in the same application domain.</span></span>|  
|`afNonSideBySideProcess`|<span data-ttu-id="76c01-113">Spécifie que l’assembly ne peut pas s’exécuter avec d’autres versions si elles s’exécutent dans le même processus.</span><span class="sxs-lookup"><span data-stu-id="76c01-113">Specifies that the assembly cannot execute with other versions if they are running in the same process.</span></span>|  
|`afNonSideBySideMachine`|<span data-ttu-id="76c01-114">Spécifie que l’assembly ne peut pas s’exécuter avec d’autres versions si elles s’exécutent sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="76c01-114">Specifies that the assembly cannot execute with other versions if they are running on the same computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76c01-115">Notes</span><span class="sxs-lookup"><span data-stu-id="76c01-115">Remarks</span></span>  
 <span data-ttu-id="76c01-116">Les valeurs comprises entre 0x0010 et 0x0070, incluses, sont utilisées pour décrire les fonctionnalités de compatibilité côte à côte de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="76c01-116">The values between 0x0010 and 0x0070, inclusive, are used to describe side-by-side compatibility features of the referenced assembly.</span></span> <span data-ttu-id="76c01-117">Si aucune de ces valeurs n’est définie, l’assembly est supposé être compatible côte à côte.</span><span class="sxs-lookup"><span data-stu-id="76c01-117">If none of these values are set, the assembly is assumed to be side-by-side compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76c01-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="76c01-118">Requirements</span></span>  
 <span data-ttu-id="76c01-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76c01-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76c01-120">**En-tête :** MsCorEE. h</span><span class="sxs-lookup"><span data-stu-id="76c01-120">**Header:** MsCorEE.h</span></span>  
  
 <span data-ttu-id="76c01-121">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="76c01-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="76c01-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76c01-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76c01-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76c01-123">See also</span></span>

- [<span data-ttu-id="76c01-124">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="76c01-124">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="76c01-125">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="76c01-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
