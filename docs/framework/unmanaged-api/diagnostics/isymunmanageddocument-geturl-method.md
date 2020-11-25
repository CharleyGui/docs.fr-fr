---
title: ISymUnmanagedDocument::GetURL, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetURL
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetURL
helpviewer_keywords:
- GetURL method [.NET Framework debugging]
- ISymUnmanagedDocument::GetURL method [.NET Framework debugging]
ms.assetid: 60600178-c2b5-4cab-b3a5-f0f61acebaf1
topic_type:
- apiref
ms.openlocfilehash: c862b6d3bfa415b622b68898db1ff30c6759e8f2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726936"
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="f8580-102">ISymUnmanagedDocument::GetURL, méthode</span><span class="sxs-lookup"><span data-stu-id="f8580-102">ISymUnmanagedDocument::GetURL Method</span></span>

<span data-ttu-id="f8580-103">Retourne l’URL (Uniform Resource Locator) de ce document.</span><span class="sxs-lookup"><span data-stu-id="f8580-103">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8580-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8580-104">Syntax</span></span>  
  
```cpp  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8580-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f8580-105">Parameters</span></span>  

 `cchUrl`  
 <span data-ttu-id="f8580-106">dans Taille, en caractères, de la `szURL` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="f8580-106">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="f8580-107">à Pointeur vers une variable qui reçoit la taille de l’URL, y compris la terminaison NULL.</span><span class="sxs-lookup"><span data-stu-id="f8580-107">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="f8580-108">à Mémoire tampon contenant l’URL.</span><span class="sxs-lookup"><span data-stu-id="f8580-108">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8580-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="f8580-109">Return Value</span></span>  

 <span data-ttu-id="f8580-110">S_OK si la méthode est réussie ; Sinon, un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="f8580-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8580-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8580-111">See also</span></span>

- [<span data-ttu-id="f8580-112">ISymUnmanagedDocument, interface</span><span class="sxs-lookup"><span data-stu-id="f8580-112">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
