---
title: -optioninfer
ms.date: 07/20/2015
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
ms.openlocfilehash: 524660fca7c56fa490cc85169898bf2bf6d1a16e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400576"
---
# <a name="-optioninfer"></a>-optioninfer
Permet l'utilisation de l'inférence de type de variable locale dans les déclarations de variable.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`+` &#124; `-`|Facultatif. Spécifiez `-optioninfer+` pour activer l'inférence de type de variable locale ou `-optioninfer-` pour la bloquer. L'option `-optioninfer`, sans aucune valeur spécifiée, est identique à `-optioninfer+`. La valeur par défaut en l'absence du commutateur `-optioninfer` est aussi `-optioninfer+`. La valeur par défaut est définie dans le fichier réponse Vbc.rsp.|  
  
> [!NOTE]
> Vous pouvez utiliser l'option `-noconfig` pour conserver les valeurs par défaut internes du compilateur au lieu de celles spécifiées dans le fichier vbc.rsp. Pour cette option, la valeur par défaut du compilateur est `-optioninfer-`.  
  
## <a name="remarks"></a>Notes  
 Si le fichier de code source contient une [instruction Option Infer](../../language-reference/statements/option-infer-statement.md), l’instruction remplace le `-optioninfer` paramètre du compilateur de ligne de commande.  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a>Pour définir-optioninfer (dans l’IDE de Visual Studio  
  
1. Sélectionnez un projet dans **Explorateur de solutions**. Dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2. Sous l’onglet **compiler** , modifiez la valeur dans la zone **Option Infer** .  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `test.vb` avec l'inférence de type de variable locale activée.  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](index.md)
- [-optioncompare](optioncompare.md)
- [-optionexplicit](optionexplicit.md)
- [-optionstrict](optionstrict.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
- [Instruction Option Infer](../../language-reference/statements/option-infer-statement.md)
- [Inférence de type local](../../programming-guide/language-features/variables/local-type-inference.md)
- [Valeurs par défaut VB, Projets, boîte de dialogue Options](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [Page Compiler, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [-noconfig](noconfig.md)
- [Génération à partir de la ligne de commande](building-from-the-command-line.md)
