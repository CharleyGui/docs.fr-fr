---
title: -optioncompare
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
ms.openlocfilehash: ac385880f8c13c23dffff67fc2a1ecc5609fd189
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581416"
---
# <a name="-optioncompare"></a>-optioncompare

Spécifie la façon dont sont effectuées les comparaisons de chaînes.

## <a name="syntax"></a>Syntaxe

```console
-optioncompare:{binary | text}
```

## <a name="remarks"></a>Notes

Vous pouvez spécifier `-optioncompare` dans l’une des deux formes `-optioncompare:binary` suivantes : pour utiliser des comparaisons de `-optioncompare:text` chaînes binaires et pour utiliser des comparaisons de chaînes de texte. Par défaut, le compilateur utilise `-optioncompare:binary`.

Dans Microsoft Windows, la page de codes actuelle détermine l’ordre de tri binaire. Un ordre de tri binaire standard est le suivant :

`A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

Les comparaisons de chaînes basées sur du texte sont basées sur un ordre de tri de texte sans respect de la casse déterminé par les paramètres régionaux de votre système. Un ordre de tri de texte classique est le suivant :

`(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`

### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a>Pour définir-optioncompare dans l’IDE de Visual Studio

1. Sélectionnez un projet dans l' **Explorateur de solutions**. Dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l’onglet **Compiler**.

3. Modifiez la valeur dans la zone **option compare** .

### <a name="to-set--optioncompare-programmatically"></a>Pour définir-optioncompare par programmation

Consultez [instruction Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md).

## <a name="example"></a>Exemple

Le code suivant compile `ProjFile.vb` et utilise des comparaisons de chaînes binaires.

```console
vbc -optioncompare:binary projFile.vb
```

## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [-optioninfer (](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Compare (instruction)](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Valeurs par défaut VB, Projets, boîte de dialogue Options](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
