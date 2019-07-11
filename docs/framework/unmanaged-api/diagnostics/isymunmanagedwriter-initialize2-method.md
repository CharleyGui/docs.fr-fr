---
title: ISymUnmanagedWriter::Initialize2, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4087bdd82041152a9946a576e0eb96bf63f177c7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777272"
---
# <a name="isymunmanagedwriterinitialize2-method"></a><span data-ttu-id="38f0a-102">ISymUnmanagedWriter::Initialize2, méthode</span><span class="sxs-lookup"><span data-stu-id="38f0a-102">ISymUnmanagedWriter::Initialize2 Method</span></span>
<span data-ttu-id="38f0a-103">Définit l’interface d’émetteur de métadonnées avec laquelle ce writer sera associé et définit le nom de fichier de sortie dans lequel les symboles de débogage doit être écrite.</span><span class="sxs-lookup"><span data-stu-id="38f0a-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span> <span data-ttu-id="38f0a-104">Cette méthode vous permet également de définir l’emplacement final du fichier programme (PDB) de la base de données.</span><span class="sxs-lookup"><span data-stu-id="38f0a-104">This method also lets you set the final location of the program database (PDB) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38f0a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38f0a-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38f0a-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="38f0a-106">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="38f0a-107">[in] Pointeur vers l’interface d’émetteur de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="38f0a-107">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `tempfilename`  
 <span data-ttu-id="38f0a-108">[in] Un pointeur vers un `WCHAR` qui contient le nom de fichier dans lequel les symboles de débogage sont écrits.</span><span class="sxs-lookup"><span data-stu-id="38f0a-108">[in] A pointer to a `WCHAR` that contains the file name to which the debugging symbols are written.</span></span> <span data-ttu-id="38f0a-109">Si vous spécifiez un nom de fichier pour un writer qui n'utilise pas les noms de fichiers, ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="38f0a-109">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="38f0a-110">[in] Si spécifié, le writer de symbole émet les symboles dans la donnée <xref:System.Runtime.InteropServices.ComTypes.IStream> plutôt que dans le fichier spécifié dans le `filename` paramètre.</span><span class="sxs-lookup"><span data-stu-id="38f0a-110">[in] If specified, the symbol writer emits the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="38f0a-111">Le paramètre `pIStream` est optionnel.</span><span class="sxs-lookup"><span data-stu-id="38f0a-111">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="38f0a-112">[in] `true` s’il s’agit d’une régénération complète ; `false` s’il s’agit d’une compilation incrémentielle.</span><span class="sxs-lookup"><span data-stu-id="38f0a-112">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
 `finalfilename`  
 <span data-ttu-id="38f0a-113">[in] Un pointeur vers un `WCHAR` qui est la chaîne de chemin d’accès à l’emplacement final du fichier PDB.</span><span class="sxs-lookup"><span data-stu-id="38f0a-113">[in] A pointer to a `WCHAR` that is the path string to the final location of the PDB file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38f0a-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="38f0a-114">Return Value</span></span>  
 <span data-ttu-id="38f0a-115">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="38f0a-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38f0a-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="38f0a-116">Requirements</span></span>  
 <span data-ttu-id="38f0a-117">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="38f0a-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38f0a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38f0a-118">See also</span></span>

- [<span data-ttu-id="38f0a-119">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="38f0a-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="38f0a-120">Initialize, méthode</span><span class="sxs-lookup"><span data-stu-id="38f0a-120">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)
