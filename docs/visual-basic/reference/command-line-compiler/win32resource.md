---
title: -win32resource
ms.date: 03/13/2018
f1_keywords:
- -win32resource
- win32resource
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
ms.openlocfilehash: 382dcc6571aa06ecdfc32bf43080c4b7a36eb1f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961302"
---
# <a name="-win32resource"></a>-win32resource
Insère un fichier de ressources Win32 dans le fichier de sortie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-win32resource:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Nom du fichier de ressources à ajouter à votre fichier de sortie. Placez le nom de fichier entre guillemets ("") s’il contient un espace.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez créer un fichier de ressources Win32 avec le compilateur de ressources Microsoft Windows (RC).  
  
 Une ressource Win32 peut contenir des informations de version ou de bitmap (icône) qui permettent d’identifier votre application dans l' **Explorateur de fichiers**. Si vous ne spécifiez `-win32resource`pas, le compilateur génère des informations de version en fonction de la version de l’assembly. Les `-win32resource` options `-win32icon` et s’excluent mutuellement.  
  
 Consultez [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) pour référencer un fichier de ressources .NET Framework, ou [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) pour attacher un fichier de ressources de .NET Framework.  
  
> [!NOTE]
> L' `-win32resource` option n’est pas disponible dans l’environnement de développement Visual Studio; elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `In.vb` et joint un `Rf.res`fichier de ressources Win32:  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
