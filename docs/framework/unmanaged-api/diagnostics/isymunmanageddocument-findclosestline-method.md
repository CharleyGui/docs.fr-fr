---
title: ISymUnmanagedDocument::FindClosestLine, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.FindClosestLine
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::FindClosestLine
helpviewer_keywords:
- FindClosestLine method [.NET Framework debugging]
- ISymUnmanagedDocument::FindClosestLine method [.NET Framework debugging]
ms.assetid: 628f2a04-e529-407d-841e-3b3da219a9cb
topic_type:
- apiref
ms.openlocfilehash: 9e6134d39096c4ab157aa545646d83339f92a0b8
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441030"
---
# <a name="isymunmanageddocumentfindclosestline-method"></a><span data-ttu-id="d873a-102">ISymUnmanagedDocument::FindClosestLine, méthode</span><span class="sxs-lookup"><span data-stu-id="d873a-102">ISymUnmanagedDocument::FindClosestLine Method</span></span>
<span data-ttu-id="d873a-103">Retourne la ligne la plus proche qui est un point de séquence, en fonction d’une ligne dans ce document qui peut être ou non un point de séquence.</span><span class="sxs-lookup"><span data-stu-id="d873a-103">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d873a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d873a-104">Syntax</span></span>  
  
```cpp  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d873a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d873a-105">Parameters</span></span>  
 `line`  
 <span data-ttu-id="d873a-106">dans Ligne dans ce document.</span><span class="sxs-lookup"><span data-stu-id="d873a-106">[in] A line in this document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="d873a-107">à Pointeur vers une variable qui reçoit la ligne.</span><span class="sxs-lookup"><span data-stu-id="d873a-107">[out] A pointer to a variable that receives the line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d873a-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d873a-108">Return Value</span></span>  
 <span data-ttu-id="d873a-109">S_OK si la méthode est réussie ; Sinon, un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="d873a-109">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d873a-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d873a-110">See also</span></span>

- [<span data-ttu-id="d873a-111">ISymUnmanagedDocument, interface</span><span class="sxs-lookup"><span data-stu-id="d873a-111">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
