---
title: -nostdlib
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 4fcc5305985f5ba32b3e6ffb740c0611821215d3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097655"
---
# <a name="-nostdlib-visual-basic"></a>-nostdlib (Visual Basic)

Fait en sorte que le compilateur ne référence pas automatiquement les bibliothèques standard.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-nostdlib  
```  
  
## <a name="remarks"></a>Notes  

 L' `-nostdlib` option supprime la référence automatique à l’assembly System.dll et empêche le compilateur de lire le fichier Vbc. rsp. Le fichier Vbc. rsp, qui se trouve dans le même répertoire que le fichier Vbc.exe, fait référence aux assemblys de .NET Framework couramment utilisés et importe les `System` `Microsoft.VisualBasic` espaces de noms et.  
  
> [!NOTE]
> Les assemblys Mscorlib.dll et Microsoft.VisualBasic.dll sont toujours référencés.  
  
> [!NOTE]
> L' `-nostdlib` option n’est pas disponible dans l’environnement de développement Visual Studio ; elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  

 Le code suivant compile `T2.vb` sans référencer les bibliothèques standard. Vous devez définir la `_MYTYPE` constante de compilation conditionnelle sur la chaîne « Empty » pour supprimer l' `My` objet.  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [-noconfig](noconfig.md)
- [Compilateur de ligne de commande de Visual Basic](index.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
- [Personnalisation de la disponibilité ou non des objets dans My](../../developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
