---
title: RUNTIME_INFO_FLAGS, énumération
ms.date: 03/30/2017
api_name:
- RUNTIME_INFO_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RUNTIME_INFO_FLAGS
helpviewer_keywords:
- RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type:
- apiref
ms.openlocfilehash: da830aaaced179fed642340c33e7b7c37b350aa3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006556"
---
# <a name="runtime_info_flags-enumeration"></a><span data-ttu-id="710c1-102">RUNTIME_INFO_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="710c1-102">RUNTIME_INFO_FLAGS Enumeration</span></span>
<span data-ttu-id="710c1-103">Contient des valeurs qui indiquent les informations relatives au common language runtime (CLR) qui doivent être retournées.</span><span class="sxs-lookup"><span data-stu-id="710c1-103">Contains values that indicate what information about the common language runtime (CLR) should be returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="710c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="710c1-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    RUNTIME_INFO_UPGRADE_VERSION             = 0x01,  
    RUNTIME_INFO_REQUEST_IA64                = 0x02,  
    RUNTIME_INFO_REQUEST_AMD64               = 0x04,  
    RUNTIME_INFO_REQUEST_X86                 = 0x08,  
    RUNTIME_INFO_DONT_RETURN_DIRECTORY       = 0x10,  
    RUNTIME_INFO_DONT_RETURN_VERSION         = 0x20,  
    RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG      = 0x40,  
    RUNTIME_INFO_IGNORE_ERROR_MODE           = 0x1000  
  
} RUNTIME_INFO_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="710c1-105">Membres</span><span class="sxs-lookup"><span data-stu-id="710c1-105">Members</span></span>  
  
|<span data-ttu-id="710c1-106">Membre</span><span class="sxs-lookup"><span data-stu-id="710c1-106">Member</span></span>|<span data-ttu-id="710c1-107">Description</span><span class="sxs-lookup"><span data-stu-id="710c1-107">Description</span></span>|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|<span data-ttu-id="710c1-108">Indique que les informations de répertoire ne doivent pas être incluses.</span><span class="sxs-lookup"><span data-stu-id="710c1-108">Indicates that directory information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|<span data-ttu-id="710c1-109">Indique que les informations de version ne doivent pas être incluses.</span><span class="sxs-lookup"><span data-stu-id="710c1-109">Indicates that version information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|<span data-ttu-id="710c1-110">Indique qu’une boîte de dialogue d’erreur ne doit pas s’afficher en cas d’échec.</span><span class="sxs-lookup"><span data-stu-id="710c1-110">Indicates that an error dialog box should not be shown upon failure.</span></span>|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|<span data-ttu-id="710c1-111">Indique que les effets de l’appel de la fonction [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) avec l’indicateur SEM_FAILCRITICALERRORS doivent être substitués.</span><span class="sxs-lookup"><span data-stu-id="710c1-111">Indicates that the effects of calling the [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) function with the SEM_FAILCRITICALERRORS flag should be overridden.</span></span> <span data-ttu-id="710c1-112">Autrement dit, une boîte de dialogue d’installation doit s’afficher en cas d’échec, au lieu d’être supprimée.</span><span class="sxs-lookup"><span data-stu-id="710c1-112">That is, an installation dialog box should be shown upon failure, instead of being suppressed.</span></span>|  
|`RUNTIME_INFO_REQUEST_AMD64`|<span data-ttu-id="710c1-113">Indique une demande d’informations sur une version compatible AMD-64 du Runtime.</span><span class="sxs-lookup"><span data-stu-id="710c1-113">Indicates a request for information about an AMD-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_IA64`|<span data-ttu-id="710c1-114">Indique une demande d’informations sur une version compatible IA-64 du Runtime.</span><span class="sxs-lookup"><span data-stu-id="710c1-114">Indicates a request for information about an IA-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_X86`|<span data-ttu-id="710c1-115">Indique une demande d’informations sur une version compatible x86 du Runtime.</span><span class="sxs-lookup"><span data-stu-id="710c1-115">Indicates a request for information about an x86-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_UPGRADE_VERSION`|<span data-ttu-id="710c1-116">Indique que les informations de mise à niveau de version doivent être incluses.</span><span class="sxs-lookup"><span data-stu-id="710c1-116">Indicates that version upgrade information should be included.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="710c1-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="710c1-117">Remarks</span></span>  
 <span data-ttu-id="710c1-118">Les indicateurs d’architecture de la plateforme suivants ne peuvent être spécifiés qu’une seule fois et ne peuvent pas être combinés :</span><span class="sxs-lookup"><span data-stu-id="710c1-118">The following platform architecture flags can be specified only one at a time and cannot be combined:</span></span>  
  
- <span data-ttu-id="710c1-119">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="710c1-119">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="710c1-120">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="710c1-120">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="710c1-121">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="710c1-121">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="710c1-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="710c1-122">Requirements</span></span>  
 <span data-ttu-id="710c1-123">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="710c1-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="710c1-124">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="710c1-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="710c1-125">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="710c1-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="710c1-126">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="710c1-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="710c1-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="710c1-127">See also</span></span>

- [<span data-ttu-id="710c1-128">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="710c1-128">Hosting Enumerations</span></span>](hosting-enumerations.md)
