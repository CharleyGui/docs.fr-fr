---
title: ISymUnmanagedDocument::GetCheckSumAlgorithmId, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSumAlgorithmId
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId method [.NET Framework debugging]
- GetCheckSumAlgorithmId method [.NET Framework debugging]
ms.assetid: c7f941cd-e25b-4b85-b1ce-5f77c9208fa9
topic_type:
- apiref
ms.openlocfilehash: 2bc673d2e331cd32d5317cb20f9418eb3a3b144a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431066"
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a><span data-ttu-id="0d9e9-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId, méthode</span><span class="sxs-lookup"><span data-stu-id="0d9e9-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId Method</span></span>
<span data-ttu-id="0d9e9-103">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span><span class="sxs-lookup"><span data-stu-id="0d9e9-103">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d9e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d9e9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d9e9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0d9e9-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="0d9e9-106">[out] A pointer to a variable that receives the checksum algorithm identifier.</span><span class="sxs-lookup"><span data-stu-id="0d9e9-106">[out] A pointer to a variable that receives the checksum algorithm identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d9e9-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0d9e9-107">Return Value</span></span>  
 <span data-ttu-id="0d9e9-108">S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="0d9e9-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d9e9-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d9e9-109">See also</span></span>

- [<span data-ttu-id="0d9e9-110">ISymUnmanagedDocument, interface</span><span class="sxs-lookup"><span data-stu-id="0d9e9-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
