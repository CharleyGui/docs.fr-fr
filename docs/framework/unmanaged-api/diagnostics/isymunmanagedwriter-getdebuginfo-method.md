---
title: ISymUnmanagedWriter::GetDebugInfo, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.GetDebugInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type:
- apiref
ms.openlocfilehash: f8eb4cb6bad95295e10a72812fa8dbb0adfcc898
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614784"
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a><span data-ttu-id="eb58b-102">ISymUnmanagedWriter::GetDebugInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="eb58b-102">ISymUnmanagedWriter::GetDebugInfo Method</span></span>
<span data-ttu-id="eb58b-103">Retourne les informations nécessaires à un compilateur pour écrire l’entrée de répertoire de débogage dans l’en-tête de fichier exécutable portable (PE).</span><span class="sxs-lookup"><span data-stu-id="eb58b-103">Returns the information necessary for a compiler to write the debug directory entry in the portable executable (PE) file header.</span></span> <span data-ttu-id="eb58b-104">Le writer de symbole remplit tous les champs à l’exception de `TimeDateStamp` et `PointerToRawData` .</span><span class="sxs-lookup"><span data-stu-id="eb58b-104">The symbol writer fills out all fields except for `TimeDateStamp` and `PointerToRawData`.</span></span> <span data-ttu-id="eb58b-105">(Le compilateur est chargé de définir ces deux champs de manière appropriée.)</span><span class="sxs-lookup"><span data-stu-id="eb58b-105">(The compiler is responsible for setting these two fields appropriately.)</span></span>  
  
 <span data-ttu-id="eb58b-106">Un compilateur doit appeler cette méthode, émettre l’objet blob de données dans le fichier PE, définir le `PointerToRawData` champ dans le IMAGE_DEBUG_DIRECTORY de façon à ce qu’il pointe vers les données émises et écrire le IMAGE_DEBUG_DIRECTORY dans le fichier PE.</span><span class="sxs-lookup"><span data-stu-id="eb58b-106">A compiler should call this method, emit the data blob to the PE file, set the `PointerToRawData` field in the IMAGE_DEBUG_DIRECTORY to point to the emitted data, and write the IMAGE_DEBUG_DIRECTORY to the PE file.</span></span> <span data-ttu-id="eb58b-107">Le compilateur doit également définir le `TimeDateStamp` champ pour qu’il soit égal à la valeur `TimeDateStamp` du fichier PE en cours de génération.</span><span class="sxs-lookup"><span data-stu-id="eb58b-107">The compiler should also set the `TimeDateStamp` field to equal the `TimeDateStamp` of the PE file being generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb58b-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb58b-108">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb58b-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="eb58b-109">Parameters</span></span>  
 `pIDD`  
 <span data-ttu-id="eb58b-110">[in, out] Pointeur vers une IMAGE_DEBUG_DIRECTORY que le writer de symbole remplira.</span><span class="sxs-lookup"><span data-stu-id="eb58b-110">[in, out] A pointer to an IMAGE_DEBUG_DIRECTORY that the symbol writer will fill out.</span></span>  
  
 `cData`  
 <span data-ttu-id="eb58b-111">dans `DWORD`Qui contient la taille des données de débogage.</span><span class="sxs-lookup"><span data-stu-id="eb58b-111">[in] A `DWORD` that contains the size of the debug data.</span></span>  
  
 `pcData`  
 <span data-ttu-id="eb58b-112">à Pointeur vers un `DWORD` qui reçoit la taille de la mémoire tampon requise pour contenir les données de débogage.</span><span class="sxs-lookup"><span data-stu-id="eb58b-112">[out] A pointer to a `DWORD` that receives the size of the buffer required to contain the debug data.</span></span>  
  
 `data`  
 <span data-ttu-id="eb58b-113">à Pointeur vers une mémoire tampon qui est suffisamment grande pour contenir les données de débogage pour le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="eb58b-113">[out] A pointer to a buffer that is large enough to hold the debug data for the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eb58b-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="eb58b-114">Return Value</span></span>  
 <span data-ttu-id="eb58b-115">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="eb58b-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb58b-116">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="eb58b-116">Requirements</span></span>  
 <span data-ttu-id="eb58b-117">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="eb58b-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb58b-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb58b-118">See also</span></span>

- [<span data-ttu-id="eb58b-119">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="eb58b-119">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
