---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 19a70e500f6b75fd003bdb798f242cddb3926935
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964350"
---
# <a name="-nostdlib-visual-basic"></a>-nostdlib (Visual Basic)
Fait en sorte que le compilateur ne référence pas automatiquement les bibliothèques standard.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-nostdlib  
```  
  
## <a name="remarks"></a>Notes  
 L' `-nostdlib` option supprime la référence automatique à l’assembly System. dll et empêche le compilateur de lire le fichier Vbc. rsp. Le fichier Vbc. rsp, qui se trouve dans le même répertoire que le fichier Vbc. exe, fait référence aux assemblys .NET Framework couramment utilisés et importe `System` les `Microsoft.VisualBasic` espaces de noms et.  
  
> [!NOTE]
> Les assemblys mscorlib. dll et Microsoft. VisualBasic. dll sont toujours référencés.  
  
> [!NOTE]
> L' `-nostdlib` option n’est pas disponible dans l’environnement de développement Visual Studio; elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="example"></a>Exemples  
 Le code suivant compile `T2.vb` sans référencer les bibliothèques standard. Vous devez définir la `_MYTYPE` constante de compilation conditionnelle sur la chaîne «Empty» pour supprimer l' `My` objet.  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Personnalisation de la disponibilité ou non des objets dans My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
