---
title: -quiet
ms.date: 07/20/2015
f1_keywords:
- -quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
ms.openlocfilehash: f894ed6a778e026ffd3976a63fe3b677eb6a9557
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400524"
---
# <a name="-quiet"></a>-quiet

Empêche le compilateur d'afficher le code pour les erreurs et les avertissements liés à la syntaxe.

## <a name="syntax"></a>Syntaxe

```console
-quiet
```

## <a name="remarks"></a>Notes

Par défaut, l'option `-quiet` n'est pas activée. Lorsque le compilateur signale une erreur ou un avertissement lié à la syntaxe, il renvoie également la ligne à partir du code source. Pour les applications qui analysent la sortie du compilateur, il peut être plus commode pour le compilateur de générer uniquement le texte du diagnostic.

Dans l’exemple suivant, `Module1` génère une erreur qui comprend le code source lorsqu’elle est compilée sans `-quiet` .

```vb
Module Module1
    Sub Main()
        x()
    End Sub
End Module
```

Sortie :

```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
```

Compilé avec `-quiet` , le compilateur génère uniquement les éléments suivants :

```console
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> L' `-quiet` option n’est pas disponible dans l’environnement de développement Visual Studio ; elle est disponible uniquement lors de la compilation à partir de la ligne de commande.

## <a name="example"></a>Exemple

Le code suivant compile `T2.vb` et n’affiche pas de code pour les diagnostics du compilateur liés à la syntaxe :

```console
vbc -quiet t2.vb
```

## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](index.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
