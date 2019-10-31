---
title: ICLRDataTarget3::GetExceptionContextRecord, méthode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetContextRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type:
- apiref
ms.openlocfilehash: 5a090b7c4801e6b2baf56f1d80e7e52f2aaa9293
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73112301"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a><span data-ttu-id="f7c90-102">ICLRDataTarget3::GetExceptionContextRecord, méthode</span><span class="sxs-lookup"><span data-stu-id="f7c90-102">ICLRDataTarget3::GetExceptionContextRecord Method</span></span>
<span data-ttu-id="f7c90-103">Appelée par les services d'accès aux données du CLR (Common Langage Runtime) pour récupérer l'enregistrement de contexte associé au processus cible.</span><span class="sxs-lookup"><span data-stu-id="f7c90-103">Called by the common language runtime (CLR) data access services to retrieve the context record associated with the target process.</span></span> <span data-ttu-id="f7c90-104">Par exemple, pour une cible de vidage, cela équivaut à l’enregistrement de contexte transmis via l’argument `ExceptionParam` à la fonction [entrée](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) dans la bibliothèque d’aide au débogage Windows (dbghelp).</span><span class="sxs-lookup"><span data-stu-id="f7c90-104">For example, for a dump target, this would be equivalent to the context record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7c90-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7c90-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7c90-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f7c90-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="f7c90-107">[en entrée] La taille de la mémoire tampon d'entrée, en octets.</span><span class="sxs-lookup"><span data-stu-id="f7c90-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="f7c90-108">Elle doit être d'une taille suffisante pour contenir l'enregistrement de contexte.</span><span class="sxs-lookup"><span data-stu-id="f7c90-108">This must be large enough to accommodate the context record.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="f7c90-109">[en sortie] Un pointeur vers un type `ULONG32` qui reçoit le nombre d'octets réellement écrits dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="f7c90-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="f7c90-110">[en sortie] Un pointeur vers une mémoire tampon qui reçoit une copie de l'enregistrement de contexte.</span><span class="sxs-lookup"><span data-stu-id="f7c90-110">[out] A pointer to a memory buffer that receives a copy of the context record.</span></span> <span data-ttu-id="f7c90-111">L’enregistrement d’exception est retourné en tant que type de [contexte](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) .</span><span class="sxs-lookup"><span data-stu-id="f7c90-111">The exception record is returned as a [CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7c90-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f7c90-112">Return Value</span></span>  
 <span data-ttu-id="f7c90-113">La valeur de retour est `S_OK` en cas de réussite ou un code d'échec `HRESULT` en cas d'échec.</span><span class="sxs-lookup"><span data-stu-id="f7c90-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="f7c90-114">Les codes `HRESULT` peuvent comprendre, sans y être limités, ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="f7c90-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="f7c90-115">Code de retour</span><span class="sxs-lookup"><span data-stu-id="f7c90-115">Return code</span></span>|<span data-ttu-id="f7c90-116">Description</span><span class="sxs-lookup"><span data-stu-id="f7c90-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="f7c90-117">La méthode a réussi.</span><span class="sxs-lookup"><span data-stu-id="f7c90-117">Method succeeded.</span></span> <span data-ttu-id="f7c90-118">L'enregistrement de contexte a été copié dans la mémoire tampon de sortie.</span><span class="sxs-lookup"><span data-stu-id="f7c90-118">The context record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="f7c90-119">Aucun enregistrement de contexte n'est associé à la cible.</span><span class="sxs-lookup"><span data-stu-id="f7c90-119">No context record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="f7c90-120">La taille de la mémoire tampon d'entrée est insuffisante pour contenir l'enregistrement de contexte.</span><span class="sxs-lookup"><span data-stu-id="f7c90-120">The input buffer size is not large enough to accommodate the context record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7c90-121">Notes</span><span class="sxs-lookup"><span data-stu-id="f7c90-121">Remarks</span></span>  
 <span data-ttu-id="f7c90-122">[Context](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) est une structure spécifique à la plateforme, définie dans les en-têtes fournis par l’SDK Windows.</span><span class="sxs-lookup"><span data-stu-id="f7c90-122">[CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) is a platform-specific structure defined in headers provided by the Windows SDK.</span></span>  
  
 <span data-ttu-id="f7c90-123">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="f7c90-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7c90-124">spécifications</span><span class="sxs-lookup"><span data-stu-id="f7c90-124">Requirements</span></span>  
 <span data-ttu-id="f7c90-125">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7c90-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7c90-126">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="f7c90-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="f7c90-127">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7c90-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7c90-128">**Versions du .NET Framework :** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f7c90-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7c90-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7c90-129">See also</span></span>

- [<span data-ttu-id="f7c90-130">ICLRDataTarget3, interface</span><span class="sxs-lookup"><span data-stu-id="f7c90-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [<span data-ttu-id="f7c90-131">GetExceptionRecord, méthode</span><span class="sxs-lookup"><span data-stu-id="f7c90-131">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
- [<span data-ttu-id="f7c90-132">GetExceptionThreadID, méthode</span><span class="sxs-lookup"><span data-stu-id="f7c90-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
