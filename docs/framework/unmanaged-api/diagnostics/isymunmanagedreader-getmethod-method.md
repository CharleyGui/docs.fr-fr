---
title: ISymUnmanagedReader::GetMethod, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedReader interface [.NET Framework debugging]
- ISymUnmanagedReader::GetMethod method [.NET Framework debugging]
ms.assetid: ae6cfb29-bc2c-4606-af86-1d32ebd31020
topic_type:
- apiref
ms.openlocfilehash: 864acb07797676c825afe62321b0d65e37938fa6
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615005"
---
# <a name="isymunmanagedreadergetmethod-method"></a><span data-ttu-id="aeffd-102">ISymUnmanagedReader::GetMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="aeffd-102">ISymUnmanagedReader::GetMethod Method</span></span>
<span data-ttu-id="aeffd-103">Obtient une méthode de lecteur de symboles, en fonction d’un jeton de méthode.</span><span class="sxs-lookup"><span data-stu-id="aeffd-103">Gets a symbol reader method, given a method token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aeffd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aeffd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethod (  
    [in]  mdMethodDef  token,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aeffd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="aeffd-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="aeffd-106">dans Jeton de méthode.</span><span class="sxs-lookup"><span data-stu-id="aeffd-106">[in] The method token.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="aeffd-107">à Pointeur vers l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="aeffd-107">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aeffd-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="aeffd-108">Return Value</span></span>  
 <span data-ttu-id="aeffd-109">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="aeffd-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aeffd-110">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="aeffd-110">Requirements</span></span>  
 <span data-ttu-id="aeffd-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="aeffd-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeffd-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aeffd-112">See also</span></span>

- [<span data-ttu-id="aeffd-113">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="aeffd-113">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
