---
title: ISymUnmanagedWriter::Abort, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Abort
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Abort
helpviewer_keywords:
- ISymUnmanagedWriter::Abort method [.NET Framework debugging]
- Abort method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 416b220f-38d4-48e0-bb49-d2faa7366702
topic_type:
- apiref
ms.openlocfilehash: 09f39d3b6486e2ec3c04c5d1858a85ce56895527
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610156"
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="c7b4d-102">ISymUnmanagedWriter::Abort, méthode</span><span class="sxs-lookup"><span data-stu-id="c7b4d-102">ISymUnmanagedWriter::Abort Method</span></span>
<span data-ttu-id="c7b4d-103">Ferme le writer de symbole sans valider les symboles dans le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="c7b4d-103">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="c7b4d-104">Après cet appel, l’enregistreur de symboles devient non valide pour les mises à jour ultérieures.</span><span class="sxs-lookup"><span data-stu-id="c7b4d-104">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="c7b4d-105">Pour valider les symboles et fermer le writer de symbole, utilisez la méthode [ISymUnmanagedWriter :: Close](isymunmanagedwriter-close-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="c7b4d-105">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7b4d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7b4d-106">Syntax</span></span>  
  
```cpp  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c7b4d-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c7b4d-107">Return Value</span></span>  
 <span data-ttu-id="c7b4d-108">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="c7b4d-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7b4d-109">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="c7b4d-109">Requirements</span></span>  
 <span data-ttu-id="c7b4d-110">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c7b4d-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7b4d-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7b4d-111">See also</span></span>

- [<span data-ttu-id="c7b4d-112">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="c7b4d-112">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
