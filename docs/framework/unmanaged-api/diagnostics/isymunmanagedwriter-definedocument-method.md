---
title: ISymUnmanagedWriter::DefineDocument, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineDocument
helpviewer_keywords:
- ISymUnmanagedWriter::DefineDocument method [.NET Framework debugging]
- DefineDocument method [.NET Framework debugging]
ms.assetid: c3bf15b0-3250-4bbe-b9b5-c5d695289b6f
topic_type:
- apiref
ms.openlocfilehash: fdcfb0c4f9c21eb516f4196d0c8f682669468219
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615226"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a><span data-ttu-id="da826-102">ISymUnmanagedWriter::DefineDocument, méthode</span><span class="sxs-lookup"><span data-stu-id="da826-102">ISymUnmanagedWriter::DefineDocument Method</span></span>
<span data-ttu-id="da826-103">Définit un document source.</span><span class="sxs-lookup"><span data-stu-id="da826-103">Defines a source document.</span></span> <span data-ttu-id="da826-104">Les GUID sont fournis pour les langages connus, les fournisseurs et les types de documents.</span><span class="sxs-lookup"><span data-stu-id="da826-104">GUIDs are provided for known languages, vendors, and document types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da826-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da826-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da826-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="da826-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="da826-107">dans Pointeur vers un `WCHAR` qui définit l’URL (Uniform Resource Locator) qui identifie le document.</span><span class="sxs-lookup"><span data-stu-id="da826-107">[in] A pointer to a `WCHAR` that defines the uniform resource locator (URL) that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="da826-108">dans Pointeur vers un GUID qui définit la langue du document.</span><span class="sxs-lookup"><span data-stu-id="da826-108">[in] A pointer to a GUID that defines the document language.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="da826-109">dans Pointeur vers un GUID qui définit l’identité du fournisseur pour le langage du document.</span><span class="sxs-lookup"><span data-stu-id="da826-109">[in] A pointer to a GUID that defines the identity of the vendor for the document language.</span></span>  
  
 `documentType`  
 <span data-ttu-id="da826-110">dans Pointeur vers un GUID qui définit le type du document.</span><span class="sxs-lookup"><span data-stu-id="da826-110">[in] A pointer to a GUID that defines the type of the document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="da826-111">à Pointeur vers l’interface [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) retournée.</span><span class="sxs-lookup"><span data-stu-id="da826-111">[out] A pointer to the returned [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da826-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="da826-112">Return Value</span></span>  
 <span data-ttu-id="da826-113">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="da826-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da826-114">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="da826-114">Requirements</span></span>  
 <span data-ttu-id="da826-115">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="da826-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da826-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da826-116">See also</span></span>

- [<span data-ttu-id="da826-117">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="da826-117">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
