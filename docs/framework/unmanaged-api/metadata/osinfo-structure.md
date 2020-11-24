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
ms.openlocfilehash: 49e29cc0367d5162dffcd641b163fd7b9a56ffd0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672888"
---
# <a name="osinfo-structure"></a><span data-ttu-id="c3706-102">OSINFO, structure</span><span class="sxs-lookup"><span data-stu-id="c3706-102">OSINFO Structure</span></span>

<span data-ttu-id="c3706-103">Contient des détails sur le système d’exploitation d’un assembly ou d’un module.</span><span class="sxs-lookup"><span data-stu-id="c3706-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3706-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3706-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;
    DWORD   dwOSMinorVersion;
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="c3706-105">Membres</span><span class="sxs-lookup"><span data-stu-id="c3706-105">Members</span></span>  
  
|<span data-ttu-id="c3706-106">Membre</span><span class="sxs-lookup"><span data-stu-id="c3706-106">Member</span></span>|<span data-ttu-id="c3706-107">Description</span><span class="sxs-lookup"><span data-stu-id="c3706-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="c3706-108">L’une des valeurs d’identificateur définie par la fonction de la plate-forme Microsoft Windows `GetVersionEx` .</span><span class="sxs-lookup"><span data-stu-id="c3706-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="c3706-109">Les valeurs suivantes sont admises :</span><span class="sxs-lookup"><span data-stu-id="c3706-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="c3706-110">-VER_PLATFORM_WIN32s, ou 0x0000, pour spécifier Microsoft Windows 3,1.</span><span class="sxs-lookup"><span data-stu-id="c3706-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="c3706-111">-VER_PLATFORM_WIN32_WINDOWS, ou 0x0001, pour spécifier les systèmes d’exploitation Windows 95, Windows 98 ou décroissants.</span><span class="sxs-lookup"><span data-stu-id="c3706-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="c3706-112">-VER_PLATFORM_WIN32_NT, ou 0x0002, pour spécifier les systèmes d’exploitation Windows NT ou décroissants.</span><span class="sxs-lookup"><span data-stu-id="c3706-112">-   VER_PLATFORM_WIN32_NT, or 0x0002, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="c3706-113">La version principale du système d’exploitation, ou une valeur NULL pour indiquer n’importe quelle version.</span><span class="sxs-lookup"><span data-stu-id="c3706-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="c3706-114">La version mineure du système d’exploitation, ou une valeur NULL pour indiquer n’importe quelle version.</span><span class="sxs-lookup"><span data-stu-id="c3706-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3706-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="c3706-115">Remarks</span></span>  

 <span data-ttu-id="c3706-116">`OSINFO` est basé sur la `OSVERSIONINFOEX` structure utilisée dans les appels à la fonction de la plate-forme Microsoft Windows `GetVersionEx` .</span><span class="sxs-lookup"><span data-stu-id="c3706-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="c3706-117">Cette structure est utilisée par la structure ASSEMBLYMETADATA pour indiquer sa prise en charge par le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="c3706-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3706-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c3706-118">Requirements</span></span>  

 <span data-ttu-id="c3706-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3706-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3706-120">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c3706-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c3706-121">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c3706-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c3706-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3706-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3706-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3706-123">See also</span></span>

- [<span data-ttu-id="c3706-124">Structures de métadonnées</span><span class="sxs-lookup"><span data-stu-id="c3706-124">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="c3706-125">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="c3706-125">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
