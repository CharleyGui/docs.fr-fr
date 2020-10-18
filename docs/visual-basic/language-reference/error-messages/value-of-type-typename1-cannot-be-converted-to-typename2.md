---
title: La valeur de type '<typename1>' ne peut pas être convertie en '<typename2>'
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: a4aab83fd5695633a660eab00a5032ffbe45f326
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161320"
---
# <a name="bc30955-value-of-type-typename1-cannot-be-converted-to-typename2"></a>BC30955 : la valeur de type' \<typename1> 'ne peut pas être convertie en' \<typename2> '

Impossible de convertir la valeur de type' ' \<typename1> en' \<typename2> '. Une incompatibilité de type peut être due à la combinaison d’une référence de fichier et d’une référence de projet à l’assembly' \<assemblyname> '. Essayez de remplacer la référence de fichier à' \<filepath> 'dans \<projectname1> le projet' 'par une référence de projet à' \<projectname2> '.

 Dans le cas où un projet fait à la fois une référence de projet et une référence de fichier, le compilateur ne peut pas garantir qu’un type peut être converti en un autre.

 Le pseudo-code suivant illustre une situation qui peut générer cette erreur.

 `' ================ Visual Basic project P1 ================`

 `'        P1 makes a PROJECT REFERENCE to project P2`

 `'        and a FILE REFERENCE to project P3.`

 `Public commonObject As P3.commonClass`

 `commonObject = P2.getCommonClass()`

 `' ================ Visual Basic project P2 ================`

 `'        P2 makes a PROJECT REFERENCE to project P3`

 `Public Function getCommonClass() As P3.commonClass`

 `Return New P3.commonClass`

 `End Function`

 `' ================ Visual Basic project P3 ================`

 `Public Class commonClass`

 `End Class`

 Project `P1` fait une référence de projet indirecte par `P2` le biais du projet à Project `P3` , ainsi qu’une référence de fichier directe à `P3` . La déclaration de `commonObject` utilise la référence de fichier à `P3` , tandis que l’appel à `P2.getCommonClass` utilise la référence de projet à `P3` .

 Dans ce cas, le problème est que la référence de fichier spécifie un chemin d’accès et un nom de fichier pour le fichier de sortie de `P3` (généralement p3.dll), tandis que les références de projet identifient le projet source ( `P3` ) par nom de projet. Pour cette raison, le compilateur ne peut pas garantir que le type `P3.commonClass` provient du même code source via les deux références différentes.

 Cette situation se produit généralement lorsque les références de projet et les références de fichier sont mélangées. Dans l’illustration précédente, le problème ne se produisait pas si `P1` vous avez effectué une référence de projet directe à `P3` au lieu d’une référence de fichier.

 **ID d’erreur :** BC30955

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Remplacez la référence de fichier par une référence de projet.

## <a name="see-also"></a>Voir aussi

- [Conversions de type en Visual Basic](../../programming-guide/language-features/data-types/type-conversions.md)
- [Gestion des références dans un projet](/visualstudio/ide/managing-references-in-a-project)
