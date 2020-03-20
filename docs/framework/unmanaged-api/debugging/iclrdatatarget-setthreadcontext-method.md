---
title: ICLRDataTarget::SetThreadContext, méthode
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetThreadContext
helpviewer_keywords:
- SetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::SetThreadContext method [.NET Framework debugging]
ms.assetid: 103c8502-81fe-40d7-9c1e-9008d8fb19e1
topic_type:
- apiref
ms.openlocfilehash: d76a907434b12b85aaedeef169390ec6f0df724a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179128"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="b61df-102">ICLRDataTarget::SetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="b61df-102">ICLRDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="b61df-103">Définit le contexte actuel du thread spécifié dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="b61df-103">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="b61df-104">Cette méthode est appelée par les services d’accès aux données de l’heure courante (CLR).</span><span class="sxs-lookup"><span data-stu-id="b61df-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b61df-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b61df-105">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b61df-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b61df-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="b61df-107">[dans] L’identifiant du système d’exploitation d’un thread dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="b61df-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="b61df-108">[dans] La taille du contexte.</span><span class="sxs-lookup"><span data-stu-id="b61df-108">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="b61df-109">[dans] Pointeur vers un tampon contenant le contexte.</span><span class="sxs-lookup"><span data-stu-id="b61df-109">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="b61df-110">Les données `context` dans le tampon seront dans le `CONTEXT` format de la structure Win32.</span><span class="sxs-lookup"><span data-stu-id="b61df-110">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="b61df-111">Le contexte spécifie les données d’enregistrement spécifiques `CONTEXT` au processeur, de sorte que la définition de la structure Win32 dépend de l’architecture du processeur.</span><span class="sxs-lookup"><span data-stu-id="b61df-111">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="b61df-112">Consultez le fichier d’en-tête WinNT.h `CONTEXT` pour la définition de la structure Win32.</span><span class="sxs-lookup"><span data-stu-id="b61df-112">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b61df-113">Notes </span><span class="sxs-lookup"><span data-stu-id="b61df-113">Remarks</span></span>  
 <span data-ttu-id="b61df-114">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="b61df-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b61df-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b61df-115">Requirements</span></span>  
 <span data-ttu-id="b61df-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b61df-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b61df-117">**En-tête:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="b61df-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="b61df-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b61df-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b61df-119">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b61df-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b61df-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b61df-120">See also</span></span>

- [<span data-ttu-id="b61df-121">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="b61df-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
