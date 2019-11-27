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
ms.openlocfilehash: fa0a40827c1b3865b90c7d796ea4dd364774e1c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343829"
---
# <a name="externalsource-directive"></a>#ExternalSource, directive

Indique un mappage entre des lignes spécifiques de code source et du texte externe à la source.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a>Composants  

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

- [Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
