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
ms.openlocfilehash: 37ccd14dae0ebba2535185f2646e312d9bb70390
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266727"
---
# <a name="-optionexplicit"></a>-optionexplicit
Le compilateur signale les erreurs si les variables ne sont pas déclarées avant qu’elles ne soient utilisées.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 facultatif. Spécifier `-optionexplicit+` pour exiger une déclaration explicite des variables. L’option `-optionexplicit+` est la valeur `-optionexplicit`par défaut et est la même que . L’option `-optionexplicit-` permet la déclaration implicite de variables.  
  
## <a name="remarks"></a>Notes   
 Si le fichier de code source contient une déclaration `-optionexplicit` Option [Explicite,](../../../visual-basic/language-reference/statements/option-explicit-statement.md)l’instruction remplace le paramètre de compilateur de ligne de commande.  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>Pour définir -optionexplicit dans le Visual Studio IDE  
  
1. Sélectionnez un projet dans l' **Explorateur de solutions**. Dans le menu **Projet** , cliquez sur **Propriétés**.
  
2. Cliquez sur l’onglet **Compiler**.  
  
3. Modifier la valeur de la boîte **Option Explicite.**  
  
## <a name="example"></a> Exemple  
 Le code suivant compile quand `-optionexplicit-` il est utilisé.  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Explicit (instruction)](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Valeurs par défaut VB, Projets, boîte de dialogue Options](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
