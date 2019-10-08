---
title: -optionexplicit
ms.date: 07/20/2015
f1_keywords:
- /optionexplicit
- -optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
ms.openlocfilehash: 5c0946b94bfe02d797d1a484088869375703eb6a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005304"
---
# <a name="-optionexplicit"></a>-optionexplicit
Fait en sorte que le compilateur signale des erreurs si les variables ne sont pas déclarées avant d’être utilisées.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 facultatif. Spécifiez `-optionexplicit+` pour exiger une déclaration explicite des variables. L’option `-optionexplicit+` est la valeur par défaut et est identique à `-optionexplicit`. L’option `-optionexplicit-` active la déclaration implicite de variables.  
  
## <a name="remarks"></a>Notes  
 Si le fichier de code source contient une [instruction Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md), l’instruction remplace le paramètre du compilateur de ligne de commande `-optionexplicit`.  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>Pour définir-optionexplicit dans l’IDE de Visual Studio  
  
1. Sélectionnez un projet dans l' **Explorateur de solutions**. Dans le menu **Projet**, cliquez sur **Propriétés**.   
  
2. Cliquez sur l’onglet **Compiler**.  
  
3. Modifiez la valeur dans la zone **Option Explicit** .  
  
## <a name="example"></a>Exemple  
 Le code suivant compile lorsque `-optionexplicit-` est utilisé.  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Explicit (instruction)](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Valeurs par défaut Visual Basic, Projets, boîte de dialogue Options](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
