---
title: ISymUnmanagedReader::GetDocumentVersion, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocumentVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocumentVersion
helpviewer_keywords:
- GetDocumentVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocumentVersion method [.NET Framework debugging]
ms.assetid: a51f1f64-e084-44c5-830c-2222da5a6bbf
topic_type:
- apiref
ms.openlocfilehash: 3bc578be680951a1d41c92fb2169c860882b2e31
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448312"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a><span data-ttu-id="50ca2-102">ISymUnmanagedReader::GetDocumentVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="50ca2-102">ISymUnmanagedReader::GetDocumentVersion Method</span></span>
<span data-ttu-id="50ca2-103">Obtient la version spécifiée du document spécifié.</span><span class="sxs-lookup"><span data-stu-id="50ca2-103">Gets the specified version of the specified document.</span></span> <span data-ttu-id="50ca2-104">La version du document commence à 1 et est incrémentée chaque fois que le document est mis à jour à l’aide de la méthode [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) .</span><span class="sxs-lookup"><span data-stu-id="50ca2-104">The document version starts at 1 and is incremented each time the document is updated using the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method.</span></span> <span data-ttu-id="50ca2-105">Si le paramètre `pbCurrent` est `true`, il s’agit de la dernière version du document.</span><span class="sxs-lookup"><span data-stu-id="50ca2-105">If the `pbCurrent` parameter is `true`, this is the latest version of the document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50ca2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50ca2-106">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50ca2-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="50ca2-107">Parameters</span></span>  
 `pDoc`  
 <span data-ttu-id="50ca2-108">dans Document spécifié.</span><span class="sxs-lookup"><span data-stu-id="50ca2-108">[in] The specified document.</span></span>  
  
 `version`  
 <span data-ttu-id="50ca2-109">à Pointeur vers une variable qui reçoit la version du document spécifié.</span><span class="sxs-lookup"><span data-stu-id="50ca2-109">[out] A pointer to a variable that receives the version of the specified document.</span></span>  
  
 `pbCurrent`  
 <span data-ttu-id="50ca2-110">à Pointeur vers une variable qui reçoit `true` s’il s’agit de la version la plus récente du document, ou `false` s’il ne s’agit pas de la version la plus récente.</span><span class="sxs-lookup"><span data-stu-id="50ca2-110">[out] A pointer to a variable that receives `true` if this is the latest version of the document, or `false` if it isn't the latest version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50ca2-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="50ca2-111">Return Value</span></span>  
 <span data-ttu-id="50ca2-112">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="50ca2-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50ca2-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="50ca2-113">Requirements</span></span>  
 <span data-ttu-id="50ca2-114">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="50ca2-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50ca2-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50ca2-115">See also</span></span>

- [<span data-ttu-id="50ca2-116">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="50ca2-116">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
