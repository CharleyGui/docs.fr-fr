---
title: ISymUnmanagedBinder2::GetReaderForFile2, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2.GetReaderForFile2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2
helpviewer_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2 method [.NET Framework debugging]
- GetReaderForFile2 method [.NET Framework debugging]
ms.assetid: dd92dcaf-403c-464d-a254-21594985dddd
topic_type:
- apiref
ms.openlocfilehash: 97b9fa537fdd9147d6d9eda036013add5393e33c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441706"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a><span data-ttu-id="5b8de-102">ISymUnmanagedBinder2::GetReaderForFile2, méthode</span><span class="sxs-lookup"><span data-stu-id="5b8de-102">ISymUnmanagedBinder2::GetReaderForFile2 Method</span></span>
<span data-ttu-id="5b8de-103">À partir d’une interface de métadonnées et d’un nom de fichier, retourne l’interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) appropriée qui lira les symboles de débogage associés au module.</span><span class="sxs-lookup"><span data-stu-id="5b8de-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="5b8de-104">Cette méthode fournit une recherche plus complète pour le fichier de base de données du programme (PDB) que la méthode [ISymUnmanagedBinder :: GetReaderForFile,](isymunmanagedbinder-getreaderforfile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5b8de-104">This method provides a more extensive search for the program database (PDB) file than the [ISymUnmanagedBinder::GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b8de-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b8de-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b8de-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5b8de-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="5b8de-107">dans Pointeur vers l’interface d’importation de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="5b8de-107">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="5b8de-108">dans Pointeur vers le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="5b8de-108">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="5b8de-109">dans Pointeur vers le chemin de recherche.</span><span class="sxs-lookup"><span data-stu-id="5b8de-109">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="5b8de-110">dans Valeur de l’énumération [CorSymSearchPolicyAttributes,](corsymsearchpolicyattributes-enumeration.md) qui spécifie la stratégie à utiliser lors de la recherche d’un lecteur de symboles.</span><span class="sxs-lookup"><span data-stu-id="5b8de-110">[in] A value of the [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="5b8de-111">à Pointeur qui a pour valeur l’interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) retournée.</span><span class="sxs-lookup"><span data-stu-id="5b8de-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b8de-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5b8de-112">Return Value</span></span>  
 <span data-ttu-id="5b8de-113">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="5b8de-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b8de-114">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="5b8de-114">Requirements</span></span>  
 <span data-ttu-id="5b8de-115">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="5b8de-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b8de-116">Notes</span><span class="sxs-lookup"><span data-stu-id="5b8de-116">Remarks</span></span>  
 <span data-ttu-id="5b8de-117">Cette version de la méthode peut rechercher le fichier PDB dans des zones autres que juste à côté du module.</span><span class="sxs-lookup"><span data-stu-id="5b8de-117">This version of the method can search for the PDB file in areas other than right next to the module.</span></span> <span data-ttu-id="5b8de-118">La stratégie de recherche peut être contrôlée en combinant [CorSymSearchPolicyAttributes,](corsymsearchpolicyattributes-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="5b8de-118">The search policy can be controlled by combining [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md).</span></span> <span data-ttu-id="5b8de-119">Par exemple, `AllowReferencePathAccess | AllowSymbolServerAccess` recherche le fichier PDB en regard du fichier exécutable et sur un serveur de symboles, mais n’interroge le registre ou n’utilise pas le chemin d’accès dans le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="5b8de-119">For example, `AllowReferencePathAccess | AllowSymbolServerAccess` looks for the PDB next to the executable file and on a symbol server, but does not query the registry or use the path in the executable file.</span></span> <span data-ttu-id="5b8de-120">Si le `searchPath` paramètre est fourni, la recherche sera toujours effectuée dans ces répertoires.</span><span class="sxs-lookup"><span data-stu-id="5b8de-120">If the `searchPath` parameter is provided, those directories will always be searched.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b8de-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b8de-121">See also</span></span>

- [<span data-ttu-id="5b8de-122">ISymUnmanagedBinder2, interface</span><span class="sxs-lookup"><span data-stu-id="5b8de-122">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="5b8de-123">GetReaderForFile, méthode</span><span class="sxs-lookup"><span data-stu-id="5b8de-123">GetReaderForFile Method</span></span>](isymunmanagedbinder-getreaderforfile-method.md)
