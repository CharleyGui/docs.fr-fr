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
ms.openlocfilehash: 65cc3fb1b2fa9daa04013caa2b93a3949d0a15b9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91098934"
---
# <a name="-optionexplicit"></a>-optionexplicit

Fait en sorte que le compilateur signale des erreurs si les variables ne sont pas déclarées avant d’être utilisées.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  

 `+` &#124; `-`  
 Optionnel. Spécifiez `-optionexplicit+` pour exiger une déclaration explicite de variables. L' `-optionexplicit+` option est la valeur par défaut et est identique à `-optionexplicit` . L' `-optionexplicit-` option active la déclaration implicite de variables.  
  
## <a name="remarks"></a>Notes  

 Si le fichier de code source contient une [instruction Option Explicit](../../language-reference/statements/option-explicit-statement.md), l’instruction remplace le `-optionexplicit` paramètre du compilateur de ligne de commande.  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>Pour définir-optionexplicit dans l’IDE de Visual Studio  
  
1. Sélectionnez un projet dans l' **Explorateur de solutions**. Dans le menu **Projet** , cliquez sur **Propriétés**.
  
2. Cliquez sur l’onglet **Compiler**.  
  
3. Modifiez la valeur dans la zone **Option Explicit** .  
  
## <a name="example"></a>Exemple  

 Le code suivant compile lorsque `-optionexplicit-` est utilisé.  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](index.md)
- [-optioncompare](optioncompare.md)
- [-optionstrict](optionstrict.md)
- [-optioninfer](optioninfer.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
- [Option Explicit (instruction)](../../language-reference/statements/option-explicit-statement.md)
- [Valeurs par défaut VB, Projets, boîte de dialogue Options](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
