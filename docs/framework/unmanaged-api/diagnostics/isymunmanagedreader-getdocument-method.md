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
ms.openlocfilehash: 950fb3b9c51ae2c9470b5aadd31c877d7aa6b6f6
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615057"
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="a7f45-102">ISymUnmanagedReader::GetDocument, méthode</span><span class="sxs-lookup"><span data-stu-id="a7f45-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="a7f45-103">Recherche un document.</span><span class="sxs-lookup"><span data-stu-id="a7f45-103">Finds a document.</span></span> <span data-ttu-id="a7f45-104">La langue, le fournisseur et le type du document sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="a7f45-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7f45-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7f45-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7f45-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a7f45-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="a7f45-107">dans URL qui identifie le document.</span><span class="sxs-lookup"><span data-stu-id="a7f45-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="a7f45-108">dans Langue du document.</span><span class="sxs-lookup"><span data-stu-id="a7f45-108">[in] The document language.</span></span> <span data-ttu-id="a7f45-109">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="a7f45-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="a7f45-110">dans Identité du fournisseur pour la langue du document.</span><span class="sxs-lookup"><span data-stu-id="a7f45-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="a7f45-111">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="a7f45-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="a7f45-112">dans Type du document.</span><span class="sxs-lookup"><span data-stu-id="a7f45-112">[in] The type of the document.</span></span> <span data-ttu-id="a7f45-113">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="a7f45-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="a7f45-114">à Pointeur vers l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="a7f45-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7f45-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a7f45-115">Return Value</span></span>  
 <span data-ttu-id="a7f45-116">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="a7f45-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7f45-117">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="a7f45-117">Requirements</span></span>  
 <span data-ttu-id="a7f45-118">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a7f45-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7f45-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7f45-119">See also</span></span>

- [<span data-ttu-id="a7f45-120">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="a7f45-120">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
