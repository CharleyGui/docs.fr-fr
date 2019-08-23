---
title: -utf8output (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 789df84bb4011d1ad128c50a9c689d1217be6694
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937277"
---
# <a name="-utf8output-visual-basic"></a>-utf8output (Visual Basic)
Affiche les résultats de la compilation au format d'encodage UTF-8.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 facultatif. La valeur par défaut de cette `-utf8output-`option est, ce qui signifie que la sortie du compilateur n’utilise pas l’encodage UTF-8. Les options `-utf8output` et `-utf8output+` sont équivalentes.  
  
## <a name="remarks"></a>Notes  
 Dans certaines configurations internationales, la sortie du compilateur ne peut pas s’afficher correctement dans la console. Dans ce cas, utilisez `-utf8output` et redirigez la sortie du compilateur vers un fichier.  
  
> [!NOTE]
> L' `-utf8output` option n’est pas disponible dans l’environnement de développement Visual Studio; elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="example"></a>Exemples  
 Le code suivant compile `In.vb` et dirige le compilateur pour afficher la sortie à l’aide de l’encodage UTF-8.  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
