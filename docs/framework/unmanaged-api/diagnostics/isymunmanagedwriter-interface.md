---
title: ISymUnmanagedWriter, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter
helpviewer_keywords:
- ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 7d6733ec-f081-4166-bc17-de09e16dc304
topic_type:
- apiref
ms.openlocfilehash: fddfd2a163f6e6513b648ee0b724c0b5bd54c81a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722932"
---
# <a name="isymunmanagedwriter-interface"></a>ISymUnmanagedWriter, interface

Représente un writer de symboles et fournit des méthodes pour définir des documents, des points de séquence, des étendues lexicales et des variables.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Abort, méthode](isymunmanagedwriter-abort-method.md)|Ferme le writer de symbole sans valider les symboles dans le magasin de symboles.|  
|[Close, méthode](isymunmanagedwriter-close-method.md)|Ferme le writer de symbole après avoir validé les symboles dans le magasin de symboles.|  
|[CloseMethod, méthode](isymunmanagedwriter-closemethod-method.md)|Ferme la méthode actuelle. Une fois qu’une méthode est fermée, aucun autre symbole ne peut être défini à l’intérieur de celle-ci.|  
|[CloseNamespace, méthode](isymunmanagedwriter-closenamespace-method.md)|Ferme l’espace de noms le plus récemment ouvert.|  
|[CloseScope, méthode](isymunmanagedwriter-closescope-method.md)|Ferme la portée lexicale actuelle.|  
|[DefineConstant, méthode](isymunmanagedwriter-defineconstant-method.md)|Définit un nom pour une valeur de constante.|  
|[DefineDocument, méthode](isymunmanagedwriter-definedocument-method.md)|Définit un document source.|  
|[DefineField, méthode](isymunmanagedwriter-definefield-method.md)|Définit une variable unique qui ne se trouve pas dans une méthode.|  
|[DefineGlobalVariable, méthode](isymunmanagedwriter-defineglobalvariable-method.md)|Définit une variable globale unique.|  
|[DefineLocalVariable, méthode](isymunmanagedwriter-definelocalvariable-method.md)|Définit une variable unique dans la portée lexicale actuelle.|  
|[DefineParameter, méthode](isymunmanagedwriter-defineparameter-method.md)|Définit un paramètre unique dans la méthode en cours.|  
|[DefineSequencePoints, méthode](isymunmanagedwriter-definesequencepoints-method.md)|Définit un groupe de points de séquence dans la méthode actuelle.|  
|[GetDebugInfo, méthode](isymunmanagedwriter-getdebuginfo-method.md)|Retourne les informations nécessaires à un compilateur pour écrire l’entrée de répertoire de débogage dans l’en-tête de fichier exécutable portable (PE).|  
|[Initialize, méthode](isymunmanagedwriter-initialize-method.md)|Définit l’interface d’émetteur de métadonnées à laquelle ce writer sera associé et définit le nom du fichier de sortie dans lequel les symboles de débogage seront écrits.|  
|[Initialize2, méthode](isymunmanagedwriter-initialize2-method.md)|Définit l’interface d’émetteur de métadonnées à laquelle ce writer sera associé, définit le nom du fichier de sortie dans lequel les symboles de débogage seront écrits et définit l’emplacement final du fichier de base de données du programme (PDB).|  
|[OpenMethod, méthode](isymunmanagedwriter-openmethod-method.md)|Ouvre une méthode dans laquelle les informations de symboles sont émises.|  
|[OpenNamespace, méthode](isymunmanagedwriter-opennamespace-method.md)|Ouvre un nouvel espace de noms.|  
|[OpenScope, méthode](isymunmanagedwriter-openscope-method.md)|Ouvre une nouvelle portée lexicale dans la méthode actuelle.|  
|[RemapToken, méthode](isymunmanagedwriter-remaptoken-method.md)|Notifie le writer de symbole qu’un jeton de métadonnées a été remappé à la sortie des métadonnées.|  
|[SetMethodSourceRange, méthode](isymunmanagedwriter-setmethodsourcerange-method.md)|Spécifie les véritables début et fin d'une méthode dans un fichier source.|  
|[SetScopeRange, méthode](isymunmanagedwriter-setscoperange-method.md)|Définit la plage d'offsets pour la portée lexicale spécifiée.|  
|[SetSymAttribute, méthode](isymunmanagedwriter-setsymattribute-method.md)|Définit un attribut personnalisé en fonction de son nom.|  
|[SetUserEntryPoint, méthode](isymunmanagedwriter-setuserentrypoint-method.md)|Spécifie la méthode définie par l’utilisateur qui est le point d’entrée de ce module.|  
|[UsingNamespace, méthode](isymunmanagedwriter-usingnamespace-method.md)|Spécifie que le nom d’espace de noms complet donné est utilisé dans la portée lexicale actuellement ouverte.|  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter2, interface](isymunmanagedwriter2-interface.md)
- [ISymUnmanagedWriter3, interface](isymunmanagedwriter3-interface.md)
