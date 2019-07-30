---
title: Fichiers de signature
description: Découvrez comment utiliser F# des fichiers de signature pour stocker des informations sur les signatures publiques d’un F# ensemble d’éléments de programme, tels que des types, des espaces de noms et des modules.
ms.date: 06/15/2018
ms.openlocfilehash: c04ac8bf4ee360a2caa15be8f2bbea41105bd160
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627155"
---
# <a name="signatures"></a>Signatures

Un fichier de signature contient des informations sur les signatures publiques d’un jeu d’éléments de programme F#, tels que des types, des espaces de noms et des modules. Il peut être utilisé pour spécifier l’accessibilité de ces éléments de programme.

## <a name="remarks"></a>Notes

Pour chaque fichier de code F#, vous pouvez avoir un *fichier de signature*, qui est un fichier portant le même nom que le fichier de code, mais avec l’extension .fsi au lieu de .fs. Les fichiers de signature peuvent également être ajoutés à la ligne de commande de compilation si vous utilisez la ligne de commande directement. Pour faire la distinction entre les fichiers de code et les fichiers de signature, les fichiers de code sont parfois appelés *fichiers d’implémentation*. Dans un projet, le fichier de signature doit précéder le fichier de code associé.

Un fichier de signature décrit les espaces de noms, modules, types et membres dans le fichier d’implémentation correspondant. Les informations dans un fichier de signature vous permettent de spécifier les parties du code dans le fichier d’implémentation correspondant auxquelles le code peut accéder à l’extérieur du fichier d’implémentation, ainsi que les parties qui sont internes au fichier d’implémentation. Les espaces de noms, modules et types inclus dans le fichier de signature doivent être un sous-ensemble des espaces de noms, des modules et des types inclus dans le fichier d’implémentation. À quelques exceptions près notées plus loin dans cette rubrique, les éléments de langage qui n’apparaissent pas dans le fichier de signature sont considérés comme privés pour le fichier d’implémentation. Si aucun fichier de signature n’est trouvé dans le projet ou la ligne de commande, l’accessibilité par défaut est utilisée.

Pour plus d’informations sur l’accessibilité par défaut, consultez [Access Control](access-control.md).

Dans un fichier de signature, vous ne répétez pas la définition des types et les implémentations de chaque méthode ou fonction. Au lieu de cela, vous utilisez la signature pour chaque méthode et fonction, qui sert de spécification complète des fonctionnalités implémentées par un fragment de module ou d’espace de noms. La syntaxe pour une signature de type est la même que celle utilisée dans les déclarations de méthode abstraites dans les interfaces et les classes abstraites, et est également indiquée par IntelliSense et l’interpréteur F# fsi.exe lorsqu’il affiche correctement l’entrée compilée.

Quand il n’y a pas assez d’informations dans la signature de type pour indiquer si un type est sealed ou non, ou s’il s’agit d’un type d’interface, vous devez ajouter un attribut qui indique la nature du type au compilateur. Les attributs utilisés à cette fin sont décrits dans le tableau suivant.

|Attribut|Description|
|---------|-----------|
|`[<Sealed>]`|Type qui n’a pas de membres abstraits ou qui ne doit pas être étendu.|
|`[<Interface>]`|Type qui est une interface.|

Le compilateur produit une erreur si les attributs ne sont pas cohérents entre la signature et la déclaration dans le fichier d’implémentation.

Utilisez le mot clé `val` pour créer une signature pour une valeur ou une valeur de fonction. Le mot clé `type` introduit une signature de type.

Vous pouvez générer un fichier de signature à l’aide de l’option de compilateur `--sig` . En général, vous n’écrivez pas les fichiers .fsi manuellement. À la place, vous générez des fichiers .fsi à l’aide du compilateur, vous les ajoutez à votre projet, si vous en avez un, et vous les modifiez en supprimant les méthodes et les fonctions que vous ne souhaitez pas rendre accessibles.

Les signatures de type sont soumises à plusieurs règles :

- Les abréviations de type dans un fichier d’implémentation ne doivent pas correspondre à un type sans abréviation dans un fichier de signature.

- Les enregistrements et les unions discriminées doivent exposer la totalité ou aucun de leurs champs et constructeurs, et l’ordre dans la signature doit correspondre à celui dans le fichier d’implémentation. Les classes peuvent révéler une partie, la totalité ou aucun des champs et des méthodes dans la signature.

- Les classes et les structures qui ont des constructeurs doivent exposer les déclarations de leurs classes de base (déclaration `inherits` ). En outre, les classes et les structures qui ont des constructeurs doivent exposer toutes leurs méthodes abstraites et leurs déclarations d’interface.

- Les types d’interface doivent révéler toutes leurs méthodes et interfaces.

Les signatures de valeur obéissent aux règles suivantes :

- Les modificateurs d’accessibilité (`public`, `internal`, etc.) et les modificateurs `inline` et `mutable` dans la signature doivent correspondre à ceux présents dans l’implémentation.

- Le nombre de paramètres de type générique (déduits implicitement ou déclarés explicitement) doit correspondre, et les types et contraintes de type dans les paramètres de type générique doivent correspondre.

- Si l’attribut `Literal` est utilisé, il doit figurer dans la signature et l’implémentation, et la même valeur littérale doit être utilisée pour les deux.

- Le modèle de paramètres (aussi appelé *arité*) des signatures et des implémentations doit être cohérent.

- Si les noms de paramètres dans un fichier de signature diffèrent du fichier d’implémentation correspondant, le nom figurant dans le fichier de signature est utilisé à la place, ce qui peut provoquer des problèmes lors du débogage ou du profilage. Si vous souhaitez être informé de ces incompatibilités, activez l’avertissement 3218 dans votre fichier projet ou lors de l’appel du compilateur ( `--warnon` consultez sous [Options du compilateur](compiler-options.md)).

Le code suivant illustre un exemple de fichier de signature contenant des signatures d’espace de noms, de module, de valeur de fonction et de type avec les attributs appropriés. Il indique également le fichier d’implémentation correspondant.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssignatures/snippet9002.fs)]

Le code suivant représente le fichier d’implémentation.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssignatures/snippet9001.fs)]

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)
- [Contrôle d'accès](access-control.md)
- [Options du compilateur](compiler-options.md)
