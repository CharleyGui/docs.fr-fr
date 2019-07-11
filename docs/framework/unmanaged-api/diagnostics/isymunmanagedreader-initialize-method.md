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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1986ed730c6f0a1ba8a2d8e3c688e6872184da9d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736757"
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="8ac61-102">ISymUnmanagedReader::Initialize, méthode</span><span class="sxs-lookup"><span data-stu-id="8ac61-102">ISymUnmanagedReader::Initialize Method</span></span>
<span data-ttu-id="8ac61-103">Initialise le lecteur de symboles avec l’interface d’importateur de métadonnées qui ce lecteur sera associé, ainsi que le nom de fichier du module.</span><span class="sxs-lookup"><span data-stu-id="8ac61-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ac61-104">Cette méthode peut être appelée qu’une seule fois et doit être appelée avant toute autre méthode de lecteur.</span><span class="sxs-lookup"><span data-stu-id="8ac61-104">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ac61-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ac61-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ac61-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8ac61-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="8ac61-107">[in] L’interface importateur de métadonnées avec laquelle ce lecteur sera associé.</span><span class="sxs-lookup"><span data-stu-id="8ac61-107">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="8ac61-108">[in] Le nom de fichier du module.</span><span class="sxs-lookup"><span data-stu-id="8ac61-108">[in] The file name of the module.</span></span> <span data-ttu-id="8ac61-109">Vous pouvez utiliser le `pIStream` paramètre à la place.</span><span class="sxs-lookup"><span data-stu-id="8ac61-109">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="8ac61-110">[in] Le chemin d’accès à rechercher.</span><span class="sxs-lookup"><span data-stu-id="8ac61-110">[in] The path to search.</span></span> <span data-ttu-id="8ac61-111">Ce paramètre est optionnel.</span><span class="sxs-lookup"><span data-stu-id="8ac61-111">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="8ac61-112">[in] Le flux de fichier, utilisé comme alternative au paramètre de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="8ac61-112">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ac61-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8ac61-113">Return Value</span></span>  
 <span data-ttu-id="8ac61-114">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="8ac61-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ac61-115">Notes</span><span class="sxs-lookup"><span data-stu-id="8ac61-115">Remarks</span></span>  
 <span data-ttu-id="8ac61-116">Vous devez spécifier un seul de le `filename` ou `pIStream` paramètres, pas les deux.</span><span class="sxs-lookup"><span data-stu-id="8ac61-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="8ac61-117">Le paramètre `searchPath` est optionnel.</span><span class="sxs-lookup"><span data-stu-id="8ac61-117">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ac61-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8ac61-118">Requirements</span></span>  
 <span data-ttu-id="8ac61-119">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8ac61-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ac61-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ac61-120">See also</span></span>

- [<span data-ttu-id="8ac61-121">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="8ac61-121">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
