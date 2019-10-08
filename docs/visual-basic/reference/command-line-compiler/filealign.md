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
ms.openlocfilehash: fef2652f591e713140c651a9cb0df1ea9e6236c8
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005599"
---
# <a name="-filealign"></a>-filealign
Spécifie où les sections du fichier de sortie doivent être alignées.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a>Arguments  
 `number`  
 Obligatoire. Valeur qui spécifie l’alignement des sections dans le fichier de sortie. Les valeurs valides sont 512, 1024, 2048, 4096 et 8192. Ces valeurs sont exprimées en octets.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser l’option `-filealign` pour spécifier l’alignement des sections dans votre fichier de sortie. Les sections sont des blocs de mémoire contiguë dans un fichier exécutable portable (PE) qui contient du code ou des données. L’option `-filealign` vous permet de compiler votre application avec un alignement non standard ; la plupart des développeurs n’ont pas besoin d’utiliser cette option.  
  
 Chaque section est alignée sur une limite qui est un multiple de la valeur `-filealign`. Il n’existe aucune valeur fixe par défaut. Si `-filealign` n’est pas spécifié, le compilateur choisit une valeur par défaut au moment de la compilation.  
  
 En spécifiant la taille de la section, vous pouvez modifier la taille du fichier de sortie. Il peut être utile de modifier la taille de la section pour les programmes qui sont exécutés sur des appareils de petite taille.  
  
> [!NOTE]
> L’option `-filealign` n’est pas disponible dans l’environnement de développement Visual Studio. elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
