---
title: ISymUnmanagedReader::Initialize, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type:
- apiref
ms.openlocfilehash: ca34d1d84d6f9960d021c35566f8412df321464d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429736"
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="88384-102">ISymUnmanagedReader::Initialize, méthode</span><span class="sxs-lookup"><span data-stu-id="88384-102">ISymUnmanagedReader::Initialize Method</span></span>
<span data-ttu-id="88384-103">Initialise le lecteur de symboles avec l’interface de l’importateur de métadonnées à laquelle ce lecteur sera associé, ainsi que le nom de fichier du module.</span><span class="sxs-lookup"><span data-stu-id="88384-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="88384-104">Cette méthode ne peut être appelée qu’une seule fois et doit être appelée avant toute autre méthode de lecteur.</span><span class="sxs-lookup"><span data-stu-id="88384-104">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88384-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88384-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88384-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="88384-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="88384-107">dans Interface de l’importateur de métadonnées à laquelle ce lecteur sera associé.</span><span class="sxs-lookup"><span data-stu-id="88384-107">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="88384-108">dans Nom de fichier du module.</span><span class="sxs-lookup"><span data-stu-id="88384-108">[in] The file name of the module.</span></span> <span data-ttu-id="88384-109">Vous pouvez utiliser le paramètre `pIStream` à la place.</span><span class="sxs-lookup"><span data-stu-id="88384-109">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="88384-110">dans Chemin d’accès à rechercher.</span><span class="sxs-lookup"><span data-stu-id="88384-110">[in] The path to search.</span></span> <span data-ttu-id="88384-111">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="88384-111">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="88384-112">dans Le flux de fichier, utilisé comme alternative au paramètre filename.</span><span class="sxs-lookup"><span data-stu-id="88384-112">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88384-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="88384-113">Return Value</span></span>  
 <span data-ttu-id="88384-114">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="88384-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88384-115">Notes</span><span class="sxs-lookup"><span data-stu-id="88384-115">Remarks</span></span>  
 <span data-ttu-id="88384-116">Vous ne devez spécifier qu’un seul des paramètres `filename` ou `pIStream`, pas les deux.</span><span class="sxs-lookup"><span data-stu-id="88384-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="88384-117">Le paramètre `searchPath` est optionnel.</span><span class="sxs-lookup"><span data-stu-id="88384-117">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88384-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="88384-118">Requirements</span></span>  
 <span data-ttu-id="88384-119">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="88384-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88384-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88384-120">See also</span></span>

- [<span data-ttu-id="88384-121">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="88384-121">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
