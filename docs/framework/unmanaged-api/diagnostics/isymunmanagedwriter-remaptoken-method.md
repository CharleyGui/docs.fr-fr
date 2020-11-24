---
title: ISymUnmanagedWriter::RemapToken, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.RemapToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::RemapToken
helpviewer_keywords:
- ISymUnmanagedWriter::RemapToken method [.NET Framework debugging]
- RemapToken method [.NET Framework debugging]
ms.assetid: bca92682-ee1e-467f-8fb0-d8d4617f82fe
topic_type:
- apiref
ms.openlocfilehash: 8799815f7c6c6aefc7081f3583e6fd174cd478f7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683555"
---
# <a name="isymunmanagedwriterremaptoken-method"></a><span data-ttu-id="90ed3-102">ISymUnmanagedWriter::RemapToken, méthode</span><span class="sxs-lookup"><span data-stu-id="90ed3-102">ISymUnmanagedWriter::RemapToken Method</span></span>

<span data-ttu-id="90ed3-103">Notifie le writer de symbole qu’un jeton de métadonnées a été remappé à la sortie des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="90ed3-103">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span> <span data-ttu-id="90ed3-104">Si le writer de symbole a stocké l’ancien jeton dans le magasin de symboles, il doit mettre à jour le jeton stocké avec la nouvelle valeur, ou il doit enregistrer la carte pour que le lecteur de symboles correspondant soit remappé au cours de la phase de lecture.</span><span class="sxs-lookup"><span data-stu-id="90ed3-104">If the symbol writer has stored the old token within the symbol store, it must either update the stored token with the new value, or it must save the map for the corresponding symbol reader to remap during the read phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90ed3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90ed3-105">Syntax</span></span>  
  
```cpp  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90ed3-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="90ed3-106">Parameters</span></span>  

 `oldToken`  
 <span data-ttu-id="90ed3-107">dans Jeton de métadonnées qui a été remappé.</span><span class="sxs-lookup"><span data-stu-id="90ed3-107">[in] The metadata token that was remapped.</span></span>  
  
 `newToken`  
 <span data-ttu-id="90ed3-108">dans Nouveau jeton de métadonnées dans lequel `oldToken` a été remappé.</span><span class="sxs-lookup"><span data-stu-id="90ed3-108">[in] The new metadata token to which `oldToken` was remapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90ed3-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="90ed3-109">Return Value</span></span>  

 <span data-ttu-id="90ed3-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="90ed3-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90ed3-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="90ed3-111">Requirements</span></span>  

 <span data-ttu-id="90ed3-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="90ed3-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90ed3-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90ed3-113">See also</span></span>

- [<span data-ttu-id="90ed3-114">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="90ed3-114">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
