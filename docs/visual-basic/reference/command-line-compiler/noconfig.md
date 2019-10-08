---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: c57ed1699d110959e9faf3dc3d43bcc200851c1c
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005435"
---
# <a name="-noconfig"></a>-noconfig
Spécifie que le compilateur ne doit pas référencer automatiquement les assemblys .NET Framework couramment utilisés ou importer les espaces de noms `System` et `Microsoft.VisualBasic`.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>Notes  
 L’option `-noconfig` indique au compilateur de ne pas compiler avec le fichier Vbc. rsp, qui se trouve dans le même répertoire que le fichier Vbc. exe. Le fichier Vbc. rsp fait référence aux assemblys .NET Framework couramment utilisés et importe les espaces de noms `System` et `Microsoft.VisualBasic`. Le compilateur fait implicitement référence à l’assembly System. dll à moins que l’option `-nostdlib` soit spécifiée. L’option `-nostdlib` indique au compilateur de ne pas compiler avec vbc. rsp ou de référencer automatiquement l’assembly System. dll.  
  
> [!NOTE]
> Les assemblys mscorlib. dll et Microsoft. VisualBasic. dll sont toujours référencés.  
  
 Vous pouvez modifier le fichier Vbc. rsp pour spécifier des options de compilateur supplémentaires qui doivent être incluses dans chaque compilation vbc. exe (sauf lors de la spécification de l’option `-noconfig`). Pour plus d’informations, consultez [@ (Spécifier un fichier réponse)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).  
  
 Le compilateur traite les options passées à la commande `vbc` en dernier. Par conséquent, toute option sur la ligne de commande remplace le paramètre de la même option dans le fichier Vbc. rsp.  
  
> [!NOTE]
> L’option `-noconfig` n’est pas disponible dans l’environnement de développement Visual Studio. elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="see-also"></a>Voir aussi

- [-nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)
- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [@ (spécifier un fichier réponse)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)
- [-Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
