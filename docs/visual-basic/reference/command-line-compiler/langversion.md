---
title: -langversion
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 72a5638a5c5364381ffd68604b0d44830d53f365
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344209"
---
# <a name="-langversion-visual-basic"></a>-langversion (Visual Basic)
Fait en sorte que le compilateur accepte uniquement la syntaxe qui est incluse dans la version de Visual Basic Language spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-langversion:version  
```  
  
## <a name="arguments"></a>Arguments  
 `version`  
 Obligatoire. Version du langage à utiliser pendant la compilation. Les valeurs acceptées `9`sont `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `default` et `latest`.

 L’un des nombres entiers peut également être spécifié `.0` à l’aide de comme version mineure `11.0`, par exemple.

 Vous pouvez voir la liste de toutes les valeurs possibles en `-langversion:?` spécifiant sur la ligne de commande.  
  
## <a name="remarks"></a>Notes  
 L' `-langversion` option spécifie la syntaxe que le compilateur accepte. Par exemple, si vous spécifiez que la version du langage est 9,0, le compilateur génère des erreurs pour la syntaxe qui est valide uniquement dans la version 10,0 et les versions ultérieures.  
  
 Vous pouvez utiliser cette option lorsque vous développez des applications qui ciblent différentes versions du .NET Framework. Par exemple, si vous ciblez .NET Framework 3,5, vous pouvez utiliser cette option pour vous assurer que vous n’utilisez pas la syntaxe de la version de langue 10,0.  
  
 Vous ne pouvez `-langversion` définir directement qu’à l’aide de la ligne de commande. Pour plus d’informations, consultez [Ciblage d’une version spécifique du .NET Framework](/visualstudio/ide/visual-studio-multi-targeting-overview).  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `sample.vb` pour Visual Basic 9,0.  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Cibler une version spécifique du .NET Framework](/visualstudio/ide/visual-studio-multi-targeting-overview)
