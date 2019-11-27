---
title: ISymUnmanagedReader::GetDocument, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocument
helpviewer_keywords:
- ISymUnmanagedReader::GetDocument method [.NET Framework debugging]
- GetDocument method [.NET Framework debugging]
ms.assetid: bb203853-6a6d-4027-b9e9-603a7f28b9d3
topic_type:
- apiref
ms.openlocfilehash: 1fcb885b6e19457065c2ca9971f068b42f97147d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448345"
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="22fb3-102">ISymUnmanagedReader::GetDocument, méthode</span><span class="sxs-lookup"><span data-stu-id="22fb3-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="22fb3-103">Recherche un document.</span><span class="sxs-lookup"><span data-stu-id="22fb3-103">Finds a document.</span></span> <span data-ttu-id="22fb3-104">La langue, le fournisseur et le type du document sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="22fb3-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22fb3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22fb3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22fb3-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="22fb3-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="22fb3-107">dans URL qui identifie le document.</span><span class="sxs-lookup"><span data-stu-id="22fb3-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="22fb3-108">dans Langue du document.</span><span class="sxs-lookup"><span data-stu-id="22fb3-108">[in] The document language.</span></span> <span data-ttu-id="22fb3-109">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="22fb3-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="22fb3-110">dans Identité du fournisseur pour la langue du document.</span><span class="sxs-lookup"><span data-stu-id="22fb3-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="22fb3-111">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="22fb3-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="22fb3-112">dans Type du document.</span><span class="sxs-lookup"><span data-stu-id="22fb3-112">[in] The type of the document.</span></span> <span data-ttu-id="22fb3-113">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="22fb3-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="22fb3-114">à Pointeur vers l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="22fb3-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22fb3-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="22fb3-115">Return Value</span></span>  
 <span data-ttu-id="22fb3-116">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="22fb3-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22fb3-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="22fb3-117">Requirements</span></span>  
 <span data-ttu-id="22fb3-118">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="22fb3-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22fb3-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22fb3-119">See also</span></span>

- [<span data-ttu-id="22fb3-120">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="22fb3-120">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
