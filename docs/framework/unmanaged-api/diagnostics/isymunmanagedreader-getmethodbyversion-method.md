---
title: ISymUnmanagedReader::GetMethodByVersion, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodByVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodByVersion
helpviewer_keywords:
- ISymUnmanagedReader::GetMethodByVersion method [.NET Framework debugging]
- GetMethodByVersion method [.NET Framework debugging]
ms.assetid: 6ddb0631-4569-41b3-93e4-50fdfaa486dc
topic_type:
- apiref
ms.openlocfilehash: 64e6b9a1942e9a69e43de3d2f09564814328ec08
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689613"
---
# <a name="isymunmanagedreadergetmethodbyversion-method"></a><span data-ttu-id="5c16d-102">ISymUnmanagedReader::GetMethodByVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="5c16d-102">ISymUnmanagedReader::GetMethodByVersion Method</span></span>

<span data-ttu-id="5c16d-103">Obtient une méthode de lecteur de symboles, en fonction d’un jeton de méthode et d’un numéro de version de modification et de copie.</span><span class="sxs-lookup"><span data-stu-id="5c16d-103">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span> <span data-ttu-id="5c16d-104">Les numéros de version commencent à 1 et sont incrémentés chaque fois que la méthode est modifiée suite à une opération de modification et de copie.</span><span class="sxs-lookup"><span data-stu-id="5c16d-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c16d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c16d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersion (  
    [in]  mdMethodDef  token,  
    [in]  int  version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c16d-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5c16d-106">Parameters</span></span>  

 `token`  
 <span data-ttu-id="5c16d-107">dans Jeton de méthode.</span><span class="sxs-lookup"><span data-stu-id="5c16d-107">[in] The method token.</span></span>  
  
 `version`  
 <span data-ttu-id="5c16d-108">dans Version de la méthode.</span><span class="sxs-lookup"><span data-stu-id="5c16d-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="5c16d-109">à Pointeur vers l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="5c16d-109">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c16d-110">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="5c16d-110">Return Value</span></span>  

 <span data-ttu-id="5c16d-111">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="5c16d-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c16d-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5c16d-112">Requirements</span></span>  

 <span data-ttu-id="5c16d-113">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="5c16d-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c16d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c16d-114">See also</span></span>

- [<span data-ttu-id="5c16d-115">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="5c16d-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
