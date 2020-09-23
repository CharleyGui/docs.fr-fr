---
title: -nologo
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 5557d681c5e6901592936efd35b3c552d43e39b0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097668"
---
# <a name="-nologo-visual-basic"></a>-nologo (Visual Basic)

Supprime l’affichage de la bannière de copyright et des messages d’information pendant la compilation.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a>Notes  

 Si vous spécifiez `-nologo` , le compilateur n’affiche pas de bannière de copyright. Par défaut, l'option `-nologo` n'est pas activée.  
  
> [!NOTE]
> L' `-nologo` option n’est pas disponible dans l’environnement de développement Visual Studio ; elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  

 Le code suivant compile `T2.vb` et n’affiche pas de bannière de copyright.  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](index.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
