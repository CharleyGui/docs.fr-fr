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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 23f77f30b84622dffd8c76bb9302ad564f40ed41
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778192"
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="a90b9-102">ISymUnmanagedWriter::CloseMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="a90b9-102">ISymUnmanagedWriter::CloseMethod Method</span></span>
<span data-ttu-id="a90b9-103">Ferme la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="a90b9-103">Closes the current method.</span></span> <span data-ttu-id="a90b9-104">Une fois qu’une méthode est fermée, plus aucun symbole ne peut être définie qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="a90b9-104">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a90b9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a90b9-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a90b9-106">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a90b9-106">Return Value</span></span>  
 <span data-ttu-id="a90b9-107">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="a90b9-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a90b9-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a90b9-108">Requirements</span></span>  
 <span data-ttu-id="a90b9-109">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a90b9-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a90b9-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a90b9-110">See also</span></span>

- [<span data-ttu-id="a90b9-111">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="a90b9-111">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="a90b9-112">OpenMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="a90b9-112">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
