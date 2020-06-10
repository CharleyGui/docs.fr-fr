---
title: "Comment : créer des exceptions définies par l'utilisateur"
description: Découvrez comment créer des exceptions définies par l’utilisateur, qui sont une alternative à la hiérarchie des classes d’exception dérivées de la classe de base exception dans .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- user-defined exceptions
- exceptions, examples
- exceptions, user-defined
ms.assetid: 25819a5a-f915-4fc8-b924-a76915674e04
ms.openlocfilehash: 14eb6246ba4347f33766f7dff36463f2bf996330
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662795"
---
# <a name="how-to-create-user-defined-exceptions"></a>Guide pratique pour créer des exceptions définies par l’utilisateur

.NET fournit une hiérarchie de classes d’exception dérivées de la classe de base <xref:System.Exception>. Toutefois, si aucune exception prédéfinie ne répond à vos besoins, vous pouvez créer vos propres classes d’exception en les dérivant de la classe <xref:System.Exception>.

Quand vous créez vos propres exceptions, terminez le nom de la classe définie par l’utilisateur par le mot « Exception » et implémentez les trois constructeurs communs, comme indiqué dans l’exemple suivant. L’exemple définit une nouvelle classe d’exception nommée `EmployeeListNotFoundException`. La classe est dérivée de l’exception <xref:System.Exception> et inclut trois constructeurs.

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> Dans les situations où vous utilisez la communication à distance, vous devez vérifier que les métadonnées des exceptions définies par l’utilisateur sont disponibles sur le serveur (appelé) et le client (objet proxy ou appelant). Pour plus d’informations, consultez les [Bonnes pratiques pour les exceptions](best-practices-for-exceptions.md).

## <a name="see-also"></a>Voir aussi

- [Exceptions](index.md)
