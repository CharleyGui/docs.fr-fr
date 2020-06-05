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
ms.openlocfilehash: ed9adc7cddd9eb204937b9819e4eeff176821e95
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400554"
---
# <a name="-optioncompare"></a>-optioncompare

Spécifie la façon dont sont effectuées les comparaisons de chaînes.

## <a name="syntax"></a>Syntaxe

```console
-optioncompare:{binary | text}
```

## <a name="remarks"></a>Notes

Vous pouvez spécifier `-optioncompare` dans l’une des deux formes suivantes : `-optioncompare:binary` pour utiliser des comparaisons de chaînes binaires et `-optioncompare:text` pour utiliser des comparaisons de chaînes de texte. Par défaut, le compilateur utilise `-optioncompare:binary` .

Dans Microsoft Windows, la page de codes actuelle détermine l’ordre de tri binaire. Un ordre de tri binaire standard est le suivant :

`A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

Les comparaisons de chaînes basées sur du texte sont basées sur un ordre de tri de texte sans respect de la casse déterminé par les paramètres régionaux de votre système. Un ordre de tri de texte classique est le suivant :

`(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`

### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a>Pour définir-optioncompare dans l’IDE de Visual Studio

1. Sélectionnez un projet dans l' **Explorateur de solutions**. Dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l’onglet **Compiler**.

3. Modifiez la valeur dans la zone **option compare** .

### <a name="to-set--optioncompare-programmatically"></a>Pour définir-optioncompare par programmation

Consultez [instruction Option Compare](../../language-reference/statements/option-compare-statement.md).

## <a name="example"></a>Exemple

Le code suivant compile `ProjFile.vb` et utilise des comparaisons de chaînes binaires.

```console
vbc -optioncompare:binary projFile.vb
```

## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](index.md)
- [-optionexplicit](optionexplicit.md)
- [-optionstrict](optionstrict.md)
- [-optioninfer](optioninfer.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
- [Option Compare, instruction](../../language-reference/statements/option-compare-statement.md)
- [Valeurs par défaut VB, Projets, boîte de dialogue Options](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
