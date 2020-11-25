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
ms.openlocfilehash: 1d684c14f14fcc93040798ae4ee3b8bb1df5354d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733254"
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="17d59-102">ISymUnmanagedWriter::Close, méthode</span><span class="sxs-lookup"><span data-stu-id="17d59-102">ISymUnmanagedWriter::Close Method</span></span>

<span data-ttu-id="17d59-103">Ferme le writer de symbole après avoir validé les symboles dans le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="17d59-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17d59-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17d59-104">Syntax</span></span>  
  
```cpp  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="17d59-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="17d59-105">Return Value</span></span>  

 <span data-ttu-id="17d59-106">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="17d59-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17d59-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="17d59-107">Remarks</span></span>  

 <span data-ttu-id="17d59-108">Après cet appel, l’enregistreur de symboles devient non valide pour les mises à jour ultérieures.</span><span class="sxs-lookup"><span data-stu-id="17d59-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="17d59-109">Pour fermer le writer de symbole sans valider les symboles, utilisez la méthode [ISymUnmanagedWriter :: Abort](isymunmanagedwriter-abort-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="17d59-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17d59-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="17d59-110">Requirements</span></span>  

 <span data-ttu-id="17d59-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="17d59-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17d59-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17d59-112">See also</span></span>

- [<span data-ttu-id="17d59-113">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="17d59-113">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
