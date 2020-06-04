---
title: -utf8output
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 0a16cdc535de5ed0619bf080bb4637449b11cfef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403055"
---
# <a name="-utf8output-visual-basic"></a>-utf8output (Visual Basic)
Affiche les résultats de la compilation au format d'encodage UTF-8.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Facultatif. La valeur par défaut de cette option est `-utf8output-` , ce qui signifie que la sortie du compilateur n’utilise pas l’encodage UTF-8. Les options `-utf8output` et `-utf8output+` sont équivalentes.  
  
## <a name="remarks"></a>Notes  
 Dans certaines configurations internationales, la sortie du compilateur ne peut pas s’afficher correctement dans la console. Dans ce cas, utilisez `-utf8output` et redirigez la sortie du compilateur vers un fichier.  
  
> [!NOTE]
> L' `-utf8output` option n’est pas disponible dans l’environnement de développement Visual Studio ; elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `In.vb` et dirige le compilateur pour afficher la sortie à l’aide de l’encodage UTF-8.  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](index.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
