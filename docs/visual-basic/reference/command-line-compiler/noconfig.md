---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: d7fc73aa24e3d2e323170f38f0f5d689f9c3abaf
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91065552"
---
# <a name="-noconfig"></a>-noconfig

Spécifie que le compilateur ne doit pas référencer automatiquement les assemblys .NET Framework couramment utilisés ou importer les `System` `Microsoft.VisualBasic` espaces de noms et.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>Notes  

 L' `-noconfig` option indique au compilateur de ne pas compiler avec le fichier Vbc. rsp, qui se trouve dans le même répertoire que le fichier Vbc.exe. Le fichier Vbc. rsp fait référence aux assemblys .NET Framework couramment utilisés et importe `System` les `Microsoft.VisualBasic` espaces de noms et. Le compilateur fait implicitement référence à l’assembly System.dll, sauf si l' `-nostdlib` option est spécifiée. L' `-nostdlib` option indique au compilateur de ne pas compiler avec vbc. rsp ou de référencer automatiquement l’assembly de System.dll.  
  
> [!NOTE]
> Les assemblys Mscorlib.dll et Microsoft.VisualBasic.dll sont toujours référencés.  
  
 Vous pouvez modifier le fichier Vbc. rsp pour spécifier des options de compilateur supplémentaires qui doivent être incluses dans chaque compilation de Vbc.exe (sauf si vous spécifiez l' `-noconfig` option). Pour plus d’informations, consultez [@ (spécifier un fichier réponse)](specify-response-file.md).  
  
 Le compilateur traite les options passées à la `vbc` commande en dernier. Par conséquent, toute option sur la ligne de commande remplace le paramètre de la même option dans le fichier Vbc. rsp.  
  
> [!NOTE]
> L' `-noconfig` option n’est pas disponible dans l’environnement de développement Visual Studio ; elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="see-also"></a>Voir aussi

- [-nostdlib (Visual Basic)](nostdlib.md)
- [Compilateur de ligne de commande de Visual Basic](index.md)
- [@ (spécifier un fichier réponse)](specify-response-file.md)
- [-Reference (Visual Basic)](reference.md)
