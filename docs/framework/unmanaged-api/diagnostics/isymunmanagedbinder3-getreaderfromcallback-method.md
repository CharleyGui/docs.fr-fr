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
ms.openlocfilehash: a0cccc0adfc666cc8e373bc1f89c8f6f97068fde
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449305"
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a><span data-ttu-id="455b1-102">ISymUnmanagedBinder3::GetReaderFromCallback, méthode</span><span class="sxs-lookup"><span data-stu-id="455b1-102">ISymUnmanagedBinder3::GetReaderFromCallback Method</span></span>
<span data-ttu-id="455b1-103">Permet à l’utilisateur d’implémenter ou de fournir via le rappel un `IID_IDiaReadExeAtRVACallback` ou `IID_IDiaReadExeAtOffsetCallback` pour obtenir les informations de répertoire de débogage à partir de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="455b1-103">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the debug directory information from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="455b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="455b1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="455b1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="455b1-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="455b1-106">dans Pointeur vers l’interface d’importation de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="455b1-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="455b1-107">dans Pointeur vers le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="455b1-107">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="455b1-108">dans Pointeur vers le chemin de recherche.</span><span class="sxs-lookup"><span data-stu-id="455b1-108">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="455b1-109">dans Valeur de l’énumération [CorSymSearchPolicyAttributes,](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) qui spécifie la stratégie à utiliser lors de la recherche d’un lecteur de symboles.</span><span class="sxs-lookup"><span data-stu-id="455b1-109">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `callback`  
 <span data-ttu-id="455b1-110">dans Pointeur vers la fonction de rappel.</span><span class="sxs-lookup"><span data-stu-id="455b1-110">[in] A pointer to the callback function.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="455b1-111">à Pointeur qui a pour valeur l’interface [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) retournée.</span><span class="sxs-lookup"><span data-stu-id="455b1-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="455b1-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="455b1-112">Return Value</span></span>  
 <span data-ttu-id="455b1-113">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="455b1-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="455b1-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="455b1-114">Requirements</span></span>  
 <span data-ttu-id="455b1-115">**En-tête :** CorSym. idl</span><span class="sxs-lookup"><span data-stu-id="455b1-115">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="455b1-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="455b1-116">See also</span></span>

- [<span data-ttu-id="455b1-117">ISymUnmanagedBinder3, interface</span><span class="sxs-lookup"><span data-stu-id="455b1-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
