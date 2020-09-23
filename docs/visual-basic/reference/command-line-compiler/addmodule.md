---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 2db122acc03056a9cb6f355119d4c4e6da6ed175
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097785"
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

 Les fichiers listés par le `fileList` paramètre doivent être créés avec l' `-target:module` option, ou avec un autre compilateur équivalent à `-target:module` .  
  
 Tous les modules ajoutés avec `-addmodule` doivent se trouver dans le même répertoire que le fichier de sortie au moment de l’exécution. Autrement dit, vous pouvez spécifier un module dans n’importe quel répertoire au moment de la compilation, mais le module doit se trouver dans le répertoire de l’application au moment de l’exécution. Si ce n’est pas le cas, vous recevez une <xref:System.TypeLoadException> erreur.  
  
 Si vous spécifiez (implicitement ou explicitement) une option[-target (Visual Basic)](target.md) autre que `-target:module` avec `-addmodule` , les fichiers que vous transmettez pour faire `-addmodule` partie de l’assembly du projet. Un assembly est requis pour exécuter un fichier de sortie qui a un ou plusieurs fichiers ajoutés avec `-addmodule` .  
  
 Utilisez [-Reference (Visual Basic)](reference.md) pour importer les métadonnées d’un fichier qui contient un assembly.  
  
> [!NOTE]
> L' `-addmodule` option n’est pas disponible dans l’environnement de développement Visual Studio ; elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  

 Le code suivant crée un module.  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 Le code suivant importe les types du module.  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 Lorsque vous exécutez `t1` , il génère `802` .  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](index.md)
- [-cible (Visual Basic)](target.md)
- [-Reference (Visual Basic)](reference.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
