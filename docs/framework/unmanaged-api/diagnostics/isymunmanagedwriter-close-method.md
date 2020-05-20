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
ms.openlocfilehash: 0a7ecd475a8031fedb2c8474593b45045fcc6fb9
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610130"
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="878a6-102">ISymUnmanagedWriter::Close, méthode</span><span class="sxs-lookup"><span data-stu-id="878a6-102">ISymUnmanagedWriter::Close Method</span></span>
<span data-ttu-id="878a6-103">Ferme le writer de symbole après avoir validé les symboles dans le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="878a6-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="878a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="878a6-104">Syntax</span></span>  
  
```cpp  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="878a6-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="878a6-105">Return Value</span></span>  
 <span data-ttu-id="878a6-106">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="878a6-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="878a6-107">Notes</span><span class="sxs-lookup"><span data-stu-id="878a6-107">Remarks</span></span>  
 <span data-ttu-id="878a6-108">Après cet appel, l’enregistreur de symboles devient non valide pour les mises à jour ultérieures.</span><span class="sxs-lookup"><span data-stu-id="878a6-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="878a6-109">Pour fermer le writer de symbole sans valider les symboles, utilisez la méthode [ISymUnmanagedWriter :: Abort](isymunmanagedwriter-abort-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="878a6-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="878a6-110">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="878a6-110">Requirements</span></span>  
 <span data-ttu-id="878a6-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="878a6-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="878a6-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="878a6-112">See also</span></span>

- [<span data-ttu-id="878a6-113">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="878a6-113">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
