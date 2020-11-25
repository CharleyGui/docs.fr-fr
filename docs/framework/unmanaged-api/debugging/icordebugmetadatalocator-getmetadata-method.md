---
title: ICorDebugMetaDataLocator::GetMetaData, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugMetaDataLocator.GetMetaData
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMetaDataLocator::GetMetaData
helpviewer_keywords:
- ICorDebugMetaDataLocator::GetMetaData method [.NET Framework debugging]
- GetMetaData method, ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: f9b0ff22-54db-45eb-9cc3-508000a3141d
topic_type:
- apiref
ms.openlocfilehash: 63efb788d8bca84da94921371309704cc7b20ac4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710439"
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a><span data-ttu-id="0bc35-102">ICorDebugMetaDataLocator::GetMetaData, méthode</span><span class="sxs-lookup"><span data-stu-id="0bc35-102">ICorDebugMetaDataLocator::GetMetaData Method</span></span>

<span data-ttu-id="0bc35-103">Indique au débogueur de retourner le chemin d’accès complet à un module dont les métadonnées sont nécessaires pour effectuer une opération demandée par le débogueur.</span><span class="sxs-lookup"><span data-stu-id="0bc35-103">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bc35-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0bc35-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaData(  
      [in] LPCWSTR wszImagePath,  
      [in] DWORD   dwImageTimeStamp,  
      [in] DWORD   dwImageSize,  
      [in] ULONG32 cchPathBuffer,  
      [out] ULONG32 * pcchPathBuffer,  
      [out, size_is(cchPathBuffer), length_is(*pcchPathBuffer)]  
               WCHAR wszPathBuffer[]  
      );  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bc35-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0bc35-105">Parameters</span></span>  

 `wszImagePath`  
 <span data-ttu-id="0bc35-106">[in] Chaîne terminée par le caractère null qui représente le chemin d’accès complet au fichier.</span><span class="sxs-lookup"><span data-stu-id="0bc35-106">[in] A null-terminated string that represents the full path to the file.</span></span> <span data-ttu-id="0bc35-107">Si le chemin d’accès complet n’est pas disponible, nom et extension du fichier (*nom_fichier*.*extension*).</span><span class="sxs-lookup"><span data-stu-id="0bc35-107">If the full path is not available, the name and extension of the file (*filename*.*extension*).</span></span>  
  
 `dwImageTimeStamp`  
 <span data-ttu-id="0bc35-108">[in] Horodatage des en-têtes de fichier PE de l'image.</span><span class="sxs-lookup"><span data-stu-id="0bc35-108">[in] The time stamp from the image's PE file headers.</span></span> <span data-ttu-id="0bc35-109">Ce paramètre peut potentiellement être utilisé pour une recherche de serveur de symboles ([symsrv](/windows/desktop/debug/using-symsrv)).</span><span class="sxs-lookup"><span data-stu-id="0bc35-109">This parameter can potentially be used for a symbol server ([SymSrv](/windows/desktop/debug/using-symsrv)) lookup.</span></span>  
  
 `dwImageSize`  
 <span data-ttu-id="0bc35-110">[in] Taille d'image dans les en-têtes de fichier PE.</span><span class="sxs-lookup"><span data-stu-id="0bc35-110">[in] The image size from PE file headers.</span></span> <span data-ttu-id="0bc35-111">Ce paramètre peut potentiellement être utilisé pour une recherche SymSrv.</span><span class="sxs-lookup"><span data-stu-id="0bc35-111">This parameter can potentially be used for a SymSrv lookup.</span></span>  
  
 `cchPathBuffer`  
 <span data-ttu-id="0bc35-112">[in] Nombre de caractères dans `wszPathBuffer`.</span><span class="sxs-lookup"><span data-stu-id="0bc35-112">[in] The character count in `wszPathBuffer`.</span></span>  
  
 `pcchPathBuffer`  
 <span data-ttu-id="0bc35-113">[out] Nombre de `WCHAR` écrits dans `wszPathBuffer`.</span><span class="sxs-lookup"><span data-stu-id="0bc35-113">[out] The count of `WCHAR`s written to `wszPathBuffer`.</span></span>  
  
 <span data-ttu-id="0bc35-114">Si la méthode retourne E_NOT_SUFFICIENT_BUFFER, contient le nombre de `WCHAR` nécessaires pour stocker le chemin d'accès.</span><span class="sxs-lookup"><span data-stu-id="0bc35-114">If the method returns E_NOT_SUFFICIENT_BUFFER, contains the count of `WCHAR`s needed to store the path.</span></span>  
  
 `wszPathBuffer`  
 <span data-ttu-id="0bc35-115">[out] Pointeur vers une mémoire tampon dans laquelle le débogueur copie le chemin d’accès complet du fichier contenant les métadonnées demandées.</span><span class="sxs-lookup"><span data-stu-id="0bc35-115">[out] Pointer to a buffer into which the debugger will copy the full path of the file that contains the requested metadata.</span></span>  
  
 <span data-ttu-id="0bc35-116">L' `ofReadOnly` indicateur de l’énumération [CorOpenFlags](../metadata/coropenflags-enumeration.md) est utilisé pour demander un accès en lecture seule aux métadonnées dans ce fichier.</span><span class="sxs-lookup"><span data-stu-id="0bc35-116">The `ofReadOnly` flag from the [CorOpenFlags](../metadata/coropenflags-enumeration.md) enumeration is used to request read-only access to the metadata in this file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0bc35-117">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="0bc35-117">Return Value</span></span>  

 <span data-ttu-id="0bc35-118">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="0bc35-118">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span> <span data-ttu-id="0bc35-119">Tous les autres HRESULT d'échec indiquent que le fichier n'est pas récupérable.</span><span class="sxs-lookup"><span data-stu-id="0bc35-119">All other failure HRESULTs indicate that the file is not retrievable.</span></span>  
  
|<span data-ttu-id="0bc35-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0bc35-120">HRESULT</span></span>|<span data-ttu-id="0bc35-121">Description</span><span class="sxs-lookup"><span data-stu-id="0bc35-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0bc35-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="0bc35-122">S_OK</span></span>|<span data-ttu-id="0bc35-123">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="0bc35-123">The method completed successfully.</span></span> <span data-ttu-id="0bc35-124">`wszPathBuffer` contient le chemin d'accès complet au fichier et se termine par le caractère null.</span><span class="sxs-lookup"><span data-stu-id="0bc35-124">`wszPathBuffer` contains the full path to the file and is null-terminated.</span></span>|  
|<span data-ttu-id="0bc35-125">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="0bc35-125">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="0bc35-126">La taille actuelle de `wszPathBuffer` n’est pas suffisante pour contenir le chemin d’accès complet.</span><span class="sxs-lookup"><span data-stu-id="0bc35-126">The current size of `wszPathBuffer` is not sufficient to hold the full path.</span></span> <span data-ttu-id="0bc35-127">Dans ce cas, `pcchPathBuffer` contient le nombre nécessaire de `WCHAR`, y compris le caractère null de fin, et la méthode `GetMetaData` est appelée une deuxième fois avec la taille de mémoire tampon demandée.</span><span class="sxs-lookup"><span data-stu-id="0bc35-127">In this case, `pcchPathBuffer` contains the needed count of `WCHAR`s, including the terminating null character, and `GetMetaData` is called a second time with the requested buffer size.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0bc35-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="0bc35-128">Remarks</span></span>  

 <span data-ttu-id="0bc35-129">Si `wszImagePath` contient le chemin d’accès complet d’un module dans un dump, il spécifie le chemin d’accès de l’ordinateur sur lequel le dump a été collecté.</span><span class="sxs-lookup"><span data-stu-id="0bc35-129">If `wszImagePath` contains a full path for a module from a dump, it specifies the path from the computer where the dump was collected.</span></span> <span data-ttu-id="0bc35-130">Le fichier n'existe peut-être pas à cet emplacement ou un fichier incorrect portant le même nom peut être stocké dans le chemin d'accès.</span><span class="sxs-lookup"><span data-stu-id="0bc35-130">The file may not exist at this location, or an incorrect file with the same name may be stored on the path.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bc35-131">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0bc35-131">Requirements</span></span>  

 <span data-ttu-id="0bc35-132">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bc35-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bc35-133">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0bc35-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0bc35-134">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0bc35-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bc35-135">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bc35-135">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bc35-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0bc35-136">See also</span></span>

- [<span data-ttu-id="0bc35-137">ICorDebugThread4, interface</span><span class="sxs-lookup"><span data-stu-id="0bc35-137">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="0bc35-138">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="0bc35-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0bc35-139">Débogage</span><span class="sxs-lookup"><span data-stu-id="0bc35-139">Debugging</span></span>](index.md)
