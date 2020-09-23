---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: c5bf988d819a8df8aed99588abbb30e19d14b1ac
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91084981"
---
# <a name="-verbose"></a>-verbose

Fait en sorte que le compilateur génère des messages d’État et d’erreur détaillés.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  

 `+` &#124; `-`  
 Optionnel. La spécification de `-verbose` est identique à la spécification de `-verbose+` , ce qui amène le compilateur à émettre des messages détaillés. La valeur par défaut de cette option est `-verbose-` .  
  
## <a name="remarks"></a>Notes  

 L' `-verbose` option affiche des informations sur le nombre total d’erreurs émises par le compilateur, signale les assemblys qui sont chargés par un module et affiche les fichiers en cours de compilation.  
  
> [!NOTE]
> L' `-verbose` option n’est pas disponible dans l’environnement de développement Visual Studio ; elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  

 Le code suivant compile `In.vb` et dirige le compilateur pour afficher les informations d’État détaillées.  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](index.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
