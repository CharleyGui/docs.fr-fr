---
title: ISymUnmanagedDocumentWriter::SetCheckSum, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum method [.NET Framework debugging]
- SetCheckSum method [.NET Framework debugging]
ms.assetid: c7e99879-421f-43ce-b193-34733cf30085
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3343710fbe4f1aba8c38e46a0a720f78944a1c10
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776921"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="b16c2-102">ISymUnmanagedDocumentWriter::SetCheckSum, méthode</span><span class="sxs-lookup"><span data-stu-id="b16c2-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>
<span data-ttu-id="b16c2-103">Définit les informations de la somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="b16c2-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b16c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b16c2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b16c2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b16c2-105">Parameters</span></span>  
 `algorithmId`  
 <span data-ttu-id="b16c2-106">[in] GUID qui représente l’identificateur d’algorithme.</span><span class="sxs-lookup"><span data-stu-id="b16c2-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="b16c2-107">[in] Un `ULONG32` qui indique la taille, en octets, de la `checkSum` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="b16c2-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="b16c2-108">[in] La mémoire tampon qui stocke les informations de somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="b16c2-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b16c2-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b16c2-109">Return Value</span></span>  
 <span data-ttu-id="b16c2-110">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="b16c2-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b16c2-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b16c2-111">Requirements</span></span>  
 <span data-ttu-id="b16c2-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b16c2-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b16c2-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b16c2-113">See also</span></span>

- [<span data-ttu-id="b16c2-114">ISymUnmanagedDocumentWriter, interface</span><span class="sxs-lookup"><span data-stu-id="b16c2-114">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
