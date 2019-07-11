---
title: ISymUnmanagedDocument::GetCheckSum, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSum method [.NET Framework debugging]
- GetCheckSum method [.NET Framework debugging]
ms.assetid: 9bc881b3-e2ce-48a7-ad69-17eaaa304120
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b34f985f199542612bcdb9b30ebae28649438e1b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776771"
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="5d955-102">ISymUnmanagedDocument::GetCheckSum, méthode</span><span class="sxs-lookup"><span data-stu-id="5d955-102">ISymUnmanagedDocument::GetCheckSum Method</span></span>
<span data-ttu-id="5d955-103">Obtient la somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="5d955-103">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d955-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d955-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d955-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5d955-105">Parameters</span></span>  
 `cData`  
 <span data-ttu-id="5d955-106">[in] La longueur de la mémoire tampon fournie par le `data` paramètre</span><span class="sxs-lookup"><span data-stu-id="5d955-106">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="5d955-107">[out] La taille et la longueur de la somme de contrôle, en octets.</span><span class="sxs-lookup"><span data-stu-id="5d955-107">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="5d955-108">[out] La mémoire tampon qui reçoit la somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="5d955-108">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d955-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5d955-109">Return Value</span></span>  
 <span data-ttu-id="5d955-110">S_OK si la méthode réussit ; Sinon, un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="5d955-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d955-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d955-111">See also</span></span>

- [<span data-ttu-id="5d955-112">ISymUnmanagedDocument, interface</span><span class="sxs-lookup"><span data-stu-id="5d955-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
