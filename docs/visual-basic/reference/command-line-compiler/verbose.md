---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 5b3899462af7c4aa8e0f77377a8d7485975f9867
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937258"
---
# <a name="-verbose"></a>-verbose
Fait en sorte que le compilateur génère des messages d’État et d’erreur détaillés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 facultatif. La `-verbose` spécification de est identique à `-verbose+`la spécification de, ce qui amène le compilateur à émettre des messages détaillés. La valeur par défaut de cette `-verbose-`option est.  
  
## <a name="remarks"></a>Notes  
 L' `-verbose` option affiche des informations sur le nombre total d’erreurs émises par le compilateur, signale les assemblys qui sont chargés par un module et affiche les fichiers en cours de compilation.  
  
> [!NOTE]
> L' `-verbose` option n’est pas disponible dans l’environnement de développement Visual Studio; elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `In.vb` et dirige le compilateur pour afficher les informations d’État détaillées.  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
