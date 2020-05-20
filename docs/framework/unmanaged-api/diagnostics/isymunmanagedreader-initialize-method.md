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
ms.openlocfilehash: 07d2de5d12fd769cb5cce243d9e721bb6fc185a7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615473"
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="1bcbb-102">ISymUnmanagedReader::Initialize, méthode</span><span class="sxs-lookup"><span data-stu-id="1bcbb-102">ISymUnmanagedReader::Initialize Method</span></span>
<span data-ttu-id="1bcbb-103">Initialise le lecteur de symboles avec l’interface de l’importateur de métadonnées à laquelle ce lecteur sera associé, ainsi que le nom de fichier du module.</span><span class="sxs-lookup"><span data-stu-id="1bcbb-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1bcbb-104">Cette méthode ne peut être appelée qu’une seule fois et doit être appelée avant toute autre méthode de lecteur.</span><span class="sxs-lookup"><span data-stu-id="1bcbb-104">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bcbb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bcbb-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bcbb-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1bcbb-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="1bcbb-107">dans Interface de l’importateur de métadonnées à laquelle ce lecteur sera associé.</span><span class="sxs-lookup"><span data-stu-id="1bcbb-107">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="1bcbb-108">dans Nom de fichier du module.</span><span class="sxs-lookup"><span data-stu-id="1bcbb-108">[in] The file name of the module.</span></span> <span data-ttu-id="1bcbb-109">Vous pouvez utiliser le `pIStream` paramètre à la place.</span><span class="sxs-lookup"><span data-stu-id="1bcbb-109">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="1bcbb-110">dans Chemin d’accès à rechercher.</span><span class="sxs-lookup"><span data-stu-id="1bcbb-110">[in] The path to search.</span></span> <span data-ttu-id="1bcbb-111">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="1bcbb-111">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="1bcbb-112">dans Le flux de fichier, utilisé comme alternative au paramètre filename.</span><span class="sxs-lookup"><span data-stu-id="1bcbb-112">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1bcbb-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1bcbb-113">Return Value</span></span>  
 <span data-ttu-id="1bcbb-114">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="1bcbb-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bcbb-115">Notes</span><span class="sxs-lookup"><span data-stu-id="1bcbb-115">Remarks</span></span>  
 <span data-ttu-id="1bcbb-116">Vous devez spécifier un seul des `filename` paramètres ou, mais `pIStream` pas les deux.</span><span class="sxs-lookup"><span data-stu-id="1bcbb-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="1bcbb-117">Le paramètre `searchPath` est facultatif.</span><span class="sxs-lookup"><span data-stu-id="1bcbb-117">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bcbb-118">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="1bcbb-118">Requirements</span></span>  
 <span data-ttu-id="1bcbb-119">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1bcbb-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bcbb-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1bcbb-120">See also</span></span>

- [<span data-ttu-id="1bcbb-121">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="1bcbb-121">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
