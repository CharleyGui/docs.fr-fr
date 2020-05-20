---
title: ISymUnmanagedDocument, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument
helpviewer_keywords:
- ISymUnmanagedDocument interface [.NET Framework debugging]
ms.assetid: 5c26b366-6e81-467c-9dd0-02dd26fee0a3
topic_type:
- apiref
ms.openlocfilehash: a8ff6d3a925773e58e0713a87b167420c246f85b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615564"
---
# <a name="isymunmanageddocument-interface"></a>ISymUnmanagedDocument, interface
Représente un document référencé par un magasin de symboles. Un document est défini par une URL (Uniform Resource Locator) et un GUID de type de document. Vous pouvez localiser le document, quelle que soit la manière dont il est stocké à l’aide de l’URL et du GUID du type de document. Vous pouvez stocker la source du document dans le magasin de symboles et la récupérer par le biais de cette interface.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[FindClosestLine, méthode](isymunmanageddocument-findclosestline-method.md)|Retourne la ligne la plus proche qui est un point de séquence, en fonction d’une ligne dans ce document qui peut être ou non un point de séquence.|  
|[GetCheckSum, méthode](isymunmanageddocument-getchecksum-method.md)|Obtient la somme de contrôle.|  
|[GetCheckSumAlgorithmId, méthode](isymunmanageddocument-getchecksumalgorithmid-method.md)|Obtient l’identificateur de l’algorithme de somme de contrôle, ou retourne un GUID de tous les zéros s’il n’y a pas de somme de contrôle.|  
|[GetDocumentType, méthode](isymunmanageddocument-getdocumenttype-method.md)|Obtient le type de document de ce document.|  
|[GetLanguage, méthode](isymunmanageddocument-getlanguage-method.md)|Obtient l’identificateur de langue de ce document.|  
|[GetLanguageVendor, méthode](isymunmanageddocument-getlanguagevendor-method.md)|Obtient le fournisseur de langage de ce document.|  
|[GetSourceLength, méthode](isymunmanageddocument-getsourcelength-method.md)|Obtient la longueur, en octets, de la source incorporée.|  
|[GetSourceRange, méthode](isymunmanageddocument-getsourcerange-method.md)|Retourne la plage spécifiée de la source incorporée dans la mémoire tampon donnée.|  
|[GetURL, méthode](isymunmanageddocument-geturl-method.md)|Retourne l’URL de ce document.|  
|[HasEmbeddedSource, méthode](isymunmanageddocument-hasembeddedsource-method.md)|Retourne `true` si la source du document est incorporée dans les symboles de débogage ; sinon, retourne `false` .|  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](diagnostics-symbol-store-interfaces.md)
