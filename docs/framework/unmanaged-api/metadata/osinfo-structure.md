---
title: OSINFO, structure
ms.date: 03/30/2017
api_name:
- OSINFO
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OSINFO
helpviewer_keywords:
- OSINFO structure [.NET Framework metadata]
ms.assetid: fac7b480-7adb-4450-a5e9-690fed81ffae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a36cd3c5fb638799a735e4b4a1a98959500300b5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761597"
---
# <a name="osinfo-structure"></a><span data-ttu-id="2719c-102">OSINFO, structure</span><span class="sxs-lookup"><span data-stu-id="2719c-102">OSINFO Structure</span></span>
<span data-ttu-id="2719c-103">Contient des détails sur le système d’exploitation pour un assembly ou un module.</span><span class="sxs-lookup"><span data-stu-id="2719c-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2719c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2719c-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="2719c-105">Membres</span><span class="sxs-lookup"><span data-stu-id="2719c-105">Members</span></span>  
  
|<span data-ttu-id="2719c-106">Membre</span><span class="sxs-lookup"><span data-stu-id="2719c-106">Member</span></span>|<span data-ttu-id="2719c-107">Description</span><span class="sxs-lookup"><span data-stu-id="2719c-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="2719c-108">Une des valeurs d’identificateur définis par la fonction de la plateforme Microsoft Windows `GetVersionEx`.</span><span class="sxs-lookup"><span data-stu-id="2719c-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="2719c-109">Les valeurs suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="2719c-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="2719c-110">-VER_PLATFORM_WIN32s, ou 0 x 0000, pour spécifier Microsoft Windows 3.1.</span><span class="sxs-lookup"><span data-stu-id="2719c-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="2719c-111">-VER_PLATFORM_WIN32_WINDOWS, ou 0 x 0001, pour spécifier Windows 95, Windows 98 ou les systèmes d’exploitation hérités à partir de celles-ci.</span><span class="sxs-lookup"><span data-stu-id="2719c-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="2719c-112">-VER_PLATFORM_WIN32_NT, ou 0 x 0010, pour spécifier Windows NT ou les systèmes d’exploitation hérités à partir de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="2719c-112">-   VER_PLATFORM_WIN32_NT, or 0x0010, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="2719c-113">La version principale du système d’exploitation, ou une valeur NULL pour indiquer n’importe quelle version.</span><span class="sxs-lookup"><span data-stu-id="2719c-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="2719c-114">La version secondaire du système d’exploitation, ou une valeur NULL pour indiquer n’importe quelle version.</span><span class="sxs-lookup"><span data-stu-id="2719c-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2719c-115">Notes</span><span class="sxs-lookup"><span data-stu-id="2719c-115">Remarks</span></span>  
 <span data-ttu-id="2719c-116">`OSINFO` est basé sur le `OSVERSIONINFOEX` structure qui est utilisé dans les appels à la fonction de la plateforme Microsoft Windows `GetVersionEx`.</span><span class="sxs-lookup"><span data-stu-id="2719c-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="2719c-117">Cette structure est utilisée par la structure ASSEMBLYMETADATA pour indiquer sa prise en charge du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="2719c-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2719c-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2719c-118">Requirements</span></span>  
 <span data-ttu-id="2719c-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2719c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2719c-120">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2719c-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2719c-121">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2719c-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2719c-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2719c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2719c-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2719c-123">See also</span></span>

- [<span data-ttu-id="2719c-124">Structures de métadonnées</span><span class="sxs-lookup"><span data-stu-id="2719c-124">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="2719c-125">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="2719c-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
