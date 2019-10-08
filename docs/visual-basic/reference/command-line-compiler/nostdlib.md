---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 819505df2e7d5f93302f9ed601de856e36ed7124
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005418"
---
# <a name="-nostdlib-visual-basic"></a>-nostdlib (Visual Basic)
Fait en sorte que le compilateur ne référence pas automatiquement les bibliothèques standard.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-nostdlib  
```  
  
## <a name="remarks"></a>Notes  
 L’option `-nostdlib` supprime la référence automatique à l’assembly System. dll et empêche le compilateur de lire le fichier Vbc. rsp. Le fichier Vbc. rsp, qui se trouve dans le même répertoire que le fichier Vbc. exe, fait référence aux assemblys .NET Framework couramment utilisés et importe les espaces de noms `System` et `Microsoft.VisualBasic`.  
  
> [!NOTE]
> Les assemblys mscorlib. dll et Microsoft. VisualBasic. dll sont toujours référencés.  
  
> [!NOTE]
> L’option `-nostdlib` n’est pas disponible dans l’environnement de développement Visual Studio. elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `T2.vb` sans référencer les bibliothèques standard. Vous devez définir la constante de compilation conditionnelle `_MYTYPE` sur la chaîne « Empty » pour supprimer l’objet `My`.  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Personnalisation de la disponibilité ou non des objets dans My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
