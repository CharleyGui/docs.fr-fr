---
title: ISymUnmanagedDocumentWriter::SetSource, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetSource
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetSource method [.NET Framework debugging]
- SetSource method [.NET Framework debugging]
ms.assetid: ea5b9d9f-ff06-4bd3-8de5-6435343aba59
topic_type:
- apiref
ms.openlocfilehash: ff18f95bd6b4cfde5aaa4d3f6f68b58fd37c04b3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449070"
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="49526-102">ISymUnmanagedDocumentWriter::SetSource, méthode</span><span class="sxs-lookup"><span data-stu-id="49526-102">ISymUnmanagedDocumentWriter::SetSource Method</span></span>
<span data-ttu-id="49526-103">Définit la source incorporée pour un document en cours d’écriture.</span><span class="sxs-lookup"><span data-stu-id="49526-103">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49526-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49526-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49526-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="49526-105">Parameters</span></span>  
 `sourceSize`  
 <span data-ttu-id="49526-106">dans `ULONG32` qui contient la taille de la mémoire tampon de `source`.</span><span class="sxs-lookup"><span data-stu-id="49526-106">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="49526-107">dans Mémoire tampon qui stocke la source incorporée.</span><span class="sxs-lookup"><span data-stu-id="49526-107">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49526-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="49526-108">Return Value</span></span>  
 <span data-ttu-id="49526-109">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="49526-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49526-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="49526-110">Requirements</span></span>  
 <span data-ttu-id="49526-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="49526-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49526-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49526-112">See also</span></span>

- [<span data-ttu-id="49526-113">ISymUnmanagedDocumentWriter, interface</span><span class="sxs-lookup"><span data-stu-id="49526-113">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
