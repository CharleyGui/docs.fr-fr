---
title: AssemblyFlags, énumération
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
ms.openlocfilehash: 561b4d68a574a2859286fb5f2e2d950518a9d29d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732774"
---
# <a name="assemblyflags-enumeration"></a><span data-ttu-id="cae13-102">AssemblyFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="cae13-102">AssemblyFlags Enumeration</span></span>

<span data-ttu-id="cae13-103">Contient des valeurs qui décrivent les fonctionnalités d’exécution d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="cae13-103">Contains values that describe run-time features of an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cae13-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cae13-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="cae13-105">Membres</span><span class="sxs-lookup"><span data-stu-id="cae13-105">Members</span></span>  
  
|<span data-ttu-id="cae13-106">Membre</span><span class="sxs-lookup"><span data-stu-id="cae13-106">Member</span></span>|<span data-ttu-id="cae13-107">Description</span><span class="sxs-lookup"><span data-stu-id="cae13-107">Description</span></span>|  
|------------|-----------------|  
|`afImplicitExportedTypes`|<span data-ttu-id="cae13-108">Spécifie que les définitions de type exporté sont implicites dans les fichiers qui composent l’assembly.</span><span class="sxs-lookup"><span data-stu-id="cae13-108">Specifies that exported type definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="cae13-109">Dans les versions 1,0 et 1,1 de .NET Framework, cette valeur est toujours supposée être définie.</span><span class="sxs-lookup"><span data-stu-id="cae13-109">In the .NET Framework versions 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afImplicitResources`|<span data-ttu-id="cae13-110">Spécifie que les définitions de ressource sont implicites dans les fichiers qui composent l’assembly.</span><span class="sxs-lookup"><span data-stu-id="cae13-110">Specifies that resource definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="cae13-111">Dans les .NET Framework 1,0 et 1,1, cette valeur est toujours supposée être définie.</span><span class="sxs-lookup"><span data-stu-id="cae13-111">In the .NET Framework 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afNonSideBySideAppDomain`|<span data-ttu-id="cae13-112">Spécifie que l’assembly ne peut pas s’exécuter avec d’autres versions si elles s’exécutent dans le même domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="cae13-112">Specifies that the assembly cannot execute with other versions if they are running in the same application domain.</span></span>|  
|`afNonSideBySideProcess`|<span data-ttu-id="cae13-113">Spécifie que l’assembly ne peut pas s’exécuter avec d’autres versions si elles s’exécutent dans le même processus.</span><span class="sxs-lookup"><span data-stu-id="cae13-113">Specifies that the assembly cannot execute with other versions if they are running in the same process.</span></span>|  
|`afNonSideBySideMachine`|<span data-ttu-id="cae13-114">Spécifie que l’assembly ne peut pas s’exécuter avec d’autres versions si elles s’exécutent sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="cae13-114">Specifies that the assembly cannot execute with other versions if they are running on the same computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cae13-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="cae13-115">Remarks</span></span>  

 <span data-ttu-id="cae13-116">Les valeurs comprises entre 0x0010 et 0x0070, incluses, sont utilisées pour décrire les fonctionnalités de compatibilité côte à côte de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="cae13-116">The values between 0x0010 and 0x0070, inclusive, are used to describe side-by-side compatibility features of the referenced assembly.</span></span> <span data-ttu-id="cae13-117">Si aucune de ces valeurs n’est définie, l’assembly est supposé être compatible côte à côte.</span><span class="sxs-lookup"><span data-stu-id="cae13-117">If none of these values are set, the assembly is assumed to be side-by-side compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cae13-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cae13-118">Requirements</span></span>  

 <span data-ttu-id="cae13-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cae13-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cae13-120">**En-tête :** MsCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cae13-120">**Header:** MsCorEE.h</span></span>  
  
 <span data-ttu-id="cae13-121">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cae13-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cae13-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cae13-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cae13-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cae13-123">See also</span></span>

- [<span data-ttu-id="cae13-124">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="cae13-124">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="cae13-125">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="cae13-125">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
