---
title: Manipulations de chaînes de base dans .NET
description: Consultez un exemple qui appelle plusieurs méthodes de chaîne.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
ms.openlocfilehash: cc04f0c874b732668b4813f8325bd7060927f22a
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889125"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a>Guide pratique pour effectuer des manipulations de chaînes de base dans .NET

L’exemple suivant utilise certaines des méthodes décrites dans les rubriques [Opérations de chaînes de base](basic-string-operations.md) pour construire une classe qui effectue des manipulations de chaînes éventuellement comme dans une application réelle. La classe `MailToData` stocke le nom et l’adresse d’une personne dans des propriétés séparées et fournit un moyen de combiner les champs `City`, `State` et `Zip` dans une seule chaîne à montrer à l’utilisateur. De plus, la classe permet à l’utilisateur d’entrer la ville, l’état et le code postal dans une chaîne unique ; l’application analyse automatiquement la chaîne unique et entre les informations appropriées dans la propriété correspondante.  
  
Pour plus de simplicité, cet exemple utilise une application console avec une interface de ligne de commande.  
  
## <a name="example"></a>Exemple  

[!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
[!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
Lorsque le code précédent est exécuté, l’utilisateur est invité à entrer son nom et son adresse. L’application place les informations dans les propriétés appropriées et les montre à l’utilisateur, en créant une chaîne unique qui affiche la ville, l’état et le code postal.  
  
## <a name="see-also"></a>Voir aussi

- [Opérations de chaînes de base](basic-string-operations.md)
