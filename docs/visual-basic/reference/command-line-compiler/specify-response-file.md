---
title: '@ (spécifier un fichier réponse)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: c578495bbba0efee79f02da284c7feffb8c12fab
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348552"
---
# <a name="-specify-response-file-visual-basic"></a>@ (spécifier un fichier réponse) (Visual Basic)

Spécifie un fichier qui contient les options du compilateur et les fichiers de code source à compiler.

## <a name="syntax"></a>Syntaxe

```console
@response_file
```

## <a name="arguments"></a>Arguments

`response_file`  
Obligatoire. Fichier qui répertorie les options du compilateur ou les fichiers de code source à compiler. Placez le nom de fichier entre guillemets ("") s’il contient un espace.

## <a name="remarks"></a>Notes

Le compilateur traite les options du compilateur et les fichiers de code source spécifiés dans un fichier réponse comme s’ils avaient été spécifiés sur la ligne de commande.

Pour spécifier plusieurs fichiers réponse dans une compilation, spécifiez plusieurs options de fichier réponse, comme ci-dessous.

```console
@file1.rsp @file2.rsp
```

Dans un fichier réponse, plusieurs options de compilateur et fichiers de code source peuvent apparaître sur une seule ligne. Une seule spécification d’option de compilateur doit apparaître sur une ligne (ne peut pas s’étendre sur plusieurs lignes). Les fichiers réponse peuvent comporter des commentaires qui commencent `#` par le symbole.

Vous pouvez combiner les options spécifiées sur la ligne de commande avec les options spécifiées dans un ou plusieurs fichiers réponse. Le compilateur traite les options de commande au fur et à mesure qu’il les rencontre. Par conséquent, les arguments de ligne de commande peuvent remplacer les options précédemment listées dans les fichiers réponse. À l’inverse, les options d’un fichier réponse remplacent les options listées précédemment sur la ligne de commande ou dans d’autres fichiers réponse.

Visual Basic fournit le fichier Vbc. rsp, qui se trouve dans le même répertoire que le fichier Vbc. exe. Le fichier Vbc. rsp est inclus par défaut, sauf `-noconfig` si l’option est utilisée. Pour plus d’informations, consultez [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).

> [!NOTE]
> L' `@` option n’est pas disponible dans l’environnement de développement Visual Studio. elle est disponible uniquement lors de la compilation à partir de la ligne de commande.

## <a name="example"></a>Exemple

Les lignes suivantes proviennent d’un exemple de fichier réponse.

```console
# build the first output file
-target:exe
-out:MyExe.exe
source1.vb
source2.vb
```

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser l' `@` option avec le fichier réponse nommé. `File1.rsp`

```console
vbc @file1.rsp
```

## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
