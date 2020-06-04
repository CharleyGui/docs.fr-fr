---
title: -netcf
ms.date: 03/13/2018
f1_keywords:
- /netcf
- -netcf
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
ms.openlocfilehash: 16fb6b3b63c848ea6c09cc18b0fcc488670f0926
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397473"
---
# <a name="-netcf"></a>-netcf

Définit le compilateur pour cibler le .NET Compact Framework.

## <a name="syntax"></a>Syntaxe

```console
-netcf
```

## <a name="remarks"></a>Notes

`-netcf`Avec l’option, le compilateur Visual Basic cible le .NET Compact Framework plutôt que le .NET Framework complet. La fonctionnalité de langage qui est présente uniquement dans le .NET Framework complet est désactivée.

L' `-netcf` option est conçue pour être utilisée avec [-sdkpath](sdkpath.md). Les fonctionnalités de langage désactivées par `-netcf` sont les mêmes que celles qui ne sont pas présentes dans les fichiers ciblés par `-sdkpath` .

> [!NOTE]
> L' `-netcf` option n’est pas disponible dans l’environnement de développement Visual Studio ; elle est disponible uniquement lors de la compilation à partir de la ligne de commande. L' `-netcf` option est définie lors du chargement d’un projet d’appareil Visual Basic.

L' `-netcf` option modifie les fonctionnalités de langage suivantes :

- Le mot clé [End \<keyword> Statement](../../language-reference/statements/end-keyword-statement.md) , qui termine l’exécution d’un programme, est désactivé. Le programme suivant compile et s’exécute sans `-netcf` mais échoue au moment de la compilation avec `-netcf` .

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- La liaison tardive, dans tous les formulaires, est désactivée. Des erreurs de compilation sont générées lorsque des scénarios de liaison tardive reconnus sont rencontrés. Le programme suivant compile et s’exécute sans `-netcf` mais échoue au moment de la compilation avec `-netcf` .

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- Les modificateurs [auto](../../language-reference/modifiers/auto.md), [ANSI](../../language-reference/modifiers/ansi.md)et [Unicode](../../language-reference/modifiers/unicode.md) sont désactivés. La syntaxe de l' [instruction DECLARE](../../language-reference/statements/declare-statement.md) est également modifiée en `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]` . Le code suivant illustre l’effet de `-netcf` sur une compilation.

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- L’utilisation des mots clés Visual Basic 6,0 qui ont été supprimés de Visual Basic génère une erreur différente lorsque `-netcf` est utilisé. Cela affecte les messages d’erreur pour les mots clés suivants :

  - `Open`

  - `Close`

  - `Put`

  - `Print`

  - `Write`

  - `Input`

  - `Lock`

  - `Unlock`

  - `Seek`

  - `Width`

  - `Name`

  - `FreeFile`

  - `EOF`

  - `Loc`

  - `LOF`

  - `Line`

## <a name="example"></a>Exemple

Le code suivant est compilé `Myfile.vb` avec l' .NET Compact Framework, à l’aide des versions de mscorlib. dll et de Microsoft. VisualBasic. dll trouvées dans le répertoire d’installation par défaut du .NET Compact Framework sur le lecteur C. En règle générale, vous utilisez la version la plus récente du .NET Compact Framework.

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](index.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
- [-sdkpath](sdkpath.md)
