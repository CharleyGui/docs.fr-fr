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
ms.openlocfilehash: c135c051637858682c22db58d562e1d50eea562b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723699"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="4a17b-102">ICLRDataTarget::SetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="4a17b-102">ICLRDataTarget::SetThreadContext Method</span></span>

<span data-ttu-id="4a17b-103">Définit le contexte actuel du thread spécifié dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="4a17b-103">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="4a17b-104">Cette méthode est appelée par les services d’accès aux données common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="4a17b-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a17b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a17b-105">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a17b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4a17b-106">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="4a17b-107">dans Identificateur de système d’exploitation d’un thread dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="4a17b-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="4a17b-108">dans Taille du contexte.</span><span class="sxs-lookup"><span data-stu-id="4a17b-108">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="4a17b-109">dans Pointeur vers une mémoire tampon contenant le contexte.</span><span class="sxs-lookup"><span data-stu-id="4a17b-109">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="4a17b-110">Les données de la `context` mémoire tampon seront au format de la structure Win32 `CONTEXT` .</span><span class="sxs-lookup"><span data-stu-id="4a17b-110">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="4a17b-111">Le contexte spécifie des données de Registre spécifiques au processeur, donc la définition de la `CONTEXT` structure Win32 dépend de l’architecture du processeur.</span><span class="sxs-lookup"><span data-stu-id="4a17b-111">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="4a17b-112">Reportez-vous au fichier d’en-tête Winnt. h pour la définition de la `CONTEXT` structure Win32.</span><span class="sxs-lookup"><span data-stu-id="4a17b-112">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a17b-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="4a17b-113">Remarks</span></span>  

 <span data-ttu-id="4a17b-114">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="4a17b-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a17b-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4a17b-115">Requirements</span></span>  

 <span data-ttu-id="4a17b-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a17b-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a17b-117">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="4a17b-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="4a17b-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a17b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a17b-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a17b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a17b-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a17b-120">See also</span></span>

- [<span data-ttu-id="4a17b-121">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="4a17b-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
