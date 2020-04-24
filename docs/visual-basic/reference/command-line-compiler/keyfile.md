---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: cffc3c5f0ff3dd48ca2c74bde346a967b209dc5f
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266740"
---
# <a name="-keyfile"></a>-keyfile
Spécifie un fichier contenant une clé ou une paire de clés afin d'attribuer un nom fort à un assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```console
-keyfile:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Obligatoire. Fichier qui contient la clé. Si le nom de fichier contient un espace, mettez-le entre guillemets ("").  
  
## <a name="remarks"></a>Notes  
 Le compilateur insère la clé publique dans le manifeste de l’assembly, puis signe l’assembly final avec la clé privée. Pour générer un fichier de clé, tapez `sn -k file` à la ligne de commande. Pour plus d’informations, consultez [sn. exe (outil Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
 Si vous compilez avec `-target:module`, le nom du fichier de clé est conservé dans le module et incorporé dans l’assembly créé quand vous compilez un assembly avec [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Vous pouvez également passer vos informations de chiffrement au compilateur avec [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md). Utilisez [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) si vous voulez obtenir un assembly partiellement signé.  
  
 Vous pouvez également spécifier cette option comme attribut personnalisé (<xref:System.Reflection.AssemblyKeyFileAttribute>) dans le code source de n’importe quel module de langage intermédiaire Microsoft.  
  
 Si `-keyfile` et [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) sont spécifiés (par option de ligne de commande ou par attribut personnalisé) dans la même compilation, le compilateur essaie d’abord le conteneur de clé. Si cette tentative réussit, l'assembly est signé avec les informations figurant dans le conteneur de clé. Si le compilateur ne trouve pas le conteneur de clé, il essaie le fichier spécifié `-keyfile`avec. Si cela se déroule correctement, l’assembly est signé avec les informations contenues dans le fichier de clé, et les informations sur la clé sont installées dans le conteneur de clé (semblable à `sn -i`). ainsi, lors de la compilation suivante, le conteneur de clé est valide.  
  
 Notez qu’un fichier de clé peut contenir uniquement la clé publique.  
  
 Pour plus d’informations sur la signature d’un assembly [, consultez Création et utilisation d’assemblys avec nom fort](../../../standard/assembly/create-use-strong-named.md) .  
  
> [!NOTE]
> L' `-keyfile` option n’est pas disponible dans l’environnement de développement Visual Studio. elle est disponible uniquement lors de la compilation à partir de la ligne de commande.

## <a name="example"></a>Exemple

Le code suivant compile le fichier `Input.vb` source et spécifie un fichier de clé.

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a>Voir aussi

- [Assemblys dans .NET](../../../standard/assembly/index.md)
- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
