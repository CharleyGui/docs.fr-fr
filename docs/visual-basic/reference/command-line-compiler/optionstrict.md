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
ms.openlocfilehash: 3dd12971a082869c32b6292ed45e2014b8b0e2c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400537"
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
Facultatif. L' `-optionstrict+` option restreint la conversion de type implicite. La valeur par défaut de cette option est `-optionstrict-` . L' `-optionstrict+` option est la même que `-optionstrict` . Vous pouvez utiliser à la fois pour la sémantique de type permissive.

`custom`  
Obligatoire. Avertir lorsque la sémantique de langue stricte n’est pas respectée.

## <a name="remarks"></a>Notes

Lorsque `-optionstrict+` est activé, seules les conversions de type étendue peuvent être effectuées implicitement. Les conversions de types restrictives implicites, telles que l’assignation d’un `Decimal` objet de type à un objet de type entier, sont signalées comme des erreurs.

Pour générer des avertissements pour les conversions de types restrictives implicites, utilisez `-optionstrict:custom` . Utilisez `-nowarn:numberlist` pour ignorer des avertissements particuliers et `-warnaserror:numberlist` traiter des avertissements particuliers comme des erreurs.

### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a>Pour définir-optionstrict dans l’IDE de Visual Studio

1. Sélectionnez un projet dans l' **Explorateur de solutions**. Dans le menu **projet** , cliquez sur **Propriétés.**

2. Cliquez sur l’onglet **Compiler**.

3. Modifiez la valeur dans la zone **option strict** .

### <a name="to-set--optionstrict-programmatically"></a>Pour définir-optionstrict par programmation

Consultez [Option Strict Statement](../../language-reference/statements/option-strict-statement.md).

## <a name="example"></a>Exemple

Le code suivant compile `Test.vb` à l’aide de la sémantique de type stricte.

```console
vbc -optionstrict+ test.vb
```

## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](index.md)
- [-optioncompare](optioncompare.md)
- [-optionexplicit](optionexplicit.md)
- [-optioninfer](optioninfer.md)
- [-nowarn](nowarn.md)
- [-warnaserror (Visual Basic)](warnaserror.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
- [Option Strict Statement](../../language-reference/statements/option-strict-statement.md)
- [Valeurs par défaut VB, Projets, boîte de dialogue Options](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
