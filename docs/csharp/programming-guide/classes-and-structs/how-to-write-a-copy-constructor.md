---
title: Comment écrire un constructeur de copie (Guide de programmation C#)
description: Découvrez comment écrire un constructeur de copie en C# qui accepte une instance de la classe et retourne une nouvelle instance avec les valeurs de l’entrée.
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: db26b26ebcc51b57fdbe58ddaf92e5019cb69659
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899384"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Comment écrire un constructeur de copie (Guide de programmation C#)

C# ne fournit pas de constructeur de copie pour les objets, mais vous pouvez en écrire un vous-même.  
  
## <a name="example"></a>Exemple  

 Dans l’exemple suivant, la `Person`[classe](../../language-reference/keywords/class.md) définit un constructeur de copie qui prend comme argument une instance de `Person`. Les valeurs des propriétés de l’argument sont assignées aux propriétés de la nouvelle instance de `Person`. Le code contient un autre constructeur de copie qui envoie les propriétés `Name` et `Age` de l’instance que vous voulez copier au constructeur d’instance de la classe.  
  
 [!code-csharp[CopyConstructor](snippets/how-to-write-a-copy-constructor/Program.cs)]
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ICloneable>
- [Guide de programmation C#](../index.md)
- [Classes et structs](./index.md)
- [Constructeurs](./constructors.md)
- [Finaliseurs](./destructors.md)
