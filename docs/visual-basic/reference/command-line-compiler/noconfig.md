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
Spécifie que le compilateur ne doit pas référencer automatiquement les assemblys .NET Framework couramment utilisés `System` ou `Microsoft.VisualBasic` importer les espaces de noms et.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>Notes  
 L' `-noconfig` option indique au compilateur de ne pas compiler avec le fichier Vbc. rsp, qui se trouve dans le même répertoire que le fichier Vbc. exe. Le fichier Vbc. rsp fait référence aux assemblys .NET Framework couramment utilisés et importe `System` les `Microsoft.VisualBasic` espaces de noms et. Le compilateur fait implicitement référence à l’assembly System. `-nostdlib` dll à moins que l’option ne soit spécifiée. L' `-nostdlib` option indique au compilateur de ne pas compiler avec vbc. rsp ou de référencer automatiquement l’assembly System. dll.  
  
> [!NOTE]
> Les assemblys mscorlib. dll et Microsoft. VisualBasic. dll sont toujours référencés.  
  
 Vous pouvez modifier le fichier Vbc. rsp pour spécifier des options de compilateur supplémentaires qui doivent être incluses dans chaque compilation vbc. exe (sauf si `-noconfig` vous spécifiez l’option). Pour plus d’informations, consultez [@ (spécifier un fichier réponse)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).  
  
 Le compilateur traite les options passées à la `vbc` commande en dernier. Par conséquent, toute option sur la ligne de commande remplace le paramètre de la même option dans le fichier Vbc. rsp.  
  
> [!NOTE]
> L' `-noconfig` option n’est pas disponible dans l’environnement de développement Visual Studio. elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="see-also"></a>Voir aussi

- [-nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)
- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [@ (spécifier un fichier réponse)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)
- [-Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
