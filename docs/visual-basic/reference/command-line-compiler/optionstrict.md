---
title: -optionstrict
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: 6d281fe07754f0471f8d6c0e31cf3ea890060504
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005353"
---
# <a name="-optionstrict"></a>-optionstrict
Applique la sémantique de type stricte pour restreindre les conversions de types implicites.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-optionstrict[+ | -]  
-optionstrict[:custom]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 facultatif. L’option `-optionstrict+` restreint la conversion de type implicite. La valeur par défaut de cette option est `-optionstrict-`. L’option `-optionstrict+` est identique à `-optionstrict`. Vous pouvez utiliser à la fois pour la sémantique de type permissive.  
  
 `custom`  
 Obligatoire. Avertir lorsque la sémantique de langue stricte n’est pas respectée.  
  
## <a name="remarks"></a>Notes  
 Lorsque `-optionstrict+` est activé, seules les conversions de type étendu peuvent être effectuées implicitement. Les conversions de types restrictives implicites, telles que l’assignation d’un objet de type `Decimal` à un objet de type entier, sont signalées comme des erreurs.  
  
 Pour générer des avertissements pour les conversions de types restrictives implicites, utilisez `-optionstrict:custom`. Utilisez `-nowarn:numberlist` pour ignorer des avertissements particuliers et `-warnaserror:numberlist` pour traiter des avertissements particuliers comme des erreurs.  
  
### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a>Pour définir-optionstrict dans l’IDE de Visual Studio  
  
1. Sélectionnez un projet dans l' **Explorateur de solutions**. Dans le menu **projet** , cliquez sur **Propriétés.**   
  
2. Cliquez sur l’onglet **Compiler**.  
  
3. Modifiez la valeur dans la zone **option strict** .  
  
### <a name="to-set--optionstrict-programmatically"></a>Pour définir-optionstrict par programmation  
  
- Consultez [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `Test.vb` à l’aide d’une sémantique de type stricte.  
  
```console
vbc -optionstrict+ test.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)
- [-warnaserror (Visual Basic)](../../../visual-basic/reference/command-line-compiler/warnaserror.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Strict (instruction)](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Valeurs par défaut Visual Basic, Projets, boîte de dialogue Options](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
