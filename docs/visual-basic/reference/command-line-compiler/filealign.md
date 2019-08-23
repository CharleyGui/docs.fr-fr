---
title: -filealign
ms.date: 03/10/2018
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
ms.openlocfilehash: 2893c1760a856a7d736e9c03ba33d9771722b5b2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929473"
---
# <a name="-filealign"></a>-filealign
Spécifie où les sections du fichier de sortie doivent être alignées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-filealign:number  
```  
  
## <a name="arguments"></a>Arguments  
 `number`  
 Requis. Valeur qui spécifie l’alignement des sections dans le fichier de sortie. Les valeurs valides sont 512, 1024, 2048, 4096 et 8192. Ces valeurs sont exprimées en octets.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser l' `-filealign` option pour spécifier l’alignement des sections dans votre fichier de sortie. Les sections sont des blocs de mémoire contiguë dans un fichier exécutable portable (PE) qui contient du code ou des données. L' `-filealign` option vous permet de compiler votre application avec un alignement non standard; la plupart des développeurs n’ont pas besoin d’utiliser cette option.  
  
 Chaque section est alignée sur une limite qui est un multiple de `-filealign` la valeur. Il n’existe aucune valeur fixe par défaut. Si `-filealign` n’est pas spécifié, le compilateur choisit une valeur par défaut au moment de la compilation.  
  
 En spécifiant la taille de la section, vous pouvez modifier la taille du fichier de sortie. Il peut être utile de modifier la taille de la section pour les programmes qui sont exécutés sur des appareils de petite taille.  
  
> [!NOTE]
> L' `-filealign` option n’est pas disponible dans l’environnement de développement Visual Studio; elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
