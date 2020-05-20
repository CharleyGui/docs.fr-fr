---
title: ISymUnmanagedBinder::GetReaderFromStream, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderFromStream
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderFromStream
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderFromStream method [.NET Framework debugging]
- GetReaderFromStream method [.NET Framework debugging]
ms.assetid: aa38efd4-de7e-4482-a5d3-adc152093460
topic_type:
- apiref
ms.openlocfilehash: 351bb2a1eb03684a0498fba35270e1bda44a93c0
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441745"
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a><span data-ttu-id="6701a-102">ISymUnmanagedBinder::GetReaderFromStream, méthode</span><span class="sxs-lookup"><span data-stu-id="6701a-102">ISymUnmanagedBinder::GetReaderFromStream Method</span></span>
<span data-ttu-id="6701a-103">À partir d’une interface de métadonnées et d’un flux de données qui contient le magasin de symboles, retourne la structure [ISymUnmanagedReader](isymunmanagedreader-interface.md) appropriée qui lira les symboles de débogage du magasin de symboles donné.</span><span class="sxs-lookup"><span data-stu-id="6701a-103">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6701a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6701a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6701a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6701a-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="6701a-106">dans Pointeur vers l’interface d’importation de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="6701a-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `pstream`  
 <span data-ttu-id="6701a-107">dans Pointeur vers le flux de contenu qui contient le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="6701a-107">[in] A pointer to the stream that contains the symbol store.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="6701a-108">à Pointeur qui a pour valeur l’interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) retournée.</span><span class="sxs-lookup"><span data-stu-id="6701a-108">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6701a-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6701a-109">Return Value</span></span>  
 <span data-ttu-id="6701a-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="6701a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6701a-111">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="6701a-111">Requirements</span></span>  
 <span data-ttu-id="6701a-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="6701a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6701a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6701a-113">See also</span></span>

- [<span data-ttu-id="6701a-114">ISymUnmanagedBinder, interface</span><span class="sxs-lookup"><span data-stu-id="6701a-114">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
