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
ms.openlocfilehash: 3685707f1983ffec413e9cea2df5034ac53f643a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615590"
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="63de9-102">ISymUnmanagedDocument::GetURL, méthode</span><span class="sxs-lookup"><span data-stu-id="63de9-102">ISymUnmanagedDocument::GetURL Method</span></span>
<span data-ttu-id="63de9-103">Retourne l’URL (Uniform Resource Locator) de ce document.</span><span class="sxs-lookup"><span data-stu-id="63de9-103">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63de9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63de9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63de9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="63de9-105">Parameters</span></span>  
 `cchUrl`  
 <span data-ttu-id="63de9-106">dans Taille, en caractères, de la `szURL` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="63de9-106">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="63de9-107">à Pointeur vers une variable qui reçoit la taille de l’URL, y compris la terminaison NULL.</span><span class="sxs-lookup"><span data-stu-id="63de9-107">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="63de9-108">à Mémoire tampon contenant l’URL.</span><span class="sxs-lookup"><span data-stu-id="63de9-108">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63de9-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="63de9-109">Return Value</span></span>  
 <span data-ttu-id="63de9-110">S_OK si la méthode est réussie ; Sinon, un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="63de9-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63de9-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63de9-111">See also</span></span>

- [<span data-ttu-id="63de9-112">ISymUnmanagedDocument, interface</span><span class="sxs-lookup"><span data-stu-id="63de9-112">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
