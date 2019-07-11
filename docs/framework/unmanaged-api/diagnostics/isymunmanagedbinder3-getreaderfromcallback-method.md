---
title: ISymUnmanagedBinder3::GetReaderFromCallback, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3.GetReaderFromCallback
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3::GetReaderFromCallback
helpviewer_keywords:
- GetReaderFromCallback method [.NET Framework debugging]
- ISymUnmanagedBinder3::GetReaderFromCallback method [.NET Framework debugging]
ms.assetid: 4ef83bd2-3d8e-499e-8a12-d9d6fd6ced30
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ed0097e072b34dd43876ddf23abbc1f513670ff
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776818"
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a><span data-ttu-id="e4f4a-102">ISymUnmanagedBinder3::GetReaderFromCallback, méthode</span><span class="sxs-lookup"><span data-stu-id="e4f4a-102">ISymUnmanagedBinder3::GetReaderFromCallback Method</span></span>
<span data-ttu-id="e4f4a-103">Permet à l’utilisateur d’implémenter ou de fournir via un rappel un `IID_IDiaReadExeAtRVACallback` ou `IID_IDiaReadExeAtOffsetCallback` pour obtenir les informations de répertoire de débogage de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="e4f4a-103">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the debug directory information from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4f4a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4f4a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4f4a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e4f4a-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="e4f4a-106">[in] Pointeur vers l’interface d’importation de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="e4f4a-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="e4f4a-107">[in] Pointeur vers le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="e4f4a-107">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="e4f4a-108">[in] Pointeur vers le chemin de recherche.</span><span class="sxs-lookup"><span data-stu-id="e4f4a-108">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="e4f4a-109">[in] Une valeur de la [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) énumération qui spécifie la stratégie à utiliser lors d’une recherche pour un lecteur de symboles.</span><span class="sxs-lookup"><span data-stu-id="e4f4a-109">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `callback`  
 <span data-ttu-id="e4f4a-110">[in] Pointeur vers la fonction de rappel.</span><span class="sxs-lookup"><span data-stu-id="e4f4a-110">[in] A pointer to the callback function.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="e4f4a-111">[out] Un pointeur qui est défini à retourné [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="e4f4a-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4f4a-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e4f4a-112">Return Value</span></span>  
 <span data-ttu-id="e4f4a-113">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="e4f4a-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4f4a-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e4f4a-114">Requirements</span></span>  
 <span data-ttu-id="e4f4a-115">**En-tête :** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="e4f4a-115">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4f4a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4f4a-116">See also</span></span>

- [<span data-ttu-id="e4f4a-117">ISymUnmanagedBinder3, interface</span><span class="sxs-lookup"><span data-stu-id="e4f4a-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
