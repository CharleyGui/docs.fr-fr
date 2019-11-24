---
title: ISymUnmanagedWriter::Close, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Close
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type:
- apiref
ms.openlocfilehash: cd601ac6041ca22d59d7467bafc7c1d87b21371f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428113"
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="dccaf-102">ISymUnmanagedWriter::Close, méthode</span><span class="sxs-lookup"><span data-stu-id="dccaf-102">ISymUnmanagedWriter::Close Method</span></span>
<span data-ttu-id="dccaf-103">Ferme le writer de symbole après avoir validé les symboles dans le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="dccaf-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dccaf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dccaf-104">Syntax</span></span>  
  
```cpp  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="dccaf-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="dccaf-105">Return Value</span></span>  
 <span data-ttu-id="dccaf-106">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="dccaf-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dccaf-107">Notes</span><span class="sxs-lookup"><span data-stu-id="dccaf-107">Remarks</span></span>  
 <span data-ttu-id="dccaf-108">Après cet appel, l’enregistreur de symboles devient non valide pour les mises à jour ultérieures.</span><span class="sxs-lookup"><span data-stu-id="dccaf-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="dccaf-109">Pour fermer le writer de symbole sans valider les symboles, utilisez la méthode [ISymUnmanagedWriter :: Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="dccaf-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dccaf-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="dccaf-110">Requirements</span></span>  
 <span data-ttu-id="dccaf-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="dccaf-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dccaf-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dccaf-112">See also</span></span>

- [<span data-ttu-id="dccaf-113">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="dccaf-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
