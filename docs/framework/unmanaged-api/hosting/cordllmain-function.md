---
title: _CorDllMain, fonction
ms.date: 03/30/2017
api_name:
- _CorDllMain
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorDllMain
helpviewer_keywords:
- _CorDllMain function [.NET Framework hosting]
ms.assetid: bc7b51cf-39d3-48ec-a5cb-2f179fbefff8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a02a899fd6fbffd04ef25913adb6a65ade27177
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755661"
---
# <a name="cordllmain-function"></a><span data-ttu-id="6c21a-102">\_CorDllMain (fonction)</span><span class="sxs-lookup"><span data-stu-id="6c21a-102">\_CorDllMain Function</span></span>

<span data-ttu-id="6c21a-103">Initialise le common language runtime (CLR), recherche le point d’entrée managé dans l’en-tête CLR de l’assembly DLL et commence l’exécution.</span><span class="sxs-lookup"><span data-stu-id="6c21a-103">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c21a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c21a-104">Syntax</span></span>  
  
```cpp  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c21a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6c21a-105">Parameters</span></span>  
 `hInst`  
 <span data-ttu-id="6c21a-106">[in] Le handle d’instance du module chargé.</span><span class="sxs-lookup"><span data-stu-id="6c21a-106">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="6c21a-107">[in] Indique la raison pour laquelle la fonction de point d’entrée DLL est appelée.</span><span class="sxs-lookup"><span data-stu-id="6c21a-107">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="6c21a-108">Ce paramètre peut être une des valeurs suivantes : DLL\_PROCESS_ATTACH, DLL\_THREAD\_attacher, DLL\_THREAD\_attacher ou DLL\_processus\_détacher.</span><span class="sxs-lookup"><span data-stu-id="6c21a-108">This parameter can be one of the following values: DLL\_PROCESS_ATTACH, DLL\_THREAD\_ATTACH, DLL\_THREAD\_ATTACH, or DLL\_PROCESS\_DETACH.</span></span> <span data-ttu-id="6c21a-109">Pour obtenir une description de ces valeurs, consultez le `DllMain` documentation dans le kit Platform SDK.</span><span class="sxs-lookup"><span data-stu-id="6c21a-109">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="6c21a-110">[in] Inutilisé.</span><span class="sxs-lookup"><span data-stu-id="6c21a-110">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c21a-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6c21a-111">Return Value</span></span>  
 <span data-ttu-id="6c21a-112">Cette méthode retourne `true` de réussite et `false` si une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="6c21a-112">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c21a-113">Notes</span><span class="sxs-lookup"><span data-stu-id="6c21a-113">Remarks</span></span>  
 <span data-ttu-id="6c21a-114">Cette fonction est appelée par le chargeur du système d’exploitation pour les assemblys DLL.</span><span class="sxs-lookup"><span data-stu-id="6c21a-114">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="6c21a-115">Pour les assemblys exécutables, le chargeur appelle le [ \_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) fonctionner à la place.</span><span class="sxs-lookup"><span data-stu-id="6c21a-115">For executable assemblies, the loader calls the [\_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="6c21a-116">Le chargeur du système d’exploitation appelle cette méthode, quel que soit le point d’entrée spécifié dans le fichier DLL.</span><span class="sxs-lookup"><span data-stu-id="6c21a-116">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
<span data-ttu-id="6c21a-117">Le `_CorDllMain` fonction est appelée directement par le chargeur du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="6c21a-117">The `_CorDllMain` function is called directly by the operating system loader.</span></span>
  
 <span data-ttu-id="6c21a-118">Pour plus d’informations, consultez la section Remarques dans le [ \_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="6c21a-118">For additional information, see the Remarks section in the [\_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c21a-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6c21a-119">Requirements</span></span>  

 <span data-ttu-id="6c21a-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c21a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c21a-121">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6c21a-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6c21a-122">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6c21a-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6c21a-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c21a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c21a-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c21a-124">See also</span></span>

- [<span data-ttu-id="6c21a-125">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="6c21a-125">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
