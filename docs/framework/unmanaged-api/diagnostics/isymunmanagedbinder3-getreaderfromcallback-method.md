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
ms.openlocfilehash: d48c2bdd55e487038048f432c5586d49f393118c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706942"
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a><span data-ttu-id="227da-102">ISymUnmanagedBinder3::GetReaderFromCallback, méthode</span><span class="sxs-lookup"><span data-stu-id="227da-102">ISymUnmanagedBinder3::GetReaderFromCallback Method</span></span>

<span data-ttu-id="227da-103">Permet à l’utilisateur d’implémenter ou de fournir via le rappel d’un `IID_IDiaReadExeAtRVACallback` ou `IID_IDiaReadExeAtOffsetCallback` pour obtenir les informations du répertoire de débogage à partir de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="227da-103">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the debug directory information from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="227da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="227da-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="227da-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="227da-105">Parameters</span></span>  

 `importer`  
 <span data-ttu-id="227da-106">dans Pointeur vers l’interface d’importation de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="227da-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="227da-107">dans Pointeur vers le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="227da-107">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="227da-108">dans Pointeur vers le chemin de recherche.</span><span class="sxs-lookup"><span data-stu-id="227da-108">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="227da-109">dans Valeur de l’énumération [CorSymSearchPolicyAttributes,](corsymsearchpolicyattributes-enumeration.md) qui spécifie la stratégie à utiliser lors de la recherche d’un lecteur de symboles.</span><span class="sxs-lookup"><span data-stu-id="227da-109">[in] A value of the [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `callback`  
 <span data-ttu-id="227da-110">dans Pointeur vers la fonction de rappel.</span><span class="sxs-lookup"><span data-stu-id="227da-110">[in] A pointer to the callback function.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="227da-111">à Pointeur qui a pour valeur l’interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) retournée.</span><span class="sxs-lookup"><span data-stu-id="227da-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="227da-112">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="227da-112">Return Value</span></span>  

 <span data-ttu-id="227da-113">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="227da-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="227da-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="227da-114">Requirements</span></span>  

 <span data-ttu-id="227da-115">**En-tête :** CorSym. idl</span><span class="sxs-lookup"><span data-stu-id="227da-115">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="227da-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="227da-116">See also</span></span>

- [<span data-ttu-id="227da-117">ISymUnmanagedBinder3, interface</span><span class="sxs-lookup"><span data-stu-id="227da-117">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
