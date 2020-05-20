---
title: ISymUnmanagedWriter::DefineSequencePoints, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type:
- apiref
ms.openlocfilehash: 8889c412f414f38d1d18d33ec297e82fd052280d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614797"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a>ISymUnmanagedWriter::DefineSequencePoints, méthode
Définit un groupe de points de séquence dans la méthode actuelle. Chaque ligne de départ et colonne de début définissent le début d’une instruction dans une méthode. Chaque ligne de fin et colonne de fin définissent la fin d’une instruction dans une méthode. Les tableaux doivent être triés par ordre de décalage. L’offset est toujours mesuré à partir du début de la méthode, en octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
## <a name="parameters"></a>Paramètres  
 `document`  
 dans Objet document pour lequel les points de séquence sont définis.  
  
 `spCount`  
 dans `ULONG32`Qui indique la taille de chacun des tampons,,, `offsets` `lines` `columns` `endLines` et `endColumns` .  
  
 `offsets`  
 dans Décalage des points de séquence mesuré à partir du début de la méthode.  
  
 `lines`  
 dans Numéros de ligne de départ des points de séquence.  
  
 `columns`  
 dans Numéros de colonne de début des points de séquence.  
  
 `endLines`  
 dans Numéros de ligne de fin des points de séquence. Ce paramètre est facultatif.  
  
 `endColumns`  
 dans Numéros de colonne de fin des points de séquence. Ce paramètre est facultatif.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedWriter, interface](isymunmanagedwriter-interface.md)
