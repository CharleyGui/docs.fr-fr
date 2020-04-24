---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: dd98b45d75ff421dc81666ed47695132a49bfa3a
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524481"
---
# <a name="-addmodule"></a>-addmodule
Entraîne la mise à disposition par le compilateur de toutes les informations de type à partir du ou des fichiers spécifiés, pour le projet en cours de compilation.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>Arguments  
 `fileList`  
 Obligatoire. Liste de fichiers délimités par des virgules qui contiennent des métadonnées, mais qui ne contiennent pas de manifestes d’assembly. Les noms de fichiers contenant des espaces doivent être placés entre guillemets ("").  
  
## <a name="remarks"></a>Notes  
 Les fichiers listés par `fileList` le paramètre doivent être créés avec `-target:module` l’option, ou avec un autre compilateur équivalent `-target:module`à.  
  
 Tous les modules ajoutés `-addmodule` avec doivent se trouver dans le même répertoire que le fichier de sortie au moment de l’exécution. Autrement dit, vous pouvez spécifier un module dans n’importe quel répertoire au moment de la compilation, mais le module doit se trouver dans le répertoire de l’application au moment de l’exécution. Si ce n’est pas le cas, <xref:System.TypeLoadException> vous recevez une erreur.  
  
 Si vous spécifiez (implicitement ou explicitement) une option[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) autre `-target:module` que `-addmodule`avec, les fichiers que vous `-addmodule` transmettez pour faire partie de l’assembly du projet. Un assembly est requis pour exécuter un fichier de sortie qui a un ou plusieurs fichiers `-addmodule`ajoutés avec.  
  
 Utilisez [-Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) pour importer les métadonnées d’un fichier qui contient un assembly.  
  
> [!NOTE]
> L' `-addmodule` option n’est pas disponible dans l’environnement de développement Visual Studio. elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  
 Le code suivant crée un module.  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 Le code suivant importe les types du module.  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 Lorsque vous exécutez `t1`, il génère `802`.  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-cible (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
