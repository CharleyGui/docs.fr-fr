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
ms.openlocfilehash: a6a6aa937078ed0627688a4eed3d9142a2e6e0ac
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428108"
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="0dc9b-102">ISymUnmanagedWriter::CloseMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="0dc9b-102">ISymUnmanagedWriter::CloseMethod Method</span></span>
<span data-ttu-id="0dc9b-103">Ferme la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="0dc9b-103">Closes the current method.</span></span> <span data-ttu-id="0dc9b-104">Une fois qu’une méthode est fermée, aucun autre symbole ne peut être défini à l’intérieur de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="0dc9b-104">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dc9b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0dc9b-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0dc9b-106">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0dc9b-106">Return Value</span></span>  
 <span data-ttu-id="0dc9b-107">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="0dc9b-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dc9b-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0dc9b-108">Requirements</span></span>  
 <span data-ttu-id="0dc9b-109">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0dc9b-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dc9b-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0dc9b-110">See also</span></span>

- [<span data-ttu-id="0dc9b-111">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="0dc9b-111">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="0dc9b-112">OpenMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="0dc9b-112">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
