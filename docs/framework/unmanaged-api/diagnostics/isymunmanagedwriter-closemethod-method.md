---
title: ISymUnmanagedWriter::CloseMethod, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseMethod
helpviewer_keywords:
- ISymUnmanagedWriter::CloseMethod method [.NET Framework debugging]
- CloseMethod method [.NET Framework debugging]
ms.assetid: b8025e04-f0e5-40c8-849c-8cd51323420e
topic_type:
- apiref
ms.openlocfilehash: fcf250f10baf4c65cd1c8c918655e4b9f4f5cc4b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731733"
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="900c6-102">ISymUnmanagedWriter::CloseMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="900c6-102">ISymUnmanagedWriter::CloseMethod Method</span></span>

<span data-ttu-id="900c6-103">Ferme la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="900c6-103">Closes the current method.</span></span> <span data-ttu-id="900c6-104">Une fois qu’une méthode est fermée, aucun autre symbole ne peut être défini à l’intérieur de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="900c6-104">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="900c6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="900c6-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="900c6-106">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="900c6-106">Return Value</span></span>  

 <span data-ttu-id="900c6-107">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="900c6-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="900c6-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="900c6-108">Requirements</span></span>  

 <span data-ttu-id="900c6-109">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="900c6-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="900c6-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="900c6-110">See also</span></span>

- [<span data-ttu-id="900c6-111">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="900c6-111">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="900c6-112">OpenMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="900c6-112">OpenMethod Method</span></span>](isymunmanagedwriter-openmethod-method.md)
