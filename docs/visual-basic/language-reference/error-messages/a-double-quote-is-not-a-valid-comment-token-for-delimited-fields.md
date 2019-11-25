---
title: Les guillemets doubles ne constituent pas un jeton de commentaire valide pour les champs délimités quand EscapeQuote a la valeur True
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_InvalidComment
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
ms.openlocfilehash: df7868c510eaacbad1d4421259234f4187f60cd7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976218"
---
# <a name="a-double-quote-is-not-a-valid-comment-token-for-delimited-fields-where-escapequote-is-set-to-true"></a>Les guillemets doubles ne constituent pas un jeton de commentaire valide pour les champs délimités quand EscapeQuote a la valeur True

Un guillemet a été fourni comme délimiteur pour `TextFieldParser`, mais `EscapeQuotes` a la valeur `True`.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Affectez la valeur `EscapeQuotes` à `False`.  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>
- [Guide pratique : lire des fichiers texte délimités par des virgules](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
