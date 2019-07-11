---
title: ISymUnmanagedReader::ReplaceSymbolStore, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.ReplaceSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::ReplaceSymbolStore
helpviewer_keywords:
- ReplaceSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::ReplaceSymbolStore method [.NET Framework debugging]
ms.assetid: 43257761-8cb1-4eaf-8fb5-1f3980cb66cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 525ec4828fb942aeb447940ea68a523cd7c69140
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736726"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="218e2-102">ISymUnmanagedReader::ReplaceSymbolStore, méthode</span><span class="sxs-lookup"><span data-stu-id="218e2-102">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>
<span data-ttu-id="218e2-103">Remplace le magasin de symboles existant par un magasin de symboles delta.</span><span class="sxs-lookup"><span data-stu-id="218e2-103">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="218e2-104">Cette méthode est similaire à la [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) (méthode), à ceci près que le delta donné opère un remplacement complet plutôt qu’une mise à jour.</span><span class="sxs-lookup"><span data-stu-id="218e2-104">This method is similar to the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="218e2-105">Vous devez spécifier un seul de le `filename` ou `pIStream` paramètres, pas les deux.</span><span class="sxs-lookup"><span data-stu-id="218e2-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="218e2-106">Si `filename` est spécifié, le magasin de symboles sera actualisée avec les symboles dans ce fichier.</span><span class="sxs-lookup"><span data-stu-id="218e2-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="218e2-107">Si `pIStream` est spécifié, le magasin sera actualisé avec les données à partir de la <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span><span class="sxs-lookup"><span data-stu-id="218e2-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="218e2-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="218e2-108">Syntax</span></span>  
  
```cpp  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="218e2-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="218e2-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="218e2-110">[in] Le nom du fichier contenant le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="218e2-110">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="218e2-111">[in] Le flux de fichier, utilisé comme alternative à le `filename` paramètre.</span><span class="sxs-lookup"><span data-stu-id="218e2-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="218e2-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="218e2-112">Return Value</span></span>  
 <span data-ttu-id="218e2-113">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="218e2-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="218e2-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="218e2-114">Requirements</span></span>  
 <span data-ttu-id="218e2-115">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="218e2-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="218e2-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="218e2-116">See also</span></span>

- [<span data-ttu-id="218e2-117">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="218e2-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
