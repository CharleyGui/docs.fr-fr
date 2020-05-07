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
ms.openlocfilehash: b8c4b4e585bba4df39a743273221f38ce14a9b9d
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860534"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="c4cfe-102">ICLRDataTarget::SetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="c4cfe-102">ICLRDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="c4cfe-103">Définit le contexte actuel du thread spécifié dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="c4cfe-103">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="c4cfe-104">Cette méthode est appelée par les services d’accès aux données common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="c4cfe-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4cfe-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4cfe-105">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4cfe-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c4cfe-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="c4cfe-107">dans Identificateur de système d’exploitation d’un thread dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="c4cfe-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="c4cfe-108">dans Taille du contexte.</span><span class="sxs-lookup"><span data-stu-id="c4cfe-108">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="c4cfe-109">dans Pointeur vers une mémoire tampon contenant le contexte.</span><span class="sxs-lookup"><span data-stu-id="c4cfe-109">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="c4cfe-110">Les données de la `context` mémoire tampon seront au format de la structure Win32 `CONTEXT` .</span><span class="sxs-lookup"><span data-stu-id="c4cfe-110">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="c4cfe-111">Le contexte spécifie des données de Registre spécifiques au processeur, donc la définition `CONTEXT` de la structure Win32 dépend de l’architecture du processeur.</span><span class="sxs-lookup"><span data-stu-id="c4cfe-111">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="c4cfe-112">Reportez-vous au fichier d’en-tête Winnt. `CONTEXT` h pour la définition de la structure Win32.</span><span class="sxs-lookup"><span data-stu-id="c4cfe-112">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4cfe-113">Notes </span><span class="sxs-lookup"><span data-stu-id="c4cfe-113">Remarks</span></span>  
 <span data-ttu-id="c4cfe-114">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="c4cfe-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4cfe-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c4cfe-115">Requirements</span></span>  
 <span data-ttu-id="c4cfe-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4cfe-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4cfe-117">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="c4cfe-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c4cfe-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4cfe-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4cfe-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4cfe-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4cfe-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4cfe-120">See also</span></span>

- [<span data-ttu-id="c4cfe-121">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="c4cfe-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
