---
title: ISymUnmanagedReader::GetMethodFromDocumentPosition, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodFromDocumentPosition
helpviewer_keywords:
- GetMethodFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 55773dbc-9053-46e3-8a3c-86caa9d91fb4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a1935b831902e975616557f512789c339baf49c5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776976"
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="29e81-102">ISymUnmanagedReader::GetMethodFromDocumentPosition, méthode</span><span class="sxs-lookup"><span data-stu-id="29e81-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>
<span data-ttu-id="29e81-103">Retourne la méthode qui contient le point d’arrêt à la position donnée dans un document.</span><span class="sxs-lookup"><span data-stu-id="29e81-103">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29e81-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29e81-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29e81-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="29e81-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="29e81-106">[in] Le document spécifié.</span><span class="sxs-lookup"><span data-stu-id="29e81-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="29e81-107">[in] La ligne du document spécifié.</span><span class="sxs-lookup"><span data-stu-id="29e81-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="29e81-108">[in] La colonne du document spécifié.</span><span class="sxs-lookup"><span data-stu-id="29e81-108">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="29e81-109">[out] Un pointeur vers l’adresse d’un [ISymUnmanagedMethod, Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) objet qui représente la méthode contenant le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="29e81-109">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29e81-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="29e81-110">Return Value</span></span>  
 <span data-ttu-id="29e81-111">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="29e81-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29e81-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="29e81-112">Requirements</span></span>  
 <span data-ttu-id="29e81-113">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="29e81-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29e81-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29e81-114">See also</span></span>

- [<span data-ttu-id="29e81-115">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="29e81-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
