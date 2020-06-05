---
title: '#ExternalSource, directive'
ms.date: 07/20/2015
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
ms.openlocfilehash: e4c7704c32c3a6c73e069d0b7129d5386696b438
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402990"
---
# <a name="externalsource-directive"></a>#ExternalSource, directive

Indique un mappage entre des lignes spécifiques de code source et du texte externe à la source.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a>Éléments  

 `StringLiteral`  
 Chemin d’accès à la source externe.  
  
 `IntLiteral`  
 Numéro de ligne de la première ligne de la source externe.  
  
 `LogicalLine`  
 Ligne où l’erreur se produit dans la source externe.  
  
 `#End ExternalSource`  
 Met fin au bloc `#ExternalSource`.  
  
## <a name="remarks"></a>Notes  

 Cette directive est utilisée uniquement par le compilateur et le débogueur.  
  
 Un fichier source peut inclure des directives de source externe, qui indiquent un mappage entre des lignes de code spécifiques dans le fichier source et du texte externe à la source, tel qu’un fichier. aspx. Si des erreurs sont rencontrées dans le code source désigné pendant la compilation, elles sont identifiées comme provenant de la source externe.  
  
 Les directives de source externe n’ont aucun effet sur la compilation et ne peuvent pas être imbriquées. Ils sont destinés à un usage interne par l’application uniquement.  
  
## <a name="see-also"></a>Voir aussi

- [Compilation conditionnelle](../../programming-guide/program-structure/conditional-compilation.md)
