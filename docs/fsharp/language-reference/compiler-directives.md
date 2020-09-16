---
title: Directives de compilateur
description: 'En savoir plus sur les directives de préprocesseur de langage F #, les directives de compilation conditionnelle, les directives de ligne et les directives de compilateur.'
ms.date: 12/10/2018
f1_keywords:
- '#endif_FS'
ms.openlocfilehash: c3e1a07e0e09b5ae090c550368f8a9f8ee575bfb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557318"
---
# <a name="compiler-directives"></a>Directives de compilateur

Cette rubrique décrit les directives de processeur et de compilateur.

## <a name="preprocessor-directives"></a>Directives de préprocesseur

Une directive de préprocesseur est précédée du symbole # et s'affiche toute seule sur une ligne. Elle est interprétée par le préprocesseur, qui s'exécute avant le compilateur lui-même.

Le tableau suivant répertorie les directives de préprocesseur disponibles en F#.

|Directive|Description|
|---------|-----------|
|`#if`*symbole*|Prend en charge la compilation conditionnelle. Code dans la section après l' `#if` inclusion de si le *symbole* est défini. Le symbole peut également être inversé avec `!` .|
|`#else`|Prend en charge la compilation conditionnelle. Marque une section de code à inclure si le symbole utilisé avec le `#if` précédent n'est pas défini.|
|`#endif`|Prend en charge la compilation conditionnelle. Marque la fin d'une section conditionnelle de code.|
|`#`spline *entier*,<br/>`#`spline *int* *chaîne*int,<br/>`#`spline *int* *Verbatim-String*|Indique la ligne et le nom de fichier du code source d'origine, à des fins de débogage. Cette fonctionnalité est fournie pour les outils qui génèrent du code source F#.|
|`#nowarn`*WarningCode*|Désactive un ou plusieurs avertissements du compilateur. Pour désactiver un avertissement, trouvez son numéro dans la sortie du compilateur et incluez-le entre guillemets. Omettez le préfixe « FS ». Pour désactiver plusieurs numéros d'avertissement sur la même ligne, incluez chaque nombre entre guillemets, puis séparez chaque chaîne par un espace. Exemple :

`#nowarn "9" "40"`

L’effet de la désactivation d’un avertissement s’applique à l’ensemble du fichier, y compris des parties du fichier qui précèdent la directive. |

## <a name="conditional-compilation-directives"></a>Directives de compilation conditionnelle

Le code qui est désactivé par l’une de ces directives apparaît en grisé dans l’éditeur de Visual Studio Code.

> [!NOTE]
> Le comportement des directives de compilation conditionnelle n'est pas le même que dans les autres langages. Par exemple, vous ne pouvez pas utiliser des expressions booléennes qui impliquent des symboles et `true` et `false` n'ont aucune signification spéciale. Les symboles que vous utilisez dans la directive `if` doivent être définis par la ligne de commande ou dans les paramètres du projet ; il n'existe aucune directive de préprocesseur `define`.

Le code suivant illustre l'utilisation des directives `#if`, `#else` et `#endif`. Dans cet exemple, le code contient deux versions de la définition de `function1`. Lorsque `VERSION1` est défini à l’aide de l' [option de compilateur-define](./compiler-options.md), le code entre la `#if` directive et la `#else` directive est activé. Sinon, le code entre `#else` et `#endif` est activé.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7301.fs)]

Il n'existe aucune directive de préprocesseur `#define` en F#. Vous devez utiliser l'option du compilateur ou les paramètres du projet pour définir les symboles utilisés par la directive `#if`.

Les directives de compilation conditionnelle peuvent être imbriquées. Le retrait n'est pas significatif pour les directives de préprocesseur.

Vous pouvez également annuler la négation d’un symbole avec `!` . Dans cet exemple, la valeur d’une chaîne est un élément uniquement lorsqu’il ne s’agit _pas_ de débogage :

```fsharp
#if !DEBUG
let str = "Not debugging!"
#else
let str = "Debugging!"
#endif
```

## <a name="line-directives"></a>Directives de ligne

Lors de la génération, le compilateur signale les erreurs dans le code F# en référençant les numéros de ligne où chaque erreur se produit. Ces numéros de ligne commencent à 1 pour la première ligne dans un fichier. Toutefois, si vous générez du code source F# à partir d'un autre outil, les numéros de ligne du code généré n'ont en général aucun intérêt, car les erreurs dans le code F# généré proviennent très probablement d'une autre source. La directive `#line` offre un moyen aux auteurs d'outils qui génèrent du code source F# de transmettre des informations sur les numéros de ligne et fichiers sources d'origine au code F# généré.

Quand vous utilisez la directive `#line`, vous devez placer les noms de fichiers entre guillemets. À moins que le jeton textuel (`@`) ne s’affiche devant la chaîne, vous devez utiliser deux barres obliques inverses en tant que caractères d’espacement au lieu d’une pour les utiliser dans le chemin d’accès. Les jetons de ligne valides sont les suivants : Dans ces exemples, supposons que le fichier d'origine `Script1` produit un fichier de code F# généré automatiquement quand il est exécuté par l'intermédiaire d'un outil et que le code situé à l'emplacement de ces directives est généré à partir de jetons à la ligne 25 du fichier `Script1`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7303.fs)]

Ces jetons indiquent que le code F# généré à cet emplacement dérive de certaines constructions situées à ou près de la ligne `25` dans `Script1`.

## <a name="compiler-directives"></a>Directives de compilateur

Les directives de compilateur ressemblent aux directives de préprocesseur, car elles sont précédées d'un signe #, mais au lieu d'être interprétées par le préprocesseur, elles sont laissées au compilateur pour ce qui est de leur interprétation et des actions qu'elles entraînent.

Le tableau suivant répertorie la directive de compilateur disponible en F#.

|Directive|Description|
|---------|-----------|
|`#light` ["on" &#124; "OFF"]|Active ou désactive la syntaxe simplifiée, à des fins de compatibilité avec d'autres versions de ML. Par défaut, la syntaxe simplifiée est activée. La syntaxe détaillée est toujours activée. Par conséquent, vous pouvez utiliser la syntaxe simplifiée et la syntaxe détaillée. La directive `#light` en elle-même équivaut à `#light "on"`. Si vous spécifiez `#light "off"`, vous devez utiliser la syntaxe détaillée pour toutes les constructions de langage. La syntaxe présentée dans la documentation de F# part du principe que vous utilisez la syntaxe simplifiée. Pour plus d’informations, consultez [syntaxe détaillée](verbose-syntax.md).|

Pour connaître les directives de l’interpréteur (fsi.exe), consultez [programmation interactive avec F #](../tutorials/fsharp-interactive/index.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F #](index.md)
- [Options du compilateur](compiler-options.md)
