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
ms.openlocfilehash: d66e9bc3a027610d917e15dc9769b92ea1c5fb71
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345601"
---
# <a name="osinfo-structure"></a><span data-ttu-id="7529a-102">OSINFO, structure</span><span class="sxs-lookup"><span data-stu-id="7529a-102">OSINFO Structure</span></span>
<span data-ttu-id="7529a-103">Contient des détails sur le système d’exploitation d’un assembly ou d’un module.</span><span class="sxs-lookup"><span data-stu-id="7529a-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7529a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7529a-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="7529a-105">Members</span><span class="sxs-lookup"><span data-stu-id="7529a-105">Members</span></span>  
  
|<span data-ttu-id="7529a-106">Member</span><span class="sxs-lookup"><span data-stu-id="7529a-106">Member</span></span>|<span data-ttu-id="7529a-107">Description</span><span class="sxs-lookup"><span data-stu-id="7529a-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="7529a-108">L’une des valeurs d’identificateur définie par la fonction de la plate-forme Microsoft Windows `GetVersionEx`.</span><span class="sxs-lookup"><span data-stu-id="7529a-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="7529a-109">Les valeurs suivantes sont admises :</span><span class="sxs-lookup"><span data-stu-id="7529a-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="7529a-110">-VER_PLATFORM_WIN32s, ou 0x0000, pour spécifier Microsoft Windows 3,1.</span><span class="sxs-lookup"><span data-stu-id="7529a-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="7529a-111">-VER_PLATFORM_WIN32_WINDOWS, ou 0x0001, pour spécifier les systèmes d’exploitation Windows 95, Windows 98 ou décroissants.</span><span class="sxs-lookup"><span data-stu-id="7529a-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="7529a-112">-VER_PLATFORM_WIN32_NT, ou 0x0002, pour spécifier les systèmes d’exploitation Windows NT ou décroissants.</span><span class="sxs-lookup"><span data-stu-id="7529a-112">-   VER_PLATFORM_WIN32_NT, or 0x0002, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="7529a-113">La version principale du système d’exploitation, ou une valeur NULL pour indiquer n’importe quelle version.</span><span class="sxs-lookup"><span data-stu-id="7529a-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="7529a-114">La version mineure du système d’exploitation, ou une valeur NULL pour indiquer n’importe quelle version.</span><span class="sxs-lookup"><span data-stu-id="7529a-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7529a-115">Notes</span><span class="sxs-lookup"><span data-stu-id="7529a-115">Remarks</span></span>  
 <span data-ttu-id="7529a-116">`OSINFO` est basé sur la structure de `OSVERSIONINFOEX` utilisée dans les appels à la fonction de la plate-forme Microsoft Windows `GetVersionEx`.</span><span class="sxs-lookup"><span data-stu-id="7529a-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="7529a-117">Cette structure est utilisée par la structure ASSEMBLYMETADATA pour indiquer sa prise en charge par le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="7529a-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7529a-118">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="7529a-118">Requirements</span></span>  
 <span data-ttu-id="7529a-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7529a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7529a-120">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7529a-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7529a-121">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7529a-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7529a-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7529a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7529a-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7529a-123">See also</span></span>

- [<span data-ttu-id="7529a-124">Structures de métadonnées</span><span class="sxs-lookup"><span data-stu-id="7529a-124">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="7529a-125">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="7529a-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
