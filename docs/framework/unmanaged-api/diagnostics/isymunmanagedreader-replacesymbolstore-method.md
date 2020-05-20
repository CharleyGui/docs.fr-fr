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
ms.openlocfilehash: db2137146ded5200e05bbf88e23ae599f3eb7dec
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615447"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="be193-102">ISymUnmanagedReader::ReplaceSymbolStore, méthode</span><span class="sxs-lookup"><span data-stu-id="be193-102">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>
<span data-ttu-id="be193-103">Remplace le magasin de symboles existant par un magasin de symboles delta.</span><span class="sxs-lookup"><span data-stu-id="be193-103">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="be193-104">Cette méthode est similaire à la méthode [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) , à ceci près que le delta donné agit comme un remplacement complet plutôt qu’une mise à jour.</span><span class="sxs-lookup"><span data-stu-id="be193-104">This method is similar to the [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="be193-105">Vous devez spécifier un seul des `filename` paramètres ou `pIStream` , mais pas les deux.</span><span class="sxs-lookup"><span data-stu-id="be193-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="be193-106">Si `filename` est spécifié, le magasin de symboles est mis à jour avec les symboles dans ce fichier.</span><span class="sxs-lookup"><span data-stu-id="be193-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="be193-107">Si `pIStream` est spécifié, le magasin est mis à jour avec les données de <xref:System.Runtime.InteropServices.ComTypes.IStream> .</span><span class="sxs-lookup"><span data-stu-id="be193-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be193-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be193-108">Syntax</span></span>  
  
```cpp  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be193-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="be193-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="be193-110">dans Nom du fichier contenant le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="be193-110">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="be193-111">dans Le flux de fichier, utilisé comme alternative au `filename` paramètre.</span><span class="sxs-lookup"><span data-stu-id="be193-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be193-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="be193-112">Return Value</span></span>  
 <span data-ttu-id="be193-113">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="be193-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be193-114">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="be193-114">Requirements</span></span>  
 <span data-ttu-id="be193-115">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="be193-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be193-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be193-116">See also</span></span>

- [<span data-ttu-id="be193-117">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="be193-117">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
