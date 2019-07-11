---
title: _CorExeMain, fonction
ms.date: 03/30/2017
api_name:
- _CorExeMain
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain
helpviewer_keywords:
- _CorExeMain function [.NET Framework hosting]
ms.assetid: 898f76e2-16f4-4a63-b7d9-dad2d3824d8a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f97e90e3953a01f07d77e604628fbdb79eb9efa0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779180"
---
# <a name="corexemain-function"></a><span data-ttu-id="47d4e-102">_CorExeMain, fonction</span><span class="sxs-lookup"><span data-stu-id="47d4e-102">_CorExeMain Function</span></span>
<span data-ttu-id="47d4e-103">Initialise le common language runtime (CLR), recherche le point d’entrée managé dans l’en-tête CLR de l’assembly exécutable et commence l’exécution.</span><span class="sxs-lookup"><span data-stu-id="47d4e-103">Initializes the common language runtime (CLR), locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47d4e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47d4e-104">Syntax</span></span>  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="47d4e-105">Notes</span><span class="sxs-lookup"><span data-stu-id="47d4e-105">Remarks</span></span>  
 <span data-ttu-id="47d4e-106">Cette fonction est appelée par le chargeur de processus créés à partir d’assemblys exécutables managés.</span><span class="sxs-lookup"><span data-stu-id="47d4e-106">This function is called by the loader in processes created from managed executable assemblies.</span></span> <span data-ttu-id="47d4e-107">Pour les assemblys DLL, le chargeur appelle le [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) fonctionner à la place.</span><span class="sxs-lookup"><span data-stu-id="47d4e-107">For DLL assemblies, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="47d4e-108">Le chargeur du système d’exploitation appelle cette méthode, quel que soit le point d’entrée spécifié dans le fichier image.</span><span class="sxs-lookup"><span data-stu-id="47d4e-108">The operating system loader calls this method regardless of the entry point specified in the image file.</span></span>  
  
 <span data-ttu-id="47d4e-109">Dans Windows 98, Windows ME, Windows NT et Windows 2000, le `_CorExeMain` fonction est appelée indirectement via une correction dans le chargeur du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="47d4e-109">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorExeMain` function is called indirectly through a fixup in the operating system loader.</span></span> <span data-ttu-id="47d4e-110">Dans tous les autres versions de Windows, elle est appelée directement par le chargeur du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="47d4e-110">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="47d4e-111">Pour plus d’informations, consultez la section Remarques dans le [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="47d4e-111">For additional information, see the Remarks section in the [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47d4e-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="47d4e-112">Requirements</span></span>  
 <span data-ttu-id="47d4e-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47d4e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47d4e-114">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="47d4e-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="47d4e-115">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="47d4e-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="47d4e-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47d4e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47d4e-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47d4e-117">See also</span></span>

- [<span data-ttu-id="47d4e-118">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="47d4e-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
