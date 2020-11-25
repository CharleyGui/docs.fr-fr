---
title: ICLRDataTarget3::GetExceptionRecord, méthode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6643c2af-2ee6-4789-aa25-1d8eaf500c94
topic_type:
- apiref
ms.openlocfilehash: 8f6eaa6ad310e9a01b2307bff091b670c3e1d6cb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723608"
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a><span data-ttu-id="e02f6-102">ICLRDataTarget3::GetExceptionRecord, méthode</span><span class="sxs-lookup"><span data-stu-id="e02f6-102">ICLRDataTarget3::GetExceptionRecord Method</span></span>

<span data-ttu-id="e02f6-103">Appelé par les services d'accès aux données du Common Langage Runtime (CLR) pour récupérer l'enregistrement d'exception associé au processus cible.</span><span class="sxs-lookup"><span data-stu-id="e02f6-103">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span> <span data-ttu-id="e02f6-104">Par exemple, pour une cible de vidage, cela équivaut à l’enregistrement d’exception passé via l' `ExceptionParam` argument à la fonction [entrée](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) dans la bibliothèque d’aide au débogage Windows (dbghelp).</span><span class="sxs-lookup"><span data-stu-id="e02f6-104">For example, for a dump target, this would be equivalent to the exception record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e02f6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e02f6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e02f6-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e02f6-106">Parameters</span></span>  

 `bufferSize`  
 <span data-ttu-id="e02f6-107">[en entrée] La taille de la mémoire tampon d'entrée, en octets.</span><span class="sxs-lookup"><span data-stu-id="e02f6-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="e02f6-108">Doit être égal à `sizeof(` [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) `)` .</span><span class="sxs-lookup"><span data-stu-id="e02f6-108">This must be equal to `sizeof(`[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception)`)`.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="e02f6-109">[en sortie] Un pointeur vers un type `ULONG32` qui reçoit le nombre d'octets réellement écrits dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="e02f6-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="e02f6-110">[en sortie] Un pointeur vers une mémoire tampon qui reçoit une copie de l'enregistrement de l'exception.</span><span class="sxs-lookup"><span data-stu-id="e02f6-110">[out] A pointer to a memory buffer that receives a copy of the exception record.</span></span> <span data-ttu-id="e02f6-111">L’enregistrement d’exception est retourné en tant que type de [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) .</span><span class="sxs-lookup"><span data-stu-id="e02f6-111">The exception record is returned as a [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e02f6-112">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="e02f6-112">Return Value</span></span>  

 <span data-ttu-id="e02f6-113">La valeur de retour est `S_OK` en cas de réussite ou un code d'échec `HRESULT` en cas d'échec.</span><span class="sxs-lookup"><span data-stu-id="e02f6-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="e02f6-114">Les codes `HRESULT` peuvent comprendre, sans y être limités, ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="e02f6-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="e02f6-115">Code de retour</span><span class="sxs-lookup"><span data-stu-id="e02f6-115">Return code</span></span>|<span data-ttu-id="e02f6-116">Description</span><span class="sxs-lookup"><span data-stu-id="e02f6-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="e02f6-117">La méthode a réussi.</span><span class="sxs-lookup"><span data-stu-id="e02f6-117">Method succeeded.</span></span> <span data-ttu-id="e02f6-118">L'enregistrement de l'exception a été copié dans la mémoire tampon de sortie.</span><span class="sxs-lookup"><span data-stu-id="e02f6-118">The exception record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="e02f6-119">Aucun enregistrement d'exception n'est associé à la cible.</span><span class="sxs-lookup"><span data-stu-id="e02f6-119">No exception record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="e02f6-120">La taille de la mémoire tampon d'entrée est différente de `sizeof(MINIDUMP_EXCEPTION)`.</span><span class="sxs-lookup"><span data-stu-id="e02f6-120">The input buffer size is not equal to `sizeof(MINIDUMP_EXCEPTION)`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e02f6-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="e02f6-121">Remarks</span></span>  

 <span data-ttu-id="e02f6-122">[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) est une structure définie dans dbghelp. h et imagehlp. h dans le SDK Windows.</span><span class="sxs-lookup"><span data-stu-id="e02f6-122">[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) is a structure defined in dbghelp.h and imagehlp.h in the Windows SDK.</span></span>  
  
 <span data-ttu-id="e02f6-123">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="e02f6-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e02f6-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e02f6-124">Requirements</span></span>  

 <span data-ttu-id="e02f6-125">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e02f6-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e02f6-126">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="e02f6-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e02f6-127">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e02f6-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e02f6-128">**Versions de .NET Framework :**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e02f6-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e02f6-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e02f6-129">See also</span></span>

- [<span data-ttu-id="e02f6-130">ICLRDataTarget3, interface</span><span class="sxs-lookup"><span data-stu-id="e02f6-130">ICLRDataTarget3 Interface</span></span>](iclrdatatarget3-interface.md)
- [<span data-ttu-id="e02f6-131">GetExceptionContextRecord, méthode</span><span class="sxs-lookup"><span data-stu-id="e02f6-131">GetExceptionContextRecord Method</span></span>](iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="e02f6-132">GetExceptionThreadID, méthode</span><span class="sxs-lookup"><span data-stu-id="e02f6-132">GetExceptionThreadID Method</span></span>](iclrdatatarget3-getexceptionthreadid-method.md)
