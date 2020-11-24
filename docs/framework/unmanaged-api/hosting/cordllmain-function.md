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
ms.openlocfilehash: 1b3ebcabc66ee7ca29245bb02d958be311bc65fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673694"
---
# <a name="_cordllmain-function"></a><span data-ttu-id="825e2-102">\_CorDllMain fonction)</span><span class="sxs-lookup"><span data-stu-id="825e2-102">\_CorDllMain Function</span></span>

<span data-ttu-id="825e2-103">Initialise le common language runtime (CLR), localise le point d’entrée managé dans l’en-tête CLR de l’assembly de DLL et commence l’exécution.</span><span class="sxs-lookup"><span data-stu-id="825e2-103">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="825e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="825e2-104">Syntax</span></span>  
  
```cpp  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="825e2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="825e2-105">Parameters</span></span>  

 `hInst`  
 <span data-ttu-id="825e2-106">dans Handle d’instance du module chargé.</span><span class="sxs-lookup"><span data-stu-id="825e2-106">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="825e2-107">dans Indique la raison pour laquelle la fonction de point d’entrée de la DLL est appelée.</span><span class="sxs-lookup"><span data-stu-id="825e2-107">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="825e2-108">Ce paramètre peut avoir l’une des valeurs suivantes : DLL \_ PROCESS_ATTACH, \_ attachement de thread dll \_ , \_ attachement de thread dll \_ ou \_ \_ détachement de processus dll.</span><span class="sxs-lookup"><span data-stu-id="825e2-108">This parameter can be one of the following values: DLL\_PROCESS_ATTACH, DLL\_THREAD\_ATTACH, DLL\_THREAD\_ATTACH, or DLL\_PROCESS\_DETACH.</span></span> <span data-ttu-id="825e2-109">Pour obtenir une description de ces valeurs, consultez la `DllMain` documentation du kit de développement Platform SDK.</span><span class="sxs-lookup"><span data-stu-id="825e2-109">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="825e2-110">[in] Inutilisé.</span><span class="sxs-lookup"><span data-stu-id="825e2-110">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="825e2-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="825e2-111">Return Value</span></span>  

 <span data-ttu-id="825e2-112">Cette méthode retourne `true` pour réussite et `false` si une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="825e2-112">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="825e2-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="825e2-113">Remarks</span></span>  

 <span data-ttu-id="825e2-114">Cette fonction est appelée par le chargeur du système d’exploitation pour les assemblys DLL.</span><span class="sxs-lookup"><span data-stu-id="825e2-114">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="825e2-115">Pour les assemblys exécutables, le chargeur appelle à la place la fonction [ \_ du CORExeMain](corexemain-function.md) .</span><span class="sxs-lookup"><span data-stu-id="825e2-115">For executable assemblies, the loader calls the [\_CorExeMain](corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="825e2-116">Le chargeur du système d’exploitation appelle cette méthode quel que soit le point d’entrée spécifié dans le fichier DLL.</span><span class="sxs-lookup"><span data-stu-id="825e2-116">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
<span data-ttu-id="825e2-117">La `_CorDllMain` fonction est appelée directement par le chargeur du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="825e2-117">The `_CorDllMain` function is called directly by the operating system loader.</span></span>
  
 <span data-ttu-id="825e2-118">Pour plus d’informations, consultez la section Notes de la rubrique [ \_ CorValidateImage](corvalidateimage-function.md) .</span><span class="sxs-lookup"><span data-stu-id="825e2-118">For additional information, see the Remarks section in the [\_CorValidateImage](corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="825e2-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="825e2-119">Requirements</span></span>  

 <span data-ttu-id="825e2-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="825e2-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="825e2-121">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="825e2-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="825e2-122">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="825e2-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="825e2-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="825e2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="825e2-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="825e2-124">See also</span></span>

- [<span data-ttu-id="825e2-125">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="825e2-125">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
