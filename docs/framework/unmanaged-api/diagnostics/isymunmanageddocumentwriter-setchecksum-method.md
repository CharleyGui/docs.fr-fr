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
ms.openlocfilehash: 58055d9ea56d7928729d289198965752985d8e0c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688898"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="46dae-102">ISymUnmanagedDocumentWriter::SetCheckSum, méthode</span><span class="sxs-lookup"><span data-stu-id="46dae-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>

<span data-ttu-id="46dae-103">Définit les informations de la somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="46dae-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46dae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46dae-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46dae-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="46dae-105">Parameters</span></span>  

 `algorithmId`  
 <span data-ttu-id="46dae-106">dans GUID qui représente l’identificateur d’algorithme.</span><span class="sxs-lookup"><span data-stu-id="46dae-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="46dae-107">dans `ULONG32` Qui indique la taille, en octets, de la `checkSum` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="46dae-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="46dae-108">dans Mémoire tampon qui stocke les informations de somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="46dae-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46dae-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="46dae-109">Return Value</span></span>  

 <span data-ttu-id="46dae-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="46dae-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46dae-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="46dae-111">Requirements</span></span>  

 <span data-ttu-id="46dae-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="46dae-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46dae-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46dae-113">See also</span></span>

- [<span data-ttu-id="46dae-114">ISymUnmanagedDocumentWriter, interface</span><span class="sxs-lookup"><span data-stu-id="46dae-114">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)
