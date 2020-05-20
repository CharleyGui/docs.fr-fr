---
title: ISymUnmanagedBinder::GetReaderForFile, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderForFile
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderForFile
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderForFile method [.NET Framework debugging]
- GetReaderForFile method [.NET Framework debugging]
ms.assetid: 46c06258-831e-47c8-a50a-8650af6b637e
topic_type:
- apiref
ms.openlocfilehash: c4416e8e4395c4e1967155310d12a1eb68c42d83
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441732"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a><span data-ttu-id="2ac00-102">ISymUnmanagedBinder::GetReaderForFile, méthode</span><span class="sxs-lookup"><span data-stu-id="2ac00-102">ISymUnmanagedBinder::GetReaderForFile Method</span></span>
<span data-ttu-id="2ac00-103">À partir d’une interface de métadonnées et d’un nom de fichier, retourne l’interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) appropriée qui lira les symboles de débogage associés au module.</span><span class="sxs-lookup"><span data-stu-id="2ac00-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="2ac00-104">Cette méthode ouvre le fichier de base de données du programme (PDB) uniquement s’il est en regard du fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="2ac00-104">This method will open the program database (PDB) file only if it is next to the executable file.</span></span> <span data-ttu-id="2ac00-105">Cette modification a été apportée pour des raisons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="2ac00-105">This change has been made for security purposes.</span></span> <span data-ttu-id="2ac00-106">Si vous avez besoin d’une recherche plus complète pour le fichier PDB, utilisez la méthode [ISymUnmanagedBinder2 :: GetReaderForFile2,](isymunmanagedbinder2-getreaderforfile2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2ac00-106">If you need a more extensive search for the PDB file, use the [ISymUnmanagedBinder2::GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ac00-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ac00-107">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ac00-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ac00-108">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="2ac00-109">dans Pointeur vers l’interface d’importation de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="2ac00-109">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="2ac00-110">dans Pointeur vers le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="2ac00-110">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="2ac00-111">dans Pointeur vers le chemin de recherche.</span><span class="sxs-lookup"><span data-stu-id="2ac00-111">[in] A pointer to the search path.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="2ac00-112">à Pointeur qui a pour valeur l’interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) retournée.</span><span class="sxs-lookup"><span data-stu-id="2ac00-112">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ac00-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2ac00-113">Return Value</span></span>  
 <span data-ttu-id="2ac00-114">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="2ac00-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ac00-115">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="2ac00-115">Requirements</span></span>  
 <span data-ttu-id="2ac00-116">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2ac00-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ac00-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ac00-117">See also</span></span>

- [<span data-ttu-id="2ac00-118">ISymUnmanagedBinder, interface</span><span class="sxs-lookup"><span data-stu-id="2ac00-118">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="2ac00-119">GetReaderForFile2, méthode</span><span class="sxs-lookup"><span data-stu-id="2ac00-119">GetReaderForFile2 Method</span></span>](isymunmanagedbinder2-getreaderforfile2-method.md)
